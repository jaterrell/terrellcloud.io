---
layout: post
title: "Five questions we ask before any cloud architecture review"
date: 2026-07-03 09:00:00 -0500
categories: [cloud]
tags: [cloud, architecture, reliability, cost-optimization]
---

Cloud architecture reviews go wrong in a predictable way: they start with
the diagram. A diagram tells you what someone intended to build. It says
very little about what the system actually does under load, what it costs,
or what breaks at 2 a.m.

Before we look at any client's architecture diagram, we ask five
questions. The answers reshape the review every time.

## 1. What does this system cost per month, and who looks at that number?

Not the budget — the actual bill, broken down by service. If nobody on the
team can answer within twenty percent, cost isn't being managed, it's
being absorbed. The follow-up ("who looks at it?") matters more than the
number: unowned costs grow, owned costs shrink. This is usually where we
find the quickest wins — idle non-production environments, oversized
instances, and data transfer patterns nobody chose on purpose.

## 2. When did this system last fail, and how did you find out?

The answer distinguishes systems with operational maturity from systems
with operational luck. "Last Tuesday, an alert paged us before customers
noticed" is a healthy answer regardless of the failure. "It doesn't really
fail" means either nobody's looking, or the system hasn't been stressed
yet — and both mean the reliability posture in the diagram is untested
theory.

## 3. What's the one change you're afraid to make?

Every team has one: the database migration nobody wants to run, the IAM
policy nobody fully understands, the service that only one engineer can
deploy. That fear is a precise map of where the architecture's real risk
lives. Reviews that skip this question produce recommendations about the
parts of the system that were already fine.

## 4. If this workload doubled next quarter, what breaks first?

The point isn't the prediction — it's watching where the team looks.
Confident, specific answers ("the write path on the primary database")
indicate a team that knows its bottlenecks. Silence, or five different
answers from five engineers, tells us the scaling story is aspiration
rather than design.

## 5. What are you paying for that you no longer need?

Architectures accrete. The message queue added for a feature that was
cancelled, the second region "for DR" that's never been failed over to,
the Kubernetes cluster running three pods. Subtraction is the most
underrated architectural move in cloud systems, and nobody inside the
team has the standing to propose it. Outside reviewers do — it's half of
why reviews are worth commissioning.

---

Only after these five answers do we open the diagram — because at that
point, we know which parts of it are load-bearing and which are wishful
thinking. If your team is due for that kind of review, the
[about page](/about/) covers how we engage.
