---
name: my-skills
description: "Route requests to the correct Skill in this collection: content-topic-ideator for batch self-media topic discovery and account analysis, zede-video-copywriter for writing a complete spoken video script from a topic after confirming the core viewpoint, zede-plan-learning-roadmap for evidence-based learning plans and progress replanning, interactive-learning for adaptive tutoring, and interactive-explainer for click-through 16:9 HTML explainers. Use when the user invokes $my-skills, asks which Skill to use, or gives a request that clearly belongs to one of these workflows."
---

# My Skills Router

Identify the user's primary intent and route to exactly one child Skill. Do not reproduce, summarize, or reimplement the child Skill's workflow here.

## Route table

| User intent | Route |
| --- | --- |
| Generate a batch of self-media topics, analyze an account for shareable directions, find differentiated topic ideas, or build a topic shortlist | `$content-topic-ideator` |
| Turn a selected topic into a complete spoken video script from scratch, after clarifying and confirming the user's core viewpoint | `$zede-video-copywriter` |
| Define a learning goal, diagnose the starting point, create an evidence-based roadmap, save a roadmap, or replan it from progress | `$zede-plan-learning-roadmap` |
| Learn a topic interactively, one question at a time, with explanations adapted to the learner's answers | `$interactive-learning` |
| Turn a complete Chinese narration script into a 1920x1080 click-through visual explainer HTML for screen recording | `$interactive-explainer` |

## Routing rules

1. Read the request and select the route whose deliverable best matches the user's immediate goal.
2. Tell the user the selected Skill in one short sentence, then follow that Skill's complete instructions.
3. If the request spans several workflows, start with the earliest blocking deliverable. For example, route topic discovery to `$content-topic-ideator` before writing, route an approved topic to `$zede-video-copywriter` when the user wants a complete script, route an undefined learning goal to `$zede-plan-learning-roadmap` before tutoring, and route an approved learning route to `$interactive-learning` when the user wants to start learning.
4. Ask one concise clarification only when two routes would produce materially different deliverables and the request does not reveal which result the user wants.
5. Respect an explicitly named child Skill unless it conflicts with higher-priority instructions.
6. Do not run several child Skills merely because their topics overlap. Hand off to another Skill only after the current deliverable is complete or the user changes goals.

## Boundary examples

- "给我的 AI 账号出 20 个有来源的选题" -> `$content-topic-ideator`
- "把这个选题从零写成一篇可直接念的视频口播稿" -> `$zede-video-copywriter`
- "帮我规划三个月学会 Python 的路线" -> `$zede-plan-learning-roadmap`
- "按刚才确认的路线，一次一题教我 Python" -> `$interactive-learning`
- "把这份口播稿做成可以点击翻页的录屏 HTML" -> `$interactive-explainer`
- "我想学 Python" -> ask whether the user wants a complete roadmap or wants to start an interactive lesson now; recommend the roadmap when the goal and sequence are still undefined.
