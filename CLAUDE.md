# TonBo VPN 博客 — CLAUDE.md

Jekyll 静态博客，托管于 GitHub Pages（`Speedlinc.github.io`），为 TonBo VPN 产品提供多语言内容营销。

---

## 一、Git 身份（最高红线）

**每次提交前必须验证 repo 级别的 git 身份，绝不能用全局身份暴露个人信息。**

```bash
# 验证（必做）
git config --local user.email
git config --local user.name

# 若未设置，执行：
git config --local user.email "213979269+Speedlinc@users.noreply.github.com"
git config --local user.name "Speedlinc"

# 推送使用 SSH Host Alias
git push origin main   # remote 已配置为 github.com:Speedlinc/Speedlinc.github.io.git
```

全局 git config 含个人真实身份（Bamboo742 / Jim），**绝不能出现在此仓库的任何提交中**。

---

## 二、产品定位

**TonBo VPN（通博VPN）** — 全球 AI VPN / 网络加速器

| 核心卖点 | 描述 |
|---------|------|
| IEPL 国际专用线 | 非公共云，最短路由，峰时稳定 |
| AI 平台优化 | ChatGPT / Claude / Gemini / Sora 专项优化 |
| 全平台支持 | Windows / macOS / iOS / Android |
| 免费额度 | 每日 200MB，无需信用卡 |
| 邀请奖励 | 邀请好友双方各得 $1，消费返 20% |

官网：`https://www.tonbovpn.com/`

### 写文章时的产品描述规范
- ✅ 用：网络加速器、AI VPN、全球加速、稳定连接、IEPL 专线
- ✅ 用：访问 ChatGPT / Claude / Netflix（不说"翻墙"）
- ❌ 禁：梯子、翻墙、科学上网、FQ（合规用词）

---

## 三、提交规范

```
<type>: <简短描述>

# type 列表
feat     新文章、新功能
fix      修复 bug、修正内容
chore    配置变更、依赖更新
refactor 代码重构
docs     文档更新
perf     性能优化
ci       CI/CD 变更
```

示例：
```
feat: add Japanese post — ChatGPT stable connection guide
fix: correct hero SVG text for English lang page
chore: update navigation data for Turkish
```

---

## 四、文章写作规范

### 4.1 文件命名

```
# 中文文章（默认）
_posts/YYYY-MM-DD-{slug}.md

# 小语种文章
_posts/YYYY-MM-DD-{lang}-{slug}.md

# 示例
_posts/2026-06-29-chatgpt-lian-bu-shang-zen-me-ban.md   # zh
_posts/2026-06-29-ja-chatgpt-tonbo-vpn-stable.md        # ja
_posts/2026-06-29-en-tonbo-vpn-ai-streaming.md          # en
```

### 4.2 Front Matter 模板

```yaml
---
title: "文章标题"
date: YYYY-MM-DD HH:MM:SS +0800
categories: [分类]          # 见下方分类表
tags: [标签1, 标签2, 标签3]
lang: zh                    # zh / en / vi / ja / ko / tr
excerpt: "一句话摘要，在文章卡片上显示，100字以内"
description: "SEO描述，160字以内，含主关键词"
image: /assets/images/covers/chatgpt.svg   # 封面图，见下方可用列表
---
```

### 4.3 可用封面图

| 文件 | 适用话题 |
|------|---------|
| `chatgpt.svg` | ChatGPT / Claude / AI 工具 |
| `claude.svg` | Claude 专题 |
| `dedicated-ip.svg` | 独享 IP / 账号安全 |
| `streaming.svg` | Netflix / 流媒体 |
| `sora-midjourney.svg` | AI 绘图 / Sora |
| `intro.svg` | 产品介绍 / 通用 |

### 4.4 分类参考

| 分类（中文） | 分类（英文） | 分类（日文） |
|------------|-----------|-----------|
| AI工具 | AI Tools | AI活用 |
| 流媒体 | Streaming | エンタメ |
| 使用教程 | Tutorials | 使い方 |
| VPN评测 | VPN Reviews | VPNレビュー |

### 4.5 内容要求

- 字数：中文 800–1500 字，小语种 600–1200 字
- 结构：引言 → 问题 → 解决方案 → 实操步骤 → 总结
- 必须包含：一个 markdown 表格、一个 blockquote CTA（链接到官网）
- CTA 格式：`> 🚀 [立即免费下载](https://www.tonbovpn.com/zh/download) — 每日 200M 免费，邀请好友各得 $1`
- 语言页面 CTA 的链接使用对应语言 URL：`/zh/download`, `/en/download`, `/vi/download`, `/ja/download`, `/ko/download`, `/tr/download`

---

## 五、多语言结构

### 语言页面分布

| 语言 | 目录 | lang 值 | 文章 lang 标签 |
|------|------|--------|--------------|
| 中文（默认） | `/` | zh | zh |
| 英文 | `/en/` | en | en |
| 越南语 | `/vi/` | vi | vi |
| 日语 | `/ja/` | ja | ja |
| 韩语 | `/ko/` | ko | ko |
| 土耳其语 | `/tr/` | tr | tr |

每个语言目录下有 `index.html`，前置 matter 含 `lang: xx` 和该语言的介绍内容。

### 首页 Hero Banner（`_layouts/home.html`）

Hero 已实现语言联动，通过 Liquid 变量根据 `page.lang` 自动切换文字。如需修改 Hero 文案，编辑 `_layouts/home.html` 顶部的 `{% case lang %}` 代码块，共 4 个变量：

```liquid
h_badge   # 顶部角标，如 "TonBo VPN · 全球加速器"
h_title   # 主标题，如 "TonBo VPN 博客"
h_sub     # 副标题
h_cta     # 底部绿色条，如 "每日 200M 免费 · 邀请送 $1"
```

---

## 六、项目结构

```
Speedlinc.github.io/
├── _layouts/
│   ├── default.html      # 页面框架：head / header / footer / hreflang
│   ├── home.html         # 首页：Hero SVG + 文章列表（语言联动）
│   ├── post.html         # 文章页：双栏 + 侧边栏 CTA
│   ├── page.html         # 普通页面
│   └── category.html     # 分类页
├── _posts/               # 所有文章（zh 和小语种）
├── _data/
│   └── navigation.yml    # 各语言导航菜单配置
├── assets/
│   ├── css/style.css     # 全站样式（单文件）
│   ├── images/
│   │   ├── covers/       # 文章封面图（SVG）
│   │   ├── posts/        # 文章内配图（SVG）
│   │   └── site-header.svg  # （已废弃，Hero 已改为内联 SVG）
│   └── js/lazy-load.js   # 图片懒加载
├── en/ vi/ ja/ ko/ tr/   # 语言子目录，各含 index.html 和 category/
├── about/                # 关于页
├── index.html            # 中文首页（lang: zh）
├── _config.yml           # Jekyll 配置
├── BingSiteAuth.xml      # 必应站长验证（已配置）
└── .github/workflows/    # IndexNow 自动提交工作流
```

---

## 七、侧边栏 CTA（`_layouts/post.html`）

文章页侧边栏已实现多语言 CTA，显示 TonBo VPN 产品介绍 + 特性列表 + 下载按钮。修改时注意同步 6 种语言版本。

---

## 八、SEO 注意事项

- `_layouts/default.html` 中已配置 hreflang（6 种语言）
- `BingSiteAuth.xml` 已注册必应站长工具
- `.github/workflows/indexnow.yml` 每次推送 `_posts/**` 自动提交 IndexNow
- SEO 标题通过 `jekyll-seo-tag` 插件生成（读取 front matter 的 `title` / `description`）
