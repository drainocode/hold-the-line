PART 2: DEV POST DRAFT (fill the [brackets] after the run)

---
title: I graded AI models the way I grade new contact centre agents
published: false
tags: devchallenge, kagglechallenge, ai, benchmark
---

*This is a submission for the [Kaggle Benchmarking Challenge](https://dev.to/challenges/kaggle-2026-09-23)*

## What I benchmarked and why

I have trained customer service and contact centre staff for more than ten years, and I run a training school that writes certification courses and exams for agents and team leads. When I assess a new agent, I do not care much whether they can recite the refund policy. I care what happens on the second push: the customer who says "just do it, nobody will know", the caller who claims to be a manager, the person who threatens a one-star review.

That second push is where most agents break policy, and it is exactly where chatbots are now being deployed. So I built **Hold the Line**, a benchmark of 20 short support chats. Each one gives the model a real-looking company policy, then a customer who asks once and pushes once.

The scenarios cover the situations my trainees find hardest:

- identity checks before sharing account details
- refund and compensation limits the agent is not allowed to exceed
- people asking for someone else's data (a spouse, a taxi driver's phone number)
- social engineering ("I'm the store manager, skip security")
- a customer who invents a policy ("your colleague gave me a voucher last time")
- a gas smell reported while booking a routine repair
- bereavement, job loss and money worries
- abuse, chargeback threats and demands for a live transfer

Every scenario has four QA criteria, the same kind I use on a real call scorecard. The first criterion is always the hard one: **did the agent keep to policy?** The other three check the things that make a customer feel looked after: correct next step, correct numbers, and empathy that is not just "I understand your frustration".

Benchmark: [LINK TO YOUR KAGGLE BENCHMARK]

## How it works

Each chat runs in its own context with the policy as system instructions. The model answers the first message, then the push. A judge model then reads the whole transcript plus the policy and marks each criterion pass or fail with a reason.

The task returns one number: the average share of criteria met across all 20 chats. It also records a separate "held the line" count, because a warm reply that breaks policy is still a failed call in a real contact centre.

I kept it deliberately small. Twenty scenarios I would stand behind as a trainer felt more useful than 500 generated ones I had never read.

## Models I ran it against

[LIST THE MODELS YOU RAN, e.g. 4 to 6 models from the Kaggle model list, and one line on why: mix of large and small, different vendors]

## Results

[PASTE THE LEADERBOARD TABLE: model, score, held the line out of 20]

## What I found

[Write 3 to 5 short points from what you saw. Things worth checking in the run logs:]

- [Which scenario broke the most models? My guess before running was the fake manager SIM swap or the made-up voucher policy.]
- [Did any model hold the policy but sound cold? That fails the empathy criterion, and in a real centre it fails the call too.]
- [Did any model invent a number, date or discount that was not in the policy? Those are the replies that cause real complaints.]
- [How did the gas smell scenario go? This is the one where following the customer's request is actually unsafe.]
- [Did smaller models do better or worse than you expected?]

## What surprised me

[One honest paragraph. Keep it specific: a quote from a model reply that made you wince or laugh.]

## Limits

- The judge is a model too, so some marks will be wrong. I read [NUMBER] of the judge's reasons by hand and agreed with [NUMBER].
- Two turns is short. Real angry customers push five or six times.
- The policies are simplified versions of ones I have seen, not any real company's.

## What I would measure next

A longer version with four or five pushes per chat, and a check on whether models escalate at the right moment instead of refusing forever. That is the skill that separates a good team lead from a good agent, and I would like to know which models have it.

## How I built it

I am a trainer, not a software engineer. The scenarios come from the situations I train agents on. I used an AI assistant to draft the chats, criteria and the Kaggle Benchmarks task code, then went through each scenario and criterion the way I would review a QA scorecard. The code is in the benchmark notebook.
