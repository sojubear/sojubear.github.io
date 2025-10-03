---
title: How to Tame Your Cursor AI
description: How GitHub's Spec Kit Fixed My AI Coding Workflow
date: 2025-10-03 00:00:00 +0800
categories: [AI]
tags: [cursor, ai]
image: "/public/spec_kit.webp"
---

### How GitHub's Spec Kit Fixed My AI Workflow

![spec_kit.webp](/public/spec_kit.webp)

I think many of us who work with AI coding assistants have fallen into the trap of "vibe coding." I know I have. I'd start a project with a clear idea in my head, give the AI a few prompts, and hope it could read my mind. For simple scripts, this sometimes worked. But the moment complexity crept in, the context window would inevitably get polluted. I've seen my AI partner refactor my Neo4j apis into oblivion, hallucinate entire functions that broke the call stack, and yes, it did drop my database tables too.

So many times my AI would go off-course, forgetting the initial request and creating a tangled mess of code. I spent way more time trying to debug what the AI did and re-educate it on the context than I'd care to admit. 

# Discovering GitHub's Spec Kit

I can't remember who shared this with me, but I recently discovered [GitHub's Spec Kit](https://github.com/github/spec-kit). It's a super cool tool that introduces "Spec-Driven Development". It currently has over 30,000 stars on GitHub

According to the Repo:
![SDD](/public/SDD.png)


It has changed how I interact with Cursor for my coding projects. The Spec Kit is a framework for defining your project's intent before it even writes the first line of code. What it does is that it creates a specification document, usually a `spec.md` file, that becomes an anchor point during the entire project.

**How it's been helping me:**

This specification file acts as a way to prevent my AI from forgetting my requirements. It is loaded into the context for every subsequent request, which reduces the chance that the AI agent will forget the context and hallucinate.

This spec document contains everything from Acceptance Scenarios to granular technical requirements. This allows the AI agent to understand clearly what I'm setting out to achieve.

This brings a much-needed engineering discipline to my workflow:

1. Instead of guessing what the user (me) wants, the AI now constantly references a detailed spec sheet with defined criteria that we agreed upon beforehand.
 
2. The AI is less likely to forget important information or introduce potential deviations deep in the development cycle because now it has the spec sheet to use as a constant reference point.

3. My development workflow and speed is far more predictable now that I have a structured workflow that I can apply to any project. 
   
Although it does take a longer time because now I have to force myself to think about what I actually want my project to achieve and all the technical specifications to get there before I even start my first prompt. 

# My Process using GitHub's Spec Kit

![SPTI](/public/SPTI.png)

I use a four step process which brings me from a high level concept to a code that is (hopefully) deployable. 

1. **Specify (`/specify`):** This is where I define the "what" and "why." I provide a high-level goal, and the AI helps me flesh it out into a `spec.md` file. It creates a structured document with sections for `Execution Flow`, `Functional Requirements`, and crucially, certain `Edge Cases`.

2. **Plan (`/plan`):** Once the spec is created and vetted by me, I focus on the "how." Using the `/plan` command, the AI generates a `plan.md`. This technical blueprint outlines the architecture. We define the `Technical Context` with specific frameworks that we want to use and what the `Project Structure` will be.

3. **Task (`/tasks`):** Now that we have the technical plan, the `/tasks` command breaks it down into a granular, actionable checklist. The AI breaks down the `plan.md` and generates a list of discrete engineering tasks, like "Implement the `User` model in `models/user.py`" or "Create the `POST /api/v1/users` endpoint with input validation."

4. **Implement:** Now the code gets created, using the `/implement` command. I can now tackle one task at a time. I will usually feed a specific task to the AI, and because the scope is so tightly defined and backed by the spec and plan files, the generated code is relatively accurate and fits within the established architecture. Alternatively, I can just YOLO and let the AI agent take the wheel and implement the entire project and test it in one go. 

Do note: This isn't a silver bullet which allows you to one-shot coding projects. There will definitely still be bugs and no matter how good your prompts are, there will always be a high chance that you forget to mention a small feature/api route that might vastly change the technical structure. There will still be some debugging and back and forth with my AI Agent.

# TLDR

The GitHub Spec Kit has really changed the way I prototype my projects. No more prompting Gemini to give me a half-baked Product Requirements Document (PRD) that my AI Agent and even myself won't follow. No more constantly reminding AI about context that we spoke about just two prompts ago. 

It has brought me a certain level of engineering rigor when it comes to AI assisted development. By forcing me to slow down and think about my specifications upfront, it changes my AI partner into a creative yet wildly unpredictable partner into a very effective tool. I have so far tested this on a new project and an existing one, and I am certain that now, I have better control, the code quality has improved, and I'm spending more time building instead of debugging hallucinations. 

If you've felt the same frustrations with AI coding assistants, I highly recommend integrating Spec Kit into your workflow. It's a glimpse into the future of how human developers and AI will collaborate to build truly great software.