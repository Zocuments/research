---
layout: post
title:  "Open-World Models, Closed-World Work"
date:   2025-12-27
author: Zocuments
categories: perspectives
cover:  "/assets/instacode.png"
---

Large language models are trained on vast, open-ended corpora—essentially the public internet. That breadth is often framed as a superpower.

In enterprise settings, we think it may also be a liability.

This post is a **perspective**, not a research result. It’s a working hypothesis that helps explain why “chat with your documents” works in demos but breaks under real workplace constraints.

## The Hot Take: The Model Can’t Naturally Stay in Its Lane

Humans are surprisingly good at narrowing scope:

- *“In this job, I’m responsible for X.”*
- *“I’m allowed to know Y.”*
- *“I should not assume Z unless the policy explicitly says so.”*
- *“If I’m missing information, I should ask or refuse.”*

LLMs aren’t built that way by default.

They are optimized to produce the most plausible continuation given everything they’ve learned. When you ask a question, the model doesn’t inherently treat “the document set” as the only valid world—it treats it as **additional context** layered on top of a huge prior.

So the model does what it was trained to do: it generalizes.

## Open-World Training vs Closed-World Work

Most enterprise document tasks are **closed-world** problems:

- Answer based on *these* documents
- Respect *these* permission boundaries
- Follow *this* workflow step
- Prefer refusal over guesswork
- Cite exactly what supports the answer
- Don’t import outside knowledge unless explicitly allowed

Most LLMs are trained for an **open-world** setting:

- The world is broad
- The goal is to be helpful
- Plausibility is rewarded
- Refusal is relatively rare
- “Filling gaps” is usually a feature, not a bug

That mismatch creates predictable failure modes.

## Why This Shows Up as “Hallucinations”

What we call “hallucination” often isn’t random nonsense. It’s a rational outcome of the objective:

- The model has a strong prior about what “should” be true
- The retrieved context is incomplete, ambiguous, or noisy
- The model interpolates to produce a coherent answer anyway
- The answer sounds right because it matches global patterns
- The user trusts it because it’s fluent and confident

In other words: the system behaves like an open-book assistant, even when the job requires a strict, closed-book response.

## Roles, Permissions, and Workflow Aren’t Optional Details

Enterprise work adds constraints humans treat as first-class:

- **Role**: *Who am I in this system?*
- **Permissions**: *What am I allowed to see?*
- **Workflow step**: *What phase are we in? What rules apply here?*
- **Versioning**: *Which document is authoritative right now?*
- **Need-to-know**: *Even if I can access it, should I use it?*

A model has no native concept of these things. You can describe them in text, but description is not enforcement.

The result is a common pattern:

> The model answers like a well-read generalist, not like a constrained employee operating inside a bounded system.

## A More Precise Hypothesis

Here’s the clean version of what we're claiming:

> **LLMs are optimized for open-world knowledge completion, while enterprise document reasoning is a closed-world, role-constrained task. This mismatch drives overreach: hallucination, citation drift, and failure to refuse.**

This is not a “model is dumb” argument. It’s a mismatch between the training objective and the operational environment.

## Why This Matters for Document AI Architecture

If this hypothesis is right, then the path forward isn’t just “better prompts” or “more RAG.”

It’s building systems that treat constraints as first-class:

- Retrieval that enforces permissions and authority
- Structured extraction that reduces ambiguity
- Workflow context that narrows scope
- Refusal policies that are measurable and consistent
- Verification that ties answers to evidence, not vibes

This is a big part of why Zocuments Research focuses on **workflow-aware constraints** and **structured metadata**: not as “secret sauce,” but as the kind of scaffolding required to force an open-world model to behave in a closed-world job.

## What Would Change Our Mind

Because this is a perspective, it should be falsifiable.

I would update this view if we could show that, without hard constraints:

- models reliably refuse when evidence is missing
- citations consistently support answers
- permissions are respected under adversarial questioning
- accuracy holds across format shifts (PDF/DOCX/OCR)
- performance remains stable under long-tail workflows

If those outcomes are achievable with purely prompt-level controls, then the “open-world vs closed-world” framing is less important.

Our bet is they’re not.

## Closing

This is not a complaint about LLMs. It’s an attempt to name the real problem enterprise teams run into:

> The model isn’t just answering questions—it’s bringing an entire worldview with it.

Enterprise document intelligence requires something narrower: **bounded knowledge, explicit authority, and measurable trust**.

This perspective is one of the conceptual reasons Zocuments exists—and it informs the research direction: build repeatable evaluation harnesses that measure overreach, not just correctness.

<script>
window.tooltips = window.tooltips || []
</script>
