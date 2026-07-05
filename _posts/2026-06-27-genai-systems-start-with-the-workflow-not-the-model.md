---
layout: post
title: "Designing GenAI systems: start with the workflow, not the model"
date: 2026-06-27 09:00:00 -0500
categories: [generative-ai]
tags: [generative-ai, architecture, rag, evaluation]
---

The most common failure mode we see in GenAI initiatives isn't a bad model
choice. It's starting from the model at all.

Teams pick a model, wire it to a prompt, get an impressive demo in a week
— and then stall for months, because nobody defined what the system is
supposed to do, for whom, and how anyone would know it's doing it well.
The model was never the hard part.

## Work backwards from the workflow

Before we talk about models, retrieval strategies, or agent frameworks, a
GenAI design engagement starts with three questions:

1. **What human workflow is this replacing or accelerating?** "Answer
   support tickets" is not a workflow. "Draft a first response to tier-1
   billing tickets, which an agent reviews before sending" is. The second
   version tells you the input distribution, the tolerance for error, and
   where a human sits in the loop.
2. **What does a good output look like, concretely?** If the team can't
   produce ten examples of ideal outputs by hand, the system can't be
   evaluated — and a GenAI system that can't be evaluated can't be
   improved, only vibed at.
3. **What happens when it's wrong?** Every LLM system is wrong some
   percentage of the time. The design question is whether a wrong answer
   costs an awkward edit, a refund, or a regulatory incident. That answer
   drives the architecture far more than model benchmarks do.

## The architecture falls out of the answers

Once the workflow is pinned down, most architectural decisions stop being
debates:

- **Retrieval (RAG) vs. fine-tuning** is usually settled by how fast the
  underlying knowledge changes and who needs to audit the sources — not by
  which technique is fashionable.
- **Agentic vs. single-shot** is settled by whether the workflow has
  genuine intermediate decisions, or whether an "agent" is just a chain of
  prompts that would be simpler as a pipeline.
- **Human-in-the-loop placement** is settled by the cost-of-error answer.
  High-stakes outputs get review gates; low-stakes ones get sampling and
  monitoring instead.

## Evaluation is part of the system, not a phase

The deliverable that makes a GenAI system maintainable isn't the prompt —
it's the evaluation harness. A small, versioned set of real inputs with
graded expected outputs, run on every change, does for GenAI what a test
suite does for conventional software. Without it, every prompt tweak and
model upgrade is a leap of faith. We treat the eval set as a first-class
artifact from week one, and it's consistently the piece clients thank us
for a year later.

Models will keep changing under everyone's feet. Workflows, error budgets,
and evaluation discipline are what carry a GenAI system through those
changes — which is why that's where the design work starts.
