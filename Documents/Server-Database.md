# <div align="center"> Drone Tracker Detailed Design
### <div align="center"> Server and Database
#### <div align="center"> Gabrielle Renfroe
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">
  
## Function of the Subsystem

The server and database...

## Specifications and Constraints

The server shall receive the packaged information obtained from the RID signal via a Transmission Control Protocol (TCP) from the central computer.
- To ensure the packaged information is sent to the correct place, the TCP method 

After unpacking and processing the data, the RID shall be permanently stored in the database, while other information, such as the last known drone location and takeoff location, shall be retained for 30 days before being deleted.
- breh

Should the network go down, the server shall buffer the received packets for 10 minutes.
- no 

## Overview of Proposed Solution

Describe the solution and how it will fulfill the specifications and constraints of this subsystem.

## Interface with Other Subsystems

Provide detailed information about the inputs, outputs, and data transferred to other subsystems. Ensure specificity and thoroughness, clarifying the method of communication and the nature of the data transmitted.

## Flowchart

For sections including a software component, produce a chart that demonstrates the decision-making process of the microcontroller. It should provide an overview of the device's function without exhaustive detail.

## BOM

Provide a comprehensive list of all necessary components along with their prices and the total cost of the subsystem. This information should be presented in a tabular format, complete with the manufacturer, part number, distributor, distributor part number, quantity, price, and purchasing website URL. If the component is included in your schematic diagram, ensure inclusion of the component name on the BOM (i.e R1, C45, U4).

## Analysis

Deliver a full and relevant analysis of the design demonstrating that it should meet the constraints and accomplish the intended function. This analysis should be comprehensive and well articulated for persuasiveness.

## References

All sources that have contributed to the detailed design and are not considered common knowledge should be duly cited, incorporating multiple references.
