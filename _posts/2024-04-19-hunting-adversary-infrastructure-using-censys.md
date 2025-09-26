---
title: "Hunting Adversary Infrastructure using Censys"
date: 2024-07-20 00:00:00 +0800
categories: [Threat Intelligence]
author: Sojubear
image: "/public/censys.jpg"
---

⚠️ **This post is outdated. Censys has recently changed their query syntax from Censys Search Language(CSL) to the new Censys Query Langauge(CQL) for their new platform.**

# Hunting Adversary Infrastructure using Censys

## Introduction

Today I want to share my experience using Censys to hunt for Adversary Infrastructure and Open Directories hosting malicious binaries.

I'll demonstrate how I use this tool to discover command and control (C2) servers and staging servers. I'll also show you how I find open directories that often contain malicious files.

## What is Adversary Infrastructure?

Adversary infrastructure refers to the systems, servers, and domains used by threat actors to carry out malicious activities. This infrastructure can include C2 servers, phishing sites, malware distribution networks, and more. It can include:

- **C2 Servers**: These servers are used by attackers to communicate with and control compromised devices. They send commands, receive stolen data, and often facilitate further attacks.
- **Phishing Domains**: Domains designed to replicate legitimate websites with the intent to deceive users into disclosing sensitive information, such as login credentials or financial details.
- **Malware Distribution Sites**: Websites or servers that host and distribute malicious software, often to infect systems or networks.
- **Bulletproof Hosting**: Hosting services that offer protection and anonymity to cybercriminals. These services are often used to host malicious content while providing minimal cooperation with law enforcement, making it challenging for attribution.

## Introduction to Censys

According to the main website, Censys is a platform that helps information security practitioners discover, monitor, and analyze devices that are accessible from the Internet. If you are familiar with Shodan and FOFA.IO, it works similar.

It's basically a search engine to find devices that are connected to the internet. It provides many details such as a host's operating system, open ports and running services.

One of the cool things about Censys is that it is totally free to use (Although the paid subscription come with certain perks) and you do not even need to sign up to start using it, although you only get 10 searches a day.

## Hunting Techniques

### Identifying Known Malicious IP Addresses

The barrier for entry is really low when it comes to hunting for evil. Censys makes it super easy to get started by providing labels for various types of malicious activity. One of my most used labels is:

```
labels:"c2"
```

which identifies a lot of the more popular C2 servers such as Cobalt Strike, Viper and Sliver.

By simply searching for this label, you can quickly pull up a list of IP addresses that have been flagged as C2 servers. This is helpful as they are a critical part of many cyber attacks — they're used by attackers to communicate with and control compromised systems. Once you've identified these servers, you can dig deeper to understand the infrastructure and potentially uncover more malicious activity.

From the above image, we can see that Censys has labeled 2,311 hosts as potential C2 servers. By scrolling through the filters on the left, we can observe that multiple C2 servers have been indexed by Censys. However, it's important to note that not all of these servers are guaranteed to be fully indexed. I suspect that more sophisticated threat actors will employ techniques to obfuscate their services, making it harder for them to be identified as C2 servers on Censys.

Now, let's take a closer look at the software Cobalt Strike, popular with both security professionals and threat actors. When examining the TLS certificates, we can see that the Certificate Subject and Issuer explicitly states the name of the software being run:

```
services.tls.certificates.leaf_data.issuer.common_name="Major Cobalt Strike"
```

Alternatively, you can search for instances of Cobalt Strike by looking for:

```
services.software.product=`Cobalt Strike`
```

Using these queries, we can pinpoint servers running Cobalt Strike, providing an indicator of potential malicious activity. Keep in mind, there are multiple ways to refine these queries to filter out results and focus on specific aspects of Cobalt Strike activity, which can further aid in uncovering malicious infrastructure.

### Leveraging Certificates for Infrastructure Identification

Besides looking at the software, we can also start looking at TLS certificates to uncover adversary infrastructure. TLS certificates are often used to secure communication between servers and clients, but they also leave behind valuable clues that can be used for attribution.

```
services.certificate:"<certificate_fingerprint>"
```

Attackers may sometimes reuse the same certificates across multiple malicious domains and IP addresses. By analyzing these certificates, we can identify connections that might otherwise go unnoticed.

### Searching for Open Directories

While it might not involve directly hunting for malicious actors, finding open directories can sometimes reveal where threat actors might host their staging servers or distribute malware without tying it back to their C2 servers. Censys has also made it very easy to search for them.

```
labels:"open-dir"
```

OR if you prefer not using labels:

```
services.http.response.html_title:"Index Of" or services.http.response.html_title:"Directory Listing"
```

One of the open directories I came across, they were filled with binaries linked to the Sliver C2 Framework.

This was interesting, I found someone hosting the actual Cobalt Strike software.

Be advised though, there are A LOT of hosts with open directories — 425k as of this writing. Going through them one by one can be a real pain without finding anything of significance. To make searches more efficient, you can extend your search terms to make it more targeted.

Here are a few search queries I use to narrow down the results:

```
labels:"open-dir" and services.http.response.body:"exploit"
labels:"open-dir" and services.http.response.body:"payload"
labels:"open-dir" and services.http.response.body:".exe"
```

However, I am certain that this isn't the best way to go about searching for malware, and I am still refining my methods. I'll keep you guys updated when I come up with something better.

> **CAUTION**: Downloading files from open directories comes with risks. If you decide to do so, always use a safe and contained environment, such as a sandbox or isolated virtual machine to avoid any harm to your system. Additionally, make sure to use a VPN to protect your real IP address from being logged by the threat actor. OPSEC is a whole other rabbit hole that I will not get into today. But treat each of them as hostile environments.

Upon finding a valid open directory that I suspect is malicious, I usually run these commands.

First, to recursively download every file from the directory, use:

```bash
wget --recursive --no-check-certificate <ip_address>
```

Next, to get the sha256sum on every file in your current folder, use:

```bash
find . -type f -exec sha256sum {} \;
```

Running these commands allows me to download and hash all the files quickly. By comparing the hashes, I can perform a quick triage to understand what the malware might do and identify any known malicious files.

## Leveraging VirusTotal

Not everyone is a malware analyst, and not everyone has the time to open IDA and go through each binary one by one. To save time and effort, I often rely on VirusTotal (VT) to analyze the hashes of files I've found.

VirusTotal is an online service that takes the results from multiple antivirus engines to help determine whether a file is malicious. By submitting the hashes of the files, I can easily understand what the malware does based on the analysis from multiple security vendors.

Found an open directory that was hosting an AsycRAT server.

VT results for 64.exe

Here's how I typically use VirusTotal in my workflow:

1. **Submit Hashes**: After running the sha256sum command on the downloaded files, I take the list of hashes and submit them to VirusTotal.
2. **Analyze Results**: VirusTotal provides a detailed report on each hash, including detections from various antivirus engines, behavior analysis, and any associated network activity.
3. **Determine Maliciousness**: Based on the aggregated results, I can get a good sense of what each file does and how harmful it might be without needing to manually reverse-engineer each binary.

I don't usually go into too deep into the individual binaries unless I'm looking to practice or if the context demands a more thorough investigation. For me, the primary goal is to quickly validate whether an IP address is associated with malicious activity.

## Collaboration and Information Sharing

I usually post my findings on Twitter and on ThreatFox. These two platforms are fantastic for sharing insights and learning from others who are also investigating adversary infrastructure.

- **Twitter**: Twitter has been my main platform because I get to see other researchers share their findings, techniques, and tools. By posting my discoveries and following others, I usually get feedback on my research and correlation to other activities they have discovered. I also try to emulate their techniques and refine my own.

- **ThreatFox**: ThreatFox is another excellent platform for sharing IOCS. It helps build a more comprehensive and up-to-date database that benefits the entire cybersecurity community.

## Final Thoughts

That's it! I've covered various methods for hunting adversary infrastructure, including how to use Censys to identify C2 servers and open directories, and how to leverage tools like VirusTotal to analyze files. One final thing, don't be afraid to just jump in and run the Censys queries that I posted earlier. I started by exploring and learning what Censys can do and then researched topics I didn't fully understand. Build your own database of query syntax and unique signatures from different C2 frameworks.

I'll definitely revisit this topic in the future and dive even deeper, so stay tuned! 