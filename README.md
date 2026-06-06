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

Make sure the gem bin folder is on your PATH. If `jekyll` is not recognized after install, add this to your PATH permanently:

```powershell
[Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\Users\<you>\.local\share\gem\ruby\3.4.0\bin", "User")
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

Jekyll will watch for file changes and rebuild automatically. Refresh your browser to see updates. Press `Ctrl+C` to stop the server.

### Deploy to GitHub Pages

Push to the `main` branch — GitHub Pages builds and deploys automatically:

```powershell
git add .
git commit -m "Your message"
git push
```

The live site updates at `https://hyounjunchang.github.io` within a minute or two.

---

## 2. Add Photos to an Article

### Step 1 — Add your image files

Place your images in `assets/images/`, organized by subtopic:

```
assets/images/
  photography/
    landscape/
      my-photo-01.jpg
      my-photo-02.jpg
    street/
    portrait/
```

Keep file sizes under 1–2 MB per image for fast page loads.

### Step 2 — Create or open the article file

Article files live in `_projects/<topic>/<subtopic>/your-article.md`.

Example: `_projects/photography/landscape/rocky-mountain-shoot.md`

### Step 3 — Add the front matter and photo_gallery list

```yaml
---
layout: article
title: "Rocky Mountain Shoot"
description: "A landscape session at RMNP in early spring."
topic: photography
topic_title: Photography
subtopic: landscape
subtopic_title: Landscape
date: 2026-06-01
tags: [landscape, nature, Colorado]
photo_gallery:
  - src: /assets/images/photography/landscape/my-photo-01.jpg
    caption: "Bear Lake at sunrise"
  - src: /assets/images/photography/landscape/my-photo-02.jpg
    caption: "Trail Ridge Road overlook"
---

Write your article content here in Markdown...
```

- `src` — path to the image from the site root (required)
- `caption` — text shown below the image (optional)

The photo grid renders automatically below your written content. Add as many entries to `photo_gallery` as you need.

---

## 3. Add a PDF Report to a Project

PDFs are attached at the **subtopic** level (one report per project), not per article.

### Step 1 — Add your PDF file

Place your PDF in the `assets/pdfs/` folder:

```
assets/pdfs/
  my-project-report.pdf
```

### Step 2 — Open the subtopic file

Subtopic files live at `_projects/<topic>/<subtopic>.md`.

Example: `_projects/cu-boulder-embedded/piano-tiles-led.md`

### Step 3 — Add the pdf field to the front matter

```yaml
---
layout: subtopic
title: "Piano Tiles LED Game"
slug: piano-tiles-led
topic: cu-boulder-embedded
topic_title: "CU Boulder: Embedded Systems Engineering Projects"
description: "A Raspberry Pi-based Piano Tiles game."
pdf: /assets/pdfs/piano-tiles-led-report.pdf
---
```

The page will automatically display an embedded PDF viewer and a Download button.
If the `pdf:` field is omitted, no viewer is shown.
