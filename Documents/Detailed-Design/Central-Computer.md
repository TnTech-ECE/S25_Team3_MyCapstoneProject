# <div align="center"> Drone Tracker Detailed Design 
### <div align="center"> Central Computer Module (Very Rough Draft: Chat GPT Special)
#### <div align="center"> Brett Ballew
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
  
## Function of the Subsystem
In the proposed drone tracking system for Tennessee Technological University (TTU), the central computer module will serve as the primary processing hub, orchestrating the collection, analysis, and dissemination of data to ensure effective monitoring and management of drone activity on campus.​

Data Aggregation and Processing:
The central computer module is designed to collect Remote ID (RID) signal data exclusively from its onboard Bluetooth and Wi-Fi modules. These modules will continuously scan for RID broadcasts from nearby drones, in accordance with FAA regulations. Upon reception, the central computer will parse and process this data to extract key information such as drone identification, location, velocity, and operator metadata. This targeted aggregation approach ensures that only relevant, standards-compliant RID information is analyzed, providing a solid foundation for accurate drone detection and classification.

Server and Website Hosting:
Due to restrictions imposed by TTU Campus Police IT policies, the central computer in the primary detection unit will host both the server and the website used to manage and display drone tracking data. This localized hosting model ensures data security and compliance with campus network requirements. Any additional detection units deployed across campus will be configured to communicate with this primary unit, forming a cohesive network architecture that centralizes all data handling through a single server.

Communication with the Server:
The central computer will serve as the communication bridge between RID detection modules and the hosted server, enabling real-time data transmission and control. Once RID data is processed, it will be securely transmitted to the local server, which will update the hosted website in real time. This site will provide an accessible, user-friendly interface for authorized personnel to monitor drone activity across the campus. Additional detection units will relay their data to the primary unit's central computer via Ethernet connections, supporting reliable and high-speed communication. This distributed yet centralized system design allows for scalable expansion of the network while maintaining consistent and secure data management, ensuring effective and comprehensive drone surveillance throughout TTU's campus.


## Specifications and Constraints
- The central computer shall be securely mounted within the chassis to ensure both physical protection and optimal performance.
- The central computer shall receive power through a dedicated power supply designed to meet the system’s operational requirements.
- The central computer shall draw no more than 16 W of power.
- To accommodate current and future operational needs, the central computer shall be equipped with no fewer than 20 General Purpose Input/Output (GPIO) pins, allowing for seamless interfacing with various components and enabling future expansions or upgrades.
- The central computer shall process packets and store data obtained from the Wi-Fi and Bluetooth transceivers.
- The central computer shall transmit the gathered drone information to the Campus Police server via a secure Ethernet connection.
- The transmitted data shall be encrypted to ensure confidentiality and integrity, preventing unauthorized access or tampering during transmission.
- This design shall ensure that all communication between the central computer and the server remains secure, reliable, and efficient, providing critical support to campus security operations in real-time.

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
- The Bluetooth module shall be integrated in the the Central Computer (Raspberry Pi).

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
- The Wi-Fi module shall be integrated in the the Central Computer (Raspberry Pi).


## Overview of Proposed Solution
The Raspberry Pi 5 serves as the Central Computer Module for the drone tracking system, and it is an ideal solution that meets both the technical specifications and constraints outlined in the project. Its compact size, robust wireless capabilities, and sufficient processing power make it a highly effective and reliable choice.

Unlike typical embedded applications that rely on multiple peripherals, the Raspberry Pi 5 in this system will only use external peripherals during the initial programming and setup phase. After deployment, it will operate headlessly—without the need for connected monitors, keyboards, or other accessories.

What makes the Raspberry Pi 5 especially suitable for this project is its integrated dual-band 802.11ac Wi-Fi and Bluetooth 5.0/BLE modules. These wireless communication features are absolutely critical for the success of the system. The drone detection process depends on capturing and interpreting Remote ID (RID) signals, which are broadcast over Bluetooth and Wi-Fi by compliant drones. The Pi’s ability to receive these signals reliably and in real time is central to the system’s function.

The onboard wireless modules eliminate the need for external receivers or dongles, simplifying the hardware setup and reducing power consumption and system complexity. With this built-in connectivity, the Raspberry Pi 5 can continuously scan for and process RID signals, enabling fast and efficient tracking of drones across the designated area.

Additionally, the Pi’s 2.4GHz quad-core Cortex-A76 processor and up to 8GB of LPDDR4X RAM ensure it can handle concurrent scanning, signal processing, and data logging tasks smoothly, even under extended operation. 


## Interface with Other Subsystems
​The Central Computer Module (CCM) in the drone tracking system is responsible for processing data from various inputs and communicating with other subsystems to ensure effective monitoring and management of drone activity on campus. Below is a detailed overview of the inputs, outputs, and data exchanges associated with the CCM:​

#### Inputs to the Central Computer Module

* Remote ID (RID) Signals:
  * Source: Drones operating within the vicinity of the campus.​
  * Nature of Data: RID signals contain essential information about the drone, including its unique identifier, location coordinates, altitude, velocity, and the location of the operator.​
  * Method of Communication: The CCM captures these signals using its integrated dual-band 802.11ac Wi-Fi and Bluetooth 5.0/BLE modules, enabling real-time reception of RID broadcasts.​

* Geofencing Parameters:
  * Source: Predefined geofencing data stored within the system.​
  * Nature of Data: This includes the geographical boundaries that define authorized and unauthorized airspace over the campus.​
  * Method of Communication: The geofencing parameters are preloaded into the CCM's internal storage during system configuration and can be updated as needed.​

#### Outputs from the Central Computer Module

* Alerts and Notifications:
  * Recipients: TTU Police Department and other designated campus security personnel.​
  * Nature of Data: When an unauthorized drone is detected within the campus geofenced area, the CCM generates alerts containing the drone's identifier, current location, trajectory, and operator information.​
  * Method of Communication: These alerts are transmitted via secure communication channels, such as encrypted emails or dedicated security applications, ensuring timely and confidential delivery.​

* Data Logs and Reports:
  * Recipients: Campus authorities and system administrators.​
  * Nature of Data: Comprehensive logs of all detected drone activities, including timestamps, drone identifiers, flight paths, and any violations of geofencing rules.​
  * Method of Communication: These logs are stored locally on the CCM and can be accessed remotely through secure network connections for analysis and record-keeping.​

#### Data Transferred to Other Subsystems

* User Interface Subsystem:
  * Nature of Data: Real-time drone tracking information, including visual representations of drone locations on a campus map, status updates, and alert notifications.​
  * Method of Communication: Data is transmitted over the campus network using standard networking protocols, allowing authorized users to access the information through a web-based interface or dedicated application.​

* Database Management Subsystem:
  * Nature of Data: Archived records of drone activities, system performance metrics, and historical data for trend analysis.​
  * Method of Communication: The CCM periodically uploads this data to a centralized database server using secure file transfer protocols (SFTP) or through direct database connections with appropriate authentication mechanisms.​

* Notification System:
  * Nature of Data: Immediate alerts and critical notifications regarding unauthorized drone activities.​
  * Method of Communication: The CCM interfaces with the campus's existing notification infrastructure, such as SMS gateways or emergency alert systems, to disseminate urgent messages to security personnel and other stakeholders.​

In summary, the Central Computer Module serves as the hub for data acquisition, processing, and dissemination within the drone tracking system. Its integrated Wi-Fi and Bluetooth capabilities are essential for capturing RID signals, while its processing power enables real-time analysis and communication with other subsystems and campus authorities. The CCM ensures that all relevant data is accurately collected, promptly analyzed, and effectively shared to maintain campus airspace security.

Fix this later to relate to power supply
<img src= "/Documents/Images/power_con.png" width="3500" height="500">

## BOM

|     Component    |        Manufacturer       |   Part No.  |   Distributor  | Qty | Unit Price |    Total   |
|------------------|---------------------------|-------------|----------------|-----|------------|------------|
|  Raspberry Pi 5  |  Raspberry Pi Foundation  |    SC1112   |  Micro Center  |  1  |   $79.99   |   $79.99   |
|     **Total**    |                           |             |                |     |            | **$79.99** |

## Analysis

The design of the Central Computer Module (CCM), centered around the Raspberry Pi 5, effectively meets the functional requirements and constraints outlined in the conceptual design for Tennessee Technological University’s drone tracking system. This analysis highlights the CCM’s capabilities, addresses system limitations, and supports the conclusion that the design will succeed in achieving its goals.

Functional Suitability
The primary role of the CCM is to detect, process, and report Remote ID (RID) signals broadcast by drones. These signals contain critical data such as the drone’s unique ID, current GPS location, altitude, velocity, and operator coordinates. The Raspberry Pi 5 is equipped with integrated Wi-Fi and Bluetooth radios, which are directly aligned with the two primary RID broadcasting standards (Wi-Fi NAN and Bluetooth Low Energy). These integrated radios ensure:

* Low latency data reception, crucial for real-time tracking,
* Elimination of extra hardware, reducing system complexity and cost,
* Efficient signal capture, enabling quick detection of potential threats.

By leveraging the Pi’s wireless modules, the system can reliably scan for RID signals over a wide area, even from multiple drones concurrently.

#### Constraint Compliance
1. Power and Space Constraints
  * The Raspberry Pi 5 operates on a 5V/5A power supply and features a compact footprint (85.6mm × 56.5mm).
  * This aligns perfectly with the limited physical and power resources typical of embedded surveillance systems.
  * The lack of need for additional peripherals during operation minimizes power draw and system heat, ensuring continuous uptime.

2. Scalability and Modularity
  * The CCM design is modular, allowing future enhancements (e.g., additional sensors, LTE modules) via USB or PCIe without fundamental redesign.
  * Software-defined radio processing and signal filtering algorithms can be updated or scaled via software packages without hardware change.

3. Autonomy and Low Maintenance
  * Once programmed, the CCM runs autonomously without a keyboard, mouse, or monitor.
  * Logs and alerts are accessible via remote access over Wi-Fi, requiring little to no physical interaction post-deployment.

#### Reliability and Real-Time Processing
The Raspberry Pi 5’s quad-core Cortex-A76 CPU (2.4GHz) and optional 8GB RAM provide sufficient headroom for real-time tasks, such as:

* Continuous signal scanning,
* RID decoding and validation,
* Triggering alerts when policy violations are detected,
* Storing and transmitting logs with timestamps.

The CPU’s efficiency ensures real-time responsiveness even when tracking multiple drones simultaneously or logging extensive datasets.

#### Data Integration and Communication
The CCM is designed to interface seamlessly with other system components:

* Notification Subsystem: Sends automated alerts to campus police and security via encrypted messages or app-based push notifications.
* User Interface: Sends real-time position and status updates to the map-based visual display via the campus LAN or secure web interface.
* Database Subsystem: Uploads detailed logs and flight history to a central database, supporting analysis and regulatory compliance.

All data transmission is handled over standard, secure networking protocols (e.g., HTTPS, SFTP), ensuring compatibility, security, and reliability.

#### Robustness and Maintainability
* The system can be updated remotely, and the OS (typically a Linux-based distro like Raspberry Pi OS) allows for advanced logging, debugging, and recovery tools.
* Built-in watchdog and cron services can ensure the system auto-recovers from unexpected failures, improving robustness.

#### Conclusion
In summary, the Central Computer Module design is a technically sound, well-integrated, and forward-compatible solution for drone detection and tracking. By leveraging the Raspberry Pi 5’s wireless capabilities, computational power, and flexible software environment, the system:

* Meets all specified power, size, and autonomy constraints,
* Efficiently performs the critical task of RID signal capture and processing,
* Communicates with other subsystems in a secure and effective manner.

Therefore, the design not only satisfies current project requirements but also positions the system for future adaptability and scalability. It is a reliable, cost-effective, and mission-appropriate implementation that supports the success of the entire drone tracking platform.


## References
[1] Raspberry Pi Ltd., “Raspberry Pi 5,” Raspberry Pi, [Online]. Available: https://www.raspberrypi.com/products/raspberry-pi-5/. [Accessed: Apr. 7, 2025].
