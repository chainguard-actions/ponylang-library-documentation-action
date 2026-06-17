<!-- markdownlint-disable -->

# Hardening Report: ponylang--library-documentation-action/0.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **ponylang--library-documentation-action/0.2.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml references a Docker image using a mutable version tag (`docker://ponylang/library-documentation-action:0.2.0`) instead of an immutable SHA digest. A tag can be silently overwritten to point to a different (potentially malicious) image, enabling a supply-chain attack. The image reference should be pinned to a full SHA256 digest, e.g. `docker://ponylang/library-documentation-action@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:19`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the Docker image reference in action.yml from `docker://ponylang/library-documentation-action:0.2.0` to `docker://ponylang/library-documentation-action@sha256:104460f90891b77056ec32145434935f09899736ad07ab3262c375ecb28b2107 # 0.2.0`. The original tag is preserved as a comment for readability.

