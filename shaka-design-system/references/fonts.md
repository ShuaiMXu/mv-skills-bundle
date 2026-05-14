# 字体层级 · Fonts

**三层分工、严禁混用。**

---

## 三层字体分工

| 层级 | 用途 | 字体栈（中文优先） |
|------|------|----|
| **衬线 Serif** | 标题、引言、金句、数字 —— "视觉重音" | `'Noto Serif SC', 'Source Han Serif SC', 'Songti SC', serif` |
| **无衬线 Sans** | 正文、描述、列表 —— "信息密度" | `'Noto Sans SC', 'PingFang SC', 'Microsoft YaHei', sans-serif` |
| **等宽 Mono** | Kicker、Meta、章节编号 —— "装饰节奏" | `'IBM Plex Mono', 'Menlo', 'Courier New', monospace` |

**英文搭配**：
- 衬线英文：`'Playfair Display'` → 优先用于大标题（Hero 页标题）
- 无衬线英文：`'Inter'` → 优先用于正文
- 等宽英文：`'IBM Plex Mono'` → 装饰性英文标签

---

## 核心规则

### 规则 1：标题用衬线，正文用无衬线

**不要反过来**。用无衬线做标题会失去杂志感，用衬线做长段正文会降低可读性。

### 规则 2：数字也用衬线

巨型数字（统计页、hero 数据）用 `Playfair Display` / `Noto Serif SC`，比无衬线数字更有杂志感。

### 规则 3：Kicker 和 Meta 用等宽

所有"标题上方的小提示"、"右上角的章节编号"、"图注（caption）"都用等宽字体 + 大写 + 字距（letter-spacing）。

这是**杂志视觉语言**的关键——让装饰性文字和内容文字区分开。

---

## 字号层级（以公众号 16px 基础为例）

### 公众号（纵向长图文）

| 层级 | 字号 | 行高 | 用途 |
|------|------|------|------|
| H1（文章标题） | 24-28px | 1.3 | 公众号后台填写，不在 body 内 |
| H2（段落标题） | 22-26px | 1.3 | 5 段式每段开头 |
| H3（子标题） | 18-20px | 1.4 | 一条情报内的小标题 |
| Lead（引导段） | 17px | 1.7 | 段落开头的总览句 |
| Body（正文） | 15-16px | 1.75 | 主体阅读内容 |
| Kicker（小提示） | 11px | 1.4 | 段落上方的英文/编号 |
| Meta（元信息） | 11-12px | 1.4 | 图注、来源标签 |
| Big Num（大数字） | 40-56px | 1 | 统计页主数字 |

### PPT（横滑演示）

使用 `vw` 单位（基于视口宽度），见 guizang-ppt-skill 原文。

---

## 字重（Font Weight）

| 场景 | 字重 |
|------|------|
| 巨型数字 / Hero 英文 | 800 (ExtraBold) |
| 标题 (H1, H2) | 700 (Bold) |
| 副标题 (H3) | 600 (SemiBold) |
| Lead | 400 (Regular) |
| Body | 400 (Regular) |
| Meta / Kicker | 400 或 500 (Regular/Medium) |

**不要随便用 300（Light）**，中文 Light 在公众号里会渲染成系统字体，反而变重。

---

## 公众号特别注意

1. **Web 字体会退化**：`Noto Serif SC` 在公众号里多数设备会退化为 `Songti SC`（iOS）或 `SimSun`（Android 旧版）或系统默认衬线。**这是可接受的退化**，不要强行引入外链字体。
2. **不要用 `font-family:serif;`** 这种通用关键字 —— 不同设备渲染差别大。**必须**写出具体字体栈。
3. **字号响应式**：公众号移动端阅读为主，桌面阅读很少。字号以**移动端 iPhone 375px 宽**为基准设计。

---

## 核心字体组合示例（公众号）

```css
/* 标题 */
font-family:'Noto Serif SC','Source Han Serif SC','Songti SC',serif;
font-weight:700;

/* 正文 */
font-family:'Noto Sans SC','PingFang SC','Microsoft YaHei',sans-serif;
font-weight:400;

/* 装饰（Kicker / Meta） */
font-family:'IBM Plex Mono','Menlo',monospace;
font-size:11px;
letter-spacing:0.1em;
text-transform:uppercase;
```

---

## 变更记录

- 2026-04-24：初版，基于 guizang-ppt-skill 的字体分工，追加公众号字号层级
