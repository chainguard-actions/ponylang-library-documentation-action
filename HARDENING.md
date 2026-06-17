<!-- markdownlint-disable -->

# Hardening Report: ponylang--library-documentation-action/0.5.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **ponylang--library-documentation-action/0.5.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image reference with a mutable tag (`docker://ponylang/library-documentation-action:0.5.0`) instead of an immutable SHA digest. This means the image could be replaced with a different (potentially malicious) version without changing the action reference, creating a supply-chain risk. It should be pinned to a specific SHA digest, e.g. `docker://ponylang/library-documentation-action@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:21`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the Docker image reference in action.yml from the mutable tag `docker://ponylang/library-documentation-action:0.5.0` to the immutable digest `docker://ponylang/library-documentation-action@sha256:5bc85c22f9fbc1b48d640a1dcfe815be3fa1a1f6dc136a03b3ae2d43e868f67b # 0.5.0`. The original tag is preserved as a comment for readability.

