# 贡献指南

感谢你对「少女心事」的兴趣！

## 快速开始

1. Fork 本仓库
2. 在 `_stories/` 新建 `.md` 文件（格式见下方）
3. 提交 Pull Request

## 故事文件格式

文件命名：`编号-标题.md`（如 `002-体育课.md`）

```markdown
---
title: "故事标题"
author: "笔名"
date: 2026-03-30
tags: [智识, 友谊]
status: seed
---

正文内容，使用 Markdown 格式。
```

**status 取值：** `seed`（种子）/ `growing`（生长中）/ `complete`（完成）

**常用 tags：** 智识、友谊、野心、贫穷、身体、竞争、家庭、成长

## 续写故事

在原文件末尾添加段落，将 `author` 改为 `"原作者 & 你的笔名"`。

## 本地预览

```bash
bundle install
bundle exec jekyll serve
```

访问 `http://localhost:4000/`

## 贡献者协议

提交 PR 即表示你同意：
- 将出版权授予本项目
- 保留署名权
- 知悉所有出版收入全部捐赠

## 审稿标准

我们不评判文笔，只关注真诚与尊重。
