# Creating a Pack: From Zero to a Working Knowledge Base

> Pack — a Repository with formalized knowledge of a Domain.
> It is the single source-of-truth for domain knowledge in IWE.
> Source-of-truth for the creation process: [SPF](https://github.com/TserenTserenov/SPF)

---

## Why You Need a Pack

Without a Pack, Claude has no knowledge of your Domain's specifics each time — terms, Methods, failure modes. With a Pack, that Knowledge loads into context automatically.

The generative chain (details: [principles-vs-skills.md](principles-vs-skills.md)):

```
FPF (мета-онтология)  →  SPF (фреймворк Pack)  →  Pack (домен)  →  DS (реализация)
```

A Pack lives between SPF and DS: SPF defines the structure, Pack fills it with domain Knowledge.

---

## Step 0: Distinguish a Domain From a Topic

A Pack is created for a **Domain**, not a topic.

| Domain | Topic (not for a Pack) |
|--------|------------------------|
| ML systems development | Machine learning |
| Systems analysis | Systems Thinking |
| Product management | Product thinking |
| Technical API design | REST API |

**Test:** are there people who DO this professionally? What do they produce (Artifacts)?
If yes — it is a Domain. If you just "find it interesting" — it is a topic.

---

## Quick Start: `/pack-new`

Type in Claude Code:

```
/pack-new
```

or simply: **"I want to create a pack"**, **"new pack on topic X"**, **"create a Pack for Y"**.

The Skill will guide you through 5 steps:

| Step | What happens |
|------|--------------|
| 0 | Checks for FPF and SPF — clones them if needed |
| 1 | 3 questions: who practices? what do they produce? how do they fail? |
| 2 | Proposes 2–3 name options → you choose |
| 3 | Fills in the Bounded Context (what is in scope / out of scope / terms) |
| 4 | Creates the `PACK-{slug}/` structure with starter files |
| 5 | Shows the Roadmap for populating phases P1–P6 |

---

## Pack Structure

```
PACK-{slug}/
├── README.md                      # Name + one-line description of the Domain
├── REPO-TYPE.md                   # Type: Pack, upstream: FPF + SPF
├── CLAUDE.md                      # Instructions for the agent
├── 00-pack-manifest.md            # Metadata + entity index
├── ontology.md                    # Domain terms (Ubiquitous Language)
├── 01-domain-contract/
│   ├── 01A-bounded-context.md     # What is in scope / out of scope / terms
│   └── 01B-distinctions.md        # Key Distinctions (A.7 FPF)
├── 02-domain-entities/            # Roles, Methods, WPs — enumeration only
├── 03-methods/                    # Method practice cards
├── 04-work-products/              # Work Product cards
├── 05-failure-modes/              # Typical errors and signals
├── 06-sota/                       # State of the Domain (optional)
└── 07-map/                        # Map of relationships between entities
```

Template: [SPF/pack-template](https://github.com/TserenTserenov/SPF/tree/main/pack-template)

---

## Pack Naming

**Formula:** `PACK-{slug}` where slug is a domain noun in Latin characters, kebab-case.

**Name criteria (all required):**
1. Specific: excludes neighboring Domains (`product-management`, not `management`)
2. Broad: covers the core Methods, not a single tool (not `jira`)
3. Recognizable: a Practitioner immediately understands what it covers

**Examples:** `PACK-product-management`, `PACK-system-analysis`, `PACK-technical-writing`

**Anti-examples:** `PACK-everything`, `PACK-jira`, `PACK-notes`, `PACK-ideas`

---

## What to Do After Creation: the P1–P6 Roadmap

A Pack is not filled in a single session. Population is Iterative.

**Phase order by value:**

| Phase | File | Purpose | Time | Priority |
|-------|------|---------|------|----------|
| **P1. Distinctions** | `01B-distinctions.md` | 7–10 "X ≠ Y" pairs for the Domain (FPF A.7) | 1–2h | First — without it, everything else is unreliable |
| **P2. Entities** | `02-domain-entities/` | Roles, WPs, Methods — enumeration only | 1–2h | Second — provides the map |
| **P3. Methods** | `03-methods/` | Inputs, outputs, quality criteria | 2–4h | Third — the core of the Pack |
| **P4. Work Products** | `04-work-products/` | Artifacts + Definition of Done | 1–2h | Fourth |
| **P5. Failure modes** | `05-failure-modes/` | 5–10 FMs: cause + signal | 1h | High value, often skipped |
| **P6. SoTA** | `06-sota/` | Sources, Knowledge version | 1–2h | Last, optional |

**Principle:** start with P1 (Distinctions). The first 5 Distinctions already deliver value — Claude stops confusing Domain terms.

---

## How to Populate a Pack During Work

You do not need to fill a Pack from scratch in a single session. The right approach is to capture Knowledge as you work:

```
Found a pattern or Distinction → /ke → Capture: [what] → PACK-{slug}/01B-distinctions.md
```

**The `/ke` command (Knowledge Extraction):**
- Call it at a Work milestone or when an important Distinction is found
- Claude announces: "Capture: [what] → [where]"
- When 5+ captures accumulate — run `/apply-captures`

---

## The Relationship Between a Pack and DS

A Pack contains **"what this is"** (domain Knowledge).
DS contains **"how we do it"** (implementations, code, plans).

```
Pack-{slug}/03-methods/           ← the Method as such (Domain)
DS-{проект}/docs/how-we-do-X.md  ← how this Method is implemented for us
```

Do not store in a Pack: code, configs, plans, registries. Those go in DS.
Do not store in DS: definitions, Distinctions, Methods, failure modes. Those go in a Pack.

---

## Further Reading

| Resource | What |
|----------|------|
| [SPF/process/](https://github.com/TserenTserenov/SPF/tree/main/process) | Detailed instructions for all 11 stages |
| [SPF/pack-template/](https://github.com/TserenTserenov/SPF/tree/main/pack-template) | Templates for each Pack file |
| [LEARNING-PATH.md §6](LEARNING-PATH.md) | Principles and frameworks: FPF, SPF, Pack |
| [principles-vs-skills.md](principles-vs-skills.md) | Why a Pack matters more than Skills |
| `/fpf` in Claude Code | Verify entity correctness against FPF |