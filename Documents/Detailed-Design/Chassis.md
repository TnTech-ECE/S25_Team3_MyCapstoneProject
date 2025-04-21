# <div align="center"> Drone Tracker Detailed Design
### <div align="center"> Chassis Module
#### <div align="center"> Amanda Bacon
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
  
## Function of the Subsystem
The chassis for the drone tracking system is the housing that shall protect and organize all the other components that make up the device. It shall hold the electrical components together in a compact and orderly fashion and keep them safe from dust, dirt, debris, water, and other foreign substances. Since the drone tracking device shall be located outside, the chassis is a crucial component in weather-proofing the system and keeping it cool. 

## Specifications and Constraints
1. The chassis shall be water and humidity resistant. It shall protect the internal electronics from water ingress due to rain storms, snow storms, water jets, high humidity, and similar hazards. 
2. The chassis shall be dust and dirt resistant, preventing buildup that could block vents or short-circuit components. It shall have a protection rating of IP65 to ensure a dust tight and water jet protected experience for the power supply and Raspberry Pi [1].
3. The chassis shall be external temperature resistant. It shall operate reliably in the wide range of temperatures typical of Tennessee weather, using ventilation and fans to keep the operational temperature between -40° and 85° C.
4. The chassis shall be shock resistant. It shall protect the internal components from damage due to drops, vibrations, or knocks. 
5. The chassis shall be wind resistant. It shall ensure that the device stays anchored or intact during strong gusts or extreme wind.
6. The chassis shall not significantly attenuate or block incoming Wifi or Bluetooth signals.
7. The chassis shall securely hold and organize all the other components, keeping them properly mounted and in place.
8. The chassis shall allow easy access to the interior components without compromising its IP65 rating. 

## Overview of Proposed Solution
The chassis shall be a 3D printed structure specifically tailored to the needs of the drone tracking device. It shall consist of two main parts: an interior shell and an exterior shell. The interior shell shall be precisely fitted to the dimensions of the Raspberry Pi with its PoE (Power over Ethernet) hat attached. This shell shall serve as a lidded case, featuring a removable top for easy access to the microcomputer. Its purpose is to keep all the internal components compactly organized and protected from minor bumps or jostling during use. Since the PoE hat includes a 5 V cooling fan, the interior shell shall include ventilation slits to allow airflow and ensure effective heat dissipation. The exterior shell shall serve as a protective enclosure, shielding the internal components from weather and debris. It shall be a larger, sealed box with no openings apart from a single cable eyelet, which shall be secured with a weatherproof grommet to help achieve the desired IP65 rating. This outer shell shall also provide additional space for air circulation around the PoE fan and shall include brackets for mounting the device onto a light post. Specific design choices — such as dimensions, materials, and thermal considerations — will be examined in greater detail in the Analysis section below.

## Interface with Other Subsystems
The chassis shall integrate with the other physical atomic subsystems by securing and protecting their hardware components. It shall provide mounting points for the Raspberry Pi, keeping it securely in place with screws to guard it against damage from drops, knocks, and vibrations. Power will be supplied to the Raspberry Pi via a PoE hat, which requires a Cat 6 Ethernet cable connection. To accommodate this, the chassis will feature an eyelet for the cable. Additionally, the design will allow sufficient space for the PoE hat’s fan to circulate air effectively.

## 3D Model of Custom Mechanical Components
Below are several images of the 3D models for both the interior and exterior shells of the chassis. The first three images model the interior shell. They show the top (lid) portion of the shell, the bottom (base) portion of the shell, and the entire shell once assembled. The design uses 16 mm M2.5 standoffs to separate the Raspberry Pi from the PoE hat, and M2.5 screws to secure the lid to the standoffs. The next set of images depict the exterior shell, which features a simple, functional design. It is another lidded box, but unlike the interior shell, it does not have ventilation slits. The only potential entry points for water or debris are the seam at the lid — which will be sealed with a waterproof sealant — and the cable eyelet, which will be protected with a weatherproof grommet. The interior shell shall be mounted inside the exterior shell using M2.5 x 16 mm screws through integrated mounting brackets. There are also mounting brackets on the outside of the chassis to allow it to be securely fastened to a lightpost using M2.5 x 16 mm screws. These brackets ensure stability and durability, even in high winds or stormy conditions. Although the exterior shell appears gray in the images for visibility, it shall be printed in white to minimize heat absorption. 

<img src="/Documents/Images/Top of Raspberry Pi Case.png" width="1800" height="800"> <br> <br>
<img src="/Documents/Images/Bottom of Raspberry Pi Case.png" width="1800" height="800"> <br> <br>
<img src="/Documents/Images/Raspberry Pi Case.png" width="2000" height="700"> <br> <br>
<img src="/Documents/Images/Exterior Shell Base.png" width="1800" height="800"> <br> <br>
<img src="/Documents/Images/Exterior Shell Lid.png" width="1800" height="800"> <br> <br>
<img src="/Documents/Images/Exterior Shell.png" width="1800" height="800"> <br> <br>

## Bill of Materials

| Component | Description | Manufacturer | Distributor | Qty | Unit Price | Total  |
|-----|-----|-----|-----|-----|-----|-----|
| PETG Filament | 1.75 mm White PETG Filament, 1 kg spool | 3DHoJor | Amazon | 1 | $13.99 | $13.99 |
| 16 mm M2.5 Standoffs | Brass or aluminum standoffs, male-female, M2.5, 16 mm, set of 10 | Unicorp | Amazon | 1 | $3.00 | $3.00 |
| M2.5 screws | 16 mm M2.5 screws, 50 piece pack | Generic | Amazon | 1 | $2.10 | $2.10 |
| Waterproof Sealant | Silicone or urethane sealant for plastic enclosure seams | GE | Amazon | 1 | $7.78 | $7.78 |
| Weatherproof Grommets | IP65 Cable Glands / Grommets (for Cat 6 cable), pack of 6 | Gunovy | Amazon | 1 | $6.99 | $6.99 |
| Total Before Tax |  |  |  |  |  | $33.86 |
| **Total After Tax** |  |  |  |  |  | **$36.91**|

## Analysis

### 3D Printing Material Selection
The type of 3D printing polymer that shall be used for the chassis is Polyethylene Terephthalate Glycol (PETG). When compared to other types of 3D printing plastics, PETG appears to be the best choice due to its combination of strength, UV resistance, low moisture absorption, and relatively high heat resistance [2]. It is a non-conductive plastic, so the a 0.5 cm thick shell shall not block or significantly attenuate incoming signals. Furthermore, PETG is compatible with the Tennessee Tech 3D printers and is a cost-effective option. To enhance thermal performance, white PETG filament was selected, as lighter colors absorb less radiant heat from the sun, which is an important factor for outdoor operation.

### Shell Design and Dimensions
The enclosure consists of two main 3D-printed parts: an interior shell tightly fitted around the Raspberry Pi 5 and its PoE HAT, and a larger exterior shell designed to shield the internal components from environmental exposure. The Raspberry Pi 5 itself measures approximately 85 mm × 56 mm × 18 mm [7]. To house this and allow some airflow around the PoE fan, the interior shell is sized accordingly. The exterior shell has been designed with dimensions of 13 cm × 10 cm × 6 cm and a wall thickness of 0.5 cm, offering enough space for air circulation and structural stability, while also maintaining a compact profile suitable for mounting on a light post. With these dimensions, the total surface area of the box is 536 square centimeters (0.0536 square meters), which will be used in the heat transfer calculation. 

### Heat Transfer Calculation
The primary challenge with sealed electronics enclosures is heat buildup, especially in outdoor environments [4]. Since the exterior shell is sealed for weather resistance, heat generated by the Raspberry Pi and PoE HAT must conduct through the PETG plastic walls and then dissipate into the ambient air. The heat transfer rate can be modeled using the equation: Q=hAΔT, where Q is the heat power dissipated (W), h is the heat transfer coefficient (W/m^2K), A is the surface area (m^2), and ΔT is the change of temperature (°C) [8]. For a 5 mm PETG wall, the heat transfer coefficient can be estimated to be 4.5 W/m^2K [9]. The heat generated by the Raspberry Pi 5 and PoE hat can be conservatively estimated to be 8 W, assuming 5–6 W generated by the Raspberry Pi 5 under moderate to high load and 1–2 W generated by the PoE circuitry and fan. Therefore, using Q=8, h=4.5, and A=0.0536, ΔT can be found to be 33.2°C. Even if this was added to 41° C (~105° F, the hottest temperature recorded in Cookeville to date[5]), the total interior heat would be still only reach 74.2°C. This is comfortably below the maximum operating temperature of 85°C, leaving about 10.5°C of thermal headroom.

### Summary of Thermal Considerations
Electronics can be extremely sensitive to heat, especially when operated in sealed containers. For the drone tracking system, thermal management is crucial to ensure long-term reliability and prevent thermal throttling or failure [6]. Here is a recap of the built in mechanisms and design decisions made to control the internal temperature of the system: 

- White PETG shall be used to reduce heat absorption
- An air gap shall be left between the shells to allow internal circulation
- An internal fan (via the PoE HAT) shall move the hot air
- Passive heat dissipation shall occur through the plastic walls, supported by conservative design margins

All these things taken together, the enclosure shall be more than capable of keeping internal temperatures well below the 85°C threshold, even during Tennessee’s hottest weather. 

### Weather Proofing Decisions
To ensure weather resistance, the chassis incorporates several protective design elements tailored for outdoor deployment. The sealed exterior shell has no ventilation holes and only two potential ingress points: the lid seam, which will be sealed with a waterproof sealant, and a cable eyelet, which will be reinforced with a weatherproof grommet. These measures support the goal of achieving an IP65 rating, making the enclosure dust-tight and capable of withstanding low-pressure water jets from any direction. The interior shell adds a secondary layer of protection, organizing and shielding the Raspberry Pi from mechanical shock while still allowing internal airflow. The decision to 3D print the shell in PETG — a polymer known for its water resistance and UV durability — further enhances its suitability for outdoor use. Together, these choices provide robust protection against rain, humidity, dirt, and environmental debris, ensuring safe and consistent operation of the drone tracking system in a wide range of weather conditions.

### Budget Analysis
Since the chassis is a custom made 3D print held together by screws, the expenses are minimal. Tennessee Tech already has 3D printers accessible to students, so the only outlays would be the PETG printing filament, sealant, and a few supplementary screws and grommets. In total, the cost comes out to less than $40, which is reasonable given its function. 

## References
[1] R. Bohn, “IP Ratings Explained - What Are IP Ratings? | NEMA Enclosures,” Stainless Steel Enclosures | NEMA Enclosures, Aug. 02, 2013. https://www.nemaenclosures.com/blog/ingress-protection-ratings/. 

[2] “Best 3D Printing Materials for Outdoor Use,” All3DP Pro, Apr. 18, 2024. https://all3dp.com/1/best-3d-printing-materials-for-outdoor-use/.  

[3] E. Ortiz, “What is a Chassis?,” Trentonsystems.com, Jun. 02, 2022. https://www.trentonsystems.com/en-us/resource-hub/blog/what-is-a-chassis. 

[4] ROHM, “Application Note Thermal Design (Basic) Basics of Thermal Resistance and Heat Dissipation,” Aug. 2021. https://fscdn.rohm.com/en/products/databook/applinote/common/basics_of_thermal_resistance_and_heat_dissipation_an-e.pdf. 

[5] US, “All-time Records for Various Middle Tennessee Locations,” Weather.gov, 2025. https://www.weather.gov/ohx/alltimerecords (accessed Apr. 19, 2025).

[6] A. Allan, “Heating and cooling Raspberry Pi 5,” Raspberry Pi, Oct. 04, 2023. https://www.raspberrypi.com/news/heating-and-cooling-raspberry-pi-5/

[7] “Raspberry Pi 5,” 2023. Available: https://datasheets.raspberrypi.com/rpi5/raspberry-pi-5-product-brief.pdf

[8] “Lumped System Analysis.” Available: https://www.sfu.ca/~mbahrami/ENSC%20388/Notes/Transient%20Heat%20Conduction.pdf

[9] “Material Properties of Thermoplastic PETG - Exceptionally Durable,” Dielectric Manufacturing. https://dielectricmfg.com/resources/knowledge-base/petg/
‌
‌
‌
‌
‌
‌
‌

