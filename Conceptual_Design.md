# <div align="center"> Drone Tracker Conceptual Design
#### <div align="center"> Amanda Bacon, Brett Ballew, Tyler Bare, Erich Krepps, Gabrielle Renfroe
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
	
## Introduction 

Unmanned Aircraft Systems (UAS), commonly referred to as drones, have gained significant popularity in recent years due to their innovative features and wide-ranging capabilities. However, not all drone operators prioritize safety or respect for others' privacy, leading to an increase in unsafe drone activities. In response, the Federal Aviation Administration (FAA) implemented a regulation in 2023 that mandates drones to transmit a remote identification (RID) signal. Based on this RID, the team proposes a drone tracking device that will alert the Tennessee Technological University (TTU) Police when an unauthorized drone emitting an RID signal enters the campus grounds. 

The purpose of this tracking device is to assist the TTU Police in addressing campus safety, privacy, and security issues caused by improper drone use. The team aims to address safety concerns including drones flying too close to students and staff, creating collision hazards; drones flying near power lines or other campus infrastructure, causing damage; and drones distracting students or staff, particularly while driving or engaging in other focused activities. Privacy and security issues the team seeks to reduce include drones flying near private areas, such as dorm rooms, and invading restricted zones like construction sites. In addition to addressing these safety, privacy, and security concerns, the drone tracking device will help enforce TTU’s drone policy (Policy 190), which requires compliance with local, state, and federal regulations to operate a drone on TTU property. 

To achieve these goals, the drone tracking device will collect and store data from RID signals and transmit this information to TTU Police via a secure website. The website will display details such as the drone's RID (serial number), location, altitude, velocity, control station location (depending on RID emitter), time stamps, and emergency status. TTU Police will also have the ability to grant or deny access to specific RID-emitting drones for defined periods. If the device detects an unapproved serial number, a warning will be sent to the TTU Police, and real-time flight information will be accessible on the website. 

## Formulating the Problem 

The usage of unmanned aircraft systems on the Tennessee Technological University contiguous campus is not permitted according to university policies, except in a few special cases. However, the campus police still receive complaints of drones causing security, safety, and privacy issues. For example, unauthorized drones are often reported over university athletic events. This is a safety issue for the student-athletes, and campus police are often notified to resolve the issue. But without a system to track the drone and its operator, the officers face a great challenge in actually locating the drone and user. With the implementation of a drone tracking system, dispatchers would be able to notify the officers of the unauthorized drone and easily relay the necessary information for the issue to be resolved. Illegal drone usage also poses serious risks to privacy on campus. Drones can be used in stalking or harassment cases; one such situation would be a drone filming into a window in on-campus housing. Currently, if such a situation were to be reported, it would be very difficult for the operator to be located. A drone tracking system would make it much easier to stop this sort of illegal activity. As explained in the Existing Solutions section below, a drone tracking system that meets the desired specifications is not currently in production without a paid subscription or a very large setup fee. The objective of this project is to design such a system and grant access to the TTU campus police. The team will need to create multiple systems consisting of hardware and software working in harmony with one another to achieve this objective. 
### Background 

Each month, the FAA receives numerous reports from various sources, including pilots and law enforcement, highlighting unauthorized flights of unmanned aircraft systems (UAS). These reports detail specific cases where drone operators’ incompetence has potentially endangered lives. To understand how the team's drone tracking project seeks to protect civilian lives, maintain privacy, and ensure security, it’s essential to examine the origins of UAS regulations and the constraints placed on drones at TTU campuses. 

This proposal references TTU Policy 190, which outlines three levels of regulations: local, state, and federal. At the federal level, the FAA, an agency within the U.S. Department of Transportation, is responsible for ensuring the safety of civil aviation, including drones. The FAA sets the national rules governing drones, which vary depending on the user. Commercial pilots, hobbyists, and government employees each have distinct regulations. Additionally, the weight of the drone determines the applicable rules. Drones weighing over 250 grams must be registered with the FAA unless a waiver is obtained. Users can request waivers for most restrictions by demonstrating an equivalent level of safety, though certain rules remain non-negotiable for commercial pilots and government employees without special licenses. These pilots must: 

- Register their drone with the FAA. 
- Obtain a Remote Pilot Certificate from the FAA. 

They must also adhere to these guidelines, though they can request waivers if necessary: 

- Maintain visual-line-of-sight while flying. 
- Do not fly near other aircraft or over people. 
- Do not fly in controlled airspace near airports without FAA authorization. 
- Fly only during daylight or civil twilight, at or below 400 feet.

For recreational pilots flying drones over 250 grams, the following rules apply, regardless of waiver status: 

- Register the drone with the FAA. 
- Follow community-based safety guidelines and fly under the direction of a nationwide community-based organization. 
- Maintain visual-line-of-sight while flying. 
- Do not fly near other aircraft. 
- Notify airport and air traffic control if flying within 5 miles of an airport. 
- Never fly near emergency response efforts.
  
Furthermore, all drones required to be registered must comply with Remote Identification (RID) laws, unless they are flown within an FAA-Recognized Identification Area (FRIA). TTU is not a FRIA, so only drones flown recreationally and weighing under 250 grams may legally fly on campus without emitting an RID signal. 

State laws in Tennessee, as established by the Tennessee General Assembly, provide additional regulations: 

- It is a crime to fly a drone within 250 feet of a critical infrastructure for the purpose of conducting surveillance or gathering information about the facility. 
- It is permissible for a person to use UAS on behalf of either a public or private institution of higher education, rather than just public institutions. 
- It is a crime to use a drone to capture an image over certain open-air events and fireworks displays. 
- It is a Class C misdemeanor for any private entity to use a drone to conduct video surveillance of a person who is hunting or fishing without their consent. 
- Law enforcement can use drones in compliance with a search warrant, to counter a high-risk terrorist attack, and if swift action is needed to prevent imminent danger to life.
 
Below the state regulations, there are no specific Putnam County UAS ordinances. However, TTU Police, who will use and enforce the drone tracking system, must consider safety regulations. Ultimately, it is up to TTU Police to understand the regulations, determine what is permissible on campus, and handle any violations accordingly. 

### Specifications and Constraints 

#### The specifications of this project, which were primarily determined by the Tennessee Technological University campus police, are as follows:  
 

1. The system shall detect and track remote ID emitting drones flown over the contiguous TTU campus.
2. The system shall display the data in a concise manner to a secure website accessible only to campus police dispatchers.
	- The campus police have specified that the database be accessed through a website, as opposed to an app, due to the security and privacy concerns that would be introduced were the officers to use their personal device on the job. The website will be accessible to the officers on scene and at the office.  
3. The system shall record and store critical data recovered from the Remote ID signal, until the data is uploaded to the website.
4. The system shall notify campus police in real-time upon detection of a drone in flight.  
5. The system shall enable campus police to grant and revoke drone authorizations as needed.
  	- The campus police have requested the ability to authorize specific drones via the website. If a drone user has permission to be operating the drone, such as a student filming a sporting event for the university’s social media page, the police will be able to easily confirm this on the website. The website will keep track of which drones are authorized and which are not.
6. The system shall be designed to minimize further maintenance.  
 

Depending on time restraints and the preferences of the campus police, this project may also do the following: 
1. The system may determine the location of the drone’s user and upload this information to the website.
2. The system may increase the urgency of the alert if a drone is detected in a specific geographical region deemed of higher importance. 
3. The system may be extended to track drones over the Golden Eagle Golf Club and the Hyder-Burks Agriculture Pavilion.  
 

#### The project is constrained by the legal standards of the United States of America, the State of Tennessee, and Tennessee Tech. These are the guidelines with which this team will adhere to remain in compliance with the law.

Standards regarding Unmanned Aerial Systems: 

- FAA 14 CFR Part 107 - This standard regulates the operation of Drones in U.S Airspace, ensuring that pilots operate their drones in a safe manner. Safety standards include limiting maximum altitude to 400 feet (122 meters), prohibiting drones from flying directly over a non-participating human being, and limiting accessible airspace for pilots to fly in without express permission. This standard also addresses recreational flying rules. 
- FAA 14 CFR Part 89 - This standard pertains to the Remote Identification of Drones operating in U.S Airspace. In sections 89.305 and 89.315, the standard details the minimum element requirements of the Remote ID transponder’s broadcast and how often pilots are required to broadcast it. 
- FCC 47 CFR Part 15 - This standard pertains to electrical and electronic devices that emit or absorb radio frequencies within the 9 kHz to 3,000 GHz range. This standard limits power and exposure levels to prevent interference and endangerment to living beings.
- IEEE 802.11 - This regulates implementation standards for WIFI Networks, Local Area Networks, and MAC Address protocols. It also defines frequency bands and collision-avoidance protocols for wireless transmissions. 
 

Standards regarding circuit design: 

- IEC 60364-1 - This standard specifies design, installation, and verification of electrical systems to ensure the safety of living beings and properties near it. It pertains to shock, over-current, fault, power interruption, and interference protections.

	- To ensure compliance with IEC 60364-1 in circuit design, the team will incorporate protective measures against electric shock, overcurrent, faults, power interruptions, and electromagnetic interference by including select components that meet IEC safety standards, implementing proper grounding and insulation, and using circuit breakers or residual-current devices (RCDs) for fault protection. During implementation, the team will adhere to wiring regulations and use correct labeling determined by IEC (International Electrotechnical Commission) to ensure clarity and remove safety risks.

Standards regarding data retention at TTU: 

- TTU Policy 403 - This policy defines procedures and standards for 
the usage of cameras on campus, along with surveillance periods and incident reporting procedures.

	- To ensure compliance with TTU Policy 403, the tracker’s camera will be installed and operated following established surveillance guidelines including proper incident reporting procedures. Access to recorded footage will not be a concern as the camera will only be used for image recognition. 

- TTU Policy 856 - This policy defines standards and requirements for data security and handling. This policy defines four levels of data security, their encryption requirements, and disposal procedures of the data.

	- To ensure compliance with TTU Policy 856, the drone tracking data displayed on the website will be classified according to defined security levels, with appropriate encryption measures in place to protect sensitive information. Data disposal procedures will be strictly followed to prevent unauthorized access or misuse.

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

[13] "DJI stops sales of its AeroScope drone detection system" www.unmannedairspace.info, 2023. https://www.unmannedairspace.info/counter-uas-systems-and-policies/dji-stops-sales-of-its-aeroscope-drone-detection-system/#:~:text=In%20August%202022%20the%20company,the%20Ukrainian%20war%20and%20that (accessed Feb. 27, 2025)

[14] "CYB21-0049" www.highergov.com, 2022. https://www.highergov.com/subcontract/N0042117D0008-N0042120F1029-CYB21-0049/#:~:text=CYB21-0049%20worth%20$59000.00%20awarded%20to%20Edgesource%20Corporation,for%20WINDTALKER%20SYSTEM%2C%20INSTALLATION%20AND%20SERVICE%20DESK. (accessed Feb. 27, 2025)

## Statement of Contributions
Amanda Bacon: Formulating the Problem, Specifications and Constraints, Skills, Broader Implications 

Brett Ballew: Resources, Budget, Skills, References, Specific Implications 

Tyler Bare: Measures of Success, Timeline, Skills, References, Broader Implications

Erich Krepps: Survey of Existing Solutions, Specific Implications, Broader Implications, Skills, References 

Elle Renfroe: Introduction, Background, Skills, References 
