# Vehicle Accident Detection And Rescue Information system 
## ABSTRACT
This system is developed in order to detect vehicle accident and send the location information of the accident place to vehicle owner, nearest hospital and police station via a web service. The communication between the web server and hardware device is established via GSM/GPRS shield, and the location is traced by using the GPS shield. The accident is detected through accelerometer, keypad and buzzer. The project is developed for real time data fetching form the hardware device using sensors and store in the web server, and send notification to different users either through web application, SMS. This project approximately provides the accurate detection of the location of accident occurred, and send notification to the nearest police station and hospital.
## DESIGN
The project is accident detection mechanism. Hardware used in this project are listed below: 
1. Arduino UNO REV3 
2. GSM, GPS, GSRM Shied (SIM808) 
3. Accelerometer (MPU6050)
4. LCD Display

![image](https://user-images.githubusercontent.com/32418411/133652108-a0d9a1f9-a57b-48df-bdb6-d7f893ccc753.png)

Block Diagram of the project
## HARDWARE CONNECTION
 ![image](https://user-images.githubusercontent.com/32418411/133652260-c13772db-96de-44b1-a407-1816dceeff7c.png)
 
Fig 1 : Block Diagram of the Hardware
## Algorithm for Accident Detection :
Step 1: Start the program.
Step 2: Read accelerometer data. 
Step 3: If sensor value is more than limit go to step 4, otherwise go to step 2. 
Step 4: Ask Driver for confirm accident. Set wait time 60 second. 
Step 5: If Driver confirm accident go to step 6, otherwise go to step 7. 
Step 6: Send notif. to web server owner account, nearest police station, hospital also send SMS. Go to step2. 
Step 7: Decrement wait time each second. 
Step 8: if wait time = 0 second go to step 9, otherwise go to step 5. 
Step 9: go to step 6. 
Step 10: Stop. 
### Communication with web server and sending notification 
The system communicates with the web server through GPRS communication via a GSM, GPRS Shield. It will send the vehicle location’s latitude and longitude data to web server upon user request or after detection of accident. The web application will forward necessary notification to the nearest police station and hospital with the website, mobile application and mobile SMS.
### Calculation of shortest distance: 
To find out the nearest police station and hospital ‘haversine’ approximation method is used. Haversine formula: 
𝑎 = 𝑠𝑖𝑛² (𝛥𝜑 /2) + 𝑐𝑜𝑠 𝜑1 × 𝑐𝑜𝑠 𝜑2 × 𝑠𝑖𝑛²( 𝛥𝜆 /2) 
𝑐 = 2 × 𝑎𝑡𝑎𝑛2 ( √𝑎,√(1−𝑎) ) 
𝑑 = 𝑅 × 𝑐 
Where 𝜑 is latitude, 𝜆 is longitude, 𝑅 is earth’s radius (mean radius = 6,371km); 
note that angles need to be in radians to pass to trig functions. 
## Project flow chart:  The complete design flow of the project can be depicted here: 
![image](https://user-images.githubusercontent.com/32418411/133652433-18aa3213-658c-4848-8355-eaac4670f34c.png)

## Embedded device 
### Circuit connection: 
The project is developed by using GSM/GPRS/GPS/Bluetooth Shield SIM808 directly connected to all the pins of Arduino. Pin 2 of Arduino is used for RX and pin 3 for TX. Accelerometer is connected with Arduino in pin number A0,A1,A2 and A LCD display is connected at pin number A5, A4. A confirmation switch is connected in pin 6, and a warning buzzer is added in pin 7. 
![image](https://user-images.githubusercontent.com/32418411/133652695-9002a0fd-d862-4608-a86d-72376f0feff5.png)

Actual Picture of the Embedded Device 
## Arduino Programming: 
![image](https://user-images.githubusercontent.com/32418411/133652789-fea44b44-020b-475d-bfd0-01f78d5ec90a.png)

## Configuration of Database: 
A web database is configured to store the data that are being sent from the embedded devices. DB2 application on ibm is used to configure the SQL database. There are 7 tables: 
1. user: Store user information. 2. policestation: Store Police Station information, location. 3. hospital: Store Hospital information, location. 4. vehicle: Store each device installed in different vehicle. 5. location: Store vehicle location on demand of user. 6. accident: Store location information after accident detection. 7. rescue: Store which police station and hospital is involving in rescue. 
![image](https://user-images.githubusercontent.com/32418411/133652886-fcd797c5-df97-4448-8731-78c27310a432.png)

![image](https://user-images.githubusercontent.com/32418411/133652907-255a8b50-8fa9-4ce5-82a8-e485be62bbfb.png)

SQL Database in webserver
## Web Application 
A web application has been developed to receive data from embedded device through GSM shield using GPRS connection.  URL https://technoutsav2.mybluemix.net/
![image](https://user-images.githubusercontent.com/32418411/133653068-d9236797-36ea-450d-a7ea-bd8bf72bc61c.png)

Website https://technoutsav2.mybluemix.net/
![image](https://user-images.githubusercontent.com/32418411/133653137-f49ac9e5-42a4-45e7-805d-cd8d793a97b3.png)

Website Screenshot 
![image](https://user-images.githubusercontent.com/32418411/133653179-4eb22765-53be-4dc2-b388-bb8bb2be5eb5.png)

Figure 4.7: User panel for multiple car installed the device. (website screenshot) 
![image](https://user-images.githubusercontent.com/32418411/133653241-ad91145c-cb21-49fa-b6fa-e6a47e869eb2.png)

Hospital get notification about accident and direction towards the spot.
![image](https://user-images.githubusercontent.com/32418411/133653307-1574ea7b-af25-45b3-bfb4-e1d1f2bb6ed8.png)

Police station get notification about accident and direction towards the spot.
## Security 
### User Authentication for Login 
To access the website, the user has to go through a login page. There is a table “user” stored in the database with username and password. This username also enables the data to load on the site. So, even if someone got access to the main webpage no data will be loaded until the correct username and password is given.
## Constraints
•	Hardware or software environment : Need Arduino Ide to upload code on arduino. Libraries are attached with code.
•	Availability of resources : IBM Cloud




