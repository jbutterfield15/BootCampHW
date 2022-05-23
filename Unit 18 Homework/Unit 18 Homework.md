## Unit 18 Homework: Let's go Splunking!

#### Scenario
You have just been hired as an SOC Analyst by Vandalay Industries, an importing and exporting company.

- Vandalay Industries uses Splunk for their security monitoring and have been experiencing a variety of security issues against their online systems over the past few months.

- You are tasked with developing searches, custom reports and alerts to monitor Vandalay's security environment in order to protect them from future attacks.



#### System Requirements
You will be using the Splunk app located in the Ubuntu VM.

#### Your Objective
Utilize your Splunk skills to design a powerful monitoring solution to protect Vandaly from security attacks.
After you complete the assignment you are asked to provide the following:

- Screen shots where indicated.
- Custom report results where indicated.


#### Topics Covered in This Assignment

- Researching and adding new apps
- Installing new apps
- Uploading files
- Splunk searching
- Using fields
- Custom reports
- Custom alerts

Let's get started!


### Vandalay Industries Monitoring Activity Instructions

#### Step 1: The Need for Speed
**Background**: As the worldwide leader of importing and exporting, Vandalay Industries has been the target of many adversaries attempting to disrupt their online business. Recently, Vandaly has been experiencing DDOS attacks against their web servers.

Not only were web servers taken offline by a DDOS attack, but upload and download speed were also significantly impacted after the outage. Your networking team provided results of a network speed run around the time of the latest DDOS attack.

**Task**: Create a report to determine the impact that the DDOS attack had on download and upload speed. Additionally, create an additional field to calculate the ratio of the upload speed to the download speed.


1. Upload the following file of the system speeds around the time of the attack.

    - Speed Test File



2. Using the eval command, create a field called ratio that shows the ratio between the upload and download speeds.

   - Hint: The format for creating a ratio is: | eval new_field_name = 'fieldA'  / 'fieldB'

    ![HW_1](https://user-images.githubusercontent.com/93692721/169772175-8502bae2-0db1-4af4-9697-dfc48194686f.PNG)



3. Create a report using the Splunk's table command to display the following fields in a statistics report:

   - _time
   - IP_ADDRESS
   - DOWNLOAD_MEGABITS
   - UPLOAD_MEGABITS
   - ratio

   Hint: Use the following format when for the table command: | table fieldA  fieldB fieldC

    ![HW_2](https://user-images.githubusercontent.com/93692721/169772369-073eb5b5-f8a5-4e7b-8c60-ed1391e2c4c7.png)

4. Answer the following questions:

   - Based on the report created, what is the approximate date and time of the attack?
   
        > It appears the attack began around 2:30PM on 02/23/2020 and lasted until 11:30PM on 02/23/2020.

   - How long did it take your systems to recover?
   
        >  Since the system appears to stabalize around 11:30PM, the systems took roughly 9 hours to recover from the attack.

    Submit a screen shot of your report and the answer to the questions above.
    
    ![HW_3](https://user-images.githubusercontent.com/93692721/169773793-6b528176-9c2b-4f77-8a5c-130ee47ec5b0.png)

    
    ![HW_4](https://user-images.githubusercontent.com/93692721/169773939-a04a5345-fffb-4de6-bd2b-19f296a9a46a.png)

    
    
#### Step 2: Are We Vulnerable?

**Background**:  Due to the frequency of attacks, your manager needs to be sure that sensitive customer data on their servers is not vulnerable. Since Vandalay uses Nessus vulnerability scanners, you have pulled the last 24 hours of scans to see if there are any critical vulnerabilities.

  - For more information on Nessus, read the following link: https://www.tenable.com/products/nessus


**Task**: Create a report determining how many critical vulnerabilities exist on the customer data server. Then, build an alert to notify your team if a critical vulnerability reappears on this server.


1. Upload the following file from the Nessus vulnerability scan.

  - Nessus Scan Results



2. Create a report that shows the count of critical vulnerabilities from the customer database server.

  - The database server IP is 10.11.36.23.
  - The field that identifies the level of vulnerabilities is severity.

    ![HW_5](https://user-images.githubusercontent.com/93692721/169774627-cde8efaa-f55b-4d58-a4d1-fc6862899685.png)
    
    ![HW_6](https://user-images.githubusercontent.com/93692721/169774759-872151f8-6efd-4d60-9183-325a8de81bd0.png)
    
    ![HW_7](https://user-images.githubusercontent.com/93692721/169774950-ced3c937-d50b-4691-8356-d130611df8e2.png)


3. Build an alert that monitors every day to see if this server has any critical vulnerabilities. If a vulnerability exists, have an alert emailed to soc@vandalay.com.

    Submit a screenshot of your report and a screenshot of proof that the alert has been created.
    
    ![HW_8](https://user-images.githubusercontent.com/93692721/169775089-1cace0b6-1d14-4864-b607-aa9736357269.png)
    
    ![HW_9](https://user-images.githubusercontent.com/93692721/169775200-fdf7ec61-3a96-461f-880e-724c4838963e.png)
    
    ![HW_10](https://user-images.githubusercontent.com/93692721/169775366-9a12c4be-4f0d-4600-b63e-b72df5968146.png)

#### Step 3: Drawing the (base)line
**Background**:  A Vandaly server is also experiencing brute force attacks into their administrator account. Management would like you to set up monitoring to notify the SOC team if a brute force attack occurs again.

**Task**: Analyze administrator logs that document a brute force attack. Then, create a baseline of the ordinary amount of administrator bad logins and determine a threshold to indicate if a brute force attack is occurring.


1. Upload the administrator login logs.

  - Admin Logins



2. When did the brute force attack occur?

      > It appears that the attack started around 9:00 AM on 02/21/2020 with a spike in failed login attempts. 

  - Hints:

        - Look for the name field to find failed logins.
        - Note the attack lasted several hours.


    ![HW_11](https://user-images.githubusercontent.com/93692721/169777909-a2e3c0d6-2f6f-4eb2-8425-8139c2e304a7.png)

     
        
3. Determine a baseline of normal activity and a threshold that would alert if a brute force attack is occurring.

      > The normal activity appears to have been less than 34 log in attempts, and considering the number of attempts spiked to more than 120, a decent threshold would be set at 35 attempts within an hour. 

4. Design an alert to check the threshold every hour and email the SOC team at SOC@vandalay.com if triggered.

Submit the answers to the questions about the brute force timing, baseline and threshold. Additionally, provide a screenshot as proof that the alert has been created.

   ![HW_12](https://user-images.githubusercontent.com/93692721/169778020-109cfc62-4c38-4df3-9462-4cdd0e6d5a61.png)
    
   ![HW_13](https://user-images.githubusercontent.com/93692721/169778105-15eefbb5-5339-4ac2-ae1c-1e2ccb4ba706.png)
    
   ![HW_14](https://user-images.githubusercontent.com/93692721/169778248-fa17bb9c-60ff-4fbd-ab14-2f2db3a6721c.png)
    
#### Your Submission
In a word document, provide the following:

  - Answers to all questions where indicated.
  - Screenshots where indicated.
