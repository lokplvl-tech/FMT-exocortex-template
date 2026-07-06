# FMT-exocortex-template Release Process

> Who bumps the template version, when, and how. Goal: a clear "ready to release" criterion
> instead of a verbal agreement. Source: WP-347 Ф3, 22 May 2026.

## What "release" means

`update.sh` downloads files from `raw.githubusercontent.com/main` — no tags, no staging branch.
Any commit to `main` becomes immediately available to users on the next `bash update.sh`.

**Version** in `update-manifest.json["version"]` serves as an informational label — displayed
at `bash update.sh` startup as "Exocortex updates (vX.Y.Z)", and also downloaded
with `--check` from the remote manifest for comparison with the local version. A version bump = a signal
that "this set of changes is stable, time to update."

---

## Version bump readiness criteria

All items must be completed:

- [ ] CI is green (`Validate Template` + all jobs)
- [ ] No open hotfix branches (`git branch --list 'hotfix/*'` — empty)
- [ ] CHANGELOG.md is complete: the `[Unreleased]` section is not empty, no "TODO" lines
- [ ] All new files are added to `update-manifest.json["files"]`
  (`git ls-files | python3 scripts/check-manifest-coverage.py update-manifest.json`)
- [ ] `deprecated_files` follows the convention (see "deprecated_files Convention" below)
- [ ] fix commits since the last bump ≤5 (if >5 → mandatory instability Review, see "Stability Metric" section)

---

## Stability Metric

The number of fix commits since the last version bump serves as a proxy metric for codebase stability. A threshold of ≤5 means accumulated instability is not yet critical and the release can proceed without additional Review. Exceeding the threshold requires an explicit risk Assessment.

```bash
# Count fix commits since the last version bump
# Branch A — tags exist (normal path):
LAST_TAG=$(git tag --list 'v*' --sort=-v:refname | head -1)
if [ -n "$LAST_TAG" ]; then
  COUNT=$(git log "$LAST_TAG"..HEAD --oneline | grep -cE '^[a-f0-9]+ (fix|hotfix)(\(|: )' || true)
else
  # Branch B — no tags (legacy, remove 2 releases after tag restoration):
  LAST_MANIFEST_BUMP=$(git log -2 --format=%H -- update-manifest.json | sed -n '2p')
  if [ -z "$LAST_MANIFEST_BUMP" ]; then
    echo "ℹ️  No previous manifest bump — skipping fix metric check (first release)"
    exit 0
  fi
  COUNT=$(git log "$LAST_MANIFEST_BUMP"..HEAD --oneline | grep -cE '^[a-f0-9]+ (fix|hotfix)(\(|: )' || true)
fi
echo "fix commits: $COUNT"
if [ "$COUNT" -gt 5 ]; then
  echo "⚠️  >5 fixes — instability Review required before bump"
  exit 1
fi
```

> Fallback Branch B is removed 2 releases after normal tagging is restored.

## Version bump steps

```bash
# 1. Confirm CI is green, pull latest changes
git pull --rebase

# 2. Determine the new version (semver: patch = fixes, minor = new skill/feature)
NEW_VERSION="0.35.0"

# 3. Bump the version in the manifest
python3 - "$NEW_VERSION" <<'EOF'
import json, sys
with open('update-manifest.json', encoding='utf-8') as f:
    m = json.load(f)
m['version'] = sys.argv[1]
with open('update-manifest.json', 'w', encoding='utf-8') as f:
    json.dump(m, f, ensure_ascii=False, indent=2)
    f.write('\n')
print(f"version bumped to {sys.argv[1]}")
EOF

# 4. Add a section to CHANGELOG.md: rename [Unreleased] → [X.Y.Z] and add a new [Unreleased]
# Template:
# ## [X.Y.Z] — YYYY-MM-DD
# ### What's new
# - brief description
# ## [Unreleased]

# 5. Commit + push
git add update-manifest.json CHANGELOG.md
git commit -m "chore: release $NEW_VERSION"
git push
```

---

## Release owner

The template author (`author_mode: true` in `params.yaml`). A release is a synchronous step
and cannot be delegated to agents without explicit permission. Frequency: as changes accumulate,
target ~once per week when significant changes are present.

Release signal: ≥1 features or ≥3 fixes in `[Unreleased]`.

---

## `deprecated_files` Convention

An entry in `deprecated_files` means: **the file has ALREADY been removed from the repo or is no longer in use.**
This does NOT mean "planning to remove" or "migrating soon."

**Rule:**

1. Remove a file from the repo → add it to `deprecated_files` in the same commit.
2. Manually verify that no Script/Hook in the repo references that path:
   ```bash
   grep -r "path/to/deprecated-file" . --include="*.sh" --include="*.md" --include="*.json"
   ```
   Detector 10 in `integration-contract-validator.sh` catches this case for
   `roles/strategist/prompts/` — but only for that file subset.
   For all other deprecated files, manual verification is required.
3. Using `deprecated_files` as a TODO tracker ("we'll remove it soon") is prohibited:
   after `update.sh`, the user will not receive the new file, but the old one is already removed from delivery.

**Why this matters:** if `deprecated_files` contains a file that the runner still uses,
after `update.sh` the runner will fail with "file not found" (precedent: `af3b15c`, strategist roles,
22 May 2026).

---

## Checklist when adding a new file to FMT

For every `git add <new-file>`, verify:

1. The file is added to `update-manifest.json["files"]` (otherwise users will not receive it).
   CI check: `git ls-files | python3 scripts/check-manifest-coverage.py update-manifest.json`.
2. If the file is intentionally NOT intended for delivery — add it to `excluded_paths` or to
   one of the excluded directories (`.github/`, `setup/`, `seed/`, `extensions/`, `templates/`).
3. If the file is a `.sh` Script — run `bash scripts/validate-fmt-scripts.sh scripts/` to check
   for hardcoded values and unsafe arithmetic under `set -e`.

---

## Related files

| File | Purpose |
|------|---------|
| `update-manifest.json` | List of delivered files + version |
| `CHANGELOG.md` | Changelog in Keep a Changelog format |
| `scripts/check-manifest-coverage.py` | CI manifest coverage check (B2) |
| `scripts/validate-fmt-scripts.sh` | Hardcode + set-e arithmetic check (B8) |
| `setup/integration-contract-validator.sh` | Validator spec↔state (including Detector 10) |
| `docs/SCRIPT-PROMOTION.md` | Script promotion process L3→L1 |