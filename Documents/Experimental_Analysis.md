# <div align="center"> Drone Tracker Experimental Analysis
#### <div align="center"> Amanda Bacon, Tyler Bare, Brett Ballew, Gabrielle Renfroe, Erich Krepps
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">

  
## Experiment 1: [Experiment Title Here]

### Purpose and Justification
Explain why this experiment was designed and how it relates to your critical success criteria.  
Clearly describe what question this experiment is trying to answer and what part of the system it validates.

### Detailed Procedure
Describe the step-by-step process of how this experiment was conducted.  
Include hardware setup, software configuration, testing conditions, and data collection methods.  
Ensure another team could replicate your work using only this description.

### Expected Results
State the hypothesis or expected outcomes **before** running the experiment.  
Include relevant equations, signal characteristics, or theoretical predictions.

I expect the system to be able to track a drone on campus. Also, it should be able to display the location and information on the website.

### Actual Results
Present your collected data clearly.  
You can use:
- Tables (Markdown-formatted)
- Images (e.g., waveform screenshots)
- Graphs (linked from repo or plotted via code)

Example:

| **Test Condition** | **Measured Voltage (V)** | **Expected (V)** | **% Error** |
|:-------------------:|:------------------------:|:----------------:|:------------:|
| 5V Input | 4.96 | 5.00 | 0.8% |
| 3.3V Input | 3.28 | 3.30 | 0.6% |

### Interpretation and Conclusions
Interpret your results and discuss what they mean.  
- Did results meet your expectations?  
- Were there discrepancies?  
- How do these findings support (or challenge) your project’s success criteria?  
Include detailed reasoning supported by your data.

---

## Experiment 2: [Experiment Title Here]

*(Repeat the same structure as above for each experiment — typically 3–5 experiments total.)*

### Purpose and Justification
[Write here.]

### Detailed Procedure
[Write here.]

### Expected Results
[Write here.]

### Actual Results
[Write here.]

### Interpretation and Conclusions
[Write here.]

---

## Summary of Experimental Outcomes

Overall, the experimental results collectively demonstrate that the system functions as intended: it reliably detects drones operating within range of the Raspberry Pi unit, retrieves their geolocation and identifying RID data, stores this information on a central server, and uploads it to a secure website where Tennessee Tech campus police are alerted when new drones appear and can view their positions on a map. Testing confirmed that the detection and reporting pipeline is consistent and accurate, though a noticeable delay exists between initial detection and server-side display. As anticipated during the design phase, expanding coverage across the entire TTU campus will require a network of multiple Raspberry Pis to ensure continuous detection and minimize blind spots. 

This section evaluates how effectively the final drone tracking system met the specifications and constraints established at the beginning of the project. The requirements provided by the TTU campus police department formed the foundation for the system’s functional goals, and the legal and ethical constraints guided the design decisions throughout development. As detailed in the following subsections, the completed system meets the intent of the required specifications and operates within the stated constraints. Each specification is addressed individually, with justification and performance evidence provided to demonstrate to what extent the implemented system fulfills the original project objectives.

## Documenting and Tracking Components

### Initial Inventory

All components ordered, borrowed, or assigned are listed below. Each item includes vendor/source, order ID, cost, and assigned storage location.

| **Item #** | **Description** | **Quantity** | **Vendor / Source** | **Order # / ID** | **Storage Location (Lab Station / Box #)** | **Date Acquired** | **Condition (New / Used)** | **Notes (Experiment Used, Damaged, Returned)** |
|:-----------:|----------------|:-------------:|---------------------|------------------|--------------------------------------------|-------------------|----------------------------|------------------------------------------------|
| 001 | GeeekPi nRF52840 Micro Dev Kit USB Dongle | 1 | Amazon | B07MJ12XLG | ? | ASAP | New | Used in SDR Interface Testing |
| 002 | JAPOO W50L-5DB WiFi Adapter | 1 | Amazon | B0DBLL14NP | ? | ASAP | New | Used for Wi-Fi Signal Capture |
| 003 | SONOFF Zigbee 3.0 USB Dongle Plus-E Gateway | 1 | Amazon | B06P22YJC | ? | ASAP | New | Used in Zigbee Node Testing |
| 004 | SanDisk 128GB Ultra microSDXC | 1 | Amazon | B07NYT2S6 | ? | ASAP | New | OS Storage for Raspberry Pi 5 |
| 005 | DHT Electronics Socket Jack Female RF Coaxial Connector | 1 | Amazon | B00CXC0SZ4 | ? | 8/15/2025 | New | Used in Antenna Connector Assembly |
| 006 | Jadaol Cat6 Ethernet Cable (50 ft) | 1 | Amazon | B00MWD17GQ | ? | 8/15/2025 | New | Used in PoE Testing Setup |
| 007 | UeeKKoo ORD-CMA-Antenna | 1 | Amazon | B0D4MKJHXJ | ? | 8/15/2025 | New | Used in Drone Antenna Simulation |
| 008 | Waveshare PoE HAT for Raspberry Pi | 1 | Amazon | B0928ZD7QQ | ? | 8/15/2025 | New | Used in Pi 5 PoE Power Testing |
| 009 | ThePoEStore Single Port PoE Injector | 1 | Amazon | B07V24C4M8 | ? | 8/15/2025 | New | Used in PoE Power Delivery Testing |
| 010 | YDDECW 14/2 UF-B Cable (25 ft) | 1 | Amazon | B0DF2Q5LGX | ? | 8/15/2025 | New | Used for AC/DC Power Simulation |
| 011 | Amazon Basics Ethernet Cable (10 ft) | 1 | Amazon | B00N2VIALK | ? | 8/15/2025 | New | Used in Network Interconnects |
| 012 | TTU Printing Services Drone Tracker Chassis Decal | 2 | TTU Printing Services | N/A | ? | 8/15/2025 | New | Used for Project Labeling |
| 013 | UCTRONICS PoE Hat for Raspberry Pi 5 | 1 | Amazon | B0DBHFQ1TC | ? | 8/15/2025 | New | Replaced failed PoE HAT (F) unit |
| 014 | Waterproof Chassis Enclosure (Project Box) | 1 | Provided by Customer | N/A | ? | 8/15/2025 | New | Provided at no cost by customer; used as main system enclosure |

---

### Usage Tracking

| **Experiment #** | **Items Used** | **Condition Changes (if any)** | **Notes** |
|:-----------------:|----------------|-------------------------------|-----------|
| 1 | Items #001, #002, #004 | None | N/A |
| 2 | Items #003, #007 | None | N/A |
| 3 | Items #008, #009, #010 | None | N/A |

---

## Statement of Contributions

Amanda Bacon: ...

Tyler Bare: Initial Inventory, Usage Tracking

Brett Ballew: ...

Gabrielle Renfroe: ...

Erich Krepps: ...
