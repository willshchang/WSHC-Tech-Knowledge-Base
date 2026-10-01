# Expo: Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** September 2026  
**Repository:** https://github.com/willshchang/wshc-tech-knowledge-base  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Legal name** | 650 Industries, Inc. (operating as Expo) |
| **Founded** | 2015; Y Combinator Summer 2016 batch |
| **HQ** | San Francisco, CA (press release dateline); open roles on the careers page are listed as remote, some US-only |
| **Stage** | Series B |
| **Latest round** | $45M Series B, April 16, 2026, led by Georgian (valuation not disclosed) |
| **Profitability** | Profitable before the Series B, per the co-founder's own funding post |
| **Scale (self-reported, homepage)** | 7M+ weekly downloads, 100K+ active developers, 500K+ projects, 100K+ daily builds, 70K+ Discord members |
| **Scale (Series B press release)** | 3M+ developers in the community; apps used by hundreds of millions of people |
| **Notable customers** | Phantom, Pizza Hut, MTA, PrizePicks (press release); case studies include incident.io, Partiful, Hipcamp, Cameo, Mollie |
| **Category** | Open-source React Native framework plus paid mobile build, release, and hosting cloud (EAS) |
| **Website** | https://expo.dev |

---

## Founders and Leadership

- **Charlie Cheever (Co-founder and CEO)**: early Facebook engineer who worked on Facebook Connect and turning Facebook into a platform, then co-founded Quora with Adam D'Angelo in 2009. Started working on Expo in summer 2015. His framing of the current problem: *"business critical apps are not making it to production."*
- **James Ide (Co-founder)**: listed as a founder on Expo's Y Combinator profile and in the Series B coverage.
- **Seth Webster (Chief Developer Evangelist)**: spent six-plus years leading React at Meta (per The New Stack), and per his own Expo blog post he continues to serve as Executive Director of the React Foundation while at Expo. His one-line reason for joining: *"When software becomes easier to generate, the bottleneck moves from tooling to shipping."*

**Founder-market read:** Cheever built platform features at Facebook, where "turn a website into a platform other developers build on" was the job. Expo is the same instinct applied to mobile: make the hard platform plumbing invisible so developers only write the app.

---

## Funding Timeline

| Round | Amount | Date | Led By | Notes |
|---|---|---|---|---|
| Earlier rounds | Not itemized by Expo | 2015 to 2025 | Not disclosed | Investors listed on Expo's about page: Y Combinator, South Park Commons, SV Angel, Avenir, Graph Ventures, Red Swan Ventures, A.Capital |
| Series B | $45M | April 16, 2026 | Georgian | Leadout Capital, A.Capital Ventures, and Red Swan Ventures participating |

> Expo was already profitable when it raised the Series B. In the co-founder's words: *"We have been profitable for a while so we didn't need to raise money to keep going."* This was growth capital, not runway. The stated uses: more engineers, faster builds, more third-party integrations, and AI tooling. Georgian's own framing: *"Expo has reached an inflection point, evolving from a popular open-source framework into an increasingly important infrastructure layer."*

---

## The Problem Expo Solves

Shipping a mobile app the traditional way means:

- **Two codebases**: Swift for iOS, Kotlin for Android, two teams, two sets of bugs
- **Heavy local tooling**: Xcode (Mac only) and Android Studio just to compile
- **Code signing pain**: certificates, provisioning profiles, keystores, all easy to break and hard to debug
- **Slow fixes**: every change, even a one-line typo fix, waits on App Store and Play Store review
- **Store submission as a manual chore**: screenshots, metadata, uploads, TestFlight

**Expo's answer:** write the app once in React and TypeScript, run it on iOS, Android, and the web, and let the cloud handle the compile, sign, submit, update, and monitor steps.

> Analogy: React Native is the engine. Expo is the rest of the car (SDK and router), plus the factory that builds it (EAS Build), the dealership paperwork (EAS Submit), and the mechanic who can fix things on the road without a recall (EAS Update).

**The strongest third-party proof:** the React Native team's own docs changed in June 2024 to recommend using a framework to start new apps, and named Expo as *"the only recommended community framework for React Native."* The same post states that *"Expo, the framework, is and will remain free and open source, while Expo Application Services (EAS) is an optional paid service."* Expo is also a founding member of the React Foundation (Linux Foundation, announced October 2025), which now governs React and React Native, alongside Amazon, Callstack, Meta, Microsoft, Software Mansion, and Vercel.

---

## Product Surface

Expo is two products that feed each other: a free, MIT-licensed open-source framework, and a paid cloud (EAS) that turns framework users into customers.

### The Open-Source Framework (free)

| Piece | What It Does |
|---|---|
| **Expo SDK** | A library of native modules (camera, notifications, image, file system, and more) that work across iOS, Android, and web. Each SDK release is pinned to a React Native version (SDK 57 ships React Native 0.86) |
| **Expo CLI** | Local dev server and project tooling (`npx expo start`, `npx expo install`, `npx expo prebuild`) |
| **Expo Router** | File-based routing for native and web: add a file, get a screen. Every screen is deep linkable, routes are typed, and API routes (`+api.ts` files) live in the same project |
| **Expo Go** | A sandbox app from the stores that runs a project instantly without building anything. Limited to the native modules bundled in the SDK |
| **Development builds** | Your own debug build (via `expo-dev-client`) that includes any custom native code. The path teams move to once they outgrow Expo Go |
| **Expo Modules API and Expo UI** | Write your own native modules in Swift and Kotlin; Expo UI exposes SwiftUI and Jetpack Compose components to React |

### Expo Application Services (EAS, paid cloud with a free tier)

| Service | What It Does |
|---|---|
| **EAS Build** | Compiles and signs iOS and Android binaries in the cloud, so no Mac is needed for iOS builds |
| **EAS Submit** | Uploads the build to the App Store or Google Play with one CLI command |
| **EAS Update** | Over-the-air (OTA) updates for the JavaScript, styling, and image parts of an app, between store releases |
| **EAS Workflows** | Mobile CI/CD defined as YAML in `.eas/workflows/`, triggered by GitHub events, cron, App Store Connect events, the CLI, or the REST API |
| **EAS Hosting** | Deploys Expo Router web apps and API routes; runs on Cloudflare Workers (V8 isolates, not full Node.js) |
| **EAS Observe** | Production performance monitoring (app startup, navigation, EAS Update health). Generally available August 20, 2026 |
| **EAS Metadata / EAS Insights** | Store listing metadata as code, and usage analytics (both in preview) |

### EAS Update: What It Can and Cannot Change

| Can ship OTA | Needs a new store build |
|---|---|
| JavaScript logic, UI copy, styling, images, translations | Native code or native dependency changes |
| Bug fixes between releases | App permission changes (camera, location, and others) |

**The guardrail Expo states itself:** updates still have to follow App Store and Play Store guidelines, which usually means behavior changes need review. OTA is for fixes, not for sneaking in new features.

**Why this matters now:** Microsoft retired Visual Studio App Center, including its CodePush OTA service, on March 31, 2025. That pushed a large base of React Native teams to find a new OTA provider, and Expo publishes a dedicated CodePush to EAS Update migration guide.

---

## The AI Surface (2025 to 2026)

Expo's homepage now leads with "Mobile AI infrastructure." The pieces:

| Offering | What It Is | Status (Sep 2026) |
|---|---|---|
| **Expo MCP Server** | Remote MCP server at `mcp.expo.dev/mcp`. Server tools cover docs, installing libraries, builds, workflow runs, TestFlight crashes and feedback, and store reviews. Local tools (via the `expo-mcp` package and a flag on `npx expo start`) add screenshots, taps, and finding views by `testID` | Live. Free plan access since May 26, 2026, with a monthly usage cap; higher allowances on paid plans |
| **Claude connector** | Expo listed in Claude's connector directory; one Expo sign-in works across Claude desktop, web, mobile, and Claude Code | Launched August 13, 2026 |
| **Expo Skills** | Open-source instruction files (`expo/skills` on GitHub) that teach coding agents how to build, deploy, and debug Expo apps. Installable as a plugin for Claude Code and Codex, or via `npx skills add expo/skills` | Live |
| **Cloud simulators** | On-demand simulators where an agent installs a build, drives it, checks its own work, and posts a session recording to the PR | Early access |
| **Expo Launch** | Connect a GitHub repo and submit to the App Store from the browser, no certificate setup. Pitched at developers, no-code creators, and AI tool builders | Beta |
| **`@expo/agent-cli`** | Experimental CLI in SDK 58 beta, described by Expo as *"built by agents and designed for agents"* | Experimental |
| **Expo Agent** | Browser-based app builder powered by Claude Code, launched alongside the Series B | Wound down: announced July 20, 2026, unavailable after July 31, 2026 |

**Why Expo Agent was shut down, in Expo's own reasoning:** rather than build its own web-based harness and IDE, Expo concluded it could have more impact by integrating with the harnesses developers already use every day. Users were pointed to Claude Code (or their editor of choice) plus the Expo MCP server, Expo Skills, and the existing CLI and EAS services.

**My read (analysis, not a company claim):** this is a clear strategic call. Expo stopped competing with the agent harnesses and chose to be the infrastructure every harness calls. An AI can write the app code, but it still cannot skip compiling, signing, store submission, OTA delivery, and production monitoring. That is exactly the part Expo charges for. The same pattern shows up with AI app builders: Bolt (StackBlitz) integrated Expo in February 2025 as its mobile path, which puts Expo underneath other companies' agents rather than beside them.

---

## Business Model and Pricing

Open core plus usage-based cloud. The framework is free forever; EAS is where revenue comes from.

| Plan | Price | Build Credit | OTA Update MAUs | Notable Gates |
|---|---|---|---|---|
| **Free** | $0 | Up to 15 Android and 15 iOS builds, low-priority queue | 1,000 | 60 CI/CD minutes, basic Observe (100K events/month) |
| **Starter** | $19/month + usage | $45 of credit, then usage-based | 3,000 | High-priority queue, Observe (500K events/month) |
| **Production** | $199/month + usage | $225 of credit, 2 concurrencies | 50,000 | SSO, priority support, EAS Update code signing |
| **Enterprise** | Custom | $1,000 of build credit, 5 concurrencies | 1M+ | 99.9% uptime SLA, audit logs, strategic support, SOC 2 Type 2 report access |

**Usage meters worth knowing:** extra build concurrency (+$50 each), update bandwidth beyond 100 GiB ($0.10 per GiB), EAS Hosting beyond the free allowance ($2 per 1M requests), and Observe events beyond the allowance ($5 per 1M events).

> The pricing page is the clearest map of Expo's upgrade path. Free covers learning and prototypes. Starter is a solo developer shipping. Production is where team and security features start (SSO, update code signing). Enterprise is compliance and scale (audit logs, SLA). Each gate lines up with a real moment in an app's life.

---

## Open Source and Product-Led Growth

**The funnel, as I read it (analysis):**

1. **Adoption is free and bottom-up**: a developer runs `npx create-expo-app`, and the React Native docs send new developers to Expo by default
2. **Identity is the first conversion**: an Expo account is needed for EAS, the MCP server (OAuth), and, since September 3, 2026, for running projects in Expo Go on iOS. Sign-in options grew in 2026 (GitHub sign-in in April, passkeys in July)
3. **Usage creates the paid moment**: builds, update MAUs, hosting requests, and Observe events all meter up as an app finds users
4. **Team and security needs create the sales moment**: SSO, audit logs, SLAs, and SOC 2 reports are gated to Production and Enterprise

**Public signal of a sales-assist layer:** the careers page (late September 2026) lists Account Executive, Technical Account Manager, Technical Inside Sales, Technical Business Development Representative, Product Marketing Manager, Growth Engineer, and GTM Engineer roles. That is the classic PLG company move: keep self-serve as the engine, then add people (and tooling) to catch the accounts that are ready to grow.

**Note on the Expo Go login change:** Expo's changelog does not state a reason for requiring login. Any link to growth, abuse prevention, or security is my speculation.

---

## Customers and Scale Signals

| Signal | Detail | Source Type |
|---|---|---|
| Named customers | Phantom, Pizza Hut, MTA, PrizePicks | Series B press release |
| Case studies | MTA (*"identify, patch, and deploy an OTA fix in under 90 seconds"*), incident.io and Partiful (never needed Xcode), MyWheels (release cycles cut from three weeks to one) | Expo customers page |
| Developer reach | 7M+ weekly downloads, 100K+ active developers, 100K+ daily builds | Expo homepage (self-reported) |
| npm | The `expo` package shows roughly 11M weekly downloads in the npm registry (late September 2026) | npm registry |
| Ecosystem standing | Only framework the React Native docs recommend; React Foundation founding member | reactnative.dev, Linux Foundation |

> Download numbers differ by source and date (about 4M weekly in the April press release, 7M+ on the homepage now, about 11M for the `expo` package on npm). Treat them as a growth trend, not a precise figure.

---

## Where GTM AI Ops Fits: My Analysis

Everything in this section is my own analysis of what an internal AI tooling function would plausibly build at a PLG developer-tools company shaped like Expo. None of it is a company claim.

**The core idea:** a PLG company has more signal than people. Thousands of accounts build, update, and deploy every day, and a small sales, support, and marketing team cannot read all of it. Internal agents turn raw product usage into the right action for the right person.

| Internal Agent (Idea) | Job | Likely Inputs | Human Gate |
|---|---|---|---|
| **Signal router (PQL scoring)** | Spot accounts showing buying intent and route them with context | Build volume vs. credit, concurrency queueing, MAUs nearing a plan limit, SSO or SOC 2 interest | Rep decides whether to reach out |
| **Account enrichment** | Map an Expo account or org to a real company and dedupe | Email domain, GitHub org, published store listings, CRM | Low risk; spot-check samples |
| **Support deflection** | Answer common questions from docs, changelog, and skills; attach build logs when escalating | Docs, changelog, build and workflow logs, past tickets | Human approves anything about billing, refunds, or account access |
| **Expansion and churn signals** | Flag overage patterns, forecast next month's bill, suggest a better-fit plan, catch accounts going quiet | Usage meters, billing, failure rates | Account owner reviews before any customer message |
| **Release enablement** | Turn each changelog entry and SDK release into a short brief for sales and support | Changelog, SDK release notes, GitHub issues | Product marketing reviews |
| **Security questionnaire assistant** | Draft answers to vendor security reviews | Trust center, SOC 2 scope, SSO and audit log docs | Security owner signs off every answer |

**Design rules I would hold these to (same rules as the agent layer in the [WSHC ZTAI Lab](https://github.com/willshchang/WSHC-ZTAI-Lab)):**

- **One agent, one task**: no shared context bleeding between the support bot and the pricing bot
- **No god mode**: each agent gets its own scoped identity and the least access its task needs, read-only by default
- **Human approval for state changes**: CRM stage changes, customer-facing emails, credits, and refunds all wait for a person
- **Every action logged with a reason**: the question later is always "what did it do, and why," not "what could it do"
- **Measure outcomes, not replies**: a support agent that answers fast but wrong is worse than no agent (see [Agentic Reliability](../../../02_ZTAI-Ecosystem/agentic-reliability.md))

**A useful parallel:** Expo already ships this pattern to its own customers. The MCP server lets an agent read builds, crashes, and reviews, and the Claude connector shows the reply text before it posts a store review response. An internal GTM agent stack can follow the same shape: MCP-style access to internal systems, with a human preview step before anything leaves the building.

---

## Security and Identity Through the ZTAI Lens

### Expo's Own Controls

| Control | Detail |
|---|---|
| **SOC 2 Type 2** | EAS compliant as of December 21, 2024; 136 controls; Expo reports the audit as exception-free |
| **SSO** | Production and Enterprise plans; Okta, OneLogin, Google, and Microsoft Entra ID supported |
| **MFA and passkeys** | TOTP MFA with backup keys; passkey sign-in added July 2026 |
| **Audit logs** | Enterprise only; covers member changes, API tokens, and credential changes |
| **Encryption** | HTTPS in transit, AES-256 or greater at rest; services hosted on Google Cloud |

### Non-Human Identity: Personal Tokens vs. Robot Users

| | Personal Access Token | Robot User |
|---|---|---|
| **Acts as** | You, with everything you can reach | A service account inside one organization |
| **Scope** | All your personal and org access | Limited by an assigned role |
| **Can sign in to Expo products** | Yes (it is you) | No, token-only |
| **ZTAI read** | An agent holding this inherits a human's full blast radius | The right shape for CI and agents: scoped, revocable, not a person |

The `EXPO_TOKEN` environment variable authenticates any EAS CLI command without `eas login`, which makes it the most important secret in an Expo CI pipeline. Expo's own guidance: treat tokens with the same care as a password.

### Secrets: Build Secrets vs. App Code

EAS environment variables have three visibility levels: **plain text** (visible everywhere), **sensitive** (masked in logs, readable in CLI), and **secret** (never readable outside EAS servers). The critical rule from Expo's docs: anything in client code, including `EXPO_PUBLIC_` variables, *"should be considered public and readable to any individual that can run your app."*

**Agent lesson:** a coding agent that writes an API key into the app bundle has published it. Secret-level variables protect build jobs, not the shipped app.

### OTA Updates as a Supply Chain

EAS Update can push new JavaScript to every installed copy of an app without store review. That is the feature, and also the risk: whoever can publish an update controls production behavior. Expo's answer is **end-to-end code signing** (Production and Enterprise), where updates are signed with the developer's own key and verified on the device, so that *"ISPs, CDNs, cloud providers, and even EAS itself cannot tamper with updates."* The private key is generated and kept locally.

This connects directly to the npm and CI/CD supply chain risks in [Cloud Security: Supply Chain Risk](../../../01_AI-Era-Security-Domains/05_Cloud-Security/cloud-security-supply-chain-risk.md).

### Agents Acting Through Expo

The MCP server uses OAuth with the user's Expo account, so an agent connected to it acts with that user's permissions. That is the exact pattern from [Agentic vs. Human Identity Governance](../../../02_ZTAI-Ecosystem/agentic-vs-human-identity-governance.md): agents do not decide, they execute conditions with whatever access they inherited. Two things Expo gets right here: the preview-before-post step on review replies, and the stated policy that Expo does not use MCP data to train AI models. What a careful team should still add (my analysis): run agents under a robot user or a least-privilege account, keep store submissions and production updates behind a human approval, and log every agent-triggered build or update.

---

## Competitors and Alternatives

| Alternative | Position vs. Expo |
|---|---|
| **Flutter (Google)** | The main cross-platform rival. Dart language and its own rendering engine, vs. Expo's React and TypeScript with real native views. Competes for the same "one codebase" decision |
| **Native (Swift/SwiftUI, Kotlin/Jetpack Compose)** | Maximum platform fidelity, two codebases. Expo narrows the gap with the Expo Modules API and Expo UI, which expose SwiftUI and Jetpack Compose components |
| **Kotlin Multiplatform / Compose Multiplatform (JetBrains)** | Shares Kotlin code across platforms; appeals to Android-first teams rather than web and React teams |
| **Capacitor (Ionic)** | Wraps a web app in a native shell; fits web-first teams that accept a WebView UI |
| **React Native without a framework** | Always possible, but the React Native docs' own line is that you are either using a framework or building your own |
| **Mobile CI/CD (Bitrise, Codemagic, GitHub Actions with fastlane)** | Compete with EAS Build, Submit, and Workflows, not with the framework. Expo's edge is that the cloud already understands Expo projects |
| **OTA update providers** | Microsoft's CodePush (App Center) was retired March 31, 2025, leaving a self-hosted standalone server as Microsoft's option. EAS Update is the managed alternative Expo markets directly to those teams |
| **AI app builders (Bolt and others)** | More partner than competitor: Bolt builds mobile apps on Expo. Expo Agent briefly overlapped with this space before being wound down |

**Honest read:** Expo's moat is not the framework alone (it is open source and anyone can fork it). The moat is the combination: default recommendation from React Native itself, a very large developer base that learns Expo first, and a cloud that already knows how to build, sign, ship, and update those exact projects.

---

## Recent News Timeline (2026)

| Date | Event |
|---|---|
| March 4 | Expo Observe enters private preview |
| April 16 | $45M Series B led by Georgian; Expo Agent launched in beta |
| April 23 | Sign in with GitHub |
| May 21 | Expo SDK 56 |
| May 26 | Expo MCP Server available on the Free plan |
| June 15 | EAS Workflows automates iOS device registration for internal builds |
| June 30 | Expo SDK 57 (React Native 0.86, React 19.2) |
| July 6 | Sign in with passkeys |
| July 20 | Expo Agent wind-down announced (off after July 31) |
| August 13 | Expo connector added to Claude |
| August 20 | EAS Observe generally available |
| September 3 | Login required to run projects in Expo Go (iOS first) |
| September 9 | One-command PostHog integration (analytics tagged with EAS Update data) |
| September 15 | Expo SDK 58 beta (React Native 0.88 RC, iOS 27 support, `expo-app-intents`, experimental `@expo/agent-cli`) |

---

## ZTAI Layer Placement

**Not a native security layer**  

Expo is developer infrastructure, not a security or identity product, so it does not take a row in the [ZTAI Ecosystem Map](../../../02_ZTAI-Ecosystem/ZTAI-ecosystem-map.md). It shows up in the map's logic in two places:

| Angle | Where It Connects |
|---|---|
| **A tool surface agents act through** | The MCP server makes Expo something agents call, which means Identity & Access questions apply: which identity, what scope, who approves |
| **A release pipeline** | Build, sign, submit, and OTA update are supply chain controls. Code signing for updates is the same "trust the artifact, not the transport" idea found across Secrets & Credentials |
| **Monitoring** | EAS Observe measures app performance (startup, navigation, update health). By my own split in [Practical Observability](../../../02_ZTAI-Ecosystem/practical-observability.md), that is app health telemetry, not agent behavior observability |

**Closest KB neighbours:** [Dosu](../Dosu/dosu-research.md) (Expo Skills solve the same "give the agent correct context" problem for Expo projects), [LangChain](../LangChain/langchain-research.md) (Expo chose to plug into existing harnesses rather than build one), and [WorkOS](../WorkOS/workos-research.md) (Airlock's approval-before-irreversible-action idea maps to store submissions and production OTA updates).

---

## Key Takeaways

- **Expo is the default way to build React Native apps**: the React Native docs name it as the only recommended framework, and Expo helped found the React Foundation that now governs React Native
- **Open core, usage-based cloud**: the framework is free and MIT-licensed; revenue comes from EAS (builds, OTA update MAUs, hosting, workflows, Observe), with SSO, code signing, audit logs, and SLAs gating the upper tiers
- **Profitable before a $45M Series B** (April 2026, Georgian), which points to a healthy self-serve engine
- **The 2026 AI strategy changed shape mid-year**: Expo Agent launched in April and was wound down by July 31, in favor of MCP, Skills, and a Claude connector. Expo chose to be infrastructure for every agent harness, not a harness itself
- **PLG with a growing sales layer**: account-first changes (Expo Go login, GitHub and passkey sign-in, OAuth MCP) plus public AE, TAM, BDR, and GTM Engineer roles show self-serve being paired with sales assist
- **Security story worth knowing**: SOC 2 Type 2 since December 2024, SSO on Production and above, robot users for scoped CI access, and end-to-end signed OTA updates
- **For GTM AI work (my analysis)**: the highest-value internal agents at a company like this route usage signals to people, deflect repeat support questions, and flag expansion, each with a scoped identity and a human gate on anything customer-facing

---

## Quick Reference

### Common CLI Commands

| Command | What It Does |
|---|---|
| `npx create-expo-app@latest` | Create a new Expo project |
| `npx expo start` | Start the local dev server |
| `npx expo install <package>` | Install a library at the version matched to your SDK |
| `npx expo prebuild` | Generate the native `ios` and `android` folders |
| `eas login` | Sign in to EAS from the CLI |
| `eas build --platform all` | Cloud build for iOS and Android |
| `eas submit --platform ios` | Upload the latest build to App Store Connect |
| `eas update --branch production --message "Fix typo"` | Publish an OTA update |
| `eas workflow:run .eas/workflows/<file>.yml` | Run a workflow manually |
| `npx expo export -p web` then `eas deploy` | Bundle and deploy a web app to EAS Hosting |
| `EXPO_TOKEN=<token> eas build` | Run an EAS command non-interactively in CI |

### Terms

| Term | Plain English |
|---|---|
| **EAS** | Expo Application Services, the paid cloud |
| **OTA update** | New JavaScript and assets delivered to installed apps without a store release |
| **MAU** | Monthly active users; EAS Update pricing counts users who receive updates |
| **Development build** | Your own debug app that includes your custom native code |
| **Expo Go** | Ready-made sandbox app for trying a project instantly |
| **Robot user** | Role-scoped, token-only account for CI and automation |

---

## Official References

| Source | Link |
|---|---|
| Expo | https://expo.dev |
| Expo: About | https://expo.dev/about |
| Expo: Pricing | https://expo.dev/pricing |
| Expo: Customers | https://expo.dev/customers |
| Expo: Careers | https://expo.dev/careers |
| Expo: AI | https://expo.dev/ai |
| Expo: Security and Compliance | https://expo.dev/security |
| Expo Changelog | https://expo.dev/changelog |
| PR Newswire: Expo Raises $45M Series B | https://www.prnewswire.com/news-releases/expo-raises-45m-series-b-and-launches-expo-agent-to-close-the-gap-from-idea-to-production-ready-mobile-apps-302744423.html |
| Expo Blog: What Expo's Series B Means for You | https://expo.dev/blog/what-expo-s-series-b-funding-means-for-you |
| Expo Blog: Seth Webster Joined Expo | https://expo.dev/blog/seth-webster-joined-expo |
| The New Stack: Expo Bets Big on React Native's Agentic Future | https://thenewstack.io/expo-bets-big-on-react-natives-agentic-future/ |
| Y Combinator: Expo Company Profile | https://www.ycombinator.com/companies/expo |
| Wikipedia: Charlie Cheever | https://en.wikipedia.org/wiki/Charlie_Cheever |
| Expo Blog: Bolt and Expo Integration | https://expo.dev/blog/bolt-expo-integration-announcement |
| Expo Blog: Introducing Expo Launch | https://expo.dev/blog/introducing-expo-launch |
| Expo Changelog: Expo Agent Wind-Down | https://expo.dev/changelog/expo-agent-ending-the-closed-beta-and-winding-the-project-down |
| Expo Changelog: MCP Server on the Free Plan | https://expo.dev/changelog/the-expo-mcp-server-is-now-available-on-the-free-plan |
| Expo Changelog: Connect Expo in Claude | https://expo.dev/changelog/connect-expo-in-claude |
| Expo Changelog: EAS Observe GA | https://expo.dev/changelog/eas-observe-is-now-generally-available |
| Expo Changelog: SDK 58 Beta | https://expo.dev/changelog/sdk-58-beta |
| Expo Docs: EAS Overview | https://docs.expo.dev/eas/ |
| Expo Docs: MCP Server | https://docs.expo.dev/mcp/ |
| Expo Docs: Skills | https://docs.expo.dev/skills |
| Expo Docs: EAS Update | https://docs.expo.dev/eas-update/introduction/ |
| Expo Docs: EAS Update Code Signing | https://docs.expo.dev/eas-update/code-signing/ |
| Expo Docs: EAS Workflows | https://docs.expo.dev/eas/workflows/introduction/ |
| Expo Docs: EAS Hosting | https://docs.expo.dev/eas/hosting/introduction/ |
| Expo Docs: Environment Variables | https://docs.expo.dev/eas/environment-variables/ |
| Expo Docs: Programmatic Access | https://docs.expo.dev/accounts/programmatic-access/ |
| Expo Blog: EAS SOC 2 Type 2 | https://expo.dev/blog/eas-soc2-type2 |
| React Native Blog: Use a Framework to Build React Native Apps | https://reactnative.dev/blog/2024/06/25/use-a-framework-to-build-react-native-apps |
| Linux Foundation: React Foundation Announcement | https://www.linuxfoundation.org/press/linux-foundation-announces-intent-to-launch-the-react-foundation |
| Microsoft CodePush Repository (Retirement Notice) | https://github.com/microsoft/code-push |
| Expo on npm | https://www.npmjs.com/package/expo |
