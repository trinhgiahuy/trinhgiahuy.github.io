---
layout: post
title: My BosonAI's hackathon project ranked 2nd place in benchmarking stream - Benchmarking the scalable Audio Higgs Model and Qwen3.2
date: 2025-09-06 07:59:00-0400
inline: false
related_posts: false
# render_with_liquid: true
# tags: [hackathon, llm, benchmarking, audio, routing]
# categories: [project]
# permalink: /news/bosonai-hackathon/
---

My [BosonAI](https://www.boson.ai/)'s hackathon project ranked 2nd place in benchmarking stream: Benchmarking the scalable Audio Higgs Model + Qwen3.2 :tada:

---

## Project Overview

### Problem

When customers call support, they often get forced into a rigid menu (“press 1/2/3…”), even though:

- they don’t know which category their issue belongs to,
- routing takes time,
- scaling human agents is expensive,
- requests can span multiple domains.

### Our idea

Use **audio-first routing**:

1. synthesize/ingest caller request (TTS caller),
2. **understand** request → decide **department + intent**,
3. dispatch to the right **expert model**,
4. respond as an **agent** via TTS.

---

## System Diagram

<img
  src="/assets/img/posts/bosonai_hackathon/slide_03_system.png"
  class="img-fluid rounded z-depth-1"
  alt="System diagram of HiggAudioUnderstand routing to expert models and TTS agent"
/>
<p class="text-muted" style="margin-top: 0.5rem;">
  System pipeline: audio request → understanding/router → expert(s) → TTS agent response.
</p>

---

## Audio Examples (Caller vs Agent)

Below are paired audio clips (caller request → agent response).  
**Tip:** keep filenames short + lowercase.

<div class="row">
  <div class="col-md-6">
    <h4>Example 1 — Simple QA</h4>
    <p><strong>Caller</strong>: “What is two plus two?”</p>
    <audio controls preload="none" style="width:100%;">
    <source src="/assets/audio/bosonai_hackathon/q1_caller.mp3" type="audio/mpeg" />
    </audio>
  </div>

  <div class="col-md-6">
    <h4>&nbsp;</h4>
    <p><strong>Agent</strong>: short phrase answer</p>
    <audio controls preload="none" style="width:100%;">
    <source src="/assets/audio/bosonai_hackathon/q1_agent.mp3" type="audio/mpeg" />
    </audio>
  </div>
</div>

<br/>
