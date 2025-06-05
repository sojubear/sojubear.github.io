---
title: My HTB CPTS Exam Review
date: 2025-06-05 00:00:00 +0800
categories: [Category]
tags: [tag1, tag2, tag3]     # TAG names should always be lowercase
author: Sojubear
---
## Real talk about Hack The Box's Certified Penetration Testing Specialist exam from someone who barely survived it

![CPTS Certificate](/public/lv58zP0Nc1rigRR47QTY0v21HfHBkBGe.jpg)

Alright, let's get straight into it. Like everyone else, I'm writing my exam review because its customary for cybersecurity professionals to do so. But to be honest, this one is worth sharing because the CPTS destroyed me in the best possible way.

## Who Am I and Why This Particular Form of Torture

I am a Cyber Threat Intelligence Engineer who masquerades as a Red Team Operator. You know the type, the ones that get way too excited when talking about attack paths and spends way too much time with other Offensive Security professionals. I have the OSCP certificate under my belt, which made me think this exam was going to be a walk in the park. Spoiler Alert : Its not a walk in the park. 

Originally, I started down the Certified Bug Bounty Hunter(CBBH) path because I thought I liked doing Web Testing. But then i came across [this](https://gatari.dev/posts/certified-cert-collector/?trk=feed_main-feed-card_feed-article-content) blog post by a friend of mine and he said something like "hey maybe try this harder thing instead" 

![CPTS Path](/public/Pasted%20image%2020250605215752.png)

So naturally, seeing how much I hate having free time, switched to the CPTS.

I kicked off the Bug Bounty path around January and switched to the Penetration Tester path in March. It took me about three months to get through the entire 28-module course while juggling a full time job. We're talking a couple hours on weeknights when I could manage it, and full weekend days when my I begged my family to give me some time to get my studying done.

## The Good, The Bad & The Why Is This Module So Damn Long?

Coming from the OSCP, I figured this would mostly be a huge refresher with maybe a few new techniques throw in here and there, but boy was I wrong. The Penetration Tester path is a long and arduous 28 module course that covers everything from basic enumeration, web attacks to documentation and reporting.

Some modules, like "Active Directory Enumeration & Attacks", took me nearly two weeks to complete due to its sheer volume. 

The final module, "Attacking Enterprise Networks" is a capstone module that integrates all previously learned penetration testing concepts into a realistic, end-to-end engagement. By the time I've hit that module, I was already running on fumes.  Everyone in the HTB Discord recommended for exam participants to tackle it blind as a real test of understanding, but honestly? I was so burned out I just followed the walkthrough and focused on organizing my notes and methodology. 

The course material is comprehensive, probably the most thorough penetration testing curriculum I've encountered. This isn't a quick certification grab. Most people need a solid six months to really absorb everything without cutting corners. The Academy content is legitimately excellent, but it's also a marathon, not a sprint.

## The Exam: Goodbye To Sleep

10 Days. Minimum 12/14 flags. One report. Sounds reasonable right?

Wrong. So very wrong.

The CPTS exam is absolutely brutal and unforgiving. 10 days might seem like a reasonable amount of time, but there are so many rabbit holes that look like legitimate attack vectors. There are no "low hanging fruit" kind of flags, one was almost out of reach. I spent every exam moment convinced I was about to fail, which might apparently be the standard CPTS exam experience.

To be fair, I kind of forgot that I had 10 days to take the exam. I was up til early in the morning hacking, slept for a couple of hours, got my kid read for school, work a full day, come back, repeat. Don't be an idiot like me, clear your calendar as much as possible before attempting the exam.

I managed to grab all 14 flags in about 4 days. That seemed like a reasonable amount of time, but it ended up biting me due to my lack of documentation along the way.

## Reporting: The Most Painful Part of the Exam

Getting that last flag should have calmed me down. But honestly, the relief never came because I still had that report to do.

I used SysReptor along with their HTB CPTS exam report format which made formatting slightly easier. But here's where I screwed up, I was so focused on blitzing through technical portion of the exam that I did not properly document my steps and missed out on a couple of screenshots. So there were multiple occasions that I had to redo entire attack chains to get the proper documentation.

I've heard multiple horror stories of people failing the exam despite obtaining all the flags because their reports were not up to standard. Some folks write 150+ page reports trying to cover every possible angle. Mine ended up at 155 pages and barely squeezed under the 20MB size limit at 19.5MB.

I submitted at 5 AM on day six while completely sleep deprived. In hindsight, I should have waited, reviewed everything with fresh eyes, and submitted something I was actually proud of. But exhaustion makes you do stupid things. But hey, a pass is a pass, and I'll take it.

## Learn from my mistakes

1. Make sure that you have your full 10 days free as much as possible, you will need the extra time
2. The exam tests material directly from the Academy content, so organize those notes like your certification depends on it (because it does)
3. Take proper screenshots, keep detailed notes of your attack paths, and save yourself the pain of recreating everything later
4. Don't pull all nighters, I learned this the hard way being exhausted makes everything harder and leads to stupid mistakes.

## CPTS vs. OSCP: The Inevitable Comparison
There's this meme floating around that CPTS passers can handle OSCP, but OSCP holders might struggle with CPTS. Having done both, I think there's truth to that.

OSCP has the reputation for being brutal because of its time pressure 24 hours to hack, 24 hours to report. But CPTS is a different kind of hard. It's more comprehensive, goes deeper into methodology, and requires a level of documentation that OSCP just doesn't demand.

Content wise, CPTS covers way more ground. I spent a month on OSCP materials plus extra lab time. CPTS took me three months just for the course content. The depth and breadth aren't even comparable

From a cost perspective, CPTS is the clear winner:

OSCP: $1,749 for three months + one exam attempt
CPTS: $490 for annual silver (includes Bug Bounty and SOC paths) + one exam voucher + free retake

# Final Thoughts and Author's Notes

I am not going to sugar coat it, this was one of the most painful experiences of my life. There were moments I genuinely questioned my life choices and wondered if I was cut out for this field. The combination of technical difficulty, time pressure, and documentation requirements creates a perfect storm of stress, and the lack of sleep did nothing to help.

That out of the way, I would still recommend this to anyone serious about penetration testing. The Academy content is top tier, the exam truly tests your skills in a realistic environment, and passing it means you've proven you can handle real world engagements.

Just don't underestimate it. Respect the process, prepare properly, and maybe don't try to balance it with everything else in your life like I did. Your future self will thank you.

Is it worth it? Absolutely. Would I do it again? Probably not haha

Good luck to anyone brave enough to take this on. You're going to need it.

![CPTS Certificate Page](/public/HTB%20Certified%20Penetration%20Testing%20Specialist_page-0001.jpg)