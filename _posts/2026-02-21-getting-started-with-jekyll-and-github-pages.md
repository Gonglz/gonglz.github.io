---
title: "Getting Started with Jekyll and GitHub Pages"
date: 2026-02-21
categories:
  - Tech
tags:
  - jekyll
  - github-pages
  - blogging
toc: true
---

If you're reading this, you might be wondering how this blog was built. It runs on **Jekyll** — a static site generator — hosted for free on **GitHub Pages**. Here's a quick overview of how it all fits together.

## What is Jekyll?

[Jekyll](https://jekyllrb.com/) is a static site generator written in Ruby. You write content in Markdown, configure your site with YAML, and Jekyll transforms everything into a static website — no database required.

## Why GitHub Pages?

[GitHub Pages](https://pages.github.com/) provides free hosting for static sites directly from a GitHub repository. For a site named `username.github.io`, GitHub automatically publishes it at `https://username.github.io`.

## The Minimal Mistakes Theme

This blog uses the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) theme by Michael Rose. It's one of the most popular Jekyll themes, offering:

- Clean, responsive design
- Multiple layout options
- Built-in search
- Author profiles
- Tag and category archives

## Creating a New Post

To write a new post, create a Markdown file in the `_posts/` directory following the naming convention:

```
YYYY-MM-DD-title-of-post.md
```

Each post starts with a YAML front matter block:

```yaml
---
title: "My Post Title"
date: 2026-02-21
categories:
  - Tech
tags:
  - example
---
```

Then write your content in Markdown below the `---` separator.

## Deploying

Simply push your changes to the `main` branch on GitHub, and GitHub Pages will automatically rebuild and deploy your site within a few minutes.

Happy blogging!
