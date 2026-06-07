# hyounjunchang.github.io

Personal portfolio and project site built with Jekyll and hosted on GitHub Pages.

---

## 1. Build and Run Locally

### Prerequisites

- Ruby 3.x ([rubyinstaller.org](https://rubyinstaller.org/downloads/) — use the Ruby+Devkit installer on Windows)
- Bundler and Jekyll installed via:

```powershell
gem install bundler jekyll
```

Make sure the gem bin folder is on your PATH. If `jekyll` is not recognized after install, add this permanently:

```powershell
[Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\\Users\\<you>\\.local\\share\\gem\\ruby\\3.4.0\\bin", "User")
```

Then close and reopen PowerShell.

### Install dependencies

From the site root folder:

```powershell
bundle install
```

### Run the local server

```powershell
bundle exec jekyll serve
```

Open your browser to [http://localhost:4000](http://localhost:4000).

Jekyll watches for file changes and rebuilds automatically. Refresh your browser to see updates. Press `Ctrl+C` to stop the server.

### Deploy to GitHub Pages

Push to the `main` branch — GitHub Pages builds and deploys automatically:

```powershell
git add .
git commit -m "Your message"
git push
```

The live site updates at `https://hyounjunchang.github.io` within a minute or two.

---

## 2. Add a New Topic

A topic is a top-level category shown on the home page (e.g. "Photography", "Quantitative Finance").

### Step 1 — Create the topic page

Create `_projects/<your-topic-slug>.md`:

```yaml
---
layout: topic
title: "Your Topic Title"
slug: your-topic-slug
description: "A short description shown on the topic card."
---
```

The `slug` must exactly match the filename (without `.md`) and becomes the URL: `/projects/your-topic-slug/`.

### Step 2 — Add a card to the home and projects pages

Open `index.md` and `projects/index.md` and add a card inside the `<div class="topic-grid">` block:

```html
<a class="topic-card" href="{{ '/projects/your-topic-slug/' | relative_url }}">
  <h2>Your Topic Title</h2>
  <p>Short description for the card</p>
</a>
```

---

## 3. Add a New Subtopic

A subtopic sits under a topic and groups related articles (e.g. "Landscape" under "Photography").

### Step 1 — Create the subtopic file

Create `_projects/<topic-slug>/<subtopic-slug>.md`:

```yaml
---
layout: subtopic
title: "Subtopic Title"
slug: subtopic-slug
topic: topic-slug
topic_title: "Topic Title"
description: "Short description."
---

Write an overview paragraph here. This appears in a highlighted box at the top of the subtopic page.
```

- `topic` — must match the parent topic's `slug`
- `slug` — must match the filename (without `.md`)

### Step 2 — (Optional) Attach a PDF report

Add a `pdf:` field to the front matter and place the file in `assets/pdfs/`:

```yaml
pdf: /assets/pdfs/your-report.pdf
```

---

## 4. Add a New Article

An article is a written page that lives under a subtopic.

### Step 1 — Create the article file

Create `_projects/<topic-slug>/<subtopic-slug>/<article-slug>.md`:

```yaml
---
layout: article
title: "Article Title"
description: "One line summary shown in the subtopic article list."
topic: topic-slug
topic_title: "Topic Title"
subtopic: subtopic-slug
subtopic_title: "Subtopic Title"
date: 2026-06-01
tags: [tag1, tag2]
---

Write your article content here in Markdown.

## Section Heading

More content...
```

- `topic` / `subtopic` — must match the parent slugs exactly
- `topic_title` / `subtopic_title` — display names used in breadcrumbs
- `tags` — optional, shown as labels on the article

The article automatically appears in the subtopic's article list.

---

## 5. Add Photos to an Article

### Step 1 — Add image files

Place images in `assets/images/`, organized by topic:

```
assets/images/
  photography/
    landscape/
      my-photo-01.jpg
      my-photo-02.jpg
```

Keep files under 1–2 MB per image for fast page loads.

### Step 2 — Add photo_gallery to the article front matter

```yaml
photo_gallery:
  - src: /assets/images/photography/landscape/my-photo-01.jpg
    caption: "Bear Lake at sunrise"
  - src: /assets/images/photography/landscape/my-photo-02.jpg
    caption: "Trail Ridge Road overlook"
```

- `src` — path from the site root (required)
- `caption` — text shown below the image (optional)

The photo grid renders automatically below your written content.

---

## 6. Add a PDF Report to a Project

### Step 1 — Add the PDF file

Place your PDF in `assets/pdfs/`:

```
assets/pdfs/my-project-report.pdf
```

### Step 2 — Add the pdf field to the subtopic front matter

```yaml
pdf: /assets/pdfs/my-project-report.pdf
```

The page automatically shows an embedded viewer and a Download button. Omit `pdf:` to hide the viewer.

---

## 7. Feature an Article on the Home Page

Any article or subtopic can be featured in the "Featured Articles" section at the top of the home page.

### Step 1 — Add featured: true to the front matter

Open the article or subtopic `.md` file you want to feature and add one line:

```yaml
---
layout: article
title: "Board 4: Instrument Droid"
description: "Thevenin Resistance/Voltage Measurement Droid with I2C"
topic: ecen5730-pcb
topic_title: "ECEN5730: PCB Design"
featured: true
---
```

The card will automatically appear in the Featured Articles section on the home page, showing the title, description, and topic name. To unfeature it, delete the line or set `featured: false`.

---

## 8. Add a YouTube Video to a Project

YouTube videos are embedded at the **subtopic** level and appear between the overview box and the PDF viewer.

### Step 1 — Find the video ID

The video ID is the part after `youtu.be/` or `?v=` in the URL:

```
https://youtu.be/vM8HINWoOFc        → ID is vM8HINWoOFc
https://youtube.com/watch?v=vM8HINWoOFc  → ID is vM8HINWoOFc
```

### Step 2 — Add the youtube field to the subtopic front matter

```yaml
---
layout: subtopic
title: "My Project"
slug: my-project
topic: ecen5730-pcb
topic_title: "ECEN5730: PCB Design"
description: "Project description."
youtube: vM8HINWoOFc
---
```

The video renders automatically as a centered, responsive 16:9 embed. Omit `youtube:` to hide it.

---

## Quick Reference

| What to add | Where to create the file |
|---|---|
| New topic | `_projects/<topic-slug>.md` + card in `index.md` and `projects/index.md` |
| New subtopic | `_projects/<topic-slug>/<subtopic-slug>.md` |
| New article | `_projects/<topic-slug>/<subtopic-slug>/<article-slug>.md` |
| Photos | `assets/images/<topic>/` |
| PDF reports | `assets/pdfs/` |
| YouTube video | `youtube: VIDEO_ID` in subtopic front matter |
| Feature on home page | `featured: true` in any article or subtopic front matter |
