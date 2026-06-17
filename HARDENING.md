<!-- markdownlint-disable -->

# Hardening Report: ponylang--library-documentation-action/0.3.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **ponylang--library-documentation-action/0.3.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image referenced by a mutable tag (`0.3.0`) instead of an immutable SHA digest. This means the image could be silently replaced with a different (potentially malicious) version without any change to the action definition. The failing reference is: `image: docker://ponylang/library-documentation-action:0.3.0`. It should be pinned to a SHA digest, e.g. `image: docker://ponylang/library-documentation-action@sha256:<64-hex-char-digest>`

Locations:

- `action.yml:20`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `ponylang/library-documentation-action:0.3.0` with the immutable SHA digest `ponylang/library-documentation-action@sha256:11d864edfe6b5e18734220989b25399d361b698c41d9ed6a0b9476cec8a1647a # 0.3.0` in action.yml. The original tag is preserved as a comment for readability.

