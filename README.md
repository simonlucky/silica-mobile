# SilicaMobile (kmp-sec)

**SilicaMobile** is an open-source, cross-platform Kotlin Multiplatform (KMP) workspace for mobile security research and application assessments targeting Android and iOS environments. It provides modular, shared Kotlin engines to audit local data storage, inspect network transport security, analyze binary metrics, and test protocol behaviors.

---

## 🏗️ Project Architecture

The workspace uses a multi-module Gradle layout to share core capabilities across JVM, Android, and Native (iOS) targets:

```text
silica-mobile/
├── modules/
│   ├── storage-inspector/     # Sandbox, SQLite, plist, & Keystore/Keychain auditing
│   ├── network-interceptor/   # Local Ktor-based HTTP/WebSocket inspection engine
│   ├── binary-auditor/        # Static byte pattern & entropy analysis
│   └── transport-harness/     # Custom transport, framing, & egress testing
├── README.md
└── build.gradle.kts

Module Responsibilities
:modules:storage-inspector (Target: KMP)

Inspects app sandbox directories, SQLite database structures, .plist files, SharedPreferences, and key store access flags.

:modules:network-interceptor (Target: KMP / Ktor)

Embeds an on-device local proxy engine to process and inspect application HTTP/WebSocket flows on loopback interfaces.

:modules:binary-auditor (Target: Shared Kotlin)

Scans target application binaries for hardcoded signatures, entropy variations, and weak cryptographic primitives.

:modules:transport-harness (Target: KMP)

Protocol harness for evaluating outbound egress filtering, transport framing, and connection state handling.

🚀 Quickstart
Prerequisites
JDK 17+

Android Studio / IntelliJ IDEA (with KMP plugin)

Xcode 15+ (required for iOS compilation)

Gradle 8.x

Compilation

# Clone the repository
git clone [https://github.com/your-username/silica-mobile.git](https://github.com/your-username/silica-mobile.git)
cd silica-mobile

# Build shared JVM/Android targets
./gradlew build

# Compile native iOS framework targets
./gradlew :modules:storage-inspector:linkDebugFrameworkIosX64

⚠️ Disclaimer
SilicaMobile is developed and published strictly for authorized security assessments, defensive research, and educational purposes. Always ensure you have explicit permission before testing any third-party application or infrastructure.

📄 License
Distributed under the MIT License. See LICENSE for details.
