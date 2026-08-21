# Networkwalks-B082-week2--Cybersecurity-Footprinting-and-Network-Scanning
Performing Footprinting and Network scanning on isolated VM and on Authorised Company 
# 🛡️ Cybersecurity: Footprinting and Reconnaissance

> **Program:** NetworkWalks Cyber Security Training & Internship  
> **Batch:** B082 — Week 2 | Project Module 1 (W2-PM1)  
> **Author:** Diksha ([@Diksha0665](https://github.com/Diksha0665))  
> **Target:** `networkwalks.com`  

---

## Legal and Ethical Notice
All activities, commands, and tests documented in this report were conducted strictly in a controlled, sandboxed lab environment for authorized training purposes. Unauthorized network scanning, port probing, or vulnerability assessment against systems without written permission is strictly prohibited under applicable cyber laws


## Liability Disclaimer
This report is published strictly for educational and research purposes[cite: 1]. The author and affiliated institutions assume no liability or responsibility for any misuse, damage, or legal consequences resulting from the application of the tools and methodologies demonstrated.

## 📋 Overview
Reconnaissance (footprinting) is the first step in any attack or security assessment. An attacker collects public information about a target—such as domain ownership, IP address, hosting provider, running software, DNS records, and firewalls—without the target knowing it is being studied. 

This project covers passive and active reconnaissance against the target `networkwalks.com` using six Kali Linux tools.

---

## 🛠️ Tools Used & Purpose

| Tool | Category | Purpose / Utility |
| :--- | :--- | :--- |
| **`whois`** | Passive Recon | Query public domain registration records, registrar details, and name servers. |
| **`whatweb`** | Technology Fingerprinting | Fingerprint web technologies: web server, CMS, plugins, frameworks, and IP address. |
| **`nslookup`** | DNS Resolution | Resolve the domain name to its direct IP address. |
| **`curl`** | Header Analysis | Read HTTP response headers to inspect server banners, cookies, and caching. |
| **`wafw00f`** | Firewall Detection | Detect whether a Web Application Firewall (WAF) is protecting the site. |
| **`dnsrecon`** | DNS Enumeration | Enumerate all DNS records (A, MX, SOA, TXT, SPF, and SRV records). |

---

## 📸 Lab Execution & Findings

### Task 1: Domain Registration Details (whois)
* **Command:**
  ```bash
  whois networkwalks.com
  ```
  ![whois](whois%20screenshots.png)

* **Extracted Findings & Technical Analysis:**
 * **Registrar:** GoDaddy.com
 * **LLC  Creation Date:** 2019-11-06
 * **Registry Expiry Date:** 2027-11-06
 * **Name Servers:** NS6135.HOSTGATOR.COM, NS6136.HOSTGATOR.COM
 * **Hosting Infrastructure:** HostGator infrastructure confirmed via authoritative DNS delegations

### Task 2: Web Technology Fingerprinting (`whatweb`)
* **Objective:** Identify underlying web application architecture, CMS components, libraries, and hosting indicators.
* **Command:**
  ```bash
  whatweb example.com
  ```
 ![whatweb](whatweb.png)

 #### Findings:
 * Target IP: 192.232.216.135 
 * Web Server: Apache
 * CMS & Plugins: WordPress 7.0.4, WordPress Download Manager 3.3.58 
 * Libraries & Frameworks: Bootstrap 7.0.4, jQuery 3.7.1, HTML5 
 * Email Contact: info@networkwalks.com

### Task 3: DNS Name Resolution (nslookup)
* Objective: Resolve domain name to its direct IP address via DNS lookup.
Command:
```bash
nslookup networkwalks.com
```

![Task 3 - NSLookup Output](nslookup.png)

#### Findings:
DNS Server Queried: 8.8.8.8#53 
Resolved IP Address: 192.232.216.135  

Task 4: HTTP Response Headers (curl)
Objective: Read the HTTP response headers to see the server banner, status, cookies, and redirects. 
Command:
```bash
curl -I [https://networkwalks.com](https://networkwalks.com)
```
![Task 3 - NSLookup Output](curl%20-I.png)

#### Findings:
HTTP Status: HTTP/2 200
Server: Apache  
Caching Layer: x-nginx-cache: WordPress, x-endurance-cache-level: 0  
REST API Discovered: WordPress API endpoint exposed at /wp-json/ 
Cookie Flags: Set-Cookie: __wpdm_client; HttpOnly; secure

Task 5: Web Application Firewall Detection (wafw00f)
Objective: Detect whether a Web Application Firewall (WAF) is protecting the target site. 
Command:
```bash
wafw00f networkwalks.com
```




