# TB Joshua – Quotable Quotes

A searchable collection of quotes by TB Joshua, hosted on GitHub Pages.

**Live site:** https://etomaa.github.io/tb-joshua-quotes/

---

## Local Setup

Clone the repo (first time only):

```powershell
git clone https://github.com/etomaa/tb-joshua-quotes.git
cd tb-joshua-quotes
```

If the remote URL needs your PAT (for push access):

```powershell
# Read PAT from .env and set remote URL
$pat = ((Get-Content ".env" | Where-Object { $_ -match "GITHUB_PAT=" }) -split "=", 2)[1].Trim()
git remote set-url origin "https://etomaa:$pat@github.com/etomaa/tb-joshua-quotes.git"
```

The `.env` file lives at the root of the project and is never committed:

```
GITHUB_PAT=ghp_yourTokenHere
```

---

## Editing Workflow

All changes go through the local file — never edit directly on GitHub.

1. Open `index.html` and make your changes (add quotes, fix typos, update styles, etc.)
2. Stage the file:
   ```powershell
   git add index.html
   ```
3. Commit with a clear message describing **what** changed and **why**:
   ```powershell
   git commit -m "Add quotes #557-560 on prayer and faith"
   ```
4. Push to GitHub:
   ```powershell
   git push origin main
   ```

---

## Adding Quotes

Quotes live in the JavaScript array inside `index.html`. Each entry follows this pattern:

```js
{id:557, text:"Your quote text here."},
```

After adding quotes, update the count in these three places in `index.html`:

| Location | Example |
|---|---|
| Quote counter display | `<strong id="vc">556</strong> quotes` |
| Go-to input placeholder & max | `placeholder="1–556" min="1" max="556"` |
| Footer text | `551 Quotes` → `556 Quotes` |
| JS validation in `goTo()` | `if(!v\|\|v<1\|\|v>556)` |
| JS hash navigation | `if(id>=1&&id<=556)` |

---

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire app — quotes, styles, and scripts |
| `.env` | Local only. Stores `GITHUB_PAT` for push authentication. Never committed. |
| `.gitignore` | Excludes `.env` and any local working copies |
