---
categories: ['HackTheBox']
tags: ['HackTheBox', 'HTB', 'CTF']
title: 'HackTheBox - CCTV Walkthrough (Easy) | Full Solution'
description:  Guide to compromising the HTB CCTV (Easy) machine covering initial access, exploitation, and privilege escalation with key commands and a red-team methodology.
---

<img src="/assets/images/post/htb/cctv/1.png" alt="hackthebox cctv article by 0xKaran" style="display:block;margin:auto;width:70%;">

### Table Of Contents
- Summary
- Recon
- Initial Access
- User Access
- Privilege Escalation

> CCTV is easy rated Linux machine on HackTheBox that demonstrates critical vulnerabilities in outdated
{: .prompt-info }

### Recon
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


```bash
sudo echo 10.129.174.233 >> /etc/hosts
```