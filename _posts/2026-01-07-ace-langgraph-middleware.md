---
layout: post
title: "Stanford's Agentic Context Engineering (ACE) as LangGraph Middleware"
date: 2026-01-07
excerpt: "I was inspired to enable ACE in popular agentic frameworks LangChain v1 and LangGraph by implementing it as a middleware, ie, a simple agent abstraction."
---

I recently heard a talk about ACE (Agentic Context Engineering) developed at Stanford.  This technique enables agents to self-improve, treating context as an evolving playbook that accumulates and refines strategies through a process of reflection and curation.  

More details from the Stanford paper here: [Agentic Context Engineering: Evolving Contexts for Self-Improving Language Models](https://arxiv.org/abs/2510.04618)

I was inspired to enable ACE in popular agentic framework LangChain v1 / LangGraph by implementing it as a "middleware", ie, a simple agent abstraction.

With ACE as middelware, one can easily enable any agent to use ACE with a simple parameter `[ace]` parameter:

```python
agent: Any = create_agent(
    model="gpt-4.1",
    tools=[calculator],
    middleware=[ace],
    checkpointer=checkpointer,
)
```

An initial implementation is here: [PR #34405: langchain-ai/langchain](https://github.com/langchain-ai/langchain/pull/34405)

This implements implements the following

1. A reflector that analyzes agent response correctness, reasoning trajectories, and tags playbook bullets as helpful/harmful
2. A curator that periodically adds new insights to the playbook based on reflections

These entities work in the background using wrappers and hooks provided by LangChain v1's middleware.

Any feedback is welcome, and hope it helps.
