# Mobile App Template

Standardized multiplatform native mobile application template for Android (Kotlin + Jetpack Compose), iOS (Swift + SwiftUI), and shared core engine (Go / Rust).

## Architecture

- **`core/`**: Shared core engine for hashing, offline SQLite event queue, and network transfer clients.
- **`android/`**: Native Android app with Jetpack Compose, background services, and hardware/content observers.
- **`ios/`**: Native iOS companion with SwiftUI and PhotoKit.

## Getting Started

```sh
# Run tests
make test

# Run full pre-commit and lint check
make check
```
