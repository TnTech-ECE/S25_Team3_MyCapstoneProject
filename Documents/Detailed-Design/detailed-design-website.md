# Website_System
## Functionality
The website subsystem is designed to provide a designated user with access to drone data stored in the database subsystem. It will regularly check for updates in the database, ensuring that newly logged drones are identified by the campus police as quickly as possible, aiming for near real-time detection. The displayed data will be organized clearly and efficiently, facilitating the effective management of dispatcher resources. The website will also allow the user to approve drones for flight, enabling the necessary authorization for flights. If a system malfunction occurs, the user can also assess the system's status through the website to identify the source of the issue.   

## Constraints
| No.| Constraint | Origin |
| -- | --------- |--------|
|  1 | The database must be accessed through a website instead of a mobile phone application. | Campus Police |
|  2 | Real-time is defined as less than or equal to ten seconds. The system shall notify campus police and display data in 'real-time' on the website. | Project Team / Campus Police |
|  3 | The drone information will be displayed on the website concisely, allowing for utilization with minimized training. | Project Team |
|  4 | The website will be constructed securely, within reason. | Project Team |
|  5 | The website will be constructed to comply with standards put into place by the W3C (World Wide Web Consortium). | Project Team / Supervisor |
|  6 | The system shall allow campus police to authorize specific drones for permitted flights in a specified time frame. | Project Team |  
|  7 | The system shall increase the alert's urgency if a drone is detected in any designated geographical region. | Project Team |  

<sup>1</sup> For the safety of officers in the field, the campus police department has requested that the obtained Remote ID (RID) data be displayed on a website instead of a mobile application. Concerns were raised about officers using personal mobile devices in the field. The police captain and dispatcher have explicitly stated a preference for a website-based information display. To relay data to officers, a dispatcher will communicate drone information directly to the officer.

<sup>2</sup> To ensure timely dispatch of officers to the detected drone location, the campus police department has requested that the system operate as close to real-time as possible. Upon initial detection of a Remote ID signal, a notification will be sent to the TTU police department. While this time frame is longer than the typical definition of real-time, it is considered reasonable for this project.

<sup>3</sup> To integrate easily into the campus police department's workflow, the system will be designed so that minimal training is required for operation. Users should be able to view the website and quickly understand its layout and functionality. 

<sup>4</sup> To protect against unauthorized access to the database, the website must be securely constructed to a reasonable standard. While perfect security is impossible, the website will be built to be resistant to malicious access. Security measures will include password protection for authorized users and the use of Google's Safe Browsing website checker.

<sup>5</sup> The W3C, a non-profit organization that develops web standards, requires that the website meet accessibility, privacy, and security standards. The project team will use W3C validators, including the Nu HTML checker, Link checker, and CSS validator, to ensure the website works across all devices.

<sup>6</sup> To prevent unnecessary alerts, campus police will have the ability to whitelist specific drone serial numbers. This will ensure that alerts are not triggered when authorized drones are detected. Although adding this check may slightly increase the program's execution time, it will still remain within the allocated time frame. This authorization will be stored in the database, allowing the website to quickly determine whether a detected drone is authorized for flight.

<sup>7</sup> Privacy concerns on campus are significant for this project. Malicious drone use may pose a threat to private areas on campus. To mitigate this risk, certain areas will be designated as high-priority zones. Any drone entering these areas will trigger an increased alert level. This prioritization allows the police to make informed decisions about which incidents to address first. The project team believes that the most malicious drones will likely be flown in these high-risk areas, and the safety of students in these zones is considered a top priority.

## Schematic
<img src="/Documents/Images/Website Schematic.png" >

### Rough Website Design
<img src="/Documents/Images/website_beta.png" >

In the image above, a rough depiction of what the final website will look like is shown. Once a user has been authorized and logged in, this layout will be displayed. The banner at the top simply displays the title of the webpage. Below the banner, there is an image showing a marker placed on a Google Maps instance. This marker represents a detected drone, and since only one drone was "detected" at the time the picture was taken, only the information for that single drone is displayed on the right side of the image. If additional drones had been detected, their serial numbers would appear under the "selected drone" section on the right side, with all other information collapsed until the user clicks on the drone marker or the serial number on the side of the screen.

### HTML/CSS and JavaScript

The languages chosen to implement this program will be HTML, CSS, and JavaScript. HTML will be used initially to create the framework of the webpage, where CSS will then be utilized to make the page look more presentable and coherent with Tech's current website theme. JavaScript will be implemented where necessary to make the webpage responsive to user inputs.

### Google Maps API
The team has decided to use Google's Maps JavaScript API to handle the placement of drones in the correct places on the map. Google allows users to utilize up to $200 monthly worth of Maps API resources for free, with the credit resetting on the first of each month. This amount of money covers nearly 30,000 map loads per month.[^1] With this API, a map can be centered on the campus of TTU, and, using the coordinates retrieved from the Remote ID signal, markers can be placed on the map in the exact location where the drone is detected. 

After obtaining an API key, the API call can implemented using the key in the HTML5 webpage, where the map will then become usable in the browser. The Maps JavaScript API allows up to 300 calls per minute per IP address.[^2] This means that the absolute maximum number of times the website can call the API is 5 times per second. Assuming that the API is called a generous 500 times per day, then in even the longest months, the most API calls the program will make will be 15,500. For the first 100,000 API calls each month, the cost per call is 0.007 USD. This means that even with a high volume of API calls, such as 500, only slightly more than half of the built-in API budget is consumed.

The program will then prompt the database for all data sets that match the search characteristic (default value is set to the current date.) These data points will then have a Google Maps marker placed on their respective locations. The dispatcher can then select a certain drone and view the related data received from the Remote ID. Drones will populate the list in the reverse order they were detected, with the most recent drones appearing first.

For the website to be accessible at all times, it will need to be hosted on a machine that doesn't turn off. The team has asked the campus police to use a server on their server rack, but due to policies put into place by the FBI and TBI only specific personnel are allowed to access those servers. The team made the decision to host both the website and database off of the raspberry pi 5.

## Analysis

### Interactions With Other Subsystems

The website subsystem will only directly interact with the database. The website will take the processed data from the database and will update the on screen information as needed. The website will also have to ablity to send info to the database, updating the autheraztion status of a selected drone.

## BOM
| Item     | Part Number | Quantity | Price/Unit     | Total Cost |
| -------- | ------------| -------- |----------------|------------|
|Domain    |            -|         1|        $30/year|         $30|
|Google Maps API Access|-|         1|     $0.007/call|          $0|
|Total     |             |          |                |         $30|

## References
<!-- This is how to do footnotes for the references: --> 
[^1]: (https://mapsplatform.google.com/pricing/)
[^2]: (https://developers.google.com/maps/documentation/javascript/usage-and-billing)
[^3]: (https://validator.w3.org/#validate_by_uri)
<!--etc.-->
