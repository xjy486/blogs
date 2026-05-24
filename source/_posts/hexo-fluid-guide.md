---
title: 如何在 Hexo 博客中插入图片
date: 2026-05-24 13:18:36
tags:
  - Hexo
  - Fluid
  - 教程
categories:
  - 博客搭建
---

## 欢迎使用 Hexo + Fluid

这是一篇示例文章，演示如何在博客中插入图片。

### 图片插入方法

由于开启了 `post_asset_folder`，每篇文章都有一个同名的资源文件夹，可以将图片放在里面。

#### 方法 1：使用 Markdown 语法（推荐）

```markdown
![图片描述](hexo-logo.png)
```

#### 方法 2：使用 Hexo 标签

```markdown
{% asset_img hexo-logo.png 图片描述 %}
```

#### 方法 3：使用绝对路径

```markdown
![图片描述](/blogs/hexo-fluid-guide/hexo-logo.png)
```

### 示例图片

下面是一张示例图片：

![Hexo Logo](hexo-logo.png)

> 提示：将图片放入与文章同名的文件夹中（`source/_posts/hexo-fluid-guide/`），然后在文章中直接引用文件名即可。

### 图片存放位置

```
source/
  _posts/
    hexo-fluid-guide.md       # 文章文件
    hexo-fluid-guide/         # 资源文件夹（自动生成）
      hexo-logo.png           # 文章配图
```

### 新建带图片的文章步骤

1. 执行 `hexo new post "文章标题"`，会自动创建 `.md` 文件和同名文件夹
2. 将图片放入同名文件夹中
3. 在文章中用 `![描述](图片文件名)` 引用
4. 执行 `hexo generate` 或 `hexo server` 查看效果

祝 blogging 愉快！
