<body>
# Script Promotion: L3 (author) → L1 (universal)

> Process for moving a script from the author zone (`WORKSPACE/scripts/`) into the FMT
> template (`FMT-exocortex-template/scripts/`), from which `update.sh` delivers it to all pilots.
> Source: WP-5 #12, DP.KR.001 §5.6.

## When to Promote

Promotion is appropriate when a script:
- has run in the author's IWE for ≥2 weeks without significant changes
- has universal value (not tied to the author's personal data)
- is parameterizable via `WORKSPACE_DIR` + `params.yaml` (or environment variables)

Do not promote a script that:
- references personal repositories (e.g., the author's governance repo)
- is a one-off script with no plans for repeated execution
- contains author-specific constants that cannot be extracted into a parameter

## 7-Step Process

### Step 1. Check for Collisions

```bash
~/IWE/FMT-exocortex-template/scripts/check-script-collisions.sh
```

If a script with the same name already exists in FMT, resolve the collision: merge (keep
one version) or rename (if both functions are needed). Skipping this step will break
behavior for pilots who already have the script.

### Step 2. Parameterize Author-Specific Constants

| Author constant | Universal pattern |
|---------------------|-----------------------|
| `$HOME/IWE` | `${WORKSPACE_DIR:-$HOME/IWE}` |
| `$HOME/IWE/PACK-personal` | `params.yaml` → user key |
| Personal paths (governance, knowledge-index) | `params.yaml` parameter + graceful skip if empty |
| WakaTime CLI path | `${WAKATIME_CLI:-$HOME/.wakatime/wakatime-cli}` |
| FMT path | `${FMT_PATH:-${WORKSPACE_DIR}/FMT-exocortex-template}` |

Rule: the script reads parameters from `${WORKSPACE_DIR}/params.yaml`. If a required
parameter is absent, the script prints a message and runs `exit 0` (no failure).

### Step 3. Add the Parameter to FMT/params.yaml

If the script requires a new parameter, add it to `FMT-exocortex-template/params.yaml`
with a default value (typically an empty string) and a comment explaining its purpose.

### Step 4. Copy into FMT

```bash
cp WORKSPACE/scripts/my-script.sh FMT-exocortex-template/scripts/my-script.sh
chmod +x FMT-exocortex-template/scripts/my-script.sh
```

### Step 5. Register in update-manifest.json

Add an entry to `FMT-exocortex-template/update-manifest.json`:

```json
{
  "path": "scripts/my-script.sh"
}
```

The list is ordered lexicographically by `path` — insert at the correct position.

### Step 6. Update the Manifest Version and CHANGELOG

In `update-manifest.json`, increment `version` (semver: a new script = minor bump).
In `CHANGELOG.md`, add an entry for this version.

The pre-commit hook `.githooks/pre-commit` checks that the manifest and CHANGELOG versions
are consistent — a commit without a bump will be blocked.

### Step 7. Smoke Test and Commit

```bash
# Smoke test 1: script runs without params.yaml (graceful skip)
bash FMT-exocortex-template/scripts/my-script.sh

# Smoke test 2: with params.yaml — performs the expected action
WORKSPACE_DIR=/tmp/test-iwe bash FMT-exocortex-template/scripts/my-script.sh

cd FMT-exocortex-template
git add scripts/my-script.sh params.yaml update-manifest.json CHANGELOG.md
git commit -m "feat: promote my-script.sh from staging"
git push
```

## Removing the Author Version (After Promotion)

If the script has **no** additional author-specific logic on top of the universal version,
delete it from `WORKSPACE/scripts/`. The next `update.sh` run will deliver the FMT version
back to `WORKSPACE/scripts/` — a single source of truth.

If the author has **additional logic** (e.g., a wrapper with author-specific arguments),
rename the author version to avoid a collision when the universal version arrives.

## Rollback

Run `git revert` on the promotion commit. The next `update.sh` run on pilot machines will
restore the previous state. The parameter in `params.yaml` remains (harmless, unused).

## The Validator Golden Rule

> **"If you depend on the validator, test it against real data in `env -i` before committing."**

This is the root cause of B4-class bugs (clean-env blind spots, 20 May 2026): a script works
for the author (the author's `IWE_GOVERNANCE_REPO` overrides the default) but breaks for
other users in a clean environment. If you modify `validate-fmt-scripts.sh` or
`integration-contract-validator.sh`, run the following check:

```bash
env -i HOME="$HOME" PATH="$PATH" \
    bash scripts/validate-fmt-scripts.sh scripts/
```

`hook-promote.sh` and `script-promote.sh` already include this check during promotion.
For a direct `git commit`, running it manually is your responsibility.

## Relation to Rules

- **DP.KR.001 §5.6** — classification of scripts as Role Performers
- **DP.D.048** — Script ≠ Agent (deterministic flow)
- **DP.D.049** — Log ≠ Incident ≠ State file (execution Artifacts)
- **§9 CLAUDE.md** — author mode (`params.yaml: author_mode: true`)
- **Extensions Gate** — user customization only through `extensions/`

---

## Bug Class B12: Promotion Completeness Drift

> Source: peer Sessions 2026-05-29-15 and 2026-05-29-20. WP-347 addressed "how to deliver" (release mechanism). B12 addresses "what to deliver and when" (promotion governance). Orthogonal scope.

5 subclasses:

| ID | Name | Symptom | Detector | Fix |
|----|-----|---------|----------|-----|
| **B12a** | **Catalog drift** | `skills-catalog.yaml` in FMT is stale: a new skill was promoted but does not appear during discovery | `coverage-skills.sh --check-catalog` | `skill-promote.sh` now regenerates the FMT catalog (commit c2e96e6) |
| **B12b** | **Missing drift** | Artifact exists in author/.claude/skills/, absent from FMT/.claude/skills/ | `coverage-skills.sh --check-missing` | Run `skill-promote.sh <name>` |
| **B12c** | **Reverse drift** | Artifact was promoted once; updates in author do not reach FMT | `coverage-skills.sh --check-reverse` (normalize before diff) | Extended `template-sync.sh` allowlist (commit d575a6b) |
| **B12d** | **Deletion drift** | Artifact deleted in author, still present in FMT (dead code in template) | `coverage-skills.sh --check-deletion` | Manual cleanup on signal + log in `promotion-status.yaml` |
| **B12e** | **Decay drift** | STAGING.md entry with status `testing` for >30 days, no machine-readable readiness criteria | `staging-audit.sh` | Per-row frontmatter `decay_after` / `ready_signals` |

## Pair-on-Promote Convention (B12 Prevention)

> Source of truth: a promotion record lives as a **pair**: STAGING.md (decision) + `promotion-status.yaml` (execution).

**When promoting a script, skill, or rule:**

1. **STAGING.md row → status: promoted**
   - Fields: `id`, `name`, `artefact_path`, `status`, `promoted_at`, `promoted_in_session`
   - If the row did not exist before promotion, create it (for post-hoc documentation)

2. **`promotion-status.yaml` append** (via `promote-common.sh::record_promotion()`)
   - Fields: `artifact_path`, `type` (skill|script|hook|rule|protocol), `source_sha` (author commit), `fmt_sha` (FMT commit), `promoted_at` (ISO-8601), `verified_in_clean_env` (bool)

3. **A clean-env smoke check is required** for scripts and skills with executable content:
   - `verified_in_clean_env: true` — passed `env -i` smoke test (see §B4 above)
   - `verified_in_clean_env: false` — acceptable for read-only artifacts (docs, rules)

**Prohibited:**
- Promoting without a STAGING.md entry (exception: emergency hotfix — create the entry retroactively within 24 hours)
- Running a promote script without reviewing the `--dry-run` diff before applying
- Pushing to FMT main without CI green (validate-template, integration-contract-validator)

**Related scripts:**
- `scripts/coverage-skills.sh` — detector for B12a/b/c/d
- `scripts/staging-audit.sh` — detector for B12e
- `scripts/promote-common.sh::record_promotion()` — writer for promotion-status.yaml
- **RELEASE-PROCESS.md** — release checklist + `deprecated_files` convention

</body>