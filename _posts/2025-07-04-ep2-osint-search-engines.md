---
categories: ['OSINT']
tags: ['OSINT']
title: 'EP02: Modern OSINT Techniques – Search Engines'
description: OSINT tutorial to use search engines and advanced search operators to find publicly exposed people data, company assets, documents, infrastructure, and forgotten digital footprints, and how to systematically gather useful intelligence from information already indexed on the internet.
---
----
#### 🏁 Starting Point
Primary reconnaissance starts with search engines:
- Google
- Bing
- Yahoo
- Yandex
- DuckDuckGo
- Baidu

Use advanced operators to filter noise and surface only relevant intelligence.

---

## Google

#### ⛺️ Basic Identity Hunting Using Google Dorks
- `"Amit Raj"` - Exact match
- `"Amit Raj" "Banglore" "Jio" "LinkedIn"` - Narrow search results
- `inurl:<username>` - Urls contaning usernames
- `inurl:<unique_PII>` - Target specific like phone, interest, college etc.
- `<username1> OR <username2>`
- `intitle:amit.raj` - Dot means space
- `"Amit * Raj"` - * finds missing info like middle name
- `Amit Raj -"Bharti Airtel" -site:linkedin.com` - Exclude irrelevant results
- `site:xyz.com "Amit Raj"` - Info on specific website
- `site:<portfolio.target> filetype:pdf` - PDF files from a website
- `site:instagram.com @user.name` - User comments

#### 📂 Multi-Filetype Intelligence Search
Use wide filetype combinations to locate leaked, archived, or sensitive documents:

- Search by username
- Search by keyword
- Search within a specific domain
- <a href="https://developers.google.com/search/docs/crawling-indexing/indexable-file-types" target="_blank" rel="noopener noreferrer">File types indexable by Google</a>

(Use the provided multi-filetype OR chains)

#### 💿 Useful Databases
- <a href="https://www.exploit-db.com/google-hacking-database" target="_blank" rel="noopener noreferrer">Google Hacking Database</a>
- <a href="https://www.dorkgpt.com" target="_blank" rel="noopener noreferrer">DorkGPT - Generate dorks using AI</a>

#### 🤓 Get More Face Results
If your google search result shows target person face, you can search for more face results
Process:
1. Open Images tab.
2. Tools → Type → Select **clipart**.
3. Replace `clipart` with `face` in the URL.

Purpose: Discover profiles, forums, and other platforms where the same face appears.

We'll learn more about this in upcoming episodes.

---

## Bing
Expand search results by using different search engines, most of the Google search operators works here.
- <a href="https://seosly.com/blog/bing-search-operators" target="_blank" rel="noopener noreferrer">Bing Search Operators</a>
- `linkfromdomain:domain.com` → External references and hosted resources
- `ip:x.x.x.x` → Identify co-hosted domains

---

## Yahoo
- Yahoo is another very good alternative of Google & Bing and it is older than Google.
- <a href="https://search.yahoo.com//web/advanced" target="_blank" rel="noopener noreferrer">Yahoo Advanced Search</a>

---

## Yandex
Yandex supports most Google-style operators but it is mainly used to do face and location searches and it is actually good in it. Google image search does not allow you to search human faces but Yandex does.

<b>Date Operators</b>
- `date:2023` (Year)
- `date:202301` (Year\|Month)
- `date:20230101` (Year\|Month\|Day)
- `date:2023..2022` (Range)
- `date:>2022` (After x year)

---

## Other Useful Search Engines

<b>Baidu</b>
- Primary search engine for China-related targets.
- Useful for Chinese individuals, companies, and organizations.

<b>DuckDuckGo</b>
- Supports Google operators.
- Used to expand and diversify result sets.

---

#### 💾 Caching & Archived Data
If you find a result but upon opening it says `404` or redirects to another location, view cache!

Google, Bing, Yahoo, Yandex, try different SEs if you don't find on one. There will be 3 dots in the corner of the url.

Or you can use <a href="https://web.archive.org" target="_blank" rel="noopener noreferrer">Web Archive</a>

---

#### ✋ One Stop Solution
Use <a href="https://inteltechniques.com/tools/Search.html" target="_blank" rel="noopener noreferrer">Intel Techniques</a> to search across all search engines.

----

#### 📒 Final Notes
- View metadata of each discovered file (images, videos, and documents), this can reveal geolocation, device information, software and its version this can lead to uncover other or fake names which target might be using or vulnerable softwares which an investigator can exploit.
- Combine all PII to get different results like Universities, Schools, Family members, Events, Projects.
- Rotate search engines to bypass result bias and censorship.
- Use disposable browsers (SquareX) or VPN when GDPR or geo-filters limit results.