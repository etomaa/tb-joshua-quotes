# Change Tracker

Living log of substantive changes to `index.html` (quote content, numbering, and count references). Newest entries on top. This file is downstream-relevant: sites like spiritworshipgen.org consume this repo, and quote IDs can shift, so record anything that changes a quote's text or number here, not just in the commit message.

---

## 2026-07-13 — Added 6 new quotes (#685–690); fixed a data-entry error on #684

**Data-entry fix on #684:** while adding this new batch, discovered that #684 had been entered as "If **you** take God's word..." instead of "If **we** take God's word..." as the user explicitly asked to keep it (see the entry below — "kept as submitted" / "we"/"you" pronoun shift was supposed to be *preserved*, not silently corrected). This was my own transcription error, now fixed to match what the user actually submitted: "If we take God's word to heart and truly make it a part of you by meditation, it will by it very nature change you and when it does, you will soon be called to act with God"

**Summary:** User supplied 6 more quotes directly. Applied only mechanical/unambiguous corrections (typos, stray copy-paste formatting artifacts); did not alter meaning or word choice.

**Corrections made:**
- #685 — added verbatim, no issues.
- #686 — stray leading quotation mark (no matching close) stripped.
- #687 — added verbatim, no issues.
- #688 — added verbatim, no issues.
- #689 — "disatisfaction" → "dissatisfaction" (typo); stray trailing quotation mark stripped.
- #690 — stripped markdown italics asterisks and quote marks (copy-paste artifacts, not part of the quote data model); removed a misplaced comma after "To the degree"; changed "...in our hearts. to that same degree..." to "...in our hearts, to that same degree..." (period → comma) since it's one continuous correlative sentence ("To the degree X, to that same degree Y"), not two.

**Added:** new #685–690, appended straight after #684 (no renumbering of prior quotes).

**Other updates bundled in because they touch quote numbering:**
- Header quote count (`684` → `690`), footer text, go-to input placeholder/max, `goTo()`/hash-link bounds.

**Files touched:** `index.html` only.

---

## 2026-07-13 — Added 3 new quotes (#682–684)

**Summary:** User supplied 3 more quotes directly. Flagged a few things during review (missing opening quote mark on #682; unusual clause phrasing in #683; a typo and a pronoun shift in #684) but user chose to keep the wording as submitted rather than apply the suggested fixes.

**Kept as submitted (no wording changes):**
- #682 — stray trailing quotation mark from the pasted text was stripped (data model doesn't wrap quote text in literal quote characters — consistent with every other entry), no other change.
- #683 — added verbatim.
- #684 — added verbatim, including "by it very nature" (not corrected to "its") and the "we"/"you" pronoun shift, and without a closing period — user's explicit call.

**Added:** new #682–684, appended straight after #681 (no renumbering of prior quotes).

**Other updates bundled in because they touch quote numbering:**
- Header quote count (`681` → `684`), footer text, go-to input placeholder/max, `goTo()`/hash-link bounds.

**Files touched:** `index.html` only.

---

## 2026-07-13 — Added 8 new quotes (#674–681)

**Summary:** User supplied 8 new quotes directly (not sourced from the web scrape) and asked for a spelling/word-usage check before adding. Corrected several typos and word choices, presented the corrected versions for approval, then appended as approved.

**Corrections made:**
- #674 — "situtation" → "situation"; "trade your joy **with** your situation" → "trade your joy **for** your situation" (for consistency with #675's "trade...for" phrasing).
- #677 — "Often times" → "Oftentimes".
- #678 — "you enemy" → "your enemy"; "attacka" → "attacks".
- #680 — "as child of God" → "as a child of God"; "will impact strength" → "will impart strength" (word-choice correction — "impart" fits the sense of conferring strength; "impact" doesn't function as a transitive verb here).
- #681 — Added missing opening quotation mark; "temptation" → "temptations" (plural, to match "Challenges" and "situations"); "the informant that" → "informants that" (subject-verb/number agreement).

**Note:** user's original list included a 9th item, but no text was provided for it — only 8 quotes were added. If a 9th quote was intended, it still needs to be supplied.

**Added:** new #674–681, appended straight after #673 (no renumbering of prior quotes).

**Other updates bundled in because they touch quote numbering:**
- Header quote count (`673` → `681`), footer text, go-to input placeholder/max, `goTo()`/hash-link bounds.

**Files touched:** `index.html` only.

---

## 2026-07-13 — Added 134 new quotes (#540–673)

**Summary:** Scraped 188 unique T.B. Joshua quotes from 5 public quote sites, cross-checked all of them against the existing 539 quotes (exact-text match, then fuzzy word-overlap for reworded near-duplicates). 145 had no match and were presented for review; 19 were flagged as likely paraphrases of an existing quote and set aside by default. User reviewed both lists in a themed HTML checklist and approved 134 for addition (some from the "likely covered" set were pulled in on review too).

**Added:** new #540–673, appended in the order approved, IDs continuing straight on from the existing #1–539 (no renumbering of prior quotes needed since these were appended, not inserted).

**Sources:**
- [AZQuotes](https://www.azquotes.com/author/41952-T_B_Joshua)
- [QuoteFancy](https://quotefancy.com/t-b-joshua-quotes)
- [AllChristianQuotes](https://www.allchristianquotes.org/authors/175/T_B_Joshua/)
- [QuotePark](https://quotepark.com/authors/t-b-joshua/)
- [WiseFamousQuotes](https://www.wisefamousquotes.com/t-b-joshua-quotes/)

**Caveat:** wording/attribution comes from third-party aggregator sites, not a primary transcript — accuracy is only as good as those sources.

**Other updates bundled in because they touch quote numbering:**
- Header quote count (`539` → `673`), footer text, go-to input placeholder/max, `goTo()`/hash-link bounds.

**Files touched:** `index.html` only. (The review tool, `quotes-candidates-review.html`, is a throwaway staging file — not part of the site.)

---

## 2026-07-13 — Removed duplicate quotes, renumbered, fixed #519 typo

**Summary:** Found and removed 22 duplicate quotes (14 exact, 8 reworded near-duplicates), then renumbered the remaining 539 quotes sequentially (1–539, no gaps). Total dropped from 561 to 539.

**Spelling fix:** Quote #519 (old numbering) corrected before this cleanup; it now reads "If we make mistakes, as we all do - don't run from God, run to Him." It landed at **new #519**.

**Exact duplicates removed** (old ID kept → old ID deleted — text was identical):
- 44 → 521 — "It is time to do something different to change your life from failure to success."
- 72 → 330 — "Fear and insecurity dominate a life without faith."
- 117 → 225 — "A believer does not have strength as long as he operates in the natural."
- 322 → 448 — "The better a man is, the worse he is thought of by his rivals."
- 386 → 397 — "Human rebellion makes us do things against God's instruction."
- 387 → 398 — "It is not a mere wishful thinking that brings about contented life but a rightful focus."
- 388 → 399 — "Those who have been delivered by Christ's Word must be ruled by His Word."
- 389 → 400 — "When your spirit loses its sensitivity, your real value is at stake; it becomes a tool in the hand of the devil, a toy for manipulation."
- 390 → 401 — "Serving God is to do what the best do."
- 391 → 402 — "You are included in God's master plan but nothing great comes easy."
- 392 → 403 — "Hard times can touch you but they cannot destroy you as a Christian."
- 393 → 404 — "Successful people did not just drift to the top. It takes focused action, personal discipline and a lot of energy every day to make things happen."
- 394 → 405 — "A true Christian is tested by his ability to face circumstances."
- 396 → 407 — "Jesus loves those who are able to exercise great faith under great trials and temptation."

Note: old #386–396 (an 11-quote block) had been pasted twice as old #397–407 — a copy/paste accident, not coincidence.

**Near-duplicates removed** (same quote, reworded slightly — kept lower ID's phrasing per user decision):
- 56 → 320
  - kept: "When you know you are who God says you are, you will stay focused on your goal alone and nothing can change your focus."
  - deleted: "When you know who God says you are, you will stay focused on your goal alone and nothing can change your focus."
- 71 → 331
  - kept: "To the people of the world, trouble, affliction, poverty and the like are a poison that kills man's happiness and zeal to move forward but to the people of God, these things serve as a tonic, a driving force to a higher aspiration."
  - deleted: "For the people of the world, trouble, affliction, poverty and the like are a poison that kills man's happiness and zeal to move forward but to the people of God, these things serve as a tonic, a driving force to a higher aspiration."
- 145 → 295
  - kept: "God is more concerned with our future than He is about our present state."
  - deleted: "God is more concerned with our future than He is about our present situation."
- 201 → 478
  - kept: "If you have not engaged your heart with God's Word, you would murmur and rebel when challenges come, instead of finding out what God has to say about those challenges."
  - deleted: "If you have not engaged your heart with God's Word, you will murmur and rebel when challenges come instead of finding out what God has to say about them."
- 229 → 459
  - kept: "As Christians our heart must be active, strong and alert; if not, the enemy of our soul will take hold of it and begin to manipulate our thoughts."
  - deleted: "As Christians our heart must be active, strong and alert; if not, the enemy of our soul will take hold of it and manipulate our thoughts."
- 230 → 378
  - kept: "A genuine spiritual experience needs to be tested in the face of the real situation in order to expose the reality of the experience."
  - deleted: "A genuine spiritual experience needs to be tested in a real situation in order to expose the reality of that experience."
- 255 → 507
  - kept: "All men fall but great men get back up."
  - deleted: "All men fall but the great ones get back up."
- 395 → 406
  - kept: "Trials and tests promote and advance your course."
  - deleted: "Trials and tests are to promote and advance your course."

**Why the near-duplicates existed:** the collection is sourced from "Volumes 1 & 2"; overlapping quotes between the two volumes (transcribed with minor wording differences) is the likely cause, since matches consistently paired a lower-numbered quote with one several hundred IDs higher.

**Other fixes bundled in because they touch quote numbering:**
- Header quote count (`561` → `539`), footer text, go-to input placeholder/max.
- Fixed a pre-existing inconsistency: `goTo()` and hash-link navigation (`#q123`) were hardcoded to cap at `556` even though the displayed total was `561`. Both now correctly cap at `539`.

**All old→new ID mappings are NOT individually recorded** beyond the deletions above — every ID besides the 22 deleted ones kept its relative order and shifted down by however many deletions preceded it. If a downstream site links to a specific old quote number, use the deletion list above to work out the offset.

**Files touched:** `index.html` only.

---

## Template for future entries

```
## YYYY-MM-DD — Short summary

**Summary:** What changed and why, in 1-3 sentences.

**Details:** Quote IDs added/removed/edited, old→new mappings if renumbering occurred, any count references updated.

**Files touched:** ...
```
