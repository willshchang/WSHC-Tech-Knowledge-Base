# DuckDuckGo — Playbook

**Document Type:** Personal Playbook / Knowledge Bridge Reference  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  

---

## What This Is

This pairs with `duckduckgo-research.md`. That file holds objective company knowledge. This file holds the bridges — how AHS/Apple experience maps onto DuckDuckGo's specific technical environment and culture — plus the language patterns worth using naturally in conversation.

**Note on figures:** source material for this playbook consistently uses a 113,000-user AHS scale rather than the 160,000 figure used elsewhere in this KB. Worth reconciling which figure is accurate before using this material live — flagged here rather than silently changed.

---

## Migration Table: AHS/Apple → DuckDuckGo

| Concept | The AHS/Apple Reality | The DuckDuckGo Reality |
|---|---|---|
| **Command structure** | Complex vertical hierarchy | Flat, non-hierarchical — equal value on all roles, can escalate directly to CEO if needed |
| **Meetings** | Necessary for alignment | Auxiliary to Asana; discouraged Wed/Thu |
| **Project ownership** | Project Managers | The DRI (Directly Responsible Individual) |
| **Compensation** | Negotiated based on experience | Fixed & transparent — no negotiation |

---

## Provisioning Evolution: PXE to Autopilot

### The AHS Vendor-Led Hybrid Provisioning Model

Microserve (vendor) applies a "Thin Image" and performs an Offline Domain Join (ODJ) to the local domain, using `dsregcmd /join` to flag the device for cloud registration.

**The three-step bridge, in sequence:**
1. **The "Clean Slate" (The Pour)** — Ivanti wipes the drive and applies the AHS image, containing local AD configuration. Because the laptop is on the AHS Ethernet, it has a direct line to local AD domain controllers immediately.
2. **Trust Reconstruction** — as the Ivanti script finishes, the device joins the domain. Active Directory sees the machine immediately; Entra Connect sees the updated object and pushes identity to the cloud.
3. **Intune Auto-Enrollment** — because the machine is on the internal network, it doesn't wait for VPN. It heartbeats to the domain controller, the "Auto-enroll to MDM" Group Policy hits the machine, and it silently reaches out to Intune for management.

| Feature | Vendor Side (Microserve) | Internal Side (AHS Deskside) |
|---|---|---|
| Connection | External / offline | Internal (Ethernet/PXE) |
| Method | Thin Image + script | Gold Image (PXE Pour) |
| Domain join | Offline Domain Join (ODJ) | Direct domain join |
| Intune speed | Slower (requires internet + sync) | Faster (direct GPO hit) |

**DuckDuckGo's model — Zero-Touch Windows Autopilot:** hardware stays completely clean. When a user enters their email, the device identifies itself to the cloud and pulls its identity and policies directly from Intune — no imaging step at all.

**The bridge:** "I've managed complex, high-scale deployments where we relied on a vendor to pre-stage our Hybrid Join architecture. I understand how to manage the hand-off between physical imaging and cloud registration. I also managed the full hardware lifecycle, including internal re-imaging using Ivanti PXE — the mechanics of the 'Gold Image,' where a local network pours the OS and a chain of GPOs triggers Intune enrollment. While this works for an on-site workforce, I've seen the friction it causes for remote recovery. I'm ready to translate that lifecycle expertise into DuckDuckGo's Autopilot workflows — moving from an on-prem-first model to a cloud-native experience that eliminates vendor-side domain joining entirely. Instead of PXE-booting a laptop to fix a software issue, Intune's Autopilot Reset or Remote Wipe restores a device to business-ready state over any Wi-Fi connection, anywhere in the world."

---

## Identity Lifecycle: The Long Chain vs. The Instant Sync

### The AHS Journey (Legacy Hybrid)

`HR System (ADP) → IDM (Middleware) → On-Prem AD (via LDAP) → Entra Connect → Entra ID`

1. **HR ADP** — the human source of truth; a recruiter enters the new hire
2. **IDM / Middleware** — pulls data from ADP, creates the username, assigns Employee ID
3. **On-Prem AD via LDAP** — IDM writes the new user into the local Active Directory using the LDAP protocol
4. **Entra Connect** — syncs every 30 minutes, pushing identity (and a password hash) to the cloud
5. **Entra ID** — the user appears in the cloud portal, but only once sync completes
6. **Login (Hybrid SSO)** — the laptop checks local AD first; once verified, Entra ID issues a Primary Refresh Token (PRT) for seamless M365 SSO

**The pain point — "Sync Latency":** any break in this chain, or the 30-minute sync wait itself, stops a user from working. A password change requires talking to on-prem AD first (VPN required), then waiting for sync to Entra ID before cloud apps recognize the change.

### The DuckDuckGo Journey (Cloud-Native)

`HR System (ADP) → Entra ID (via SCIM) → Automated Provisioning (Terraform)`

This is the "Instant Sync" — all middle layers eliminated. Entra ID communicates directly with ADP via SCIM; the moment an account is created, Terraform sees the new user's department attribute and automatically provisions the correct Slack channels, Asana projects, and GitHub repos — no 30-minute wait involved anywhere in the chain.

**The bridge:** "At AHS, I managed an identity lifecycle that functioned as a long chain — moving from ADP through IDM middleware into on-prem AD via LDAP. I understand the importance of data integrity at the source, because any break in that sync chain stops someone from being able to log in. At DuckDuckGo, I'm excited to work with a cloud-native identity model — leveraging SCIM for direct HR-to-cloud provisioning and Terraform for group automation, eliminating those legacy layers entirely. This ensures the Day 1 experience for a new hire is instantaneous and reliable, rather than dependent on legacy sync windows."

---

## MDM Bridge: Workspace ONE to Entra/Intune

| Feature | Workspace ONE (WSO) | Microsoft Intune |
|---|---|---|
| Logic engine | Smart Groups | Dynamic Groups (Entra ID) |
| Setup | Profiles / Payloads | Configuration Profiles |
| Health check | Compliance Policies | Compliance Policies (same concept) |
| Remote support | Assist | Remote Help / Screen Sharing |
| Software hub | Intelligent Hub | Company Portal |

**The "Duck BYOD" key concept:** Automated Device Enrollment (ADE) makes the management profile non-removable — if a laptop is stolen, it becomes a paperweight.

**The AHS gap this bridge exploits:** at AHS, WSO Smart Groups are managed manually and not synced to Entra ID — creating a "double work" entitlement step (managing access in two separate places). This gap is a genuine talking point: "At AHS, our EMM team manages WSO Smart Groups independently of Entra ID. While it works, it creates a manual entitlement step. I've seen the efficiency gaps there, which is why I'm focused on Dynamic Groups in Intune — building a system where HR attributes automatically trigger MDM groups, removing the manual middle-man entirely."

---

## Citrix vs. Native: The Application Virtualization Bridge

### The Core Concept — "Pixel Streaming"

In Citrix, an application (e.g., Connect Care/Epic) actually runs on a server in the data center. Only screen updates (pixels) are sent to the local device; keystrokes and mouse input are sent back to the server. **The privacy win:** no patient data ever touches the local laptop — if a device is lost, there's zero data exposure on the hard drive.

**Key components:**
- **StoreFront** — the web portal where users log in to see their app icons
- **Delivery Controller** — routes users to the least-loaded server
- **NetScaler (Citrix Gateway)** — the security gate handling external login and identity verification before granting data center access

### AHS vs. DuckDuckGo Comparison

| Feature | AHS (Legacy Hybrid) | DuckDuckGo (Full Cloud-Native) |
|---|---|---|
| App delivery | Citrix virtualization — pixels streamed from server | Native SaaS — apps run locally or in a secure browser |
| Security model | Data isolation — data never leaves the data center | Zero Trust — secured by Entra ID and device compliance |
| User experience | Dependent on Citrix Gateway/NetScaler connection | Dependent on local device power and direct cloud access |

**The bridge:** "At AHS, we rely heavily on Citrix Application Virtualization for tools like Connect Care. It's a strong security-by-design choice — sensitive data stays centralized in the data center while Citrix Workspace provides a seamless user experience. It does add infrastructure complexity, though. At DuckDuckGo, I'm excited to see how that same data sovereignty gets achieved with cloud-native tools like Conditional Access and Bitwarden — moving away from heavy virtualization toward secure, managed endpoints directly."

---

## Cloud Migration Discovery — The Honest Framing

**Why this matters:** explains genuinely deep knowledge of Intune, Autopilot, and Entra ID despite AHS still operating in a hybrid state.

"I was heavily involved in the discovery and playbook-drafting phase for a transition to a cloud-native architecture. While the broader provincial rollout was paused due to budget and scale constraints, that experience allowed me to map out exactly how Zero-Touch and Modern Identity should look. I'm now looking to bring that ready-to-go expertise to a team like DuckDuckGo, where the culture and technology are already aligned for that speed."

"I know how to uphold operational excellence with high speed and high security while maintaining the most convenient, least-consequence path — I want to do that at DuckDuckGo."

---

## Infrastructure as Code — The Terraform Bridge

Terraform reframed simply: a version-controlled shopping list. Instead of manually clicking "New Group" in the Entra ID portal:

```terraform
resource "azuread_group" "duck_engineering" {
  display_name     = "Engineering Team"
  security_enabled = true
}
```

**The benefits that matter for this bridge:** consistency (no typos, the 100th group is identical to the 1st), audit trail visibility (GitHub shows exactly who changed what), and speed/security combined (an entire new department onboarded in 5 minutes via script).

---

## DuckDuckTalk — Language Patterns Worth Using Naturally

| Instead of Saying | Say This |
|---|---|
| "Let's have a meeting" | "I'll start an Asana task for this so we can keep the momentum async" |
| Describing a project decision generically | "I trusted the vendor's documentation, but I questioned the security impact and validated the fix in a sandbox environment" |
| "Information" or "Trends" | "Signals" — e.g., "I'm looking at the signals in our Entra ID logs" |
| Generic UX language | "Frictionless" — e.g., "My goal is frictionless privacy for our team members" |

---

## Technical Hot-Seat Prep — Identity Focus

Since DuckDuckGo is a privacy company, identity is central. Expect depth on:

- **Conditional Access** — e.g., "Only allow access to Bitwarden if the device is a managed Mac and the user is on a known VPN"
- **SCIM (automated provisioning)** — e.g., adding a user to the "Marketing" group in Entra should automatically surface them in Zoom, Mattermost, and Asana

**The bridge:** "At scale, I had to question assumptions about manual provisioning and validate direction through automated Conditional Access and SCIM — I'm ready to DRI that for the Ducks."

---

## BYOD Device Lifecycle — How Enrollment Actually Works

At AHS, IT selects the hardware and pushes it out. At DuckDuckGo, employees choose their own device (a developer might want a high-spec MacBook Pro, a recruiter a thin-and-light Windows laptop), pay upfront or use a company card, and get reimbursed. This means managing a genuinely diverse fleet, not a uniform one.

**Zero-Touch enrollment mechanics (Windows):** a new hire selects "Work or School" setup on first boot (not a personal Microsoft account). Entering their @duck.com email triggers Entra ID recognition, which hands the device directly to Intune — which then automatically pushes standard apps (Asana, Mattermost, 1Password/Bitwarden) and security policies (FileVault/BitLocker).

---

## Operational Bridge Phrases

**On automation:** "I see you're using Terraform and Jenkins for infrastructure. At my scale, I learned that manual changes are a security risk. I'm excited to apply that logic to an environment where Identity-as-Code via Entra ID is the standard."

**On stack diversity:** "I'm very comfortable in a multi-OS environment. Whether it's Ubuntu for servers, macOS for creative teams, or Windows via Autopilot, I view them all as endpoints that need to meet the same compliance bar in Intune."

**On privacy tools specifically:** "I'm a big proponent of privacy-first tools like Bitwarden. It aligns with experience in healthcare, where data sovereignty isn't optional — it's the core mission."

**The "insider" signal worth knowing:** DuckDuckGo's core search engine was originally built on Perl — most modern companies use Python instead. Knowing this and referencing it naturally (e.g., being prepared to support that legacy while automating the future with PowerShell and Terraform) signals genuine familiarity with the company beyond surface research.

---

## Final Architecture Mental Map

- **Identity:** ADP (HR) → LDAP/AD → Entra ID (SSO)
- **Hardware:** Dell → vendor thin image (via PXE) → user login
- **Management:** Ivanti (updates/remote) + Intune/WSO (policy/SSO)
- **Clinical apps:** Citrix (virtual apps) + mobile tunnel tooling

**Consolidated summary of the transition being described:**
- Imaging: Thin Imaging (PXE/Ivanti/Task Sequences) → Zero-Touch (Autopilot/ABM)
- Identity: Hybrid-Sync (LDAP/Entra Connect) → Cloud-Native SCIM (ADP to Entra ID directly)
- Tooling: Citrix/Ivanti (legacy workhorses) → Terraform/Jenkins (modern workhorses)
