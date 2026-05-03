# Cloud Security: Supply Chain, Infrastructure Risk & Responsible Disclosure

**Document Type:** Knowledge Article  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** May 2026  

---

## Case Study: GitHub RCE via git push (CVE-2026-3854)

Wiz Research discovered a critical Remote Code Execution vulnerability in GitHub's internal git infrastructure — affecting both GitHub.com and GitHub Enterprise Server.

### How It Worked

GitHub's internal services communicate via a **semicolon-delimited header**. `git push` options (user-controlled strings) were embedded into this header **without sanitizing semicolons**.

```bash
git push -o "x;`cat payload.txt`"
# remote: uid=500(git) gid=500(git) groups=500(git)
```

By injecting three chained payloads, researchers:
1. Bypassed the production sandbox
2. Injected a malicious hook definition pointing to an arbitrary binary
3. Achieved **unsandboxed RCE on GitHub.com**

### Impact

| Scope | Detail |
|---|---|
| Affected systems | GitHub.com + all supported GitHub Enterprise Server versions |
| Data exposure | From a compromised storage node: access to **millions of repositories** across organizations |
| Tenant isolation | Fully broken on GitHub.com |

### Responsible Disclosure Outcome

- Wiz Research ceased testing immediately upon confirming the vulnerability
- GitHub deployed a fix to GitHub.com **the same day** of disclosure
- Patches released for all supported GHES versions

> "GitHub for addressing the issue in record time" — Wiz Research

**Lesson:** Header injection via user-controlled strings without sanitization is a critical class of vulnerability. Delimiter characters (semicolons, pipes, newlines) in inputs must be treated as untrusted.

---

## The Broader Cloud Security Problem Space

AI-powered tools like Claude Code and Claude Security handle **code scanning** well. But cloud security is much wider:

| Domain | What It Covers |
|---|---|
| Identity sprawl | Over-privileged users, stale accounts, unmanaged service identities |
| Active exploitation detection | Suspicious logins, unusual device activity, abnormal traffic patterns |
| Network segmentation | Flat networks, exposed services, uncontrolled outbound access |
| Cloud misconfiguration | Public storage buckets, overly permissive IAM policies, disabled logging |
| Secrets & machine credentials | Hardcoded tokens, shared API keys, long-lived certificates |
| Infrastructure integrity | Configuration drift, unauthorized changes, shadow infrastructure |
| Supply chain / third-party access | Vendor VPN, SaaS integrations, unmanaged OAuth apps |
| Incident response | Access revocation, cross-system investigation, threat containment |
| Cyber resilience | Environment rollback, data recovery, service re-deployment |

> Code scanning is one slice. All of the above still needs dedicated tooling and human judgment.

---

## OAuth & Supply Chain Risk in Cloud Environments

OAuth tokens create a **persistent access surface** that survives standard deprovisioning:

- User offboarded from directory → OAuth token in connected SaaS app may still be live
- Attacker compromises third-party service → uses valid token to access primary environment
- From the security system's perspective: **nothing looks wrong**

This is particularly relevant in G-Suite and Microsoft 365 environments where "Sign in with" flows are common.

**Mitigation:**
- Treat OAuth token discovery as **continuous**, not periodic
- Enforce short token lifetimes
- Monitor **how** access is used, not just how it was granted
- Move toward just-in-time access patterns

---

## Linux Kernel Vulnerability: copy_fail

A critical Linux kernel vulnerability was disclosed in April 2026 affecting the copy-on-write mechanism.

> Reference: [The Hacker News — Linux copy_fail Vulnerability](https://thehackernews.com/2026/04/new-linux-copy-fail-vulnerability.html)

Details pending further review. Relevant for environments running Linux-based infrastructure (Azure VMs, Kubernetes nodes, Docker hosts).

---

## Key Takeaways

- **Header injection is a critical vulnerability class** — user-controlled strings near delimiter characters must be sanitized
- **Responsible disclosure works** — Wiz + GitHub demonstrated the gold standard: confirm, stop testing, report, fix fast
- **AI code scanning doesn't cover cloud security breadth** — identity, network, misconfig, and incident response require dedicated tooling
- **OAuth tokens outlive their users** — deprovisioning from the directory is not the same as revoking access
- **Supply chain risk lives in integrations** — every SaaS OAuth connection is a potential lateral movement path

---

## Official References

| Source | Link |
|---|---|
| Wiz Research — GitHub RCE CVE-2026-3854 | https://www.wiz.io/blog/github-rce-vulnerability-cve-2026-3854 |
| The Hacker News — Linux copy_fail | https://thehackernews.com/2026/04/new-linux-copy-fail-vulnerability.html |
| 1Password — OAuth Supply Chain Breaches | https://1password.com/blog/protect-against-oauth-supply-chain-breaches |
| Fast Company — 1Password: AI as Threat and Tool | https://www.fastcompany.com/91530685/1password-sees-ai-as-both-threat-and-tool |
| CSO Online — AI Reshaping DevSecOps | https://www.csoonline.com/article/4163355/ai-is-reshaping-devsecops-to-bring-security-closer-to-the-code.html |
