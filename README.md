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

## UI Assets

### Mobile App (APP.UI/)
Screenshots demonstrating XenComm user interface:
- **Broadcast:** Emergency and government broadcast display
- **Contact:** User contact list and management
- **Homes:** Main dashboard and message overview
- **Others:** Additional utility screens
- **Schedule:** Message scheduling and queue management

### Hub Dashboard (Software.UI/)
Screenshots of XenHub admin interface:
- **Dashboard:** System overview and status
- **DTN:** Data Transfer Node visualization
- **Emergency Broadcast:** Alert transmission interface
- **Emergency Broadcast Message Acknowledgment:** Delivery confirmation
- **Queue:** Pending message and bundle queue
- **Relay:** Data mule and vehicle status tracking
- **User:** Connected users and activity management

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
├── .github/
│   └── workflows/
│       └── xencomm-release.yml
├── docs/
│   └── architecture-diagrams/
├── APP.UI/
│   ├── Broadcast.jpg
│   ├── Contact.jpg
│   ├── Homes.jpg
│   ├── Others.jpg
│   └── Schedule.jpg
├── Software.UI/
│   ├── Dashboard.png
│   ├── DTN.png
│   ├── Emergency broadcast.png
│   ├── Emergency broadcast message Acknowledgment.png
│   ├── Queue.png
│   ├── Relay.png
│   └── User.png
├── XenComm/
│   ├── pubspec.yaml
│   ├── analysis_options.yaml
│   ├── README.md
│   ├── LICENSE
│   ├── lib/
│   │   ├── core/
│   │   ├── models/
│   │   ├── services/
│   │   ├── ui/
│   │   │   ├── screens/
│   │   │   ├── widgets/
│   │   │   └── themes/
│   │   ├── simulation/
│   │   └── main.dart
│   ├── assets/
│   ├── android/
│   ├── ios/
│   ├── web/
│   ├── linux/
│   ├── macos/
│   ├── windows/
│   └── test/
├── XenHub/
│   ├── pubspec.yaml
│   ├── analysis_options.yaml
│   ├── README.md
│   ├── LICENSE
│   ├── lib/
│   │   ├── core/
│   │   ├── models/
│   │   ├── services/
│   │   ├── ui/
│   │   │   ├── screens/
│   │   │   ├── widgets/
│   │   │   └── themes/
│   │   └── main.dart
│   ├── assets/
│   ├── android/
│   ├── windows/
│   └── test/
├── LICENSE
└── README.md
```

**Core Folders:**
- `lib/core/` — Constants, config, utilities
- `lib/models/` — Data models (User, Hub, Message, Bundle)
- `lib/services/` — SQLite, Crypto, Notifications, API
- `lib/ui/screens/` — App screens (Chat, Broadcast, Dashboard, etc)
- `lib/ui/widgets/` — Reusable UI components
- `lib/ui/themes/` — Material 3 theming
- `lib/simulation/` — DTN visualization (XenComm only)
- `assets/` — Images, fonts, data files
- `test/` — Unit & widget tests

---

## Build & Development

### Prerequisites
- Flutter 3.x

### XenComm (Mobile APK)
```bash
cd XenComm
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

---

## Authors

| Author | GitHub |
|--------|--------|
| **Disha Mohite** | [@dishamohitedev](https://github.com/dishamohitedev) |
| **Hemant Thakur** | [@stackht](https://github.com/stackht) |
| **Vedh Pokharkar** | [@Vedh28](https://github.com/Vedh28) |
| **Nihal Mishra** | [@NihalMishra3009](https://github.com/NihalMishra3009) |
