---
name: landing-copy-collector
description: Capture minimal landing page copy references into this project's language folders. Use when the user provides one or more landing page URLs and wants the service name, one-line service summary, category, link, headline, subheadline, SEO title/meta description, and structured line-by-line notes about headline/subheadline breaks and emphasis, saved as Markdown for later landing page copywriting reference.
---

# Landing Copy Collector

## Overview

Use this skill to turn landing page URLs into minimal Markdown reference cards. Save English pages under `english/` and Korean pages under `korean/`.

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
5. Capture only the main hero copy:
   - Primary headline exactly as visible
   - Subheadline/supporting line exactly as visible
6. Inspect only how the headline and subheadline are presented. Record line breaks structurally:
   - `Headline lines`: one item per visual line, in displayed order
   - `Subheadline lines`: one item per visual line, in displayed order
   - `Alignment`: centered, left, right, or mixed
   - `Emphasis`: line-specific emphasis such as larger line, highlighted word, bold word, dynamic/rotating term, badge/eyebrow directly attached to the hero copy
   - `Relationship`: how the subheadline supports, narrows, or expands the headline
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

- Category: ...
- One-liner: ...

## SEO

- Title: ...
- Meta description: ...

## Hero Copy

- Headline: ...
- Subheadline: ...

## Line Layout

- Headline lines:
  1. ...
  2. ...
- Subheadline lines:
  1. ...
  2. ...
- Alignment: ...
- Emphasis: ...
- Headline/subheadline relationship: ...
```

## Quality Rules

- Write `one_liner` as a compact sentence that explains what the service does and who it helps. Prefer observable claims from the page; if the page is vague, keep the wording conservative.
- Keep `category` short and reusable so future prompts can group similar services.
- Preserve visible copy exactly for headline and subheadline.
- Preserve visual line breaks in `Line Layout`. If the browser wraps text differently by viewport, use the desktop hero layout unless the user asks otherwise.
- Keep layout notes minimal and limited to headline/subheadline line breaks, alignment, and emphasis. Do not add broader marketing analysis, CTA notes, product UI descriptions, copy takeaways, or browsing/debug logs.
- Do not invent missing metadata or copy. Use `Not found` when unavailable.
- If a headline contains rotating/dynamic words, capture the observed variant as its own line or inline phrase exactly as displayed and mention that it appears dynamic in `Emphasis`.
- After writing the file, tell the user the saved path and summarize the captured headline plus one notable presentation pattern.
