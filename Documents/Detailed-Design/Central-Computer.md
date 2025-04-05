# <div align="center"> Drone Tracker Detailed Design
### <div align="center"> Central Computer Module
#### <div align="center"> Brett Ballew
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
  
## Function of the Subsystem
The power supply module is responsible for delivering stable and efficient power to the Central Computer Module, which serves as the central computer for the drone tracking system. This module ensures continuous operation by converting alternating current (AC) from a standard wall outlet to a regulated 5 V DC output, while incorporating surge and overcurrent protection to safeguard sensitive electronics. The subsystem adheres to IEC 60364-1 safety standards, preventing electrical hazards and ensuring reliable performance in varied environmental conditions.


## Specifications and Constraints
The power supply shall provide stable and efficient power to the Central Computer Module.
- To ensure stable and efficient power delivery, the MeanWell LRS-50-5 power supply was selected for its precisely regulated 5V DC (±5%) output. Advanced filtering circuitry maintains output ripple below 50mV, preventing voltage fluctuations that could disrupt Raspberry Pi operation. With an efficiency rating of 89%, the unit minimizes power loss and heat generation while delivering consistent performance across all operating conditions.

The power supply shall be mounted within the chassis for protection and thermal management.
- The LRS-50-5 unit is securely mounted inside the IP66-rated enclosure using specialized anti-vibration screws that prevent movement while accommodating thermal expansion. A 30 BTU through-wall cooling system actively maintains optimal operating temperatures by dissipating heat buildup. The chassis provides complete environmental protection, meeting IP66 standards for being both dust-tight and resistant to powerful water jets, making it suitable for permanent outdoor deployment.

The power supply shall operate from 100-240 V AC at 50/60 Hz.
- Designed for global compatibility, the LRS-50-5 automatically adjusts to accept any AC input voltage between 100-240V at either 50 or 60Hz frequency. This universal input capability ensures reliable operation when connected to standard wall outlets worldwide. Power is delivered through a heavy-duty C13 power cable rated for continuous use, with reinforced strain relief at the connection points to prevent wear.

The power supply shall deliver a continuous 25 W output.
- While rated for a maximum 50W output (5V at 10A), the power supply typically operates at just 50% of capacity when powering the Raspberry Pi, providing substantial headroom for peak loads. This derating significantly extends the unit's operational lifespan while maintaining stable output. A 5A fast-acting fuse provides additional protection against potential overload conditions.

The power supply shall incorporate surge and overcurrent protection.
- Multiple protection layers are implemented, beginning with a metal oxide varistor (MOV) that instantly clamps any voltage spikes above 250V from the AC line. A 2A slow-blow fuse protects against sustained overcurrent conditions, while the power supply's built-in safeguards include automatic shutdown for short-circuit, overload, and overvoltage scenarios. These redundant protection systems ensure both device safety and continuous operation.

The power supply shall comply with IEC 60364-1 for electrical safety.
- The MeanWell LRS-50-5 carries full certification to UL/IEC/EN 62368-1 safety standards, exceeding the basic IEC 60364-1 requirements. All wiring employs double-insulated conductors with proper creepage and clearance distances. The design maintains complete galvanic isolation between the AC input and DC output sides, with reinforced insulation barriers tested to 3000VAC.

The power supply shall connect to the Raspberry Pi via a barrel jack.
- Power delivery to the Raspberry Pi is accomplished through a locking 5.5×2.1mm barrel jack connector that prevents accidental disconnection. The cable incorporates strain relief booting at both ends, and the connector's polarized design ensures proper orientation. Gold-plated contacts minimize resistance and prevent corrosion over time.

The power supply shall remain within a -40°C to 85°C operational temperature range.
- Engineered for industrial environments, the LRS-50-5 maintains full specification operation across the entire temperature range. The IP66 enclosure provides additional protection against thermal cycling and moisture ingress. The cooling system's design accounts for worst-case ambient conditions, maintaining safe operating temperatures even during extended high-load periods.

The power supply shall cost less than $60 per unit.
- Through careful component selection and leveraging commercial off – the – shelf solutions, the complete power subsystem maintains a total cost of $60 per unit. This includes all necessary cabling, connectors, and protection devices while staying well below the budget threshold. The design achieves this cost efficiency without compromising on quality or reliability.

The power supply shall minimize maintenance requirements.
- The completely solid-state design eliminates all moving parts, removing wear items like fans from the system. The sealed IP66 enclosure prevents dust and moisture ingress that could degrade components over time. Industrial-grade capacitors and other components are rated for at least 100,000 hours of continuous operation, ensuring long-term reliability with minimal maintenance needs.



## Overview of Proposed Solution
The power supply subsystem is designed to provide reliable, efficient, and safe power conversion for the drone tracking system’s central computer (Raspberry Pi 4 B). Given the system’s 24/7 operational requirements and deployment in outdoor, weather-exposed conditions, the power supply must meet stringent performance, safety, and durability standards.

#### Key Design Choices
Switching Power Supply (MeanWell LRS-50-5)
- Selected for its high efficiency (89%), compact size, and compliance with UL/IEC/EN 62368-1 safety standards. Unlike linear regulators, a switching design minimizes heat generation while maintaining stable voltage under load fluctuations.

Surge & Overcurrent Protection
- Metal Oxide Varistor (MOV) clamps transient voltage spikes (>250V) from AC mains. 2A slow-blow fuse protects against sustained overcurrent, preventing catastrophic failure. Built-in protections in the LRS-50-5 (overload/short-circuit/overvoltage) add redundancy.

Thermal & Environmental Resilience
- Fanless operation eliminates mechanical wear, critical for long-term reliability. IP66-rated enclosure shields electronics from rain, dust, and humidity. Through-wall cooler (30 BTU) passively dissipates heat, ensuring stable operation in -40°C to 85°C environments.

Raspberry Pi Integration
- 5.5×2.1mm barrel jack ensures secure power delivery with reverse-polarity prevention. Low ripple (<50mV) avoids voltage instability that could crash the Raspberry Pi.

Why This Solution Works
- Compliance with Standards: Meets IEC 60364-1 for electrical safety and FCC Part 15 for EMI limits. Scalability: Modular design allows replication across all 10 campus units.
- Cost-Effectiveness: Off-the-shelf components keep unit cost under $30, freeing budget for other subsystems.

Validation Approach
- Lab Testing: Verify voltage stability under load (0–5A) using oscilloscope measurements.
- Environmental Stress Testing: Confirm operation in high-temperature (85°C) and humid conditions.
- Longevity Testing: Simulate 1,000+ hours of continuous use to validate durability.


## Interface with Other Subsystems
Provide detailed information about the inputs, outputs, and data transferred to other subsystems. Ensure specificity and thoroughness, clarifying the method of communication and the nature of the data transmitted.


## 3D Model of Custom Mechanical Components
<img src= "/Documents/Images/Detailed Design Power Supply 3D model #1.png" width="2000" height="900">

<img src= "/Documents/Images/Detailed Design Power Supply 3D model #2.png" width="2000" height="900">



## Buildable Schematic 
Integrate a buildable electrical schematic directly into the document. If the diagram is unreadable or improperly scaled, the supervisor will deny approval. Divide the diagram into sections if the text and components seem too small.

The schematic should be relevant to the design and provide ample details necessary for constructing the model. It must be comprehensive so that someone, with no prior knowledge of the design, can easily understand it. Each related component's value and measurement should be clearly mentioned.


## Printed Circuit Board Layout
Include a manufacturable printed circuit board layout.

## BOM

| Component               | Manufacturer | Part No.    | Distributor | Qty | Unit Price | Total  |
|-------------------------|--------------|-------------|------------|-----|------------|--------|
| MeanWell LRS-50-5 PSU   | MeanWell     | LRS-50-5    | Digi-Key   | 1   | $18.50     | $18.50 |
| C13 Power Cord          | Tripp Lite   | P004-006    | Amazon     | 1   | $6.99      | $6.99  |
| 5.5x2.1mm DC Jack       | Amphenol     | DCJ020-5A-K | Mouser     | 1   | $1.20      | $1.20  |
| 2A Fuse Holder          | Littelfuse   | 0343002.H   | Arrow      | 1   | $2.50      | $2.50  |
| **Total**               |              |             |            |     |            | **$29.19**|

## Analysis
The power supply subsystem has been designed to meet all operational requirements while providing substantial safety margins. The MeanWell LRS-50-5 power supply was selected after thorough analysis of the system's power demands and operational constraints.

### Power Budget Analysis
The Raspberry Pi 4B represents the primary power consumer in the system, with maximum power draw specifications of 5V at 3.0A (15W) under peak load conditions. When combined with peripheral components including Wi-Fi and Bluetooth transceivers, the total system power requirement remains well below the power supply's 50W capacity. This substantial derating provides multiple benefits:

- Thermal Management: Operating at approximately 30% of maximum capacity significantly reduces heat generation and improves long-term reliability.
- Future Expansion: The 50W capacity allows for addition of future components or upgraded versions of existing modules without requiring power supply replacement.
- Voltage Stability: The generous power headroom ensures stable voltage regulation even during current transients or startup surges.

### Component-Specific Considerations
The power supply's 5V output directly matches the voltage requirements of all system components. Particular attention was given to:

- Raspberry Pi 4B Requirements: The 5V/3A (15W) specification is comfortably supported, with the power supply capable of delivering more than three times this current if needed.
- Transceiver Modules: The integrated Wi-Fi and Bluetooth components add minimal additional load (typically <1W combined), representing negligible impact on the power budget.
- Ancillary Circuits: All support components including status LEDs and cooling system controls operate within the ample remaining capacity.

### Safety Margin Justification
The design incorporates a 2:1 safety margin between maximum expected load (25W) and power supply capacity (50W). This margin accounts for:

- Peak Current Demands: Brief current spikes during processor-intensive operations
- Component Aging: Gradual efficiency reduction over the system's operational life
- Environmental Factors: Performance degradation in high-temperature conditions
- Measurement Uncertainty: Variations in actual versus specified power consumption

### Cost-Benefit Analysis
While lower-capacity power supplies were considered, the LRS-50-5 provides optimal value by:

- Eliminating the need for future upgrades as the system expands
- Reducing thermal stress through lower operating temperatures
- Improving reliability through reduced component stress
- Maintaining cost-effectiveness at just $18.50 per unit

### Verification Methodology
The design will be validated through:
- Load Testing: Measuring voltage regulation from 0-10A load
- Efficiency Testing: Confirming >85% efficiency across operating range
- Thermal Testing: Monitoring temperature rise at maximum continuous load
- Transient Response: Evaluating performance during load steps


## References

MEAN WELL LRS-50-5 50W 5VDC 10A Single Ouput Switching Mode Power Supply Amazon: https://www.amazon.com/MEAN-WELL-LRS-50-5-Single-Switching/dp/B085QKVLB6 Datasheet: https://www.meanwell.com/Upload/PDF/LRS-50/LRS-50-SPEC.PDF
