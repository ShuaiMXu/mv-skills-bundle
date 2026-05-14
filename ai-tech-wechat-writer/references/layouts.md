# 公众号 5 段式版式 · Layouts

> 公众号业务特定的段落结构。共享组件来自 `shaka-design-system/references/components.md`。

---

## 5 段式总览

```
┌──────────────────────────────────────┐
│  📰 今日 AI 头条（1 条 S 级情报）        │ ← Section 1：震撼开头
│  [Section Header + Callout + Body]    │
├──────────────────────────────────────┤
│  🔥 行业要闻（2-3 条 A 级情报）          │ ← Section 2：信息密度
│  [Section Header + 3 条 Rowline]       │
├──────────────────────────────────────┤
│  🚀 产品动态（1-2 条工具/模型更新）       │ ← Section 3：数据对比
│  [Section Header + Stat 矩阵 × 3]      │
├──────────────────────────────────────┤
│  💡 观点短评（Shaka 的视角）             │ ← Section 4：判断输出
│  [Section Header + Callout（带 cite）]  │
├──────────────────────────────────────┤
│  🔍 明日预告（留钩子）                   │ ← Section 5：轻盈收尾
│  [Section Header + Tag 列表]           │
└──────────────────────────────────────┘
```

---

## Section 1：📰 今日 AI 头条

**组件**：Section Header + **大 Callout** + 正文段落

**视觉目标**：震撼开头，一条最重磅情报放大展示。

```html
<section style="margin:0 0 64px 0">
  <!-- Section Header -->
  <header style="margin:0 0 24px 0">
    <div style="font-family:'IBM Plex Mono',monospace;font-size:11px;letter-spacing:0.15em;color:rgba(10,31,61,0.5);text-transform:uppercase;margin-bottom:12px">HEADLINE · 头条</div>
    <h2 style="font-family:'Noto Serif SC',serif;font-size:28px;font-weight:700;color:#0a1f3d;margin:0;line-height:1.3">📰 今日 AI 头条</h2>
    <div style="height:2px;background:#0a1f3d;width:48px;margin-top:12px"></div>
  </header>

  <!-- 大 Callout：情报核心 -->
  <div style="padding:32px 28px;background:rgba(10,31,61,0.06);border-left:4px solid #0a1f3d;margin:24px 0;border-radius:0 8px 8px 0">
    <p style="font-family:'Noto Serif SC',serif;font-size:22px;line-height:1.6;color:#0a1f3d;font-weight:700;margin:0 0 16px 0">
      【情报标题】一句话压缩核心事实
    </p>
    <p style="font-size:15px;line-height:1.8;color:rgba(10,31,61,0.85);margin:0">
      展开叙述的正文，说明发生了什么、涉及什么、时间线。3-5 句话即可。
    </p>
    <p style="font-family:'IBM Plex Mono',monospace;font-size:11px;color:rgba(10,31,61,0.5);letter-spacing:0.05em;margin-top:16px;text-transform:uppercase">📡 来源：量子位</p>
  </div>
</section>
```

---

## Section 2：🔥 行业要闻（2-3 条）

**组件**：Section Header + **Rowline 列表**（每行一条）

**视觉目标**：信息密度，快速扫读。

```html
<section style="margin:0 0 64px 0">
  <header style="margin:0 0 24px 0">
    <div style="font-family:'IBM Plex Mono',monospace;font-size:11px;letter-spacing:0.15em;color:rgba(10,31,61,0.5);text-transform:uppercase;margin-bottom:12px">INDUSTRY · 行业</div>
    <h2 style="font-family:'Noto Serif SC',serif;font-size:28px;font-weight:700;color:#0a1f3d;margin:0;line-height:1.3">🔥 行业要闻</h2>
    <div style="height:2px;background:#0a1f3d;width:48px;margin-top:12px"></div>
  </header>

  <table width="100%" cellpadding="0" cellspacing="0" style="margin:16px 0">
    <!-- Row 1 -->
    <tr style="border-top:1px solid rgba(10,31,61,0.15)">
      <td width="30%" style="padding:20px 0;font-family:'Noto Serif SC',serif;font-weight:600;color:#0a1f3d;vertical-align:top;font-size:16px">
        【关键词】
      </td>
      <td style="padding:20px 12px;color:rgba(10,31,61,0.85);vertical-align:top;line-height:1.7;font-size:15px">
        一段描述 + <span style="font-family:'IBM Plex Mono',monospace;font-size:11px;color:rgba(10,31,61,0.5);letter-spacing:0.05em">📡 来源：机器之心</span>
      </td>
    </tr>
    <!-- Row 2 -->
    <tr style="border-top:1px solid rgba(10,31,61,0.15)">
      <td width="30%" style="padding:20px 0;font-family:'Noto Serif SC',serif;font-weight:600;color:#0a1f3d;vertical-align:top;font-size:16px">
        【关键词 2】
      </td>
      <td style="padding:20px 12px;color:rgba(10,31,61,0.85);vertical-align:top;line-height:1.7;font-size:15px">
        ...
      </td>
    </tr>
    <!-- ... 2-3 行 ... -->
  </table>
</section>
```

---

## Section 3：🚀 产品动态（1-2 条）

**组件**：Section Header + **Stat 矩阵（如有数据）** + 描述段

**视觉目标**：数据密度，突出产品更新的量化信息。

```html
<section style="margin:0 0 64px 0">
  <header style="margin:0 0 24px 0">
    <div style="font-family:'IBM Plex Mono',monospace;font-size:11px;letter-spacing:0.15em;color:rgba(10,31,61,0.5);text-transform:uppercase;margin-bottom:12px">PRODUCT · 产品</div>
    <h2 style="font-family:'Noto Serif SC',serif;font-size:28px;font-weight:700;color:#0a1f3d;margin:0;line-height:1.3">🚀 产品动态</h2>
    <div style="height:2px;background:#0a1f3d;width:48px;margin-top:12px"></div>
  </header>

  <!-- 产品名 + 核心更新 -->
  <h3 style="font-family:'Noto Serif SC',serif;font-size:20px;font-weight:600;color:#0a1f3d;margin:24px 0 12px 0">
    GPT-5 Turbo 发布
  </h3>
  <p style="font-size:15px;line-height:1.8;color:rgba(10,31,61,0.85);margin:0 0 24px 0">
    OpenAI 今日推出 GPT-5 Turbo，上下文扩大至 10M tokens，推理延迟降低 40%。
  </p>

  <!-- Stat 矩阵（3 列，如果有数据的话） -->
  <table width="100%" cellpadding="0" cellspacing="0" style="margin:24px 0">
    <tr>
      <td width="33%" style="vertical-align:top;text-align:center;padding:16px 12px">
        <div style="font-family:'IBM Plex Mono',monospace;font-size:11px;letter-spacing:0.1em;color:rgba(10,31,61,0.5);text-transform:uppercase;margin-bottom:8px">CONTEXT</div>
        <div style="font-family:'Playfair Display','Noto Serif SC',serif;font-size:40px;font-weight:800;color:#0a1f3d;line-height:1;margin-bottom:8px">10M</div>
        <div style="font-size:12px;color:rgba(10,31,61,0.7)">tokens</div>
      </td>
      <td width="33%" style="vertical-align:top;text-align:center;padding:16px 12px">
        <div style="font-family:'IBM Plex Mono',monospace;font-size:11px;letter-spacing:0.1em;color:rgba(10,31,61,0.5);text-transform:uppercase;margin-bottom:8px">LATENCY</div>
        <div style="font-family:'Playfair Display','Noto Serif SC',serif;font-size:40px;font-weight:800;color:#0a1f3d;line-height:1;margin-bottom:8px">-40<span style="font-size:18px;opacity:0.5">%</span></div>
        <div style="font-size:12px;color:rgba(10,31,61,0.7)">延迟降低</div>
      </td>
      <td width="33%" style="vertical-align:top;text-align:center;padding:16px 12px">
        <div style="font-family:'IBM Plex Mono',monospace;font-size:11px;letter-spacing:0.1em;color:rgba(10,31,61,0.5);text-transform:uppercase;margin-bottom:8px">PRICE</div>
        <div style="font-family:'Playfair Display','Noto Serif SC',serif;font-size:40px;font-weight:800;color:#0a1f3d;line-height:1;margin-bottom:8px">$8<span style="font-size:18px;opacity:0.5">/M</span></div>
        <div style="font-size:12px;color:rgba(10,31,61,0.7)">输入 token</div>
      </td>
    </tr>
  </table>

  <p style="font-family:'IBM Plex Mono',monospace;font-size:11px;color:rgba(10,31,61,0.5);letter-spacing:0.05em;margin-top:8px;text-transform:uppercase">📡 来源：OpenAI 官方博客</p>
</section>
```

---

## Section 4：💡 观点短评

**组件**：Section Header + **Callout（带 cite）**

**视觉目标**：带有 Shaka 主观视角的判断，视觉上和"头条"的大 Callout 呼应，但更紧凑。

```html
<section style="margin:0 0 64px 0">
  <header style="margin:0 0 24px 0">
    <div style="font-family:'IBM Plex Mono',monospace;font-size:11px;letter-spacing:0.15em;color:rgba(10,31,61,0.5);text-transform:uppercase;margin-bottom:12px">PERSPECTIVE · 观点</div>
    <h2 style="font-family:'Noto Serif SC',serif;font-size:28px;font-weight:700;color:#0a1f3d;margin:0;line-height:1.3">💡 观点短评</h2>
    <div style="height:2px;background:#0a1f3d;width:48px;margin-top:12px"></div>
  </header>

  <div style="padding:24px 28px;background:rgba(10,31,61,0.04);border-left:4px solid #0a1f3d;margin:16px 0;border-radius:0 8px 8px 0">
    <p style="font-family:'Noto Serif SC',serif;font-size:18px;line-height:1.7;color:#0a1f3d;font-weight:500;font-style:italic;margin:0 0 16px 0">
      "今天三件事的共同信号是：大模型能力开始外溢到工具层——以前模型公司自己不做的事，现在都做了。对独立 AI 工具公司，这是窗口期收紧。"
    </p>
    <p style="font-family:'IBM Plex Mono',monospace;font-size:11px;letter-spacing:0.05em;color:rgba(10,31,61,0.6);margin:0;text-transform:uppercase">— SHAKA · 2026.04.24</p>
  </div>
</section>
```

---

## Section 5：🔍 明日预告

**组件**：Section Header + **Tag 列表**

**视觉目标**：轻盈收尾，留钩子引导关注。

```html
<section style="margin:0 0 48px 0">
  <header style="margin:0 0 20px 0">
    <div style="font-family:'IBM Plex Mono',monospace;font-size:11px;letter-spacing:0.15em;color:rgba(10,31,61,0.5);text-transform:uppercase;margin-bottom:12px">TOMORROW · 预告</div>
    <h2 style="font-family:'Noto Serif SC',serif;font-size:24px;font-weight:700;color:#0a1f3d;margin:0;line-height:1.3">🔍 明日预告</h2>
  </header>

  <p style="font-size:15px;line-height:1.8;color:rgba(10,31,61,0.85);margin:0 0 16px 0">
    明天的关键看点：
  </p>

  <div style="margin:16px 0">
    <span style="display:inline-block;padding:6px 14px;font-size:13px;color:#0a1f3d;border:1px solid rgba(10,31,61,0.3);border-radius:20px;margin:4px 6px 4px 0;font-family:'Noto Sans SC',sans-serif">Anthropic 财报</span>
    <span style="display:inline-block;padding:6px 14px;font-size:13px;color:#0a1f3d;border:1px solid rgba(10,31,61,0.3);border-radius:20px;margin:4px 6px 4px 0;font-family:'Noto Sans SC',sans-serif">Meta Llama 5 发布会</span>
    <span style="display:inline-block;padding:6px 14px;font-size:13px;color:#0a1f3d;border:1px solid rgba(10,31,61,0.3);border-radius:20px;margin:4px 6px 4px 0;font-family:'Noto Sans SC',sans-serif">Anthropic Max 降价传言</span>
  </div>

  <p style="font-family:'IBM Plex Mono',monospace;font-size:11px;color:rgba(10,31,61,0.5);letter-spacing:0.05em;margin-top:24px;text-transform:uppercase;text-align:center">明天见 · SEE YOU TOMORROW</p>
</section>
```

---

## 节奏规划（Shaka's Rhythm）

5 段的视觉权重分布（防审美疲劳）：

| 段 | 视觉权重 | 核心元素 |
|----|---------|---------|
| 📰 头条 | ⭐⭐⭐⭐ 重 | 大 Callout + 大标题 |
| 🔥 要闻 | ⭐⭐ 轻 | Rowline 列表（扫读） |
| 🚀 动态 | ⭐⭐⭐ 中 | Stat 矩阵（数据密度） |
| 💡 短评 | ⭐⭐⭐⭐ 重 | Callout（带 cite） |
| 🔍 预告 | ⭐ 轻 | Tag 列表（装饰性） |

**节奏**：重-轻-中-重-轻，形成 "开篇震撼 → 松驰扫读 → 数据验证 → 判断高潮 → 轻盈收尾" 的阅读体验。

---

## 变更记录

- 2026-04-24：初版，将 5 段式从 hardcode 配色升级为组件化，引用 `shaka-design-system` 共享主题和组件
