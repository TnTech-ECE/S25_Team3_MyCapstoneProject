# <div align="center"> Drone Tracker Conceptual Design
#### <div align="center"> Amanda Bacon, Brett Ballew, Tyler Bare, Erich Krepps, Gabrielle Renfroe
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
	
## Introduction 
Unmanned Aircraft Systems (UAS), commonly referred to as drones, have gained significant popularity in recent years due to their innovative features and wide-ranging capabilities. However, not all drone operators prioritize safety or respect for others' privacy, leading to an increase in unsafe drone activities. Drones emit a radio frequency (RF) signal to communicate between the drone and controller. Based on this RF signal, the team proposes a drone tracking device that will alert the Tennessee Technological University (TTU) Police when an unauthorized drone emitting an RF signal enters the campus grounds. 

The purpose of this tracking device is to assist the TTU Police in addressing campus safety, privacy, and security issues caused by improper drone usage. The team aims to address safety concerns including drones flying too close to students, staff, or athletic events, creating collision hazards; drones flying near power lines or other campus infrastructure, causing damage; and drones distracting students or staff, particularly while driving or engaging in other focused activities. Privacy and security issues the team seeks to reduce include drones flying near private areas, such as dorm rooms, and invading restricted zones like construction sites. In addition to addressing these safety, privacy, and security concerns, the drone tracking device will help enforce TTU’s drone policy (Policy 190), which requires compliance with local, state, and federal regulations to operate a drone on TTU property. 

To achieve these goals, the drone tracking device will collect and store data from RF and Wi-Fi signals and transmit this information to TTU Police via a secure website. The website will display details such as the drone's location, altitude, velocity, time stamps, and emergency status. TTU Police will also have the ability to grant or deny access to drones for defined periods. If the device detects an unapproved RF signal, a warning will be sent to the TTU Police, and real-time flight information will be accessible on the website. 

## The Fully Formulated Problem
Other than in a few special cases, the usage of unmanned aircraft systems on the Tennessee Technological University campus is not permitted according to university policies. Be that as it may, the campus police continue to receive complaints of drones causing security, safety, and privacy issues. Without a system in place to locate the offending devices, the officers face a great challenge of actually tracking down the drones and their users. In response to that challenge, this team has been tasked with creating an electronic sensing system to automatically detect these drones and alert the TTU campus police of their presence. Information about the illicit drones will be relayed to the police department via a private website, so that they can assess the threat to campus security and take whatever action they deem necessary. The drone tracking system will meet the specifications defined by the police department, while adhering to all constraints placed upon it by the existing standards for operation, the ethical responsibilities of engineers, and the potential broader impact of the system. The specifications and constraints for this drone tracking system are expounded below. 

### Drone Tracking System Specifications
#### In accordance with the expectations of the TTU campus police department, this project shall do the following: 
1. The system shall detect and track remote ID emitting drones flown over the contiguous TTU campus.
2. The system shall display the data in a concise manner to a secure website accessible only to campus police dispatchers. The campus police have specified that the database be accessed through a website, as opposed to an app, due to the security and privacy concerns that would be introduced were the officers to use their personal device on the job. The website will be accessible to the officers on scene and at the office.  
3. The system shall record and store critical data recovered from the Remote ID signal, until the data is uploaded to the website.
4. The system shall notify campus police in real-time upon detection of a drone in flight.  
5. The system shall enable campus police to grant and revoke drone authorizations as needed. The campus police have requested the ability to authorize specific drones via the website. If a drone user has permission to be operating the drone, such as a student filming a sporting event for the university’s social media page, the police will be able to easily confirm this on the website. The website will keep track of which drones are authorized and which are not.
6. The system shall be designed to minimize further maintenance.

#### Depending on time restraints and the preferences of the campus police, this project may also do the following: 
1. The system may determine the location of the drone’s user and upload this information to the website.
2. The system may increase the urgency of the alert if a drone is detected in a specific geographical region deemed of higher importance by the police department. 
3. The system may be extended to track drones over the Golden Eagle Golf Club and the Hyder-Burks Agriculture Pavilion.

### Drone Tracking System Constraints
The drone tracking system is primarily contrained by the legal standards of the United States of America, the State of Tennessee, and Tennessee Tech University. It is additionally constrained by the ethical and professional duties levied on all engineers in the process of designing a new product. The specific legal and moral obligations by which this project is constrained are examined in closer detail in the Ethical, Professional, and Standards Consideration section immediately below. 

## Ethical, Professional, and Standards Consideration
### Legal Standards
The drone tracking system must comply with all pertinent federal and state laws and with all applicable TTU policies. The way by which this team intends to adhere to each of these laws and policies is explained here. In regards to circuit design, the applicable standard is IEC 60364-1, which requires that the system be designed and installed in a way that does not produce a shock, over-current, fault, power interruption, or interference so as to ensure the safety of living beings and properties near the system. In regards to data transmission and storage, the applicable standards are included in TTU Policy 403 and TTU Policy 856. The first of these two policies is related to proper incident reporting. Since the camera for this drone tracking system will be used for image recognition purposes only, and since the camera will be directed mostly towards the sky, this policy will not be breached. The second policy discusses four levels of data security, their encryption requirements, and disposal procedures of the collected data. The website designed for this system will comply with this policy in full so that no sensitive or personal information is jeopardized. The drone tracking system will be sure to adhere to all of the stated standards in deference to the law, the environment, and human safety.

### Ethical and Professional Responsibilities
The drone tracking system is intended to aid the Tennessee Tech police department in their mission to effectuate order and safety across campus. It is not intended to make students, faculty, staff, or any other person on the TTU campus feel as though their freedoms are being infringed upon. In the prevalent digital landscape of today, some people already feel as though they are under constant surveillance, and it is possible that with the implementation of this system, that feeling will be increased. However, by being enrolled at or employed by Tennessee Tech, students and employees consent to all university policies, including TTU Policy 190. This is the key university policy regarding drone usage, which says that all users "must comply with any local, state, and federal policies and standards" [2]. A variety of laws are laid out in Title 14 Part 107 of the Code of Federal Regulations, dictating the requirements for legal drone operation: the user must carry their piloting certificate while flying the drone (107.7), the user must keep the drone in their line of sight (107.33), the drone must be in near perfect condition (107.14), the drone must not be flown carelessly or recklessly (107.23), and perhaps most intriguingly, the drone must not be flown over a human being unless that being is directly participating in its operation (107.39) [15]. This drone tracking system will detect the drone but not discern if its operation is safe and permissible. Whether or not the use of the drone in question merits suppression will ultimately be decided by the dispatcher on the case, who will then determine the best and most professionally correct way to proceed. With all this taken into consideration, the engineering team believes that the creation of a device to simply alert the police of a drone's presence will not in itself create any serious ethical dilemmas, but rather legitimizes the idea that, if a drone is found to be in severe violation of the law, the campus police will have the capabilities to take care of the problem. The approach that the dispatchers take to respond to these alerts is left to the discretion and ethical convictions of the Tennessee Tech police department. 

### Broader Impact
The team belives that the impact of this project on the general public of Tennessee Tech will be predominantly positive. However, there are a few economic and safety concerns worth mentioning as well. The implementation of this project may result in a minor increase in power allocation from the university, due to the usage of mainline power for the sensor arrays of the tracker. There may also be a slight increase in financial costs to support the maintenance of the web server, website, and physical hardware required for this project. Additionally, potential hazards may be encountered during and after the implementation process if proper installation and maintenance procedures are not followed. Having said that, the success and implementation of this drone tracking system will provide an additional layer of surveillance to the TTU campus, improving public safety in general. The tracking and handling of non-authorized drone traffic on campus will be more easily managed, and privacy issues involving drones with cameras will be more easily addressed. With all this in mind, the team is confident that the advantages of this drone tracking system far surpass its drawbacks, making it a highly beneficial addition to the TTU campus.

## Comparative Analysis of Potential Solutions

## High Level Solution

### Hardware Block Diagram

### Operational Flowchart
<img src= "/Documents/Images/Conceptual Design - Flow Chart (1).png" width="3200" height="900">

## Atomic Subsystem Specifications

## Resources

### Budget

### Division of Labor

### Timeline
<img src= "/Documents/Gantt Chart for Project Proposal (1)-1-1.png" width="3200" height="900">

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

## Statement of Contributions
Amanda Bacon: The Fully Formulated Problem; Ethical, Professional, and Standards Contributions

Brett Ballew: High Level Solution

Tyler Bare: High Level Solution

Erich Krepps: Ethical, Professional, and Standards Contributions; Comparative Analysis of Potential Solutions

Gabrielle Renfroe: Introduction; Comparative Analysis of Potential Solutions
