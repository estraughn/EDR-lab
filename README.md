# EDR lab

## Objective
To develop skills in detecting, analyzing, and responding to endpoint threats by leveraging EDR tools and techniques, and improving incident response capabilities.



### Skills Learned

-  Identifyed malicious activities and potential indicators of compromise (IOCs) on endpoints using EDR tools
-  Utilized real-time monitoring and analytics to track system behaviors and detect anomalies
-  Analyzed malicious files and processes detected on endpoints to understand their behavior and impact
-  Analyzed endpoint logs and telemetry data to uncover patterns and identify security breaches
-  Gained hands-on experience with EDR platforms 



### Tools Used

- Task Scheduler
- Metasploit
- Kali linux
- Powershell
- Registry Editor
- Windows Services
- Autoruns


## Steps

1. First I created some test malware utilizing metasploit on my Kali Linux VM to infect my Windows VM. The malware I created will use a reverse TCP connection between my host VM (kali linux) and my target VM (windows 11). I then imput the settings for the exploitation by inputting my local host and port number for the reverse tcp connection to run through. Then I created a directory on my kali linux machine to house the payload, and then spun up a http server that my windows VM could connect to and trigger the malware. I then navigated on my windows VM over to the ip address and port number of http server, once there I clicked the suspicous link and downloaded the malware. After the malware was downloaded I then proceeded to open a command prompt as an administrator and executed the notmalware.exe file. I then created a shell connection between my host and the target to allow me access to the command prompt and created a directory for the exfiltration of data.

*Ref 1.1:![Screenshot 2025-01-31 163828](https://github.com/user-attachments/assets/be75f5d1-a337-4072-bbf9-4fb6b2e18cc3)

*Ref 1.2:![Screenshot 2025-01-31 164411](https://github.com/user-attachments/assets/b3f41817-0fdd-4d63-8d57-e7d071f35255)

*Ref 1.3:![Screenshot 2025-01-31 164547](https://github.com/user-attachments/assets/53219003-0d35-436f-9367-1e3ede431208)

*Ref 1.4:![Screenshot 2025-01-31 165901](https://github.com/user-attachments/assets/963ed34d-38c6-49bd-8665-32da3f9d21cf)

*Ref 1.5![Screenshot 2025-01-31 171252](https://github.com/user-attachments/assets/1b732888-7d3b-4299-81ff-cadfb821d377)

2. Now for me to establish persistance on my target VM I will Create a backdoor by adding a key to the Windows registry. First utilizing my reverse tcp connection and the shell command I ran the commands in Ref 2.1 creating a new key named NotABackDoor that will run on startup of my target VM giving me persistant access. I then went to the registry editor on my target VM to confirm the creation of my registry entry. To establish a backup method of persistance I also created a backdoor within Windows services by executing the command in Ref 2.3 via my reverse tcp connected shell. I then went over to Windows services to confirm the creation of new auto start service. Lastly to establish one last foothold I will create a scheduled service to execute my malware every day at 09:00 to provide me with continous access. To do this I executed the command shown in Ref 2.5 from my kali linux VM. I then opened Windows task scheduler on my target VM to confirm the creation and proper configuration of my scheduled task.

*Ref 2.1:![Screenshot 2025-02-08 102310](https://github.com/user-attachments/assets/03eb6f55-bc86-4645-9fa9-4b50505a8b82)

*Ref 2.2:![Screenshot 2025-02-08 103626](https://github.com/user-attachments/assets/a3dfb3b3-0068-48fe-96ab-850e48dc999d)

*Ref 2.3:![Screenshot 2025-02-10 112236](https://github.com/user-attachments/assets/0523947e-b2a8-4670-970c-8de7c2553dd9)

*Ref 2.4:![Screenshot 2025-02-10 113256](https://github.com/user-attachments/assets/cf3929fb-b25e-4d2a-8917-a5d2b9a0f2a8)

*Ref 2.5:![Screenshot 2025-02-10 115159](https://github.com/user-attachments/assets/79189329-52e1-479f-a0d9-c2e6327b735d)

*Ref 2.6:![Screenshot 2025-02-10 115637](https://github.com/user-attachments/assets/84f2fc00-bf03-4321-b350-dff0a25add13)

3. Now that my target VM is infected with malware the EDR process can begin. So my first step is to utilize some of the built in Windows tools to begin my investigation, I open powershell in adminstrator mode and run the tasklist command to view running processes on my VM. I then located the downloaded file that contained the malware which in this case is "notmalware.exe" and took note of the process ID number (PID) and the parent process ID number. Followed by running the same command with the /M argument to return the dynamic link libraries (DLL) associated with the malware file and documented them and proceeded to delete the file. The next step is to investigate the Windows registry to see if the attacker added any entries to the registry to establish persistance. In this case I noted that a new entry had been created named NotABackDoor I took note of this. Then I proceeded to investigate Windows services to identify any other possible backdoors into the endpoint. I made note of the newly added service in windows services called BackupService Which if a real scenario I would compare a baseline file of services vs the current to find discrepancies. I did a deeper dive into the properties of this service by using the command in Ref 3.6 and made note of my findings. For the last part of my investigation I proceeded to check for any suspicous scheduled tasks that have been added to the endpoint. In this case I noted the addition of the scheduled task SystemCleanup and proceeded to use the command in Ref 3.7 to find out more about the task. Now using the Autoruns application I made my way to all three of the established persistance methods and proceeded to remove all of the additons to the endpoint and then proceeded to restore the VM to its last known clean backup.

*Ref 3.1: ![Screenshot 2025-02-07 115628](https://github.com/user-attachments/assets/97c87243-5b0f-44aa-9cf9-4345ab02cd62)

*Ref 3.2: ![Screenshot 2025-02-07 120504](https://github.com/user-attachments/assets/715c3071-12dc-4f6e-95c8-b5b2c3474220)

*Ref 3.3: ![Screenshot 2025-02-07 121439](https://github.com/user-attachments/assets/4608f967-6d20-4c0b-ba25-574116acac02)

*Ref 3.4: ![Screenshot 2025-02-08 102604](https://github.com/user-attachments/assets/dd9df999-da7e-4253-b10d-a76019473a71)

*Ref 3.5: ![Screenshot 2025-02-08 111332](https://github.com/user-attachments/assets/0bff2f6d-cf1a-4ef1-873a-9a78fe3afa00)

*Ref 3.6: ![Screenshot 2025-02-10 113559](https://github.com/user-attachments/assets/f5d3ef9b-4aef-48d3-86ea-3c9bad593fff)

*Ref 3.7: ![Screenshot 2025-02-10 120122](https://github.com/user-attachments/assets/b46ded68-2cae-463c-b549-6cdb2bd1212e)

*Ref 3.8: ![Screenshot 2025-02-10 121513](https://github.com/user-attachments/assets/995c0738-ca11-46b4-b58e-efb31dd7ae32)
