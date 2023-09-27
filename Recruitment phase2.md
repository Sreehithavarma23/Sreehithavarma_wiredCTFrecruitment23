# Recruitment phase2
------------------------------------------------------------------------------
# WEB
## PicoCTF challenges
```Power cookies```
- In the description it was given that can u get the flag! and a website was given .
- Inside hint box it was given that Do you know how to modify cookies? so I searched on how to modify cookies.
- From the website given in description inside inspect we have guest.js after that I found isadmin=0  and something like check.php
- As in the hint box it was given that modify cookie so I changed isadmin value from 0 to 1 as 1 is boolean always true.
- After refresing the page the got the flag.
## Flag - picoCTF{gr4d3_A_c00k13_5d2505be}
![img](https://github.com/Sreehithavarma23/Sreehithavarma_wiredCTFrecruitment23/blob/main/screenshots/powercookie.png)

```SQL Direct```
- In the description it was given that Connect to this PostgreSQL server and find the flag!
- So with the instance given I connected to postgreSQL server with password as postgres.
```psql -h saturn.picoctf.net -p 59914 -U postgres pico```
- In this command line psql allows you to interact with PostgreSQL databases, and performs various database related tasks
  and -h saturn.picoctf.net this part of command line is connecting to a server with the hostname "saturn.picoctf.net.
-p 59914 this specifies the port number on which the PostgreSQL server is listening for incoming connections.and -U postgres This option specifies the PostgreSQL username that you want to use when connecting to the database, and then pico is database name that you want to connect to.
- Now from help I used \? to get help about psql commands in that informations I found list of relation tables
- so I used \d  in that I got table in that we have flags so I used ```select * from flags;``` in that I got the flag.
## Flag - picoCTF{L3arN_S0m3_5qL_t0d4Y_73b0678f}
![img](https://github.com/Sreehithavarma23/Sreehithavarma_wiredCTFrecruitment23/blob/main/screenshots/sql%20direct.png)

```Irish Name Repo 1```
-In the description they gave a link which redirects to a page and they gave hint as 

    There doesn't seem to be many ways to interact with this, I wonder if the users are kept in a database? Try to think about how does the website verify your login?

- When we open this site and go to support page we see something like this Hi. I tried adding my favorite Irish person, Conan O'Brien. But I keep getting something called a SQL Error
-  This tells us that the site uses a SQL database.
- When we go to the Admin Login, we can try a basic SQL Injection to bypass the login portal.
- so I used username as ```admin' OR 1=1--``` and password can be anything so I used ```password``` in the place of password.
- Here this  query checks if the username is equal to nothing ,Then it checks OR 1=1 as 1 boolean value true .The -- at the end simply comments out the rest of the query.
- This fools the server into letting us through the portal.
## Flag -  picoCTF{s0m3_SQL_c218b685}
![img](https://github.com/Sreehithavarma23/Sreehithavarma_wiredCTFrecruitment23/blob/main/screenshots/irish%20name%20repo1.png)


```Irish Name Repo 2```
- In the description they gave link which redirects to page same like irish name repo 1.
- I tried this same SQL Injection of ' OR 1=1-- here, we get nothing but a page that says SQLi detected
- After some blind SQLi, we bypass it by setting the username to ```admin'--``` and password can be anything so same ```password```
  - from this I found the flag.
## Flag - picoCTF{m0R3_SQL_plz_fa983901}
![img](https://github.com/Sreehithavarma23/Sreehithavarma_wiredCTFrecruitment23/blob/main/screenshots/irish%20name%20repo2.png)


```Irish Name Repo 3```
- Once again we are brought back to what seems like the same page as in Irish-Name-Repo 1 and 2.
-  This time when we enter a SQL Injection such as ' or 1=1--, we get a server side we get something like this
``` password: ' or 1=1-- SQL query: SELECT * FROM admin where password = '' be 1=1--'```
-We see that the alphabetical characters 'o' and 'r' have been swapped to a 'b' and 'e'. Let's try putting every letter in the alphabet after the comment to see exactly what happens.
- ``` ' or 1=1--abcdefghijklmnopqrstuvwxyz``` both worked and I got the flag.
## Flag - picoCTF{3v3n_m0r3_SQL_06a9db19}
![img](https://github.com/Sreehithavarma23/Sreehithavarma_wiredCTFrecruitment23/blob/main/screenshots/irish%20name%20repo%203.png)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# EMBEDDED
## Tinker Cad Challenges
1 - ``` Make a simple Traffic light controlled using a push button(Pullup or pulldown). Each time we press the button the LEDs should change.```

- Firstly open tinker cad and login then Create a new circuit by clicking on "Create New Circuit."
- In the Components panel, search for the following components and add them to your workspace.
-  Arduino UNO
    Breadboard
    3 LEDs (Red, Yellow, and Green)
    3 current-limiting resistors (220-330 ohms)
    Push button
    10k-ohm resistor (for the pull-up)
    Jumper wires
##  Assembly the circuits as following:
- Connect the long leg (anode) of the red LED to digital pin 2 of the Arduino .    
- Connect the long leg of the yellow LED to digital pin 3 .
- Connect the long leg of the green LED to digital pin 4 .
- Connect one terminal of the push button to digital pin 5.
- Connect the other terminal of the push button to the ground (GND) rail on the breadboard.
- Connect a 10k ohm resistor between the same terminal of the push button and the 5V rail on the breadboard.
- And then now in code panel and searched in google how stimulate that from that I built the code and then start stimulation button.
--------------------------------------------------------------------------------------------------------------------------------  
2 -``` Make a circuit involving Potentiometer so that a servo motor will rotate according to the potentiometer value.```
- open tinker cad ,Click on "Create New Circuit" to start a new project.
- Search and add the following components to your virtual circuit.
-  Arduino UNO
    Servo Motor
    Potentiometer
    Breadboard
  - Connect one end of the potentiometer to the 5V rail on the breadboard.
  - Connect the other end of the potentiometer to the GND on the breadboard.
  - Connect the middle pin of the potentiometer to analog pin A0 on the Arduino.
  - Connect the servo motor's signal  to digital pin 9 on the Arduino.
  -  Connect the servo motor's power to the 5V rail on the breadboard.
  -  Connect the servo motor's ground to the GND (ground) rail on the breadboard to anode so that whole is considered as ground
  - Then I gave the code to rotate that servo meter.
![img](https://github.com/Sreehithavarma23/Sreehithavarma_wiredCTFrecruitment23/blob/main/screenshots/Screenshot%20from%202023-09-09%2017-47-02.png)
