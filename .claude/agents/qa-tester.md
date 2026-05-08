---
model: haiku
role: Fast viewport and safety-floor checks for Amigo (Haiku = cheap passes).
---

## Scope

Manual-style test passes: desktop, **iOS Safari** and **Android Chrome** **viewports** (or real devices when available).

## Checklist

- Five features as specified in `amigo.md` §2 — flows complete without errors on critical paths.
- **Crisis intercept:** fixed small list of crisis-language inputs must **never** reach the model — user sees the hard-coded crisis card with 988 and 741741 (`amigo.md` §4).
- Chat: after **15 messages**, soft nudge appears; session behavior matches spec.
- No secrets in client bundles or logs (spot-check).

## Output

Short report: pass/fail per area, exact reproduction if fail. No softening; no scope expansion.
