---
title: Let's Hunt for C2 Servers using Censys
date: 2024-09-17 00:00:00 +0800
categories: [Threat Intelligence]
author: Sojubear
image: "/public/censys.jpg"
---
⚠️ **This post is outdated. Censys has recently changed their query syntax from Censys Search Language(CSL) to the new Censys Query Langauge(CQL) for their new platform.**

# Introduction

I love Censys. It's exciting to look for the next big campaign, a new undocumented C2 server, or malware samples that haven't been documented before. If you manage to find an open directory hosted alongside a C2 server, then jackpot!

In a previous article, I explained how Censys can be used to look for open directories and some general hunting techniques. In this one, we'll look at queries to find some of the more common C2 Frameworks and how to share findings with the cybersecurity community.

## Basic Query Syntax
- **TLS Certificates:** `services.certificate:`
- **Subject CN:** `services.tls.certificates.leaf_data.subject_dn:`
- **Issuer CN:** `services.tls.certificates.leaf_data.issuer_dn:`
- **HTML Title:** `services.http.response.html_title:`
- **Banner Service:** `services.banner:`
- **Software Name:** `services.software.product:`

*Don't worry about saving all the syntax here, I've uploaded all the queries to GitHub in a link below.*

## Example C2 Framework Queries
- **Cobalt Strike:** `services.tls.certificates.leaf_data.issuer.common_name="Major Cobalt Strike"`
- **Mythic:** `services.http.response.html_title="Mythic"`
- **Metasploit:** `services.http.response.html_title: "Metasploit"`
- **Sliver:** `services.tls.certificates.leaf_data.subject_dn:"multiplayer"`
- **Havoc:** `services.banner: "X-Havoc"`
- **Viper:** `services.software.product: Viper`
- **Covenant:** `services.http.response.html_title="Covenant"`
- **SuperShell:** `services.http.response.html_title="Supershell — 登录"`
- **Brute Ratel C4:** `services.http.response.body_hash="sha1:1a279f5df4103743b823ec2a6a08436fdf63fe30"`
- **PenTera Red Team:** `services.http.response.html_title="Pentera™"`

## Sharing Your Findings with Abuse.ch
1. **Create an Account:** [ThreatFox](https://threatfox.abuse.ch/)
2. **Select Threat Type:** Choose botnet, malware family, etc.
3. **Select IOC Type:** IP, domain, URL, hash, etc.
4. **Enter Malware Name:** If applicable
5. **Provide IOC Details:** IP, port, etc.
6. **Add Additional Details:** (Optional)
7. **Submit:** Contribute to the community and earn credits

*On a side note, you get credits for uploading newly discovered C2 servers. These can be used to request specific IOCs you or your organization need.*

## Crafting Your Queries
Click on the "VIEW ALL DATA" icon in Censys to see more details about a particular software. This allows you to craft queries based on the signature, e.g.:
- `services.software.vendor:"Fortra"`
- `services.software.product:"Cobalt Strike"`

There are many ways to go about things, so experiment and see what works for you.

## Conclusion
We learned some of the different queries for popular C2 Frameworks and how to share findings with the cybersecurity community. I've uploaded more signatures I've collected in my [GitHub repo](https://github.com/thehappydinoa/awesome-censys-queries) (non-exhaustive). Please share your queries with me in the future!

## Additional Resources
- [Awesome Censys Queries](https://github.com/thehappydinoa/awesome-censys-queries)
- [C2IntelFeeds](https://github.com/drb-ra/C2IntelFeeds/tree/master)
- [Fox_threatintel on Twitter/X](https://x.com/banthisguy9349) *(inspiration for Censys hunting!)* 