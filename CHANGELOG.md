> English-only projection of the changelog: entries written
> in Russian are omitted by the publishing pipeline.

# Changelog

All notable changes to FMT-exocortex-template will be documented in this file.

Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
Versioning: [Semantic Versioning](https://semver.org/).



































































































### Added

- `d450902` feat(day-close): token-discipline execution model — digest + subagent phases (#234)
- `f4ca48e` feat(manifest): update-manifest.local.json — fork-local exclusions survive update.sh (#247)
- `c65f9d0` feat(WP-450 S-50): promote hot-files.list auto-discovery to FMT
- `33ebbf9` feat(WP-450): promote verify-context-budget.sh to FMT (S-50)
- `4bebc58` feat: complete gate-metrics.sh promotion — manifest coverage + changelog
- `dd011fa` feat(hindsight): deliver hindsight_trigger.py + hindsight_adapter.py, closing L2 integration gap (#252)
- `a7f5f9d` feat: promote 8 personal utility scripts to platform
- `695033d` feat(residency-gate): ResidencyGate full implementation
- `c286e98` feat: promote day-open-pipeline.sh to platform
- `e919c04` feat(update.sh): add --fast check mode, version-only comparison (#230)
- `34bcc57` feat(en-projection): community channels live on iwesys/IWE itself (pilot decision)
- `7eeee9e` feat(en-projection): EN distribution is self-contained — no RU-source references (pilot decision)
- `0a1de9a` feat(pack-creator,pack-new): seed/mature maturity marker + move .spf-state.yaml out of Pack tree
- `2381d7f` feat(wp-7): promote 6 day-open scripts + fix scaffold drift + seed new-user scripts
- `927808b` feat(wp-7): promote 6 day-open scripts + fix scaffold drift + seed new-user scripts
- `1c71664` feat: promote day-open-pipeline.sh entry point (WP-7 FMT-PROMOTE-DAYOPEN1)
- `c428393` feat(canon-sync): add iwesys/MimEcoSys publish jobs to translate-sync workflow
- `a100fa6` feat: promote iwe-bug-report.sh to platform (WP-5 sub-#3)
- `77e856c` feat(wp-415): sync glossary from iwe-translation-engine (18/78/30 tiers)
- `acf10e4` feat(wp-415): automate RU→EN translation sync with tier-based delivery tests
- `1d1d4fa` feat(wp-149): promote skill personal-guide-render v2.0.0 to platform (L1)

### Changed

- `d68413b` docs: regenerate [Unreleased] CHANGELOG after #234 promotion
- `a5697c3` docs: regenerate [Unreleased] CHANGELOG after #247 local-manifest feature
- `387dd77` docs: regenerate [Unreleased] CHANGELOG after issue sweep (#264/#240/#222/#223/#254/#234)
- `750eaf6` chore: remove __pycache__ .pyc from tree + gitignore (sync 238a5c1 garbage)
- `8e69322` docs: regenerate [Unreleased] CHANGELOG after #263 fix
- `806ba4c` docs(changelog): add cec81a3 (DayPlan follow-up to #248)
- `82b1cc8` docs(changelog): sync Unreleased section — #248/#251/#252 fixes, thank VxxxlBxxxxv
- `67571f3` docs(changelog): thank den317 for #247/#249/#250 reports
- `3c62228` docs(changelog): sync Unreleased section — #247/#249/#250 fixes
- `9f0f31c` docs(changelog): sync Unreleased section — scripts/ delivery fix (#247)
- `0fafee4` docs(changelog): sync Unreleased section — FMT issues #230-246 batch
- `65e5534` rename(canon-sync): target repo iwesys/iwe-template -> iwesys/IWE
- `bdb2c9b` docs(changelog): thank users for #229/#228 reports, sync Unreleased section
- `5b72787` rename(canon-sync): target repo iwesys/FMT-exocortex-template-en -> iwesys/iwe-template
- `5bce5e3` revert(canon-sync): drop MimEcoSys mirror job — wrong repo scope
- `b3ba993` refactor(translate): drop openai SDK dependency, call OpenRouter directly
- `901103d` docs: python3 in maintaining-skills snippets
- `c25790a` refactor(translate): switch provider to OpenRouter (reuse existing key, mirror enrich-glossary client)

### Fixed

- `1c62621` fix(day-close): language-tolerant postcondition patterns 9a/9b (#234)
- `5ab284f` fix(executor-catalog): VALID_EXECUTORS += agent, script+judgment (#222)
- `655d385` fix(setup,update): quote env values (#223) + merge-managed base↔remote detector (#254)
- `e67ca20` fix(dry-run-gate): restore #237 v2 matcher + whitelist read-only bash helpers (#264)
- `8a611bf` fix(validate-template): restore staged mode + dynamic TEMPLATE_DIR (sync 238a5c1 regression)
- `7e5be12` fix: resolve WP-REGISTRY schema drift cluster (#263)
- `fc763e4` fix(WP-450): promote missing checklists.md pointer + ailev↔IWE glossary
- `8b61285` fix(changelog): restore 0200a93 entry dropped by the auto-regeneration step
- `0e933ee` fix(audit-installation): mark github_status as subscription-gated
- `d55b855` fix(day-close): correct check-index-health.py path
- `51f30fc` fix(iwe-drift): resolve script: helpers relative to the template, not IWE_ROOT
- `b0d1fe0` fix(day-open-scaffold): resolve template-owned scripts locally, not via governance repo
- `40c2d70` fix(strategist): retire redundant day-plan scenario on non-strategy-days (WP-484)
- `7cbd225` fix: 3 template bugs from bot-flagged issue sweep (#253, #255, #256)
- `3703abd` fix(residency-gate): replace hand-rolled YAML parsing with real yaml library
- `9169115` fix(residency-gate): consistent package-relative imports
- `658cfde` fix(residency-gate): test assertion referenced stale example name
- `cec81a3` fix(hooks): DayPlan resolution had the same latest-on-disk bug as #248
- `2ea3510` fix(manifest): drop stale deprecated_files[] entry for docs/DATA-RESIDENCY.md (#251)
- `0bb38e5` fix(hooks): WeekPlan validator checks staged artifact, not latest-on-disk (#248)
- `ae960a2` fix(close-protocols): move final commit after knowledge-write steps (#249)
- `914a39b` fix(validate-template): checks 2/3 print same file types they count (#247)
- `e98f152` fix(gitignore): cover .claude/state/ — create-wp.sh consent-sentinels leave untracked tail (#250)
- `cd240eb` fix(script-promote.sh): bound smoke-test with 5s alarm, daemon scripts hung it forever
- `242ec42` fix(manifest): deliver scripts/ by default instead of blanket-excluding it (#247, root #246)
- `a5c6d0f` fix(day-open-scaffold): bound remaining unprotected network calls (#241 residual)
- `b0ad33b` fix(update.sh): git-based author_diverged() guard replaces path whitelist (#238)
- `65e6b76` fix(dry-run-gate): unified sentinel + command-split matcher closes 4 bypass holes (#237)
- `f37d93a` fix(exocortex): back up and restore extensions/, matching DATA-POLICY.md promise (#235)
- `b3b6a37` fix(week): remove phantom auto-publisher claim, fix day_num GNU-date fallback (#245)
- `a3d0b95` fix(day-open-scaffold): bound gh issue list calls with portable timeout (#241)
- `e0f5031` fix(strategy-session): wire load-extensions before/after hooks (#236)
- `cddc7aa` fix(seed): align WP-REGISTRY.md schema with create-wp.sh's 6-column output (#232)
- `3647e57` fix(memory-active-wp-update): fall back to nested FMT-exocortex-template/ layout (#242)
- `2b7109c` fix(dt-collect): read scheduler/reports, not scheduler/scheduler-reports (#243)
- `fa23ff0` fix(hooks): scope destructive-guard force detection to git push segment (#233)
- `b4a3fa9` fix(perms): restore executable bit on .claude/lib/frontmatter.sh
- `d234799` fix(manifest): restore executable bit for shell scripts (#239)
- `0f15820` fix(strategy): avoid false calendar and issue defaults in day plan (#238)
- `6a7a7b0` fix(hooks): harden dry-run gate git and cleanup handling (#237)
- `189b62a` fix(en-projection): install command on the EN side forks iwesys/IWE, not the RU source
- `a92471a` fix(en-projection): ONTOLOGY.md is bilingual by design — rewrite link instead of translating
- `b8f8d22` fix(en-projection): heal 3 broken README links on iwesys/IWE found by live audit
- `857cdad` fix(ontology): IWE abbreviation — Intellectual Work Environment (align with distinctions.md and README H1)
- `e4a23f0` fix(wp415): jq null-guard for per-commit added/modified/removed in translate-sync
- `4dea62e` fix(translate-sync): publish single attributed commits to iwesys, not en-draft's full history
- `040012c` fix(translate-sync): handle null github.event.commits on workflow_dispatch
- `1113cd0` fix(day-open): promote WP-5 VDV correction — snapshot refresh ordering + drop dead report step
- `41c20fe` fix(translate-sync): attribute EN commits to the human source author, not a bot
- `726fa80` fix(ci): restore scripts/iwe-bug-report.sh dropped from manifest by 7ae267a
- `7ae267a` fix(#229,#228): protect owner:user memory files from stale-repair, add hot-budget validator
- `c828396` fix(canon-sync): persist-credentials false on en-draft checkout
- `8562439` fix(translate): strip <body> markers unconditionally, detect output truncation
- `791df86` fix(translate-sync): stop rsync --delete mirror from wiping en-draft
- `702244e` fix(translate): exclude blank fill-in templates from auto-translate
- `e8c6d2e` fix(translate-sync): push HEAD:en-draft for detached worktree, tolerate ASCII-guard warnings, add manual dispatch
- `60e3591` fix(#226): CLAUDE.md conflict no longer aborts update.sh mid-delivery
- `1f00b75` fix(#225,#224): create-wp.sh legacy WP-N regex + archive-done-wp.sh git mv -f
- `93828f4` fix(ci): register .claude/templates/ in delivery contract
- `53c9711` fix: cold-review findings on #217/#220 — sed & escaping, WP-N without bold
- `4eb05e2` fix(#217): CLAUDE.md/AGENTS.md exocortex backup+restore is OS-agnostic
- `c26c0ae` fix(#218): CI catches renamed paths missing from deprecated_files[]
- `1d1a2d9` fix(#220): drift detector executes check:script + recognizes bold WP-id
- `b21d412` fix(#197): setup.sh generates executor-catalog.yaml on install
- `4458412` fix(#221): protocol-artifact-validate.sh accepts <summary> as section heading
- `ef3d728` fix(#192): enforce jq as required prerequisite in setup.sh
- `84858e4` fix(release): sync-version-badge.sh --fix broken on macOS BSD sed + README badge drift
- `b4d08a2` fix(v0.35.5): orphan-detection TypeError + DS-strategy validator + root detection (#214 #215)
- `212fa2f` fix(setup): include rules-lazy in dry-run and section message
- `b7d75a8` fix(template): verify-template-integrity mirrors CI contract+smoke jobs
- `0200a93` fix(template): close manifest drift + setup/update rules-lazy gap, wire parity gate


## [0.35.5] — 2026-06-30

### Fixed

- fix(#215): orphan detection TypeError — `set(dict_list)` → `_path()` helper + set comprehension (`update.sh` Python heredoc)
- fix(#215): bare `DS-strategy` literals in `update.sh` lines 306/533-544 → `${IWE_GOVERNANCE_REPO:-DS-strategy}` (no longer blocked by `validate-fmt-scripts.sh`)
- fix(#215): add `roles/strategist/WORKPLAN.md`, `.claude/hooks/wakatime-heartbeat.sh`, `.claude/skills/peer-conversation/modes.md` to `update-manifest.json deprecated_files` — suppresses false orphan warnings for removed platform files
- fix(#214): `iwe-env-bootstrap.sh` `.claude/` branch — inline `basename` check prevents `WORKSPACE_DIR` landing inside `FMT-exocortex-template` when bootstrap is sourced from `FMT/.claude/lib/`

## [0.35.4] — 2026-06-15

### Fixed


## [0.35.3] — 2026-06-01

### Added


### Notes


## [0.35.2] — 2026-06-01



### Notes


## [0.35.1] — 2026-06-01

### Added


### Notes













































## [0.35.0] — 2026-06-01



  Multi-platform KIMI_BIN auto-detect (macOS / Linux / Windows VS Code Code-extension paths + PATH + `KIMI_BIN` env override).




- `7e9aa78` feat(triage): post-2026-06-01 backlog cleanup infrastructure
- `dc18e90` feat(detection): MVP FMT critical/deadline issues alert (peer-session 2026-06-01-18) (#145)
- `43e8268` feat(WP-377): promote pack-creator + org-dev + spf-guard
- `f47bf49` feat(WP-348): promote apply-captures defer_until invariant to L1
- `b144b3a` feat(strategist): read weekly-digest.md as Loop C input
- `abca838` feat(hooks): pre-commit gates PROMOTE-DRY-RUN + CLEAN-ENV-SMOKE (PD-2/PD-1, WP-347)
- `a8eadab` feat(promote): promotion-status.yaml + record_promotion (PZ-6)
- `36285bc` feat(coverage): coverage-skills.sh — B12a/b/c/d detector (PZ-3)
- `ab2f461` feat(staging): staging-audit.sh — B12e decay detector (PZ-4)
- `d575a6b` feat(sync): extend template-sync allowlist (PZ-2)
- `2655dbb` feat(catalog): generate FMT skills-catalog.yaml (B12a artifact)
- `a9ee8ac` feat(memory): backfill protocol-month-close.md to FMT (B12c)
- `656262a` feat(rules): promote role-prefixes (S-15) to platform
- `3b1cd77` feat(skills): promote bottleneck-pick (S-42+S-46) to platform L1
- `2136de9` feat(WP-350): JSON output, routing-path-distribution audit, routing-errors.log
- `33cc31d` feat(WP-350): strict/flex routing + test suite (8 cases)
- `016833a` feat(week-close): add step 7a iwe-backup-check.sh before backup
- `836997c` feat: promote iwe-backup-check.sh to platform scripts
- `a4260e7` feat(day-open): scaffold PENDING markers + protocol-close WP archiving step
- `2136141` feat: settings-promote.sh + pre-commit HOOK-PATH-CONVENTION gate
- `333c83d` feat(strategist): complete runner migration — run_skill() for day-open/day-close/week-close/strategy-session

### Changed

- `33537d6` docs(promotion): B12 class + pair-on-promote convention (PZ-5)
- `c098042` ci(validate-template): add validate-fmt-scripts.sh to CI pipeline
- `a5b9aa8` docs(changelog): add 2c92438 warn() fix to Unreleased
- `f721eb0` chore(audit-installation): add SKILL.md frontmatter (version, layer, status, triggers)
- `af829fe` chore: sync headless-runner.sh
- `e77406c` chore: release 0.34.1
- `5b43a38` chore: release 0.34.0

### Fixed

- `f112f0d` fix: iwe-audit portability + release-audit-log.md (closes #24, #142) (#144)
- `575ae4e` fix(notify): make TEMPLATES_DIR overridable via environment (#49)
- `934e9c9` fix(verify): add model mapping for verification_class in wp type (#47)
- `4a00339` fix(dt-collect): replace hardcoded DS-strategy with $GOVERNANCE_DIR (#46)
- `065e60a` fix(day-close): portability — HOME_SLUG + rsync --delete (#119)
- `df591ea` fix(dry-run-gate): make sentinel discovery session-agnostic (closes #59) (#60)
- `bffd92c` fix(skill): quote pack-new description in SKILL.md frontmatter (#137)
- `c2e96e6` fix(promote): regenerate FMT skills-catalog.yaml (B12a)
- `143ca6a` fix(claude.md): restore IntegrationGate checklist items 1, 3
- `32e3607` fix(server-calendar): add utf-8 encoding declaration to Python heredocs
- `39ca8ea` fix(template): replace author-specific DS-my-strategy with placeholder
- `8676d68` fix(setup): auto-enable core.hooksPath for repos with .githooks/
- `ed67968` fix(validate): whitelist direct-call hooks + parametrize DS-strategy literal in iwe-audit
- `89367b4` fix(router): interpreter auto-detection + T13 agent-fault args
- `03515f0` fix(WP-350): explicit return 0 in all dispatch branches
- `4dd7cf2` fix(WP-350): llm_tokens field, 10 test cases, return consistency
- `8a3fa5d` fix(WP-350): audit-log on script failure, return exit code
- `8d51a01` fix(WP-350): audit-log calls, yaml check, args quoting, test rename
- `63503aa` fix(test-route-task): add || true to ((VAR++)) under set -e
- `27fecea` fix(validate-fmt-scripts): safe-pattern exclusions for detector false positives
- `457950b` fix(manifest): B2 coverage gap — add 3 orphan scripts to update-manifest.json
- `81e5727` fix: scaffold guard + D11 upgrade to FAIL
- `af3b15c` fix: remove stale deprecated entries + add detector 10 for runner/manifest cross-check
- `2c92438` fix(smoke-test): define warn() — undefined function broke Validate Template CI
- `ea7ead8` fix(dispatcher): race-condition after claude -p — git reset --hard before status commit
- `72f7572` fix: hook paths — $CLAUDE_PROJECT_DIR/ convention for all hook commands
- `e337183` fix(manifest): remove strategist prompts from deprecated_files — runner still uses them
- `5bffbc9` fix: replace hardcoded DS-strategy with GOVERNANCE_DIR/GOVERNANCE_REPO env vars


## [0.34.1] — 2026-05-21

### Fixed



## [0.34.0] — 2026-05-20

### Added

- `4c7bf32` feat(calendar): promote day-open + week-close skills — meeting/task split, week mode, bot QA restored
- `6df8f7a` feat(calendar): server-calendar.sh v2 — L3 template sync
- `c277672` feat(pack-ci): auto-install CI guard via pack-new + pack-ci-install.sh
- `72f7572` fix(WP-7): hook paths — $CLAUDE_PROJECT_DIR/ convention for all hook commands
- `2136141` feat(WP-7): settings-promote.sh + pre-commit HOOK-PATH-CONVENTION gate

### Fixed

- `d451166` fix(memory-active-wp-update): fallback to exocortex when runtime memory is read-only
- `0263a5a` fix(agent-inbox): add fetch+rebase before push in commit_and_push
- `767ad46` fix(dt-collect+templates): fix weekly multiplier parser + format note


## [0.33.0] — 2026-05-18

### Added

- `6970050` feat(WP-324): Agent Inbox 0.32.0 — pack-templates + dispatcher script
- `223fb5f` feat(WP-324): promote S-45 Agent Inbox — extensions/agent-inbox/
- `63aa96c` feat: changelog automation — changelog-append.sh + changelog-flush.sh + v0.31.0
- `4002819` feat: promote S-44 to L1 — Telegram reminders as platform rule (rule 8)

### Fixed

- `767ad46` fix(dt-collect+templates): fix weekly multiplier parser + format note
- `4db37fd` fix: rename S-43→S-44 (Telegram reminders) to avoid numbering conflict with Agent Fault Profile


## [0.32.0] — 2026-05-17

### Added


### Changed



- `223fb5f` feat(WP-324): promote S-45 Agent Inbox — extensions/agent-inbox/
- `63aa96c` feat: changelog automation — changelog-append.sh + changelog-flush.sh + v0.31.0
- `4002819` feat: promote S-44 to L1 — Telegram reminders as platform rule (rule 8)
- `4db37fd` fix: rename S-43→S-44 (Telegram reminders) to avoid numbering conflict with Agent Fault Profile

## [0.31.0] — 2026-05-17

### Added

- cross-platform path leaks detector (WP-5/WP-7 Stability-4)
- Secret Drift Detector: `iwe-grep-secret.sh` MVP + Railway GraphQL v2 cloud scan (WP-315)

### Fixed

- `load-extensions`: robust workspace resolution + BASH_SOURCE fallback
- `setup.sh`: `source ~/.iwe-paths` before role install + validate `WORKSPACE_DIR`

## [0.30.0] — 2026-05-11






## [0.29.32] — 2026-05-06





## [0.29.31] — 2026-05-06




## [0.29.30] — 2026-05-06






## [0.29.29] — 2026-05-06







## [0.29.28] — 2026-05-05





## [0.29.27] — 2026-05-05



## [0.29.26] — 2026-05-05




## [0.29.25] — 2026-05-04




## [0.29.24] — 2026-05-02

### Fixed — Architecture A: IWE_GOVERNANCE_REPO env var in launchd plist templates





## [0.29.23] — 2026-05-01




Commit: `150ed2c`

## [0.29.22] — 2026-05-01





Commit: `8e79aa0`

## [0.29.21] — 2026-04-30






Commit: `84dd6dc`

## [0.29.20] — 2026-04-29

### Fixed — protocol-close.md: pre-commit checks ambiguity (Eugene's report)



## [0.29.19] — 2026-04-29

### Fixed (sub-agent post-release verify 0.29.18)


### Added — Pack documentation (retro-fix IntegrationGate skip P10)


|----------|------|-----------|


### Verified

`integration-contract-validator.sh` → ✅ PASS (8/8)
`smoke-test-fresh-install.sh` → ✅ PASS (14/14)

## [0.29.18] — 2026-04-29





**3. Detector regex regression tests (item 3):**

**4. Scheduled adversarial audit workflow (item 4):**

**5. UX walkthrough prompt template (item 5):**

### Verified

`integration-contract-validator.sh` → ✅ PASS (8/8)
`smoke-test-fresh-install.sh` → ✅ PASS (14/14)
`test-detectors.sh` → ✅ PASS (1 fixture)



## [0.29.17] — 2026-04-29

### Fixed (sub-agent post-release verify 0.29.16 — 2 minor)

**SA-6 — `day-close after` orphan hook:**


### Verified

`integration-contract-validator.sh` → ✅ PASS (8/8)
`smoke-test-fresh-install.sh` → ✅ PASS (14/14)

## [0.29.16] — 2026-04-29







**Pre-commit hook (`.githooks/pre-commit`):**

**CI workflow (`.github/workflows/validate-template.yml`):**


### Verified

`integration-contract-validator.sh` → ✅ PASS (8/8)
`smoke-test-fresh-install.sh` → ✅ PASS (14/14)

## [0.29.15] — 2026-04-29




### Verified

`smoke-test-fresh-install.sh` → ✅ PASS (14/14)

## [0.29.14] — 2026-04-29




**SA-3 — validator regex gap:**

### Verified

`integration-contract-validator.sh` → ✅ PASS (8/8), `smoke-test-fresh-install.sh` → ✅ PASS (14/14).

## [0.29.13] — 2026-04-29







**RT-5 — `update-manifest.json` intersection `files ∩ deprecated_files`:**


### Verified

`integration-contract-validator.sh` → ✅ PASS (8/8), `smoke-test-fresh-install.sh` → ✅ PASS (14/14).

### Root cause


## [0.29.12] — 2026-04-28

### Fixed


## [0.29.11] — 2026-04-28

### Added


## [0.29.10] — 2026-04-28






**Verification:**
- macOS smoke (BSD): `iwe-drift.sh --top 5` + `iwe-audit.sh` PASS.
- `validate-template.sh` PASS.


## [0.29.9] — 2026-04-28





|------|-------|--------|
| `memory/protocol-open.md` | 1 | after |
| `memory/protocol-close.md` | 2 | checks, after |
| `.claude/skills/run-protocol/SKILL.md` | 3 (generic) | before, after, checks |
| `.claude/skills/day-open/SKILL.md` | 3 | before, after, checks |
| `.claude/skills/day-close/SKILL.md` | 4 (3 × `checks` + 1 × `before`) | before, checks |
| `.claude/skills/month-close/SKILL.md` | 2 | before, after |

```
```




### Why


## [0.29.8] — 2026-04-28



### Why


## [0.29.7] — 2026-04-27







### Why


## [0.29.6] — 2026-04-27



```bash
sed -e "s|{{GOVERNANCE_REPO}}|$_gov_repo|g" ...
```

```bash
```



```bash
sed -e "s|${_o}GOVERNANCE_REPO${_c}|$_gov|g" ...
```




### Why

## [0.29.5] — 2026-04-27





### Added (smoke test 9 → 11 + detector #6 → #7)


### Why

## [0.29.4] — 2026-04-27











### Why

## [0.29.3] — 2026-04-27





### Fixed (validator false positives)

### Changed (silent degradation guards)

### Why

## [0.29.2] — 2026-04-27




### Why

## [0.29.1] — 2026-04-27



### Why

## [0.29.0] — 2026-04-27







```bash
bash $IWE_TEMPLATE/scripts/migrate-to-runtime-target.sh
```

4. `git restore` FMT → clean upstream.

### Why

## [0.28.12] — 2026-04-27



### Why

## [0.28.11] — 2026-04-27



### Why

## [0.28.10] — 2026-04-26



### Why

## [0.28.9] — 2026-04-26

### Changed (validator hardening — `validate-template.sh` rule 6/6)


### Why

## [0.28.8] — 2026-04-26



### Why

## [0.28.7] — 2026-04-26



### Why

## [0.28.6] — 2026-04-26



### Why

## [0.28.5] — 2026-04-26



### Why


## [0.28.4] — 2026-04-26

### Fixed

### Added

### Why

## [0.28.3] — 2026-04-25

### Added

### Changed

## [0.28.2] — 2026-04-25

### Added

### Changed

## [0.28.1] — 2026-04-25

### Changed

### Fixed

## [0.28.0] — 2026-04-25

### Changed

### Fixed

### Meta

## [0.27.7] — 2026-04-24

### Fixed

## [0.27.6] — 2026-04-24

### Fixed


## [0.27.5] — 2026-04-24

### Changed

## [0.27.4] — 2026-04-24

### Fixed


## [0.27.3] — 2026-04-24

### Added

### Fixed

## [0.27.2] — 2026-04-23

### Fixed

## [0.27.1] — 2026-04-22

### Changed
- **`.claude/skills/ke/SKILL.md`, `memory/{repo-type-rules,protocol-open}.md`:** `DS-my-strategy` → `<governance-repo>` (env).

### Added

### Fixed

## [0.27.0] — 2026-04-21

### Added

### Changed

## [0.26.4] — 2026-04-18

### Added

### Fixed

## [0.26.3] — 2026-04-18

### Fixed

## [0.26.2] — 2026-04-17

### Fixed

## [0.26.1] — 2026-04-17

### Fixed

## [0.26.0] — 2026-04-17

### Added

### Changed

## [0.25.1] — 2026-04-14

### Changed

## [0.25.0] — 2026-04-13

### Changed

### Added

## [0.24.1] — 2026-04-13

### Fixed

## [0.24.0] — 2026-04-12

### Added

### Changed

## [0.23.1] — 2026-04-09

### Fixed

## [0.23.0] — 2026-04-07

### Added

### Changed

### Fixed

## [0.22.0] — 2026-04-06

### Added

### Changed
- **update-manifest.json** → v0.22.0

## [0.21.0] — 2026-03-29

### Added

### Changed
- **update-manifest.json** → v0.21.0

## [0.20.0] — 2026-03-29

### Added

### Changed
- **update-manifest.json** → v0.20.0

## [0.19.0] — 2026-03-29

### Added

### Changed

## [0.18.0] — 2026-03-28

### Added

### Changed

### Removed

## [0.17.1] — 2026-03-28

### Added

## [0.17.0] — 2026-03-28

### Changed

### Added

## [0.16.9] — 2026-03-28

### Added

## [0.16.8] — 2026-03-28

### Added

## [0.16.7] — 2026-03-27

### Fixed

## [0.16.6] — 2026-03-27

### Changed

## [0.16.5] — 2026-03-27

### Changed

## [0.16.4] — 2026-03-27

### Changed

## [0.16.3] — 2026-03-27

### Changed

## [0.16.2] — 2026-03-25

### Changed

## [0.16.1] — 2026-03-25

### Changed

## [0.16.0] — 2026-03-25

### Changed

### Added

### Updated
- collectors.d/README.md — unsatisfied → agent-workspace path

## [0.15.2] — 2026-03-24

### Changed

## [0.15.1] — 2026-03-24

### Fixed

## [0.15.0] — 2026-03-24

### Changed

### Added

## [0.14.2] — 2026-03-24

### Changed

## [0.14.1] — 2026-03-24

### Changed

## [0.14.0] — 2026-03-24

### Added

## [0.13.5] — 2026-03-22

### Changed

## [0.13.4] — 2026-03-22

### Added

## [0.13.3] — 2026-03-21

### Fixed

## [0.13.2] — 2026-03-21

### Changed

### Fixed

## [0.13.1] — 2026-03-21

### Fixed

## [0.13.0] — 2026-03-20

### Added

## [0.12.0] — 2026-03-20

### Added

### Changed

## [0.11.1] — 2026-03-20

### Changed

## [0.11.0] — 2026-03-20

### Changed

### Added

## [0.10.0] — 2026-03-19

### Changed

### Added

## [0.9.1] — 2026-03-18

### Added

## [0.9.0] — 2026-03-18

### Added

## [0.8.8] — 2026-03-18

### Added

## [0.8.7] — 2026-03-17

### Added

## [0.8.6] — 2026-03-17

### Added

## [0.8.5] — 2026-03-17

### Added

## [0.8.4] — 2026-03-17

### Added

## [0.8.3] — 2026-03-17

### Added

## [0.8.2] — 2026-03-17

### Added

## [0.8.1] — 2026-03-16

### Added

## [0.8.0] — 2026-03-16

### Added

### Changed

## [0.7.0] — 2026-03-16

### Added

## [0.6.4] — 2026-03-16

### Fixed

## [0.6.3] — 2026-03-16

### Fixed
- **Cross-platform compat:** `sed -i ''` → `sed_inplace` (setup.sh, update.sh) — GNU sed (Linux)
- **Cross-platform compat:** `date -v` → `portable_date_offset` (fetch-wakatime.sh, dt-collect.sh, scheduler.sh) — GNU date (Linux)
- **Cross-platform compat:** `osascript` → fallback notify-send (strategist.sh, extractor.sh) — Linux desktop

### Added

## [0.6.2] — 2026-03-16

### Added

### Changed


## [0.6.1] — 2026-03-15

### Changed

### Added

## [0.6.0] — 2026-03-14

### Added

### Changed
- **repo-type-rules** — DS-ecosystem-development = governance + staging for Pack

### Fixed

## [0.5.0] — 2026-03-10

### Added

### Fixed

### Changed

## [0.4.0] — 2026-03-01

### Added

### Fixed

## [0.3.0] — 2026-02-16

### Added

## [0.2.0] — 2026-02-09

### Added

## [0.1.0] — 2026-01-27

### Added
