# MV Skills Bundle

> AI 漫剧 / MV 端到端制作流水线 · Claude Code Skills 套装
>
> **1 小时出方案，180 元跑成片** ── 实测降本 28 倍

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Skills-6-blue.svg)](#-包含-6-个-skill)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Compatible-purple.svg)](https://claude.com/code)

---

## 📖 这是什么

一套用 **GPT Image 2 + Seedance 2.0 + Suno V5** 做端到端 AI 漫剧 / MV 的 Skill 工作流。

**核心创新**：把 N 帧 Midjourney 单帧叙事重切为 **8 镜头 × 10-15s 长镜头**，每个镜头一张 **9 宫格 storyboard**（GPT Image 2），再用 Seedance 把 9 宫格变成 15s 长镜头视频，最后 Suno 配乐。

---

## 🎯 包含 6 个 Skill

| Skill | 角色 |
|---|---|
| [`comic-mv-director`](./comic-mv-director/) ⭐ | **端到端总指挥**（MV / Story 双工作流） |
| [`story-director`](./story-director/) | 故事编排（漫剧叙事节拍） |
| [`shot-optimizer`](./shot-optimizer/) | 单镜头 V1/V2/V3 打磨 |
| [`seedance-2-guide`](./seedance-2-guide/) | Seedance 2.0 知识手册 |
| [`ai-tech-wechat-writer`](./ai-tech-wechat-writer/) | 公众号 HTML 排版 |
| [`shaka-design-system`](./shaka-design-system/) | 共享设计系统（主题 / 组件 / 字体）|

**核心 Skill 是 `comic-mv-director`**，其他 5 个是它内部引用的方法论模块。

---

## 🚀 快速开始

### 安装

```bash
# 方式 1：克隆整个仓库到 Claude Code skills 目录
git clone https://github.com/ShuaiMXu/mv-skills-bundle.git ~/.claude/skills/mv-skills-bundle

# 然后把 6 个 skill 目录软链到 ~/.claude/skills/
cd ~/.claude/skills && for s in comic-mv-director story-director shot-optimizer seedance-2-guide ai-tech-wechat-writer shaka-design-system; do
  ln -sf mv-skills-bundle/$s $s
done

# 方式 2：直接下载 Release 中的 zip 包，解压到 ~/.claude/skills/
# https://github.com/ShuaiMXu/mv-skills-bundle/releases
```

### 使用

在 Claude Code 里说：

> 「我要做一支 1 分钟的 MV，治愈系画风」

`comic-mv-director` 会被自动触发，先做 **CLASSIFY 分流**（MV / Story），然后走对应的 7 步工作流，最终输出一份**可直接交付制作的完整方案**（故事 + 8 镜头表 + 8 × GPT Image 2 prompt + 8 × Seedance 运镜 prompt + Suno 配乐方案 + 角色一致性 + 成本估算 + 5 天排期）。

---

## 🛤 5 步法工作流

```
        用户的创作种子（一段文字 / 一张参考图 / 一首歌）
                          │
                          ▼
              ┌────────────────────────┐
              │  Step 1 · CLASSIFY     │
              │  这是 MV 还是 Story？  │
              └───────────┬────────────┘
                          │
                          ▼
              ┌────────────────────────┐
              │  Step 2 · 8 镜头重切   │
              │  N 帧 → 8 × 10-15s     │
              └───────────┬────────────┘
                          │
                          ▼
              ┌────────────────────────┐
              │  Step 3 · 9 宫格出图   │
              │  GPT Image 2 · 16:9    │
              │  整图 + 16:9 单格      │
              └───────────┬────────────┘
                          │
                          ▼
              ┌────────────────────────┐
              │  Step 4 · 视频生成     │
              │  Seedance 2.0 i2v      │
              │  每镜 10-15s           │
              └───────────┬────────────┘
                          │
                          ▼
              ┌────────────────────────┐
              │  Step 5 · Suno 配乐    │
              │  分段 or 一次成片      │
              │  纯器乐 or 带人声      │
              └───────────┬────────────┘
                          │
                          ▼
                  剪辑拼接 = 成片
```

---

## 💰 实测成本

按 Ride v2（1'45" 水彩 MV，8 镜头）真实跑通数据：

| 项目 | 实测用量 | 单价 | 小计 |
|---|---|---|---|
| GPT Image 2 9 宫格（4K 16:9）| 8 张，一稿出 | ¥1.5/张 | ¥12 |
| GPT Image 2 角色锚图集 | 8 张，一稿出 | ¥1.5/张 | ¥12 |
| Seedance 2.0 image-to-video | 8 × 13s × 1.5 = 156s | ¥1/秒 | **¥156** |
| Suno V5 Pro 订阅分摊 | 一首歌均摊 | — | ¥3 |
| **总计** | | | **~¥180/集** |

**对比**：
- 传统漫剧单集成本 **5,000+ 元** → 降本 28 倍
- Midjourney v7 仅出图（不含视频）：~$60/集
- Runway Gen-4 / Pika 同等长度：~$60-80/集

---

## ⚠️ 5 个关键约束（铁律）

1. **CLASSIFY 前置**：MV / Story 必须先分流，方法论不能复用
2. **16:9 整图 + 16:9 单格**：3×3 网格里每格也是 16:9，必须 prompt 显式声明
3. **Style Mimicry 防护**：禁用具名艺人 / 工作室 / IP（Makoto Shinkai / Studio Ghibli / Tatsuro Yamashita 等），用描述性词汇替换
4. **Suno Lyrics 字段**：方括号 `[...]` 内 = production cue（不唱），方括号外 = 歌词（会被唱出来）
5. **8 镜头 × 10-15s 长镜头**：不要 1:1 复刻 N 帧 Midjourney 方案，必须按叙事节拍重切

详见 [`comic-mv-director/SKILL.md`](./comic-mv-director/SKILL.md) 和其 `references/` 目录。

---

## 📚 文档结构

```
mv-skills-bundle/
├── comic-mv-director/          ⭐ 核心 Skill
│   ├── SKILL.md
│   ├── references/             方法论模块
│   │   ├── nine-panel-storyboard.md
│   │   ├── suno-music-handbook.md
│   │   ├── style-mimicry-blocklist.md
│   │   └── style-presets.md
│   └── examples/
│       └── ride-v2-case-study.md
├── story-director/
├── shot-optimizer/
├── seedance-2-guide/
├── ai-tech-wechat-writer/
├── shaka-design-system/
├── README.md
└── LICENSE                     MIT
```

---

## 🎨 实战产物

用本 Skill 套装做的两份方案：

| 方案 | 画风 | 故事 | 链接 |
|---|---|---|---|
| Ride v2 复刻 | 水彩动漫 | 画师重获色彩感知 | [飞书文档](https://feishu.cn/docx/EmeXdfRLOobFP0xZs34cB6RVncX) |
| Ride 2 Starlight Cruise | Acid Kawaii | 少女出逃笑脸小镇 | [飞书文档](https://feishu.cn/docx/Tu7TdK9i3o94GTxNPX7cAUKen4f) |

---

## 🤝 贡献

欢迎 PR 添加新画风 / 新方法论 / 新案例：

- 新画风模板 → `comic-mv-director/references/style-presets.md`
- 新 Style Mimicry 触发词 → `comic-mv-director/references/style-mimicry-blocklist.md`
- 新 Suno 打法 → `comic-mv-director/references/suno-music-handbook.md`
- 新案例 → `comic-mv-director/examples/`

---

## 📝 License

[MIT](./LICENSE) © 2026 ShuaiMXu
