# Improvements

Suggestions for changes to `CLAUDE.md`, `voice.md`, `template.md`, or wiki workflows. Logged by the agent during ingest and lint operations. The user decides which to act on.

## Pending

### [2026-05-02] Em dash conflict between template.md and voice.md
- **Affects**: template.md / voice.md
- **Problem**: `template.md` shows the **Definition** callout format using an em dash separator (`> **Definition:** {Term} — {one-sentence...}`), but `voice.md` lists em dashes as a HARD RULE never. Following the template literally produces voice violations.
- **Suggestion**: Update the template's Definition callout example to use a period or colon separator (e.g., `> **Definition:** {Term}. {one-sentence...}` or `> **Definition:** {Term}: {one-sentence...}`). Apply the same fix to any other em dashes used as separators in `template.md`.
- **Example**: While ingesting Resource-Guide-Marketing-Client-Acquisition-and-Sales, six Definition callouts across new pages were initially written with the template's em dash separator and had to be rewritten before saving.

### [2026-05-03] Forward-pointer format at category boundaries
- **Affects**: CLAUDE.md / template.md
- **Problem**: The numbering convention specifies `Next up: **NN. Title**` for intra-category pointers but says nothing about the last page of a category. As a result the wiki ended up with three different cross-category styles: prose form ("continue to category **NN. Name**, where..."), bare next-page reference ("**01. Title**"), and a curriculum-end paragraph. The bare style at a category boundary also caused two miswired pointers (cat 02 jumping to cat 04, cat 08 pointing back to cat 07) because the writer used the next-page slot without noticing the category had changed.
- **Suggestion**: Codify a single cross-category form in `CLAUDE.md` and `template.md`. Recommended: `Next up: continue to category **NN. Category Name**, where {one-line bridge}.` for any forward pointer that crosses a category boundary. Keep `Next up: **NN. Title**` for intra-category pointers.
- **Example**: 2026-05-03 lint found four broken forward pointers, three of which were cross-category transitions written in the bare intra-category style.

### [2026-05-03] Forward pointers should be markdown links, not bold text
- **Affects**: CLAUDE.md / template.md
- **Problem**: Forward pointers are written as `**NN. Title**`, which means renaming a page silently breaks every reference to it. There is also no automated way to lint these references, so a title typo (e.g., `$1,000-an-Hour Test` vs `Thousand-Dollar Test`) survives until a human reads the page. Index entries already use markdown links to the same pages, so the data exists.
- **Suggestion**: Change the convention to `Next up: [NN. Title](relative/path.mdx)`. This makes pointers link-checkable with standard markdown tools, survives renames if a rename script updates links, and keeps the visible text identical to today's bold form when rendered.
- **Example**: 2026-05-03 lint found that `07-business-operations-and-growth/02-the-profit-leak-most-creatives-live-with.mdx` had pointed to a stale title (`$1,000-an-Hour Test`) for unknown duration before being caught by hand. Markdown link form would have surfaced it as a broken link on the first lint.

## Rejected

_(none yet)_
