# Tutorial Page Template

## File Location

```
content/{category}/{NN}-{slug}.mdx
```

Where `{category}` is one of: `mindset-and-confidence`, `communication-and-influence`, `personal-brand-and-identity`, `specialization-and-positioning`, `pricing-and-value-strategy`, `client-acquisition-and-sales`, `business-operations-and-growth`, `creative-process-and-learning`, `resilience-and-long-term-vision`
Where `{NN}` is a 2-digit sequence number within the category (e.g., `01`, `02`, `03`)
And `{slug}` is kebab-case (e.g., `the-three-circle-framework`)

## Frontmatter

```yaml
---
title: "{NN. Descriptive title, 5-12 words}"
category: "{mindset-and-confidence | communication-and-influence | personal-brand-and-identity | specialization-and-positioning | pricing-and-value-strategy | client-acquisition-and-sales | business-operations-and-growth | creative-process-and-learning | resilience-and-long-term-vision}"
difficulty: "{beginner | intermediate | advanced}"
readTime: "{N} min"
publishedAt: "{YYYY-MM-DD}"
featured: false
description: "{One action-oriented sentence, 15-25 words, describing what the reader will learn, decide, or be able to do}"
---
```

## Content Structure

```markdown
## {Opening Section Title — names the topic}

{1-2 paragraphs introducing what this topic is and why it matters. Open with a concrete situation a reader will recognize: a sales call that went sideways, a pricing decision, a brand choice. Then say what the page will teach.}

{Optional bullet list of what the reader will be able to do, decide, or notice differently after reading.}

## {Foundation or Prerequisites Section Title}

{Explain any concepts, frameworks, or context the reader needs before the core teaching. If the page builds on another tutorial, link it here. If a key term is about to be used, define it in plain language.}

> **Definition:** {Term} — {one-sentence plain-language definition. Optional, use when introducing a jargon term.}

## {Core Teaching Section 1 Title}

{1-2 paragraphs explaining the concept. Lead with the idea in plain words, then name the term if there is one.}

**Example.** {A concrete worked example. Use real situations: a client conversation, a pricing scenario, a brand decision. Show the before and after, the choice and the consequence, or the dialogue as it actually plays out.}

> **Tip:** {Helpful supplementary advice the reader can apply immediately.}

## {Core Teaching Section 2 Title}

{1-2 paragraphs explaining the next concept, building on the previous section.}

**Example.** {Another worked example, dialogue, or before-and-after.}

> **Warning:** {Common mistake, trap, or thing that sounds right but isn't.}

## {Core Teaching Section 3 Title — optional, add 1-2 more sections if the topic requires it}

{Explanation and example following the same pattern. Frameworks, checklists, decision trees, and dialogue scripts all fit here — pick the format that makes the idea clearest.}

### {Optional subsection — for a sub-step inside a section}

{Use `###` only when a section has clearly distinct sub-steps that benefit from their own headings.}

## Try This

{Optional but encouraged. A short, concrete exercise the reader can do in 5-15 minutes to apply the idea. Examples: "Write three versions of your one-line positioning statement and read them aloud," "List your last five clients and circle the ones who said yes within one call." This converts reading into doing.}

## Summary

{1 paragraph, 3-5 sentences: recap what was covered and what the reader can now decide or do differently.
End with a forward pointer to a related topic using: "Next up: **{NN. related topic}**."}
```

## Rules

| Rule | Detail |
|------|--------|
| Headings | `##` for main sections, `###` for subsections. Never `#` — frontmatter title is the h1. |
| Examples | Every core teaching section needs at least one concrete example: a dialogue, a worked scenario, a before-and-after, real numbers, or a named case. No example = abstract theory = cut it or fix it. |
| Callouts | Blockquotes with **Tip:**, **Warning:**, **Definition:**, or **Example:** prefix. Plain blockquotes become info callouts. |
| Dialogues | Format speaker turns as `**Client:** ...` and `**You:** ...` on separate lines. Keep turns short and realistic. |
| Frameworks | When introducing a named framework, name its origin if known (e.g., "Chris Do's three-circle framework"). If origin is unknown or disputed, say so rather than guessing. |
| Numbers and stats | Any specific number (pricing benchmarks, conversion rates, percentages) must be sourced or marked as illustrative. Hedge with "in my experience" if it is anecdotal. |
| Length | Aim for 100-250 lines. Longer is fine when the topic demands it; prefer splitting into multiple pages over padding a short one. `readTime` should match ~200 words/min. |
| Tone | Second person ("you"), conversational but concise. No fluff. No grandiose words. No em dashes. |
| No inline HTML | Pure markdown only. MDX components handle styling. |
| No images | Not supported. Describe visual frameworks in words or as ASCII diagrams in plain code fences when truly necessary. |
| Slug | Filename = `{NN}-{slug}`. 2-digit prefix + descriptive kebab-case. |
| Title prefix | Frontmatter title must start with `{NN}.` matching the filename prefix. |
| Sections | Aim for 3-5 teaching sections. Up to 7 is acceptable when the topic decomposes naturally. More than 7 should split into two pages. Each section = explanation + example + optional callout. |
| Stand-alone | Every page must make sense on its own. Define jargon on first use, even if it was defined in a sibling page. |
