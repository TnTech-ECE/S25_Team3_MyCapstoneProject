# <div align="center"> Drone Tracker Detailed Design 
### <div align="center"> Central Computer Module 
#### <div align="center"> Brett Ballew
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
  
## Function of the Subsystem
The central computer module will act as the system’s processing hub, handling data collection, analysis, and distribution to monitor drone activity on campus.​

Data Processing:
It will collect Remote ID (RID) signals via onboard Bluetooth and Wi-Fi, scanning for FAA-compliant broadcasts. Extracted data—such as drone ID, location, velocity, and operator info—will be parsed and analyzed to ensure accurate detection and classification.

Server and Website Hosting:
Due to TTU Campus Police IT policies, the first detection unit’s central computer will locally host both the server and the monitoring website, ensuring data security and compliance. Other detection units will connect to this primary node, forming a unified network.

Server Communication:
The central unit will relay processed RID data to the local server for real-time website updates. Additional detection units will transmit their data via Ethernet to this central hub, supporting scalable, secure, and consistent campus-wide drone surveillance.


## Specifications and Constraints
- The central computer shall be securely mounted within the chassis to ensure both physical protection and optimal performance.
- The central computer shall have dimensions no greater than 6 x 6 x 6 inches, ensuring easy integration into a compact and appropriately sized chassis for streamlined deployment.
- The central computer shall receive power through a dedicated power supply designed to meet the system’s operational requirements.
- The central computer shall draw no more than 16 W of power.
- To accommodate current and future operational needs, the central computer shall be equipped with no fewer than 20 General Purpose Input/Output (GPIO) pins, allowing for seamless interfacing with various components and enabling future expansions or upgrades.
- The central computer shall process packets and store data obtained from the Wi-Fi and Bluetooth transceivers.
- The central computer shall internally transmit the gathered drone information to the hosted server.
- The central computer shall ensure that all communication between the central computer and the hosted server remains secure, reliable, and efficient, providing critical support to campus security operations in real-time.

#### Bluetooth RID Module (Integrated)
- The Bluetooth transceiver shall continuously scan the 2.4 GHz Bluetooth frequency band to detect and capture RID signals while filtering out non-RID transmissions.
- The transceiver shall have a minimum range of 200 meters (dependent on RID transciever quality).
- The transciever shall have a Bluetooth PHY sensitivity of LE 1M to ensure adequate connections at the minimum specified range.
- Upon detection of an RID signal, the Bluetooth transceiver shall extract the relevant data packets embedded in the signal. These packets shall include, but are not limited to:
  - Drone Identification: A unique identifier assigned to the drone.
  - Geolocation Data: The latitude, longitude, and altitude of the drone at the time of transmission.
  - Velocity Information: The drone’s ground speed and direction of movement.
  - Timestamp: A precise timestamp indicating when the data was transmitted.
  - Emergency Status (if applicable): Indication of any emergency condition, such as a loss of control or return-to-home activation.
- The system shall ensure reliable reception of all RID data from drones operating within the designated tracking area.
- This system shall function autonomously, requiring minimal intervention while ensuring accurate and efficient drone tracking for compliance, security, and situational awareness purposes.
- The Bluetooth module shall be integrated in the the Central Computer.

#### Wi-Fi RID Module (Integrated)
- The Wi-Fi transceiver shall receive Wi-Fi signals transmitted by drones flying over the campus.
- The transceiver shall have a minimum range of 200 meters (dependent on RID transciever quality).
- The Wi-Fi module shall continually scan the 2.4 GHz Wi-Fi band to locate RID signals transmitted from a drone.
- Once a RID signal is aquired from a drone, the following information shall be extracted:
  - Drone Identification: A unique identifier assigned to the drone.
  - Geolocation Data: The latitude, longitude, and altitude of the drone at the time of transmission.
  - Velocity Information: The drone’s ground speed and direction of movement.
  - Timestamp: A precise timestamp indicating when the data was transmitted.
  - Emergency Status (if applicable): Indication of any emergency condition, such as a loss of control or return-to-home activation.
- This module shall be designed to ensure constant reception of RID information packets gathered from drones within campus airspace.
- The Wi-Fi module shall be designed to operate autonomously and with limited outside interaction.
- The Wi-Fi module shall be integrated in the the Central Computer.


## Overview of Proposed Solution
<div align="center"> <img src= "/Documents/Images/rpi.jpg" width="500" height="300"> <div align="left"> <br>
The Raspberry Pi 5 is the ideal candidate for the central computer in the drone tracking system due to its compact form factor, versatility, and sufficient processing power to meet system requirements. The following specifications highlight key features that make the Raspberry Pi 5 well-suited for this application:

### Nice to Haves
+ 2 USB 2.0 Ports: Serves as reliable interfaces for local programming and debugging, offering an alternative to SSH access when needed.
+ 2 micro-HDMI Ports: Allows direct connection to external monitors for local programming, diagnostics, and system maintenance, enhancing flexibility during setup and troubleshooting.
+ 5V DC via USB-C: Ensures compatibility with standard power supplies, simplifying integration and reducing the need for specialized hardware.
+ PCI Express Lane: Allows for expansion through accessories such as M.2 storage enhancing system capabilities and performance.
+ PoE Interface: Provides the ability to use an alternative power source for locations that do not have access to standard wall outlets.
+ 2.7 W Idle Power Draw: Offers energy efficiency, reducing operational costs and enabling continuous deployment with minimal power requirements.

### Critical Components
#### CYW43455 Wi-Fi/Bluetooth Chip:
The Infineon CYW43455 is a highly integrated single-chip transceiver that provides dual-band 802.11ac Wi-Fi and Bluetooth 5.0 connectivity. It supports 2.4 GHz and 5 GHz Wi-Fi bands with 802.11ac single-stream (1x1) operation.

#### Integrated Antenna
The Raspberry Pi 5 includes an integrated dual-band 802.11ac Wi-Fi antenna, which delivers satisfactory performance for long-range, unobstructed communication scenarios. Community testing and user feedback indicate that the onboard antenna can maintain a stable wireless connection at distances of up to approximately 50 meters in open environments [6]. While the integrated antenna offers a compact and cost-effective solution, it lacks advanced features such as MIMO or directional gain, which can limit performance in obstructed or high-interference settings. For applications requiring enhanced range or reliability in challenging RF environments, the use of an external antenna or a high-gain USB Wi-Fi adapter is recommended. A more detailed evaluation of these factors is provided in the analysis section.

#### 2 USB 3.0 Ports 
USB 3.0 ports enable high-speed data transfer for peripherals like spectrum analyzers and allow external Bluetooth adapters when the onboard antenna lacks sufficient range.

#### MicroSD Card Slot: 
Provides flexible and scalable storage options for the system, supporting high-capacity cards suitable for long-term data logging. This feature allows the central computer to locally store collected RID data, host the server and website interface, and maintain logs for historical analysis or compliance documentation. The use of a microSD card ensures easy upgrades or replacements, contributing to the overall maintainability and adaptability of the system.

#### 40 GPIO Pins: 
Offer extensive expandability for custom components or sensors, enabling system adaptability as future requirements evolve.

#### RJ45 Ethernet Port: 
Enables stable wired communication between client devices and additional detection units, supporting system scalability and reliability.

#### Broadcom BCM2712 Processor:
The Broadcom BCM2712 is a quad-core Arm Cortex-A76 processor running at 2.4GHz, offering a strong balance between performance and efficiency. With four high-speed cores, it can easily manage multiple tasks simultaneously, such as hosting a local server to handle web dashboards, API endpoints, or telemetry logging. The high clock speed and modern architecture ensure responsive performance even under load, making it suitable for continuous operation without significant slowdowns or thermal throttling.

This processing capability is especially valuable for drone Remote ID (RID) tracking, where the system needs to receive and interpret real-time data over Bluetooth Low Energy (BLE) and Wi-Fi NAN. The BCM2712 is capable of decoding these wireless signals while concurrently running server processes, enabling real-time data collection, analysis, and visualization. Its ability to manage concurrent wireless and server workloads ensures reliable and uninterrupted tracking in complex or busy environments.

#### Dimensions (3.94 x 2.76 x 1.18 inches): 
Its small footprint allows for easy enclosure in a custom-designed case, facilitating compact integration within the overall system.

<div align="center"> <img src= "/Documents/Images/rpi5_Size.png" width="500" height="400"> <img src= "/Documents/Images/rpi5_layout.jpg" width="500" height="400"> <div align="left"> <br>

These specifications make the Raspberry Pi 5 a cost-effective yet powerful solution, capable of supporting both the current needs and future expansions of the drone tracking system.


## Interface with Other Subsystems
​
The central computer subsystem, implemented on a Raspberry Pi 5, interfaces with two components: external drones broadcasting Remote ID (RID) data, and a local server hosted on the Pi. It receives RID signals over integrated Bluetooth and Wi-Fi radios, processes the data, and transmits the extracted information to the server via a local HTTP interface.

#### Inputs:
The central computer receives broadcasted RID signals from nearby drones. These signals arrive via two wireless communication interfaces:
+ Bluetooth Low Energy (BLE): Drones emit RID data as BLE advertisement packets. The Raspberry Pi continuously scans for these packets using its integrated Bluetooth radio. A custom script (e.g., using the bluez stack or a Python BLE library) extracts the payloads in real time.
+ Wi-Fi NAN (Neighbor Awareness Networking): RID data is also broadcast over Wi-Fi using NAN frames. The Pi’s Wi-Fi interface, set to monitor mode, captures these frames using tools such as tcpdump, tshark, or a custom packet parser.

Each RID broadcast contains a standardized set of data fields:
+ Drone ID (e.g., UUID or MAC address)
+ GPS coordinates (latitude, longitude, altitude)
+ Ground and vertical velocity
+ Timestamp of the broadcast
+ Emergency status flags
+ Optional operator identification

#### Internal Processing:
The Pi runs a continuously operating parser script that decodes incoming BLE and Wi-Fi packets, extracts the relevant fields, and formats them into structured JSON-like objects. Example:

(data = { <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"drone_id": unique_id, <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"location": { <br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"latitude": lat_value, <br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"longitude": lon_value, <br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"altitude": alt_value }, <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"velocity": { <br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"horizontal": speed_value, <br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vertical": vertical_speed_value }, <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"timestamp": current_time, <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"emergency_status": status_flag }) <br>

#### Output to Server Subsystem:
Once parsed, the data is transmitted to a backend server hosted locally on the Pi. The server, implemented using a lightweight framework (Flask or FastAPI), exposes a secured HTTPS endpoint to receive the data. Communication is protected by SSL/TLS encryption to ensure data confidentiality and integrity. Additionally, token-based authentication (JWT) is used to validate requests.

Communication occurs over a local HTTPS POST request. The pseudocode for this transfer is as follows:

send_https_post( <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;url = "http://127.0.0.1:8000/drone-data", <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;payload = data, <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;headers = {"Authorization": "Bearer <jwt-token>"}, <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;verify = '/path/to/cert.pem' <br>
)

The server receives, validates, and stores the data for further processing or transmission. This setup enables real-time capture and secure handling of drone telemetry.

#### Note: 
The power supply and chasis subsystems are not involved in any data exchange and do not constitute communication interfaces. The chasis will however need to dissipate 16 watts of heat during peak load ad passively dissipate 8 watts of heat during standard operation. 


## Flowchart

<div align="center"> <img src= "/Documents/Images/central_computer_flow.png" width="400" height="600"> <div align="left"> <br>

## BOM

|      Component      |        Manufacturer       |         Part No.        |   Distributor  | Qty | Unit Price |    Total    |
|---------------------|---------------------------|-------------------------|----------------|-----|------------|-------------|
|   Raspberry Pi 5    |  Raspberry Pi Foundation  |          SC1112         |     Amazon     |  1  |   $90.19   |    $90.19   |
|   Micro SD 128 GB   |          SanDisk          |    SDSQUAB-128G-GN6MN   |     Amazon     |  1  |   $13.24   |   $103.43   |
|  RPi Active Cooler  |  Raspberry Pi Foundation  |          SC1148         |     Amazon     |  1  |   $10.69   |   $114.12   |
|     Antenna Kit     |          UeeKKoo          |    ORD-CM4-ANTENNA      |     Amazon     |  1  |    $9.59   |   $123.71   |
|    U.FL Connector   |      DHT Electronics      |          AD054          |     Amazon     |  1  |    $5.00   |   $128.71   |
|  Bluetooth Adapter  |         TP-Link           |        UB500 Plus       |     Amazon     |  1  |   $17.99   |   $146.70   |
|    Ethernet Cable   |          Jadaol           |    Cat6-50Ft-White-ML   |     Amazon     |  1  |    $9.99   |   $156.69   |
|      **Total**      |                           |                         |                |     |            | **$156.69** |

## Analysis

### Analysis of Effective Range
As outlined in the specifications section, a minimum reception range of 200 meters is required for receiving RID signals. To assess the feasibility of this requirement, a small experiment was conducted to evaluate the performance of the Raspberry Pi 5's integrated antenna. Although limited documentation exists on the integrated antenna, the specification sheet indicates support for Class 1 (100 m) and Class 2 (10 m) devices. An iPhone 13, which supports only Class 2 devices, was selected as a test subject due to availability. Both antennas are expected to have similar gains, typically around 3 to 5 dBi. The iPhone 13 was placed at the top of the bleachers on the north side of Tucker Stadium, with the RID module moved across various distances until a satisfactory result was achieved. The results are as follows:

### Core Functionality and Role
At its foundation, the Central Computer is responsible for:
- Receiving and parsing Remote ID (RID) signals via Bluetooth and Wi-Fi.
- Extracting key telemetry and identification data from drones operating in the vicinity.
- Formatting and transmitting this data to a centralized database/server for further analysis, storage, and action.
- Facilitating debugging, testing, and upgrades through a direct interface.
The Pi 5 was chosen for its processing power, compact size, and robust I/O. It reliably handles real-time tasks with room for future analytics.

### Meeting Project Constraints
- Cost Efficiency:
Affordable, open-source components meet budget requirements.
- Size and Portability:
Compact and easily deployable in restrictive cases.
- Power Consumption:
Operates efficiently (5–15W), suitable for continuous use.
- Data Security:
SSH-secured access and data protection, with potential for encrypted protocols.
-Reliability and Uptime:
Supports long-term uptime with cooling, watchdogs, and modular recovery features.
- Scalability and Flexibility:
Modular software allows easy feature expansion without hardware changes.

### Alignment with Intended Function
The Central Computer design fulfills its core functions:
- Signal Detection:
By leveraging *onboard Wi-Fi and Bluetooth, the system is capable of detecting both Standard and Broadcast RID messages in compliance with FAA regulations.
- Data Parsing and Processing:
The onboard Python-based parsing software reliably interprets captured packets and extracts metadata such as drone ID, coordinates, and operator information.
- Communication:
Using HTTPS protocols, the system successfully transmits parsed data to the central database/server, facilitating aggregation, visualization, and historical logging.
- Human Interaction:
Through terminal access (either direct or remote), developers and administrators can perform system checks, update software, or review logs.


(might take out)The Central Computer, built on a Raspberry Pi 5, is demonstrably fit for its intended role in the drone detection system. It meets every specified constraint—technical, logistical, and regulatory—while delivering reliable, scalable, and cost-effective functionality. The design not only supports current system requirements but also provides a solid foundation for future enhancements.


## References
[1] Raspberry Pi Ltd., “Raspberry Pi 5,” Raspberry Pi, [Online]. Available: https://www.raspberrypi.com/products/raspberry-pi-5/. [Accessed: Apr. 7, 2025]. <br>

[2] Yahboom, “Yahboom Official Original Raspberry Pi 5 4GB RAM Development Board (In Stock),” RobotShop, [Online]. Available: https://www.robotshop.com/products/yahboom-official-original-raspberry-pi-5-4gb-ram-development-board-in-stock. [Accessed: Apr. 11, 2025]. <br>

[3] Raspberry Pi Forums, "Raspberry Pi 5 details and specs," Raspberry Pi Forums, Oct. 2023. [Online]. Available: https://forums.raspberrypi.com/viewtopic.php?t=341526 <br>

[4] Infineon Technologies, CYW43455 Single-Chip 5G WiFi IEEE 802.11n/ac MAC/Baseband/Radio with Integrated Bluetooth 5.0 Datasheet – Additional Technical Information, v16.00, Apr. 2022. [Online]. Available: https://www.infineon.com/dgdl/Infineon-CYW43455_Single-Chip_5G_WiFi_IEEE_802.11n_ac_MAC_Baseband_Radio_with_Integrated_Bluetooth_5.0_Datasheet-AdditionalTechnicalInformation-v16_00-EN.pdf?fileId=8ac78c8c7d0d8da4017d0ee226686889 <br>

[5] T. Genes, "External antenna mod for Raspberry Pi 5 - Questions," Zynthian Discourse, Nov. 19, 2024. [Online]. Available: https://discourse.zynthian.org/t/external-antenna-mod-for-raspberry-pi-5-questions/10532. [Accessed: Apr. 22, 2025]. <br>

[6] illecitnom, "Bluetooth 5.0 actual performance with Pi 4," Raspberry Pi Forums, Feb. 28, 2021. [Online]. Available: https://forums.raspberrypi.com/viewtopic.php?t=305574. [Accessed: Apr. 22, 2025]. <br>

