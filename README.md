# Generating Telemetry & Detection Home Lab

## Objective

This Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to generate telemetry by first using nmap to scan for open ports, then creating a malware file and running it with the windows defender off, and then detecting and seeing what kind of telemetry was generated and analyze logs within Splunk. This hands-on experience was designed to deepen understanding of network security, attack patterns, and detection.

### Skills Learned

- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used

- Splunk for log ingestion and analysis.
- nmap
- msfvenom
- Kali Linux
- Windows

## Steps
First, I made sure to make note of the Linux machine’s IP, as well as the Windows machine’s IP.

After that, I scanned the Windows machine for any open ports using nmap as you can see in reference 1.

Ref 1: nmap ports scanning Windows machine

<img width="575" height="463" alt="Screenshot 2026-07-12 at 8 18 57 PM" src="https://github.com/user-attachments/assets/957ca55d-75dd-4e65-bee3-aa048b0e5f59" />

<img width="548" height="454" alt="Screenshot 2026-07-12 at 8 24 29 PM" src="https://github.com/user-attachments/assets/ad56a8c1-30b2-4431-ad8b-f3f4a4227cbf" />

As we can see, port 3389 is open.

Then I built out my malware using a meterpreter reverse shell as my payload. I picked out a payload from the list that I got using the command: msfvenom -l payloads

The payload that I chose is shown in ref 2.

Ref 2: Choosing payload.

<img width="687" height="455" alt="Screenshot 2026-07-12 at 8 31 39 PM" src="https://github.com/user-attachments/assets/3f5e962c-674c-46e4-994a-5c9b480dad16" />

Then I started building out my malware using the command shown in ref 3.
This malware’s payload is instructed to connect back to our machine based on the lhost and lport. 

Ref 3: building the malware.

<img width="619" height="332" alt="Screenshot 2026-07-12 at 8 45 05 PM" src="https://github.com/user-attachments/assets/13259eeb-c699-4fb1-93d1-48f35df7cb16" />

Then I built out a handler that will listen in on the port that we have configured in our malware. 
To do that, I opened up metasploit using the “msfconsole” command, then I entered the command: use exploit/multi/handler. Ref 4 shows these 2 steps.

Ref 4: building handler

<img width="689" height="439" alt="Screenshot 2026-07-12 at 8 53 38 PM" src="https://github.com/user-attachments/assets/161b286e-5c68-4143-9475-3c3113bb4ea5" />

<img width="708" height="490" alt="Screenshot 2026-07-12 at 8 54 21 PM" src="https://github.com/user-attachments/assets/3cb7c98e-ac79-4b41-84e6-1b8a5d36d9c4" />

