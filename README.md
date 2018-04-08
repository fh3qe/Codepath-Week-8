# Project 8 - Pentesting Live Targets

Time spent: **3** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL Injection (SQLI)
  - [x] GIF Walkthrough: 
  	- <img src="Blue - SQLI.gif" width="800">
  - [x] Steps to recreate: 
  	- I checked every website for a vulnerability by messing with the id field of the "Find a Salesperson" functionality and found a SQLI vulnerability in the Blue website. Then I formatted my id field to call a SLEEP(5) command (id='OR SLEEP(5)=0--') which was then executed. 

Vulnerability #2: Session Hijacking/Fixation
  - [x] GIF Walkthrough: 
  	- <img src="Blue - Session Hijacking.gif" width="800">
  - [x] Steps to recreate: 
  	- Using the change_session_id.php script provided, I saw that the BLue website allowed you to successfully perform session hijacking/fixation when you set the attacker's session ID to the target's session ID.


## Green

Vulnerability #1: __________________

Vulnerability #2: __________________


## Red

Vulnerability #1: __________________

Vulnerability #2: __________________


## Notes

Describe any challenges encountered while doing the work



