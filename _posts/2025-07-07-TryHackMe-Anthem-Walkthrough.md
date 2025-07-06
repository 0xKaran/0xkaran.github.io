---
categories: ['CTF', 'TryHackMe', 'Windows', 'Active Directory']
tags: ['CTF', 'TryHackMe', 'Windows', 'Active Directory', 'Anthem', 'THM']
title: 'TryHackMe Anthem Walkthrough'
---

### ✅ Disclaimer

Don’t use this write-up for quick and easy answers—instead, use it to develop your understanding. I’ve also explained my approach and mindset while solving the challenge. If you face any problem and have query you can connect with me, links are in the end.

Challenge URL: https://tryhackme.com/room/anthem

---

1. Ping was not working: `ping 10.10.194.170`
2. Used Nmap with -Pn to treat the host as online and identify services: `nmap -Pn 10.10.194.170`
    
    ```
    $ nmap -Pn 10.10.194.170
    Starting Nmap 7.95 ( https://nmap.org ) at 2025-07-05 15:57 IST
    Nmap scan report for 10.10.194.170
    Host is up (0.19s latency).
    Not shown: 998 filtered tcp ports (no-response)
    PORT     STATE SERVICE
    80/tcp   open  http
    3389/tcp open  ms-wbt-server
    
    Nmap done: 1 IP address (1 host up) scanned in 13.19 seconds
    ```
    

### ✅ Task 1: Website Analysis

**⏰ Question**: What port is for the web server?

💡 **Solution:** Identified using the Nmap scan.

🔑 **Answer**: `80`

**⏰ Question**: What port is for remote desktop service?

💡 **Solution:** Identified using the Nmap scan.

🔑 **Answer**: `3389` 

**⏰ Question**: What is a possible password in one of the pages web crawlers check for?

💡 **Solution:** A web crawler is a bot that automatically browses & indexes web pages for search engine. Web crawlers often check files like `sitemap.xml` and `robots.txt`. Upon inspecting `robots.txt`, a suspicious string was found, which appears to be a possible password.

![Screenshot 2025-07-06 at 22.32.01.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_22.32.01.png)

🔑 **Answer**: `UmbracoIsTheBest!`

**⏰ Question**: What CMS is the website using?

💡 **Solution:** Checked Wappalyzer and html codes but no clues found, but the name “Umbraco” appeared multiple times. Looked it up and turns out it’s a CMS.

![image.png](Anthem%2022783fa810768027b664df6f97f59669/image.png)

![Screenshot 2025-07-06 at 22.32.01.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_22.32.01%201.png)

![Screenshot 2025-07-06 at 22.38.08.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_22.38.08.png)

🔑 **Answer**: `Umbraco`

**⏰ Question**: What is the domain of the website?

💡 **Solution:** See website footer

![Screenshot 2025-07-06 at 22.39.51.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_22.39.51.png)

🔑 **Answer**: `Anthem.com`

**⏰ Question**: What's the name of the Administrator

💡 **Solution:** Tried checking author metadata and brute-forcing common files for user info, but didn’t find any useful results.

![Screenshot 2025-07-06 at 22.41.09.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_22.41.09.png)

But there is one blog post looked unusual, it contained a poem. A quick search revealed it’s a known rhyme called *Solomon Grundy*. Tried the name and confirmed it’s the website administrator.

![Screenshot 2025-07-06 at 22.45.10.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_22.45.10.png)

🔑 **Answer**: `Solomon Grundy`

**⏰ Question**: Can we find find the email address of the administrator?

💡 **Solution:** Since we found the admin name, let’s try to identify the company’s email pattern because it needs to be consistent for all employees.

For example, different companies would assign different formats for my email.

Employee Name: Karan Chaudhary

Emails: `Karan.Chaudhary@xyz.com`, `KC@xyz.com`, `Karan.C@xyz.com`

Since we already have an employee’s email, Jane Doe with the address `JD@anthem.com`, we can assume Solomon Grundy’s email would be `SG@anthem.com`.

![Screenshot 2025-07-06 at 22.53.24.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_22.53.24.png)

🔑 **Answer**: `SG@anthem.com`

### ✅ Task 2: Spot The Flags

Upon enumerating the website, like viewing the source code of different pages, we had already identified 2 out of 4 flags.

To find the remaining 2 flags, I went with a quick and low-effort method that saved me from manually checking each page.

I crawled all pages using the hakrawler tool, downloaded each page’s response using curl, and then used grep to extract the flag pattern `THM{`.

You can also use tools like GoSpider or Burp Suite and search through the history.

```bash
echo http://anthem.com | hakrawler -u | xargs -n1 -P10 curl -s -k | tee responses.txt | grep 'THM{'
```

![Screenshot 2025-07-06 at 23.02.06.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_23.02.06.png)

**⏰ Question:** What is flag 1?

🔑 **Answer:** `THM{L0L_WH0_US3S_M3T4}`

**⏰ Question:** What is flag 2?

🔑 **Answer:** `THM{G!T_G00D}`

**⏰ Question:** What is flag 3?

🔑 **Answer:** `THM{L0L_WH0_D15}`

**⏰ Question:** What is flag 4?

🔑 **Answer:** `THM{AN0TH3R_M3TA}`

### ✅ Task 3: Final Stage

**⏰ Question:** Gain initial access to the machine, what is the contents of user.txt?

💡 **Solution:** Using the credentials we gathered earlier, let’s try accessing the machine. Since we know the RDP service is running, we’ll use that.

**RDP Requirements:**

- Remote machine IP: x.x.x.x
- Username: Could be Solomon Grundy, Solomon, or SG
- Password: UmbracoIsTheBest! (found in robots.txt)

Choose your RDP client based on your OS. If you’re on Linux, use xfreerdp or rdesktop; for WSL inside Windows, use mstsc; on macOS, go with xfreerdp.

I’m using Kali Linux, so I’ll use xfreerdp with the following command:

```bash
xfreerdp3 /u:SG /p:UmbracoIsTheBest! /v:10.10.215.56 /cert:ignore
```

![Screenshot 2025-07-06 at 23.15.55.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_23.15.55.png)

🔑 **Answer:** `THM{N00T_NO0T}`

**⏰ Question:** Can we spot the admin password?

💡 **Solution:** Remember to always explore new system with hidden files visible, whether via GUI or command line.

![Screenshot 2025-07-06 at 23.18.35.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_23.18.35.png)

We don’t have permission to view admin files and folders, but we noticed a backup folder in the root directory.

Upon further enumeration, we found that while we can’t access the file inside the folder, the admin forgot to apply the same restrictive permissions on the **folder** itself, and we have edit access there.

![Screenshot 2025-07-06 at 23.19.44.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_23.19.44.png)

Let’s assign full control to ourselves, which in turn allows us to modify the permissions of child files as well.

![Screenshot 2025-07-06 at 21.30.12.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_21.30.12.png)

Then, change the permissions of `restore.txt` and read its contents.

Steps:

1. Right-click the folder > Properties
2. Go to the **Security** tab
3. Click **Edit** > **Add**, and enter the user or group to assign permissions, in our case, it’s SG
4. Type SG in the object name field and click **Check Names** to autocomplete
5. Assign **Full Control**, apply changes, then open `restore.txt`

The file contains the admin password.

![Screenshot 2025-07-06 at 23.26.50.png](Anthem%2022783fa810768027b664df6f97f59669/Screenshot_2025-07-06_at_23.26.50.png)

🔑 **Answer:** `ChangeMeBaby1MoreTime`

**⏰ Question:** Escalate your privileges to root, what is the contents of root.txt?

💡 **Solution:** Let’s try accessing `C:\Users\Administrator\Desktop` since CTF flags are commonly stored there. Use the admin password we just obtained to log in.

🔑 **Answer:** `THM{Y0U_4R3_1337}`

---

I hope you found this write-up helpful. Feel free to share it with your friends and explore other useful write-ups on this website.
If you have any doubts or want to connect, reach me out.

---

![profile preview.png](Anthem%2022783fa810768027b664df6f97f59669/profile_preview.png)

> **Thanks for reading**
> 

---

                                     [Porfolio](https://0xkaran.github.io/)  |  [LinkedIn](https://www.linkedin.com/in/0xkaran/)  |  [X/Twitter](https://x.com/0xkaran)  |  [Instagram](https://www.instagram.com/0xkaran_/)