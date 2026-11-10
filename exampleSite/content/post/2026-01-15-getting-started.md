---
title: "Hugo Zen 主题快速上手与排版指南"
date: 2026-01-15
author: "Hugo Zen"
tags: ["Hugo", "Theme", "Guide"]
categories: ["Documentation"]
toc: true
---

本文展示 **Hugo Zen** 主题的正文排版、多级标题阶梯、表格、引用块、代码高亮以及右侧悬浮目录（TOC）的交互效果。

---

## 一、快速配置

在站点根目录的 `config.yaml` 中指定 `theme: "hugo-zen"`，并开启 JSON 搜索索引输出与 Chroma 编译期语法高亮：

```yaml
theme: "hugo-zen"

outputs:
  home: ["HTML", "RSS", "JSON"]

markup:
  highlight:
    codeFences: true
    noClasses: false
    guessSyntax: false
    tabWidth: 4
```

## 二、代码高亮展示

### 1. Go 语言示例

```go
package main

import (
	"context"
	"fmt"
	"time"
)

// Server 定义极简 HTTP 服务配置
type Server struct {
	Addr    string
	Timeout time.Duration
}

func NewServer(addr string) *Server {
	return &Server{
		Addr:    addr,
		Timeout: 5 * time.Second,
	}
}

func (s *Server) Start(ctx context.Context) error {
	fmt.Printf("listening on %s (timeout=%v)\n", s.Addr, s.Timeout)
	return nil
}
```

### 2. Java 语言示例

```java
package io.zen.demo;

import java.util.List;
import java.util.stream.Collectors;

public class StreamExample {
    private static final int THRESHOLD = 100;

    @Override
    public String toString() {
        return "StreamExample[threshold=" + THRESHOLD + "]";
    }

    public List<String> filterActive(List<String> items) {
        return items.stream()
                .filter(item -> item != null && !item.isEmpty())
                .map(String::trim)
                .collect(Collectors.toList());
    }
}
```

## 三、表格与引用排版

### 1. 数据表格

| 组件模块 | 快捷键 / 触发方式 | 依赖方式 |
| :--- | :--- | :--- |
| 全文搜索面板 | `⌘K` / `Ctrl+K` 或 `/` | 编译期 `/index.json` + 原生 JS |
| 悬浮章节目录 | 滚动监听 + 鼠标悬停展开 | Hugo `.TableOfContents` |
| 语法高亮 | 编译期自动渲染 | Hugo Chroma (`Atom One Light`) |

### 2. 引用块与行内代码

> 大道至简：好的工具应当在阅读时隐形，只留下清晰的结构与内容本身。通过 `:not(pre) > code` 规则，正文中的行内代码如 `go build -o app` 与标题中的 `Server.Start()` 均能保持恰当的字号比例。
