---
title: 如何编写和推送博客
date: 2026-05-24 14:00:00
categories: 博客搭建
tags:
  - Hexo
  - Fluid
  - 教程
---

## 前言

本博客基于 Hexo + Fluid 主题搭建，使用 GitHub Actions 自动部署到 GitHub Pages。本文介绍日常编写和发布博客的完整流程。

<!-- more -->

## 目录结构

```
myblog/
├── source/
│   └── _posts/          # 文章存放目录
├── themes/              # 主题目录
├── _config.yml          # 站点配置
└── .github/workflows/   # 自动部署配置
```

## 编写文章

### 创建新文章

进入博客目录，使用 Hexo 命令创建：

```bash
cd myblog
npx hexo new "文章标题"
```

执行后会在 `source/_posts/` 下生成 `文章标题.md` 文件，带有默认的 front-matter 头部：

```yaml
---
title: 文章标题
date: 2026-05-24 12:00:00
tags:
---
```

### Front-matter 说明

| 字段 | 说明 |
|------|------|
| `title` | 文章标题 |
| `date` | 发布日期 |
| `categories` | 分类（只能有一个） |
| `tags` | 标签（可多个） |

示例：

```yaml
---
title: 如何编写和推送博客
date: 2026-05-24 14:00:00
categories: 博客搭建
tags:
  - Hexo
  - Fluid
  - 教程
---
```

### 插入摘要

在文章中插入 `<!-- more -->`，其前的内容会显示在首页作为摘要，之后的部分需要点击"阅读全文"查看。

### 本地预览

```bash
npm run server
```

访问 http://localhost:4000/blogs/ 预览效果。

## 标签和分类

Hexo 的标签和分类**无需手动创建页面**，只需在文章的 front-matter 中声明即可：

- **分类**：`categories: 博客搭建`
- **标签**：`tags: [Hexo, Fluid]`

Hexo 构建时会自动生成对应的分类页和标签页。

## 发布文章

### 提交到 GitHub

```bash
git add .
git commit -m "add: 文章标题"
git push origin main
```

### 自动部署

代码推送到 `main` 分支后，GitHub Actions 会自动执行以下操作：

1. 检出代码
2. 安装依赖
3. 执行 `hexo generate` 生成静态页面
4. 推送到 `gh-pages` 分支
5. GitHub Pages 从 `gh-pages` 分支部署上线

整个过程约 1 分钟，完成后刷新博客地址即可看到新文章。

## 常用命令速查

| 命令 | 作用 |
|------|------|
| `npx hexo new "标题"` | 创建新文章 |
| `npm run server` | 本地预览 |
| `npm run build` | 生成静态文件 |
| `npm run clean` | 清除缓存 |

## 总结

日常发博客就三步：

1. **`npx hexo new "标题"`** 创建文章
2. 在 `source/_posts/` 下编辑 Markdown
3. **`git push`** 到 main 分支，等 Actions 自动部署

无需手动运行 `hexo generate` 或 `hexo deploy`，CI/CD 流水线已全部接管。
