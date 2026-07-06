<body>
# Where to Start as an IWE Developer

> **This is the only reference a newcomer needs.** Read top to bottom — in 10 minutes you will understand what to do and complete your first task.

Development in IWE follows a **Pipeline of 6 stations** (Formulation → Opening → Design → Work → Verification → Closing — details in the [«Task Cycle»](#task-cycle-6-stations) section below and in the [guide](developer-guide.md)). Each task travels from formulation to closing, and the output is not just code but also captured Knowledge (this is called the **dual output**). You are a T4+ developer — pick up a task card, move through the stations, and submit a Pull Request for Review.

## Your Role in This System

There are two ways to contribute to the Platform. Do not confuse them:

- **Leave a comment** (users T1–T3 do this) — submit a bug or idea, and someone else decides what to do with it. You do not touch the code.
- **Do the work** (you, T4+) — pick up the card yourself, write the code and Knowledge yourself, submit the Pull Request yourself. Your work merges into the Platform.

In short: some people **say what to fix**, you **fix it**. That is the difference between a volunteer leaving a comment and a team developer.

## Your First Day — 3 Steps

1. **Understand the rules.** Read the [developer guide](developer-guide.md) — it covers all 6 stations on one page, explains what dual output is, and identifies who accepts your code. 5 minutes.
2. **Get the task Template.** Copy the [card Template](card-template.md) into your task folder and fill it in: what you are doing, what will appear in the code, what Knowledge you will capture.
3. **Go through the 6 stations and submit a Pull Request.** The card guides you through the stations. The output is code + capture (a Distinction or a note in Memory). The lead developer accepts the Merge.

## Do This Inside Your IWE

You do not need to run the Pipeline manually. You run it **inside your own IWE** — your workspace with an agent (Claude or Kimi), Memory, and Protocols. Set it up once, and the agent will guide you through the stations on its own.

1. **Set up your IWE.** Run the Template setup (`bash setup.sh`). You will get: an agent, instructions, this guide, and a task card Template — locally, under your account. All team developers use the same Template, so everyone speaks the same language.
2. **Load the team's working Repositories.** Clone into your workspace (`~/IWE/`) the Repositories where you will work on tasks: the Service code and the Knowledge base (Pack). Without them the agent has nowhere to work. Before each task the agent pulls the latest version (`git pull`) so you are not editing stale code. When working in a shared Repository with others, the agent marks your active files to prevent conflicts. **If you are improving the Template itself** (not the team's product), the target Repository is your fork of `FMT-exocortex-template` — no separate Service needs to be cloned.
3. **Open a task through the agent (WP Gate).** Tell the agent what you are doing. It will run the Opening ritual itself: declare the Role, Work, Verification class, Assessment, and Model, then wait for your confirmation. This is the Opening station.
4. **The agent guides you through the stations.** It knows the framework from its own instructions (OWC — Opening/Work/Closing, WP Gate, dual output). For the full 6-station scheme it reads the [guide](developer-guide.md) — ask it to read the guide at the start of work so it does not skip Verification and does not forget the capture. You write the code; the agent assists and checks.
5. **Knowledge accumulates in your Memory.** Every Distinction, lesson, and note (capture) goes into your exocortex (IWE's external Memory). Nothing is lost between tasks — the agent will recall it next time.
6. **Before the Pull Request — agent-run check.** It will run the checklist or tests for the Verification class. When everything passes, submit the Pull Request.

> **The key point:** your IWE is not a code editor — it is a workspace that remembers your work and maintains Pipeline Discipline for you. The more tasks you complete, the smarter your personal Memory becomes.

## What to Read (As Needed)

| Document | Purpose |
|----------|---------|
| [Developer guide](developer-guide.md) | Essential: 6 stations, dual output, WP Gate, who merges. Read **first**. |
| [Task card Template](card-template.md) | Copy and fill in for your task. |
| [T0–T4 tier path](../LEARNING-PATH.md) | If you do not know your access tier — start here. |
| Developer Roles (full definitions are in the team Pack, `DP.ROLE.068`–`072`, **available to members only**) | In brief: the Formulator defines the task and acceptance criteria; the Architect selects the Method and fits the solution into the Template; the Executor writes the code and capture. Pack codes do not resolve for external forkers — the summary above is sufficient. |
| Pipeline promise (`DP.SC.171`, team Pack, **members only**) | The contract: what the Pipeline guarantees and how user feedback is handled. External forkers do not need this to work. |
| Example of a completed card (`inbox/tasks/` in the team workspace) | Shows what a finished card looks like — use it as a reference. (External forkers do not have access to the team workspace — use the [Template](card-template.md) instead.) |

## Task Cycle (6 Stations)

**Formulation → Opening → Design → Work → Verification → Closing.**

Each station is described in detail in the [guide](developer-guide.md). In brief: define the task → confirm with the pilot (WP Gate) → design → write the code **together with** a Knowledge record → check against the Verification class → submit a Pull Request and merge.

**Dual output is mandatory.** A task that produces code without a captured Knowledge record is considered **unclosed**.

When you open a Pull Request, a Template with the 6-station checklist will be inserted — fill it in honestly. The reviewer uses it to immediately see that the Pipeline was completed.

## Entry Barrier and Who Accepts Code

- The Pipeline is for **T4+** developers. If your level is lower, the path forward is described in [LEARNING-PATH.md](../LEARNING-PATH.md) (those are development programs, not this Pipeline).
- **Only** the lead developer (TD1+TA4) or the pilot accepts a Merge. No one else — without explicit delegation.
- Stuck longer than the estimate? Do not stall silently — escalate to the lead developer or pilot.

---

*Related documents: [developer guide](developer-guide.md), [card Template](card-template.md), [tier path](../LEARNING-PATH.md). Roles and the Pipeline promise (`DP.ROLE.068`–`072`, `DP.SC.171`) live in the team Pack — available to members only; external forkers do not need them to work (role summaries are in the table above and in the «Your Role in This System» section).*
</body>