# <div align="center"> Drone Tracker Conceptual Design
#### <div align="center"> Amanda Bacon, Brett Ballew, Tyler Bare, Erich Krepps, Gabrielle Renfroe
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
	
## Introduction 
### Introduction  

The increasing presence of Unmanned Aircraft Systems (UAS), commonly known as drones, has introduced both opportunities and challenges in various environments, including university campuses. While drones offer numerous benefits, concerns regarding safety, privacy, and security have emerged due to unauthorized or reckless operations. In response to these challenges, regulatory measures such as the Federal Aviation Administration’s (FAA) Remote Identification (RID) requirement have been implemented to enhance drone accountability.  

This conceptual design presents a drone tracking system tailored for Tennessee Technological University (TTU) to help campus authorities monitor and manage drone activity. By leveraging RID signals, the proposed system will provide real-time tracking and alert TTU Police when unauthorized drones enter campus grounds. This initiative aims to improve campus safety, protect privacy, and enforce drone regulations effectively.

## Fully Formulated Problem
### Problem Statement  
Despite Tennessee Technological University’s policy prohibiting most drone operations on campus, unauthorized drone activity remains an ongoing issue. Campus police continue to receive reports of drones posing security, safety, and privacy risks, yet they lack an efficient method to locate and identify the offending devices. Without a dedicated tracking system, officers are forced to rely on eyewitness reports or visual confirmation, making enforcement difficult and often ineffective.  

To address this challenge, the team has been tasked with developing an electronic sensing system capable of detecting unauthorized drones in real time. This system will automatically identify drones emitting Remote Identification (RID) signals and relay critical flight information to TTU Police through a secure website. By providing precise location data, identification details, and alert notifications, the proposed solution will enable law enforcement to assess potential threats and respond accordingly.  

The design of this drone tracking system must meet the operational requirements set forth by TTU Police while adhering to federal regulations, ethical engineering principles, and broader societal considerations. The following sections outline the technical specifications and constraints that will guide the development of this system. 

### Drone Tracking System Specifications
#### In accordance with the expectations of the TTU campus police department, this project shall do the following: 
1. The system shall detect and track drones emitting RID signals flown over the contiguous TTU campus.
2. The system shall display the RID packet data (the drone's coordinates, speed, and ID)  in a concise manner to a secure website accessible only to campus police dispatchers. The campus police have specified that the database be accessed through a website, as opposed to an app, due to the security and privacy concerns that would be introduced were the officers to use their personal device on the job. The website will be accessible to the officers on scene and at the office.  
3. The system shall record and store critical data recovered from the RID signal, until the data is uploaded to the website.
4. The system shall notify campus police in real-time upon detection of a drone in flight.
5. The system shall accurately determine the location of a detected drone within a 50-meter radius.
6. The system shall enable campus police to grant and revoke drone authorizations as needed. The campus police have requested the ability to authorize specific drones via the website. If a drone user has permission to be operating the drone, such as a student filming a sporting event for the university’s social media page, the police will be able to easily confirm this on the website. The website will keep track of which drones are authorized and which are not.
7. The system shall be designed to minimize further maintenance.

#### Depending on time restraints and the preferences of the campus police, this project may also do the following: 
1. The system may determine the location of the drone’s user and upload this information to the website.
2. The system may increase the urgency of the alert if a drone is detected in a specific geographical region deemed of higher importance by the police department. 
3. The system may be extended to track drones over the Golden Eagle Golf Club and the Hyder-Burks Agriculture Pavilion.
4. The system may possess a secondary tracking function that utilizes RF signals and/or photo recogtnition.

### Drone Tracking System Constraints
The drone tracking system is primarily contrained by the legal standards of the United States of America, the State of Tennessee, and Tennessee Tech University. It is additionally constrained by the ethical and professional duties levied on all engineers in the process of designing a new product. The specific legal and moral obligations by which this project is constrained are examined in greater detail in the Ethical, Professional, and Standards Consideration section included later in the document.

## Comparative Analysis of Potential Solutions
### Drone Tracking using Image Recognition
Drone tracking through image recognition relies on a camera system equipped with a trained machine learning model capable of distinguishing drones from other airborne objects, such as birds or debris. The process begins with continuous video capture using a high-resolution camera, preferably mounted on a gimbal for a wider area of coverage. Each frame is then analyzed in real time using a convolutional neural network (CNN) or a pre-trained deep learning model, such as YOLO (You Only Look Once) or Faster R-CNN, which are optimized to detect drones based on unique features like rotor blades, shape, and movement patterns [17]. Once a drone is detected, the system calculates its approximate position using the horizontal and vertical angles from the gimbal yaw and pitch. If multiple cameras are deployed and networked together, the system can achieve greater accuracy through multi-angle tracking. Finally, when an unauthorized drone is detected, an alert is sent to the TTU Police via a secure website, along with timestamped images or video footage for verification. Additional tracking can be initiated to follow the drone’s movement across campus.

#### Pros:
+ Cost-Effective: Requires less complex hardware components compared to radar-based or RF-based solutions.
+ Easy Deployment: Simple design with limited need for specialized telecommunications knowledge.
+ Visual Confirmation: Provides direct visual evidence of unauthorized drones, aiding law enforcement in verifying threats.

#### Cons:
+ Limited Range & Accuracy: Camera-based tracking is highly dependent on environmental conditions, such as lighting, weather, and obstructions (e.g., buildings, trees).
+ False Detections: The system may misidentify birds, flying debris, or even reflections as drones, leading to false positives (90 % accurate up to 80 meters [16]).
+ Tracking Limitations: Without multiple cameras or advanced depth-sensing technology, estimating drone altitude and precise location can be challenging.
+ Computational Demand: Real-time image processing requires significant computing power, potentially necessitating cloud-based processing or high-performance edge devices.
+ Drone Distinguishability: The system is unable to track multiple drones simultaneously and cannot differentiate between individual drones, making it impossible to determine whether they were previously approved for operation.

### Drone Tracking using Triangulation
Another approach to drone tracking involves using three or more transceivers strategically positioned around the monitored area to triangulate the drone's location based on its emitted RF signal. The process of triangulation begins with the transceivers measuring the Time of Arrival (ToA) or Power of Arrival (PoA) of the signal. ToA measures how long it takes for the RF signal to travel from the drone to each transceiver. The longer the signal takes to arrive, the farther the drone is from the transceiver. By calculating the time delay for the signal to reach each transceiver, the system can estimate the drone's position within a certain range. Alternatively, PoA measures the strength of the received signal, which decreases with distance. By analyzing how the signal strength changes as it reaches each receiver, the system can approximate the drone’s distance from each transceiver.

Once the ToA or PoA data from all three transceivers is collected, the system uses trilateration to determine the drone’s location. Trilateration involves calculating the intersection of three spheres, each centered on one of the transceivers, with the radius of each sphere corresponding to the estimated distance between the drone and the transceiver. The intersection of these spheres reveals the approximate location of the drone within the monitored area.

#### Pros:
+ Wide Coverage: Capable of tracking drones across a larger area than single-point detection systems.
+ Independent of Visual Conditions: Functions effectively in low-visibility environments, such as at night or during poor weather conditions.
+ Non-Line-of-Sight Detection: Can detect drones even when they are obscured by buildings, trees, or other obstacles, as long as they are emitting an RF signal.
+ Simple (If using PoA): Power of arrival does not require synchronized transcievers to determine position.
+ Accurate (If using ToA): Time of arrival provides superior accuracy due to a lack of variable fluctuation.
+ Transceiver Placement: Does not require preprogrammed location for transcievers if a GPS module is attatched to each unit.

#### Cons:
+ Innacurate (If using PoA): Environmental factors like signal interference from other devices, obstacles, or atmospheric conditions can lead to inaccuracies in distance calculations.
+ Complex (If using ToA): Synchronizing multiple transceivers and processing the RF data in real-time adds technical complexity and increases the system’s cost.
+ Expensive: The cost of the system will increase linearly with each additional transceiver added. Furthermore, spectrum analyzers will be necessary at each unit for drone detection, which will further contribute to the overall cost of the system.
+ Multiple Drones: The system is unable to track multiple drones simultaneously. However, it can differentiate between individual drones based on RF characteristics.

### Drone Tracking using Image Recognition and Spectral Analysis
Another approach integrates machine learning with a spectrum analyzer and a camera to detect RF signals, measure their power, and estimate the drone's approach angle. This method requires only a single transceiver, combining elements from both image recognition and RF-based tracking systems. In its idle state, the system continuously sweeps a designated frequency range, using machine learning algorithms to identify the presence of a drone's RF signal. Upon detecting a drone, the system estimates its position by analyzing the horizontal and vertical angles from the camera’s gimbal yaw and pitch (as previously discussed in the first method), while the spectrum analyzer provides the power level of the detected signal. The combination of these data points allows for more accurate tracking and localization of the drone within the monitored area.

#### Pros:
+ Improved Accuracy: Combines visual tracking with RF signal analysis for more accurate estimation of drone location and trajectory (mostly distance from transciever).
+ Power Consmption: Low power draw in its idle state due the camera not rotating and no computation.
+ Cost: Of all the solutions, this approach is moderately priced, striking a balance between cost and complexity. It requires only one transceiver, but the need for additional components, such as the spectrum analyzer and camera system, elevates its overall cost compared to simpler solutions.

#### Cons: 
+ Environmental Dependency: Like camera-based tracking, it is affected by environmental conditions such as lighting, weather, and obstructions (e.g., buildings, trees).
+ Power Consumption: High power draw in its active state. The simultaneous processing of RF and image data places significant demands on computing power, which may require high-performance edge devices or cloud-based processing.
+ Multiple Drones: The system is unable to track multiple drones simultaneously. However, it can differentiate between individual drones based on RF characteristics.

### Drone Tracking using RID Signals
The final solution utilizes Remote ID (RID) signals transmitted via Wi-Fi and/or Bluetooth to track and identify drones. This method relies on a Bluetooth and Wi-Fi transceiver that detects and connects to a drone's RID module, which transmits critical data such as the drone's unique ID, location, altitude, and velocity. By capturing RID signals, the system can continuously monitor the position and status of drones within the area of interest. The information provided by the RID signal allows for efficient tracking of drones, including their real-time movements, ensuring compliance with regulations and enhancing security within the monitored space.

#### Pros:
+ Multiple Drone Tracking: Offers the tracking of multiple drones simultaneously by utilizing RID information, which provides essential data without the need for continuous visual or RF monitoring.
+ Simpler Integration: Utilizes standard communication protocols (Wi-Fi and Bluetooth), making integration into existing infrastructure relatively straightforward.
+ Effective Identification: Allows for precise identification of drones by their RID, reducing the risk of false detections and improving threat assessment.
+ Coverage Range: The effective detection range is limited by the Wi-Fi and Bluetooth signal ranges, which are generally shorter than those of other RF-based solutions. However, these ranges are still significantly greater than those of camera-based tracking methods.
+ RID Data: The RID data packet has the potential to relay the operator's location or the drone's takeoff point, depending on the specific case. While this may vary, it remains a valuable benefit worth noting.
#### Cons:
+ Dependency on RID Compliance: This method requires that the drones are equipped with and transmitting RID signals, which may not be mandatory for all drones or could be disabled by unauthorized operators.
+ Potential Interference: The system could experience interference from other devices using the same Wi-Fi or Bluetooth frequency bands, potentially impacting tracking reliability.


## High Level Solution
To implement the drone tracking device, the RID solution has been selected. This section examines the functionality of this method and its effect on maximizing stakeholder value, achieving key objectives, adhering to established constraints, minimizing risks, and optimizing resource utilization.  

#### High-Level Description 
The system operates by utilizing Wi-Fi and Bluetooth RID modules, which are programmed to continuously scan the designated central frequencies (2.4 GHz and 5.8 GHz) for broadcasting devices. Upon detecting a drone’s RID signal, the system establishes communication between the RID module and the Bluetooth or Wi-Fi transceiver, initiating an exchange of critical data from the drone’s RID packet. This data includes key information such as the drone’s unique ID, location (longitude and latitude), speed, and altitude. Once this data is captured, it is transmitted to the central computer, which processes the information to determine the drone’s position and other critical parameters.

Following the retrieval of the drone's data, the system initiates a File Transfer Protocol (FTP) to relay the gathered information to the Campus Police server. The data is then processed and displayed on the user interface, where a corresponding icon appears on a map to provide real-time visualization of the drone’s location. The user is notified with details such as the drone’s ID, location, and speed. The interface allows the user to either approve or deny the drone’s operation or dismiss the notification. This feature ensures that campus security has full control over the approval of drone activities, enhancing security by preventing unauthorized operations.

The device operates in two primary states: active and inactive. In the inactive state, no RID-emitting drones are present, and the system continuously scans for incoming drone signals. During this state, power consumption is minimal, approximately 2.7 W. In contrast, when the system is active, it establishes communication with RID modules, processes the data, and transfers files to the server. This active state requires more power, drawing around 15 W. The flexibility of these states allows the system to efficiently manage power while ensuring continuous monitoring and quick response times when unauthorized drone activity is detected.

#### Effects 
This proposed system is designed to maximize stakeholder goal attainment by addressing the primary needs of TTU Campus Police, who require enhanced campus safety, privacy, and security while enforcing TTU policies and FAA regulations. The solution achieves these objectives through several key features. Real-time detection and alerts enable continuous monitoring of campus airspace for RID signals, providing immediate notifications to Campus Police when unauthorized drones are detected. This allows for swift responses to potential threats, such as drones near crowded areas or restricted zones. A secure web interface offers a user-friendly platform for dispatchers and officers to access specific data including drone location, velocity, and operator location. Authorization management allows Campus Police to grant or revoke flight permissions for specific drones, ensuring controlled airspace usage during events such as athletic games or construction projects. Additionally, the system logs and stores system logs and authorization status data to ensure compliance with TTU Policy 856 and FAA regulations, providing a reliable audit trail for investigations. By addressing safety, privacy, and regulatory enforcement, the system aligns with stakeholder priorities and enhances overall campus security. 

The design adheres to established technical, legal, and budgetary constraints through planning and compliance with relevant standards. The system operates within frequency ranges specified by FCC 47 CFR Part 15 and IEEE 802.11 standards, minimizing interference with other wireless devices. Hardware components, such as the Wi-Fi and Bluetooth module, are selected to meet performance requirements while staying within budget. The system complies with FAA Part 107 and Part 89 regulations for drone operation and RF broadcasting, as well as TTU policies like Policy 403 for surveillance and Policy 856 for data security ensuring ethical and lawful operation. Budgetary constraints are addressed by leveraging existing components from prior projects and utilizing free or university-licensed software tools, with an estimated cost of $820.00 per unit. Future scalability, such as coverage for the Golden Eagle Golf Club, will be implemented incrementally to manage costs effectively. 

To minimize risks, the system incorporates several safeguards. Data security is ensured through encryption and role-based access controls on the secure website, protecting sensitive information and complying with TTU Policy 856. Rigorous testing and validation in both controlled and real-world environments ensure system reliability and accuracy, with controlled experiments validating core functionalities and field tests assessing performance under varying conditions. Ethical considerations are addressed by focusing on RID data rather than visual surveillance, minimizing privacy concerns. Stakeholder consultations will be conducted to address any ethical issues and build trust within the campus community. 

The design also optimizes resource utilization by maximizing available resources and minimizing waste. Hardware efficiency is achieved through the selection of cost-effective yet high-performing components, such as the Wi-Fi transciever, Bluetooth transciever, and microcontroller. Software optimization is accomplished through the use of open-source tools like KiCad for PCB design and FreeRTOS for embedded systems, as well as university-licensed software such as AutoCAD and Visual Studio Code. Python and C/C++ are utilized for their versatility in high-level data processing and low-level firmware development. The modular design allows for incremental deployment, starting with high-priority areas like athletic fields and dormitories, and expanding to additional zones like the Golden Eagle Golf Club as resources permit. Finally, the system is designed for long-term reliability, with weatherproofing and durable components reducing the need for frequent maintenance. 

### Hardware Block Diagram
<img src= "/Documents/Images/Conceptual Design - Block Diagram - RID.png" width="5000" height="450">

### Operational Flowchart
<img src= "/Documents/Images/Conceptual Design - Flow Chart - RID-1.png" width="3200" height="900">

## Atomic Subsystem Specifications
### Power Supply
The power supply module shall convert AC power into usable DC voltage for the system components. It shall first step down the AC voltage using a transformer and then convert it to DC using an AC/DC converter. The regulated DC power shall be distributed via a bus to modules that require DC power such as the Central Computer (Raspberry Pi) and the Spectrum Analyzer, ensuring they receive the necessary power for operation.

### Chassis Module
...

### Bluetooth RID Module
The Bluetooth RID subsystem shall receive and process Bluetooth signals emitted by drones equipped with Remote ID (RID) transmitters. The Bluetooth transceiver shall continuously scan the 2.4 GHz Bluetooth frequency band to detect and capture RID signals while filtering out non-RID transmissions.

Upon detection of an RID signal, the Bluetooth transceiver shall extract the relevant data packets embedded in the signal. These packets shall include, but are not limited to:

+ Drone Identification: A unique identifier assigned to the drone.
+ Geolocation Data: The latitude, longitude, and altitude of the drone at the time of transmission.
+ Velocity Information: The drone’s ground speed and direction of movement.
+ Timestamp: A precise timestamp indicating when the data was transmitted.
+ Emergency Status (if applicable): Indication of any emergency condition, such as a loss of control or return-to-home activation.

Once extracted, the RID data packets shall be transmitted in real-time to the central computer for processing and server transmission. The system shall ensure reliable reception of all RID data from drones operating within the designated tracking area, which includes the entire contiguous campus. This subsystem is designed to function autonomously, requiring minimal intervention while ensuring accurate and efficient drone tracking for compliance, security, and situational awareness purposes.
Implementation with Raspberry Pi Pico W

For example, this subsystem may be implemented using a Raspberry Pi Pico , which includes Bluetooth Low Energy (BLE) functionality via its wireless module. The implementation shall include the following components:

+ Bluetooth Module Setup: The Raspberry Pi Pico can be programmed to operate as a Bluetooth Low Energy (BLE) scanner, continuously scanning for RID signals within the 2.4 GHz spectrum. It shall filter out non-RID packets and focus solely on recognized RID-compliant transmissions.
+ Data Processing: The Raspberry Pi Pico can parse the received BLE advertising packets, extracting relevant drone data such as identification, location, velocity, and status information.
+ Data Transmission: The processed RID data can be transmitted via UART, SPI, or Wi-Fi to a central server for real-time monitoring and further analysis. The Raspberry Pi Pico's built-in Wi-Fi capability can be leveraged to send RID data over a local network or cloud-based server for centralized tracking.
+ Power Efficiency: The power consumption of the Raspberry Pi Pico W varies depending on its operational state. In Idle Mode (Bluetooth disabled), it draws approximately 30 mA, equating to about 100 mW at 3.3V. In Deep Sleep Mode, the power consumption decreases to approximately 4 mA, equating to about 13.2 mW at 3.3V.

### Wi-Fi RID Module
The Wi-Fi transceiver shall receive Wi-Fi signals transmitted by drones flying over the campus. The Wi-Fi module shall continually scan the 2.4 GHz Wi-Fi band to locate RID signals transmitted from a drone.

Once a RID signal is aquired from a drone, the following information can be extracted.

+ Drone Identification: A unique identifier assigned to the drone.
+ Geolocation Data: The latitude, longitude, and altitude of the drone at the time of transmission.
+ Velocity Information: The drone’s ground speed and direction of movement.
+ Timestamp: A precise timestamp indicating when the data was transmitted.
+ Emergency Status (if applicable): Indication of any emergency condition, such as a loss of control or return-to-home activation.

The Wi-Fi module shall transfer the gathered information packets to the central computer module for proper interpretation and transmission to the server. This module designed to ensure consitant reception of RID infomation packets gathered from drones within campus airspace. The Wi-Fi module shall be designed to operate autonomously and with limited outside interaction.

### Central Computer (Raspberry Pi)
The central computer shall be securely mounted within the chassis to ensure both physical protection and optimal performance. It shall receive power through a dedicated power supply designed to meet the system’s operational requirements. To accommodate current and future operational needs, the central computer shall be equipped with no fewer than 20 General Purpose Input/Output (GPIO) pins, allowing for seamless interfacing with various components and enabling future expansions or upgrades.

In terms of power distribution, the central computer shall supply power to both the Wi-Fi and Bluetooth RID modules, ensuring that these modules have the necessary power for operation. It shall communicate with the Wi-Fi and Bluetooth RID modules through digital signaling, ensuring proper data exchange and synchronization within the system.

Additionally, the central computer shall handle packet processing and data storage. It shall process incoming RID signal data, extracting relevant information such as drone ID, location, speed, and other key parameters. This data shall be securely stored for both real-time and historical tracking purposes. After processing, the central computer shall transmit the gathered drone information to the Campus Police server via a secure Wi-Fi connection. The transmitted data shall be encrypted to ensure confidentiality and integrity, preventing unauthorized access or tampering during transmission. This design shall ensure that all communication between the central computer and the server remains secure, reliable, and efficient, providing critical support to campus security operations in real-time.

The Raspberry Pi Model B is the ideal candidate for the central computer due to its compact size, versatility, and sufficient processing power for the system's requirements. The following specifications highlight key features that make the Raspberry Pi Model B an appropriate choice for this application:

+ 2 USB 3.0 Ports: These provide high-speed data transfer, useful for future upgrades such as connecting a spectrum analyzer or other peripherals.
+ 2 USB 2.0 Ports: These are essential for local programming and debugging, offering an alternative to SSH access.
+ 2 micro-HDMI Ports: These allow for direct connection to monitors for local programming and system diagnostics, providing flexibility in system setup and maintenance.
+ 40 GPIO Pins: This provides ample room for future expansions and customizations, making the Raspberry Pi Model B highly adaptable for additional components or sensors as the system evolves.
+ 5V DC via USB-C: This simplifies the integration of the power supply, ensuring compatibility with commonly available power sources.
+ 5V DC via GPIO Header: This feature is crucial for powering the Wi-Fi and Bluetooth RID modules, ensuring that all system components are adequately powered.
+ 2.7 W Idle Power Draw: This low power consumption makes the Raspberry Pi Model B an efficient choice, minimizing operational costs when the system is in an idle state.
+ 3.94 x 2.76 x 1.18 Inches: Its compact size ensures that the Raspberry Pi Model B can be easily housed in a custom-designed case, saving space and facilitating integration within the overall system design.

These specifications ensure that the Raspberry Pi Model B is both cost-effective and capable of meeting the performance and expandability needs of the drone tracking system.

### Server, Database, and Website
The server shall receive the packaged information obtained from the RID signal via a File Transfer Protocol (FTP) transmission from the central computer. After the data has been unpacked and processed, it shall be stored in the database system and acquired by the website when needed. The information being stored is the information extracted by the Bluetooth or Wi-Fi module: the drone identification, geolocation data, velocity information, timestamp, and emergency status. 

The website will be created to allow the police to interact with and interpret the captured data in real time. This website shall require a password to be accessed to ensure that the ability to track the detected drones and make changes to their authorization status is given to campus authorities only. The website will be straightforward with an intuitive user interface. Upon entering the password to log in to the website, the user will be presented with a map of the TTU contiguous campus. If there are any RID emitting drones detected to be flying over campus in the present moment, those drones shall be represented by mobile icons indicating their location in real time. As a visual indicator of their authorization status, drones that have been granted permission to be flown over campus shall be represented by green icons, and drones that have not been granted permission shall be represented by red icons. In the event that a new, unauthorized drone enters campus air space, the system shall respond in this way: 

1. An additional red icon shall appear on the map, marking the location of the drone.
2. A window with specific information about the drone and its flight shall appear, stemming from the corresponding icon.
3. The user will be presented with the option to grant or the new drone permission to make its flight. If authorization is granted, the icon will turn green and the informational box will go away. Otherwise, the information will continue to be displayed, so that the situation can be easily managed by dispatchers.

An ordered list of all the detected drones and their authorization status shall be available on the website, as well. The user may click the Drone Management tab and revoke authorization from a drone when needed. This tool, combined with the map, ensures that the police have awareness and control over all the drones present on campus at any given time. 

## Ethical, Professional, and Standards Consideration
### Legal Standards
The drone tracking system must comply with all pertinent federal and state laws and with all applicable TTU policies. The way by which this team intends to adhere to each of these laws and policies is explained here. In regards to circuit design, the applicable standard is IEC 60364-1, which requires that the system be designed and installed in a way that does not produce a shock, over-current, fault, power interruption, or interference so as to ensure the safety of living beings and properties near the system. In regards to data transmission and storage, the applicable standards are included in TTU Policy 403 and TTU Policy 856. The first of these two policies is related to proper incident reporting. Since the camera for this drone tracking system will be used for image recognition purposes only, and since the camera will be directed mostly towards the sky, this policy will not be breached. The second policy discusses four levels of data security, their encryption requirements, and disposal procedures of the collected data. The website designed for this system will comply with this policy in full so that no sensitive or personal information is jeopardized. The drone tracking system will be sure to adhere to all of the stated standards in deference to the law, the environment, and human safety.

### Ethical and Professional Responsibilities
The drone tracking system is intended to aid the Tennessee Tech police department in their mission to effectuate order and safety across campus. It is not intended to make students, faculty, staff, or any other person on the TTU campus feel as though their freedoms are being infringed upon. In the prevalent digital landscape of today, some people already feel as though they are under constant surveillance, and it is possible that with the implementation of this system, that feeling will be increased. However, by being enrolled at or employed by Tennessee Tech, students and employees consent to all university policies, including TTU Policy 190. This is the key university policy regarding drone usage, which says that all users "must comply with any local, state, and federal policies and standards" [2]. A variety of laws are laid out in Title 14 Part 107 of the Code of Federal Regulations, dictating the requirements for legal drone operation: the user must carry their piloting certificate while flying the drone (107.7), the user must keep the drone in their line of sight (107.33), the drone must be in near perfect condition (107.14), the drone must not be flown carelessly or recklessly (107.23), and perhaps most intriguingly, the drone must not be flown over a human being unless that being is directly participating in its operation (107.39) [15]. This drone tracking system will detect the drone but not discern if its operation is safe and permissible. Whether or not the use of the drone in question merits suppression will ultimately be decided by the dispatcher on the case, who will then determine the best and most professionally correct way to proceed. With all this taken into consideration, the engineering team believes that the creation of a device to simply alert the police of a drone's presence will not in itself create any serious ethical dilemmas, but rather legitimizes the idea that, if a drone is found to be in severe violation of the law, the campus police will have the capabilities to take care of the problem. The approach that the dispatchers take to respond to these alerts is left to the discretion and ethical convictions of the Tennessee Tech police department. 

### Broader Impact
The team belives that the impact of this project on the general public of Tennessee Tech will be predominantly positive. However, there are a few economic and safety concerns worth mentioning as well. The implementation of this project may result in a minor increase in power allocation from the university, due to the usage of mainline power for the sensor arrays of the tracker. There may also be a slight increase in financial costs to support the maintenance of the web server, website, and physical hardware required for this project. Additionally, potential hazards may be encountered during and after the implementation process if proper installation and maintenance procedures are not followed. Having said that, the success and implementation of this drone tracking system will provide an additional layer of surveillance to the TTU campus, improving public safety in general. The tracking and handling of non-authorized drone traffic on campus will be more easily managed, and privacy issues involving drones with cameras will be more easily addressed. With all this in mind, the team is confident that the advantages of this drone tracking system far surpass its drawbacks, making it a highly beneficial addition to the TTU campus.

## Resources

### Budget 
As this project builds upon the work of the previous senior design team, certain components have already been purchased and are available for a single unit. However, this budget outlines the projected costs per unit, as multiple units will likely be required to adequately serve Tennessee Tech's campus. Software costs have not been included in this estimate, as the majority of the tools to be utilized are free, and any additional software required is likely covered under the university’s existing licenses. 

|        Component        | Count |  Unit Cost  |    Cost    | Running Total |
|        ---------        | ----- |    ------   |   -------  | ------------- |
|      Power Supply       |   1   |    $60.00   |    $60.00  |      $60.00   |
| Omnidirectional Antenna |   2   |    $50.00   |   $100.00  |     $160.00   |
|     Wi-Fi Transceiver   |   1   |    $50.00   |    $50.00  |	   $210.00   |
|  Bluetooth Transceiver  |   1   |    $50.00   |    $50.00  |	   $260.00   |
|     Microcontroller     |   1   |   $100.00   |   $100.00  |	   $360.00   | 
|      Memory Module      |   1   |    $50.00   |    $50.00  |     $410.00   |
|         Wiring          |  N/A  |    $50.00   |    $50.00  |	   $460.00   |
|        Enclosure        |   1   |    $20.00   |    $20.00  |	   $480.00   |
|     Weather Proofing    |  N/A  |    $20.00   |    $20.00  |	   $500.00   |
|    Mounting Hardware    |  N/A  |    $20.00   |    $20.00  |	   $520.00   |	
|          Misc           |  N/A  |   $300.00   |   $300.00  |   **$820.00** |	

The first unit is estimated to cost approximately $590.00, utilizing the equipment already provided, along with necessary modifications and supplemental components. If time permits and campus police grant approval, additional units will be installed. Each of these units will function independently while maintaining a connection to the server.

### Division of Labor
Amanda Bacon: Website/Server/Database

Brett Ballew: Central Computer (Rasperry Pi)

Tyler Bare: Bluetooth RID Module

Erich Krepps: Wi-Fi RID Module

Gabrielle Renfroe: Power Supply, Chassis

### Timeline
<img src= "/Documents/Images/Gantt Chart for Project Proposal-1.png" width="3200" height="900">

## References
[1] “C-sUAS - Edgesource,” Edgesource, Mar. 07, 2024. https://www.edgesource.com/c-suas/?gad_source=1&gclid=CjwKCAiA5Ka9BhB5EiwA1ZVtvIU81T-Bijn2FebQkpRLQ9babd4jQCjz57KS0FSbXfN7X3ajevz0rxoCGE0QAvD_BwE (accessed Feb. 12, 2025). 

‌[2] 911 security, “Drone Detection | Everything you need to know| Can drones be detected?,” Airsight.com, 2024. https://www.airsight.com/en-us/knowledg-hub/drone-detection (accessed Feb. 12, 2025). 

‌[3] “Introduction | Dronetag Help,” Dronetag.com, 2023. https://help.dronetag.com/drone-scanner/ (accessed Feb. 12, 2025). 

‌[4] “New Drone Laws by State in the USA (2022),” Drone UTM, Jan. 17, 2024. https://www.thedroneu.com/blog/usa-drone-laws-regulations-by-state/ (accessed Feb. 12, 2025). 

[5] “Drone Laws in Tennessee (2024) - UAV Coach,” UAV Coach, Dec. 21, 2023. https://uavcoach.com/drone-laws-tennessee/ (accessed Feb. 12, 2025). 

‌[6] “190 Unmanned Aircraft Systems v.1,” Navexone.com, 2018. https://tntech.navexone.com/content/dotNet/documents/?docid=483&public=true (accessed Feb. 12, 2025). 

‌[7] FAA, “UAS remote identification | federal aviation administration,” Faa.gov, 2019. https://www.faa.gov/uas/getting_started/remote_id (accessed Feb. 12, 2025). 

‌[8] Skybrary, “Federal aviation administration (FAA),” SKYbrary Aviation Safety, Dec. 30, 2020. https://skybrary.aero/articles/federal-aviation-administration-faa (accessed Feb. 12, 2025). 

[9] A. Schirn, “IEEE 802.11-2020: Collision Avoidance in Wireless Networks - ANSI Blog,” The ANSI Blog, Feb. 01, 2023. https://blog.ansi.org/ieee-802-11-collision-avoidance-wireless-networks/ (accessed Feb. 12, 2025). 

‌[10] “UAS Sightings Report | Federal Aviation Administration,” Faa.gov, 2022. https://www.faa.gov/uas/resources/public_records/uas_sightings_report (accessed Feb. 12, 2025). 

[11] “S24_Team1_DroneTracker,” Github.com, 2025. https://github.com/mrnye42/S24_Team1_DroneTracker/tree/main (accessed Feb. 12, 2025). 

[12] "Aeroscope" dji.com, 2025. https://www.dji.com/aeroscope (accessed Feb. 27, 2025).

[13] "DJI stops sales of its AeroScope drone detection system" www.unmannedairspace.info, 2023. https://www.unmannedairspace.info/counter-uas-systems-and-policies/dji-stops-sales-of-its-aeroscope-drone-detection-system/#:~:text=In%20August%202022%20the%20company,the%20Ukrainian%20war%20and%20that (accessed Feb. 27, 2025).

[14] "CYB21-0049" www.highergov.com, 2022. https://www.highergov.com/subcontract/N0042117D0008-N0042120F1029-CYB21-0049/#:~:text=CYB21-0049%20worth%20$59000.00%20awarded%20to%20Edgesource%20Corporation,for%20WINDTALKER%20SYSTEM%2C%20INSTALLATION%20AND%20SERVICE%20DESK (accessed Feb. 27, 2025).

[15] "Part 107- Small Unmanned Aircraft Systems," Code of Federal Regulations, Jan. 15, 2021. https://www.ecfr.gov/current/title-14/chapter-I/subchapter-F/part-107 (accessed Mar. 4, 2025).

[16] J. M. Llauradó, F. A. Pujol, D. Tomás, A. Visvizi, and M. Pujol, "Study of image sensors for enhanced face recognition at a distance in the Smart City context," Scientific Reports, https://pmc.ncbi.nlm.nih.gov/articles/PMC10484932/ (accessed Mar. 13, 2025).

[17] Z. Zhang, Y. Li, X. Wang, and J. Chen, "Enhanced Small Drone Detection Using Optimized YOLOv8 With Attention Mechanisms," https://ieeexplore.ieee.org/document/10577135 (accessed Mar. 13, 2025).

## Statement of Contributions
Amanda Bacon: Introduction; The Fully Formulated Problem; Ethical, Professional, and Standards Contributions

Brett Ballew: High Level Solution; Hardware Block Diagram; Budget; Comparative Analysis of Potential Solutions

Tyler Bare: High Level Solution; Hardware Block Diagram; Operational Flowchart

Erich Krepps: Comparative Analysis of Potential Solutions; Operational Flowchart; Legal Standards

Gabrielle Renfroe: Introduction; Comparative Analysis of Potential Solutions
