# Translating the CTF Packet with Claude Code

**How to use Claude Code to translate the framework documents into Japanese (or any other language) while preserving formatting, technical terms, and tone.**

---

## Why this matters

Japanese DReps were the bloc that rejected the IOG Vision 2026 research proposal this week. Reaching them in Japanese isn't optional — it's strategically essential. The same logic applies to Korean, Spanish, and Portuguese audiences if you want broader engagement.

This guide gives you Claude Code prompts that produce reliable translations with minimal manual cleanup.

---

## Setup

You need:

- Claude Code installed (`claude` command available in your terminal)
- The CTF packet in a local directory
- ~10 minutes per document

Open Claude Code in your project directory:

```bash
cd /path/to/connected-treasury-framework
claude
```

---

## Master translation prompt

This is the prompt to paste into Claude Code for each document. Replace `01_report.md` with the file you're translating.

```
Translate docs/en/01_report.md into natural, professional Japanese.
Save the result to docs/ja/01_report.md.

Translation rules:

1. Preserve all markdown formatting exactly: headings, tables, code blocks, 
   lists, bold/italic emphasis, blockquotes, horizontal rules.

2. Do NOT translate the following technical terms — keep them in the 
   original form:
   - Project and product names: Cardano, ADA, USDCx, USDM, USDA, iUSD, 
     BTC, Bitcoin, Pyth Network, Snek Foundation, Cardano Foundation, 
     IOG, Input Output, Emurgo, Intersect, Midnight Foundation, 
     Draper Dragon, Circle, xReserve, CCTP
   - Governance terms: DRep, SPO, CIP, NCL, Net Change Limit, 
     Treasury Withdrawal, Info Action, Constitutional Committee, 
     Pentad, Voltaire, Plomin, Chang, Leios, Hydra, Mithril, Ouroboros
   - Technical: APY, TVL, DeFi, LMDB, CDDL
   - Numbers and units: 1.621B ADA, $389M, 4%, etc.
   - Greek letters in formulas: ρ, τ
   - Roman/Greek-origin SI: Q3 2033, etc.

3. For "Connected Treasury Framework (CTF)", use 
   「Connected Treasury Framework(CTF)」 (with full-width parentheses 
   in Japanese context).

4. Use sentence-case translations — do NOT use overly formal keigo (敬語) 
   unless the source is overly formal. Match the source's register.

5. For currency:
   - "ADA" stays "ADA"
   - "$389M" stays as-is (or render as "3億8,900万ドル" if context is 
     consumer-facing)
   - "M ADA" can stay or be rendered as "百万ADA"

6. For dates: render as "2026年5月26日" format in body text, 
   keep "Q3 2033" format in technical tables.

7. Add this notice at the top of the translated file 
   (after the title heading):

   > 🌐 この文書はAIの支援を受けて翻訳されました。
   > 英語版が正本です。翻訳の問題はGitHubのissuesで報告してください。

8. Preserve all hyperlinks and URLs unchanged.

9. For Japanese-original concepts that appear in the source 
   (omotenashi, musubi, tsunagi, etc.), use the original Japanese 
   characters with romaji in parentheses: おもてなし (omotenashi).

10. Maintain the same paragraph structure and line breaks as the source.

Output: write the complete translated document to docs/ja/01_report.md.
After writing, give me a brief summary of any translation decisions you 
made that were non-obvious, so I can review.
```

---

## Translation order (high-impact first)

Translate in this order. The earlier files reach more readers and inform 
the translation of later ones.

| Order | File | Reason |
|---|---|---|
| 1 | `README.md` → `README.ja.md` | Front page; every visitor sees this first |
| 2 | `docs/en/07_twitter_thread.md` | Already partially translated; verify and refine |
| 3 | `docs/en/02_proposal.md` | The submission proposal itself |
| 4 | `docs/en/02b_proposal_lite.md` | Foot-in-door variant |
| 5 | `docs/en/01_report.md` | The long-form context |
| 6 | `docs/en/05_objections.md` | Debate-defense |
| 7 | `docs/en/06_hostile_review.md` | Single-voice attack |
| 8 | `docs/en/03_cip.md` | Technical document (smaller audience) |

After each translation, run a quick review:

```
Read docs/ja/01_report.md and identify:
1. Any English text that wasn't translated (other than the preserved 
   technical terms listed in the translation rules)
2. Any markdown formatting that broke
3. Any places where the Japanese feels awkward or overly literal
Suggest fixes inline.
```

---

## Special cases

### The simulator (`index.html`)

The simulator is already bilingual via the EN/日本語 toggle button in the 
top-right corner. No translation needed for the UI itself.

If you want to refine the Japanese strings in the simulator:

```
Open index.html and find the `i18n.ja` object in the <script> section.
Review each translated string for naturalness and Cardano-community 
terminology accuracy. Update strings that feel awkward or technically 
incorrect. Do not change keys, only values.
```

### The Twitter thread

The Japanese thread in `docs/en/07_twitter_thread.md` was generated as a 
starter. Have Claude Code review it:

```
Read docs/en/07_twitter_thread.md, focus on the Japanese thread section.
For each Japanese tweet:
1. Verify character count fits within Twitter's limit 
   (Japanese tweets allow ~280 chars but Japanese chars often count as 2)
2. Check that the tone matches typical Cardano-Japanese-community Twitter
3. Verify all technical terms are correctly preserved
4. Flag any tweets that should be split or condensed
Output the refined Japanese thread.
```

---

## Quality checks before publishing translations

After Claude Code produces a translation, verify:

1. **Markdown integrity:** Open the translated file in a markdown 
   previewer (GitHub's web UI works) and confirm tables, code blocks, 
   and headings render correctly.

2. **Technical term consistency:** Run a grep to make sure preserved 
   terms appear exactly as expected:

   ```bash
   grep -c "Cardano" docs/ja/01_report.md
   grep -c "DRep" docs/ja/01_report.md
   grep -c "USDCx" docs/ja/01_report.md
   ```

   These counts should be similar to the English source.

3. **Native speaker review (optional but recommended):** Post the 
   translated README to a Cardano Japan Discord or Telegram channel 
   and ask for native-speaker feedback before announcing widely. 
   Frame it as "AI-assisted translation, looking for native review."

4. **Language attribute:** Confirm that every `.ja.md` file has 
   the AI-translation disclaimer notice at the top (the master prompt 
   includes this automatically).

---

## Beyond Japanese

The same workflow translates to any language. Change the prompt's first 
sentence and target language. Suggested priority order:

1. **Japanese** (this guide) — largest non-English Cardano voting bloc
2. **Korean** (한국어) — active Cardano community
3. **Spanish** (español) — significant LATAM presence
4. **Portuguese** (português) — Brazil's Cardano activity is growing
5. **Mandarin Chinese** (中文) — significant institutional interest

Use the same master prompt template, substituting language-appropriate 
preservation rules and disclaimers.

---

## Cost and time

Translating the full packet (six documents, ~10,000 words) takes Claude 
Code approximately 15–30 minutes of total processing time, depending 
on document length. The longest single document (01_report.md at ~3,500 
words) takes 3–5 minutes per language.

If you're paying per token, expect each full-packet translation to cost 
on the order of $1–3 per language. The strategic value of reaching the 
Japanese DRep bloc far exceeds this cost.

---

## When to publish each language

Recommended sequence:

| Day | Action |
|---|---|
| 0 | Publish English packet, enable GitHub Pages |
| 1 | Translate and commit Japanese README + simulator strings |
| 2 | Translate proposal + report, post Japanese forum thread |
| 3-5 | Translate remaining documents |
| 6+ | Solicit native speaker corrections via GitHub issues |

This gives the English version a 24-hour head start (most Cardano 
discussion is initially English) while ensuring the Japanese 
community has access within 48 hours.

---

## Maintenance

When you update an English document, flag the corresponding Japanese 
version for re-translation:

```
docs/en/01_report.md was updated on YYYY-MM-DD.
Compare against docs/ja/01_report.md and update the Japanese version 
to match. Preserve all unchanged paragraphs; only translate the 
new/modified portions. Note in the commit message which sections changed.
```

Treat the English version as the source of truth. Always update 
English first, then propagate.
