<!-- markdownlint-disable -->

# Hardening Report: ponylang--library-documentation-action/0.1.6

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **ponylang--library-documentation-action/0.1.6** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references across every workflow file use mutable tags or version strings instead of pinned 40-character commit SHAs. This exposes the action to supply-chain attacks where a tag is moved to point at malicious code. Affected references include: `actions/checkout@v1`, `actions/checkout@v2`, `docker://github/super-linter:v3.8.3`, `ponylang/release-bot-action@0.5.0`, `ponylang/changelog-bot-action@0.3.3`, `ponylang/action-readme-version-updater@0.1.3`, `ponylang/release-notes-reminder-bot-action@0.1.0`, `ponylang/release-notes-bot-action@0.3.3`.

Locations:

- `.github/workflows/pr.yml:10`
- `.github/workflows/pr.yml:16`
- `.github/workflows/pr.yml:28`
- `.github/workflows/pr.yml:37`
- `.github/workflows/announce-a-release.yml:11`
- `.github/workflows/announce-a-release.yml:13`
- `.github/workflows/changelog-bot.yml:11`
- `.github/workflows/release-notes-reminder.yml:11`
- `.github/workflows/release-notes.yml:11`
- `.github/workflows/release.yml:11`
- `.github/workflows/release.yml:22`
- `.github/workflows/release.yml:24`
- `.github/workflows/start-a-release.yml:11`
- `.github/workflows/start-a-release.yml:13`

### missing-permissions (severity: medium)

None of the 7 workflow files define a top-level `permissions:` key, and none of the individual jobs define job-level `permissions:` keys. Without explicit permissions, workflows run with the default (potentially broad) token permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/pr.yml:1`
- `.github/workflows/announce-a-release.yml:1`
- `.github/workflows/changelog-bot.yml:1`
- `.github/workflows/release-notes-reminder.yml:1`
- `.github/workflows/release-notes.yml:1`
- `.github/workflows/release.yml:1`
- `.github/workflows/start-a-release.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all 7 workflow files:

**unpinned-uses**: Pinned all action references to full 40-char commit SHAs:
- actions/checkout@v1 → @50fbc622fc4ef5163becd7fab6573eac35f8462e
- actions/checkout@v2 → @0717577d45739eb3c851188b29f50ed6c0b2194e
- docker://github/super-linter:v3.8.3 → pinned with sha256:11ec9aa31cdcb296de042942b18bb2c1a00495775657eb3b68c271f79ba1e86c (docker:// scheme and tag preserved inline)
- ponylang/release-bot-action@0.5.0 → @34efa6656c60a3075ef39a9861ee105a5d8ac42f
- ponylang/changelog-bot-action@0.3.3 → @082ec1b28d0c0e634155d0933528a8b44bdfcafa
- ponylang/action-readme-version-updater@0.1.3 → @200c5c4d881a315f7a41a49bb4643a7a8021eed5
- ponylang/release-notes-reminder-bot-action@0.1.0 → @60b0f3c7f4601925362ea4057aeb66d7410ac32e
- ponylang/release-notes-bot-action@0.3.3 → @c7daca8c09af7df3a8cb58f2e35c7143ee189501

**missing-permissions**: Added `permissions: {}` top-level block to all 7 workflow files (pr.yml, announce-a-release.yml, changelog-bot.yml, release-notes-reminder.yml, release-notes.yml, release.yml, start-a-release.yml).

