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
