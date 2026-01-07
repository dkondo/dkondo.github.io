# Agentic Context Engineering (ACE) as LangGraph Middleware

**Date:** January 7, 2026  
**Status:** Work in Progress

---

Adds ACE (Agentic Context Engineering) middleware that enables agents to self-improve through an evolving playbook.

Implementation was Claude assisted.

## Features:

- Reflector analyzes agent response correctness, reasoning trajectories, and tags playbook bullets as helpful/harmful
- Curator periodically adds new insights to the playbook based on reflections
- Based on the paper: *Agentic Context Engineering* and original Implementation: [github.com/ace-agent/ace](https://github.com/ace-agent/ace)

## New features compared to base implementation:

- Support reflection/curation in each interaction in the react loop
- Drop "stale" bullets when max context size exceeds max threshold. Measure freshness of bullets by harmful and helpful counts. Ensure new bullets are not dropped due to recency bias.

