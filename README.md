# Oral Health Quality — Lab Website

Source for **oralhealthquality.com**, the website of the Texas Center for Oral Healthcare Quality and Safety at UTHealth Houston.

Built with [Hugo](https://gohugo.io/) (a static site generator) and a custom theme, deployed automatically to GitHub Pages. The site is organized around **projects**; publications, products, and presentations connect upward to the project that produced them.

---

## How it works

- Content lives in `content/` as Markdown files with YAML front matter.
- The 8 research projects each have a folder under `content/projects/<slug>/`.
- Publications, products, and presentations are Markdown files placed inside their project's folder, each with a `project:` field linking it back.
- Grant details live once in `data/grants.yaml`; project pages reference them by `id`.
- Every push to `main` triggers a GitHub Action that builds the site and deploys it — live in about a minute.

You do not need to know HTML to add content. Just add or edit a Markdown file and commit it.

---

## Adding content (plain-English prompts)

You can ask Claude (Cowork or Claude Code) to do any of these:

**Add a publication**
> Add a publication to the *Dental Patient Safety* project. Title: …, authors: …, journal: …, year: …, DOI: …, one-sentence summary: …. Create it in `content/projects/dental-patient-safety/` as `pub-YYYY-slug.md` with `type: "publication"` and `project: "dental-patient-safety"`, then commit to main.

**Add a product/tool**
> Add a product to the *Caries Management Toolkit* project: title …, type toolkit, summary …, link …, featured yes. Create it in `content/projects/caries-management-toolkit/` and commit to main.

**Add a presentation**
> Add a presentation to the *dPROs* project: presented at … on … by …, type poster. Create it in `content/projects/dental-patient-reported-outcomes/` with `type: "presentation"` and commit to main.

**Add a news post**
> Add a news post titled …, related project …, body …. Create it in `content/news/` as `YYYY-MM-DD-slug.md` and commit to main.

**Add a team member**
> Add a team member: name, role, organization, bio. They work on projects X and Y. Create `content/team/firstname-lastname.md` and add them to the `team:` list in those projects' `_index.md`. Commit to main.

**Add a whole new project**
> Create a new project "…": grant …, summary …, team …. Make `content/projects/<slug>/_index.md` with `layout: project`, add the grant to `data/grants.yaml`, and commit to main.

---

## Front-matter fields

**Publication** — `title, date, type: "publication", authors[], journal, volume, issue, pages, year, doi, pubmed, project, summary, pdf, featured`

**Product** — `title, date, type: "product", product_type, summary, project, status, version, url, download, featured, tags[]`
(`product_type`: dataset, measure set, toolkit, dashboard, terminology, web tool, app, guideline, report, other)

**Presentation** — `title, date, type: "presentation", event, location, presenters[], presentation_type, slides, project, summary`

**Team member** — `title, slug, role, organization, department, email, image, weight, links[]`

**Project** (`_index.md`) — `title, slug, layout: project, status (active|completed), weight, start_year, end_year, summary, grants[], team[] ({role, member}), tags[]`

> Items auto-imported from PubMed and flagged `needs_review: true` had their project assigned by keyword and should be confirmed. Remove the flag once verified.

---

## Local preview (optional)

Requires Hugo Extended ≥ 0.147:

```bash
hugo server
# open http://localhost:1313
```

## Editing the design

The custom theme lives in `layouts/` (HTML templates) and `assets/css/main.css`. No external theme dependency.

---

## Custom domain

To point **oralhealthquality.com** at this site, see the DNS instructions in the launch notes (A records to GitHub Pages + `www` CNAME), then add a `static/CNAME` file containing `oralhealthquality.com` and enable *Enforce HTTPS* in Settings → Pages.
