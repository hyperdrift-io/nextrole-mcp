# NextRole — MCP Server

> **NextRole is a job-search companion** — tailor your CV to a role, score fit, and fix ATS issues at [nextrole.site](https://nextrole.site). It is also available to AI agents via this MCP server.

This repo is the public discovery surface for the **NextRole** MCP server. The server itself is a hosted, remote service — there is nothing to install.

- **Endpoint:** `https://nextrole.site/api/mcp` — remote, streamable-HTTP, stateless, **anonymous** (no NextRole API key; usage limits apply)
- **Website:** https://nextrole.site
- **Registry:** `io.github.hyperdrift-io/nextrole`

## Tools

| Tool | What it does | LLM |
|------|--------------|-----|
| `ats_lint` | Deterministic CV checks — returns flagged symbols, phrasing, headers and unquantified bullets for review | No |
| `score_cv` | Reviews a CV against a role — 1–10 fit scores, strengths, gaps, and a priority to improve | Yes |
| `find_roles` | Searches live job listings (Reed + Adzuna) by role/location query | No |
| `fetch_job_spec` | Pulls a clean job description from a posting URL, ready to score or tailor against | No |
| `tailor_cv_to_role` | Rewrites a CV for a target job using a multi-pass tailor→critic engine | Yes |

The tools chain into a job-search arc agents can run end to end: **find roles → fetch a JD → score fit → tailor.** Every result links back to nextrole.site to save, track applications, and refine. Review the returned suggestions against your real experience before using them. Fit scores are guidance; hiring outcomes remain unmeasured.

## Connect

Use a client that supports remote MCP servers over **Streamable HTTP**. Connection availability and permissions depend on the client and account. Start with a synthetic CV to check the connection before providing personal information.

Claude Code:

```bash
claude mcp add --transport http nextrole https://nextrole.site/api/mcp
```

## Example prompts

- "Check my CV and explain the findings so I can review them." → `ats_lint`
- "Find product manager roles in London." → `find_roles`
- "Pull this job posting and score my CV against it." → `fetch_job_spec` + `score_cv`
- "Tailor my CV to this job description." → `tailor_cv_to_role`

## About

Built by [Hyperdrift](https://hyperdrift.io). NextRole is a job-search companion — it turns your real CV into a role-specific application and helps you move your search forward.

For product owners: [see this integration and Orchestra’s offering](https://ai.hyperdrift.io/work#work-nextrole) for making an existing product usable through agents. NextRole remains the career product; Orchestra handles implementation enquiries.
