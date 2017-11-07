# Project 8 - Pentesting Live Targets

Time spent: 4 hours spent in total

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

Vulnerability #1: Session Hijacking
  - GIF Walkthrough:
    ![Dunno why this didn't load](/images/blue-vuln-session-hijacking 'instructions')
  - Explanation: Using the included tool to change the session ID, the blue site does not check if the session belongs to the browser used. Therefore, replacing the session ID for the blue site with a logged in green site resulted in access to the admin controls without logging in.

Vulnerability #2: SQL Injection (SQLi)
  - GIF Walkthrough:
    ![Dunno why this didn't load](/images/blue-vuln-sqli.gif 'instructions')
  - Explanation: The salesperson pages on the blue site have a SQL injection vulnerability in the id parameter. This is shown most easily through using the sleep injection, which cause the page to load for an extra 5 seconds as used.


## Green

Vulnerability #1: Username Enumeration
  - GIF Walkthrough:
    ![Dunno why this didn't load](/images/green-vuln-userEnumeration].gif 'instructions')
  - Trying to log in with a non existent account/username results in the output of: "Log in was unsuccessful". Trying to log in with an existing account, but incorrect password shows the same output in bold.

Vulnerability #2: Cross-Site Scripting (XSS)
  - GIF Walkthrough:
    ![Dunno why this didn't load](/images/green-vuln-XSS.gif 'instructions')
  - Explanation: The Contact page's feedback box is rendered as entered on the Feedback page in the admin section. Therefore, it is trivial to enter any XSS payload into the Feedback box for the admin to eventually load.


## Red

Vulnerability #1: Cross-Site Request Forgery (CSRF)
  - GIF Walkthrough:
    ![Dunno why this didn't load](/images/red-vuln-csrf.gif 'instructions')
  - Explanation: It is simple to replay the POST request through the Burp suite, where parameters can be altered.

Vulnerability #2: Insecure Direct Object Reference (IDOR)
  - GIF Walkthrough:
    ![Dunno why this didn't load](/images/red-vuln-IDOR.gif 'instructions')
  - Explanation: Through the admin panel, it can be seen that Testy McTesterson should be hidden. However, his id is 10. By selecting any of the other salesperson in the public site and changing the id to 10 in the address bar, Testy's page can be accessed.

## Notes

Finding the SQLi was the trickiest part.
Close second was the XSS, mostly since my original test code never displayed and made it seem that the vulnerability wasn't on that site.
