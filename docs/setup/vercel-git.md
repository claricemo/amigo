# Vercel: connect a Git repository

Use Vercel’s Git integration so pushes to GitHub trigger deployments.

## Quick link

**Connect / import a Git repository:** [https://vercel.link/git](https://vercel.link/git)

That opens the flow to link GitHub (or GitLab / Bitbucket) and pick a repo.

## Canonical repository

- **HTTPS:** `https://github.com/claricemo/amigo.git`
- **Web:** [github.com/claricemo/amigo](https://github.com/claricemo/amigo)

If **Connect** fails for a **private** repo, grant the **Vercel** GitHub App access to `claricemo/amigo` under GitHub → **Settings** → **Applications** → **Installed GitHub Apps** → **Vercel** → **Configure** → repository access.

## Amigo

1. Sign in at [vercel.com](https://vercel.com).
2. Use [https://vercel.link/git](https://vercel.link/git) (or **Add New → Project → Import Git Repository**).
3. Choose **`claricemo/amigo`** (or select your fork).
4. Framework preset **Next.js**, branch **`main`**, then **Deploy**.
5. Confirm **Production** shows **Hello Amigo**; optional: open the `.vercel.app` URL on your phone (Phase 0 gate in `amigo.md`).

No env vars are required for the current static home page.
