# Hugo Zen

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/qiref/hugo-zen/blob/master/LICENSE.md)
[![Hugo](https://img.shields.io/badge/Hugo-%E2%89%A50.100.0-ff4088.svg)](https://gohugo.io)

**Hugo Zen** is a fast, clean, and minimalist Hugo theme designed for technical blogs, architecture essays, and personal notes. Inspired by [hugo-xmin](https://github.com/yihui/hugo-xmin) and GitHub Primer Light, it delivers modern reading ergonomics—instant `⌘K` search, a floating scroll-spy table of contents, a 5-year post contribution heatmap, and zero-JS compile-time syntax highlighting—without heavy frontend frameworks.

[**Live Demo**](https://qiref.github.io) · [**中文文档**](#-中文文档)

---

## ✨ Features

- **Minimalist Typography & Reading Layout**: Focused single-column layout (`max-width: 800px`) with GitHub Primer-inspired typography, clean tables, and subtle dividers.
- **Instant `⌘K` / `/` Full-Text Search**: Built-in client-side search modal with glassmorphism backdrop, keyword highlighting, snippet extraction, and full keyboard navigation (`↑` `↓` `↵` `ESC`).
- **Floating Minimal TOC Sidebar**: Unobtrusive line-indicator on the right margin that expands into a frosted-glass Table of Contents card on hover, complete with active heading scroll-spy and smooth scrolling.
- **5-Year Contribution Heatmap**: GitHub-style post activity heatmap automatically rendered on the homepage.
- **Tag Cloud Pill Matrix**: Clean taxonomy pill badges with post counts.
- **Atom One Light Syntax Highlighting**: Zero-JS, compile-time syntax highlighting powered by Hugo's native Chroma lexer.
- **Dual Content Sections (`post` & `note`)**: Separate long-form technical articles (`post`) from lightweight daily notes (`note`).
- **Zero Hardcoding & Extensible**: Native configuration for Google Analytics (`gtag.js`), Utterances comments, MathJax/KaTeX passthrough, and custom head/footer partial hooks.

---

## 🚀 Installation

### Option 1: Git Submodule (Recommended)

From the root of your Hugo site:

```bash
git submodule add https://github.com/qiref/hugo-zen.git themes/hugo-zen
```

Then set `theme: "hugo-zen"` in your `config.yaml` (or `hugo.yaml`).

To update the theme later:

```bash
git submodule update --remote --merge themes/hugo-zen
```

### Option 2: Clone Directly

```bash
git clone https://github.com/qiref/hugo-zen.git themes/hugo-zen
```

### Running the Built-in Demo (`exampleSite`)

You can preview the theme immediately using the bundled `exampleSite`:

```bash
git clone https://github.com/qiref/hugo-zen.git
cd hugo-zen
hugo server -s exampleSite --themesDir ../..
```

---

## ⚙️ Configuration

Below is a complete `config.yaml` reference:

```yaml
baseurl: "https://example.com/"
languageCode: "en-us" # or "cn-zh"
defaultContentLanguage: "zh"
title: "My Blog"
theme: "hugo-zen"

# Optional: Google Analytics 4 Measurement ID
googleAnalytics: ""

enableEmoji: true
footnotereturnlinkcontents: "↩"

permalinks:
  note: "/note/:year/:month/:day/:slug/"
  post: "/post/:year/:month/:day/:slug/"

# Required for Cmd+K instant search (/index.json)
outputs:
  home: ["HTML", "RSS", "JSON"]

menu:
  main:
    - name: Home
      url: "/"
      weight: 1
    - name: Posts
      url: "post/"
      weight: 2
    - name: Tags
      url: "tags/"
      weight: 3
    - name: Note
      url: "note/"
      weight: 4
    - name: About
      url: "about/"
      weight: 5
    - name: Subscribe
      url: "index.xml"
      weight: 6

params:
  description: "Personal blog powered by Hugo and hugo-zen."
  footer: "&copy; powered by [Hugo](https://gohugo.io/) & [Hugo Zen](https://github.com/qiref/hugo-zen) 2017 -- {Year}"
  homePostLimit: 25       # Number of recent posts displayed on the homepage
  enableHeatmap: true     # Show 5-year post contribution heatmap on the homepage
  enableSearch: true      # Enable Cmd+K / Ctrl+K search trigger and modal
  utterances:
    repo: ""              # e.g. "username/repo" (leave empty to disable comments)
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
    noClasses: false      # Required: use semantic Chroma CSS classes
    guessSyntax: false
    tabWidth: 4
  goldmark:
    renderer:
      unsafe: true
    extensions:
      passthrough:
        enable: true
        delimiters:
          block:
            - - \[
              - \]
            - - $$
              - $$
          inline:
            - - \(
              - \)
```

---

## 📝 Front Matter Parameters

You can customize individual posts via YAML front matter:

```yaml
---
title: "Understanding Distributed Consensus"
date: 2026-01-15
author: "Your Name"
tags: ["Distributed Systems", "Go"]
categories: ["Architecture"]
toc: true # Set to false to hide the floating TOC sidebar on a specific post
---
```

| Parameter | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `title` | `string` | Required | Article title |
| `date` | `date` | Required | Publication date (`YYYY-MM-DD`) |
| `author` | `string` | Optional | Author name displayed in article metadata |
| `tags` | `string[]` | `[]` | Tags rendered as pills in metadata and `/tags/` |
| `categories` | `string[]` | `[]` | Categories rendered in metadata |
| `toc` | `boolean` | `true` | Toggle the right-hand floating TOC sidebar |

---

## 🔌 Customization Hooks

**Hugo Zen** provides two clean partial hooks so you can inject custom CSS, fonts, or scripts without overriding core templates:

- `layouts/partials/head_custom.html`: Injected right before `</head>`.
- `layouts/partials/foot_custom.html`: Injected inside `<footer>` before `</body>`.

---

## 📖 中文文档

**Hugo Zen** 是一款极简、克制、高性能的 Hugo 博客主题，基于 [hugo-xmin](https://github.com/yihui/hugo-xmin) 深度演进而来，专为长篇技术博客、源码解析与日常笔记打造。

### 核心特性

1. **`⌘K` 全文搜索弹窗**：基于编译期生成的 `/index.json`，支持 `⌘K`（macOS）/ `Ctrl+K`（Windows/Linux）或 `/` 键快速唤出，支持多关键词匹配高亮与键盘上下键导航。
2. **极简右侧悬浮目录（TOC）**：默认在正文右侧显示极简短横线指示器（随标题层级呈现不同长度），鼠标悬停时展开毛玻璃目录卡片，并随页面滚动自动高亮当前章节。
3. **五年发文贡献热力图**：首页底部自动统计近 5 年每月的发文频次，生成仿 GitHub 风格的绿色渐变热力图。
4. **Atom One Light 编译期代码高亮**：直接利用 Hugo 内置的 Chroma 词法分析器在编译期生成静态高亮 HTML，无需加载任何前端 `highlight.js` 脚本，首屏零闪烁。
5. **双内容分区（`post` 与 `note`）**：支持将正式长文放在 `content/post/`（展示在首页与热力图中），将日常随手记放在 `content/note/`（独立归档在 Note 栏目）。

### 快速安装

在你的 Hugo 博客根目录下执行：

```bash
git submodule add https://github.com/qiref/hugo-zen.git themes/hugo-zen
```

然后在 `config.yaml` 中设置 `theme: "hugo-zen"`，并确保开启以下两项配置以支持搜索索引与 Chroma 代码高亮：

```yaml
outputs:
  home: ["HTML", "RSS", "JSON"]

markup:
  highlight:
    codeFences: true
    noClasses: false
    guessSyntax: false
    tabWidth: 4
```

---

## 📄 License & Credits

Released under the [MIT License](https://github.com/qiref/hugo-zen/blob/master/LICENSE.md).
Originally inspired by [Yihui Xie's hugo-xmin](https://github.com/yihui/hugo-xmin).
