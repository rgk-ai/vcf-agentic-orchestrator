# VCF Agentic Orchestrator

A working orchestrator agent that manages VMware Cloud Foundation tenant lifecycle through natural language. Built as the reference implementation for a four-part blog series on [rgk-ai.github.io](https://rgk-ai.github.io/posts/).

## What this is

An LLM-driven orchestrator (Claude) that takes a natural-language tenant onboarding request, decomposes it into a plan, and coordinates four domain sub-agents — tenant, networking, compute, day 2 — each of which calls an MCP server that wraps a mock VCF API.

## Architecture
User prompt 
     ↓
Orchestrator (Claude) 
   ↓ structured handoffs 
┌──┴──--┬─────────┬─────────┐ 
Tenant  Net    Compute 	 Day 2   ← domain sub-agents 
↓ 	↓	↓ 	↓ 
MCP servers (one per domain) 
↓ 	↓ 	↓ 	↓ 
Mock VCF APIs (FastAPI)
## Status

Work in progress. See the blog series for context:

- [Post 0a: From POC to Production](https://rgk-ai.github.io/posts/from-poc-to-production/)
- [Post 0b: Why GSIs and CSPs Need Agentic AI](https://rgk-ai.github.io/posts/why-gsis-csps-need-agentic-ai/)
- Post 1: Building an orchestrator agent for real infrastructure *(coming soon)*
- Post 2: MCP server design for platform APIs *(coming soon)*
- Post 3: How do I know my agent actually works? *(coming soon)*
- Post 4: What broke, what I'd change, what I learned *(coming soon)*

## Running it

Requires Python 3.11+, `uv`, and an Anthropic API key.

```bash
uv venv && source .venv/bin/activate
uv sync
cp .env.example .env  # then add your ANTHROPIC_API_KEY
python demo/demo.py
```

## License

MIT. See LICENSE.

## About

Built by [Raj Kuchimanchi](https://linkedin.com/in/kbrajgopal), a Solutions Architect at Broadcom (VMware) focused on the intersection of enterprise infrastructure and agentic AI.
