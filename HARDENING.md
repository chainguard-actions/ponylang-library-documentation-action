<!-- markdownlint-disable -->

# Hardening Report: ponylang--library-documentation-action/0.3.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **ponylang--library-documentation-action/0.3.0** was hardened automatically. 3 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml uses a Docker image with a mutable tag instead of a SHA digest: `image: docker://ponylang/library-documentation-action:0.3.0`. This is vulnerable to supply-chain attacks as the tag can be silently updated to point to a different image.

Locations:

- `action.yml:20`

### unpinned-uses (severity: high)

Multiple workflow files use `uses:` references pinned to mutable version tags or branch names instead of full 40-character commit SHAs. Failing references include: `actions/checkout@v2`, `ponylang/release-bot-action@0.6.1`, `docker://github/super-linter:v3.8.3`, `docker://ponylang/changelog-bot-action:0.3.3`, `docker://ponylang/release-notes-bot-action:0.3.3`, `docker://ponylang/release-notes-reminder-bot-action:0.1.0`.

Locations:

- `.github/workflows/announce-a-release.yml:13`
- `.github/workflows/announce-a-release.yml:18`
- `.github/workflows/announce-a-release.yml:23`
- `.github/workflows/announce-a-release.yml:28`
- `.github/workflows/announce-a-release.yml:36`
- `.github/workflows/announce-a-release.yml:41`
- `.github/workflows/announce-a-release.yml:47`
- `.github/workflows/pr.yml:9`
- `.github/workflows/pr.yml:18`
- `.github/workflows/pr.yml:27`
- `.github/workflows/pr.yml:35`
- `.github/workflows/prepare-for-a-release.yml:16`
- `.github/workflows/prepare-for-a-release.yml:21`
- `.github/workflows/prepare-for-a-release.yml:27`
- `.github/workflows/prepare-for-a-release.yml:33`
- `.github/workflows/prepare-for-a-release.yml:39`
- `.github/workflows/prepare-for-a-release.yml:50`
- `.github/workflows/prepare-for-a-release.yml:56`
- `.github/workflows/prepare-for-a-release.yml:66`
- `.github/workflows/prepare-for-a-release.yml:72`
- `.github/workflows/prepare-for-a-release.yml:78`
- `.github/workflows/release.yml:18`
- `.github/workflows/release.yml:23`
- `.github/workflows/release.yml:31`
- `.github/workflows/release.yml:39`
- `.github/workflows/release.yml:45`
- `.github/workflows/changelog-bot.yml:14`
- `.github/workflows/release-notes.yml:14`
- `.github/workflows/release-notes-reminder.yml:12`

### missing-permissions (severity: medium)

None of the workflow files define a top-level `permissions:` block, and no job within any workflow defines job-level `permissions:`. This means all jobs run with GitHub's default permissions (which include write access to contents and other scopes), violating the principle of least privilege.

Locations:

- `.github/workflows/add-discuss-during-sync.yml:1`
- `.github/workflows/announce-a-release.yml:1`
- `.github/workflows/changelog-bot.yml:1`
- `.github/workflows/pr.yml:1`
- `.github/workflows/prepare-for-a-release.yml:1`
- `.github/workflows/release-notes-reminder.yml:1`
- `.github/workflows/release-notes.yml:1`
- `.github/workflows/release.yml:1`
- `.github/workflows/remove-discuss-during-sync.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all three finding types across all affected files:

1. action.yml: Pinned `docker://ponylang/library-documentation-action:0.3.0` to SHA digest `sha256:11d864edfe6b5e18734220989b25399d361b698c41d9ed6a0b9476cec8a1647a`.

2. Workflow files - pinned all mutable references:
   - `actions/checkout@v2` → `@ee0669bd1cc54295c223e0bb666b733df41de1c5 # v2`
   - `ponylang/release-bot-action@0.6.1` → `@bba498464671710e261c364d6278d6efaab7f987 # 0.6.1`
   - `docker://github/super-linter:v3.8.3` → pinned with SHA digest
   - `docker://ponylang/changelog-bot-action:0.3.3` → pinned with SHA digest
   - `docker://ponylang/release-notes-bot-action:0.3.3` → pinned with SHA digest
   - `docker://ponylang/release-notes-reminder-bot-action:0.1.0` → pinned with SHA digest
   - `ponylang/changelog-tool:release` container in pr.yml → pinned with SHA digest

3. Added `permissions: {}` at the top level of all 9 workflow files, with appropriate job-level permissions (contents: read/write, pull-requests: write, issues: write) based on each job's actual needs.

