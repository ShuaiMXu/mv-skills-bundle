---
name: ai-tech-wechat-writer
description: 微信公众号文章排版与发布技能。将用户提供的内容转换为公众号可发布的美化 HTML，采用 shaka-design-system 的主题系统 + 5 段式固定结构（今日AI头条→行业要闻→产品动态→观点短评→明日预告）。触发条件：用户提到「公众号」「微信文章」「写一篇文章」「排版」「生成HTML」「发到公众号」「美化日报」「生成公众号」「写公众号」「发公众号」「微信推送」「推文」「文章排版」等任何与微信公众号内容创作或发布相关的请求。关键规则：只要意图是产出公众号文章,无论措辞如何都必须触发此技能,不输出纯文本或裸 Markdown。本技能只负责排版和发布,不主动抓取新闻。
allowed-tools: Read, Write, Edit, Exec
---

# 微信公众号 · 排版发布技能

> 本技能将用户提供的内容整合为公众号风格的精美 HTML。
> **设计规则来自 `shaka-design-system`（共享设计系统）**，本技能只维护公众号业务特定结构。

---

## 📐 设计系统引用（必读）

在生成 HTML 前，**必须先读**共享设计系统的三个文件：

1. **主题配色**：`~/.claude/skills/shaka-design-system/references/themes.md`
   → 5 套主题（🖋墨水经典 / 🌊靛蓝瓷 / 🌿森林墨 / 🍂牛皮纸 / 🌙沙丘）
   → AI 日报默认用 **🌊 靛蓝瓷**

2. **组件库**：`~/.claude/skills/shaka-design-system/references/components.md`
   → callout / stat / pillar / tag / section-header / figure / rowline
   → **使用"内联 Style 版"**（公众号编辑器会剥离 class）

3. **字体层级**：`~/.claude/skills/shaka-design-system/references/fonts.md`
   → 衬线标题 / 无衬线正文 / 等宽装饰

4. **设计原则**：`~/.claude/skills/shaka-design-system/references/principles.md`
   → 特别关注"原则 3：节奏优于元素"应用到公众号段落交替

---

## 📋 固定模板结构（公众号业务约束）

发布到公众号的文章必须使用以下 5 段式结构：

```
📰 今日AI头条（1条 S级情报） ← Section Header + Callout
🔥 行业要闻（2-3条 A级情报） ← Section Header + Pillar(3柱) 或 Rowline
🚀 产品动态（1-2条工具/模型更新） ← Section Header + Stat 矩阵
💡 观点短评（Shaka的视角总结） ← Section Header + Callout（带 cite）
🔍 明日预告（留钩子引导关注） ← Section Header + 轻量 Tag 列表
```

**段落组件映射见 `references/layouts.md`**。

---

## 📜 内容规范

- 去掉「Shaka简评」，只保留客观叙事（但"观点短评"段可以有主观判断）
- 每条情报只保留**出处**（如：📡 来源：量子位），不要附带链接
- 不要加粗「Shaka说」「Shaka简评」等主观标签
- H1 标题在 Markdown 中用注释替代，发布时在公众号后台填写
- 封面图：AI 生成科技感封面

---

## ⚡ 执行流程

### 步骤 1：获取文章素材

素材来源按优先级：
1. 用户在当前对话中直接提供的内容
2. 用户指定的本地文件（使用 Read 工具读取）
3. 会话上下文中已有的素材

**不要主动去抓取新闻源**。若素材不足，先向用户确认补充。

### 步骤 2：问用户选主题（或推荐）

> 默认 **🌊 靛蓝瓷**（AI/科技调性最匹配）。只有用户明确要求换（"这次想轻松点" / "文化类内容"等），才从其他 4 套主题挑选。**不允许自定义 hex**——引导用户从 5 套预设选。

### 步骤 3：对齐段落节奏（按 principles.md 原则 3）

为防审美疲劳，**5 段式段落背景应交替**（以靛蓝瓷为例）：

| 段 | 背景 | 视觉层级 |
|----|------|---------|
| 📰 今日AI头条 | **深段**（paper-tint）| 视觉重点，震撼开头 |
| 🔥 行业要闻 | 浅段（paper）| 阅读松驰 |
| 🚀 产品动态 | **深段**（paper-tint）| 数据密度 |
| 💡 观点短评 | 浅段（paper）+ callout 深 | 阅读松驰 |
| 🔍 明日预告 | 浅段（paper）| 收尾轻盈 |

### 步骤 4：生成 HTML

按 `references/layouts.md` 的组件映射，组装完整 HTML。

**工作目录**：`/tmp/wechat_article_YYYY-MM-DD.html`

**颜色替换**：
- 从 `shaka-design-system/themes.md` 读取选定主题的 CSS 变量
- 在本 skill 的 `assets/template.html` 基础上替换（或直接内联）

### 步骤 5：跑 checklist 自检

检查清单：
- [ ] 5 段式结构完整（头条 / 要闻 / 动态 / 短评 / 预告）
- [ ] 每条情报有出处（📡 来源），无原文链接
- [ ] 没有 "Shaka 说" / "Shaka 简评" 字样
- [ ] 段落节奏深浅交替，不超过 2 段连续同色调
- [ ] 字体层级清晰：衬线标题 + 无衬线正文 + 等宽 kicker
- [ ] 所有样式内联（不依赖 `<style>` 块）
- [ ] 无 JS / `display:grid` / `position:fixed` / 外链 SVG

### 步骤 6：发布到公众号草稿箱（可选）

```bash
cd ~/.openclaw/workspace
python3 skills/ai-tech-intel/scripts/publish_wechat.py
```

或让用户手动复制 HTML 到公众号编辑器。

---

## 🔄 与其他工作流的边界

**不走本技能**的场景：
- **Product Hunt 每日推荐发布**：由独立 script 模式定时任务执行
- **其他由定时任务 script 模式驱动的公众号发布脚本**

本技能仅限"用户在对话中要求把已有素材排版成公众号文章"。

---

## 变更记录

- 2026-04-24：重构 v2 —— 引入 `shaka-design-system` 共享设计系统，从 5 段式 hardcode 背景色升级为"5 主题 × 节奏规划"，段落组件化（callout/stat/pillar）
