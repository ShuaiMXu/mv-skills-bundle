# 9 宫格 Storyboard 设计规范

> GPT Image 2 + Seedance 2.0 工作流的核心创新点。本文档是 SKILL.md 第三步的展开。

---

## 一、为什么是 9 宫格

### 1.1 vs 单帧 prompt

| 维度 | Midjourney v7 单帧 | GPT Image 2 9 宫格 |
|---|---|---|
| 出图次数 | 每个镜头 1 张 | 每个镜头 1 张（含 9 格）|
| 镜头时长 | 单帧 1 静态 | 9 格 = 9 个瞬间，构成镜头节奏 |
| Seedance 接入 | 一张图作首帧 + prompt 脑补 | 9 格作为视觉 DNA，运动逻辑更清晰 |
| 成本 | 25 帧 × 0.05 美金 ≈ 1.25 美金 | 8 张 × 0.42 元 ≈ 3.4 元 |
| 镜头连贯性 | 帧间需剪辑过渡 | 单镜头内自带运动连贯 |

### 1.2 vs 12 宫格 / 6 宫格

社区实测（截至 2026/04）：

| 网格 | 整图比例 | 每格比例 | 清晰度 / 信息量 | 适用 |
|---|---|---|---|---|
| 3×2 | 16:9 横长 | 8:9 接近方 | 高 / 低 | 短叙事 |
| **3×3** ⭐ | 16:9 | **16:9** | 中 / 中 | **MV / 短片标配** |
| 4×3 | 64:27 | 16:9 但每格被压扁 | 中低 / 高 | 信息密集表格 |
| 6×4 | 16:9 | 16:9 但 24 格太小 | 低 / 极高 | 漫画分镜册 |

**3×3 是几何 + 信息密度 + 镜头叙事感的最佳折中。**

---

## 二、几何规范（铁律）

### 2.1 整图与单格

- **整图比例**：**16:9**（GPT Image 2 在 4K 模式下原生支持）
- **整图分辨率**：3840×2160（4K）
- **单格分辨率**：1280×720（720p），3×3 平均切分
- **网格分隔线**：thin white gridlines（白色细线），不要黑色或粗线（会被模型当成画面元素）

### 2.2 prompt 中必须显式声明

```
Layout: 9 panels in a 3×3 grid, OVERALL image is 16:9 cinematic
widescreen, and EACH INDIVIDUAL panel is also 16:9 (each panel frames
its content in cinematic widescreen composition — no square cropping,
no portrait framing inside any panel).
```

**没有这段声明 = 模型会把每格塞成方块**，构图全部失败。

### 2.3 网格选型论证

| 网格 | 整图 | 每格 | 评价 |
|---|---|---|---|
| **3×3** ⭐ | 16:9 | **16:9** | 几何上唯一干净的匹配 |
| 2×3 | 32:27 ≈ 5:4 | 16:9 但整图变方 | 不推荐 |
| 4×2 | 64:18 ≈ 3.6:1 | 16:9 但整图超宽 | 信息密度太低 |
| 4×3 | 64:27 ≈ 2.37:1 | 16:9 但 12 格 | 单格太挤 |
| 6×4 | 16:9 | 16:9 但 24 格 | 单格太小看不清 |

---

## 三、Prompt 标准结构

### 3.1 6 段式结构

```
[风格锚定 + 阶段视觉风格描述（30-50 字）]

[3×3 网格 + 16:9 几何声明（前文 3.1 中那段）]

Panel 1 (top-left): [画面描述 1-2 句]
Panel 2: [画面描述]
Panel 3: [画面描述]
Panel 4 (middle-left): [画面描述]
Panel 5: [画面描述]
Panel 6: [画面描述]
Panel 7 (bottom-left): [画面描述]
Panel 8: [画面描述]
Panel 9: [画面描述]

[整体调色 / 笔触 / 氛围总述（20-30 字）]. Overall aspect ratio 16:9.
```

### 3.2 描述写作要点

| 维度 | 怎么写 | 反面例子 |
|---|---|---|
| 画面主体 | 「she cycles past a flower shop」 | 「一个场景」（太抽象）|
| 关键瞬间 | 「at the moment her fingertip touches the petal」 | 「touching」（缺时刻感）|
| 视觉细节 | 「pale blue pigment spreads from fingertip to petal edge」 | 「nice colors」 |
| 情绪 | 「expression snaps from blank to stunned」 | 「she is surprised」（无层次）|
| 风格细节 | 「ink wash with one point of pale watercolor blue」 | 「ink style」（缺修饰）|

### 3.3 跨格连贯性

9 格之间必须有**叙事逻辑**：

- ✅ Panel 1-3 是同一时间瞬间的不同景别（远 / 中 / 近）
- ✅ Panel 1-9 是时间序列（早 → 晚）
- ✅ Panel 1-3 远景，4-6 中景，7-9 特写（节奏推进）
- ❌ 9 格毫无关联的不同场景（模型会随机生成，无法用作视频输入）

---

## 四、风格锁定（Style Anchor）

### 4.1 单一画风模式

如果整个镜头是同一阶段视觉（如阶段① 线稿），所有 9 格用同一锚定 prompt：

```
[Anchor]
pure pencil graphite on cream paper texture, hand-drawn wobble in
lines, cross-hatching for shadows, no color anywhere, architectural
sketch + figure drawing aesthetic.
```

### 4.2 阶段过渡模式（关键镜头）

某些镜头本身就是过渡（如 S3 从线稿 → 第一抹蓝），9 格内可以有渐变：

```
[Anchor]
ink wash style on cream paper transitioning to first hints of
watercolor color, the pivotal moment of color discovery.

Panel 1-3: still pure ink wash grey
Panel 4-6: first hints of pale blue emerging
Panel 7-9: half ink-wash half-watercolor-bloom
```

明确告诉模型「哪几格是哪种风格」，避免它随机分配。

---

## 五、角色一致性策略

### 5.1 跨镜头一致性的 3 个保险

| 层级 | 做法 | 效果 |
|---|---|---|
| **角色锚图集** | 每个阶段出 1 张角色独立图，作为参考输入 | ⭐⭐⭐ |
| **prompt 锚定短语** | 每个镜头 prompt 都用同一段角色描述短语开头 | ⭐⭐ |
| **首格特征锁定** | 9 宫格 Panel 1 强制是角色正面特写 | ⭐ |

### 5.2 推荐的角色锚图集（6-8 张）

针对四阶段视觉进化的 MV，必备：

1. 阶段① 风格 · 角色正面肖像
2. 阶段② 风格 · 角色半身像
3. 阶段③ 风格 · 角色侧面
4. 阶段④ 风格 · 角色正面肖像（与 #1 同构图，但风格全变）
5. 服装独立图（贯穿全片的标志性服装）
6. 关键道具图（如本案例中的单车）
7. 手部 / 表情特写
8. 标志性符号（如本案例中"扎头发的铅笔"）

### 5.3 prompt 锚定短语模板

```
A [年龄][身份] with [发型], wearing [服装], [关键道具], [特征],
[no jewelry / always with X].
```

例：
```
A young woman in her early 20s, art student / freelance painter,
with short hair where the front strands often blown by wind, wearing
a white t-shirt with paint stains, blue jeans, canvas shoes, a pencil
tucked through her hair tie, no jewelry.
```

---

## 六、9 宫格成图后的 Seedance 接入

### 6.1 整图喂参考（推荐）

把整张 9 宫格图作为 Seedance 2.0 image-to-video 的输入：

- 优点：单次出 15s 长镜头，运动连贯
- 缺点：Seedance 自己决定运镜，可能与 9 格的顺序不完全一致

### 6.2 首尾帧模式

把 9 格中的 Panel 1 + Panel 9 单独裁出来，作为首尾帧入口：

- 优点：起止状态精确锁定
- 缺点：中间过程模型自由发挥

### 6.3 混合模式（推荐复杂镜头）

- 上传整图作主参考
- 同时上传 Panel 1（首帧）+ Panel 9（尾帧）
- 上传角色锚图（保一致性）
- prompt 描述运动顺序（按 panel 编号）

---

## 七、避坑速查

| 错误 | 后果 | 修复 |
|---|---|---|
| 没有显式声明 16:9 单格 | 模型把每格塞成 1:1 方形 | 加入 §2.2 的声明段 |
| 9 格内突然变风格 | 视频段内画风跳跃 | 用 §4.2 阶段过渡模式 |
| Panel 描述太抽象 | 模型生成无关画面 | 按 §3.2 写关键瞬间 + 视觉细节 |
| 跨镜头角色变脸 | 镜头间不像同一个人 | 用 §5 三个保险全套 |
| 整图比例不是 16:9 | 视频输出要裁切 | GPT Image 2 API 强制 `aspect_ratio: "16:9"` |
| 没有锁定 4K 模式 | 单格分辨率不够 | API 加 `quality: "4K"` 参数 |
