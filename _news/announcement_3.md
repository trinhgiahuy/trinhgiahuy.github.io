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
<div class="row">
  <div class="col-md-6">
    <h4>Example 7 — Time question</h4>
    <p><strong>Caller</strong>: “How many minutes are in an hour?”</p>
    <audio controls preload="none" style="width:100%;">
    <source src="/assets/audio/bosonai_hackathon/q7_agent.mp3" type="audio/mpeg" />
    </audio>
  </div>

  <div class="col-md-6">
    <h4>&nbsp;</h4>
    <p><strong>Agent</strong>: short phrase answer</p>
    <audio controls preload="none" style="width:100%;">
    <source src="/assets/audio/bosonai_hackathon/q7_agent.mp3" type="audio/mpeg" />
    </audio>
  </div>
</div>

---

## Case Study: Airline Customer Calling Service

<div class="row">
  <div class="col-md-4">
    <h4>Example 0</h4>
    <p class="text-muted">“Please help me make a new reservation for Toronto.”</p>
    <audio controls preload="none" style="width:100%;">
      <source src="/assets/audio/bosonai_hackathon/example0.mp4" type="audio/mpeg">
    </audio>
  </div>

  <div class="col-md-4">
    <h4>Example 35</h4>
    <p class="text-muted">“Online check-in isn’t working for me.”</p>
    <audio controls preload="none" style="width:100%;">
      <source src="/assets/audio/bosonai_hackathon/example35.mp4" type="audio/mpeg">
    </audio>
  </div>

  <div class="col-md-4">
    <h4>Example 56</h4>
    <p class="text-muted">“Set up UM service for my child.”</p>
    <audio controls preload="none" style="width:100%;">
      <source src="/assets/audio/bosonai_hackathon/example56.mp4" type="audio/mpeg">
    </audio>
  </div>
</div>

<br/>

### Routing taxonomy (skeleton)
We route into:
- **Department** (BOOKING / CHANGES / REFUNDS / …)
- **Intention** (NEW_BOOKING / SEAT_SELECTION / …)

<details>
<summary><strong>Click to expand routing labels</strong></summary>

- **BOOKING**: NEW_BOOKING, SEAT_SELECTION, …
- **CHANGES**: FLIGHT_CHANGE, NAME_CORRECTION, …
- **REFUNDS**: CANCEL_ITINERARY, VOUCHER_QUESTION, …
- **BAGGAGE**: ADD_EXTRA_BAGS, LOST_BAGS, …
- **FLIGHT_STATUS**: STATUS_REQUEST, DELAY_REASON, …
- **CHECK_IN**: ONLINE_CHECKIN, PASSPORT_ISSUE, …
- **LOYALTY**: MISSING_MILES, MERGE_ACCOUNTS, …
- **PAYMENT**: PAYMENT_FAILED, REQUEST_RECEIPT, …
- **SPECIAL_ASSISTANCE**: WHEELCHAIR, SPECIAL_MEAL, …
- **GENERAL**: SPEAK_TO_AGENT, OTHER, …

</details>

---

## Benchmarking: Concurrency

<!-- {% include figure.html
  path="assets/img/posts/bosonai_hackathon/slide_05_concurrency.png"
  class="img-fluid rounded z-depth-1"
  alt="Latency p50/p95 by stage vs concurrency"
  caption="Concurrency benchmark (replace with your exported plot image)."
%} -->
<img
  src="/assets/img/posts/bosonai_hackathon/slide_05_concurrency.png"
  class="img-fluid rounded z-depth-1"
  alt="Latency p50/p95 by stage vs concurrency"
/>
<p class="text-muted" style="margin-top: 0.5rem;">
Latency p50/p95 by stage vs concurrency"
</p>


### Key metrics (fill in)
| Setting | p50 Total Latency (ms) | p95 Total Latency (ms) | Notes |
|---|---:|---:|---|
| C=1 | TBD | TBD | baseline |
| C=2 | TBD | TBD |  |
| C=4 | TBD | TBD |  |
| C=8 | TBD | TBD |  |

---

## Benchmarking: Small dataset

<div class="row">
  <div class="col-md-12">
    <img
    src="/assets/img/posts/bosonai_hackathon/slide_07_confusion.png"
    class="img-fluid rounded z-depth-1"
    alt="Department and intent confusion matrices"
    />
    <p class="text-muted" style="margin-top: 0.5rem;">
    Confusion matrices on SMALL DATASET (department / intent).
    </p>
  </div>
</div>

### Summary numbers (example)
- Dataset: **64 examples**
- Department accuracy: **87.5%**
- Intent accuracy: **87.5%**

<div class="row">
  <div class="col-md-12">
    <img
    src="/assets/img/posts/bosonai_hackathon/slide_08_confusion.png"
    class="img-fluid rounded z-depth-1"
    alt="Department and intent confusion matrices"
    />
    <p class="text-muted" style="margin-top: 0.5rem;">
    Confusion matrices on LARGE DATASET (department / intent).
    </p>
  </div>
</div>

<!-- --- -->

<!-- ## Live Demo (embed)

If you have a demo video (mp4) in `assets/video/bosonai_hackathon/demo.mp4`:

<video controls preload="none" style="width:100%; border-radius:12px;">
  <source src="{{ '/assets/video/bosonai_hackathon/demo.mp4' | relative_url }}" type="video/mp4">
</video>

If you’re using YouTube instead, paste an iframe here: -->

<!--
<div style="position:relative;padding-bottom:56.25%;height:0;overflow:hidden;border-radius:12px;">
  <iframe
    src="https://www.youtube.com/embed/YOUR_ID"
    style="position:absolute;top:0;left:0;width:100%;height:100%;border:0;"
    allowfullscreen>
  </iframe>
</div>
-->

---

## Reproducibility

**Environment**
- TTS caller: HiggAudio v2
- Router: HiggAudioUnderstand + Qwen3.2
- TTS agent: HiggAudio v2

**How to run (skeleton)**

```bash
# 1) install
pip install -r requirements.txt

# 2) run demo
python demo.py --config configs/demo.yaml