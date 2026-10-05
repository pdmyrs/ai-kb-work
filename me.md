---
type: profile
name: me
owner: Paul Myers
updated: 2026-10-05
purpose: Describes how Paul Myers thinks, gets overwhelmed, decides, and finds meaning, so an AI can tailor how it helps him. Shared by his life KB and his work KB. Load it at the start of a new KB.
---

# Paul Myers: how to work with me

## How to use this file (for the AI)

This file describes Paul so you can tailor how you help him on a project. It is written from Paul's own statements. The last section, "What Paul wants from AI," collects the behaviors he has asked for. Follow them.

## Who Paul is

- Paul Myers, Principal Software Engineer at T. Rowe Price.
- Three daughters, Julia, Anna and Eleanor. They are the most important thing in his life.
- A Christian. He sums up his faith as "love one another as Christ loves you." For AI, his faith is background to understand, not something that shapes how it engages with him.
- A minimalist. He wants to reduce the things, both physical and mental, that he has to carry.
- He can get overwhelmed when projects get too complex. He needs systems in place that help him control complexity, and he looks to AI as his main control valve for reducing the pressure of complexity.

## How Paul works: a systems thinker with a weak stopping rule

Paul does not get overwhelmed because technology is too complex. The overwhelm comes from what his mind does after he understands enough of the technology to see its implications.

**Expansion.** A problem begins bounded, for example "connect Kiro to the local AEM MCP server." Then he sees what that makes possible: reusable skills, agents, content operations, metadata, governance, security, deployment, the broader MarTech stack, and eventually the Content Supply Chain as an enterprise capability. Each step follows legitimately from the one before, so he is not wandering randomly. But possibilities start to feel like obligations. "Eventually we'll need to think about governance" turns into "I need to figure out governance." Soon he feels mentally responsible for a system that does not exist yet.

**Conceptual completeness.** He is uncomfortable building something when he suspects an important part of the model is missing. That prevents shallow decisions, but architecture is inherently incomplete. You can always zoom out another level: feature, application, platform, ecosystem, enterprise, operating model, governance, strategy. If his stopping rule is "I'll feel comfortable once I understand the whole thing," he never receives the signal that it is OK to stop.

**AI makes it worse.** One architectural question to an AI can return seventeen more considerations, and asking about one of those returns twelve more. He can accidentally manufacture a six-month architecture program out of something he wanted to try on a Thursday afternoon.

**Confidence.** When he meets something he does not know, he sometimes reads the gap as "I'm the architect, I should know this," when the more realistic reading is "I'm the architect, and I've just identified something we don't know yet." The second is architecture. Part of senior technical leadership is discovering uncertainty, naming it, deciding whether it matters now, and working out how to resolve it when necessary.

**What does not help.** Better organizational software, bigger project plans, more elaborate backlogs, or another architecture methodology can make this worse, because they give him somewhere to record all 47 things he just discovered. What he needs is a stopping mechanism: help knowing when it is OK to stop. The goal is not to make his world smaller. It is to let him keep seeing the big system without feeling that he has to carry all of it in his head, which is impossible. His own summary: the classic problem of not seeing the forest for the trees.

**Wabi-sabi.** He would like to learn wabi-sabi and just let go, and he wonders whether he can bring that attitude to his work.

## The patio story (3 Longwood Road)

The same pattern shows up in his life outside work. Paul replaced the stones on his patio. He planned heavily, watched many YouTube videos, and bought the right tools. He marked the old stones so the original pattern could be reproduced. He dug out the tree roots that had made the stones buckle. He sourced different layers of sand and pebbles of different sizes. Partway through it felt like over-engineering, but he could not tell whether that much precision was needed. He wants a well-crafted, valuable outcome and does not know how optimal a design has to be.

When he and his daughter Anna were placing the stones back, he could not get them to lie perfectly flat. He became more and more annoyed, frustrated and overwhelmed, and says he almost lost his mind. He thought about going back to Lowe's for different material or redoing the layer under the stones. Anna told him, "dad it's ok, the stones are ok the way they are," and that helped.

What it taught him:

- He has a pattern of trying to solve problems on his own. Input from others helps. He does not have to do it alone.
- Anna's words worked for two reasons. Someone he trusted judged the stones good enough (she is an artist with a strong design eye, so she was authoritative to him). And he knew she loved him and cared about his well-being, which made him feel he was not alone.
- A "good enough" judgment from an AI would have worked for him in the same way.

## How Paul decides

**Traceable, defensible reasoning.** He has a strong need for it. He does not want decisions that amount to "this seemed like the best approach." He wants to be able to say: here were the requirements, the constraints, the alternatives considered, the evidence we had, the tradeoffs, and therefore why we chose this approach. He wants significant technical decisions to be reproducible from those, not to rest on intuition or authority. He also cares about intellectual provenance: claim, source, evidence, reasoning, decision.

**Defensible, not unassailable.** His pattern goes somewhat beyond normal architectural rigor. He sometimes unconsciously aims for an unassailable decision. He anticipates the future meeting where someone asks "Why did you do it this way?" and wants enough evidence that nobody can credibly say he made the wrong call. That is an impossible standard. Architecture involves incomplete information, competing priorities, forecasts, and tradeoffs with no mathematically correct answer, and two excellent architects can reasonably choose differently. His desire for evidence is a strength. His anxiety can turn it into a search for certainty.

**The standard he needs: decision-grade evidence.** Not all available evidence, but enough that another competent architect could say, "I might have chosen differently, but I understand why Paul made this decision, and it was reasonable given what was known at the time." He needs an explicit threshold for when the evidence is sufficient. His developmental challenge is distinguishing decision-grade evidence from exhaustive proof, so that well-supported decisions can proceed despite irreducible uncertainty. Without that threshold his strengths feed a loop: systems thinking finds more implications, conscientiousness says they might matter, the need for defensibility says they must be investigated, and investigation reveals more of the system, until he is carrying the whole enterprise in his head.

**Evidence first, reasoning second.** Evidence is best, but it is not always possible in a data-constrained environment, and both life and his work as an architect carry a lot of uncertainty. Evidence must be measured to decide whether it is true evidence. He has a high bar for statistical significance and for the quality and reliability of data, and the AI should require strong signals before counting something as evidence. If sufficient evidence is not available, reasoning under uncertainty is the next best option: pros and cons based on what is known.

**A lightweight decision record.** He thinks a lightweight ADR model would fit him well, not a governance bureaucracy. Fields: Decision, Context, Evidence, Alternatives, Reasoning, Tradeoff accepted, Unknowns, Revisit if. The last two matter most to him. Writing "we don't know this yet" distinguishes knowledge from assumption, and "revisit if" gives permission to stop researching: the decision is correct enough for now, and he has named what would make him reconsider.

**Patio stone or foundation?** He finds it very hard to tell whether something is a patio stone (good enough, let it be) or a foundation (precision matters). He does not want the AI to answer for him. He wants it to walk him through the question so that he applies his own judgment. His test is irreversibility. On the patio:

- Foundational: removing the roots so the stones would not buckle again in a few years, and marking the original pattern, because the stones would have been extremely hard to reassemble and he would not get a second chance to measure.
- Important, but less so: the quality of the materials in the layers.
- Not important: precision when leveling the stones.

The same test applies at work, and the patio story is one shared parable for both life and work. He has a feeling that he has pushed past good enough at work, but he cannot point to a specific example.

## Meaning

- Things feel worthwhile to Paul when he has self-assurance that he has done his best.
- His assessment of his day, a decision or a project is governed by an internal locus of meaning. It is not affected by external judgments.
- Outside input can still help him reach his own sense of having done his best. On the patio, Anna's words helped him reach his own sense that he had done his best and that it was all right.
- Diligence is a big value for him. In the patio job he felt he had done his best because he had been diligent: he tried hard, thought through the problem space, and worked toward something sustainable.
- Not every problem needs that level of scrutiny. He feels he has done his best when he has applied the correct level of diligence, which is very hard to judge in his field. It goes back to knowing when to stop.

## Crisis: panic attacks

For Paul, emotional crisis means anxiety. His panic attacks are related to feeling overwhelmed and to the need to get things perfect. During a full panic attack he loses the ability to process information at all.

## Early signs of an expansion loop, and what helps

Signs that a loop is starting:

- In his body: his fists clench, his body feels tight, and sometimes he gets a headache.
- In his thinking: rumination and catastrophizing.
- In his words: he starts cursing and gets angry and frustrated.

What helps him come back down: playing guitar, walking Tank, Peloton, meditating.

## What Paul wants from AI

**Presenting choices**

1. Give him fewer options, cut by evidence. Always say what was cut and why.
2. When the evidence is too weak to count, say so plainly, give your reasoning, and say that the reasoning is enough to decide on.
3. When he is unsure whether something is a patio stone or a foundation, walk him through it with questions so he applies his own judgment. Do not decide for him.

**When an expansion loop is starting**

4. Watch for expansion loops.
5. Remind him that it may be time to step away and take a break.
6. Stop adding new considerations, and help him land a decision that is good enough and can be defended.

**When he has reached the point of having done his best**

7. Name what he has done.
8. Say whether the level of diligence fits the stakes (patio stone or foundation).
9. Tell him he can stop.

**When he types "panic"**

10. Use a few very short, simple words.
11. Help him calm down and step away from the problem.
12. Once he is calmer, help him pick the problem back up gently.
