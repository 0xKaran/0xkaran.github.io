---
title: "EP03: Modern OSINT Techniques – Leaked Credentials & Personal Data Investigation"
categories: ['OSINT']
tags: ['OSINT', 'Data Breach', 'Leaks']
description: OSINT tutorial on understanding, locating, and analyzing leaked personal data from public and underground breach sources.
---
----

#### ✅ What is a Data Breach / Data Leak

A **data breach or data leak** refers to any incident where sensitive or private information is accessed, exposed, stolen, or publicly distributed without authorization.  
Breaches usually occur through hacking or malware, while leaks often happen due to misconfiguration or human error.

Leaked databases can contain one or more of the following:

- **Account credentials** – emails, usernames, passwords  
- **Contact data** – phone numbers, email IDs  
- **Government identifiers** – SSN, Aadhaar, Passport numbers  
- **Financial records** – debit/credit card details, bank data  
- **Personal profiles** – addresses, date of birth  
- **Health information** – medical history, prescriptions  
- **Technical data** – IP logs, device fingerprints  
- **Corporate secrets** – internal documents, source code, API keys  

---

#### 🐝 Types of Leaks

| Type | Meaning |
|----|-------|
| **Breach** | Data stolen directly through hacking activity |
| **Leak** | Accidental public exposure due to misconfiguration |
| **Dump** | Public release of stolen or leaked data |
| **Combo List** | Compiled email:password credential lists |
| **Paste** | Small, partial data samples posted publicly |
| **Scrape** | Mass data collected using APIs or automation |
| **Insider Leak** | Data exposed intentionally or accidentally by employees |

---

#### ☢️ How Data Leaks Happen

- Exposed databases (MongoDB, Elastic, Firebase)
- SQL Injection (SQLi) and Remote Code Execution (RCE)
- Third-party service provider compromise
- Open cloud storage (e.g., public S3 buckets)
- Phishing emails and malware infections

---

#### 𒎓 Famous Breaches in History

| Leak | Year | Records | Data |
|----|----|-------|-----|
| Collection #1 | 2019 | 773M | Emails, passwords |
| Collection #2–5 | 2019 | 845M | Emails, passwords, IPs |
| Facebook | 2019 | 533M | Phones, names, locations |
| Yahoo | 2013–14 | 3B | Emails, passwords |
| LinkedIn | 2012/16 | 700M | Emails, hashed passwords |
| MySpace | 2013 | 360M | Emails, hashed passwords |
| Adobe | 2013 | 153M | Encrypted passwords |
| Equifax | 2017 | 147M | SSN, DOB |
| RockYou | 2009 | 32M | Plaintext passwords |
| Canva | 2019 | 137M | Emails, passwords |
| Twitter | 2022 | 235M | Emails, phones |
| Aadhaar (India) | 2018 | 1.1B | Aadhaar, addresses |
| Marriott | 2018 | 500M | Passport & travel data |
| Experian SA | 2020 | 24M | ID & employment |
| Dropbox | 2012 | 68M | Emails, hashed passwords |

---

#### Legal & Ethical Warning
Using leaked data to access private accounts or systems is illegal.  
Law-enforcement agencies has hundreds of ways to track you if caught in serious case.

---

#### 🔎 Where Leaked Data Is Found

Leaked databases are distributed on:

- Telegram leak channels  
- Dark-web forums  
- GitHub repositories and paste sites  
- Breach marketplaces / search engines

**Known search engines**
- <a href="https://haveibeenpwned.com" target="_blank" rel="noopener noreferrer">HaveIBeenPwned</a> 
- <a href="https://dehashed.com" target="_blank" rel="noopener noreferrer">Dehashed</a> 
- <a href="https://intelx.io" target="_blank" rel="noopener noreferrer">IntelligenceX</a>
- <a href="https://leakpeek.com" target="_blank" rel="noopener noreferrer">LeakPeak</a>
- <a href="https://snusbase.com" target="_blank" rel="noopener noreferrer">Snusbase</a>

Cloud hosted search engines are efficient but costly, you can also download the databases locally for forever with below requirements but remember leaked databases often contain malware. They should be opened only in isolated environments (VMware / VirtualBox).

- High disk space
- Torrent client
- Agent Ransack (for searching inside large dumps)

**Known public database indexes**
- <a href="https://sizeof.cat/post/data-leaks" target="_blank" rel="noopener noreferrer">sizeof.cat</a>
- <a href="https://cracking.org/forums/databases.31" target="_blank" rel="noopener noreferrer">cracking.org</a>
- <a href="https://breachforums.st/Announcement-Database-Index" target="_blank" rel="noopener noreferrer">breachforums</a>
- <a href="https://darkforums.st" target="_blank" rel="noopener noreferrer">darkforums</a>
- <a href="https://www.chiaselinks.com/public/nl0mqtgegm" target="_blank" rel="noopener noreferrer">chiaselinks</a>
- <a href="https://leakbase.la" target="_blank" rel="noopener noreferrer">leakbase</a>
- <a href="https://altenens.is" target="_blank" rel="noopener noreferrer">altenens</a>

If these indexes does not work, you can also search on google by including `magnet:?` in search term to find torrent files. examples:

- `"twitter 200m" "magnet:?"`
- `facebook data leak "magnet:?" github`

---

#### 🦺 Initial Recon Workflow

1. Start with **HaveIBeenPwned** or **Leakpeak** or  **Dehashed** to check if the target data exists in breaches.
2. Identify which databases contain relevant information.
3. Download only necessary dumps for deeper investigation.
