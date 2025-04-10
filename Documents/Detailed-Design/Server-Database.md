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

The database is implemented using Structured Query Language (SQL), the standard language for managing and manipulating data in relational databases. MySQL is installed on the Raspberry Pi as the database server, and SQL commands are used to define the schema and organize data across multiple tables. This structure ensures efficient storage, retrieval, and management of the data while preserving the relationships between various data points, enabling smooth interactions between the system components.

Python is used to implement a 10-minute buffering mechanism that temporarily stores telemetry data if the network connection is lost. In the event of a network failure, the server will buffer incoming packets for up to 10 minutes. Once the connection is restored, the buffered data is flushed to the database. This ensures that no data is lost during network interruptions and that the system continues operating smoothly without impacting real-time data tracking.

## Interface with Other Subsystems

The server receives packaged data from the central computer and processes it according to the defined protocols. After processing, the server forwards the information to the database for structured storage, ensuring that the data is categorized and indexed appropriately. The database is optimized for fast access and retrieval, making it easy to query for the required data.

When the website requests data, it interacts with the server, which then queries the database to retrieve the relevant information. This information is presented to the user in a user-friendly format. The system is designed to handle multiple concurrent requests efficiently, ensuring that data retrieval remains fast even during periods of high demand. The interactions between the server, database, and website are streamlined to provide seamless user experiences and maintain system performance, scalability, and data integrity.

## Flowchart

<img src="/Documents/Images/Server-Database Flowchart.png" width="600" height="900">

## Analysis

The following command installs MySQL to the Raspberry Pi:

    sudo apt install mariadb-server

To secure the software and set a password:

    sudo mysql_secure_installation

To access the Raspberry Pi's MySQL server and make changes:

    sudo mysql -u root -p

1. Table for *drones* - stores drone identity

    | Name         | Type          | Description                       |
    | ------------ | ------------- | --------------------------------- |
    | drone_id     | VARCHAR(100)  | Unique drone identifier (UAS ID)  |
    | operator_id  | VARCHAR(100)  | Opertaor ID                       |
    | manufacturer | VARCHAR(100)  | Drone brand                       |
    | model        | VARCHAR(100)  | Drone model                       | 
    | last_seen    | TIMESTAMP     | Last time information was sent    |

2. Table for *telemetry* - store real time flight data

    | Name      | Type          | Description                    |
    | --------- | ------------- | ------------------------------ |
    | numList   | VARCHAR(100)  | Auto-increment numList         |
    | drone_id  | VARCHAR(100)  | FK to *drones*                 |
    | timestamp | DATETIME      | Current time of the data point |
    | latitude  | DOUBLE        | Drone latitude                 |
    | longitude | DOUBLE        | Drone longitude                | 
    | altitude  | DOUBLE        | Altitude in meters             |
    | speed     | DOUBLE        | Horizontal speed               |
    | heading   | DOUBLE        | Direction of travel            |
    | source    | ENUM          | 'broadcast' or 'network'       |
    
    *FK - foreign key: points to a row in another table. For example, ensures telemetry.drone_id matches drones.drone_id*

## References

[1] W3Schools, “SQL Tutorial,” W3schools.com, 2019. https://www.w3schools.com/sql/default.asp (Accessed April 8, 2025).

[2] Emmet, “Setup a Raspberry Pi MYSQL Database,” Pi My Life Up, Jul. 04, 2019. https://pimylifeup.com/raspberry-pi-mysql/ (Accessed April 8, 2025).
