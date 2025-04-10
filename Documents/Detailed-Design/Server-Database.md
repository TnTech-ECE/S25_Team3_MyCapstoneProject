# <div align="center"> Drone Tracker Detailed Design
### <div align="center"> Server and Database
#### <div align="center"> Gabrielle Renfroe
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">

## Function of the Subsystem

The server and database subsystem plays a critical role within the overall system architecture by managing, processing, and securely storing data, ensuring efficient data flow and integrity between the central computer and website. 

## Specifications and Constraints

- The server shall receive the packaged information obtained from the RID signal via a Transmission Control Protocol (TCP) from the central computer.

- After unpacking and processing the data, the RID shall be permanently stored in the database, while other information, such as the last known drone location and takeoff location, shall be retained for 30 days before being deleted.

- Should the network go down, the server shall buffer the received packets for 10 minutes.

## Overview of Proposed Solution

Describe the solution and how it will fulfill the specifications and constraints of this subsystem.

The server...

The database is written using a Structured Query Language (SQL). It is the standard language used to store, manipulate, and retrieve data in databases. MySQL server is installed onto the Raspberry Pi. Using SQL commands, the database is organzied into multiple tables.

## Interface with Other Subsystems

The server receives the packaged information from the central computer. Once received, the server processes the data and sends it to the database for storage and organization. The database structures and stores the information, making it easily accessible. The website, through the server, queries the database to retrieve the necessary data and then displays it to the user. 

## Flowchart

For sections including a software component, produce a chart that demonstrates the decision-making process of the microcontroller. It should provide an overview of the device's function without exhaustive detail.

## Analysis

Installing the MySQL server

Creating a database

Organizing stacks for different 

## References

[1] W3Schools, “SQL Tutorial,” W3schools.com, 2019. https://www.w3schools.com/sql/default.asp (Accessed April 8, 2025).

