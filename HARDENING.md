<!-- markdownlint-disable -->

# Hardening Report: ponylang--library-documentation-action/0.4.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **ponylang--library-documentation-action/0.4.0** was hardened automatically. 17 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml uses a Docker image reference with a mutable version tag instead of a SHA digest: `image: docker://ponylang/library-documentation-action:0.4.0`. This is vulnerable to supply-chain attacks if the image tag is overwritten.

Locations:

- `action.yml:19`

### unpinned-uses (severity: high)

announce-a-release.yml uses mutable tag/version references instead of pinned SHA commits: `actions/checkout@v2` (line 12), `ponylang/release-bot-action@0.6.1` (lines 15, 21, 27, 43, 48, 54).

Locations:

- `.github/workflows/announce-a-release.yml:12`
- `.github/workflows/announce-a-release.yml:15`
- `.github/workflows/announce-a-release.yml:21`
- `.github/workflows/announce-a-release.yml:27`
- `.github/workflows/announce-a-release.yml:43`
- `.github/workflows/announce-a-release.yml:48`
- `.github/workflows/announce-a-release.yml:54`

### unpinned-uses (severity: high)

changelog-bot.yml uses a mutable Docker image tag reference: `uses: docker://ponylang/changelog-bot-action:0.3.3`.

Locations:

- `.github/workflows/changelog-bot.yml:14`

### unpinned-uses (severity: high)

pr.yml uses mutable tag/version references: `actions/checkout@v2` (multiple steps) and `docker://github/super-linter:v3.8.3`.

Locations:

- `.github/workflows/pr.yml:9`
- `.github/workflows/pr.yml:18`
- `.github/workflows/pr.yml:26`
- `.github/workflows/pr.yml:33`
- `.github/workflows/pr.yml:38`

### unpinned-uses (severity: high)

prepare-for-a-release.yml uses mutable tag/version references: `actions/checkout@v2` (multiple steps) and `ponylang/release-bot-action@0.6.1` (multiple steps).

Locations:

- `.github/workflows/prepare-for-a-release.yml:17`
- `.github/workflows/prepare-for-a-release.yml:20`
- `.github/workflows/prepare-for-a-release.yml:27`
- `.github/workflows/prepare-for-a-release.yml:34`
- `.github/workflows/prepare-for-a-release.yml:41`
- `.github/workflows/prepare-for-a-release.yml:48`
- `.github/workflows/prepare-for-a-release.yml:57`
- `.github/workflows/prepare-for-a-release.yml:60`
- `.github/workflows/prepare-for-a-release.yml:72`
- `.github/workflows/prepare-for-a-release.yml:79`

### unpinned-uses (severity: high)

release-notes-reminder.yml uses a mutable Docker image tag reference: `uses: docker://ponylang/release-notes-reminder-bot-action:0.1.0`.

Locations:

- `.github/workflows/release-notes-reminder.yml:13`

### unpinned-uses (severity: high)

release-notes.yml uses a mutable Docker image tag reference: `uses: docker://ponylang/release-notes-bot-action:0.3.3`.

Locations:

- `.github/workflows/release-notes.yml:14`

### unpinned-uses (severity: high)

release.yml uses mutable tag/version references: `actions/checkout@v2` (multiple steps) and `ponylang/release-bot-action@0.6.1`.

Locations:

- `.github/workflows/release.yml:18`
- `.github/workflows/release.yml:21`
- `.github/workflows/release.yml:30`
- `.github/workflows/release.yml:40`
- `.github/workflows/release.yml:46`

### missing-permissions (severity: medium)

add-discuss-during-sync.yml has no top-level `permissions:` key and no job-level `permissions:` key on any job. This means the workflow runs with the default (potentially broad) GITHUB_TOKEN permissions.

Locations:

- `.github/workflows/add-discuss-during-sync.yml:1`

### missing-permissions (severity: medium)

announce-a-release.yml has no top-level `permissions:` key and no job-level `permissions:` key on any job.

Locations:

- `.github/workflows/announce-a-release.yml:1`

### missing-permissions (severity: medium)

changelog-bot.yml has no top-level `permissions:` key and no job-level `permissions:` key on any job.

Locations:

- `.github/workflows/changelog-bot.yml:1`

### missing-permissions (severity: medium)

pr.yml has no top-level `permissions:` key and no job-level `permissions:` key on any job.

Locations:

- `.github/workflows/pr.yml:1`

### missing-permissions (severity: medium)

prepare-for-a-release.yml has no top-level `permissions:` key and no job-level `permissions:` key on any job.

Locations:

- `.github/workflows/prepare-for-a-release.yml:1`

### missing-permissions (severity: medium)

release-notes-reminder.yml has no top-level `permissions:` key and no job-level `permissions:` key on any job.

Locations:

- `.github/workflows/release-notes-reminder.yml:1`

### missing-permissions (severity: medium)

release-notes.yml has no top-level `permissions:` key and no job-level `permissions:` key on any job.

Locations:

- `.github/workflows/release-notes.yml:1`

### missing-permissions (severity: medium)

release.yml has no top-level `permissions:` key and no job-level `permissions:` key on any job.

Locations:

- `.github/workflows/release.yml:1`

### missing-permissions (severity: medium)

remove-discuss-during-sync.yml has no top-level `permissions:` key and no job-level `permissions:` key on any job.

Locations:

- `.github/workflows/remove-discuss-during-sync.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all unpinned action/image references by resolving them to immutable SHA digests or commit SHAs: ponylang/library-documentation-action:0.4.0, ponylang/changelog-bot-action:0.3.3, github/super-linter:v3.8.3, ponylang/release-notes-reminder-bot-action:0.1.0, ponylang/release-notes-bot-action:0.3.3 (Docker images pinned with sha256 digests); actions/checkout@v2 and ponylang/release-bot-action@0.6.1 (GitHub Actions pinned to full commit SHAs). Added `permissions:` blocks to all 9 workflows that were missing them: add-discuss-during-sync.yml and remove-discuss-during-sync.yml got `contents: read, issues: write, pull-requests: write` (needed for label management); all other workflows got `contents: read` as the minimal required permission.

