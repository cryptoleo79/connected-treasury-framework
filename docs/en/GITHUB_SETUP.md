# GitHub Publication & Hosting Guide

**How to take this packet from a folder on your computer to a live, shareable, multilingual website that the Cardano community can engage with.**

---

## What you'll have when you're done

- A GitHub repository at `https://github.com/YOUR_HANDLE/connected-treasury-framework`
- A live simulator at `https://YOUR_HANDLE.github.io/connected-treasury-framework/`
- Markdown documents rendered natively on GitHub for forum links
- A structure ready for Japanese translation via Claude Code
- A canonical URL to share on the Cardano Forum, X/Twitter, and Discord

Total setup time: **15–30 minutes** if you're comfortable with GitHub, **45–60 minutes** if it's your first time.

---

## Step 1: Create the repository

### Option A: Via the GitHub web UI (easiest, no terminal required)

1. Go to https://github.com/new
2. Repository name: `connected-treasury-framework` (or `ctf-cardano`, or whatever feels right)
3. Description: *"A self-sustaining treasury model for Cardano — proposal packet, simulator, and CIP outline"*
4. Public visibility
5. Check "Add a README file" (you'll replace it in a moment)
6. Add a license: **MIT** is recommended (most permissive, ecosystem standard)
7. Click "Create repository"

### Option B: Via terminal (faster if you're set up)

```bash
gh repo create connected-treasury-framework --public --description "A self-sustaining treasury model for Cardano" --add-readme --license MIT
git clone https://github.com/YOUR_HANDLE/connected-treasury-framework.git
cd connected-treasury-framework
```

---

## Step 2: Lay out the file structure

Inside the repo, organize files like this:

```
connected-treasury-framework/
├── README.md                    # English landing page (replaces auto-generated)
├── README.ja.md                 # Japanese landing page
├── LICENSE                      # MIT (auto-generated)
├── index.html                   # The simulator — served at the root URL
├── docs/
│   ├── en/
│   │   ├── 01_report.md
│   │   ├── 02_proposal.md
│   │   ├── 02b_proposal_lite.md
│   │   ├── 03_cip.md
│   │   ├── 05_objections.md
│   │   ├── 06_hostile_review.md
│   │   └── 07_twitter_thread.md
│   └── ja/
│       └── (translated versions, added via Claude Code)
├── .github/
│   └── ISSUE_TEMPLATE/
│       ├── objection.md         # Template for community-submitted objections
│       └── improvement.md       # Template for framework improvements
└── CONTRIBUTING.md              # How to propose changes
```

**Critical detail:** `index.html` at the repo root is what GitHub Pages will serve as the live simulator. Rename `index.html` to `index.html` when you upload it.

### Upload the files

**Via web UI:**
1. Click "Add file" → "Upload files" in your repo
2. Drag-and-drop the entire `ctf_packet` folder
3. Rename `index.html` to `index.html` (use GitHub's web editor or just rename locally first)
4. Move the markdown files into `docs/en/`
5. Commit

**Via terminal:**
```bash
# Assuming you're in the cloned repo directory:
cp /path/to/ctf_packet/index.html ./index.html
mkdir -p docs/en docs/ja
cp /path/to/ctf_packet/01_report.md docs/en/
cp /path/to/ctf_packet/02_proposal.md docs/en/
cp /path/to/ctf_packet/02b_proposal_lite.md docs/en/
cp /path/to/ctf_packet/03_cip.md docs/en/
cp /path/to/ctf_packet/05_objections.md docs/en/
cp /path/to/ctf_packet/06_hostile_review.md docs/en/
cp /path/to/ctf_packet/07_twitter_thread.md docs/en/
cp /path/to/ctf_packet/00_README.md README.md  # rename for GitHub convention

git add .
git commit -m "Initial packet: framework, proposal, CIP, simulator, objections"
git push
```

---

## Step 3: Enable GitHub Pages

1. In your repo, go to **Settings** → **Pages** (left sidebar)
2. Under "Build and deployment":
   - **Source:** Deploy from a branch
   - **Branch:** `main` (or `master`, whatever yours is called)
   - **Folder:** `/ (root)`
3. Click **Save**
4. Wait 1–2 minutes for the first deployment

Your simulator is now live at:

**`https://YOUR_HANDLE.github.io/connected-treasury-framework/`**

This is the URL you'll share everywhere. Test it. The simulator should load with the four sliders and the projection chart, and you should be able to interact with it.

---

## Step 4: Update internal links

In the repository, any link pointing to `index.html` should now point to either `index.html` (the live URL) or just `/` (the root).

Update the README.md and any other docs that reference the simulator file:

```markdown
- Old: see `index.html`
- New: try the [interactive simulator](https://YOUR_HANDLE.github.io/connected-treasury-framework/)
```

The README.md is the most important file to update — it's what people see when they visit the GitHub repo URL.

---

## Step 5: Japanese translation via Claude Code

The `docs/ja/` directory is your translation target. Use Claude Code to translate the English markdown files into Japanese.

### Recommended workflow

From your terminal, in the repo directory:

```bash
# Open Claude Code
claude

# Then ask Claude Code:
"Translate docs/en/01_report.md into natural, professional Japanese 
suitable for the Cardano DRep community. 
Preserve all markdown formatting, tables, and technical terms 
(ADA, Pyth, USDCx, DRep, etc.) in their original form. 
Save the result to docs/ja/01_report.md."
```

Repeat for each file. Claude Code will read the source, translate, and write the output. After each translation, commit:

```bash
git add docs/ja/01_report.md
git commit -m "Add Japanese translation of report"
git push
```

### Translation order (high impact first)

1. `README.md` → `README.ja.md` (front page — every Japanese visitor sees this first)
2. `docs/en/07_twitter_thread.md` → `docs/ja/07_twitter_thread.md` (already has Japanese — just verify and refine)
3. `docs/en/02_proposal.md` → `docs/ja/02_proposal.md` (the actionable piece)
4. `docs/en/01_report.md` → `docs/ja/01_report.md` (the long-form context)
5. `docs/en/05_objections.md` → `docs/ja/05_objections.md` (the debate-defense document)
6. The rest as time allows

### Pro tip

Add a small note at the top of every translated file:

```markdown
> 🌐 This document was translated with the help of AI. 
> The English version is authoritative. 
> Please report translation issues via GitHub issues.
> 
> 🌐 この文書はAIの支援を受けて翻訳されました。
> 英語版が正本です。
> 翻訳の問題はGitHubのissuesで報告してください。
```

This sets expectations honestly and invites correction from native speakers.

---

## Step 6: Polish the README

The README.md is your front door. It should:

1. Open with a one-sentence pitch
2. Link prominently to the live simulator
3. Link to each document with a one-line description
4. Include a "Languages" section listing English and 日本語
5. Have a clear "How to engage" section (forum link, X thread, GitHub issues)

The `00_README.md` in your packet is already structured this way. Just update it to use the live URLs after Pages deploys.

---

## Step 7: Cardano Forum post

Once the repo is live, create the Cardano Forum thread:

1. Go to https://forum.cardano.org/
2. Category: "Catalyst" or "Governance" depending on your framing
3. Title: *"The Connected Treasury Framework — a proposal packet for community review"*
4. Body: paste the English `README.md` directly (forum supports markdown)
5. Include the live simulator URL prominently
6. Tag relevant DReps, the Cardano Foundation account, and Intersect

**Forum etiquette:** post once, link from X/Discord *to the forum thread*. Don't fragment the discussion across platforms.

---

## Step 8: Cross-posting checklist

In order of priority:

| Where | What | When |
|---|---|---|
| Cardano Forum | Full README post with packet link | Day 1 |
| X/Twitter (English) | Thread from `07_twitter_thread.md` | Day 1, 14:00 UTC |
| X/Twitter (Japanese) | Translated thread | Day 1, 10:00 JST |
| r/cardano | Link to forum thread, short summary | Day 2 |
| Discord (Cardano server) | Link to forum thread, brief context | Day 2 |
| Telegram (Cardano channels) | Link to forum thread, brief context | Day 2 |
| Japan Cardano community | Translated forum post or direct outreach | Day 3 |
| Intersect | Direct submission notification | Day 4 if engagement is strong |

---

## Step 9: Maintain the conversation

The repository's `.github/ISSUE_TEMPLATE/` directory is where the community will surface objections, improvements, and questions. Create these two templates:

**`.github/ISSUE_TEMPLATE/objection.md`:**
```markdown
---
name: Substantive objection
about: Argue against the framework with a specific concern
title: '[OBJECTION] '
labels: objection
---

## What you're objecting to
(Quote or reference the specific claim, component, or section.)

## Your argument
(One or two paragraphs of substantive critique.)

## What would change your view
(What would the proposer need to demonstrate or change?)
```

**`.github/ISSUE_TEMPLATE/improvement.md`:**
```markdown
---
name: Framework improvement
about: Propose a change to the framework's mechanics
title: '[IMPROVEMENT] '
labels: enhancement
---

## What you'd change
## Why
## Trade-offs
```

These turn the GitHub issues page into a structured debate ledger that survives the Forum thread's chronological drift.

---

## Optional: Custom domain

If you want a cleaner URL than `YOUR_HANDLE.github.io/connected-treasury-framework`:

1. Buy a domain (e.g., `connected-treasury.org`, `cardano-ctf.com`) from any registrar (~$10/year)
2. In repo Settings → Pages → Custom domain, enter the domain
3. At your DNS provider, add a CNAME record pointing the domain to `YOUR_HANDLE.github.io`
4. Wait 5–60 minutes for DNS propagation
5. Enable "Enforce HTTPS" once GitHub provisions the certificate

This is optional. The `*.github.io` URL works perfectly well.

---

## Optional: IPFS mirror for permanence

To ensure the packet survives even if GitHub goes down:

1. Install `ipfs` CLI or use https://app.fleek.co/ for a hosted IPFS pinning service
2. Upload the entire repo to IPFS
3. The IPFS hash becomes a permanent address (`ipfs://bafy...`)
4. Add the hash to your README so it's findable

The Cardano community is unusually IPFS-aware and will appreciate the permanence signal.

---

## Troubleshooting

**Simulator doesn't load on GitHub Pages:**
- Check that `index.html` is at the repo root, not in a subfolder
- Verify GitHub Pages is enabled and source is set to `/ (root)`
- Check the Actions tab for build errors
- Open browser DevTools console to check for resource load errors

**Charts.js fails to load:**
- The simulator uses `https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js` — verify this URL is reachable from your network
- If you need to self-host: download the chart.umd.js file and place it next to index.html, then update the `<script src=...>` reference

**Japanese characters display incorrectly:**
- Verify `<meta charset="UTF-8">` is present in `index.html` (it is, by default)
- Ensure your markdown files are saved as UTF-8 (most editors default to this)

**README.md doesn't render properly on GitHub:**
- GitHub uses GitHub Flavored Markdown — most CommonMark works
- Tables, code blocks, lists, headings all render natively
- HTML inside markdown is partially supported (no scripts, no styles)

---

## Quick command summary

```bash
# Clone after creating repo on GitHub
git clone https://github.com/YOUR_HANDLE/connected-treasury-framework.git
cd connected-treasury-framework

# Set up structure
mkdir -p docs/en docs/ja .github/ISSUE_TEMPLATE

# Copy files (adjust paths)
cp /path/to/ctf_packet/index.html ./index.html
cp /path/to/ctf_packet/00_README.md ./README.md
cp /path/to/ctf_packet/0[1-7]*.md docs/en/

# Update README link references (use sed or your editor)
sed -i 's/index.html/index.html/g' README.md docs/en/*.md

# Commit and push
git add .
git commit -m "Initial Connected Treasury Framework packet"
git push

# Then enable GitHub Pages in repo Settings → Pages → main / root
```

After this, your simulator is live and shareable in under 5 minutes.

---

## Final checklist before announcing

- [ ] Simulator loads at `YOUR_HANDLE.github.io/connected-treasury-framework/`
- [ ] All four sliders work and update the chart in real time
- [ ] README.md displays correctly on github.com with working links
- [ ] All documents in `docs/en/` open and render
- [ ] At least Japanese README (`README.ja.md`) is translated
- [ ] LICENSE file is present
- [ ] Issue templates are set up
- [ ] Cardano Forum thread is drafted (not yet posted)
- [ ] X/Twitter thread is drafted (not yet posted)

When all eight are checked, ship.
