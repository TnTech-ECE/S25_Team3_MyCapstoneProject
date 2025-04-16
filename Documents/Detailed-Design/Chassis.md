# <div align="center"> Drone Tracker Detailed Design
### <div align="center"> Chassis Module
#### <div align="center"> Amanda Bacon
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
  
## Function of the Subsystem
The chassis for the drone tracking system is the housing that will protect and organize all the other components that make up the device. It will hold the electrical components together in a compact and orderly fashion and keep them safe from dust, dirt, debris, water, and other foreign substances. Since the drone tracking system will be located outside, the chassis is a crucial component in weather-proofing the system and keeping it cool. 

## Specifications and Constraints
1. The chassis shall be water and humidity resistant. It shall protect the internal electronics from water ingress due to rain storms, snow storms, water jets, high humidity, and similar hazards. 
2. The chassis shall be dust and dirt resistant, preventing buildup that could block vents or short-circuit components. It shall have an ingress protection rating of IP66 to ensure a dust tight and water jet protected experience for the power supply and Raspberry Pi.
4. The chassis shall be external temperature resistant. It shall operate reliably in the wide range of temperatures typical of Tennessee weather, using ventilation and fans to keep the operational temperature between -40 and 85 degrees celsius.
5. The chassis shall be shock resistant. It shall protect the internal components from damage due to drops, vibrations, or knocks. 
6. The chassis shall be wind resistant. It shall ensure that the device stays anchored or intact during strong gusts or extreme wind.
7. The chassis shall not significantly attenuate or block incoming Wifi or Bluetooth signals.
8. The chassis shall hold the other physical components together and in place. It shall keep all the internal and external components securely mounted and organized.

## Overview of Proposed Solution
The chassis shall be a 3D printed structure specifically tailored to the needs of the drone tracking device. 

#### Key Design Choices

## Interface with Other Subsystems
The chassis shall integrate with the other physical atomic subsystems by securing and protecting their hardware components. 
- Power Supply: The chassis shall , ensuring stable power delivery.
- Central Computer: The chassis shall provide mounting points and protection for the Raspberry Pi. 

## 3D Model of Custom Mechanical Components


## BOM

| Component               | Manufacturer | Part No.    | Distributor | Qty | Unit Price | Total  |
|-------------------------|--------------|-------------|------------|-----|------------|--------|
| blank                   | blank        | blank       | blank      | 1   |  blank     |        |
| **Total**               |              |             |            |     |            | **$blank**|

## Analysis

### Budget Analysis

### Component-Specific Considerations

### Safety Margin Justification

### Verification Methodology



## References
purpose of chassis (general): https://www.trentonsystems.com/en-us/resource-hub/blog/what-is-a-chassis 
best 3d print materials for outdoor use: https://all3dp.com/1/best-3d-printing-materials-for-outdoor-use/
ip ratings https://www.nemaenclosures.com/blog/ingress-protection-ratings/ 
