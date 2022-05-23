## Unit 19 Homework: Protecting VSI from Future Attacks

### Scenario

In the previous class,  you set up your SOC and monitored attacks from JobeCorp. Now, you will need to design mitigation strategies to protect VSI from future attacks. 

You are tasked with using your findings from the Master of SOC activity to answer questions about mitigation strategies.

### System Requirements 

You will be using the Splunk app located in the Ubuntu VM.

### Logs

Use the same log files you used during the Master of SOC activity:

- Windows Logs
- Windows Attack Logs
- Apache Webserver Logs
- Apache Webserver Attack Logs

---

### Part 1: Windows Server Attack

Note: This is a public-facing windows server that VSI employees access.
 
#### Question 1
![image](https://user-images.githubusercontent.com/93692721/169816107-688f7ee7-a1d6-4d92-bc00-860cbb9c7ab4.png)
  - Several users were impacted during the attack on March 25th.
  - Based on the attack signatures, what mitigations would you recommend to protect each user account? Provide global mitigations that the whole company can use and individual mitigations that are specific to each user.
    - I would recommend creating a VPN to be used by all employees, to ensure no unauthorized access to the server is allowed. Having the company whitelist the employees IP addresses, would also help ensure a more secure network for each employee individually. 

#### Question 2
- VSI has insider information that JobeCorp attempted to target users by sending "Bad Logins" to lock out every user.
- What sort of mitigation could you use to protect against this?
    - Creating a company wide failed login attempt policy would be the easiest course of action. Setting it at 3 failed login attempts within a 10 minute period of time will lockout that user account, which would then need admin privileges to unlock the account.

---

### Part 2: Apache Webserver Attack:

#### Question 1
- Based on the geographic map, recommend a firewall rule that the networking team should implement.
- Provide a "plain english" description of the rule.
  - For example: "Block all incoming HTTP traffic where the source IP comes from the city of Los Angeles."
  
  - Recommended Firewall Rule: 
    - "Block all incoming HTTP traffic where the source IP is coming out of either of these cities "Kiev" or "Kharkiv" in Ukraine."

- Provide a screen shot of the geographic map that justifies why you created this rule. 
![image](https://user-images.githubusercontent.com/93692721/169817849-635efff7-752c-4672-8487-45350dbfb5b8.png)
![image](https://user-images.githubusercontent.com/93692721/169817896-19f2dbc7-d1f5-4418-aecd-e7e687d54e1c.png)

  
#### Question 2

- VSI has insider information that JobeCorp will launch the same webserver attack but use a different IP each time in order to avoid being stopped by the rule you just created.

- What other rules can you create to protect VSI from attacks against your webserver?
  - Conceive of two more rules in "plain english". 
  - Hint: Look for other fields that indicate the attacker.

  - Additional Rules: 
    - "Lock User Account after 3 failed login attempts within 10 minute time period"
    - Creating a web application firewall to determine the true source IP of all incoming traffic, with a rule of "Block all Malicious Traffic" 
  
---

### Guidelines for your Submission:
  
In a word document, provide the following:
- Answers for all questions.
- Screenshots where indicated

Submit your findings in BootCampSpot!

