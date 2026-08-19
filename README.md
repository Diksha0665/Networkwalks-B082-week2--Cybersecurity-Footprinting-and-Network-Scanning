# Networkwalks-B082-week2--Cybersecurity-Footprinting-and-Network-Scanning
Performing Footprinting and Network scanning on isolated VM and on Authorised Company 
# 🛡️ Cybersecurity: Footprinting and Reconnaissance

> **Program:** NetworkWalks Cyber Security Training & Internship  
> **Batch:** B082 — Week 2 | Project Module 1 (W2-PM1)  
> **Author:** Diksha ([@Diksha0665](https://github.com/Diksha0665))  
> **Target:** `networkwalks.com`  

---

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
