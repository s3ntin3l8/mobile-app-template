# CLAUDE.md — Mobile App Template

Guidance for Claude Code (claude.ai/code) and AI coding assistants working in this repository.

## Guidelines

- **PR & Issue Templates:** Fill [`.github/pull_request_template.md`](.github/pull_request_template.md) and [`.github/ISSUE_TEMPLATE/issue-blueprint.md`](.github/ISSUE_TEMPLATE/issue-blueprint.md). See [`CONTRIBUTING.md`](CONTRIBUTING.md) for pre-PR checklist.
- **Review Thread Resolution:** Hermes/human review threads require two API calls to resolve:
  ```sh
  # 1. Reply to inline comment (REST)
  gh api repos/<owner>/<repo>/pulls/<PR>/comments/<comment_id>/replies -f body="Fixed in <sha>"
  # 2. Resolve thread (GraphQL)
  gh api graphql -f query="mutation { resolveReviewThread(input: {threadId: \"<thread_id>\"}) { thread { isResolved } } }"
  ```

## Commands

```sh
# Pre-PR Gates & Testing
make check           # check core (lint + test) and android (lint + test)
make test            # run go core unit tests
make lint            # pre-commit check + golangci-lint
make android         # assemble android debug build
```

## Architecture & Responsibilities

| Subsystem | Responsibility |
|---|---|
| `core/` | Shared Go engine (BLAKE3/FastHash, offline SQLite `queue.db`, HTTP uploader client) |
| `android/` | Android application (Kotlin, Jetpack Compose, MediaStore observers, WorkManager) |
| `ios/` | iOS application (Swift, SwiftUI, PhotoKit, NSURLSession) |

## Key Invariants

1. **Offline Queue Persistence:** All ingest intent and events are durably recorded in `queue.db` before network dispatch.
2. **Cryptographic Checksum Verification:** Full hashes are computed using BLAKE3-256 (64 hex characters).
3. **Safe Storage Reclaim:** Local files are never deleted for storage reclaim unless the remote server confirms verified archival.
