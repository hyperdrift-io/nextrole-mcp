# NextRole — MCP Server

> Résumé & job-search tools for AI agents: **ATS check, CV-vs-role score, live role search, JD fetch, and CV tailoring.** Turn a CV into interview callbacks.

This repo is the public discovery surface for the **NextRole** MCP server. The server itself is a hosted, remote service — there is nothing to install.

- **Endpoint:** `https://nextrole.site/api/mcp` — remote, streamable-HTTP, stateless, **anonymous** (no auth, no API key, works on the first call)
- **Website:** https://nextrole.site
- **Registry:** `io.github.hyperdrift-io/nextrole`

## Tools

| Tool | What it does | LLM |
|------|--------------|-----|
| `ats_lint` | Free, deterministic ATS check — flags banned symbols, first-person/passive phrasing, non-standard headers, unquantified bullets, each with a one-click autofix | No |
| `score_cv` | Scores a CV against a specific role — overall match, per-dimension scores, gaps, and the single top priority to fix | Yes |
| `find_roles` | Searches live job listings (Reed + Adzuna) by role/location query | No |
| `fetch_job_spec` | Pulls a clean job description from a posting URL, ready to score or tailor against | No |
| `tailor_cv_to_role` | Rewrites a CV for a target job using a multi-pass tailor→critic engine | Yes |

The tools chain into a job-search arc agents can run end to end: **find roles → fetch a JD → score fit → tailor.** Every result links back to nextrole.site to save, track applications, and refine. Results stay grounded in the CV you provide — nothing is invented.

## Connect

Add the remote server in any MCP-capable client (Claude, ChatGPT, Cursor, Cline, VS Code, …) using the endpoint and **Streamable HTTP** transport.

Claude Code:

```bash
claude mcp add --transport http nextrole https://nextrole.site/api/mcp
```

## Example prompts

- "Run an ATS check on my CV and fix the issues." → `ats_lint`
- "Find product manager roles in London." → `find_roles`
- "Pull this job posting and score my CV against it." → `fetch_job_spec` + `score_cv`
- "Tailor my CV to this job description." → `tailor_cv_to_role`

## About

Built by [Hyperdrift](https://hyperdrift.io). NextRole is a job-search companion — it turns your real CV into a role-specific application and helps you move your search forward.
