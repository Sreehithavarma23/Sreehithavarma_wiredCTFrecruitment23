# Recruitment phase2
------------------------------------------------------------------------------
# WEB
## PicoCTF challenges
```Power cookies```
- In the description it was given that can u get the flag! and a website was given .
- Inside hint box it was given that Do you know how to modify cookies? so I searched on how modify cookies.
- From the website given in description inside inspect we have guest.js after that I found isadmin=0  and something like check.php
- As in the hint box it was given that modify cookie so I changes isadmin value from 0 to 1 as 1 is boolean always true.
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


```Irish Name Repo```
- In the description they gave link which directs to page same like irish name repo 1.
- 
