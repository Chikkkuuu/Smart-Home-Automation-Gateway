# Smart Home Automation Gateway: Centralized IoT Ecosystem
### Edge-to-Cloud Orchestration | Node-RED Architecture | Voice-Integrated Control
**Focus:** Event-driven state synchronization, local-first automation logic, and Google Assistant integration.

---

## Engineering Philosophy
Modern smart homes often suffer from "Control Fragmentation," where different devices operate on isolated silos. This **Smart Home Automation Gateway** was engineered to act as a unified **Edge Controller**. By utilizing a **Raspberry Pi 4** and a flow-based event-driven model, the system centralizes logic at the edge, ensuring that manual, virtual, and voice-activated commands remain synchronized in real-time with sub-millisecond latency.

---

## 🛠️ Technical Challenges & Engineering Solutions

### 1. Bidirectional State Synchronization
*   **The Problem:** Toggling a physical switch (GPIO) often leaves the web dashboard or voice assistant in a stale state, showing the "old" status.
*   **The Solution:** Implemented a **Feedback-Loop Logic** within Node-RED. Every trigger—whether from a physical GPIO, a Dashboard node, or a Google Assistant (NORA) command—updates a global state variable first, which then pushes the update to all other interfaces simultaneously to ensure total state consistency.

### 2. Edge-First Resilience
*   **The Problem:** Most consumer hubs rely entirely on the cloud; if the internet drops, the home becomes "dumb."
*   **The Solution:** The gateway is architected for **Local Execution**. All automation logic and physical pin toggling are processed locally on the Raspberry Pi 4. Cloud integration (Google Assistant) is treated as an optional *service layer*, meaning local switches and dashboards remain fully operational even during network outages.

### 3. High-Voltage Isolation & Relay Logic
*   **The Problem:** Directly switching high-voltage AC loads via low-voltage MCU pins is a safety risk.
*   **The Solution:** Utilized an optoisolated relay module as the physical interface layer. The firmware/logic manages the low-voltage trigger (PIN 12, 11, 37), while the relay provides a mechanical air-gap to isolate the Raspberry Pi’s delicate GPIO from 220V/110V AC surges.

---

## System Architecture

![System Architecture](link-to-architecture.png)

### 1. Logic Layer (Node-RED)
*   **Centralized Dispatcher:** Manages the flow between NORA (Google Home), the Dashboard UI, and the hardware GPIO nodes.
*   **Mapping:** PIN 12, PIN 11, and PIN 37 are mapped to aliases (e.g., "Main Light", "Fan") for intuitive management.

### 2. Connectivity Layer
*   **NORA/Smart Home Integration:** Facilitates a secure TCP/IP tunnel to Google’s voice services without requiring complex firewall port-forwarding.
*   **Dashboard:** Provides a lightweight, browser-based UI for manual overrides.

---

## Repository Structure
```text
Smart_Home_Gateway/
├── Flows/                    # Node-RED Logic & State Sync
│   ├── main_flow.json        # Unified flow JSON (GPIO + NORA + UI)
│   └── connections.json      # PIN-to-Alias hardware mappings
├── Configuration/            # System & Environment Settings
│   ├── config.json           # MQTT & Gateway Credentials
│   └── package.json          # Dependency list (Dashboard, NORA nodes)
└── Documentation/            # Architecture Visualization
```

---

## Technical Specifications
| Category | Specifications |
| :--- | :--- |
| **Controller** | Raspberry Pi 4 (Broadcom BCM2711) |
| **Logic Engine** | Node-RED (Flow-based Programming) |
| **I/O Interface** | GPIO (Optoisolated Relay Integration) |
| **Protocols** | MQTT, TCP/IP, WebSocket (via NORA) |
| **Network** | Static IP Configuration (e.g., `169.254.79.11`) |

---

## Lessons Learned & Future Iterations
This project was an exercise in managing complex event-driven states across distributed interfaces:

*   **The Pivot:** Initially, the system lacked a unified state bridge, which led to "race conditions" where voice and physical commands would conflict. Transitioning to a **Centralized State Hub** design within Node-RED eliminated these conflicts, ensuring total state consistency across all control points.
*   **Future Refinement:** I am currently exploring the integration of **Zigbee/Z-Wave** via a USB gateway. This will expand the system’s reach to battery-powered sensors and low-power peripherals, moving the architecture beyond hardwired GPIO control into a fully wireless mesh ecosystem.

---

## Contact & Proof of Work
**Ritul Raj Bhakat**  
*Firmware Developer | IoT Systems Architect*

*   **Deep Dive:** [View My Full Portfolio](https://ritulrajbhakatportfolio.vercel.app/)
*   **Professional:** [LinkedIn](https://linkedin.com/in/ritul-raj-bhakat)
*   **Direct:** [Email Me](mailto:ritulraj384@gmail.com)

---
© 2026 Ritul Raj Bhakat. Engineered for centralized IoT orchestration.
