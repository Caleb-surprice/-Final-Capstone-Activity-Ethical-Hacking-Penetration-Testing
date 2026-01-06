# 🛡️ Capstone Project: Network & Web Application Security Assessment

**Author**
Caleb Kutani

# Environment

>> Kali Linux (Ethical Hacker Course VM)

>> Target Networks: 10.5.5.0/24, 192.168.0.0/24

>> Tools: Nmap, smbclient, Wireshark, Browser

# 📌 Project Overview

This capstone project focuses on practical reconnaissance, enumeration, and vulnerability analysis techniques used in real-world cybersecurity assessments. The project covers web application enumeration, directory listing analysis, SQL injection remediation, SMB share enumeration, and packet capture (PCAP) analysis.

All activities were conducted in a controlled lab environment for educational purposes only.

# 🎯 Objectives

>> Identify exposed web directories and sensitive files

>> Analyze common web vulnerabilities and propose remediation

>> Enumerate SMB services and unsecured file shares

>> Analyze network traffic using PCAP files

>> Document findings and security recommendations

# 🧰 Tools & Technologies Used

>> Nmap (service discovery & enumeration)

>> smbclient / enum scripts

>> Wireshark

>> Web browser (manual inspection)

>> Linux (Kali)


# 🧪 Challenge 1: SQL Injection
**Vulnerability Identified**

SQL Injection in DVWA (Low Security)

**Key Actions**

>> Identified vulnerable input field

<img width="638" height="140" alt="chal1 1 input field" src="https://github.com/user-attachments/assets/91193dbd-4875-4f9c-9432-c45a9d2f6857" />

>> Extracted credentials from users table

<img width="536" height="62" alt="1  Bob Smith&#39;s (smithy account)" src="https://github.com/user-attachments/assets/7f5a6f99-8752-48f4-a468-360abb7aaf32" />

>> Cracked MD5 password hash

<img width="1066" height="418" alt="chal1 3 pwd cracked" src="https://github.com/user-attachments/assets/e8b3dc53-7a1a-4ec1-84fe-c8009fa55f5d" />

>> Logged in as Bob Smith via SSH

<img width="766" height="437" alt="2  flag 1 found" src="https://github.com/user-attachments/assets/4a6f4dfa-bea1-4dc1-aa78-01ef65a4833c" />


**Findings**

Username: smithy

Password: password

Flag File Location: /home/smithy/

Flag Filename: my_passwords.txt

flag ccode: 8748wf8j

**SQL Injection Remediation**

>> Use prepared statements

>> Input validation and sanitization

>> Least-privilege database accounts

>> Hide detailed SQL error messages

>> Use secure password hashing (bcrypt/Argon2)


#🌐 Challenge 2: Web Server Vulnerabilities
**Vulnerability Identified**

Directory listing enabled on Apache web server

**Reconnaissance Command**
>> nmap --script http-enum -p 80 10.5.5.12

<img width="740" height="295" alt="chal 2 2  nmap scan for files" src="https://github.com/user-attachments/assets/69586995-638a-4639-ba57-f11c3377dd70" />

>> Checking the /config/ filepath

 <img width="631" height="377" alt="chal2 2  config file" src="https://github.com/user-attachments/assets/233aef9b-2845-4db1-9cf8-f1ffeed32927" />
 
<img width="642" height="231" alt="chal2 3  flag found" src="https://github.com/user-attachments/assets/b0d3b202-be18-45d8-b570-c3ce065955ab" />


**Accessible Directories**

/config/

/docs/

/external/

**Flag Discovery**

Location: /config/db_form.html

Filename: db_form.html

flag code: aWe-4975

**Directory Listing Remediation**

>> Disable directory indexing (Options -Indexes)

>> Add default index files (index.html)


# 🗄️ Challenge 3: SMB Enumeration
**SMB Host Identified**

IP Address: 10.5.5.14
Ports: 139, 445 (Samba)

**Enumeration Commands**
>> smbclient -L //10.5.5.14 -N

<img width="661" height="356" alt="chal3 4 files found" src="https://github.com/user-attachments/assets/2587edb3-6fb5-49c3-a037-97b363cbb1b5" />

>> nmap --script smb-enum-shares.nse -p 445 10.5.5.14

<img width="460" height="185" alt="chal3 3 network scan" src="https://github.com/user-attachments/assets/db54153c-85e5-4c46-baef-637b9d69cb3c" />

>> searching through OTHER directory

<img width="623" height="79" alt="chal3 6 file found" src="https://github.com/user-attachments/assets/fda4b277-ef7c-4202-a249-c2295fd08895" /> 

>> found another file

 <img width="623" height="79" alt="chal3 6 file found" src="https://github.com/user-attachments/assets/fa6fd656-d6d6-40b2-8123-04508e28398c" />

<img width="861" height="55" alt="chal3 7  flag copied" src="https://github.com/user-attachments/assets/df875fb9-3726-4cc2-b7c8-3e95c6bdcde4" />

Flag Found

<img width="470" height="100" alt="chal3 8  flag opened" src="https://github.com/user-attachments/assets/5c9fa2c1-cfbc-4c76-b304-8ad44749e5a7" />


**Shares Found**

>> homes

>> workfiles

>> print$

>> IPC$


**Anonymous Access Confirmed**

>> workfiles

>> print$

>> IPC$

**Challenge 3 Flag**

Share: print$

Filename: sxij42.txt

Flag Code: NWs39691

**SMB Remediation**

>> Disable anonymous/guest access

>> Restrict SMB using firewalls and ACLs


# 📡 Challenge 4: PCAP Analysis

**File Analyzed**

SA.pcap

**Tool**

Wireshark

**Findings**

>> Target IP Address: (10.5.5.11)

>> Directories Observed:
 /test/ , /data/ , /includes/ , /passwords/, /styles/,  /javascript/ , /webservices/

<img width="1355" height="414" alt="chal4 2 packet analysis" src="https://github.com/user-attachments/assets/0475cebc-1f5f-446a-9e64-cb413ab3fea0" />

>> Flag URL: (http://10.5.5.11/data/user_accounts.xml)

<img width="820" height="382" alt="chal4 3 file found" src="https://github.com/user-attachments/assets/040d6f12-b983-4e64-889c-a31e842a2ea2" />

<img width="815" height="603" alt="chal4 1 flag found" src="https://github.com/user-attachments/assets/717b8e67-1549-487e-962d-dc11a5b831bb" />


**PCAP Remediation**

>> Use HTTPS instead of HTTP

>> Encrypt sensitive network traffic
