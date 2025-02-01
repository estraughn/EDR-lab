# EDR lab

## Objective
To develop skills in detecting, analyzing, and responding to endpoint threats by leveraging EDR tools and techniques, , and improving incident response capabilities.



### Skills Learned

-  Identifyed malicious activities and potential indicators of compromise (IOCs) on endpoints using EDR tools
-  Utilized real-time monitoring and analytics to track system behaviors and detect anomalies
-  Analyzed malicious files and processes detected on endpoints to understand their behavior and impact
-  Analyzed endpoint logs and telemetry data to uncover patterns and identify security breaches
-  Gained hands-on experience with EDR platforms 



### Tools Used

- Sysmon
- Cron Jobs
- LimaCharlie
- Metasploit
- Kali linux


## Steps

1. First I created some test malware utilizing metasploit on my Kali Linux VM to infect my Windows VM. The malware I created will use a reverse TCP connection between my host VM (kali linux) and my target VM (windows 11). I then imput the settings for the exploitation by inputting my local host and port number for the reverse tcp connection to run through. Then I created a directory on my kali linux machine to house the payload, and then spun up a http server that my windows VM could connect to and trigger the malware. I then navigated on my windows VM over to the ip address and port number of http server, once there I clicked the suspicous link and downloaded the malware. After the malware was downloaded I then proceeded to open a command prompt as an administrator and executed the notmalware.exe file. I then created a shell connection between my host and the target to allow me access to the command prompt and created a directory for the exfiltration of data.

*Ref 1.1:![Screenshot 2025-01-31 163828](https://github.com/user-attachments/assets/be75f5d1-a337-4072-bbf9-4fb6b2e18cc3)
*Ref 1.2:![Screenshot 2025-01-31 164411](https://github.com/user-attachments/assets/b3f41817-0fdd-4d63-8d57-e7d071f35255)
*Ref 1.3:![Screenshot 2025-01-31 164547](https://github.com/user-attachments/assets/53219003-0d35-436f-9367-1e3ede431208)
*Ref 1.4:![Screenshot 2025-01-31 165901](https://github.com/user-attachments/assets/963ed34d-38c6-49bd-8665-32da3f9d21cf)

*Ref 1.5![Screenshot 2025-01-31 171252](https://github.com/user-attachments/assets/1b732888-7d3b-4299-81ff-cadfb821d377)

