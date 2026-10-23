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

## License

Copyright (C) 2026 Björn Hansen

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU Affero General Public License as published by the Free
Software Foundation, either version 3 of the License, or (at your option) any
later version. See [LICENSE](LICENSE).
