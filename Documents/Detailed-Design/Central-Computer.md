# <div align="center"> Drone Tracker Detailed Design
### <div align="center"> Central Computer Module
#### <div align="center"> Brett Ballew
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
  
## Function of the Subsystem
The central computer is responsible for


## Specifications and Constraints
-The central computer shall be securely mounted within the chassis to ensure both physical protection and optimal performance.
-The central computer shall receive power through a dedicated power supply designed to meet the system’s operational requirements.
-The central computer shall draw no more than 16 W of power.
-To accommodate current and future operational needs, the central computer shall be equipped with no fewer than 20 General Purpose Input/Output (GPIO) pins, allowing for seamless interfacing with various components and enabling future expansions or upgrades.
-The central computer shall process packets and store data obtained from the Wi-Fi and Bluetooth transceivers.
-The central computer shall transmit the gathered drone information to the Campus Police server via a secure Ethernet connection.
-The transmitted data shall be encrypted to ensure confidentiality and integrity, preventing unauthorized access or tampering during transmission.
-This design shall ensure that all communication between the central computer and the server remains secure, reliable, and efficient, providing critical support to campus security operations in real-time.

####Bluetooth RID Module (Integrated)
-The Bluetooth transceiver shall continuously scan the 2.4 GHz Bluetooth frequency band to detect and capture RID signals while filtering out non-RID transmissions.
-The transceiver shall have a minimum range of 200 meters (dependent on RID transciever quality).
-The transciever shall have a Bluetooth PHY sensitivity of LE 1M to ensure adequate connections at the minimum specified range.
-Upon detection of an RID signal, the Bluetooth transceiver shall extract the relevant data packets embedded in the signal. These packets shall include, but are not limited to:
  -Drone Identification: A unique identifier assigned to the drone.
  -Geolocation Data: The latitude, longitude, and altitude of the drone at the time of transmission.
  -Velocity Information: The drone’s ground speed and direction of movement.
  -Timestamp: A precise timestamp indicating when the data was transmitted.
  -Emergency Status (if applicable): Indication of any emergency condition, such as a loss of control or return-to-home activation.
-The system shall ensure reliable reception of all RID data from drones operating within the designated tracking area.
-This system shall function autonomously, requiring minimal intervention while ensuring accurate and efficient drone tracking for compliance, security, and situational awareness purposes.
-The Bluetooth module shall be integrated in the the Central Computer (Raspberry Pi).

####Wi-Fi RID Module (Integrated)
-The Wi-Fi transceiver shall receive Wi-Fi signals transmitted by drones flying over the campus.
-The transceiver shall have a minimum range of 200 meters (dependent on RID transciever quality).
-The Wi-Fi module shall continually scan the 2.4 GHz Wi-Fi band to locate RID signals transmitted from a drone.
-Once a RID signal is aquired from a drone, the following information shall be extracted:
  -Drone Identification: A unique identifier assigned to the drone.
  -Geolocation Data: The latitude, longitude, and altitude of the drone at the time of transmission.
  -Velocity Information: The drone’s ground speed and direction of movement.
  -Timestamp: A precise timestamp indicating when the data was transmitted.
  -Emergency Status (if applicable): Indication of any emergency condition, such as a loss of control or return-to-home activation.
-This module shall be designed to ensure constant reception of RID information packets gathered from drones within campus airspace.
-The Wi-Fi module shall be designed to operate autonomously and with limited outside interaction.
-The Wi-Fi module shall be integrated in the the Central Computer (Raspberry Pi).


## Overview of Proposed Solution
The central computer subsystem is designed to 

#### Key Design Choices
Things that are crucial it can do and how it can perform

Why This Solution Works

Validation Approach
- Lab Testing:
- Environmental Stress Testing: 
- Longevity Testing: 


## Interface with Other Subsystems
Provide detailed information about the inputs, outputs, and data transferred to other subsystems. Ensure specificity and thoroughness, clarifying the method of communication and the nature of the data transmitted.


## 3D Model of Custom Mechanical Components


## Buildable Schematic 
Integrate a buildable electrical schematic directly into the document. If the diagram is unreadable or improperly scaled, the supervisor will deny approval. Divide the diagram into sections if the text and components seem too small.

The schematic should be relevant to the design and provide ample details necessary for constructing the model. It must be comprehensive so that someone, with no prior knowledge of the design, can easily understand it. Each related component's value and measurement should be clearly mentioned.


## Printed Circuit Board Layout
Include a manufacturable printed circuit board layout.

## BOM

|     Component    |        Manufacturer       |   Part No.  |   Distributor  | Qty | Unit Price |    Total   |
|------------------|---------------------------|-------------|----------------|-----|------------|------------|
|  Raspberry Pi 5  |  Raspberry Pi Foundation  |    SC1112   |  Micro Center  |  1  |   $79.99   |   $79.99   |
|     **Total**    |                           |             |                |     |            | **$79.99** |

## Analysis


### Power Budget Analysis

- Thermal Management: 
- Future Expansion: 

### Component-Specific Considerations

### Safety Margin Justification

### Cost-Benefit Analysis

### Verification Methodology
The design will be validated through:
- Load Testing: 
- Efficiency Testing: 
- Thermal Testing: 


## References
[1] Raspberry Pi Ltd., “Raspberry Pi 5,” Raspberry Pi, [Online]. Available: https://www.raspberrypi.com/products/raspberry-pi-5/. [Accessed: Apr. 7, 2025].
