# ApexPlanet Cybersecurity Internship - Task 3

# Web Application Security

## Overview

This repository contains the implementation of **Task 3 – Web Application Security** from the ApexPlanet Cybersecurity Internship Program.

The objective of this task is to understand, identify, exploit, and mitigate common web application vulnerabilities in a controlled lab environment using OWASP Top 10 concepts.

The practical exercises were performed on **DVWA (Damn Vulnerable Web Application)** running locally inside Kali Linux.

---

# Objective

The objectives of this task are:

- Learn Web Application Security
- Understand OWASP Top 10 vulnerabilities
- Perform SQL Injection attacks
- Demonstrate Stored and Reflected XSS
- Demonstrate CSRF attack
- Perform Local File Inclusion
- Learn Burp Suite request interception
- Perform Burp Suite Intruder fuzzing
- Analyze HTTP Security Headers
- Document mitigation techniques

---

# Lab Environment

## Operating System

- Kali Linux

## Vulnerable Application

- DVWA (Damn Vulnerable Web Application)

## Web Server

- Apache2

## Database

- MariaDB

## Programming Language

- PHP

## Tools Used

- Burp Suite Community Edition
- Firefox Browser
- Apache2
- MariaDB
- Git
- curl

---

# Project Structure

```
ApexPlanet-Task3-Web-Application-Security/

│── README.md
│── Task3_Report.pdf
│── Findings.md
│── Mitigation_Notes.md
│── Commands_Used.txt
│── Apache_Headers_Config.txt
│
├── Screenshots
│   ├── DVWA Setup
│   ├── SQL Injection
│   ├── Stored XSS
│   ├── Reflected XSS
│   ├── CSRF
│   ├── File Inclusion
│   ├── Burp Suite
│   ├── Security Headers
│
└── Video
    └── Demo Link
```

---

# Vulnerabilities Covered

## SQL Injection

Performed SQL Injection against DVWA.

### Objective

Extract information from the database using vulnerable SQL queries.

### Demonstrated

- Authentication bypass
- Data extraction
- SQL payload execution

### Mitigation

- Prepared Statements
- Parameterized Queries
- Input Validation
- Least Privilege Database Accounts

---

## Cross Site Scripting (XSS)

### Stored XSS

Injected malicious JavaScript into stored input fields.

Example payload

```html
<script>alert('Stored XSS')</script>
```

### Reflected XSS

Injected JavaScript through URL parameters.

Example payload

```html
<script>alert('Reflected XSS')</script>
```

### Mitigation

- Output Encoding
- Input Validation
- Content Security Policy (CSP)
- HttpOnly Cookies

---

## Cross Site Request Forgery (CSRF)

Created a CSRF page that changes the victim's password.

### Mitigation

- CSRF Tokens
- SameSite Cookies
- Origin Validation
- Re-authentication

---

## File Inclusion

Performed Local File Inclusion testing.

Example payload

```
../../../../etc/passwd
```

### Mitigation

- Whitelist Allowed Files
- Validate File Paths
- Disable allow_url_include
- Secure File Handling

---

## Burp Suite

Performed

- HTTP Request Interception
- Request Modification
- Intruder Fuzzing

---

## HTTP Security Headers

Verified and configured

- Content-Security-Policy
- X-Frame-Options
- X-Content-Type-Options
- Referrer-Policy
- Permissions-Policy

---

# Installation

## Update Kali

```bash
sudo apt update
sudo apt upgrade -y
```

---

## Install Apache

```bash
sudo apt install apache2 -y
```

---

## Install MariaDB

```bash
sudo apt install mariadb-server -y
```

---

## Install PHP

```bash
sudo apt install php php-mysqli php-gd libapache2-mod-php -y
```

---

## Install Git

```bash
sudo apt install git -y
```

---

## Start Apache

```bash
sudo systemctl start apache2
sudo systemctl enable apache2
```

---

## Start MariaDB

```bash
sudo systemctl start mariadb
sudo systemctl enable mariadb
```

---

## Clone DVWA

```bash
cd /var/www/html

sudo rm index.html

sudo git clone https://github.com/digininja/DVWA.git
```

---

## Set Permissions

```bash
sudo chown -R www-data:www-data /var/www/html/DVWA

sudo chmod -R 755 /var/www/html/DVWA
```

---

## Configure DVWA

```bash
cd /var/www/html/DVWA/config

sudo cp config.inc.php.dist config.inc.php

sudo nano config.inc.php
```

---

## Create Database

```bash
sudo mysql
```

```sql
CREATE DATABASE dvwa;

CREATE USER 'dvwa'@'localhost' IDENTIFIED BY 'p@ssw0rd';

GRANT ALL PRIVILEGES ON dvwa.* TO 'dvwa'@'localhost';

FLUSH PRIVILEGES;

EXIT;
```

---

## Restart Apache

```bash
sudo systemctl restart apache2
```

---

## Open DVWA

```
http://localhost/DVWA
```

---

# Burp Suite

Launch Burp Suite

```bash
burpsuite
```

Configure browser proxy

```
127.0.0.1

8080
```

---

# Check HTTP Headers

```bash
curl -I http://localhost/DVWA
```

---

# Enable Apache Headers

```bash
sudo a2enmod headers

sudo systemctl restart apache2
```

---

# Useful Commands

Check Apache

```bash
sudo systemctl status apache2
```

Check MariaDB

```bash
sudo systemctl status mariadb
```

Restart Services

```bash
sudo systemctl restart apache2

sudo systemctl restart mariadb
```

Check PHP

```bash
php -v
```

Check Git

```bash
git --version
```

Check Apache Version

```bash
apache2 -v
```

---

# Learning Outcomes

After completing this task, I gained practical experience in

- SQL Injection
- Cross Site Scripting
- Cross Site Request Forgery
- Local File Inclusion
- Burp Suite
- HTTP Request Interception
- Web Application Testing
- HTTP Security Headers
- Secure Coding Practices
- OWASP Top 10

---

# Screenshots

- Kali Linux Setup
- DVWA Installation
- SQL Injection
- Stored XSS
- Reflected XSS
- CSRF
- File Inclusion
- Burp Suite Interception
- Burp Suite Intruder
- Security Headers

---

# Conclusion

This task provided practical exposure to Web Application Security by performing controlled attacks on DVWA. The exercises demonstrated how common web vulnerabilities can compromise confidentiality, integrity, and availability when applications lack proper security controls. Each vulnerability was analyzed along with recommended mitigation techniques based on OWASP best practices. The knowledge gained from this task strengthens understanding of secure web development and ethical penetration testing methodologies.

---

# Disclaimer

This project was developed strictly for educational purposes inside a controlled laboratory environment using DVWA. No unauthorized systems or networks were targeted during this project.

---

# Author

Vadla Laxmi

B.Tech Student

ApexPlanet Cybersecurity Internship
