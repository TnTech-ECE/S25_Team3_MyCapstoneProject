# <div align="center"> Drone Tracker Detailed Design
### <div align="center"> Server and Database - UNFINISHED 
#### <div align="center"> Gabrielle Renfroe
<div align="center"> Department of Electrical and Computer Engineering <br>
Tennessee Technological University
<div align="left">

## Function of the Subsystem

The server and database subsystem is essential to the overall system architecture, managing, processing, and securely storing real-time telemetry data from both broadcast and network Remote ID sources. It ensures smooth data flow between the data collection layer and user-facing components like the website. This subsystem efficiently handles high-frequency telemetry, enforces data validation, maintains historical logs, and ensures consistency across sessions. By leveraging proper indexing, optimized queries, and security practices, it ensures high performance and data integrity. Additionally, the database is designed for scalability, capable of handling increasing drone data and supporting both real-time tracking and historical analysis as the application grows.

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

Using the following commands to install MySQL 

Creating a database

1. Table for *drones* - stores drone identity

    | Name         | Type          | Description                       |
    | ------------ | ------------- | --------------------------------- |
    | drone_id     | VARCHAR(100)  | Unique drone identifier (UAS ID)  |
    | operator_id  | VARCHAR(100)  | Opertaor ID                       |
    | manufacturer | VARCHAR(100)  | Drone brand                       |
    | model        | VARCHAR(100)  | Drone model                       | 
    | last_seen    | TIMESTAMP     | Last time information was sent    |

2. Table for *telemetry* - store real time flight data

    | Name      | Type          | Description               |
    | --------- | ------------- | ------------------------- |
    | numList   | VARCHAR(100)  | Auto-increment numList    |
    | drone_id  | VARCHAR(100)  | FK to *drones*            |
    | timestamp | DATETIME      | Time of the data point    |
    | latitude  | DOUBLE        | Drone latitude            |
    | longitude | DOUBLE        | Drone longitude           | 
    | altitude  | DOUBLE        | Altitude in meters        |
    | speed     | DOUBLE        | Horizontal speed          |
    | heading   | DOUBLE        | Direction of travel       |
    | source    | ENUM          | 'broaddcast' or 'network' |
    
    *FK - foreign key: points to a row in another table. For example, ensures telemetry.drone_id matches drones.drone_id*



## References

[1] W3Schools, “SQL Tutorial,” W3schools.com, 2019. https://www.w3schools.com/sql/default.asp (Accessed April 8, 2025).

[2] Emmet, “Setup a Raspberry Pi MYSQL Database,” Pi My Life Up, Jul. 04, 2019. https://pimylifeup.com/raspberry-pi-mysql/ (Accessed April 8, 2025).
