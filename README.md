# XENECOSYS: Communication Beyond Infrastructure

*XENECOSYS* is a decentralised, infrastructure-independent communication ecosystem designed for a "post-digital" world where traditional networks (Internet, Cellular, Cloud) have failed. It reimagines human connectivity through a resilient network of community hubs and physical data carriers.

## Ecosystem Components

The system is divided into four core pillars:
1.  *XenComm (The App):* A mobile interface for citizens to register, send encrypted messages, and sync with local nodes.
2.  *XenHub (The Node):* An offline community coordination point that manages local message queues and bundle creation.
3.  *XenRelay (The Mule):* Software for vehicles (buses, ambulances) that physically transport encrypted bundles between hubs.
4.  *XenRoute (The Intelligence):* An adaptive routing engine that selects the best path (Direct, Hub, or Relay) based on cached network metadata.

---

## What The Project Does

### XenComm (Mobile App)
XenComm is an *offline-first* platform built for community coordination.
*   *Unique Identity:* Uses globally unique *HX-XXXXXXXX* IDs instead of phone numbers or emails.
*   *Security:* Features *End-to-End Encryption (E2EE)* using AES-256 for content and RSA for identities.
*   *Message Prioritization:* Supports specialized categories including *Emergency, Medical, Government, and Normal*.
*   *Adaptive Sync:* Automatically uploads pending messages and downloads new ones when near a XenHub.

### XenHub (Companion Hub App)
XenHub transforms any existing hardware (laptops, PCs) into a local communication center.
*   *Hub-Blindness:* Stores only encrypted "blobs"; the hub cannot read message contents.
*   *Bundling Mechanism:* Groups individual messages into *Encrypted Bundles* for faster physical transport.
*   *Local Management:* Provides a dashboard for tracking connected users, pending bundles, and emergency alerts.

---

## Delivery Architecture
Information moves through a physical lifecycle rather than a digital one:
*User A* → *XenHub A* → *Encrypted Bundle* → *XenRelay (Data Mule)* → *XenHub B* → *User B*.

---

## Repository Structure

text
XENECOSYS/
|-- .github/workflows/      # Automated XenComm release builds
|-- XenComm/                # User Mobile Application
|   `-- Xencomm/
|       |-- lib/
|       |   |-- core/       # App-wide constants and utils
|       |   |-- models/     # User, Hub, Mule, Message, Bundle
|       |   |-- services/   # SQLite, Crypto, and Notifications
|       |   |-- ui/         # 11+ Screens including Chat & Simulator
|       |   `-- simulation/ # DTN visualization logic
|       `-- android/        # Native Android platform channels
`-- XenHub/                 # Desktop/Admin Hub Application
    |-- lib/                # API server & dashboard logic
    `-- windows/            # Desktop target build files


---

## Tech Stack
*   *Framework:* Flutter (Material 3 Design).
*   *State Management:* Riverpod.
*   *Persistence:* SQLite (sqflite) for all local data—no cloud dependency.
*   *Encryption:* AES-256 and RSA-2048 keypairs.
*   *Routing:* XenRoute adaptive engine for Opportunistic Networking.

---

## Build & Development

### XenComm (Mobile)
Requires Flutter 3.x.
bash
cd XenComm/Xencomm
flutter pub get
flutter pub run build_runner build  # Generate JSON serialization
flutter build apk --release


### XenHub (Desktop/Admin)
bash
cd XenHub
flutter pub get
flutter run


---

## Key Features & Simulation
*   *DTN Simulator:* An internal module to visualize "Data Mule" movement between hubs to demonstrate end-to-end delivery without internet.
*   *Emergency Broadcasts:* Highest-priority alerts (Medical/Food/Gov) that sync before normal traffic.
*   *Offline Notifications:* Local-only triggers for new messages and alerts—no Firebase or Push services used.

---

## Releases
The xencomm-release workflow automates the generation of the production APK. To release:
1.  Tag the commit (e.g., xencomm-v1.0.0).
2.  Push tags to trigger the build and upload to GitHub Releases.

---

## Notes
*   *Infrastructure-Independent:* Every device becomes part of the infrastructure.
*   *Privacy:* No central server stores unencrypted user data or message history.
*   *Scalability:* Designed to support a hybrid of direct P2P, mesh, and DTN-relay modes.
