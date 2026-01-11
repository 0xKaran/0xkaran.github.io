---
layout: post
title: "OSINT EP04: Master Person Info & Digital Identity"
categories: [OSINT, Cyber Security, Tutorials]
---

Welcome back to the OSINT series. In the previous episodes, we covered the fundamentals. Now, we dive deep into the most common target of Open Source Intelligence: **The Person.**

Tracking a digital footprint involves connecting three core pillars: **Social Media, Email, and Phone Numbers**. Here is how to gather, verify, and expand on personal information.

### 1. Social Media Discovery
*Find where they exist online.*

The easiest entry point is often a username. People tend to reuse handles across different platforms.

**Tools for Username Enumeration:**
* **[WhatsMyName.app](https://whatsmyname.app){:target="_blank"}:** The gold standard. Fast and supports hundreds of sites.
* **[InstantUsername](https://instantusername.com){:target="_blank"}:** Good alternative for quick checks.
* **[Blackbird (GitHub)](https://github.com/p1ngul1n0/blackbird){:target="_blank"}:** A powerful python tool that checks 700+ sites and often retrieves metadata.

**Search Operators:**
Don't forget manual dorks. For example, to find user comments or mentions:
`site:instagram.com "@user.name"`

**Demographic Analysis:**
If you only have a name or username, you can infer origin or gender:
* **[Namsor](https://namsor.app){:target="_blank"}:** Classify names by gender and country of origin.
* **[FamilySearch](https://www.familysearch.org/en/global){:target="_blank"}:** Great for historical records and family tree mapping.

---

### 2. Email Intelligence
*The key to the digital kingdom.*

#### Part A: Finding the Email
If the email isn't public, you have to hunt for it.
1.  **Professional Presence:** Check LinkedIn "Contact Info," YouTube Channel "About" sections, or GitHub bios.
2.  **GitHub Commit Logs:** Developers often leak personal emails in commit history.
    * `https://api.github.com/repos/<username>/<repo>/commits`
    * `https://braingainsoft.com/gh/index.html?q=<username>`
3.  **Pattern Guessing:**
    * Use **[Email Permutator](https://www.politepol.com/en/email-permutator/){:target="_blank"}** to generate likely combinations (e.g., `firstname.lastname@gmail.com`).
    * **Hunter.io:** Excellent for guessing corporate/business email formats.
    * **Search Dorks:** `"<name>" "@gmail.com" OR "@hotmail.com" OR "@yahoo.com"`

#### Part B: Gathering Intel from an Email
Once you have the address, what can you find?

* **Reputation Check:** Is it a real user or a bot? Use **[EmailRep.io](https://emailrep.io){:target="_blank"}**.
* **Registered Accounts:** Find which websites the email is signed up for.
    * **[Epieos](https://epieos.com){:target="_blank"}:** (Highly recommended) Checks Google account details, Maps reviews, and calendar.
    * **[OSINT.industries](https://app.osint.industries){:target="_blank"}**
    * **[Castrick Clues](https://castrickclues.com){:target="_blank"}**
* **Google ID (Gaia) & Maps:**
    * Tools like **GHunt** (Linux/Python) or [Gmail OSINT](https://gmail-osint.activetk.jp){:target="_blank"} can extract the Gaia ID.
    * Use the ID to find map reviews: `https://www.google.com/maps/contrib/<Gaia ID>`. This reveals physical locations visited.
* **Breach Data:** Check if the email appears in leaked databases (e.g., HaveIBeenPwned or dehashed alternatives). This often leads to passwords, which leads to... patterns.

#### Part C: Verification Tricks
* **The "Forgot Password" Method:** Enter the target email on sites like Facebook or Twitter. It may partially reveal a phone number (e.g., `+1 ***-***-9921`) or a recovery email.
* **The "Compose Email" Method:** Type the address into Gmail/Outlook compose box. Hover over the profile to see if a profile picture or full name populates.

---

### 3. Phone Number Intelligence
*Connecting the physical to the digital.*

#### Part A: Finding the Number
* **Resume/CVs:** Often indexed by Google. Search `filetype:pdf "name" "resume" "phone"`.
* **LinkedIn Extensions:** SignalHire, ContactOut, or Easyleadz.
* **Search Operators:**
    * US: `"XXX-XXX-XXXX" OR "XXX.XXX.XXXX"`
    * International: `"+91XXXXXXXXXX" OR "0091XXXXXXXXXX"`

#### Part B: Gathering Intel from a Number
* **Validation:** Use **[IPQualityScore](https://www.ipqualityscore.com/free-phone-number-lookup){:target="_blank"}** to identify if it is VoIP, Landline, or Cellular.
* **Caller ID Databases:**
    * **Truecaller:** The massive global database.
    * **Sync.me:** Often syncs with social media photos.
* **Financial Apps (UPI):** In regions like India, try sending a negligible amount (via GPay/PhonePe) to the number. The banking confirmation screen will often reveal the target's **Full Legal Name**.
* **Social Lookups:**
    * Check **[HaveIBeenZuckered](https://haveibeenzuckered.com){:target="_blank"}** to see if the number was in the massive 2019 Facebook leak.
    * Use **[PhoneInfoga](https://github.com/sundowndev/phoneinfoga){:target="_blank"}** for automated scanning.

---

### 4. Government & Regional Records (Context Specific)
*When digital fails, look for official records.*

Depending on your target region (specifically India/South Asia), public records can be a goldmine:
* **Voter Rolls:** Often public and searchable by name/constituency.
* **Court/Police Records:** Check e-court services for litigation history.
* **Ration Cards/Medical Certificates:** In some states, beneficiary lists for government schemes are publicly indexed.

> **Note:** Always respect privacy laws and ethical boundaries when accessing government data.