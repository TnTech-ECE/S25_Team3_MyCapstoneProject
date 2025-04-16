# <div align="center"> Drone Tracker Detailed Design
### <div align="center"> Power Supply Module
#### <div align="center"> Tyler Bare
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
  
## Function of the Subsystem
The power supply module is responsible for delivering stable and efficient power to the Raspberry Pi 5, which serves as the central computer for the drone tracking system. This module ensures continuous operation by converting alternating current (AC) from a standard wall outlet to a regulated 5 V DC output, while incorporating surge and overcurrent protection to safeguard sensitive electronics. The subsystem adheres to IEC 60364-1 safety standards, preventing electrical hazards and ensuring reliable performance in varied environmental conditions.


## Specifications and Constraints
The power supply shall provide stable and efficient power to the Central Computer Module.
- To ensure stable and efficient power delivery, the MeanWell LRS-50-5 power supply was selected for its precisely regulated 5 V DC (±5%) output. Advanced filtering circuitry maintains output ripple below 50mV, preventing voltage fluctuations that could disrupt Raspberry Pi operation. With an efficiency rating of 89%, the unit minimizes power loss and heat generation while delivering consistent performance across all operating conditions.

The power supply shall be mounted within the chassis for protection and thermal management.
- The LRS-50-5 unit is securely mounted inside the IP66-rated enclosure using screws while accommodating thermal expansion. The chassis provides complete environmental protection, meeting IP66 standards for being both dust-tight and resistant to powerful water jets, making it suitable for permanent outdoor deployment.

The power supply shall operate from 100-240 V AC at 60 Hz.
- Designed for global compatibility, the LRS-50-5 automatically adjusts to accept any AC input voltage of 120 V at 60 Hz frequency. This universal input capability ensures reliable operation when connected to standard wall outlets. Power is delivered through a heavy-duty C13 power cable rated for continuous use, with reinforced strain relief at the connection points to prevent wear.

The power supply shall deliver a continuous 25 W output.
- While rated for a maximum 50 W output (5 V at 10 A), the power supply typically operates at just 50% of capacity when powering the Raspberry Pi, providing substantial headroom for peak loads. This derating significantly extends the unit's operational lifespan while maintaining stable output. A 5 A fast-acting fuse provides additional protection against potential overload conditions.

The power supply shall incorporate surge and overcurrent protection.
- Multiple protection layers are implemented, beginning with a metal oxide varistor (MOV) that instantly clamps any voltage spikes above 250 V from the AC line. A 2 A slow-blow fuse protects against sustained overcurrent conditions, while the power supply's built-in safeguards include automatic shutdown for short-circuit, overload, and overvoltage scenarios. These redundant protection systems ensure both device safety and continuous operation.

The power supply shall comply with IEC 60364-1 for electrical safety.
- The MeanWell LRS-50-5 carries full certification to UL/IEC/EN 62368-1 safety standards, exceeding the basic IEC 60364-1 requirements. All wiring employs double-insulated conductors with proper creepage and clearance distances. The design maintains complete galvanic isolation between the AC input and DC output sides, with reinforced insulation barriers tested to 3000 VAC.

The power supply shall connect to the Raspberry Pi via a barrel jack.
- Power delivery to the Raspberry Pi is accomplished through a locking 5.5×2.1 mm barrel jack connector that prevents accidental disconnection. The cable incorporates strain relief booting at both ends, and the connector's polarized design ensures proper orientation. Nickel-plated contacts minimize resistance and prevent corrosion over time.

The power supply shall remain within a -40°C to 85°C operational temperature range.
- Engineered for industrial environments, the LRS-50-5 maintains full specification operation across the entire temperature range. The IP66 enclosure provides additional protection against thermal cycling and moisture ingress. The cooling system's design accounts for worst-case ambient conditions, maintaining safe operating temperatures even during extended high-load periods.

The power supply shall minimize maintenance requirements.
- The completely solid-state design eliminates all moving parts, removing wear items like fans from the system. The sealed IP66 enclosure prevents dust and moisture ingress that could degrade components over time. Industrial-grade capacitors and other components are rated for at least 100,000 hours of continuous operation, ensuring long-term reliability with minimal maintenance needs.



## Overview of Proposed Solution
The power supply subsystem is designed to provide reliable, efficient, and safe power conversion for the drone tracking system’s central computer (Raspberry Pi 5). Given the system’s 24/7 operational requirements and deployment in outdoor, weather-exposed conditions, the power supply must meet stringent performance, safety, and durability standards.

#### Key Design Choices
Switching Power Supply - MeanWell LRS-50-5
- Selected for its high efficiency (89%), compact size, and compliance with UL/IEC/EN 62368-1 safety standards. Unlike linear regulators, a switching design minimizes heat generation while maintaining stable voltage under load fluctuations.

Surge & Overcurrent Protection
- Metal Oxide Varistor (MOV) clamps transient voltage spikes (>250V) from AC mains. 2 A slow-blow fuse protects against sustained overcurrent, preventing catastrophic failure. Built-in protections in the LRS-50-5 (overload/short-circuit/overvoltage) add redundancy.

Thermal & Environmental Resilience
- Fanless operation eliminates mechanical wear, critical for long-term reliability. IP66-rated enclosure shields electronics from rain, dust, and humidity. Through-wall cooler (30 BTU) passively dissipates heat, ensuring stable operation in -40°C to 85°C environments.

Outdoor Wiring Method  
- 12/2 UF-B cable (Southwire 13128202) for exposed outdoor AC power delivery  
- NEC 225.22/340-compliant without conduit when properly supported  
- GFCI protection at source outlet (NEC 210.8)

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
The power supply module delivers power to the Raspberry Pi 5 subsystem while receiving input from standard AC mains. All connections are designed for reliability, safety, and minimal voltage drop.

### AC Main Input Interface

| Parameter               | Specification                                           |
|------------------------|---------------------------------------------------------|
| Connection Type        | Hardwired screw terminals (IEC 61076-2-101 compliant)  |
| Voltage                | 100-240V AC, 50/60 Hz                                   |
| Current                | 1.5 A max at 100 V, 0.7 A max at 240 V                    |
| Protection             | MOV (VDRM250) for surge suppression<br>2 A slow-blow fuse (Littelfuse 0215002.HXP) |
| Cable Requirements     | 18AWG minimum (for 3 A rating)<br>300 V rated insulation<br>C13 connector at wall outlet end |

---

### Raspberry Pi 5 Power Delivery Interface

| Parameter               | Specification                                           |
|------------------------|---------------------------------------------------------|
| Connection Type        | Locking 5.5×2.1mm barrel jack (Amphenol DCJ020-5A-K)  |
| Voltage                | 5 V DC ±5% (4.75 V-5.25 V)                                |
| Current                | 0-10 A continuous (50 W max)                            |
| Ripple                 | <50 mV p-p                                              |
| Cable Specifications   | 16AWG stranded copper (for low voltage drop)<br>Double-insulated<br>1.5m maximum length |

---

### Protection System Interfaces

| Protection Type        | Specification                                           |
|------------------------|---------------------------------------------------------|
| Overcurrent Protection | Open-collector fault signal (5 V, 10 mA max)<br>Connects to Raspberry Pi GPIO |
| Thermal Protection     | Normally-closed thermal switch (70°C trip)<br>Series with DC output |


## 3D Model of Custom Mechanical Components
<img src="/Documents/Images/Detailed%20Design%20Power%20Supply%203D%20model%20%233.png" width="2000" height="900">

<div align="center"> <img src="/Documents/Images/Power Supply Dimensions.png" width="600" height="800">
<div align="left">


## BOM

| Component               | Manufacturer | Part No.    | Distributor | Qty | Unit Price | Total  |
|-------------------------|--------------|-------------|------------|-----|------------|--------|
| MeanWell LRS-50-5 PSU   | MeanWell     | LRS-50-5    | Amazon     | 1   | $16.91     | $16.91 |
| C13 Power Cord          | Tripp Lite   | P004-006    | Amazon     | 1   | $6.99      | $6.99  |
| 5.5x2.1 mm DC Jack      | Amphenol     | DCJ020-5A-K | Mouser     | 1   | $1.20      | $1.20  |
| 2 A Fuse Holder         | Littelfuse   | F5749-ND    | Digi-Key   | 1   | $2.65      | $2.65  |
| UF-B Cable (25 ft.)     | Southwire    | 13055921    | Amazon     | 1   | $39.98     | $39.98  |
| **Total**               |              |             |            |     |            | **$67.73**|

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

NEC Compliance Verification 
- UF-B meets 225.22 for exposed outdoor feeders  
- GFCI satisfies 210.8 wet location requirements  
- Physical protection via IP66 enclosure and secure routing

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

Littelfuse 2A Slow-Blow Fuse (0215002.HXP) Datasheet: https://www.littelfuse.com/~/media/electronics/datasheets/fuses/littelfuse_fuse_0215_2_hxp_datasheet.pdf

IP66 Enclosure Standards (IEC 60529): https://www.iec.ch/standards

IEC 60364-1 Electrical Installation Standards: https://webstore.iec.ch/publication/6376
