<!-- markdownlint-disable -->

# Hardening Report: ponylang--library-documentation-action/0.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **ponylang--library-documentation-action/0.2.0** was hardened automatically. 2 finding(s) were identified and resolved across 2 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple workflow files and action.yml reference actions and Docker images using mutable tags/versions instead of immutable full SHA digests, making the action vulnerable to supply-chain attacks.

action.yml: `image: docker://ponylang/library-documentation-action:0.2.0` (tag, not SHA digest)

.github/workflows/announce-a-release.yml: `actions/checkout@v2`, `ponylang/release-bot-action@0.6.1` (×5)
.github/workflows/changelog-bot.yml: `docker://ponylang/changelog-bot-action:0.3.3`
.github/workflows/pr.yml: `actions/checkout@v2` (×4), `docker://github/super-linter:v3.8.3`
.github/workflows/prepare-for-a-release.yml: `actions/checkout@v2` (×3), `ponylang/release-bot-action@0.6.1` (×8)
.github/workflows/release-notes-reminder.yml: `docker://ponylang/release-notes-reminder-bot-action:0.1.0`
.github/workflows/release-notes.yml: `docker://ponylang/release-notes-bot-action:0.3.3`
.github/workflows/release.yml: `actions/checkout@v2` (×3), `ponylang/release-bot-action@0.6.1` (×2)

Locations:

- `action.yml:18`
- `.github/workflows/announce-a-release.yml:15`
- `.github/workflows/announce-a-release.yml:20`
- `.github/workflows/announce-a-release.yml:26`
- `.github/workflows/announce-a-release.yml:32`
- `.github/workflows/announce-a-release.yml:44`
- `.github/workflows/announce-a-release.yml:49`
- `.github/workflows/announce-a-release.yml:55`
- `.github/workflows/changelog-bot.yml:14`
- `.github/workflows/pr.yml:10`
- `.github/workflows/pr.yml:18`
- `.github/workflows/pr.yml:19`
- `.github/workflows/pr.yml:31`
- `.github/workflows/pr.yml:38`
- `.github/workflows/prepare-for-a-release.yml:18`
- `.github/workflows/prepare-for-a-release.yml:23`
- `.github/workflows/prepare-for-a-release.yml:29`
- `.github/workflows/prepare-for-a-release.yml:35`
- `.github/workflows/prepare-for-a-release.yml:41`
- `.github/workflows/prepare-for-a-release.yml:52`
- `.github/workflows/prepare-for-a-release.yml:57`
- `.github/workflows/prepare-for-a-release.yml:66`
- `.github/workflows/prepare-for-a-release.yml:71`
- `.github/workflows/prepare-for-a-release.yml:77`
- `.github/workflows/release-notes-reminder.yml:11`
- `.github/workflows/release-notes.yml:11`
- `.github/workflows/release.yml:19`
- `.github/workflows/release.yml:23`
- `.github/workflows/release.yml:32`
- `.github/workflows/release.yml:43`
- `.github/workflows/release.yml:49`

### missing-permissions (severity: medium)

None of the 7 workflow files define a top-level `permissions:` key, and no individual job within any of these files defines a `permissions:` key either. Without explicit permissions, workflows run with the default (often write-all) token permissions, granting unnecessary access to the GITHUB_TOKEN.

Locations:

- `.github/workflows/announce-a-release.yml:1`
- `.github/workflows/changelog-bot.yml:1`
- `.github/workflows/pr.yml:1`
- `.github/workflows/prepare-for-a-release.yml:1`
- `.github/workflows/release-notes-reminder.yml:1`
- `.github/workflows/release-notes.yml:1`
- `.github/workflows/release.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all unpinned action/image references by pinning to full SHA digests: actions/checkout@v2 → SHA 0717577d..., ponylang/release-bot-action@0.6.1 → SHA bba49846..., and all docker:// container images pinned with sha256 digests (preserving docker:// scheme and tag inline). Added top-level `permissions: contents: read` to all 7 workflow files (announce-a-release.yml, changelog-bot.yml, pr.yml, prepare-for-a-release.yml, release-notes-reminder.yml, release-notes.yml, release.yml). Also pinned the action.yml docker image reference with its sha256 digest.

### Iteration 2

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the mutable container image reference `ponylang/changelog-tool:release` in `.github/workflows/pr.yml` (line 40) to its SHA digest: `ponylang/changelog-tool:release@sha256:fc9aa9546bf1fb669eb956fb7c4ec63f53bf065da748ddaf4fbaa04971d6ebd4`. The tag is preserved inline alongside the digest for readability.

