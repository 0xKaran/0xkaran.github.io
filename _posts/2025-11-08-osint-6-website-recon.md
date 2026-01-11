---
layout: post
title: "OSINT EP06: Investigating Websites"
categories: [OSINT, Tech, Web Analysis]
---

Sometimes your target isn't a person, but a website. Whether you are investigating a scam site, a competitor, or just curious about who owns a domain, Website OSINT is the way to go.

### 1. WHOIS Records
*The Birth Certificate of a Website.*

A WHOIS record reveals the registered owner, creation date, and registrar of a domain.
* **[Who.is](https://who.is){:target="_blank"}:** Clean and simple interface.
* **What to look for:**
    * **Registrant Email:** Did they forget to turn on Privacy Protection?
    * **Registration Date:** Is this "official bank" website only 3 days old? (Huge red flag).

### 2. DNS & Infrastructure Analysis
*Mapping the network.*

* **[DNSlytics](https://dnslytics.com){:target="_blank"}:** A powerful search engine for DNS.
    * **Reverse Analytics:** If you find an AdSense ID or Google Analytics ID in the website source code, you can search it here to see *what other websites* the same person owns.
    * **Wildcard Search:** `name: *netflix*` to find phishing domains trying to look like the real thing.

### 3. Finding Related Assets
If you find one email address or one server IP, you can pivot to find the whole network.

* **Reverse Whois:**
    * **[ReverseWhois.io](https://www.reversewhois.io){:target="_blank"}:** Enter an email address (e.g., `admin@bad-guy.com`) to find every other domain registered by that email.
* **Shared Hosting:**
    * Use **[ViewDNS.info](https://viewdns.info){:target="_blank"}** to see which other websites are hosted on the same IP address. This helps identify server neighbors.

### 4. The Toolbox
Don't reinvent the wheel. Use aggregated toolkits for website reconnaissance:
* **[OSINT.sh](https://osint.sh){:target="_blank"}:** A curated collection of web monitors and DNS tools.
* **[UrlScan.io](https://urlscan.io){:target="_blank"}:** Safely browse and screenshot a website without actually visiting it (great for analyzing malicious links).

---

*This concludes our mini-series on OSINT techniques. Remember, the tools change, but the methodology—Critical Thinking—remains the same. Happy hunting!*