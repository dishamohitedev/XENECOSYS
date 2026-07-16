# XENECOSYS: Communication Beyond Infrastructure

Decentralised, infrastructure-independent communication ecosystem for post-digital world. Enables human connectivity when traditional networks (Internet, Cellular, Cloud) fail.

---

## Overview

**Four Core Pillars:**

| Component | Role |
|-----------|------|
| **XenComm** | Mobile app for users to register, message, sync with local nodes |
| **XenHub** | Offline community hub managing message queues and bundling |
| **XenRelay** | Vehicle software transporting encrypted bundles between hubs |
| **XenRoute** | Adaptive routing engine selecting optimal path (Direct/Hub/Relay) |

---

## Architecture

### Information Flow
```
User A → XenHub A → Encrypted Bundle → XenRelay (Data Mule) → XenHub B → User B
```

### XenComm (Mobile App)
- **Unique Identity:** HX-XXXXXXXX format (no phone/email)
- **Encryption:** AES-256 (content) + RSA-2048 (identities)
- **Message Priority:** Emergency, Medical, Government, Normal
- **Sync:** Automatic upload/download when near XenHub
- **Offline-First:** Designed for no internet dependency

### XenHub (Desktop/Admin Hub)
- **Hub-Blindness:** Stores encrypted blobs only; cannot read contents
- **Bundling:** Groups messages into encrypted bundles for physical transport
- **Dashboard:** Track connected users, pending bundles, emergency alerts
- **Local Management:** No cloud dependency

### XenRelay (Data Mule)
Vehicles (buses, ambulances) physically transport encrypted message bundles between hubs.

### XenRoute (Intelligence)
Adaptive routing selecting optimal delivery path based on cached network metadata.

---

## Tech Stack

| Category | Technology |
|----------|------------|
| **Framework** | Flutter (Material 3 Design) |
| **State Management** | Riverpod |
| **Persistence** | SQLite (sqflite) |
| **Encryption** | AES-256 + RSA-2048 |
| **Routing** | XenRoute (Opportunistic Networking) |

---

## Repository Structure

```
XENECOSYS/
├── .github/workflows/           # Automated XenComm release builds
├── XenComm/                     # User Mobile Application
│   └── Xencomm/
│       ├── lib/
│       │   ├── core/            # App-wide constants and utils
│       │   ├── models/          # User, Hub, Mule, Message, Bundle
│       │   ├── services/        # SQLite, Crypto, Notifications
│       │   ├── ui/              # 11+ Screens (Chat, Simulator)
│       │   └── simulation/      # DTN visualization logic
│       └── android/             # Native Android platform channels
└── XenHub/                      # Desktop/Admin Hub Application
    ├── lib/                     # API server & dashboard logic
    └── windows/                 # Desktop target build files
```

---

## Build & Development

### Prerequisites
- Flutter 3.x

### XenComm (Mobile APK)
```bash
cd XenComm/Xencomm
flutter pub get
flutter pub run build_runner build  # Generate JSON serialization
flutter build apk --release
```

### XenHub (Desktop/Admin)
```bash
cd XenHub
flutter pub get
flutter run
```

---

## Key Features

- **DTN Simulator:** Visualize data mule movement between hubs; demonstrate end-to-end delivery without internet
- **Emergency Broadcasts:** Highest-priority alerts (Medical/Food/Gov) sync before normal traffic
- **Offline Notifications:** Local-only triggers; no Firebase or push services
- **Infrastructure-Independent:** Every device becomes part of infrastructure
- **Privacy-First:** No central server stores unencrypted data or history
- **Hybrid Modes:** Direct P2P, mesh, DTN-relay

---

## Release Process

**Automated via xencomm-release workflow:**

1. Tag commit (e.g., `xencomm-v1.0.0`)
2. Push tags → triggers build and upload to GitHub Releases

---

## Design Philosophy

- **Infrastructure-Independent:** Resilient without centralized networks
- **Privacy:** End-to-end encryption; no unencrypted cloud storage
- **Scalability:** Supports hybrid P2P, mesh, and DTN modes
- **Community-First:** Local hubs empower grassroots connectivity
