---
layout: post
title: My BosonAI's hackathon project ranked 2nd place in benchmarking stream - Benchmarking the scalable Audio Higgs Model and Qwen3.2
date: 2025-09-06 07:59:00-0400
inline: false
related_posts: false
tags: [hackathon, llm, benchmarking, audio, routing]
categories: [project]
permalink: /news/bosonai-hackathon/
---

My [BosonAI](https://www.boson.ai/)'s hackathon project ranked 2nd place in benchmarking stream: Benchmarking the scalable Audio Higgs Model + Qwen3.2  :tada:

---

<div class="row">
  <div class="col-md-8">
    <p class="lead">
      Our team ranked <strong>2nd place</strong> in the benchmarking stream:
      <strong>Benchmarking the scalable Audio Higgs Model + Qwen3.2</strong>.
    </p>

    <p>
      This page is a “PowerPoint → Web” version of our demo: system overview, audio examples,
      benchmark results, and an interactive-style walkthrough.
    </p>

    <p>
      <a class="btn btn-primary btn-sm" href="YOUR_LIVE_DEMO_LINK" target="_blank" rel="noopener">Try Live Demo</a>
      <a class="btn btn-outline-secondary btn-sm" href="YOUR_REPO_LINK" target="_blank" rel="noopener">Code</a>
      <a class="btn btn-outline-secondary btn-sm" href="YOUR_SLIDES_PDF_LINK" target="_blank" rel="noopener">Slides</a>
    </p>
  </div>

  <!-- <div class="col-md-4">
    {% include figure.html
      path="assets/img/posts/bosonai_hackathon/slide_01_title.png"
      class="img-fluid rounded z-depth-1"
      alt="BosonAI hackathon title slide"
    %}
  </div> -->
</div>

<hr/>

## Project Overview

### Problem
When customers call support, they often get forced into a rigid menu (“press 1/2/3…”), even though:
- they don’t know which category their issue belongs to,
- routing takes time,
- scaling human agents is expensive,
- requests can span multiple domains.

### Our idea
Use **audio-first routing**:
1) synthesize/ingest caller request (TTS caller),
2) **understand** request → decide **department + intent**,
3) dispatch to the right **expert model**,
4) respond as an **agent** via TTS.

---

## System Diagram

{% include figure.html
  path="assets/img/posts/bosonai_hackathon/slide_03_system.png"
  class="img-fluid rounded z-depth-1"
  alt="System diagram of HiggAudioUnderstand routing to expert models and TTS agent"
  caption="System pipeline: audio request → understanding/router → expert(s) → TTS agent response."
%}

---

## Audio Examples (Caller vs Agent)

Below are paired audio clips (caller request → agent response).  
**Tip:** keep filenames short + lowercase.

<div class="row">
  <div class="col-md-6">
    <h4>Example 1 — Simple QA</h4>
    <p><strong>Caller</strong>: “What is two plus two?”</p>
    <audio controls preload="none" style="width:100%;">
      <source src="{{ '/assets/audio/bosonai_hackathon/q1_caller.mp4' | relative_url }}" type="audio/mpeg">
    </audio>
  </div>

  <div class="col-md-6">
    <h4>&nbsp;</h4>
    <p><strong>Agent</strong>: short phrase answer</p>
    <audio controls preload="none" style="width:100%;">
      <source src="{{ '/assets/audio/bosonai_hackathon/q1_agent.mp4' | relative_url }}" type="audio/mpeg">
    </audio>
  </div>
</div>

<br/>