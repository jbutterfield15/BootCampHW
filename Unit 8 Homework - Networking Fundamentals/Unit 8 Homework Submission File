Unit 8 Homework - Networking Fundamentals


Phase I

fping -g 15.199.95.91/28 - Was found to be unreachable
fping -g 15.199.94.91/28 - Was found to be unreachable
fping -g 11.199.158.91/28 - Was found to be unreachable
fping -g 167.172.144.11/32 - Was found to be Alive
fping -g 11.199.141.91/28 - Was found to be unreachable

To mitigate these potentially vulnerabilities, Rockstar Corp. should restrict all ICMP Echo requests to all of their servers including 167.172.144.11.

The results would be found in the Network Layer, due to the need of an IP Address to run the ping command.

Phase II

The results indicate that the only open port is port 22 which is used by the SSH Service. Rockstar Corp should also filter out SSH traffic to restrict unauthorized access to their servers.
[SYN SCAN](https://github.com/jbutterfield15/BootCampHW/blob/de1ea371380a84fa4bdbf7083907d63b8683e940/Unit%208%20Homework%20-%20Networking%20Fundamentals/Images/Phase%20II%20SYN%20Scan%20Results.PNG)

A SYN SCAN runs on the Transport Layer

Phase III

Running cat /etc/hosts/ indicates what is causing the redirection when trying to rollingstone.com. It displayed an IP Address of 98.137.246.8

To figure out the domain of the IP Address listed above I ran nslookup 98.137.246.8, which indicated that the domain is Yahoo.com
[nslookup](https://github.com/jbutterfield15/BootCampHW/blob/de1ea371380a84fa4bdbf7083907d63b8683e940/Unit%208%20Homework%20-%20Networking%20Fundamentals/Images/Phase%20III%20nslookup.PNG)

DNS is found in the Application Layer

Phase IV

After SSH'ing into Jimi, I ran cd /etc, followed by cat packetcaputreinfo.txt to locate the hackers packet captures.
[Packet Capture Location](https://github.com/jbutterfield15/BootCampHW/blob/de1ea371380a84fa4bdbf7083907d63b8683e940/Unit%208%20Homework%20-%20Networking%20Fundamentals/Images/Phase%20IV%20Packet%20Capture%20locations.PNG)

[HTTP Findings](https://github.com/jbutterfield15/BootCampHW/blob/de1ea371380a84fa4bdbf7083907d63b8683e940/Unit%208%20Homework%20-%20Networking%20Fundamentals/Images/HTTP%20Findings.PNG)

HTTP Runs on the Application Layer

[ARP Findings](https://github.com/jbutterfield15/BootCampHW/blob/de1ea371380a84fa4bdbf7083907d63b8683e940/Unit%208%20Homework%20-%20Networking%20Fundamentals/Images/ARP%20Findings.PNG)

A possible mitigation for these findings would be to create static ARP entries, rather than dynamic ones. This would ensure that IP to MAC mappings are created in the local ARP cache and cannot be changed. 

ARP is Located in the Data Link Layer
