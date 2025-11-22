# <div align="center"> Drone Tracker Experimental Analysis
#### <div align="center"> Amanda Bacon, Tyler Bare, Brett Ballew, Gabrielle Renfroe, Erich Krepps
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">


## Experiment 1: Range and Detection Latency of Wi-Fi & Bluetooth Drone RID Signals

### Purpose and Justification

This experiment was designed to evaluate how well the drone-tracking system detects Remote ID (RID) signals broadcast over Bluetooth and Wi-Fi, and how quickly detection occurs at various distances.

This aligns with the project’s critical success criteria:
- The system must track a drone on campus using its RID signal.
- The system must display the drone’s ID and location data on the website.
- The system must demonstrate sufficient range, signal reliability, and detection latency for real-time campus-scale tracking.
This experiment validates the RF receiver hardware, RID-processing pipeline, and backend detection logic.

### Detailed Procedure

#### System Setup
- The receiver hardware and software were installed at the Tucker Stadium announcer’s box, approximately 50 ft above ground level.
- The system was configured to continuously scan for:
  - Bluetooth RID packets from aftermarket transmitters.
  - Wi-Fi RID beacons on channel 6 (used by the Parrot Anafi AI drone).

#### Transmitters Used
- Bluetooth RID: Aftermarket Potensic Bluetooth RID transmitter.
- Wi-Fi RID: Parrot Anafi AI drone (flight disabled; RID active only).

#### Testing Process
- Two team members walked away from the stadium in a straight line:
  - One carried the Bluetooth RID transmitter.
  - The other carried the Parrot Anafi AI emitting Wi-Fi RID.
- Distances were pre-marked:
  - Bluetooth: 5m → 200m
  - Wi-Fi: 5m → 1000m
- At each distance:
  - The transmitter was held stationary.
  - The team waited for the system to detect the RID signal.
  - Detection time was recorded from arrival to first logged RID packet.
  - If no detection occurred, it was recorded as N/A.

#### Data Collection
- All detections were verified using the system’s backend logs.
- Data was recorded in tabular form (shown below).

### Expected Results
Ahead of testing, expectations were:

- Wi-Fi RID (higher power and modulation robustness) should exceed Bluetooth in detection range.
- Bluetooth RID expected to be reliable at short to moderate distances (up to ~150–200m).
- Detection times should be fastest at close range (≈2–5 seconds) and increase with distance.
- The system should be capable of reliably detecting RID-equipped drones on campus and displaying them on the website.

### Actual Results
#### Bluetooth RID Detection
| Distance | Detected | Detection Time |
|:--------:|:--------:|:---------------:|
| 5m       | Yes      | 2.21 s          |
| 10m      | Yes      | 2.30 s          |
| 20m      | Yes      | 2.30 s          |
| 50m      | Yes      | 4.02 s          |
| 100m     | Yes      | 8.32 s          |
| 150m     | Yes      | 20.14 s         |
| 200m     | No       | N/A             |

#### Wi-Fi RID Detection
| Distance | Detected | Detection Time |
|:--------:|:--------:|:----------------:|
| 5m       | Yes      | 2.27 s           |
| 10m      | Yes      | 2.29 s           |
| 20m      | Yes      | 2.32 s           |
| 50m      | Yes      | 3.89 s           |
| 100m     | Yes      | 4.10 s           |
| 150m     | Yes      | 12.28 s          |
| 200m     | Yes      | 12.40 s          |
| 300m     | Yes      | 16.93 s          |
| 600m     | Yes      | 24.67 s          |
| 1000m    | No       | N/A              |

### Interpretation and Conclusions
- Wi-Fi RID significantly outperformed Bluetooth in range, remaining detectable up to 600 meters, whereas Bluetooth detection ended around 150–180 meters.
- Detection latency increased with distance, consistent with reduced signal strength.
  - At close range, both protocols detected in ~2.2–2.3 seconds.
  - At long range, Wi-Fi detection reached ~25 seconds at 600m.
- The system successfully detected both Bluetooth and Wi-Fi RID signals, supporting the core requirement for drone tracking.
- Bluetooth RID is not suitable for long-range campus coverage, but it works well at short to mid-range.
- Wi-Fi RID is effective for campus-scale monitoring, validating its use as the system’s primary detection method.
- Elevating the receiver (50 ft up) clearly improved performance; further elevation or directional antennas could extend coverage even more.
  
## Experiment 2: [Experiment Title Here]

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

## Experiment 3: [Experiment Title Here]

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
| 01 | GeeekPi nRF52840 Micro Dev Kit USB Dongle | 1 | Amazon | B07MJ12XLG | ? | 8/15/2025 | New | Used in SDR Interface Testing |
| 02 | JAPOO W50L-5DB WiFi Adapter | 1 | Amazon | B0DBLL14NP | ? | 8/15/2025 | New | Used for Wi-Fi Signal Capture |
| 03 | SONOFF Zigbee 3.0 USB Dongle Plus-E Gateway | 1 | Amazon | B06P22YJC | ? | 8/15/2025 | New | Used in Zigbee Node Testing |
| 04 | SanDisk 128GB Ultra microSDXC | 1 | Amazon | B07NYT2S6 | ? | 8/15/2025 | New | OS Storage for Raspberry Pi 5 |
| 05 | DHT Electronics Socket Jack Female RF Coaxial Connector | 1 | Amazon | B00CXC0SZ4 | ? | 8/15/2025 | New | Used in Antenna Connector Assembly |
| 06 | Jadaol Cat6 Ethernet Cable (50 ft) | 1 | Amazon | B00MWD17GQ | ? | 8/15/2025 | New | Used in PoE Testing Setup |
| 07 | UeeKKoo ORD-CMA-Antenna | 1 | Amazon | B0D4MKJHXJ | ? | 8/15/2025 | New | Used in Drone Antenna Simulation |
| 08 | Waveshare PoE HAT for Raspberry Pi | 1 | Amazon | B0928ZD7QQ | ? | 8/15/2025 | New | Used in Pi 5 PoE Power Testing |
| 09 | ThePoEStore Single Port PoE Injector | 1 | Amazon | B07V24C4M8 | ? | 8/15/2025 | New | Used in PoE Power Delivery Testing |
| 10 | YDDECW 14/2 UF-B Cable (25 ft) | 1 | Amazon | B0DF2Q5LGX | ? | 8/15/2025 | New | Used for AC/DC Power Simulation |
| 11 | Amazon Basics Ethernet Cable (10 ft) | 1 | Amazon | B00N2VIALK | ? | 8/15/2025 | New | Used in Network Interconnects |
| 12 | TTU Printing Services Drone Tracker Chassis Decal | 2 | TTU Printing Services | N/A | ? | 8/15/2025 | New | Used for Project Labeling |
| 13 | UCTRONICS PoE Hat for Raspberry Pi 5 | 1 | Amazon | B0DBHFQ1TC | ? | 8/15/2025 | New | Replaced failed PoE HAT (F) unit |
| 14 | Waterproof Chassis Enclosure (Project Box) | 1 | Provided by Customer | N/A | ? | 8/15/2025 | New | Provided at no cost by customer; used as main system enclosure |
| 15 | Raspberry Pi 5 (8GB) | 1 | TTU ECE Dept | N/A | ? | 8/15/2025 | New | Main processing unit for Drone Tracker |
| 16 | Raspberry Pi 5 (8GB) | 1 | TTU ECE Dept | N/A | ? | 8/15/2025 | New | Server/Website |
| 17 | Potensic FAA-Compliant Remote ID Broadcast Module | 1 | Amazon / Potensic | N/A | ? | 9/2025 | Used | Used for RID signal testing and validation |
| 18 | Parrot ANAFI Ai Drone | 1 | TTU Police / Testing Loan | N/A | ? | 9/2025 | Used | Used for live-flight RID testing and telemetry validation |

---

### Usage Tracking

| **Experiment #** | **Items Used** | **Condition Changes (if any)** | **Notes** |
|:-----------------:|----------------|-------------------------------|-----------|
| 1 | Items #06, #09, #11, #13, #12, #14, #15, #16, #17, #18  | None | N/A |
| 2 | Items #06, #09, #11, #13, #12, #14, #15, #16, #17, #18  | None | N/A |
| 3 | Items #06, #09, #11, #13, #12, #14, #15, #16, #17, #18  | None | N/A |

---

## Statement of Contributions

Amanda Bacon: ...

Tyler Bare: Initial Inventory, Usage Tracking

Brett Ballew: ...

Gabrielle Renfroe: ...

Erich Krepps: ...
