# 组件参考 · Components

Shaka 设计系统的**跨媒介通用组件库**。每个组件给两个版本：
- **Class 版**（PPT / 独立 HTML 站用）：使用 CSS class，需要 template.html 提供样式
- **内联 Style 版**（公众号用）：所有样式内联，无需外部 CSS，单位用 `rem/px` 而非 `vh/vw`

---

## 目录

- [Callout 引用框](#callout-引用框)
- [Stat 数字矩阵](#stat-数字矩阵)
- [Pillar 支柱卡（三柱并列）](#pillar-支柱卡三柱并列)
- [Tag & Kicker](#tag--kicker)
- [Section Header 段落标题](#section-header-段落标题)
- [Figure 图片框](#figure-图片框)
- [Rowline 表格行](#rowline-表格行)

> 所有颜色变量来自 `themes.md`。公众号内联版需要把 `var(--ink)` 等替换成具体 hex（从选定主题取值）。

---

## Callout 引用框

**用途**：展示金句 / 关键观点 / 引言 / 作者判断。

### Class 版（PPT/站点）

```html
<div class="callout" style="max-width:80vw">
  <div class="q-big">"这东西在三年前，<br>需要一个十人团队做一年。"</div>
  <span class="cite">— 一个观察者的判断</span>
</div>
```

### 内联 Style 版（公众号）

```html
<section style="
  padding:24px 28px;
  background:rgba(10,31,61,0.04);
  border-left:4px solid #0a1f3d;
  margin:32px 0;
  border-radius:0 8px 8px 0;
">
  <p style="
    font-family:'Noto Serif SC',serif;
    font-size:20px;
    line-height:1.6;
    color:#0a1f3d;
    font-weight:600;
    margin:0 0 12px 0;
  ">
    "这东西在三年前，需要一个十人团队做一年。"
  </p>
  <p style="
    font-family:'IBM Plex Mono',monospace;
    font-size:12px;
    letter-spacing:0.05em;
    color:rgba(10,31,61,0.6);
    margin:0;
    text-transform:uppercase;
  ">— 一个观察者的判断</p>
</section>
```

**颜色替换规则**：`#0a1f3d` 要替换成当前主题的 `--ink` 值（从 themes.md 取）。

---

## Stat 数字矩阵

**用途**：展示数据指标、对比数字、关键量化信息。

### Class 版（PPT/站点）

```html
<div class="grid-3">
  <div class="stat">
    <span class="m">Duration</span>
    <span class="n">64<em style="font-size:.4em;opacity:.5;font-style:normal"> 天</em></span>
    <span class="l">从 0 到现在</span>
  </div>
  <!-- ... 更多 stat（推荐 3 或 6 个） ... -->
</div>
```

### 内联 Style 版（公众号）

**单个 stat**：
```html
<div style="text-align:center;padding:20px 16px">
  <div style="
    font-family:'IBM Plex Mono',monospace;
    font-size:11px;
    letter-spacing:0.1em;
    color:rgba(10,31,61,0.5);
    text-transform:uppercase;
    margin-bottom:8px;
  ">DURATION</div>
  <div style="
    font-family:'Playfair Display','Noto Serif SC',serif;
    font-size:48px;
    font-weight:800;
    color:#0a1f3d;
    line-height:1;
    margin-bottom:8px;
  ">64<span style="font-size:20px;opacity:0.5;font-weight:400"> 天</span></div>
  <div style="
    font-size:13px;
    color:rgba(10,31,61,0.7);
  ">从 0 到现在</div>
</div>
```

**3 列布局（公众号用 table，编辑器更兼容）**：
```html
<table width="100%" cellpadding="0" cellspacing="0" style="margin:24px 0">
  <tr>
    <td width="33%" style="vertical-align:top">[stat 1]</td>
    <td width="33%" style="vertical-align:top">[stat 2]</td>
    <td width="33%" style="vertical-align:top">[stat 3]</td>
  </tr>
</table>
```

**提示**：公众号部分编辑器会剥离 `display:grid`，用 `<table>` 最稳。

---

## Pillar 支柱卡（三柱并列）

**用途**：三个并列概念（产品三特性、方法论三步骤、数据三维度）。

### Class 版（PPT/站点）

```html
<div class="grid-3">
  <div class="pillar">
    <div class="ic">01</div>
    <div class="t">三层<br>文档体系</div>
    <div class="d">CLAUDE.md<br>+ 项目知识库<br>+ 护栏文件</div>
  </div>
  <!-- ... -->
</div>
```

### 内联 Style 版（公众号）

```html
<table width="100%" cellpadding="0" cellspacing="0" style="margin:32px 0">
  <tr>
    <td width="33%" style="
      vertical-align:top;
      padding:20px 12px;
      border-top:1px solid rgba(10,31,61,0.2);
    ">
      <div style="
        font-family:'IBM Plex Mono',monospace;
        font-size:14px;
        color:#0a1f3d;
        margin-bottom:16px;
      ">01</div>
      <div style="
        font-family:'Noto Serif SC',serif;
        font-size:18px;
        font-weight:600;
        color:#0a1f3d;
        line-height:1.4;
        margin-bottom:12px;
      ">三层<br>文档体系</div>
      <div style="
        font-size:13px;
        color:rgba(10,31,61,0.7);
        line-height:1.6;
      ">CLAUDE.md<br>+ 项目知识库<br>+ 护栏文件</div>
    </td>
    <!-- 其他两柱同构 -->
  </tr>
</table>
```

---

## Tag & Kicker

**Kicker**：标题上方的小提示文字（等宽、全大写、小字号）。

### 内联 Style 版（公众号）

```html
<div style="
  font-family:'IBM Plex Mono',monospace;
  font-size:11px;
  letter-spacing:0.1em;
  color:rgba(10,31,61,0.5);
  text-transform:uppercase;
  margin-bottom:8px;
">过去 64 天 · 开发篇</div>
```

**Tag**：独立标签胶囊。

```html
<span style="
  display:inline-block;
  padding:4px 12px;
  font-size:12px;
  color:#0a1f3d;
  border:1px solid rgba(10,31,61,0.3);
  border-radius:16px;
  margin:4px 4px 4px 0;
">早上 10 点起床</span>
```

---

## Section Header 段落标题

**用途**：公众号 5 段式每一段的起点（kicker + H2）。

### 内联 Style 版（公众号）

```html
<header style="margin:48px 0 24px 0">
  <div style="
    font-family:'IBM Plex Mono',monospace;
    font-size:11px;
    letter-spacing:0.15em;
    color:rgba(10,31,61,0.5);
    text-transform:uppercase;
    margin-bottom:12px;
  ">SECTION 01 · HEADLINE</div>
  <h2 style="
    font-family:'Noto Serif SC',serif;
    font-size:28px;
    font-weight:700;
    color:#0a1f3d;
    margin:0;
    line-height:1.3;
  ">📰 今日 AI 头条</h2>
  <div style="
    height:2px;
    background:#0a1f3d;
    width:48px;
    margin-top:12px;
  "></div>
</header>
```

---

## Figure 图片框

### 公众号关键约束

1. **图片必须上传到微信服务器**后获取 `https://mmbiz.qpic.cn/...` 地址，外链图会被压缩
2. **宽度用 100%**，高度自动（不要用 `height:Nvh`，公众号 vh 不稳）
3. **caption 放在下方**，不要绝对定位

### 内联 Style 版（公众号）

```html
<figure style="margin:32px 0;text-align:center">
  <img src="https://mmbiz.qpic.cn/..." alt="说明" style="
    width:100%;
    max-width:600px;
    height:auto;
    display:block;
    margin:0 auto 12px auto;
  ">
  <figcaption style="
    font-family:'IBM Plex Mono',monospace;
    font-size:11px;
    color:rgba(10,31,61,0.5);
    letter-spacing:0.05em;
  ">图 1 · 架构示意</figcaption>
</figure>
```

---

## Rowline 表格行

**用途**：关键词+描述 列表（术语表、特性列表）。

### 内联 Style 版（公众号）

```html
<table width="100%" cellpadding="0" cellspacing="0" style="margin:16px 0">
  <tr style="border-top:1px solid rgba(10,31,61,0.15)">
    <td width="30%" style="
      padding:16px 0;
      font-family:'Noto Serif SC',serif;
      font-weight:600;
      color:#0a1f3d;
      vertical-align:top;
    ">CLAUDE.md</td>
    <td style="
      padding:16px 12px;
      color:rgba(10,31,61,0.8);
      vertical-align:top;
      line-height:1.6;
    ">你该怎么做事 —— 行为规则 + 工作偏好 + 禁止事项</td>
  </tr>
  <!-- 更多行 ... -->
</table>
```

---

## 公众号兼容红黑榜

### ✅ 可用
- `<table>` 布局（最稳）
- 内联 `style` 属性
- `border-radius` / `box-shadow` 基本支持
- `rgba()` / `var()` 内联 CSS 变量（部分编辑器）
- 中文 Web 字体（但会退化为系统字体，不影响阅读）

### ❌ 避免
- `<style>` 块（某些编辑器会剥离）
- `display:grid` / `display:flex`（不稳定，用 table 替代）
- `position:fixed/sticky`（编辑器会重排）
- 外链 SVG `<use href>`（不加载）
- JS / @media / @keyframes（全部不支持）
- `vh / vw` 单位（不稳定，用 `px/rem`）

---

## 变更记录

- 2026-04-24：从 op7418 guizang-ppt-skill 抽取核心 6 个组件，追加公众号内联 Style 版
