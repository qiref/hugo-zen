# Hugo Zen

**Hugo Zen** is a clean, minimalist Hugo theme inspired by [hugo-xmin](https://github.com/yihui/hugo-xmin) and GitHub Primer Light.

## Features

- **Minimalist Typography & Layout**: Clean reading experience with responsive layout (`max-width: 800px`).
- **Instant `⌘K` / `/` Search Modal**: Built-in client-side full-text search with keyword highlighting and keyboard navigation (`/index.json`).
- **Floating Minimal TOC Sidebar**: Subtle line-indicator sidebar on desktop that expands into an interactive table of contents card on hover with active scroll-spy.
- **Post Contribution Heatmap**: GitHub-style 5-year post activity heatmap on the homepage.
- **Tag Cloud Pill Matrix**: Clean pill matrix with post counts on taxonomy pages.
- **Atom One Light Syntax Highlighting**: Zero-JS compile-time syntax highlighting powered by Hugo Chroma.
- **Parameterized Integrations**: Built-in support for Google Analytics (`gtag.js`), MathJax/KaTeX passthrough, and Utterances comments.

## Quick Start (`config.yaml`)

```yaml
baseurl: "https://example.com/"
languageCode: "cn-zh"
defaultContentLanguage: "zh"
title: "My Blog"
theme: "hugo-zen"
googleAnalytics: "G-XXXXXXXXXX"
enableEmoji: true
footnotereturnlinkcontents: "↩"

outputs:
  home: ["HTML", "RSS", "JSON"]

params:
  description: "Personal blog built with Hugo and hugo-zen."
  footer: "&copy; powered by [Hugo](https://gohugo.io/) & [Hugo Zen](https://github.com/qiref/hugo-zen) 2017 -- {Year}"
  homePostLimit: 25
  enableHeatmap: true
  enableSearch: true
  utterances:
    repo: "username/repo"
    issueTerm: "pathname"
    label: "Comment"
    theme: "github-light"

markup:
  tableOfContents:
    startLevel: 2
    endLevel: 4
    ordered: false
  highlight:
    codeFences: true
    noClasses: false
    guessSyntax: false
    tabWidth: 4
```
