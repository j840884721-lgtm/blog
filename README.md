# AI 学习日志（个人博客）

基于 Hugo + PaperMod 主题的静态博客，记录每日学习 & 研究 AI 的过程。
部署在 GitHub Pages，推送 `main` 分支后自动发布。

## 目录结构

- `hugo.yaml` — 站点配置（标题、菜单、主题参数）
- `content/posts/` — 博客文章（Markdown）
- `content/about.md` — 关于页
- `themes/PaperMod/` — 主题文件（已内置，无需额外安装）
- `.github/workflows/hugo.yml` — GitHub Pages 自动部署

## 本地使用

Hugo 主程序在 `D:/AI-Tools/hugo/hugo.exe`。

```bash
cd /d/AI-Projects/blog

# 本地预览（草稿也能看到），浏览器打开 http://localhost:1313
/d/AI-Tools/hugo/hugo.exe server -D

# 新建一篇文章
/d/AI-Tools/hugo/hugo.exe new content posts/2026-08-03-标题.md
# 或直接复制 content/posts/ 里的已有文章改 front matter
```

文章开头的 front matter 说明：

```yaml
---
title: "文章标题"
date: 2026-08-03T20:00:00+08:00
draft: false        # true 则发布时跳过这篇
tags: ["LLM", "论文"]
categories: ["日志"]
summary: 列表页显示的摘要，不写则自动截取。
---
```

## 发布流程（首次）

1. 注册 GitHub 账号，新建一个**公开**仓库（例如 `blog`），不要勾选初始化 README。
2. 把 `hugo.yaml` 和 `content/about.md` 里的 `yourname` 替换成你的 GitHub 用户名。
3. 在仓库页面：Settings → Pages → Source 选 **GitHub Actions**。
4. 本地推送：

```bash
cd /d/AI-Projects/blog
git init
git add -A
git commit -m "init blog"
git branch -M main
git remote add origin https://github.com/j840884721-lgtm/blog.git
git push -u origin main
```

5. 等 Actions 跑完（约 1 分钟），网站就能访问：
   `https://<用户名>.github.io/blog/`

之后每次写完文章，只需 `git add -A && git commit -m "xxx" && git push`，网站自动更新。
