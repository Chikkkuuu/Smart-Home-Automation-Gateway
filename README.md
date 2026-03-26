# Smart Home Automation Gateway: Centralized IoT Ecosystem
[cite_start]The **Smart Home Automation Gateway** is a centralized IoT hub designed to unify isolated smart devices into a single, cohesive local-area network[cite: 42]. By leveraging a **Raspberry Pi 4** as the primary edge controller, the system orchestrates communication between physical GPIO pins and consumer-facing interfaces like Google Assistant.

## Detailed System Architecture
The architecture utilizes a flow-based programming model where hardware states are synchronized across physical, virtual, and voice-controlled interfaces.
### 1. Edge Intelligence & Gateway Layer
* **Centralized Controller**: A Raspberry Pi 4 serves as the heart of the ecosystem, running **Node-RED** to manage automation logic.
* **Physical Pin Mapping**: The system interacts directly with the Raspberry Pi's GPIO pins (e.g., PIN 12, PIN 11, and PIN 37) to control connected hardware.
* **Local Execution**: Logic is processed at the edge, ensuring that manual switches and automated flows remain responsive within the local network.
### 2. Device Management & Connectivity
* **Node-RED Dashboard**: Provides a visual interface with virtual "switch" nodes that allow for manual override and status monitoring from any web browser.
* **Voice Integration**: Synchronizes local GPIO states with **Google Assistant** (NORA/Smart Home nodes), enabling voice-activated control for devices like "light 1".
* **Bidirectional Sync**: The flow is engineered so that toggling a physical pin, a dashboard switch, or a voice command updates all other interfaces simultaneously.

## Hardware Wiring Specification
[cite_start]The gateway utilizes the high-bandwidth GPIO interface of the Raspberry Pi 4 to interact with relay modules and sensors[cite: 40, 42].
| Component | Interface | Description |
| :--- | :--- | :--- |
| **Raspberry Pi 4** | **Master Controller** | [cite_start]Runs Node-RED, the MQTT Broker, and the UI Dashboard[cite: 40, 42]. |
| **GPIO 12, 11, 37** | **Digital Output** | Connected to relay modules to manage AC appliances like lights. |
| **Relay Module** | **Switching** | [cite_start]Acts as the physical interface between the Pi's low-voltage signals and high-voltage loads[cite: 42]. |
| **Network Gateway** | **TCP/IP** | Facilitates communication between Node-RED and Google Assistant services. |

## Repository Structure
The project focuses on the flow-based logic and dashboard configuration implemented within the Node-RED environment.
```text
Smart_Home_Gateway/
├── Flows/                    # Node-RED Logic
│   ├── main_flow.json        # Contains GPIO, Dashboard Switch, and Google Home nodes
│   └── config_nodes.json     # Configuration for NORA and UI Base settings
├── Documentation/            # Visual Reference
│   ├── node_red_flow.png     # Screenshot of the operational Flow 1 logic
│   └── dashboard_layout.png  # UI Grouping for "[Home] light 1" and "[Home] Light 3"
├── LICENSE                   # MIT Open Source License
└── README.md                 # Project Documentation
```

## Deployment & Setup
### 1. Environment Configuration
* [cite_start]**Node-RED Installation**: Ensure Node-RED is running on your Raspberry Pi 4[cite: 42].
* **Palette Manager**: Install `node-red-dashboard` for UI elements and `node-red-contrib-smart-home` (or similar) for Google Assistant integration.
### 2. Gateway Initialization
1.  **Flow Import**: Copy and paste the JSON flow into the Node-RED editor.
2.  **Pin Verification**: Double-check that the GPIO nodes match your physical wiring (PIN 12, 11, and 37).
3.  **Voice Binding**: Configure the "nora config" nodes with your credentials to link the devices to your Google Home app.

## Professional Profile
* [cite_start]**Developer**: Ritul Raj Bhakat (Firmware Developer) [cite: 1]
* [cite_start]**Core Expertise**: IoT System Architecture, Node-RED, and Edge Computing[cite: 40, 42].
* [cite_start]**Contact**: [ritulraj384@gmail.com](mailto:ritulraj384@gmail.com) [cite: 2]
* **Links**: [LinkedIn](https://www.linkedin.com/in/ritul-raj-bhakat-521202277/) | [cite_start][GitHub Portfolio](https://github.com/Chikkkuuu) [cite: 2]
