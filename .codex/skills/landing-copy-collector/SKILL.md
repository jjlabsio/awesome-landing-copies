---
name: landing-copy-collector
description: Capture landing page copy into this project's language folders. Use when the user provides one or more landing page URLs and wants the service name, one-line service summary, category, link, headline, subheadline, SEO title/meta description, and notes about hero layout, text hierarchy, emphasis, and copy presentation saved as Markdown for later landing page copywriting reference.
---

# Landing Copy Collector

## Overview

Use this skill to turn landing page URLs into structured Markdown reference notes. Save English pages under `english/` and Korean pages under `korean/`.

## Workflow

1. Open the URL in a browser or fetch the HTML. Prefer a browser when the page is rendered client-side or layout details matter.
2. Identify the page language from visible copy and metadata. Use `english/` for English, `korean/` for Korean. If a page is bilingual, choose the dominant landing page copy language and note the secondary language.
3. Capture SEO metadata:
   - `<title>`
   - `<meta name="description">`, `og:description`, or the closest available description. Label missing values as `Not found`.
4. Capture service context for future copy generation:
   - Service/product name
   - Category, such as `AI writing assistant`, `developer tool`, `CRM`, `analytics platform`, or `consumer finance app`
   - One-line service summary describing what the service does and who it helps
5. Capture hero copy:
   - Service/product name
   - Primary headline exactly as visible
   - Subheadline/supporting line exactly as visible
   - Primary CTA text when visible
   - Secondary CTA text when visible
6. Inspect how the copy is presented above the fold. Record concise visual notes about:
   - Layout: centered, split hero, left-aligned column, dashboard preview, nav relationship, spacing density
   - Hierarchy: what appears largest, first, repeated, or closest to the CTA
   - Emphasis: bold words, line breaks, color highlights, badges, eyebrow text, animated/rotating words, underlines
   - Context: screenshots, product UI, customer logos, trust badges, social proof, pricing hooks, audience cues
7. Save one Markdown file per URL using a stable slug:
   - `english/{service-slug}.md`
   - `korean/{service-slug}.md`
   Use lowercase hyphen-case. If a filename exists, append `-2`, `-3`, etc. rather than overwriting.

## Markdown Format

Use this structure:

```markdown
---
service: "Service Name"
url: "https://example.com"
language: "English"
category: "Product category"
one_liner: "One sentence explaining what the service does and who it helps."
captured_at: "YYYY-MM-DD"
---

# Service Name

## Service Summary

- Category: ...
- One-liner: ...

## SEO

- Title: ...
- Meta description: ...

## Hero Copy

- Headline: ...
- Subheadline: ...
- Primary CTA: ...
- Secondary CTA: ...

## Presentation Notes

- Layout: ...
- Text hierarchy: ...
- Emphasis: ...
- Above-the-fold context: ...

## Copy Takeaways

- ...
- ...

## Raw Notes

- Access notes, uncertainty, or alternate copy variants observed.
```

## Quality Rules

- Write `one_liner` as a compact sentence that explains what the service does and who it helps. Prefer observable claims from the page; if the page is vague, infer carefully and mention uncertainty in `Raw Notes`.
- Keep `category` short and reusable so future prompts can group similar services.
- Preserve visible copy exactly for headline, subheadline, and CTA fields.
- Keep layout and emphasis notes interpretive but concrete enough to recreate the pattern later.
- Do not invent missing metadata or copy. Use `Not found` and explain the access limitation in `Raw Notes`.
- If cookie banners, modals, or geolocation variants affect the view, close only non-destructive overlays and note what changed.
- Avoid long verbatim page extracts. Capture only the requested landing page elements and short supporting snippets.
- After writing the file, tell the user the saved path and summarize the captured headline plus one notable presentation pattern.
