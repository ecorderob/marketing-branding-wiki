---
name: wiki-lint
description: On-demand health check for the marketing-branding-wiki knowledge base. Use when the user says "lint the wiki", "health-check the wiki", "run wiki lint", "check the wiki for issues", "audit the wiki", or any equivalent. Produces a structured report covering duplicates, contradictions, missing concept pages, orphan pages (no inbound links), stale claims (old `updated` dates or superseded material), index-vs-filesystem reconciliation, difficulty-level consistency, and template compliance. Reports findings as a checklist and asks before making changes — never edits content without approval.
---

# Wiki Lint

Run a full health check of the wiki. Report findings as a checklist. Do not modify any content until the user approves changes.

## Scope

Check everything under `content/` and the root `index.md`. The wiki's schema (`CLAUDE.md`, `voice.md`, `template.md`) is input to the checks, not a target of them.

## Checks to run

Run each check below. For each check, list findings as bullet points with file paths. If a check produces zero findings, say so explicitly — do not omit the section.

### 1. Duplicates and overlap
Scan for pages covering the same concept. Flag clear overlaps where two pages teach the same material with minor rewording. Exclude deliberate review or recap sections.

### 2. Contradictions
Compare claims across pages. A contradiction is a factual statement on one page that is incompatible with a statement on another. Report both pages and the conflicting claims.

### 3. Orphan pages
Find pages that no other page links to. For each tutorial file, check whether any other file in `content/` or `index.md` contains a markdown link to it. Report every file with zero inbound links. Exclude: the first tutorial in each category (entry points) and `index.md` itself.

### 4. Stale claims
Flag pages where stated facts have likely been superseded by newer material. Signals:
- The page's frontmatter `updated` or `publishedAt` date is more than 90 days old AND a more recently ingested page on a related topic contradicts or refines it.
- Version-specific claims (model names, pricing, feature availability) that may have changed since the page was written.
- Forward pointers ("Next up:") that point to pages that no longer exist or have been renumbered.

Do not flag pages just for being old. Stale = old AND contradicted / outdated.

### 5. Index reconciliation
Compare `index.md` against the actual filesystem under `content/`.
- Every file on disk must appear in `index.md`. List any that do not.
- Every entry in `index.md` must point to a file that exists. List any dead links.
- Numbering in `index.md` must match filename prefixes. List any mismatches.

### 6. Difficulty-level consistency
A beginner tutorial must not depend on advanced concepts without explaining them. Check that:
- Beginner pages do not use jargon introduced only in intermediate or advanced pages without defining it.
- The difficulty progression within each category is non-decreasing (a `02-` page should not be harder than the `05-` page that follows it).

### 7. Template compliance
For each page, verify against `template.md`:
- Frontmatter has all required fields with valid values.
- Title prefix matches filename prefix (`01. Title` in a file named `01-slug.mdx`).
- Minimum 3 teaching sections, maximum 5.
- Code blocks specify a language.
- No `#` headings (frontmatter title is the h1).
- No inline HTML.
- Second-person voice.

### 8. Voice violations
Search every page for em dashes (`—`) in prose, code comments, and frontmatter. List every file that contains them. The voice filter bans them.

### 9. Schema improvement opportunities
If any finding suggests a change to `CLAUDE.md`, `voice.md`, or `template.md` itself, note it. At the end of the report, remind the user these must be logged in `improvements.md` under `## Pending` per the Improve workflow — do not modify the schema files directly.

## Report format

Produce a single markdown report with one `##` section per check above, in order. Each section starts with a one-line count (`Found: N`). Under each finding include the relevant file paths so the user can jump straight to them.

End the report with a short "Recommended next actions" list, ranked by severity. Then ask: "Which of these would you like me to fix?" Wait for approval before editing anything.

## What this skill does NOT do

- Does not edit any wiki content.
- Does not modify `CLAUDE.md`, `voice.md`, `template.md`, or `improvements.md`.
- Does not delete orphan pages (orphans may be deliberate).
- Does not commit to git.

All fixes require user approval and run as separate operations after the report.
