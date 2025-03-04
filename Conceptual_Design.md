# <div align="center"> Drone Tracker Conceptual Design
#### <div align="center"> Amanda Bacon, Brett Ballew, Tyler Bare, Erich Krepps, Gabrielle Renfroe
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
	
## Introduction 

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
The drone tracking system must comply with all pertinent federal and state laws and with all applicable TTU policies. The way by which this team intends to adhere to each of these laws and policies is explained categorically here.

#### Standards regarding circuit design

#### Standards regarding data retention

### Ethical Responsibilities

### Broader Impact











Standards regarding circuit design: 

- IEC 60364-1 - This standard specifies design, installation, and verification of electrical systems to ensure the safety of living beings and properties near it. It pertains to shock, over-current, fault, power interruption, and interference protections.

	- To ensure compliance with IEC 60364-1 in circuit design, the team will incorporate protective measures against electric shock, overcurrent, faults, power interruptions, and electromagnetic interference by including select components that meet IEC safety standards, implementing proper grounding and insulation, and using circuit breakers or residual-current devices (RCDs) for fault protection. During implementation, the team will adhere to wiring regulations and use correct labeling determined by IEC (International Electrotechnical Commission) to ensure clarity and remove safety risks.

Standards regarding data retention at TTU: 

- TTU Policy 403 - This policy defines procedures and standards for 
the usage of cameras on campus, along with surveillance periods and incident reporting procedures.

	- To ensure compliance with TTU Policy 403, the tracker’s camera will be installed and operated following established surveillance guidelines including proper incident reporting procedures. Access to recorded footage will not be a concern as the camera will only be used for image recognition. 

- TTU Policy 856 - This policy defines standards and requirements for data security and handling. This policy defines four levels of data security, their encryption requirements, and disposal procedures of the data.

	- To ensure compliance with TTU Policy 856, the drone tracking data displayed on the website will be classified according to defined security levels, with appropriate encryption measures in place to protect sensitive information. Data disposal procedures will be strictly followed to prevent unauthorized access or misuse.







for the drones and users themselves: 
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



Standards regarding Unmanned Aerial Systems: 

- FAA 14 CFR Part 107 - This standard regulates the operation of Drones in U.S Airspace, ensuring that pilots operate their drones in a safe manner. Safety standards include limiting maximum altitude to 400 feet (122 meters), prohibiting drones from flying directly over a non-participating human being, and limiting accessible airspace for pilots to fly in without express permission. This standard also addresses recreational flying rules. 
- FAA 14 CFR Part 89 - This standard pertains to the Remote Identification of Drones operating in U.S Airspace. In sections 89.305 and 89.315, the standard details the minimum element requirements of the Remote ID transponder’s broadcast and how often pilots are required to broadcast it. 
- FCC 47 CFR Part 15 - This standard pertains to electrical and electronic devices that emit or absorb radio frequencies within the 9 kHz to 3,000 GHz range. This standard limits power and exposure levels to prevent interference and endangerment to living beings.
- IEEE 802.11 - This regulates implementation standards for WIFI Networks, Local Area Networks, and MAC Address protocols. It also defines frequency bands and collision-avoidance protocols for wireless transmissions. 
 









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
Amanda Bacon: 

Brett Ballew:  

Tyler Bare: 

Erich Krepps:  

Elle Renfroe: 
