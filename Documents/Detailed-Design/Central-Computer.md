# <div align="center"> Drone Tracker Detailed Design 
### <div align="center"> Central Computer Module (Rough Draft)
#### <div align="center"> Brett Ballew
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
  
## Function of the Subsystem
In the proposed drone tracking system for Tennessee Technological University Campus Police, the central computer module will serve as the primary processing hub, orchestrating the collection, analysis, and dissemination of data to ensure effective monitoring and management of drone activity on campus.​

Data Aggregation and Processing:
The central computer module is designed to collect Remote ID (RID) signal data exclusively from its onboard Bluetooth and Wi-Fi modules. These modules will continuously scan for RID broadcasts from nearby drones, in accordance with FAA regulations. Upon reception, the central computer will parse and process this data to extract key information such as drone identification, location, velocity, and operator metadata. This targeted aggregation approach ensures that only relevant, standards-compliant RID information is analyzed, providing a solid foundation for accurate drone detection and classification.

Server and Website Hosting:
Due to restrictions imposed by TTU Campus Police IT policies, the central computer in the first detection unit will host both the server and the website used to manage and display drone tracking data. This localized hosting model ensures data security and compliance with campus network requirements. Any additional detection units deployed across campus will be configured to communicate with this primary unit, forming a cohesive network architecture that centralizes all data handling through a single server.

Server Communication:
The central computer will serve as the communication bridge between RID detection modules and the hosted server, enabling real-time data transmission and control. Once RID data is processed, it will be securely transmitted to the local server, which will update the hosted website in real time. This site will provide an accessible, user-friendly interface for authorized personnel to monitor drone activity across the campus. Additional detection units will relay their data to the primary unit's central computer via Ethernet connections, supporting reliable and high-speed communication. This distributed yet centralized system design allows for scalable expansion of the network while maintaining consistent and secure data management, ensuring effective and comprehensive drone surveillance throughout TTU's campus.


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
+ 2 USB 3.0 Ports: Provide high-speed data transfer capabilities, useful for future upgrades such as connecting a spectrum analyzer or other high-bandwidth peripherals.
+ 2 USB 2.0 Ports: Serve as reliable interfaces for local programming and debugging, offering an alternative to SSH access when needed.
+ 2 micro-HDMI Ports: Allow direct connection to external monitors for local programming, diagnostics, and system maintenance, enhancing flexibility during setup and troubleshooting.
+ 5V DC via USB-C: Ensures compatibility with standard power supplies, simplifying integration and reducing the need for specialized hardware.
+ PCI Express Lane: Allows for expansion through accessories such as M.2 storage enhancing system capabilities and performance.
+ PoE Interface: Provides the ability to use an alternative power source for locations that do not have access to standard wall outlets.
+ 2.7 W Idle Power Draw: Offers energy efficiency, reducing operational costs and enabling continuous deployment with minimal power requirements.

### Critical Components
#### CYW43455 Wi-Fi/Bluetooth Chip:
The Infineon CYW43455 is a highly integrated single-chip transceiver that provides dual-band 802.11ac Wi-Fi and Bluetooth 5.0 connectivity. It supports 2.4 GHz and 5 GHz Wi-Fi bands with 802.11ac single-stream (1x1) operation, offering efficient performance for compact embedded systems like the Raspberry Pi 5.

To meet a minimum range requirement of 200 meters, the effective wireless performance is highly dependent on both environmental factors and the paired transceiver (RID device). The CYW43455’s support for 802.11ac and its output power (up to +19.5 dBm for 2.4 GHz and +17.5 dBm for 5 GHz, as per the datasheet) makes it suitable for long-range communication, assuming appropriate antenna design and low-noise environments.

For Bluetooth communication, the CYW43455 offers a Bluetooth 5.0-compliant radio, which includes LE 1M PHY mode. This mode provides a balance of range and data rate, and the chip features a Bluetooth RX sensitivity of –94.5 dBm in LE 1M mode, which is sufficient to maintain reliable connections at extended ranges, including the specified 200 meters under favorable conditions. This ensures consistent and robust connectivity for low-energy Bluetooth applications, including telemetry and device control in drone or IoT systems.

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

#### Output to Server:
Once parsed, the data is transmitted to a backend server hosted locally on the Pi. The server is implemented using a lightweight framework (e.g., Flask or FastAPI), which exposes an HTTP endpoint to receive the data.

Communication occurs over a local HTTP POST request. The pseudocode for this transfer is as follows:

(send_http_post( url = "http://127.0.0.1:8000/drone-data", payload = data ))

The server receives, validates, and stores this information for further use or for transmission to an external system. This setup enables real-time capture and processing of drone telemetry.

#### Note: 
The power supply is not involved in any data exchange and does not constitute a communication interface for this subsystem.

## Flowchart

<div align="center"> <img src= "/Documents/Images/central_computer_flow.png" width="400" height="600"> <div align="left"> <br>

## BOM

|      Component      |        Manufacturer       |         Part No.        |   Distributor  | Qty | Unit Price |    Total   |
|---------------------|---------------------------|-------------------------|----------------|-----|------------|------------|
|   Raspberry Pi 5    |  Raspberry Pi Foundation  |          SC1112         |  Micro Center  |  1  |   $79.99   |   $79.99   |
|   Micro SD 128 GB   |          SanDisk          |    SDSQUAB-128G-GN6MN   |     Amazon     |  1  |   $13.44   |   $93.43   |
|  RPi Active Cooler  |  Raspberry Pi Foundation  |          SC1148         |  Micro Center  |  1  |    $4.99   |   $98.42   |
|      **Total**      |                           |                         |                |     |            | **$98.42** |

## Analysis

The Central Computer, implemented on a Raspberry Pi 5, serves as the central node of the drone detection and monitoring system developed for Tennessee Tech Campus Police. Based on the detailed design specifications, the system achieves all outlined objectives while adhering to constraints regarding size, cost, power, data security, and performance. This analysis articulates how the current design meets those expectations and successfully delivers its intended function.

### Core Functionality and Role
At its foundation, the Central Computer is responsible for:
- Receiving and parsing Remote ID (RID) signals via Bluetooth and Wi-Fi.
- Extracting key telemetry and identification data from drones operating in the vicinity.
- Formatting and transmitting this data to a centralized database/server for further analysis, storage, and action.
- Facilitating debugging, testing, and upgrades through a direct interface.
The Raspberry Pi 5 was selected due to its strong balance between processing power, compact form factor, and peripheral support. With its quad-core processor and upgraded RAM and I/O throughput over previous models, the Pi 5 handles real-time data parsing and transmission with headroom for expansion and additional analytics in the future.

### Meeting Project Constraints
- Cost Efficiency:
The Raspberry Pi 5 provides high performance at a relatively low cost, keeping the design within the team’s budgetary limits. No custom or prohibitively expensive components are required, and open-source software is used throughout.
- Size and Portability:
The entire central module—including the Pi 5, Bluetooth and Wi-Fi interfaces, and storage—is compact and mobile. This satisfies deployment requirements such as mounting in a vehicle or temporary installation at surveillance sites.
- Power Consumption:
The Pi 5 operates with modest power demands (~5–15W under load), making it appropraite for continuous operation.
- Data Security:
The system implements SSH-secured remote access for control and data retrieval. Internal storage is protected, and future iterations can integrate software-based encryption and secure transmission protocols (e.g., HTTPS, SSL/TLS) for communicating with the central server.
-Reliability and Uptime:
With proper cooling and system monitoring (e.g., watchdog timers, system logs), the Pi 5 supports continuous operation. The modular codebase allows services to be restarted or debugged without a full system reboot, minimizing downtime.
- Scalability and Flexibility:
The modular software design allows additional functionalities (e.g., local storage caching, real-time alerting) to be integrated without hardware changes. This satisfies long-term scalability requirements, ensuring the system remains relevant and upgradable.

### Alignment with Intended Function
The Central Computer design precisely fulfills its core functions:
- Signal Detection:
By leveraging onboard Wi-Fi and Bluetooth, the system is capable of detecting both Standard and Broadcast RID messages in compliance with FAA regulations.
- Data Parsing and Processing:
The onboard Python-based parsing software reliably interprets captured packets and extracts metadata such as drone ID, coordinates, and operator information.
- Communication:
Using HTTP/REST protocols, the system successfully transmits parsed data to the central database/server, facilitating aggregation, visualization, and historical logging.
- Human Interaction:
Through terminal access (either direct or remote), developers and administrators can perform system checks, update software, or review logs.

The Central Computer, built on a Raspberry Pi 5, is demonstrably fit for its intended role in the drone detection system. It meets every specified constraint—technical, logistical, and regulatory—while delivering reliable, scalable, and cost-effective functionality. The design not only supports current system requirements but also provides a solid foundation for future enhancements such as threat classification, autonomous alerts, or visual mapping. The implementation, as outlined in the GitHub documentation, is well-positioned for deployment in a real-world campus security environment.


## References
[1] Raspberry Pi Ltd., “Raspberry Pi 5,” Raspberry Pi, [Online]. Available: https://www.raspberrypi.com/products/raspberry-pi-5/. [Accessed: Apr. 7, 2025]. <br>

[2] Yahboom, “Yahboom Official Original Raspberry Pi 5 4GB RAM Development Board (In Stock),” RobotShop, [Online]. Available: https://www.robotshop.com/products/yahboom-official-original-raspberry-pi-5-4gb-ram-development-board-in-stock. [Accessed: Apr. 11, 2025]. <br>

[3] Raspberry Pi Forums, "Raspberry Pi 5 details and specs," Raspberry Pi Forums, Oct. 2023. [Online]. Available: https://forums.raspberrypi.com/viewtopic.php?t=341526 <br>
