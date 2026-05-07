---
layout: page
title: MKTG 565
permalink: /mktg565/
description:
nav: false
display_title: false
---

<style>
  .course-hero {
    border-left: 4px solid var(--global-theme-color);
    padding: 0.4rem 0 0.4rem 1.25rem;
    margin: 1rem 0 2.25rem 0;
  }
  .course-hero .course-tag {
    font-family: 'SF Mono', Consolas, Monaco, monospace;
    font-size: 0.72rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--global-text-color-light);
    display: block;
    margin-bottom: 0.55rem;
  }
  .course-hero h1 {
    font-size: 1.75rem;
    line-height: 1.2;
    margin: 0 0 0.6rem 0;
    color: var(--global-theme-color);
    font-weight: 700;
  }
  .course-hero .course-tagline {
    font-size: 1.02rem;
    line-height: 1.55;
    margin-bottom: 0.65rem;
  }
  .course-hero .course-meta {
    font-size: 0.88rem;
    color: var(--global-text-color-light);
    line-height: 1.55;
    margin: 0;
  }
  .schedule-table {
    width: 100%;
    border-collapse: collapse;
    margin: 0.5rem 0 1.5rem 0;
  }
  .schedule-table td {
    padding: 0.85rem 0.5rem;
    vertical-align: top;
    border-bottom: 1px solid var(--global-divider-color);
    line-height: 1.55;
  }
  .schedule-table td.col-week {
    width: 5rem;
    color: var(--global-theme-color);
    font-weight: 700;
    font-family: 'SF Mono', Consolas, Monaco, monospace;
    font-size: 0.85rem;
    padding-top: 1rem;
  }
  .schedule-table .week-title {
    font-weight: 700;
    color: var(--global-text-color);
    display: block;
    margin-bottom: 0.3rem;
  }
  .schedule-table .week-body {
    font-size: 0.95rem;
    margin: 0;
  }
  .schedule-table .week-tag {
    display: inline-block;
    margin-top: 0.4rem;
    font-family: 'SF Mono', Consolas, Monaco, monospace;
    font-size: 0.72rem;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--global-theme-color);
  }
  .grading-table {
    width: 100%;
    border-collapse: collapse;
    margin: 0.5rem 0 1.5rem 0;
  }
  .grading-table th, .grading-table td {
    padding: 0.55rem 0.5rem;
    border-bottom: 1px solid var(--global-divider-color);
    line-height: 1.5;
  }
  .grading-table th {
    text-align: left;
    font-size: 0.78rem;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--global-text-color-light);
    font-weight: 600;
  }
  .grading-table td.weight {
    text-align: right;
    font-family: 'SF Mono', Consolas, Monaco, monospace;
    width: 6rem;
    white-space: nowrap;
  }
  .grading-table tr.total td {
    border-top: 2px solid var(--global-theme-color);
    font-weight: 700;
    border-bottom: none;
  }
  .policy-block {
    margin: 1.1rem 0;
  }
  .policy-block h5 {
    color: var(--global-theme-color);
    font-weight: 700;
    margin-bottom: 0.35rem;
    font-size: 1rem;
  }
  .policy-block p {
    margin: 0;
    font-size: 0.95rem;
    line-height: 1.6;
  }
</style>

<div class="course-hero">
  <h1>Building Business Applications of LLMs and Generative Models</h1>
  <p class="course-tagline">I believe human language has become the standard programming language. This course teaches future product managers, investors, and entrepreneurs at Foster to build with that capability.</p>
  <p class="course-meta"><strong>Instructor:</strong> Zikun Ye &nbsp;·&nbsp; <strong>Term:</strong> Every spring quarter, starting Spring 2026</p>
</div>

#### Description

Building with AI no longer requires writing code: students describe what they want, and the model produces it. This course is grounded in that shift. In ten weeks, we go from a first API call to a working LLM-powered prototype: agents that use tools, retrieval systems built on any corpus, and fine-tuned models that produce reliable business outputs.

The course has three parts. We build hands-on every week. We demystify the techniques underneath, from attention and embeddings to RAG, fine-tuning, agents, multimodality, and physical AI. Every concept is grounded in a business application: market research, content generation, advertising, and AI search.

**No prior coding experience is required.**

#### Learning Outcomes

By the end of this course, you will be able to:

1. **Demystify** the core building blocks of generative AI: attention, embeddings, RAG, fine-tuning, alignment, and the AI product stack from chat interfaces to agentic workflows.
2. **Build** end-to-end LLM-powered applications and agentic systems that solve real business problems.
3. **Lead** AI initiatives, weighing feasibility, cost, risk, and responsible deployment.

#### Course Materials

- All slides, Colab notebooks, case readings, and recordings are posted on Canvas. No textbook required.
- We use the OpenAI API for some in-class activities and assignments.
- Use any AI coding tool of your choice. IDE-based options include Cursor and Antigravity. CLI-based options include Claude Code, Codex, and Gemini CLI. In class, I primarily demo with Claude Code and Codex.

#### Schedule

<table class="schedule-table">
  <tbody>
    <tr>
      <td class="col-week">Week 1</td>
      <td>
        <span class="week-title">Agentic Coding</span>
        <p class="week-body">Course overview and an introduction to agentic coding. A coding agent runs analytics and builds a frontend dashboard from a plain-English brief, and we explore more agent use cases together.</p>
      </td>
    </tr>
    <tr>
      <td class="col-week">Week 2</td>
      <td>
        <span class="week-title">LLM Foundations &amp; API</span>
        <p class="week-body">Demystify the LLM: tokens, next-word prediction, sampling, transformers, pre-training and post-training, and deployment for inference. We then run zero-shot, few-shot, and chain-of-thought sentiment analysis on Amazon Reviews via the OpenAI API.</p>
        <span class="week-tag">Mini Assignment 1: First API call &nbsp;·&nbsp; Major Assignment 1: Batch text analysis</span>
      </td>
    </tr>
    <tr>
      <td class="col-week">Week 3</td>
      <td>
        <span class="week-title">Agentic AI</span>
        <p class="week-body">An agent is an LLM that decides its own next step, looping through plan, act, observe, and verify, with tools, memory, skills, and MCP integrated. We dissect coding, deep research, and shopping agents, then build our own ad-campaign generation agent.</p>
        <span class="week-tag">Mini Assignment 2: Agentic AI showcase</span>
      </td>
    </tr>
    <tr>
      <td class="col-week">Week 4</td>
      <td>
        <span class="week-title">Embeddings &amp; RAG</span>
        <p class="week-body">Why vanilla LLMs hallucinate and lack access to private data, and how embeddings and RAG address these limitations. We build a full pipeline on Amazon reviews, evaluate whether RAG outperforms the baseline, then discuss enterprise RAG and the trajectory of agentic RAG.</p>
        <span class="week-tag">Mini Assignment 3: Embeddings &amp; RAG &nbsp;·&nbsp; Major Assignment 2: RAG in the wild</span>
      </td>
    </tr>
    <tr>
      <td class="col-week">Week 5</td>
      <td>
        <span class="week-title">GenAI Ecosystem</span>
        <p class="week-body">Map the five-layer AI stack from energy and chips up through infrastructure, models, and applications. We trace where value is captured across the stack, where competitive moats are forming, and the implications for builders and investors.</p>
      </td>
    </tr>
    <tr>
      <td class="col-week">Week 6</td>
      <td>
        <span class="week-title">Fine-Tuning</span>
        <p class="week-body">What fine-tuning is, when to apply it, and what it powers: safety alignment, distillation, reasoning models, brand voice, content generation. We work through the Upworthy headline case study end-to-end, from data and LoRA to deployment and revenue lift.</p>
        <span class="week-tag">Major Assignment 3: Fine-tuning</span>
      </td>
    </tr>
    <tr>
      <td class="col-week">Week 7</td>
      <td>
        <span class="week-title">GenAI Applications</span>
        <p class="week-body">AI beyond text: multimodal and vision models, and physical AI. We tour applications in content generation via adaptive prompting, market research via digital twins, and robotics in operations.</p>
      </td>
    </tr>
    <tr>
      <td class="col-week">Week 8</td>
      <td>
        <span class="week-title">Deploying AI Agents</span>
        <p class="week-body">Deploying an agent in production: evaluations, guardrails, cost, latency, and the organizational changes such deployments require.</p>
        <span class="week-tag">Panel with industry experts</span>
      </td>
    </tr>
    <tr>
      <td class="col-week">Week 9</td>
      <td>
        <span class="week-title">AI Impact, Risks &amp; Society</span>
        <p class="week-body">How AI is reshaping work and society, and the live debates around safety, polarization, discrimination, and copyright. We translate the governance debates into what it means for the businesses you'll build or invest in.</p>
      </td>
    </tr>
    <tr>
      <td class="col-week">Week 10</td>
      <td>
        <span class="week-title">Demo Day</span>
        <p class="week-body">Each team demonstrates a working LLM-powered prototype to a non-technical audience.</p>
      </td>
    </tr>
  </tbody>
</table>

#### Assessment

<table class="grading-table">
  <thead>
    <tr><th>Component</th><th class="weight" style="text-align:right;">Weight</th></tr>
  </thead>
  <tbody>
    <tr><td>Class participation</td><td class="weight">15%</td></tr>
    <tr><td>Mini assignments</td><td class="weight">15%</td></tr>
    <tr><td>Major assignments</td><td class="weight">30%</td></tr>
    <tr><td>Final project</td><td class="weight">40%</td></tr>
    <tr class="total"><td>Total</td><td class="weight">100%</td></tr>
  </tbody>
</table>

The **final project** is the central deliverable: an end-to-end LLM-powered application that solves a real business problem. The format is flexible: a web app, a local demo, a tool built on top of an LLM API, or any other working prototype. The expectation is a functioning prototype, not a slide deck.

#### Course Policies

<div class="policy-block">
  <h5>Generative AI</h5>
  <p>Students are <strong>permitted and encouraged</strong> to use generative AI tools such as ChatGPT, Claude, Gemini, and GitHub Copilot throughout this course, including assignments, projects, and in-class exercises. Students are responsible for the accuracy and quality of all submitted work, regardless of whether AI assisted in producing it. Submitting AI-generated work that the student cannot explain constitutes a violation of academic integrity.</p>
</div>

<div class="policy-block">
  <h5>Prerequisites</h5>
  <p>None. Prior exposure to machine learning or analytics is helpful but not required. Familiarity with AI tools such as ChatGPT through general use is sufficient preparation.</p>
</div>

<div class="policy-block">
  <h5>Academic Integrity, Disability &amp; Religious Accommodations</h5>
  <p>This course follows the University of Washington Student Conduct Code. Students requiring accommodations should contact <a href="https://depts.washington.edu/uwdrs/">Disability Resources for Students (DRS)</a> as early as possible. Religious accommodations follow UW's <a href="https://registrar.washington.edu/staffandfaculty/religious-accommodations-policy/">Religious Accommodations Policy</a> and must be requested within the first two weeks of the course.</p>
</div>
