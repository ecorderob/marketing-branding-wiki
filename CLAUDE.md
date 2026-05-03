# LLM Wiki Schema — Marketing & Branding Course Content Builder

This file defines how you (the LLM) operate this wiki. Follow these instructions for all operations.

## Purpose

This wiki is a structured, evolving knowledge base for marketing, branding, and creative-business education. Its content feeds online courses, tutorials, and supporting materials (LinkedIn posts, podcast episodes, book chapters). Everything you write must be:

- **Clear**: Use simple English. Assume the reader is not a native English speaker and not deeply familiar with marketing or business jargon. Define terms on first use. Prefer short sentences and concrete examples over abstract explanations.
- **Tutorial-oriented**: Content follows a logical learning progression. Each page builds on what came before.
- **In my voice**: Before writing or updating any content, read `voice.md` and match my writing style, tone, and personality.
- **Practitioner-grounded**: Anchor advice in real situations — client conversations, pricing decisions, brand choices, sales calls, content strategy. Avoid abstract theory without an applied example.

## Source Material

The `content/` folder contains long-form resource guides distilled from Chris Do's teachings (and related practitioners) covering:

- Entrepreneurial mindset and confidence
- Communication and influence
- Personal brand and identity
- Specialization and positioning
- Pricing and value strategy
- Business operations and growth
- Client acquisition and sales
- Creative process and learning
- Resilience and long-term vision

Treat these as primary source material to ingest and transform into tutorials. The MOC (`Marketing-Branding-Resources-MOC.md`) maps the territory.

## Directory Structure

```
CLAUDE.md          # This file — schema and instructions
voice.md           # My writing voice and style guide
template.md        # Standard page format — use this for every wiki page
index.md           # Auto-maintained catalog of all wiki pages
content/
  00-welcome/                        # Course introduction and orientation
  01-mindset-and-confidence/         # Entrepreneurial mindset, growth, imposter syndrome, courage
  02-communication-and-influence/    # Listening, diagnostic questioning, transparency, strategic vulnerability
  03-personal-brand-and-identity/    # Brand stories, authenticity, touchpoints, portfolio, brand evolution
  04-specialization-and-positioning/ # Niching, three-circle framework, validation, thought leadership
  05-pricing-and-value-strategy/     # Value-based pricing, premium positioning, profit leaks, pricing psychology
  06-client-acquisition-and-sales/   # Advisor positioning, referrals, pipeline, qualification, contracts
  07-business-operations-and-growth/ # Delegation, hiring, culture, profit recovery, income diversification
  08-creative-process-and-learning/  # Flow, energy management, burnout prevention, strategic learning
  09-resilience-and-long-term-vision/ # Radical responsibility, constraints-as-assets, vision, legacy
  Resource-Guide-*.md                # Long-form source guides queued for ingestion. Each guide is deleted once its content has been digested into tutorial pages.
```

## Reading Order and Branches

The intended reading path is linear: 00 through 09. There is a deliberate branch around category 04:

- **Solo creators and freelancers building their brand** can stop after `04-specialization-and-positioning`. Categories 00-04 give them the inner game and outward positioning needed to show up clearly without yet running a business.
- **Operators building a practice or studio** continue from `05-pricing-and-value-strategy` onward. Categories 05-09 assume the reader is monetizing, working with clients, and possibly building a team.

When deciding where a new page belongs, ask: "Does this require running a business, charging clients, or managing operations?" If yes, it belongs in 05 or later. If a solo creator with no clients yet could benefit, it goes in 04 or earlier.

## Creating New Categories

The 00-09 list above is the current set, not a permanent ceiling. New categories can be created when a body of material clearly does not fit any existing category and is large enough to warrant its own learning track (typically 4+ tutorials).

**When to propose a new category:**
- Material accumulates around a coherent theme that does not belong in any existing category, and forcing it in would distort that category's purpose.
- A clearly distinct stage of the reader's journey emerges that the linear 00-09 path does not cover.

**How to propose a new category:**
1. Stop before creating any files.
2. Propose the new category to the user with: suggested 2-digit number, slug (`NN-kebab-case`), one-line scope description (matching the inline comment style in the directory listing above), where it fits in the linear reading path, and which category branch it belongs to (solo-creator track 00-04, or operator track 05+).
3. Wait for explicit approval before creating the directory or any pages inside it.

**What to update once approved:**
- The directory tree in `CLAUDE.md` (the `content/` block above) with the new entry and its inline scope comment.
- The reading-order/branches section in `CLAUDE.md` if the new category shifts the solo-creator vs operator split.
- The `category` enum in `template.md` (both the file location section and the frontmatter example).
- The `index.md` with a new `### Category: NN-slug` heading. Use `_(empty)_` until pages exist.
- If the new category is inserted between existing categories rather than appended, renumber downstream categories using the same renumbering checklist as for tutorials (work highest-down, update directory names, frontmatter `category` fields in every page inside renamed categories, and `index.md` headings and links).

**Numbering rule for new categories:**
- Append at the end (next free 2-digit number) by default.
- Insert mid-sequence only when the new category genuinely belongs earlier in the reader's path. Inserting is more expensive (every downstream category and every page inside renumbers), so prefer appending unless the linear order demands otherwise.

**Hard rule:** Never create a new category silently as a side effect of an ingest. Categories are structural decisions about the curriculum. Always propose and wait for approval first.

## Page Format

Every wiki page must follow the format defined in `template.md`. Read it before creating any page.

## Numbering Convention

Every tutorial file must have a 2-digit number prefix in both the filename and the frontmatter title:

- **Filename**: `{NN}-{slug}.mdx` (e.g., `01-why-mindset-comes-first.mdx`, `02-the-two-voices-of-confidence.mdx`)
- **Title**: `"{NN}. {Title}"` (e.g., `"01. Why Mindset Comes Before Tactics"`)
- Numbers are sequential within each category, starting at `01`.
- Forward pointers ("Next up:") must include the number prefix of the next page's title.

**Forward pointer format:** `Next up: **NN. Title**`.

**Inserting a tutorial mid-category:**

When a new tutorial needs to be inserted between existing pages (not appended at the end), follow this checklist to keep numbering and forward pointers consistent:

1. Rename downstream files in order, working from the highest number down to avoid collisions (e.g. `11-foo.mdx` → `12-foo.mdx` before `10-bar.mdx` → `11-bar.mdx`).
2. Update the frontmatter `title` in each renamed file so the `NN.` prefix matches the new filename.
3. Update the forward pointer in the page that previously preceded the now-shifted next-numbered page.
4. Update each renamed page's own forward pointer to reflect the new number of the page it points to.
5. Update `index.md` entries for every renamed file.

## Difficulty Levels

Every tutorial page must be tagged with a difficulty level:

- **beginner** — No prior knowledge assumed. Explains from first principles. Suited to someone new to running a creative business or building a personal brand.
- **intermediate** — Assumes familiarity with basic business and brand concepts. Builds on beginner material. The reader has done work, charged for it, and faced common obstacles.
- **advanced** — Assumes solid practitioner experience. Covers nuance, edge cases, and deeper strategy. The reader is operating, scaling, or refining.

Tutorials should have a clear progression from easier to harder topics within them. Concept pages should state what level of understanding they target.

**Within each category, difficulty must be non-decreasing from one page to the next.** If a beginner-level page belongs in an otherwise intermediate category, place it before the intermediate pages or move it to a different category. When a category has mixed levels, order them so all beginner pages come first, then intermediate, then advanced.

## Content Generation Method: The Feynman Skill

**Hard rule.** Any time you write or rewrite a tutorial page or any other piece of content for this wiki, you must invoke the `feynman-tutorial` skill (via the Skill tool, as `/feynman-tutorial`) before producing the final text. This is non-negotiable. If the skill is not registered in the current environment (no entry in the skills catalog), note this in the report and apply the method's principles manually: write analogies for every core concept, explain each concept in words a bright 12-year-old would know, and fill any jargon gaps before drafting.

The Feynman method is the engine that keeps this wiki understandable for non-native English speakers and beginners. Marketing and branding content is full of jargon (positioning, value proposition, funnel, brand equity, ICP, LTV) that hides simple ideas. The method forces you to:

1. Identify the distinct concepts in the source material.
2. Try to explain each one in words a bright 12-year-old would know.
3. Surface the places where the explanation reaches for jargon or hand-waves, and fill those gaps.
4. Build at least one everyday analogy per core concept.
5. Rewrite until a smart reader with no business background could follow it.

The skill runs internally before the page is written. Its output is not saved as a separate file. It shapes the draft that you then format into `template.md` and filter through `voice.md`.

**Order of operations for any content write:**

1. Read the source material (resource guides, transcripts, articles, or notes).
2. Enrich with NotebookLM (see Ingest step 2 for the full workflow). You must attempt the `/notebooklm` skill — only skip if invocation fails or authentication is rejected.
3. If NotebookLM was skipped, fill gaps with web research (see Ingest step 3). If NotebookLM succeeded, skip this step.
4. Read `voice.md`.
5. Read `template.md`.
6. Invoke the `/feynman-tutorial` skill on the combined material (source + enrichment).
7. Draft the page using the skill's output as the backbone.
8. Filter every sentence through `voice.md` (short sentences, no em dashes, no grandiose words, no credential flexing, etc.).
9. Check the page against `template.md` rules (line count, section count, callouts, examples).
10. **Fact-check against the internet**: Extract every concrete factual claim from the draft. Specifically watch for: attributions to named people (Chris Do, Seth Godin, etc.), dates and numbers, study or statistic citations, claims about how a specific platform behaves (LinkedIn, YouTube algorithm changes), pricing benchmarks, named frameworks and their original authors, and cause-and-effect claims. For each one, run a web search or web fetch against authoritative sources (the original creator's content, primary research, reputable reporting). Anything that cannot be confirmed must be softened to a hedged claim, attributed as "in my experience," or removed. Report the list of claims checked and the verification result for each at the end of the operation.
11. **Voice filter verification**: Search the new or modified files for em dashes (`—`) in prose, code-style blocks, and frontmatter fields. Fix any violations before saving. This ensures the voice filter step is complete across the entire file.
12. Update `index.md`.

Skipping the Feynman step produces content that sounds like generic marketing advice. That defeats the purpose of this wiki, which is to make creative-business thinking actually accessible to people who didn't grow up speaking the jargon.

## Operations

### Ingest

When asked to ingest a source (resource guide, podcast transcript, article, book chapter, or any content):

1. Read the source fully.
2. **Enrich with NotebookLM**: Use NotebookLM to deepen understanding of the topic before anything else. This step produces richer source material for every subsequent step. The workflow:
   1. Create a notebook named `"Enrichment: {topic}"`.
   2. Add the source material and 2-4 authoritative references (URLs, YouTube videos, PDFs) on the topic. For marketing topics, prefer primary sources (the original creator's posts, talks, interviews, books) over secondary commentary.
   3. Run `source add-research` with `--mode deep` on the core topic to pull in supplementary sources.
   4. Wait for all sources to be indexed.
   5. Ask 2-4 targeted questions: common misconceptions beginners hold, concepts practitioners struggle to apply, everyday analogies, real-world examples of the principle in action, and details that introductory explanations usually skip.
   6. Generate a mind map to get a structured concept tree for the topic.
   7. Use the answers and mind map as supplementary input for subsequent steps.
   8. Delete the notebook after drafting is complete — these notebooks are ephemeral, not archival.
   You must invoke the `/notebooklm` skill and attempt the enrichment workflow. Only skip if the skill invocation fails, authentication is rejected, or the NotebookLM API returns an error. If the skill is not registered in the current environment (no entry in the skills catalog), note this in the report and fall back to web research (step 3). Silent skipping without an attempt is not allowed.
3. **Fill gaps with web research (only if NotebookLM was skipped)**: This step runs only when step 2 failed or was unavailable. If NotebookLM enrichment succeeded, skip this step — NotebookLM's deep research already covers gap-filling. When this step does run: identify any concepts the source mentions but does not explain. Use web search and web fetch to gather supplementary information for those gaps. Prioritize the original creator's published material, authoritative references, and recent sources. Do not fabricate details — if you cannot find a reliable source, note the gap explicitly in the draft rather than guessing.
4. Read `voice.md` to calibrate tone.
5. Read `index.md` to understand what already exists in the wiki.
6. Determine where the content belongs:
   - Does it fit into an existing tutorial? Add or update pages within it.
   - Is there enough new material to justify a new tutorial? Propose it (see below).
7. **Deduplicate**: If the source covers something already in the wiki, do NOT create duplicate content. Instead, enrich the existing page with any new information.
8. **Cross-check existing claims**: Before drafting anything, extract the core factual claims from the source (attributions, frameworks, numbers, statements about how things work). For each, grep the wiki for pages that make a related claim. List the matches. If any existing page contradicts the source, stop and ask me which version is correct before making changes. Do not silently pick a winner and do not draft around the conflict.
9. **Invoke the `/feynman-tutorial` skill** on the combined material (source + NotebookLM enrichment + web research) before drafting. See the "Content Generation Method" section above. This step is required, not optional.
10. Write or update pages using `template.md` format and my voice from `voice.md`, with the Feynman skill's output as your backbone.
11. **Fact-check against the internet**: Apply the same fact-check step from the "Order of operations for any content write" list (step 10 there). Verify each concrete factual claim in the new or modified pages against authoritative web sources. Soften or remove anything that cannot be confirmed before updating the index.
12. Update `index.md` to reflect any new or changed pages.
13. Delete the source file after all pages are written and `index.md` is updated. This applies to both `raw/` files and `Resource-Guide-*.md` files at the root of `content/`. Once content has been digested into tutorial pages, the source is redundant and keeping it creates two sources of truth.
14. Report a brief summary of what was added or changed.
15. Check if this ingest surfaced any improvement opportunities. If yes, log them in `improvements.md` following the **Improve** operation rules below, then mention them briefly at the end of your report.

**Do not link to or reference source files.** Sources are removed after ingestion. All tutorial and concept content must be self-contained in the wiki.

**Minimal interaction**: Proceed autonomously. Only ask me when there is genuine uncertainty — where content belongs, how to resolve a conflict, or whether to create a new tutorial.

### Batch ingest mode

When ingesting 3 or more sources in a single session, the per-page `/notebooklm` and `/feynman-tutorial` invocations exhaust the context window before the third file. Use batch mode in that case:

- Apply the Feynman method manually instead of invoking the skill per page. The principles still apply (analogies for every core concept, 12-year-old vocabulary, jargon gaps filled), but the skill is not invoked once per page.
- Either skip NotebookLM enrichment entirely, or create a single shared enrichment notebook covering all sources in the batch and reuse its output across pages.
- The fact-check step (Order of operations step 10, Ingest step 11) still runs per page. Do not batch-skip it. Factual accuracy on attributions and frameworks is non-negotiable — getting Chris Do's frameworks wrong, misattributing a Seth Godin idea, or fabricating a statistic is the kind of thing that destroys trust.
- State explicitly in the final report that batch mode was used, how many files were in the batch, and whether NotebookLM was skipped or batched.

Batch mode is a context-window concession, not a quality concession. Use it only when single-file mode would fail.

### Proposing New Tutorials

When you notice enough material accumulating around a topic that does not fit cleanly into existing tutorials, propose a new one. Include:

- Suggested title
- Target difficulty level
- Proposed page outline (list of topics in learning order)
- Which existing tutorials it would link to or build on

Wait for my approval before creating the tutorial.

### Query

When I ask a question:

1. Read `index.md` to find relevant pages.
2. Read those pages.
3. Synthesize an answer using simple, clear language in my voice.
4. Cite which wiki pages informed the answer.
5. If the answer produces valuable content (a comparison, an analysis, a new explanation, a worked example), ask if I want it filed as a new wiki page. If I say yes, run it through the `/feynman-tutorial` skill before writing the page (see "Content Generation Method" above).

### Lint / Health Check

When asked to lint or health-check the wiki, invoke the `wiki-lint` skill. That skill owns the full check set, the report format, and the approval gate.

The skill covers: duplicates and overlap, contradictions, orphan pages (no inbound links), stale claims (superseded material, outdated platform-specific facts, broken forward pointers), index-vs-filesystem reconciliation, difficulty-level consistency, template compliance, and voice violations (em dashes).

The skill produces a report and asks before any edits. After reviewing its report, if any findings suggest changes to the agent's own instructions (`CLAUDE.md`, `voice.md`, `template.md`), log them in `improvements.md` under the **Improve** operation rules. Never modify the schema files directly.

If the `wiki-lint` skill is not registered in the current environment, fall back to running the same checks manually using the check list described in `.claude/skills/wiki-lint/SKILL.md`.

### Improve

The agent can notice things that would make its own instructions clearer, more consistent, or more useful. When that happens, log the observation in `improvements.md` rather than silently working around it.

**When to look for improvements:**
- After every Ingest operation (step 15 above)
- After every Lint / Health Check
- When explicitly asked: "Any improvements to suggest?"

**What qualifies as an improvement suggestion:**
- A rule in `CLAUDE.md` that was ambiguous and required a judgment call
- A rule that was missing and had to be improvised
- A contradiction between `CLAUDE.md`, `voice.md`, or `template.md`
- A recurring pattern in content that should be codified as a rule
- A workflow step that causes friction or could be simplified
- A gap in `template.md` for content that does not fit the current format (e.g., a framework explainer, a script, a worked dialogue)

**What does NOT qualify:**
- Content suggestions — those go through the Proposing New Tutorials workflow
- One-off edge cases that are not worth codifying
- Anything already listed under `## Rejected` in `improvements.md`

**How to log a suggestion:**
1. Read `improvements.md` to check for duplicates and rejected items.
2. Append a new entry under `## Pending` using this format:

```markdown
### [YYYY-MM-DD] Short title
- **Affects**: CLAUDE.md / voice.md / template.md / workflow
- **Problem**: What you noticed
- **Suggestion**: What you recommend changing
- **Example**: The concrete case that triggered this observation
```

3. Mention the suggestion briefly to the user at the end of the current operation. One line is enough.

**Hard rule:** Never modify `CLAUDE.md`, `voice.md`, or `template.md` based on your own suggestions. Log. The user decides.

## Index (index.md)

The index is a catalog of every page in the wiki. Maintain it on every ingest. Structure:

```markdown
# Wiki Index

## Tutorials

### Category: 00-welcome
- [Tutorial Title](content/00-welcome/slug.mdx) — difficulty, brief description

### Category: 01-mindset-and-confidence
- [Tutorial Title](content/01-mindset-and-confidence/slug.mdx) — difficulty, brief description

### Category: 02-communication-and-influence
- [Tutorial Title](content/02-communication-and-influence/slug.mdx) — difficulty, brief description

### Category: 03-personal-brand-and-identity
- [Tutorial Title](content/03-personal-brand-and-identity/slug.mdx) — difficulty, brief description

### Category: 04-specialization-and-positioning
- [Tutorial Title](content/04-specialization-and-positioning/slug.mdx) — difficulty, brief description

### Category: 05-pricing-and-value-strategy
- [Tutorial Title](content/05-pricing-and-value-strategy/slug.mdx) — difficulty, brief description

### Category: 06-client-acquisition-and-sales
- [Tutorial Title](content/06-client-acquisition-and-sales/slug.mdx) — difficulty, brief description

### Category: 07-business-operations-and-growth
- [Tutorial Title](content/07-business-operations-and-growth/slug.mdx) — difficulty, brief description

### Category: 08-creative-process-and-learning
- [Tutorial Title](content/08-creative-process-and-learning/slug.mdx) — difficulty, brief description

### Category: 09-resilience-and-long-term-vision
- [Tutorial Title](content/09-resilience-and-long-term-vision/slug.mdx) — difficulty, brief description
```

## Writing Guidelines

- Use simple, direct English. Short sentences. No filler.
- Define marketing and business terms on first use, in plain language. Pretend the reader has never heard "positioning," "value proposition," or "ICP" before.
- Use concrete examples and analogies. Prefer "think of it like..." over abstract definitions. The best examples come from real situations: a sales call, a pricing conversation, a brand decision someone actually made.
- Use headers, bullet points, and numbered steps to break up content.
- Include worked examples: dialogues, before-and-after rewrites, decision trees, real numbers. These are the heart of practitioner content.
- Every page should make sense on its own — a reader might land on any page directly.
- Follow the voice and tone defined in `voice.md` at all times.
- Format markdown cleanly — this content will be exported to a course platform.
