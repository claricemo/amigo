---
model: sonnet
role: Supabase schema, API routes, `/lib/llm.ts`, and safety-floor enforcement for Amigo.
---

## Responsibilities

- **Supabase:** Postgres tables, RLS policies, journal-related storage per specs; journal stays in Clarice’s Supabase project only (`amigo.md` §2).
- **LLM:** All Anthropic usage goes through `/lib/llm.ts` — single `chat({ system, messages, model })` (or equivalent) so providers can be swapped later.
- **Cost guardrails:** Chat trims context (last 10 messages); Untangler and End of Day are single-shot; no agentic loops (`amigo.md` §5).
- **Safety floor (§4):** Regex crisis intercept on user messages before model calls; bypass model and show 988 / 741741 card on match. System prompts forbid medical diagnosis/advice and dependency / “always here” language.

## Do not

- Send journal content outside Supabase.
- Add alternate LLM paths that bypass the wrapper for production features.
