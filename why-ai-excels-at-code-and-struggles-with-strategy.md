# Why AI Excels at Code and Struggles with Strategy

## The Verifiability Problem

There's a pattern anyone who works with LLMs has noticed. Ask an AI to write code, and it often produces something useful. Ask it to help with strategy, and you get fluent, confident, completely generic advice. The structure is there. The thinking isn't.

This isn't about intelligence. The same model that can debug a complex algorithm produces bland strategy documents. What's going on?

The answer isn't that strategy requires "creativity" or "intuition" that AI lacks. It's simpler: **most knowledge work is non-verifiable, and that breaks the training loop.**

---

## What Makes Code Different

Code has a property that most knowledge work lacks: **fast, objective feedback.**

You write a function. You run tests. They pass or fail. The compiler accepts your code or rejects it. There's no ambiguity. This isn't just convenient for programmers — it's essential for how AI learns.

Reinforcement learning requires a feedback signal. The agent takes an action, the environment responds, and the agent learns from that response. In code, the environment is the test suite. The response is binary: correct or incorrect. This enables what researchers call RLVR — Reinforcement Learning from Verifiable Rewards.

DeepSeek-R1-Zero demonstrated something striking: when you train a model with pure RL on verifiable rewards (unit tests), it develops emergent behaviors. The model learns to self-verify, to backtrack when it hits dead ends, to have what researchers call "aha moments." No supervised fine-tuning required. The feedback loop teaches it to reason.

This works because code is:
- **Verifiable**: Tests pass or fail
- **Fast**: Feedback in seconds
- **Objective**: Same answer for everyone

Most knowledge work has none of these properties.

---

## The Non-Verifiability Spectrum

Knowledge work exists on a spectrum:

| Work | Verifiable? | Feedback Speed | RL-able? |
|------|-------------|----------------|----------|
| Code | Yes | Seconds | Yes |
| Legal contracts | Yes | Months-Years | Hard |
| Product strategy | Sometimes | Quarters | Very Hard |
| Aesthetic judgment | No | Never | No |

The key insight: **verifiability alone isn't enough.** You need fast feedback loops. A legal contract is verifiable — did it get challenged? did we win? — but the feedback takes years. By the time you learn, the training opportunity is gone.

Strategy sits in the worst position. It's often non-verifiable (did the strategy work, or did execution fail?). When it is verifiable, the feedback takes quarters. You can't run a thousand strategy experiments per second like you can with code.

This isn't a gap that more data fixes. It's structural.

---

## When You Can't Verify, You Impose Taste

Here's what happens when you train an AI on non-verifiable tasks.

You can't use RLVR because there's no verifiable reward. So you use RLHF — Reinforcement Learning from Human Feedback. You show humans two outputs, ask which is better, train a reward model on those preferences, optimize the AI to maximize that reward.

But whose preferences?

The annotators hired by the lab. People selected for agreeing with the lab's values. People who may or may not share your context, your industry, your aesthetic sense.

The article I was critiquing called this "no taste" — training averages away individual judgment. But that's not quite right. **RLHF produces a specific taste: the taste of the lab's annotators.**

This isn't absence. It's misalignment.

When you ask an AI for strategy advice, you're not getting "no taste." You're getting OpenAI's taste, or Anthropic's taste, or DeepSeek's taste. These are reasonable defaults — they're not random. But they're not *yours*.

The problem isn't that AI can't have taste. The problem is that when verifiability fails, the lab's taste is what you get.

---

## Reasoning Amplifies, Doesn't Substitute

The latest models — o1, o3, Claude's extended thinking — do something new. They "reason" for longer, spending more compute at inference time, working through problems step by step.

This is genuinely powerful. On verifiable tasks (math, code, logic puzzles), extended reasoning dramatically improves performance. The model can catch its own errors, backtrack, verify intermediate steps.

But here's the catch: **reasoning operates on premises.** If you give the model wrong premises, extended reasoning produces confident wrong answers.

This is why context isn't a nice-to-have. It's the foundation that reasoning builds on.

A model with superhuman reasoning but generic context will produce superhuman reasoning about the wrong problem. It will optimize for objectives you don't have, consider constraints you don't face, ignore constraints you do face. The reasoning is sound. The premises are wrong.

---

## Context is Fractal

This is where most "just add context" advice fails.

The problem isn't context window size. Modern models have 1-2 million token contexts. You can dump your entire document library into them.

The problem is that **context is fractal** — infinitely detailed, and you don't know what's relevant until you need it.

Consider a product strategy decision. What context matters?

- Your company's competitive position
- Your team's capabilities
- Your technical debt
- Market dynamics
- Customer feedback
- Regulatory environment
- Your personal risk tolerance
- Your investors' expectations
- Your burn rate
- Your runway
- Your competitors' likely responses
- Your past failed attempts
- Your organizational politics
- ...

You can't pre-index all of this because you don't know what matters. The relevance is discovered in the moment, during the specific decision. And the next decision will need different context.

This is why labs can't solve this at scale. Every user's fractal is different. Every decision needs different slices of the fractal. The problem isn't engineering — it's that relevance is emergent, not pre-determinable.

---

## The Product Opportunity

If context is fractal and labs can't solve it at scale, the opportunity isn't in better models. It's in better context infrastructure.

What would that look like?

**Personal AI**: Models fine-tuned on your data, your decisions, your taste. Not "your documents" — your *decisions*. The pattern of what you chose when, what worked, what didn't. This is how you encode your taste into the model.

**Context-gathering agents**: AI that interviews you, reads your docs, asks clarifying questions, surfaces what you might have forgotten. Not passive retrieval — active discovery. "You mentioned the competitor's pricing, but I noticed you haven't discussed their recent acquisition. Is that relevant?"

**Fractal surfacing**: Tools that help you discover what context is relevant. You don't know either. The AI's job isn't to have the answer — it's to help you figure out what question you're actually asking.

The companies that win won't be the ones with the best reasoning models. They'll be the ones that solve the context problem — that help users navigate their own fractal, that encode individual taste, that surface relevance in the moment.

---

## What This Means for You

If you're using AI for knowledge work:

1. **Recognize the verifiability gradient.** Code, math, logic — these work well because they're verifiable. Strategy, aesthetics, judgment — these work poorly because they're not. Don't expect the same quality.

2. **Know whose taste you're getting.** When you ask for non-verifiable work, you're getting the lab's taste. This might be fine. But know it's not neutral.

3. **Context is your job, not the model's.** The model can't know what context is relevant. You have to surface it. The more specific your context, the more useful the reasoning.

4. **The opportunity is in context infrastructure.** If you're building products, don't compete on reasoning. Compete on context — personalization, discovery, relevance.

---

## The Core Insight

AI excels at code not because code is simple, but because code is verifiable. It struggles with strategy not because strategy is creative, but because strategy is non-verifiable.

When you can verify, RL works. When you can't, the lab's taste is imposed.

Reasoning is powerful, but reasoning on wrong premises produces confident wrong answers.

Context isn't a context window problem — it's a fractal discovery problem. You don't know what matters until you're in the moment.

The models will keep getting better at reasoning. But the companies that win will be the ones that solve context — that help users navigate their own infinite detail, that encode individual taste, that surface relevance when it matters.

Reasoning is the engine. Context is the fuel. Right now, we have increasingly powerful engines running on generic fuel.

The opportunity is in the fuel.