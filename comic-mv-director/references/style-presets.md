# 画风模板库

> 漫剧 MV 的画风锚定 prompt 模板，持续扩展。所有模板都已通过 Style Mimicry 防护检查。

---

## 一、水彩动漫风（Watercolor Anime）

### 调性
- 适合内敛叙事、治愈、艺术家成长、东方意境
- 案例：Ride v2 复刻方案

### 锚定 Prompt

```
hand-painted 2D animation aesthetic, watercolor textures, lush
natural environments with painterly clouds, soft volumetric golden-
hour lighting, warm cinematic palette of cobalt skies and amber
sunsets, delicate ink linework, dreamy nostalgic mood
```

### 阶段变体（四阶段视觉进化）

#### 阶段① 纯铅笔线稿
```
pure pencil graphite on cream paper texture, hand-drawn wobble in
lines, cross-hatching for shadows, no color anywhere, architectural
sketch + figure drawing aesthetic
```

#### 阶段② 墨线灰调
```
ink wash style on cream paper, bold calligraphy brush strokes, grey
tonal shading creating dimension, dramatic chiaroscuro with light as
negative space (paper itself as light source), no color yet
```

#### 阶段③ 水彩渗入
```
ink wash base with first watercolor color seeping through, color
emerging from edges and crevices like pigment bleeding through paper
cracks, half-monochrome half-color, wet edges and pigment pooling
```

#### 阶段④ 全饱和
```
full saturated hand-painted 2D anime aesthetic, cinematic golden-
hour lighting, deep cobalt sky with massive white cumulus clouds,
warm soft volumetric sunlight, watercolor-textured painterly
backgrounds, maximum saturation
```

### 负向 prompt
```
no 3D render, no neon glow, no cyberpunk, no chibi, no cute anime,
no glossy texture, no plastic, no digital flat shading, no anime-
style overshading
```

---

## 二、Acid Kawaii / Lowbrow Pop Chibi

### 调性
- 适合反差喧闹、个体觉醒、Y2K kidcore、出逃叙事
- 案例：Ride 2 Starlight Cruise

### 锚定 Prompt

```
acid kawaii / lowbrow pop illustration, thick PURPLE-RED outlines
(NOT black, this is the signature) around every shape, candy palette
of hot pink + mint cyan + lavender purple + banana yellow + lime
green, flat color blocks with NO grayscale or mid-tones, chibi
proportions (big head, tiny body, chunky short limbs), faintly
unsettling "kawaii horror" undertone — cute things doing slightly
wrong things, sticker-collage flat composition
```

### 关键特征
- **描边**：紫红色（不是黑色！）8-12 px 等粗
- **配色**：5 色调色板（hot pink #FF6FB5 / mint cyan #7BE5DC / lavender #A88FE5 / banana yellow #FFD93D / lime green #9DE85E）
- **比例**：Chibi（大头小身）
- **眼睛**：大红圆点 + 一个白高光（无瞳孔）
- **氛围**：可爱 + 一丝诡异（cute horror）

### 角色描述短语模板
```
A small chibi character with [发型] hair, wearing [服装], LARGE RED
CIRCULAR DOT eyes with single white highlight (no pupils, just solid
red circles), tiny stitched mouth, [配饰特征]
```

### 负向 prompt
```
no 3D render, no realistic shading, no anime soft pastel, no
painterly texture, no blackline-only manga, no gradient, no dull
colors, no photorealism, no anime-style overshading
```

---

## 三、写实电影感（Cinematic Photoreal）

### 调性
- 适合人物 vlog 风、记录感、情绪写实
- 案例：尚未启用

### 锚定 Prompt

```
cinematic photoreal, 35mm film grain, anamorphic lens flare, shallow
depth of field with soft bokeh, natural skin tones, soft daylight
key + warm fill, color graded with teal-and-orange palette, intimate
handheld camera feel, documentary-style framing
```

### 关键特征
- **质感**：胶片颗粒（35mm grain）
- **镜头**：浅景深（f/1.4-2.8 模拟）
- **色调**：teal-orange 电影调色
- **运镜**：手持感（handheld）

### 负向 prompt
```
no anime, no cartoon, no illustration, no oversaturated, no
artificial lighting, no plastic skin, no AI-render look
```

---

## 四、铅笔线稿（Pure Pencil Sketch）

### 调性
- 适合开场 / 失落 / 空白 / 黑白叙事
- 案例：Ride v2 阶段①

### 锚定 Prompt

```
pure pencil graphite on cream paper texture, hand-drawn wobble in
lines (imperfect human linework), cross-hatching for shadows, no
color anywhere, no shading beyond cross-hatching, architectural
sketch + figure drawing aesthetic, the "real" world drawn with the
same linework as a sketch
```

### 关键特征
- **媒材**：纸面 + 石墨
- **线条**：手绘抖动感（imperfect human linework）
- **阴影**：交叉排线（cross-hatching）
- **氛围**：纯黑白，无中间灰调

### 负向 prompt
```
no color, no watercolor, no ink wash, no digital art, no manga
overshading, no anime style, no 3D
```

---

## 五、墨线水墨（Ink Wash Brush）

### 调性
- 适合觉醒过渡 / 东方意境 / 黑白但有体积
- 案例：Ride v2 阶段②

### 锚定 Prompt

```
ink wash painting style on cream paper, bold calligraphy brush
strokes ranging from thin pen lines to thick brush sweeps, grey
tonal shading creating clear light and shadow sides, dramatic
chiaroscuro with light represented as PAPER NEGATIVE SPACE (the
paper itself is the light source), no color, organic brush imperfection
```

### 关键特征
- **媒材**：宣纸 + 墨
- **线条**：粗细变化（从签字笔到毛笔）
- **光影**：留白 = 光（负空间作为光源）
- **氛围**：东方意境，黑白但有空间感

---

## 六、自定义画风：从图片抽取关键词

当用户提供一张参考图，从以下 5 个维度抽取关键词：

### 6.1 描边维度

| 观察 | 关键词 |
|---|---|
| 没有描边 | `no outlines`, `painterly` |
| 黑色细描边 | `thin black outlines`, `comic linework` |
| 黑色粗描边 | `thick black outlines`, `bold comic linework` |
| 彩色描边 | `[color] outlines, [thickness] px-equivalent` |
| 描边粗细变化 | `variable line weight`, `brush stroke quality` |

### 6.2 调色维度

| 观察 | 关键词 |
|---|---|
| 高饱和纯色块 | `flat saturated color blocks`, `no gradient` |
| 渐变水彩 | `watercolor gradients`, `wet wash blending` |
| 单色调 / 灰阶 | `monochromatic [color]`, `grayscale tones` |
| 多色糖果 | `candy palette of [colors]` |
| 电影调色 | `cinematic [palette] grading` |

### 6.3 比例维度

| 观察 | 关键词 |
|---|---|
| 写实人体 | `realistic proportions` |
| Chibi | `chibi proportions (big head, tiny body)` |
| 拉长 | `elongated proportions, fashion illustration style` |
| 压扁 | `compressed proportions, stylized exaggeration` |

### 6.4 笔触维度

| 观察 | 关键词 |
|---|---|
| 数字平涂 | `flat digital coloring` |
| 手绘抖动 | `hand-drawn imperfect linework, wobble` |
| 油画质感 | `oil painting impasto texture` |
| 水彩晕染 | `watercolor bleed and wet edges` |
| 像素艺术 | `pixel art aesthetic, [N]x[N] resolution feel` |

### 6.5 氛围维度

| 观察 | 关键词 |
|---|---|
| 温暖怀旧 | `warm nostalgic`, `vintage`, `golden hour` |
| 冷冽科技 | `cold cyberpunk`, `neon noir` |
| 怪可爱 | `kawaii horror`, `cute uncanny` |
| 宏大史诗 | `epic cinematic`, `dramatic scale` |
| 内敛意境 | `intimate`, `contemplative`, `minimalist` |

### 6.6 抽取后的组装公式

```
[描边描述], [调色描述], [比例描述], [笔触描述], [氛围描述],
[参考时代/流派关键词]
```

例（参考一张 Ride 2 风格图）：
```
thick purple-red outlines, candy palette of hot pink + mint cyan +
lavender, chibi proportions, flat color blocks with no gradient,
kawaii horror undertone, Y2K kidcore sticker-collage aesthetic
```

---

## 七、模板组合策略

### 7.1 同一镜头的多版本（V1/V2/V3 打磨）

主画风固定，**只改一个维度**：

| 改动维度 | V1 → V2 例 |
|---|---|
| 调色 | 暖橙 → 冷蓝 |
| 光线 | 顶光 → 侧光 |
| 运镜 | 固定 → 跟拍 |
| 景别 | 中景 → 特写 |
| 情绪强度 | 内敛 → 激烈 |

参考 `shot-optimizer` skill 的 V1/V2/V3 打磨流程。

### 7.2 阶段过渡（一个镜头内多画风共存）

如 Ride v2 的 S3（从线稿到第一抹蓝），同一 9 宫格内：
- Panel 1-3：阶段① 线稿
- Panel 4-6：发现蓝色瞬间
- Panel 7-9：阶段②/③ 起步

prompt 里必须明确**哪几格用哪个风格**，避免模型随机分配。

---

## 八、模板贡献指南

新画风加入本清单前，应满足：

1. ✅ 通过 Style Mimicry 防护清单检查（无任何专有名词）
2. ✅ 至少跑通过 3 张测试图（不同主题）
3. ✅ 标注「适合主题」让其他用户能快速决策
4. ✅ 提供具体的 prompt 例子（不只是关键词列表）
5. ✅ 给负向 prompt（防止画风跑偏）
