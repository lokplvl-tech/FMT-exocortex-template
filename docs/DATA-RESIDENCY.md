# Personal Data Residency in IWE

> Date: 2026-07-11 · Status: template principle (WP-475)

**If you arrived here from [DATA-POLICY.md](DATA-POLICY.md):** that document covers data the **platform** collects about you (profile, progress, digital twin). This document covers data **you** bring into your IWE from external sources (health, calendar, working hours) and defines where that data may and may not flow.

---

## 1. Principle

Data you bring into your IWE perimeter does not leave it without your explicit consent. Reading data collected by the platform into your IWE is normal and does not require separate permission each time. The question is not where IWE reads data from, but where the outgoing flow may go. All computation and generation based on your data happens on your IWE side, not on the platform.

**"Residency" here is not a geographic data location** (not a server jurisdiction, as in the industry term data residency) — **it is a control rule**: data you bring into your IWE perimeter does not leave it without explicit consent. The term is borrowed from another domain and redefined here.

**"IWE perimeter"** is not a physical location and not a trust level assigned to a service. It is a question of substrate: the perimeter is wherever the tree of your personal IWE is physically versioned (`memory/`, `extensions/`, `params.yaml`, your strategy). This means your local machine plus your private git hosting (GitHub, GitLab, self-hosted — any provider). Everything else — platform Neon, Railway, WakaTime, and other services — is not IWE substrate. These are external points: some you may read from (incoming flow, always permitted); some you may send data to with explicit consent (outgoing flow, requires opt-in).

Example: the digital twin in Neon is not part of the perimeter, even if IWE reads it regularly (incoming flow — permitted). Your private git repository is part of the perimeter, because it is the storage location for the IWE tree, not a destination for data.

> Terminology note: [DATA-POLICY.md §2](DATA-POLICY.md#2-где-хранятся-данные) labels the server-side platform component as "IWE (server side)" in one table alongside your personal files. In this document, "IWE" refers only to your personal instance — the platform is separate.

---

## 2. Three-Layer Model

Pilot decision, 10.07.2026:

| Layer | What it provides | What it does not do |
|-------|-----------------|---------------------|
| **Platform** | Collects its own data about your activity inside the platform (courses, diagnostics, events) and delivers it to your IWE (incoming flow) | Never acts as a transit point or storage for your local data |
| **IWE template** | Provides the mechanism (data need declaration + consent + skill inventory) and ready-made recipes for popular sources | Does not prescribe a specific method for exporting data |
| **User** | Decides and performs the data export personally — using a template recipe, a custom Script, or manually | — |

Exporting data from devices and clouds is always your own action. Neither the platform nor the template transfers data on your behalf.

---

## 3. Types of Personal Data

Source: the post "Everyone has an all-knowing AI, but only those who built it themselves have a useful one" (six information types, four of which are personal):

| Type | Description | Typical location |
|------|-------------|-----------------|
| **2.1** | Stable facts about you (profile, goals) | Partly platform (incoming flow to IWE), partly your local notes |
| **2.2** | Operational event stream (health, working hours, activity) | Typically a third-party device/service → your local IWE |
| **2.3** | Formalized personal knowledge (your Pack) | Your git hosting |
| **2.4** | Non-formalizable personal practice (decision log, intuition) | Your git hosting (sessions, `memory/`) |

---

## 4. Third-Party Cloud — Two Distinct Cases

Infrastructure that is neither the platform nor your IWE substrate (see §1) is also an external point and also requires consent for outgoing flow. However, it covers two distinct cases with different risk profiles:

| Subtype | Example | Who controls the infrastructure | Consent |
|---------|---------|--------------------------------|---------|
| **PaaS under your control** | Health data receiver on Railway | You (your account, your instance, deletable at any time) | Required — data physically leaves your device, even if the infrastructure is "yours" |
| **SaaS aggregator** | WakaTime | Third-party service — you do not control the processing | Required — same principle, higher risk: no control over how the service uses your data downstream |

Both cases represent outgoing flow and require explicit consent. A more granular consent strictness model (for example, different UX for the two subtypes) is a question for the implementation Phase, not this document.

---

## 5. Data Source Recipe Format

Specific data sources are defined as template extensions (`extensions/`). The general pattern and data need declaration schema are the subject of a separate Phase. A draft example has already been outlined in one of the WP-475 sessions.

---

## 6. Your Data Inventory

A Skill is planned to help you ask: what data of types 2.1–2.4 do you have, and where does it live — instead of manually designing an Integration for each source every time. Location: `.claude/skills/` in the template, alongside other inventory skills. The specific name and full implementation are the subject of a separate Phase.

---

## Out of Scope for This Phase

- **Back-reference from `DATA-POLICY.md`.** This document references `DATA-POLICY.md`, but not the reverse — `DATA-POLICY.md` is synchronized with an external Pack source (DP.D.035), and editing its content is a decision for the owner of that Pack document, not a task for this Phase.
- **Formal registration of the principle in the Pack** (draft identifiers `DP.SC.475-residency`, `DP.ROLE.475`) — an open question from the first Phase of WP-475, awaiting a pilot decision.
- **Consent mechanism (ResidencyGate)** — data need declaration, consent state, consent request trigger points — designed and passed architectural Assessment within WP-475, but implementation (code) is a separate Phase / child work item.

