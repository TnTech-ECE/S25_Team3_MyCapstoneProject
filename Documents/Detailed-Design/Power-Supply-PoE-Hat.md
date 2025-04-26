# <div align="center"> Drone Tracker Detailed Design
### <div align="center"> Power Supply Module (PoE Hat)
#### <div align="center"> Tyler Bare
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
  
## Function of the Subsystem
The power supply module is responsible for delivering stable and efficient power to the Raspberry Pi 5, which serves as the central computer for the drone tracking system. This module ensures continuous operation by converting alternating current (AC) from a standard wall outlet to a regulated 5 V DC output, while incorporating surge and overcurrent protection to safeguard sensitive electronics. The subsystem adheres to IEC 60364-1 safety standards, preventing electrical hazards and ensuring reliable performance in varied environmental conditions.


## Specifications and Constraints
The power supply shall provide stable and efficient power to the Central Computer Module.  
- The PoE HAT delivers **5V DC ±5%** via direct board-to-board connection, with built-in DC-DC conversion (<50mV ripple). Efficiency exceeds **85%** under typical loads (IEEE 802.3af compliant).  

The power supply shall be mounted within the chassis for protection and thermal management.  
- The HAT attaches directly to the Raspberry Pi 5’s GPIO header, with an **integrated heatsink and cooling fan**. The IP66 enclosure provides environmental protection.  

The power supply shall operate from 100-240 V AC at 60 Hz.  
- Power is supplied via **802.3af/at PoE switch** (input: 100-240V AC). The HAT accepts **37–57V DC** from PoE and converts it to 5V.  

The power supply shall deliver a continuous 25 W output.  
- Complies with **802.3at (25.5W max)**. The Raspberry Pi 5’s peak draw (15W) leaves 40% headroom.  

The power supply shall incorporate surge and overcurrent protection.  
- **IEEE 802.3af/at** provides inherent surge protection via Ethernet isolation transformers. The HAT includes short-circuit/overload safeguards.  

The power supply shall comply with IEC 60364-1 for electrical safety.  
- The PoE HAT is **UL/IEC 60950-1 certified** and meets IEEE 802.3af/at standards for galvanic isolation.  

The power supply shall connect to the Raspberry Pi via a barrel jack.  
- **Updated:** Power is delivered through the **GPIO header** (no barrel jack). Ethernet replaces AC power cabling.  

The power supply shall remain within a -40°C to 85°C operational range.  
- The HAT’s **active cooling** maintains safe temperatures. The PoE switch operates at -40°C to 75°C.  

The power supply shall cost less than $60 per unit.  
- **Total cost: $54.98** (PoE HAT: $29.99 + 4-port PoE switch: $24.99).  

The power supply shall minimize maintenance requirements.  
- Fan requires occasional dusting. No consumable parts (e.g., fuses) to replace.


## Overview of Proposed Solution
The power supply subsystem is designed to provide reliable, efficient, and safe power conversion for the drone tracking system’s central computer (Raspberry Pi 5). Given the system’s 24/7 operational requirements and deployment in outdoor, weather-exposed conditions, the power supply must meet stringent performance, safety, and durability standards.

#### Key Design Choices
Switching Power Supply - MeanWell LRS-50-5
- Selected for its high efficiency (89%), compact size, and compliance with UL/IEC/EN 62368-1 safety standards. Unlike linear regulators, a switching design minimizes heat generation while maintaining stable voltage under load fluctuations.

Surge & Overcurrent Protection
- Metal Oxide Varistor (MOV) clamps transient voltage spikes (>250V) from AC mains. 2 A slow-blow fuse protects against sustained overcurrent, preventing catastrophic failure. Built-in protections in the LRS-50-5 (overload/short-circuit/overvoltage) add redundancy.

Thermal & Environmental Resilience
- Fanless operation eliminates mechanical wear, critical for long-term reliability. IP66-rated enclosure shields electronics from rain, dust, and humidity. Through-wall cooler (30 BTU) passively dissipates heat, ensuring stable operation in -40°C to 85°C environments.

Raspberry Pi Integration
- 5.5×2.1mm barrel jack ensures secure power delivery with reverse-polarity prevention. Low ripple (<50 mV) avoids voltage instability that could crash the Raspberry Pi.

Why This Solution Works
- Compliance with Standards: Meets IEC 60364-1 for electrical safety and FCC Part 15 for EMI limits. Scalability: Modular design allows replication across all 10 campus units.
- Cost-Effectiveness: Off-the-shelf components keep unit cost under $30, freeing budget for other subsystems.

Validation Approach
- Lab Testing: Verify voltage stability under load (0 – 5 A) using oscilloscope measurements.
- Environmental Stress Testing: Confirm operation in high-temperature (85°C) and humid conditions.
- Longevity Testing: Simulate 1,000+ hours of continuous use to validate durability.


## Interface with Other Subsystems

| **Parameter**          | **Specification**                                      |  
|------------------------|--------------------------------------------------------|  
| **PoE Input**          | 802.3af/at (48V DC, 0.3–0.6A) via Cat6 cable           |  
| **RPi 5 Power**        | 5V ±5% @ 5A max (via GPIO header)                      |  
| **Thermal Control**    | PWM fan (controlled by RPi 5)                          |  


## 3D Model of Custom Mechanical Components
<img src="/Documents/Images/" width="2000" height="900">


## Buildable Schematic 
NOT DONE YET: Integrate a buildable electrical schematic directly into the document. If the diagram is unreadable or improperly scaled, the supervisor will deny approval. Divide the diagram into sections if the text and components seem too small.

The schematic should be relevant to the design and provide ample details necessary for constructing the model. It must be comprehensive so that someone, with no prior knowledge of the design, can easily understand it. Each related component's value and measurement should be clearly mentioned.

## BOM

## BOM

| Component               | Manufacturer | Distributor | Qty | Unit Price | Total  |
|-------------------------|--------------|-------------|-----|------------|--------|
| PoE HAT for Raspberry Pi 5 | Waveshare | Amazon      | 1   | $29.99     | $28.79 |
| Single Port PoE Injector | TP-Link     | Amazon      | 1   | $24.99     | $19.89 |
| Cat6 Ethernet Cable     | Cable Matters| Amazon      | 1   | $8.99      | $8.99  |
| **Total**               |              |             |     |            | **$57.67** |


## Analysis
The power supply subsystem has been designed to meet all operational requirements while providing substantial safety margins. The MeanWell LRS-50-5 power supply was selected after thorough analysis of the system's power demands and operational constraints.

### Power Budget Analysis
The Raspberry Pi 5 represents the primary power consumer in the system, with maximum power draw specifications of 5 V at 3.0 A (15 W) under peak load conditions. When combined with peripheral components including Wi-Fi and Bluetooth transceivers, the total system power requirement remains well below the power supply's 50 W capacity. This substantial derating provides multiple benefits:

- Thermal Management: Operating at approximately 30% of maximum capacity significantly reduces heat generation and improves long-term reliability.
- Future Expansion: The 50 W capacity allows for addition of future components or upgraded versions of existing modules without requiring power supply replacement.
- Voltage Stability: The generous power headroom ensures stable voltage regulation even during current transients or startup surges.

### Component-Specific Considerations
The power supply's 5 V output directly matches the voltage requirements of all system components. Particular attention was given to:

- Raspberry Pi 5 Requirements: The 5 V/3 A (15 W) specification is comfortably supported, with the power supply capable of delivering more than three times this current if needed.
- Transceiver Modules: The integrated Wi-Fi and Bluetooth components add minimal additional load, representing negligible impact on the power budget.
- Ancillary Circuits: All support components including status LEDs and cooling system controls operate within the ample remaining capacity.

### Safety Margin Justification
The design incorporates a 2:1 safety margin between maximum expected load (25 W) and power supply capacity (50 W). This margin accounts for:

- Peak Current Demands: Brief current spikes during processor-intensive operations
- Component Aging: Gradual efficiency reduction over the system's operational life
- Environmental Factors: Performance degradation in high-temperature conditions
- Measurement Uncertainty: Variations in actual versus specified power consumption

### Cost-Benefit Analysis
While lower-capacity power supplies were considered, the LRS-50-5 provides optimal value by:

- Eliminating the need for future upgrades as the system expands
- Reducing thermal stress through lower operating temperatures
- Improving reliability through reduced component stress
- Maintaining cost-effectiveness at just $16.91 per unit

### Verification Methodology
The design will be validated through:
- Load Testing: Measuring voltage regulation from 0 - 10 A load
- Efficiency Testing: Confirming >85% efficiency across operating range
- Thermal Testing: Monitoring temperature rise at maximum continuous load
- Transient Response: Evaluating performance during load steps


## References

MEAN WELL LRS-50-5 50W 5VDC 10A Single Ouput Switching Mode Power Supply Amazon: https://www.amazon.com/MEAN-WELL-LRS-50-5-Single-Switching/dp/B085QKVLB6 Datasheet: https://www.meanwell.com/Upload/PDF/LRS-50/LRS-50-SPEC.PDF

Raspberry Pi 5 Datasheet: https://datasheets.raspberrypi.com/rpi5/raspberry-pi-5-product-brief.pdf
