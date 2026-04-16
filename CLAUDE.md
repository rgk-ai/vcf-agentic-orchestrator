# VCF Agentic Orchestrator — Claude Code context

## Project
An orchestrator agent that manages VCF (VMware Cloud Foundation) tenant lifecycle through natural language. Demonstrates production-grade agentic patterns for enterprise infrastructure: orchestrator + domain sub-agents + MCP servers over real-shaped APIs.

## Goals (in priority order)
1. Working end-to-end demo for a realistic tenant-onboarding scenario
2. MCP server design that could plausibly wrap real VCF Automation / NSX / vSphere / Aria Operations APIs
3. Eval harness that measures correctness, tool-call quality, and failure modes — not just "did it work once"
4. Codebase readable by a senior engineer in 20 minutes

## Conventions
- Python 3.11+, type hints everywhere, `ruff` for lint
- MCP servers use the official `mcp` Python SDK
- Mock APIs are FastAPI, return shapes modeled on real VCF Automation 9.x API responses
- All tool calls logged to SQLite with request_id, timestamp, input, output, latency
- ADRs in `docs/decisions/` for every non-obvious design choice
- Never commit API keys; use `.env` + `python-dotenv`

## Non-goals
- Not building a real VCF integration (mocks only)
- Not building a UI (CLI + logs are enough)
- Not supporting models other than Claude (this is intentional — post is about Claude)

## Style
- Functions over classes where reasonable
- Explicit over implicit; a senior SA reader should understand without running it
- Comments explain *why*, not *what*
- Use Pydantic models for all inter-agent handoff contracts
