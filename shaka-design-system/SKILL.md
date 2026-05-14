---
name: shaka-design-system
description: Shaka 内容产出的共享设计系统（主题/字体/组件规则的单一真相源）。**本 skill 不主动触发**，仅作为设计规则库供其他内容生成 skill（公众号、PPT、小红书、邮件等）在 HTML 生成时读取引用。灵感来源：op7418 的 guizang-ppt-skill。
allowed-tools: Read
---

# Shaka 设计系统 · 单一真相源

> 本 skill **不主动触发**，仅供其他 skill（公众号、PPT、小红书等）在生成 HTML 内容时读取引用。
> 修改这里的规则 = 修改所有下游 skill 的视觉语言。

---

## 为什么存在

- 保持 Shaka 所有内容产出（公众号日报、PPT、小红书、邮件）的**设计语言一致性**
- 避免在每个 content skill 里重复定义配色 / 字体 / 组件
- 规则升级只需改一处，所有下游 skill 自动受益
- 呼应 [[Design DNA]] 理念——把风格规格从视觉稿解耦出来

---

## 引用方式

下游 skill 在生成 HTML 前，先 Read 以下文件拿到设计规则：

```
shaka-design-system/
├── SKILL.md              本文件（读我就够了解整体）
└── references/
    ├── themes.md         5 套主题配色（唯一色板真相源）
    ├── components.md     通用组件（callout / stat / pillar / figure / tag）
    ├── fonts.md          字体层级（标题 / 正文 / 等宽）
    └── principles.md     约束式设计原则（不允许自定义 hex、主题节奏等）
```

**实际挂载路径**：
- Skills 通过符号链接发现，实际位置视运行环境而定
- 在 Claude Agent 容器中：`/workspace/user-skills/shaka-design-system/references/*`
- 在宿主机 admin 模式：`~/.claude/skills/shaka-design-system/references/*`

---

## 下游 skill 清单

| Skill | 用途 | 输出形态 | 业务特定文件 |
|-------|------|---------|-----------|
| `ai-tech-wechat-writer` | AI 日报公众号 | 纵向长图文 HTML | `layouts.md` 5 段式 + 公众号模板 |
| `guizang-ppt-skill`（上游） | 杂志风 PPT | 横滑分页 HTML | `layouts.md` 10 版式 + 横滑模板 |
| `xhs-poster-writer`（规划中） | 小红书封面 | 3:4 单图 HTML → PNG | 小红书封面版式 |
| `email-newsletter`（规划中） | 邮件订阅 | 邮件兼容 HTML | 邮件客户端安全版式 |

**每个下游 skill 职责**：只维护自己的 **layouts.md**（业务特定结构）和 **template.html**（业务特定容器）。所有共享部分统一从本 skill 读取。

---

## 核心哲学

引用自 op7418 的 guizang-ppt-skill，经我方验证并吸收：

1. **约束式设计**：枚举优于自由 —— 5 套主题不允许自定义 hex，因为用户配色 99% 会翻车
2. **规则文档化**：设计不是品味，是可查询的手册 —— `references/` 就是给 agent 和设计师共用的手册
3. **节奏优于元素**：单页漂亮不够，**整体节奏**才是杂志感的来源 —— 主题交替、视觉呼吸、深浅对比
4. **踩坑沉淀**：所有"血泪经验"必须进 checklist，不能靠记忆

---

## 修改规则的流程

1. 提案改哪个文件（themes.md / components.md / etc.）
2. 检查**所有下游 skill** 是否会受影响
3. 在改动后的文件底部加 `## 变更记录` 注明日期和原因
4. 如果是破坏性变更（删除某个组件 / 重命名变量），同步更新下游 skill

---

## 边界

本 skill **不**：
- 不生成任何 HTML / 文件
- 不维护任何业务特定结构（5 段式、10 版式等，归下游 skill）
- 不触发任何工作流（只被 Read）

本 skill **是**：
- 设计规则的**唯一真相源**
- 被引用的**字典**
