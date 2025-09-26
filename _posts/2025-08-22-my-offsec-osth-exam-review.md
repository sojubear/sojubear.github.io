---
title: My OSTH Exam Review
description: Threat Hunting with Kali Linux and Why the Random Side Quest?
date: 2025-08-22 00:00:00 +0800
categories: [Course Review]
tags: [osth, offsec, threat hunting, exam] 
image: "/public/Course-TH-200.png"
---

# Threat Hunting with Kali Linux and Why the Random Side Quest?

To start off, I never actually planned on taking the OSTH exam. I was super lucky to have been sponsored OffSec's Learn Unlimited Subscription by my company recently, and my original plan was to knock out the three courses I needed for my OSCE3. Looking at the subscription details, my brain somehow fixated on the "3 downloads of course material" and I completely misinterpreted it. I thought this meant I could only "lock in" three courses and their exams for the entire year.

![OSTH Course Overview](/public/osth_image_1.png)

But, as you can see, I completely misread it. The subscription actually gives you a full year of lab access with unlimited courses and exam attempts. The only "3" was for the number of course PDFs I could download. Armed with this new knowledge that I had access to everything, I went on a tiny short adventure.

## The TH-200 Course Materials

To begin, the TH-200 is a foundation threat hunting course that teaches you how to proactively search for threats lurking undetected within a network. Unlike traditional SOC roles that mostly react to alerts, threat hunting usually assume that threat actors are already inside(assume breach) and need to be actively sought out. The course starts off with the essentials, covering the types of threat actors you'll face and how to properly report your findings. From there, you're thrown into hands-on labs where you'll need to hunt across networks and endpoints using tools such as Suricata, Wireshark, Splunk and CrowdStrike Falcon.

What I appreciated was how easy the course materials were to understand. Compared to the PEN-200, this was significantly easier to digest. Each module starts at a high level with clear objectives, so the concepts never felt convoluted.

The part I enjoyed the most, however, was the hands-on practice with CrowdStrike Falcon. While you also get to work with other key tools like Splunk and Suricata, Falcon was the standout. What made it so cool was its Real Time Response (RTR) capability, which allows you to actively query and run commands on live endpoints. It's a powerful feature that you don't typically get to experiment with unless you're using it on the job, and it was the absolute highlight of the labs for me.

![CrowdStrike Falcon Experience](/public/osth_image_2.png)

## Room for Improvement

Personally, I felt like the course materials were a little short. With only eight modules, it does feel a bit light for a 200-level course, especially when you compare it to the amount of content in PEN-200 (8 modules vs 20+ modules). I managed to get through the course materials in just under two days, with another two days to finish all the labs.

Although it does cover a lot of ground, the breadth does come at the cost of depth. Some modules feel like a high speed tour of a topic which had the potential to go much deeper. You get a solid introduction to a tool or concept, but just as you're ready to explore move, the course moves you on to the next thing.

Don't get me wrong, TH-200 is an excellent course. My main takeaway wasn't that it was lacking, but that I wished it was even bigger and more challenging because the content is so engaging.

That said, I think OffSec is taking a huge step in the right direction by branching out into blue team courses. I really hope they continue to build on this foundation and add more material to TH-200 in the future.

## The OSTH Exam Review

The OSTH exam is an 8-hour practical test that really does feel like a proper threat hunting sprint. You're given a threat intelligence report on a specific actor, and your goal is to hunt them down within a simulated network. To pass the exam, you need to obtain at least 50 out of 70 points(5 out of 7 questions). A crucial part of passing depends on submitting a detailed report that includes a "Hunt Narrative" and a timeline of the threat actor's activities.

The exam itself was super fun. Although 8 hours might seem short compared to the 24 hours for the OSCP, I felt it was more than enough time to find what I needed and write the report. What I did was to first take copious amounts of notes and screenshots of any potentially malicious activity without worrying too much about the specific exam questions. I focused on building a timeline of the threat actor's intrusion using the MITRE ATT&CK framework heavily to map out the threat actor's actions from one stage to the next.

Once I had a decent timeline, I started working through the seven questions. I was lucky that I had already found the answers to some of them while building my narrative, but a few required me to try harder(hehe). I think I took about 2 hours to obtain 5/7 flags. I spent another hour looking for the last 2 flags, but sadly was unable to find them (I couldn't quite figure out what the questions were asking for). But knowing that I already had a passing score, I took a long break and went for a premature celebration with some Mala Hotpot.

Upon returning, the report then took me about another two hours to complete. The process was relatively smooth because I was already pasting IoCs, screenshots, and my queries into the report template as I went along during the hunt. I only had to revisit the exam environment for a short time to better flesh out the story.

Oh, and here's something important to note: unlike many other OffSec exams, the OSTH does not have a pre-made SysReptor template. I was struggling a bit with the format at first and ended up writing my entire report in Markdown, so be prepared to structure it yourself.

## Is the TH-200 Worth Your Time and Money?

I really enjoyed this course and exam, but I find it difficult to recommend as a standalone purchase for someone looking to get into Threat Hunting. According to OffSec's website on the course. The Learn One bundle for TH-200 costs the same as other 200-level courses, like the PEN-200. However, when you compare the sheer volume of content, it feels a bit light. I completed the TH-200 course materials and labs in under a week of casual study, whereas the PEN-200 took me a full month of hardcore grinding. While the quality is there, the price point does feel steep for the amount of material provided.

On top of the initial cost, it's also important to remember that the OSTH certification expires after three years. There is a requirement to earn CPEs and pay the OffSec Annual Membership to maintain it, which is a long-term commitment to factor into your decision.

I would recommend this course to two specific groups:

**OffSec Learn Unlimited Subscribers**: If you already have the subscription, absolutely go for it. The OSTH is a fun and relaxing certification to add to your list.

**Anyone interested in CrowdStrike Falcon Experience**: If your main goal is to get structured, hands on lab time with CrowdStrike Falcon, this course is one of the best ways to do it.

## Conclusion

The random and unexpected detour into TH-200 turned out to be a really enjoyable certification journey. OffSec has created a course with high quality, easily digestible content and an exam that feels like a genuine threat hunt. The hands-on experience, particularly with CrowdStrike Falcon, is invaluable and makes the course a standout.

Despite my excitement, I stand by my feelings regarding the standalone price. The quality is definitely there, but the current content volume doesn't yet match the hefty price compared to the other courses provided by OffSec. That being said, I'm really looking forward to seeing how they build upon this course, hopefully fleshing out the materials to make it as comprehensive as its more famous counterparts.

With that out of the way, I really ought to focus on my PEN-300 course...

![OSTH Certificate](/public/osth_image_3.png)
