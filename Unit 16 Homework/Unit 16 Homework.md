# Unit 16 Homework: Pen Testing 1

### Step 1: Google Dorking
- Using Google, can you identify who the Chief Executive Officer of Altoro Mutual is:

    > Karl Fitzgerald
- How can this information be helpful to an attacker:

    > This is information that can be used to perform social engineering or phishing.

### Step 2: DNS and Domain Discovery
  
Enter the IP address for demo.testfire.net into Domain Dossier and answer the following questions based on the results:

   ![HW16_1](https://user-images.githubusercontent.com/93692721/169436960-a2c498e1-3591-413d-a0b6-1f243c71daaf.png)

  
1. Where is the company located:
 
    > Sunnyvale, CA
   
   ![HW16_2](https://user-images.githubusercontent.com/93692721/169437032-e2eee97c-9bc0-4c23-8205-d7aed8e8178b.png)

2. What is the NetRange IP address:

    > 65.61.137.64 - 65.61.137.127

   ![HW16_3](https://user-images.githubusercontent.com/93692721/169437131-44e5f2a8-c1d6-4f36-99cb-3125e4d01200.png)

3. What is the company they use to store their infrastructure: 

    > Rackspace Backbone Engineering (C05762718)
 
   ![HW16_3](https://user-images.githubusercontent.com/93692721/169437262-f141231f-dcf5-404a-be94-5915ff9d253e.png)
    

4. What is the IP address of the DNS server: 

    > 65.61.137.117

    ![HW16_4](https://user-images.githubusercontent.com/93692721/169437419-7ddd3135-389b-477b-aa12-3d0effc1f66d.png)

### Step 3: Shodan

1. What open ports and running services did Shodan find:

    > - Open Ports: 80, 443, 8080
    > - Services: Apache Tomcat/Coyote JSP Engine (1.1)

    ![HW16_5](https://user-images.githubusercontent.com/93692721/169437450-a5379871-42ef-4c22-9dc4-97d82e848e0c.png)

### Step 4: Recon-ng

1. Install the Recon module xssed.
 
    > marketplace install xssed

    ![HW16_6](https://user-images.githubusercontent.com/93692721/169437503-70facab3-6064-4d5a-b0e5-6f3714a2c7f6.png)

2. Set the source to demo.testfire.net.

    > options set SOURCE demo.testfire.net
  
    ![HW16_7](https://user-images.githubusercontent.com/93692721/169437535-71163dd0-d53e-4e93-a450-c874abcc84c8.png)
  
3. Run the module.

    > run

    ![HW16_8](https://user-images.githubusercontent.com/93692721/169437608-e497656b-2583-4071-acba-8a2677bd5b63.png)

4. Is Altoro Mutual vulnerable to XSS: 

    > Yes. Per the screenshot provided, there is a vulnerability to XSS found.
   
    ![HW16_9](https://user-images.githubusercontent.com/93692721/169437645-b929e021-6cbc-403c-a4ff-385886e0f720.png)

### Step 5: Zenmap
Your client has asked that you help identify any vulnerabilities with their file-sharing server. Using the Metasploitable machine to act as your client's server, complete the following:


1. Command for Zenmap to run a service scan against the Metasploitable machine:

     > nmap-T4-A-v 192.168.0.10

2. Bonus command to output results into a new text file named zenmapscan.txt:
 
 
3. Use Zenmap's scripting engine to identify a vulnerability associated with the service running on the 139/445 port from your previous scan. Zenmap vulnerability script command:
 
     > nmap--script ftp-vsftpd-backdoor 192.168.0.10

   ![HW16_10](https://user-images.githubusercontent.com/93692721/169437675-8b56eb6b-41a3-4d82-9d56-90d78a2c4132.png)

- Once you have identified this vulnerability, answer the following questions for your client:

 1. What is the vulnerability:
 
    > SMB Listening in on Port

 2. Why is it dangerous:
 
    > Since ports 139 and 445 are SMB ports, these ports being open can be vulnerable to exploit by port listening. 

 3. What mitigation strategies can you recommendations for the client to protect their server:
  
    > - Ensure that systems are up-to-date
    > - Use Firewall or VPN
    > - Make sure that there is redundancy (back-up of files) in case of attack
