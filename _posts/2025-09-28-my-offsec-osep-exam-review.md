---
title: My OSEP Exam Review
description: A Journey Through Study Burnout and Wonky VPNs
date: 2025-09-27 00:00:00 +0800
categories: [Course Review]
tags: [osep, offsec, exam] 
image: "/public/Course-PEN-300.png"
---

I was lucky enough to have my company sponsor my attendance at a live WEB-300 training at BlackHat USA 2025, which also came with access to OffSec's Learn Unlimited. The logical next step would have been to work on the OSWE. But after talking to a few people who’d been through it, the picture they painted was one of staring at thousands of lines of PHP code. My soul withered, and so, I respectfully pivoted.

That’s how I landed on OSEP.

![BlackHat Banner](/public/osep_blackhat.jpeg)
*4 days of source code madness*

### What is the PEN-300? You mean the OSCP doesn't make me a 1337 h4ck3r?

According to OffSec's [website](https://www.offsec.com/courses/pen-300/):

> PEN-300 is OffSec’s advanced penetration testing course, focused on evading defenses, developing custom techniques, and preparing for the OSEP exam. Learners engage with hands-on, live machines to exploit using customized tools and countermeasures, building advanced skills in ethical hacking.

In practical terms, it picks up right where the PEN-200 leaves off. The curriculum is focused on defense evasion in a relatively modern environment. You’ll get deep into topics like:

- **AV/EDR Evasion:** Moving beyond basic meterpreter exe payloads to custom process injection, hollowing, and shellcode loaders
- **In-Memory Execution:** Leveraging reflective PowerShell and DLLs to operate in memory
- **Endpoint Control Bypasses:** Navigating a gauntlet of modern controls like AppLocker, Constrained Language Mode (CLM), and the Antimalware Scan Interface (AMSI)
- **Advanced AD Attacks:** ADCS and Delegation attacks

I would highly recommend that you have basic level knowledge of Pentesting before you attempt this course or exam, something along the lines of OSCP-level knowledge. The course goes deep on a lot of topics that you might have trouble following without prior experience. You should be comfortable with your enumeration and privilege escalation workflows and already know how to use tools like Impacket and NetExec.

### What I Loved: The Realism

PEN-300 forces you to confront a reality many courses ignore: modern defenses are _on by default_. You’re not attacking boxes where Defender has been conveniently disabled. You’re actively fighting against AMSI, CLM, and AppLocker. It forces a mindset shift away from just throwing `shell1.exe, shell2.exe, shell3.exe` at a target and hoping for a callback. You have to consider your payload's signature, its behavior, and its delivery mechanism before you even think about executing.

The phishing modules were also excellent, covering everything from standard VBA macros to clever vectors like calendar invites and Jscript execution.

And yes, there is **a lot** of C# and PowerShell. While it felt like a grind, I came to appreciate how the course makes you build your own tooling which allows you to understand the underlying functionality of them. A lot of times we are using prepackaged ones without realizing what happens under the hood.

### A Minor Gripe: The Pacing

I did feel the materials could be a bit dry and long-winded. Some modules felt like they took too much time to get to the important parts. This might just be my learning style, but it’s something to be aware of if you prefer a faster pace.

But other than that, I felt like the course was relatively well written and i could (eventually) understand the concepts that they were teaching

### My Exam Prep (Or Lack Thereof)

I’d read in multiple reviews that proficiency with a good C2 framework is non-negotiable. This gave me a good opportunity to finally learn the Sliver C2 Framework, although a friend did recommend something more _Mythical_.

These were some of the resources that I used:

- Hack The Box's [Intro to C2 Operations with Sliver](https://academy.hackthebox.com/module/details/241)
- This incredibly useful [Sliver Cheatsheet](https://github.com/Anon-Exploiter/sliver-cheatsheet)
- Bishop Fox's blogpost: ["Passing the OSEP exam using Sliver"](https://bishopfox.com/blog/passing-the-osep-exam-using-sliver)

I don't recall using a lot of other external resources in preparation for the exam, the course does its job well in teaching you what to look out for. What I did however, was to properly prepare the scripts that I needed for the exam (which were properly covered in the course). And also to understand the different commands of how Sliver worked. I actually felt like I spent more time playing around with Sliver than on preparing for the exam.

⚠️ **Full disclosure:** I was hitting a serious wall with burnout. Staring at C# for weeks will do that. I skipped a chunk of the labs and only completed the first Challenge Lab. In hindsight, slowing down would have saved me a lot of pain.

That "serious wall" isn't just a figure of speech. I came to a grinding halt and the initial excitement was replaced by a certain level of dread. The materials eventually started to blur into an incomprehensible wall of text. It's a frustrating cycle: you know you need to be in the labs building muscle memory, but your brain actively resists. You avoid the work because you're exhausted, which only makes you feel guilty and unprepared.

![OSEP Course Progress](/public/osep_course_progress.png)
*Sometimes, the "Try Harder" mentality leads you straight into a wall.*

So, after about a month and a half into my course materials, I decided to book the exam. I told myself it would be a low-pressure 'recon run' to just get a feel of how the environment exam was like. But it quickly turned into a try-hard session when my ego took over.
### The Exam Gauntlet : I've never felt so much pain in my life

The exam started brutally. I had random disconnects and very spotty connections during my first 6 hours. I wasted time assuming my methodology was flawed before support confirmed a wonky VPN connection. 

Then came a real hard `#%$#$` blocker. I had tried all the enumeration vectors from the course but was unable to progress. 30 hours in, I was panicking and started lobbing random enumeration queries, hoping for a Hail Mary. As if on cue, a separate, wonky machine forced me to revert the entire exam environment. After the reset, I went back and tried one of my earliest queries, one of the very first I had attempted. And I instantly found my attack vector. Honestly, I did not know if I should be angry or relieved.

After that breakthrough, every box fell easily, and I secured slightly more than enough flags to pass. Unfortunately, the time lost to the VPN and the finicky box meant the `secrets.txt` was out of reach. With 10 hours left, I was too mentally drained to push further.

Oh, did I mention? BloodHound CE broke on me too, forcing me to fall back to good old PowerView.

My take? The exam is challenging but an extremely fair assessment. Aside from the unstable machines, the difficulty didn't come from rabbit holes. Instead, the challenge is in how you understand and apply the course materials under pressure. Every single vector and technique was mostly covered in the PEN-300 course, with a healthy amount of fundamentals from the PEN-200. Unlike the OSCP, I had no need to look for other materials during the course of the exam, just the original PEN-300 ones and my Sliver Cheatsheet.

### My Advice for Taking the OSEP

1. **Master a Modern C2.** The course focuses on Metasploit, but for OPSEC-aware engagements, you need more. Learn Sliver, Mythic, or something comparable. Understand its payload generation, its traffic profiles, and its post-exploitation capabilities intimately.
2. **Threat Model the Course Syllabus and Exam Reviews.** Read the syllabus and check out other user reviews. Understand the hidden meaning behind their words and you'll get a feel for which topics are more critical than others. But don't ignore the rest; every topic is fair game.
3. **When in Doubt, Revert.** I cannot stress this enough. Don't be afraid to revert a machine if you're stuck. Sometimes things just break, and a fresh start can magically reveal the path forward.
4. **It's a Marathon, Not a Sprint.** 48 hours is a long time. The exam isn’t designed to send you down rabbit holes. If a vector feels too complicated, it usually is the wrong one. Take breaks, manage your mental state, and trust your methodology.

### Conclusion: Is OSEP Worth It?

So, after the burnout and battling a demonic VPN, was the OSEP worth it?

Absolutely.

There were countless moments of frustration where I found myself asking, "Why am I spending hours trying to understand and write a C# tool when a one-liner from my C2/insert-popular-tool-here could do the same thing?" But I reckon that the painful process is precisely the point. The PEN-300 changes your approach to offensive operations and push you out of your comfort zone(for those who do not understand C#, it will REALLY push you) of using pre-built tools and into someone who builds and adapts their own tooling.

I can't believe I'm saying this, but the OSEP is an exam I actually wouldn't mind taking again.

![OSEP Cert](/public/osep_cert.png)
