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
The chassis shall integrate with the other physical atomic subsystems by securing and protecting their hardware components. It shall provide mounting points for the Raspberry Pi, keeping it securely in place with screws and shock absorbing rubber bumpers to guard it against damage from drops, knocks, and vibrations. Power will be supplied to the Raspberry Pi via a PoE hat, which requires a Cat 6 Ethernet cable connection. To accommodate this, the chassis will feature an eyelet for the cable. Additionally, the design will allow sufficient space for the PoE hat’s fan to circulate air effectively.

## 3D Model of Custom Mechanical Components
Below are several images of the 3D models for both the interior and exterior shells of the chassis. The first three images model the interior shell. They show the top (lid) portion of the shell, the bottom (base) portion of the shell, and the entire shell once assembled. The design uses 16 mm M2.5 standoffs to separate the Raspberry Pi from the PoE hat, and M2.5 screws to secure the lid to the standoffs. The next set of images depict the exterior shell, which features a simple, functional design. It is another lidded box, but unlike the interior shell, it does not have ventilation slits. The only potential entry points for water or debris are the seam at the lid — which will be sealed with a waterproof sealant — and the cable eyelet, which will be protected with a weatherproof grommet. The interior shell shall be mounted inside the exterior shell using M2.5 x 16 mm screws through integrated mounting brackets. There are also mounting brackets on the outside of the chassis to allow it to be securely fastened to a lightpost using M2.5 x 16 mm screws. These brackets ensure stability and durability, even in high winds or stormy conditions. Although the exterior shell appears black in the images for visibility, it shall be printed in white to minimize heat absorption. 

<img src="/Documents/Images/Top of Raspberry Pi Case.png" width="1800" height="800"> <br> <br>
<img src="/Documents/Images/Bottom of Raspberry Pi Case.png" width="1800" height="800"> <br> <br>
<img src="/Documents/Images/Raspberry Pi Case.png" width="2000" height="700">

## BOM

| Component               | Manufacturer | Part No.    | Distributor | Qty | Unit Price | Total  |
|-------------------------|--------------|-------------|-------------|-----|------------|--------|
| 16 mm M2.5 standoffs    |              |             |             |     |            |        |
| M2.5 screws
| PLA printing material
| weather proof grommets
| sealant for around the lid
| rubber bumpers
| **Total**               |              |             |             |     |            | **$$$**|

## Analysis

### Choice of 3D Printing Material

### Interior and Exterior Shell Dimensions
A Raspberry Pi 5 is about 85 mm long, 56 mm wide, and 18 mm tall [7]. The interior shell has been designed to encase the Raspberry Pi with the PoE hat tightly, but the exterior shell has more flexibility in its dimensions. The chosen dimensions are 14 cm by 11 cm by 11 cm. These dimensions were chosen because they allow it to be compact and mountable to a light post but still have enough surface area to give a large enough heat dissipation through passive heat dissipation through the plastic, as will be explained below. 

### Heat Transfer Calculation

### Summary of Thermal Considerations
A big challenge in designing electronic equipment is countering the heat that is produced, especially when the device is operating in a warm environment, such as the great Tennessee outdoors during the summer months. Heat production and dissipation is an important thing to consider because it affects the performance and reliability of the parts and equipment [4]. For the drone tracking device to operate correctly, it needs to remain in the operating temperature range of -40° to 85° C. Given that the lowest recorded temperature of all time in Cookeville was -30° C [5], this lower bound isn't much of a concern. However, between the hot tennessee sun and the heat produced by the device itself, we need to make sure it never exceeds 85° C to avoid thermal throttling [6]. For the most part, the Raspberry Pi and PoE hat combination take care of themselves using a passive heat sink, active cooler, and fan. However, a couple additional measures have been taken for greater heat dissipation. First, the color of choice for the 3D printing material is white, because it absorbs the least amount of heat. Also, the exterior shell has larger dimensions than the interior shell, allowing room for more air to circulate and more power to be dissipated. As explained above, about ___ W of power are dissipated, which will assist in keeping the temperature down. Between all these things, the device shall be able to operate even in high temperatures. 

### Weather Proofing Decisions

### Budget Analysis
Since the chassis is a custom made 3D print held together by screws, the expenses are minimal. Tennessee Tech already has 3D printers accessible to students, so we would just have to buy the PLA printing material and a few miscellaneous pieces. In total, the cost comes out to less than ______ which is reasonable given its function. 

## References
[1] R. Bohn, “IP Ratings Explained - What Are IP Ratings? | NEMA Enclosures,” Stainless Steel Enclosures | NEMA Enclosures, Aug. 02, 2013. https://www.nemaenclosures.com/blog/ingress-protection-ratings/. 

[2] “Best 3D Printing Materials for Outdoor Use,” All3DP Pro, Apr. 18, 2024. https://all3dp.com/1/best-3d-printing-materials-for-outdoor-use/.  

[3] E. Ortiz, “What is a Chassis?,” Trentonsystems.com, Jun. 02, 2022. https://www.trentonsystems.com/en-us/resource-hub/blog/what-is-a-chassis. 

[4] ROHM, “Application Note Thermal Design (Basic) Basics of Thermal Resistance and Heat Dissipation,” Aug. 2021. https://fscdn.rohm.com/en/products/databook/applinote/common/basics_of_thermal_resistance_and_heat_dissipation_an-e.pdf. 

[5] US, “All-time Records for Various Middle Tennessee Locations,” Weather.gov, 2025. https://www.weather.gov/ohx/alltimerecords (accessed Apr. 19, 2025).

[6] A. Allan, “Heating and cooling Raspberry Pi 5,” Raspberry Pi, Oct. 04, 2023. https://www.raspberrypi.com/news/heating-and-cooling-raspberry-pi-5/

[7] “Raspberry Pi 5,” 2023. Available: https://datasheets.raspberrypi.com/rpi5/raspberry-pi-5-product-brief.pdf
‌
‌
‌
‌

