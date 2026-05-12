# Vision Zero Idea

Vision Zero is an AI brain that talks directly with a human, understands the goal, and delegates the actual work to specialized agents.

The central idea is simple: the main agent should not be the thing that holds every tool, connector, memory source, and company context directly. It should stay thin. It should reason about intent, route work to the right agents, receive only the answer it asked for, and preserve its own context window for judgment.

Today, most agent systems work by giving one agent a large set of tools: file access, GitHub, Linear, Datadog, Slack, docs, memory, review tools, browser tools, and more. That makes the main agent powerful, but it also makes it expensive, noisy, and easy to overload. Even a simple question like "How many Linear tickets do I have?" can waste thousands of tokens because the main agent needs to carry tool schemas, connector context, intermediate results, and reasoning traces that do not matter to the final answer.

Vision Zero flips that model.

Instead of giving the brain direct access to every tool, it gives the brain access to other agents.

## Core Thesis

The brain agent should mainly do four things:

1. Talk with the human.
2. Understand the task.
3. Choose or create the right specialist agents.
4. Combine their answers into useful decisions.

It should not fetch Linear tickets itself. It should ask the Linear agent.

It should not inspect every file itself. It should ask the file system agent.

It should not carry every company document in its own context. It should ask the documentation agent.

It should not review its own work as the only reviewer. It should ask a senior-review agent that is built for critique.

The goal is to make the brain agent act like an adapter layer for intelligence. It should be able to connect a person to a network of agents, each with its own tools, context, permissions, model choice, and job.

## Why This Matters

The best coding and knowledge-work agents need a lot of context, but context is also the thing that makes them worse when it gets too large.

Large context windows create real problems:

- The main agent becomes slower and more expensive.
- Simple tasks consume too many tokens.
- Tool schemas compete with the user's actual goal.
- Sensitive information gets pulled into places where it may not be needed.
- The agent loses focus because it sees too much.
- Reasoning quality drops when the context is full of unrelated details.

Vision Zero should keep the main brain as small and focused as possible.

If the human asks, "How many tickets are assigned to me in Linear?", the brain should ask the Linear agent that exact question. The Linear agent can use the Linear connector, count the tickets, and return:

> You have 23 assigned tickets.

The brain does not need the whole ticket list unless the human asks for it. It does not need the Linear schema. It does not need the raw API response. It only needs the answer.

## Agent Network

Vision Zero is built around a network of specialized agents.

Examples:

- **Brain agent**: Talks to the human, plans, delegates, summarizes, and decides when to involve the human.
- **Linear agent**: Owns Linear access and can answer issue, project, and planning questions.
- **GitHub agent**: Handles repositories, pull requests, issues, branches, commits, and reviews.
- **File system agent**: Reads, writes, organizes, and explains local files with strict boundaries.
- **Documentation agent**: Indexes project docs, design docs, internal papers, runbooks, and specs.
- **Review agent**: Critiques plans, diffs, architecture, tests, and production readiness like a senior engineer.
- **Datadog agent**: Handles observability, logs, traces, dashboards, incidents, and production signals.
- **Prompt engineer agent**: Improves prompts, task briefs, tool instructions, and agent handoffs.
- **Identity agent**: Holds personal or professional profile context, preferences, work history, and stable facts.
- **Notification agent**: Decides when and how to notify the human if they are away.
- **Memory agent**: Stores and retrieves long-term useful context without flooding the brain agent.

The key is that each specialist owns a boundary. It can use whatever tools it needs inside that boundary, but the brain only receives the information needed for the current task.

## Delegation Over Direct Tool Use

Vision Zero should prefer delegation by default.

Instead of:

> Human -> Main agent -> Linear MCP -> raw issues -> reasoning -> answer

Vision Zero should do:

> Human -> Brain agent -> Linear agent -> answer

Instead of:

> Human -> Main agent with 20 tools

Vision Zero should move toward:

> Human -> Brain agent with 20 specialized agents

Each agent can still have tools. The difference is that tools are hidden behind agents that know how to use them well.

This lets the system choose the right model and reasoning budget for the job. A simple count can use a fast model with no heavy thinking. A hard architecture review can use an expensive reasoning model. A long-running coding task can be delegated to a replica or a dedicated builder agent.

## Replication And Branching

The brain should also be able to replicate itself.

If the human says:

> Build the feature, but also review the plan carefully.

The brain could create two branches of work:

- One replica focuses on implementation.
- Another replica focuses on review and critique.

Those agents can work in parallel, return their findings, and let the brain reconcile the result.

This creates a system where Vision Zero is not just one assistant taking one linear path. It can branch, compare, evaluate, and merge work back into a clear decision for the human.

## Human In The Loop

Vision Zero should know when to stop and ask for help.

It should involve the human when:

- A decision has business, security, privacy, or product impact.
- The task requires credentials or approval.
- The system detects low confidence.
- Two agents disagree in a meaningful way.
- A change could affect production systems or customer data.
- The next step would be expensive, destructive, or hard to reverse.

The brain should not pretend to be autonomous when the right move is to ask.

## Personal And Professional Brain

The long-term version of Vision Zero can become a personal and professional AI brain.

Professionally, it could know:

- Where I work.
- What teams and projects I am part of.
- Which repositories I touch.
- Which issues, pull requests, and reviews matter to me.
- What previous decisions were made and why.
- Which documents explain the systems I work on.
- What my coding standards, review preferences, and communication style are.

Personally, it could eventually know more about my preferences, routines, priorities, and goals, but that needs to be designed carefully with privacy and security as first-class concerns.

The practical first version should focus on coding and technical work.

## Main Use Case

The first user is me.

I work at Vercel and build AI agents. I want Vision Zero to help me code better, review better, plan better, and avoid wasting context on tasks that should be delegated.

The product should start as a tool for one technical user, then expand toward teams.

The company-level version would let people create and use mini agents inside their organization. A company could eventually "hire" a Vision Zero agent that acts like a full-time technical teammate:

- It communicates clearly.
- It delegates work to the right agents.
- It opens and reviews pull requests.
- It checks its own work.
- It runs tests.
- It asks for human help when needed.
- It remembers project context without leaking it everywhere.

## Evaluation First

This needs to be built carefully.

The goal is not just to make a cool agent router. The goal is to prove that delegation improves results.

Vision Zero should be evaluated at every step:

- Does delegation reduce token usage?
- Does it improve answer quality?
- Does it reduce context pollution?
- Does it make simple tasks faster?
- Does it make hard tasks more reliable?
- Does it preserve privacy boundaries better than one large agent?
- Does it know when to ask the human for help?
- Does it choose the right model for the task?
- Does it improve coding outcomes compared to a single-agent baseline?

Every major feature should have a benchmark or evaluation attached to it. If a routing strategy sounds good but does not improve results, it should be changed.

## Product Direction

Vision Zero should become an AI brain for technical work first.

The first strong version should help with:

- Coding tasks.
- Code review.
- Project documentation.
- GitHub and Linear workflows.
- Internal technical knowledge.
- Agent delegation.
- Model selection.
- Context management.
- Human approval points.

Later, the same architecture can support sales, marketing, content creation, operations, and personal productivity. But the first wedge should be coding and internal technical work for people and teams that already live inside tools like GitHub, Linear, Slack, Datadog, and docs.

## The Desired Feeling

Vision Zero should feel like talking to one focused brain that knows how to get help.

The human should not need to think about which tool to call, which connector to use, which model is appropriate, or which context source matters. The human should describe the goal. The brain should handle the delegation.

The result should be:

- Less context waste.
- Better specialization.
- Better privacy boundaries.
- Better coding outcomes.
- Better reviews.
- Better long-running work.
- Better human control.

Vision Zero is the attempt to build an AI brain from first principles: one that does not try to be every tool at once, but knows how to coordinate the right intelligence at the right time.
