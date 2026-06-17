<!-- markdownlint-disable -->

# Hardening Report: ponylang--library-documentation-action/0.4.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **ponylang--library-documentation-action/0.4.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image referenced by a mutable tag (`docker://ponylang/library-documentation-action:0.4.0`) rather than an immutable SHA digest. This means the image could be replaced with a different (potentially malicious) version without changing the action reference. It should be pinned to a SHA digest, e.g. `docker://ponylang/library-documentation-action@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:21`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `docker://ponylang/library-documentation-action:0.4.0` with the immutable SHA256 digest `docker://ponylang/library-documentation-action@sha256:e6f4578afeebd406896f9ed84a2da0b9cd2b0eaa67601c18c6d8213bfb6a4be6 # 0.4.0` in action.yml line 21.

