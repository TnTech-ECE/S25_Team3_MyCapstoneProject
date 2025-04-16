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
2. The chassis shall be dust and dirt resistant, preventing buildup that could block vents or short-circuit components. It shall have a protection rating of IP66 to ensure a dust tight and water jet protected experience for the power supply and Raspberry Pi [3].
4. The chassis shall be external temperature resistant. It shall operate reliably in the wide range of temperatures typical of Tennessee weather, using ventilation and fans to keep the operational temperature between -40 and 85 degrees celsius.
5. The chassis shall be shock resistant. It shall protect the internal components from damage due to drops, vibrations, or knocks. 
6. The chassis shall be wind resistant. It shall ensure that the device stays anchored or intact during strong gusts or extreme wind.
7. The chassis shall not significantly attenuate or block incoming Wifi or Bluetooth signals.
8. The chassis shall hold the other physical components together and in place. It shall keep all the internal and external components securely mounted and organized.
9. The chassis shall allow easy access to the interior components without compromising its IP66 rating. 

## Overview of Proposed Solution
The chassis shall be a 3D printed structure specifically tailored to the needs of the drone tracking device. 

#### Key Design Choices

## Interface with Other Subsystems
The chassis shall integrate with the other physical atomic subsystems by securing and protecting the other hardware components. It shall provide mounting points for the Raspberry Pi, keeping it securely in place with screws and shock absorbing rubber bumpers to protect it from damage from drops, knocks, and vibrations. The Raspberry Pi shall have power supplied to it from a PoE (Power over Ethernet) hat. A Cat 6 Ethernet Cable will be required to plug into the PoE Hat, so an eyelet for the cable shall be included in the chassis design. Weatherproof grommets shall keep water and dirt from entering the device through the eyelet. 

## 3D Model of Custom Mechanical Components
<img src="/Documents/Images/Top of Raspberry Pi Case.png" width="2000" height="900">
<img src="/Documents/Images/Bottom of Raspberry Pi Case.png" width="2000" height="900">


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
[1] E. Ortiz, “What is a Chassis?,” Trentonsystems.com, Jun. 02, 2022. https://www.trentonsystems.com/en-us/resource-hub/blog/what-is-a-chassis (accessed Apr. 16, 2025). 

[2] “Best 3D Printing Materials for Outdoor Use,” All3DP Pro, Apr. 18, 2024. https://all3dp.com/1/best-3d-printing-materials-for-outdoor-use/ (accessed Apr. 16, 2025).  

[3] R. Bohn, “IP Ratings Explained - What Are IP Ratings? | NEMA Enclosures,” Stainless Steel Enclosures | NEMA Enclosures, Aug. 02, 2013. https://www.nemaenclosures.com/blog/ingress-protection-ratings/ (accessed Apr. 16, 2025). 
