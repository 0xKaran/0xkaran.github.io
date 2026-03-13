---
categories: ['HackTheBox']
tags: ['HackTheBox', 'HTB', 'CTF']
title: 'HackTheBox - CCTV Walkthrough (Easy) | Full Solution'
description:  Guide to compromising the HTB CCTV (Easy) machine covering initial access, exploitation, and privilege escalation with key commands and a red-team methodology.
---

<img src="/assets/images/post/htb/cctv/1.png" alt="hackthebox cctv article by 0xKaran" style="display:block;margin:auto;width:70%;">

## 0. Table Of Contents
1. Summary
2. Recon
3. Initial Access
4. User Access
5. Privilege Escalation To Root Access

## 1. Summary
CCTV is an easy-rated Linux machine on HackTheBox that showcases critical flaws in outdated CCTV management softwares.
Initial access is gained by exploiting an SQL injection to dump password hashes, followed by privilege escalation through an RCE CVE in another identified service to obtain a root shell.

## 2. Recon
```bash
┌──(karan㉿kali)-[~/Desktop/htb/cctv]
└─$ nmap -A -oN nmap.txt 10.129.174.233

# Nmap 7.95 scan initiated Mon Mar  9 12:56:55 2026 as: /usr/lib/nmap/nmap --privileged -A -oN nmap.txt 10.129.174.233
Nmap scan report for 10.129.174.233
Host is up (0.091s latency).
Not shown: 998 closed tcp ports (reset)

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 9.6p1 Ubuntu 3ubuntu13.14 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|_  256 76:1d:73:98:fa:05:f7:0b:04:c2:3b:c4:7d:e6:db:4a (ECDSA)

80/tcp open  http    Apache httpd 2.4.58
|_http-title: Did not follow redirect to http://cctv.htb/

Device type: general purpose|router
Running: Linux 4.X|5.X, MikroTik RouterOS 7.X
OS CPE: cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel:5 cpe:/o:mikrotik:routeros:7 cpe:/o:linux:linux_kernel:5.6.3
OS details: Linux 4.15 - 5.19, MikroTik RouterOS 7.2 - 7.5 (Linux 5.6.3)
Network Distance: 2 hops
Service Info: Host: default; OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

To access the website on browser, add `cctv.htb` in hosts file

```bash
sudo nano /etc/hosts
10.129.174.233  cctv.htb
```

> <b>Active HackTheBox Challenge</b><br><br>
This challenge is currently active on HackTheBox. As per [HTB’s content policy](https://help.hackthebox.com/en/articles/5188925-streaming-writeups-walkthrough-guidelines){:target="_blank"}, writeups for active machines are not allowed.
This writeup will be published publicly once the machine is retired.<br><br>
💡 For hints or guidance, you can reach out to me on any social media profiles.
{: .prompt-danger }