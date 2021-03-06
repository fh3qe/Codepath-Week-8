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
  		 <img src="Blue - SQLI.gif" width="800">
  - [x] Steps to recreate: 
  	- I checked every website for a vulnerability by messing with the id field of the "Find a Salesperson" functionality and found a SQLI vulnerability in the Blue website. Then I formatted my id field to call a SLEEP(5) command (id='OR SLEEP(5)=0--') which was then executed. 

Vulnerability #2: Session Hijacking/Fixation
  - [x] GIF Walkthrough: 
  		 <img src="Blue - Session Hijacking.gif" width="800">
  - [x] Steps to recreate: 
  	- Using the change_session_id.php script provided, I saw that the BLue website allowed you to successfully perform session hijacking/fixation when you set the attacker's session ID to the target's session ID.


## Green

Vulnerability #1: Username Enumeration
  - [x] GIF Walkthrough: 
  		 <img src="Green - Username Enumeration.gif" width="800">
  - [x] Steps to recreate: 
  	- Upon testing the Login functionality of all the websites, I saw that there was a difference in styling for the unsuccessful login message on the Green website. When you fed a dummy username, the resulting message would be unbolded. However when you used a legitimate username (jmonroe99), the message would be bolded. Thus an attacker could enumerate through the website and find legitimate usernames to attack for passwords. 

Vulnerability #2: Cross-Site Scripting
  - [x] GIF Walkthrough: 
  		 <img src="Green - XSS.gif" width="800">
  - [x] Steps to recreate: 
  	- When submitting a javascript snippet into the comment portion of the contact form ("<script>alert("Frank found the XSS!");</script>"), the snippet will be run when you login and click the Feedback tab.


## Red

Vulnerability #1: Insecure Direct Object Reference
  - [x] GIF Walkthrough: 
  		 <img src="Red - Insecure Direct Object Reference.gif" width="800">
  - [x] Steps to recreate: 
  	- When inspecting the Salesperson listing, I noticed that the IDs listed only go up to 9. So I tested for "id=10" and was able to access the corresponding salesperson on the Red website.

Vulnerability #2: Cross-Site Request Forgery
  - [x] GIF Walkthrough: 
  		 <img src="Red - CSRF.gif" width="800">
  - [x] Steps to recreate: 
  	- I wrote a HTML file with the following sourcecode (also in the repository):
  	```html
  			<html>
				<head>
					<title> Hello World! </title>
				</head>
				<body onload="document.forms[0].submit()">
					<form id="form" target="res" action="https://35.225.125.173/red/public/staff/users/edit.php?id=1" method="post">
						<input type="hidden" name="first_name" value="CSRF">
						<input type="hidden" name="last_name" value="Attack">
					</form>
					<iframe name="res" style="display: none;"></iframe>
				</body>
			</html>
	```
	- The HTML file (which I hosted on WPDistillery as an easy access point) executes when loaded, which will edit the first and last name of the Users on the page. In this instance, I targeted Jon Monroe. However, the admin can't tell that anything was submitted or that any information was changed until they look at the User's page. 


## Notes

Describe any challenges encountered while doing the work



