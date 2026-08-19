<!-- markdownlint-disable -->

# Hardening Report: ponylang--library-documentation-action/0.5.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **ponylang--library-documentation-action/0.5.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple workflow files and action.yml use mutable tag or version references instead of pinned 40-character commit SHAs or SHA digests, making them vulnerable to supply-chain attacks.

action.yml: `image: docker://ponylang/library-documentation-action:0.5.0` (mutable tag, not a SHA digest)

announce-a-release.yml: `actions/checkout@v2`, `ponylang/release-bot-action@0.6.1` (multiple occurrences)

changelog-bot.yml: `uses: docker://ponylang/changelog-bot-action:0.3.3`

pr.yml: `actions/checkout@v2` (multiple), `uses: docker://github/super-linter:v3.8.3`

prepare-for-a-release.yml: `actions/checkout@v2` (multiple), `ponylang/release-bot-action@0.6.1` (multiple)

release-notes-reminder.yml: `uses: docker://ponylang/release-notes-reminder-bot-action:0.1.0`

release-notes.yml: `uses: docker://ponylang/release-notes-bot-action:0.3.3`

release.yml: `actions/checkout@v2` (multiple), `ponylang/release-bot-action@0.6.1` (multiple)

Locations:

- `action.yml:19`
- `.github/workflows/announce-a-release.yml:14`
- `.github/workflows/announce-a-release.yml:18`
- `.github/workflows/announce-a-release.yml:24`
- `.github/workflows/announce-a-release.yml:30`
- `.github/workflows/changelog-bot.yml:13`
- `.github/workflows/pr.yml:9`
- `.github/workflows/pr.yml:17`
- `.github/workflows/pr.yml:33`
- `.github/workflows/pr.yml:40`
- `.github/workflows/prepare-for-a-release.yml:18`
- `.github/workflows/prepare-for-a-release.yml:22`
- `.github/workflows/prepare-for-a-release.yml:28`
- `.github/workflows/prepare-for-a-release.yml:34`
- `.github/workflows/prepare-for-a-release.yml:40`
- `.github/workflows/release-notes-reminder.yml:11`
- `.github/workflows/release-notes.yml:13`
- `.github/workflows/release.yml:17`
- `.github/workflows/release.yml:24`
- `.github/workflows/release.yml:35`
- `.github/workflows/release.yml:42`

### missing-permissions (severity: medium)

None of the workflow files define a top-level `permissions:` key, and no individual jobs define job-level `permissions:` blocks. Without explicit permissions, workflows run with the default (often broad) token permissions, violating the principle of least privilege.

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

Fixed all unpinned action/image references by resolving real commit SHAs and container digests: actions/checkout@v2 → @0717577d45739eb3c851188b29f50ed6c0b2194e, ponylang/release-bot-action@0.6.1 → @bba498464671710e261c364d6278d6efaab7f987, and all docker:// container images pinned with their sha256 digests (preserving docker:// scheme and tag inline). Added top-level permissions: blocks to all 9 workflow files with least-privilege permissions (contents: read for most; issues: write and pull-requests: write added for label management workflows).

