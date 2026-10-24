# Site maintenance guide

## Scope and sources

This is Yuan Yao's academic homepage, built with Jekyll and Academic Pages for GitHub Pages. Follow the existing content and layout conventions when making updates.

The user explicitly requested that new publications follow the other entries and that this guide summarize tab formats and previous styling requirements. Earlier conversation instructions are not available in this checkout. The conventions below are grounded in the current files and Git history; they are not quotations of unavailable requests. New explicit user instructions take precedence.

## Navigation and tab formats

The header links are defined in `_data/navigation.yml`, in this order: **Publications**, **Projects**, **News & Press**, **CV**. The site title links to the **Bio** homepage. Preserve these labels, routes, and order unless asked to change them.

| Page | Route | Content source | Format |
| --- | --- | --- | --- |
| Bio / home | `/` | `_pages/about.md` | First-person biography, research interests, honors and awards, then a large photograph; author sidebar enabled. |
| Publications | `/publications/` | `_pages/publications.html`, `_publications/*.md` | Google Scholar link, category headings, then publication entries in reverse collection order; author sidebar enabled. |
| Projects | `/portfolio/` | `_pages/portfolio.html`, `_portfolio/portfolio-N.html` | Project title, short caption, and large image in collection order; author sidebar enabled. |
| News & Press | `/year-archive/` | `_pages/year-archive.html`, `_posts/*.md` | Posts in reverse chronological order grouped under year headings; author sidebar enabled. |
| CV | `/cv-json/` | `_pages/cv-json.md`, `_includes/cv-template.html`, `files/*.pdf` | One PDF download button above an embedded PDF viewer; author sidebar disabled. |

### Bio

- Keep the page title `Bio`, permalink `/`, and existing `/about/` and `/about.html` redirects.
- Use short first-person paragraphs for the biography and research description.
- Keep **Honors and Awards** as a bold label, followed by newest-first year-and-award lines with Markdown hard line breaks.
- Preserve the photograph below the awards. Its current inline styling is `width: 100%; max-width: 1366.67px; height: auto; margin-bottom: 20px;`.
- Author name, avatar, affiliation, contact links, Google Scholar, and ORCID are configured in `_config.yml`.

### Publications

- Create one Markdown file per publication: `_publications/YYYY-MM-DD-descriptive-slug.md`.
- Follow the front matter fields and order in existing entries: `title`, `collection: publications`, `category: manuscripts`, `permalink`, `excerpt`, `date`, `venue`, `paperurl`, `citation`.
- Use the singular permalink prefix `/publication/`, followed by the date and slug. Keep the new filename, permalink, and date consistent. Some older entries have mismatches; do not copy those inconsistencies.
- Use a verified publication date when available. Do not silently invent a month or day when only the year is known.
- `manuscripts` appears as **Selected Articles**, configured in `_config.yml`. The archive uses `_includes/archive-single.html`; adding a collection entry automatically adds it to the list.
- Keep the title in sentence case and the excerpt a concise, factual description of the paper's subject or contribution. Do not invent findings or impact claims.
- Use the journal's full name in `venue`. `paperurl` should point to the DOI resolver or publisher page.
- Match the existing citation style: `Yao, Y. (2026). Article title. <i>Journal Name</i>.` Preserve author order, any verified `(co-first)` designation, and available volume/page/article details. Omit unavailable bibliographic details. Existing publication citations do not bold the author's name.
- Keep journal italics as `<i>...</i>` inside the quoted YAML citation. The template displays the venue/year, excerpt, recommended citation, and a **Download Paper** link.
- Start the body with a brief description. Use **Highlights:** with bullet points for verified invitations, awards, or coverage. Longer entries may use `## Abstract`, `## Key Findings`, `## Public Health Significance`, and `## Media Coverage` when supported by source material.
- For the 2026 community-engagement paper, retain the exact note **Invited by the Editor-in-Chief.** in the excerpt and highlights. Crossref records its online publication date as October 23, 2026, for DOI `10.1038/s41370-026-00996-y`.
- Do not fabricate abstracts, impact factors, volume numbers, pages, or media coverage. A publication update does not automatically require editing the separately maintained CV PDF or adding a news post.

### Projects

- Keep the user-facing label **Projects** even though the collection and URL use `portfolio`.
- Entries are HTML files with YAML fields `title`, `excerpt`, and `collection: portfolio`.
- The excerpt contains a short project/activity caption, `<br/>`, and an `<img>` referencing an image in `images/`. Existing project images use `width='800' height='600'`.
- Preserve the simple image-led list and existing collection ordering; do not introduce a grid or date-based sorting for routine content additions.
- Use HTML in `.html` bodies; use Markdown only in `.md` bodies.

### News & Press

- Create `_posts/YYYY-MM-DD-descriptive-slug.md` with `title`, `date`, `permalink: /posts/YYYY/MM/descriptive-slug/`, and a YAML list of `tags`.
- Start with a concise summary of the news, recognition, presentation, or coverage. Without an explicit `excerpt`, the first paragraph supplies the archive summary.
- Follow the relevant existing post's structure: `## Media Coverage`, `## Event Details`, `## Award Announcement`, or similar descriptive headings; bold metadata labels such as **Article:**, **Published:**, **Event:**, and **Announcement:**; link to the original source.
- Where relevant, include `## Related Research` linking to the local publication page.
- Images are optional. Existing illustrated news posts use `width: 100%; max-width: 1000px; height: auto; margin-bottom: 20px;`.
- Preserve year grouping and newest-first ordering. The tab label is **News & Press**, not the upstream template's Blog Posts label.

### CV

- Despite the `/cv-json/` route and the presence of `_data/cv.json`, the active page displays a PDF through `_includes/cv-template.html`. Editing the JSON does not update the displayed CV.
- Keep **Download CV as PDF** above the viewer, with both links pointing to the same PDF under `files/`. The current file is `CV_Yuan_Yao_UCLA_09232026.pdf`; update both references together when replacing the CV.
- Keep `author_profile: false`, the `/resume-json` redirect, and the current archive layout.
- The current CV-specific `.archive` styling centers the content at 80% width, changing to 70% at `min-width: 80em`, with no float or right padding.
- The viewer wrapper is 100% wide and 800px high, with a 2em bottom margin, a `1px solid #ccc` border, 8px rounded corners, and a subtle shadow. The iframe currently has 120% width and height and no border. These are recorded existing settings, not general sizing recommendations; change them only as part of a requested layout fix.
- Keep the single active download button. The extra links in `_pages/cv-json.md` are intentionally commented out. Do not switch to the inactive `_layouts/cv-layout.html` or Markdown CV as part of a content update.

### Inactive tabs and utility pages

- Talks, Teaching, the Markdown CV (`/cv/`), and Guide (`/markdown/`) are commented out in navigation. Their pages still exist; do not enable them for unrelated updates or treat their sample content as Yuan Yao's credentials.
- Talks use `_talks/*.md` with `title`, `collection: talks`, `type`, `permalink`, `venue`, `date`, and `location`; `_pages/talks.html` renders the reversed collection with `_includes/archive-single-talk.html`.
- Teaching uses `_teaching/*.md` with the corresponding `collection: teaching` and similar metadata; `_pages/teaching.html` renders the reversed collection with `_includes/archive-single.html`.
- Sitemap, category/tag archives, collection archives, terms, and other template pages are utility pages, not additional active header tabs.

## Shared styling and paths

- Preserve the Academic Pages theme, existing typography, colors, spacing, header, author sidebar, and light/dark theme support during content edits. The configured theme is `default`.
- Shared styles enter through `assets/css/main.scss`, with theme variables under `_sass/theme/` and layout rules under `_sass/layout/`. Prefer existing classes and theme variables for requested style changes.
- Reuse the archive templates rather than duplicating publication, project, or news markup in each entry.
- Keep photos proportional where the existing responsive styles apply. Add meaningful image alt text to new images.
- The current `_config.yml` sets `url` to `https://yuanyao22.github.io/yuanyao.github.io` and `baseurl` to an empty string. Some older image links explicitly include `/yuanyao.github.io/`. Inspect the relevant page and `_includes/base_path` before constructing links; avoid duplicating the project path or changing deployment configuration incidentally.
- Keep agent instructions out of the published site: `AGENTS.md` belongs in the Jekyll `exclude` list.

## Validation

- Inspect `git status` before editing and preserve unrelated user changes.
- For content updates, validate YAML front matter, date/permalink consistency, required fields, source links, and referenced local assets. Run `git diff --check`.
- When the Ruby dependencies are available, run `bundle exec jekyll build` and inspect the affected archive and detail pages. Use `bundle exec jekyll serve -l -H localhost` for visual checks when needed.
- If dependencies are unavailable, report that a full build was not run and state the checks actually completed. Do not describe source-only checks as a rendered-site test.
