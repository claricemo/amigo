# GitHub: remote and first push (manual)

Use this if `gh` is not logged in or `git push` fails.

## 1. One-time login (pick one)

**Browser (easiest)**

```powershell
gh auth login -w -p https -h github.com
```

Complete the browser flow. Verify:

```powershell
gh auth status
```

**Token (headless / CI)**

Create a classic PAT with `repo` scope (GitHub → Settings → Developer settings → Personal access tokens).

```powershell
$env:GH_TOKEN = "ghp_xxxxxxxx"   # session only; do not commit
gh auth login --with-token
# paste token, Enter, Ctrl+Z, Enter on Windows PowerShell
```

Or set `GH_TOKEN` for the session and use `gh` commands.

## 2. Fix `origin` if it still points at a placeholder

Check:

```powershell
cd E:\Amigo
git remote -v
```

If the URL contains `<your-user>`, set your real repo URL:

```powershell
git remote set-url origin https://github.com/YOUR_GITHUB_USERNAME/Amigo.git
```

## 3. Create the repo and push this branch

**Option A — GitHub CLI (creates repo and remote)**

```powershell
cd E:\Amigo
git remote remove origin   # only if origin is wrong or duplicate
gh repo create Amigo --private --source=. --remote=origin --push
```

If the repo already exists on GitHub, only add remote and push:

```powershell
git remote add origin https://github.com/YOUR_GITHUB_USERNAME/Amigo.git
git push -u origin cursor/amigo-rules-and-claude-md
```

**Option B — Create empty repo on github.com**

Create a private repo named `Amigo`, then:

```powershell
cd E:\Amigo
git remote set-url origin https://github.com/YOUR_GITHUB_USERNAME/Amigo.git
git push -u origin cursor/amigo-rules-and-claude-md
```

## 4. Pre-push secret check (Amigo rule)

```powershell
git diff --staged | Select-String -Pattern "sk-|anthropic|supabase.*key|password" -CaseSensitive:$false
```

If anything matches, fix before pushing.
