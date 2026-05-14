# Ride v2 复刻案例 · 端到端工作流实战

> 本案例展示如何用 `comic-mv-director` skill 把一份已有 MV 企划复刻成完整可制作方案。

---

## 项目背景

**原企划**：Ride v2 — Pop 骑行 MV（飞书文档）
- 总时长：1'45"
- 镜头数：25 帧关键帧
- 出图工具：Midjourney v7
- 风格：黑白线稿 → 水彩 → 全彩手绘动漫
- 故事：失去色彩感知的画师，通过骑行重新看见色彩

**用户需求**：用 GPT Image 2 + Seedance 2.0 + Suno 全 AI 工作流复刻一遍。

---

## 工作流分解

### 第一步 · CONCEPT（项目立项）

由于已有原企划，跳过提问，直接评估改造方向：

- ✅ 时长 1'45" → 8 镜头 × 13s 设计
- ✅ 画风水彩动漫 → 用 `style-presets.md` 中的「水彩动漫风」模板
- ✅ 四阶段视觉进化保留（线稿 → 墨线 → 水彩 → 全彩）
- ✅ 音乐 Lo-fi City Pop（原企划已有方向）
- ✅ 16:9 主流平台

---

### 第二步 · BREAKDOWN（25 帧 → 8 镜头重切）

#### 重切表

| 镜头# | 时长 | 合并原帧 | 阶段 | 9 宫格主题 | 核心运动 |
|---|---|---|---|---|---|
| **S1** | 0:00–0:13 | 帧01-04 | ① 线稿 | 线稿世界的清晨 | 俯拍画桌 → 推车 → 出门 → 街道骑行 |
| **S2** | 0:13–0:26 | 帧05-08 | ② 墨线灰调 | 灰调觉醒 | 水洼溅墨 → 下坡 → 头发飞扬 → 树影留白 |
| **S3** | 0:26–0:39 | 帧09-10 | ②→③ 转折 | 第一抹蓝 | 路口停车 → 划车架 → 指尖蓝 → 重新骑行 |
| **S4** | 0:39–0:52 | 帧11-13 | ③ 水彩渗入 | 花店爆发 | 经过花店 → 颜色爆炸 → 触碰花瓣 → 颜色扩散 |
| **S5** | 0:52–1:05 | 帧14-16 | ③→④ 上坡 | 上坡—闭眼—睁眼 | 上坡挣扎 → 坡顶喘气 → 闭眼听色 → 睁眼全彩 |
| **S6** | 1:05–1:20 | 帧17-20 | ④ 全饱和 | 全彩城市 | 下坡飞驰 → 衬衫特写 → 行人 → 蓝天仰拍 |
| **S7** | 1:20–1:35 | 帧21-23 | ④ 海边/回家 | 海边公路 → 画桌 | 黄昏海边 → 回到画桌 → 滴水复活颜料 → 第一笔 |
| **S8** | 1:35–1:45 | 帧24-25 | ④ Outro | 彩色肖像 + RIDE | 与帧02同构图的彩色版 → 画面延展 → 标题浮现 |

合计 8 × 13s ≈ 1'45"，匹配原企划。

#### 重切决策日志

- S6/S7 帧号边界：帧 21（海边公路）从 S6 调到 S7，因为它属于"全彩城市完成后"的情绪收束节拍，跟 S6 的"飞驰"调性不同
- S3 是关键转折镜头：仅有 2 帧但需独立成镜，因为「第一抹蓝」是全片的核心情感转折点

---

### 第三步 · GPT Image 2 PROMPT（9 宫格 storyboard）

#### S5（关键镜头）完整 prompt

```
A 9-panel storyboard (3 rows × 3 columns, thin white gridlines), the
pivotal transition from half-watercolor to FULL SATURATED ANIME COLOR,
the climactic perception breakthrough.

Panel 1: she climbs a steep hill, body leaning forward gritting teeth,
colors on both sides of the road FLICKERING between watercolor and
grey wash like a fading radio signal.
Panel 2: medium — when she pushes harder colors intensify, when she
falters they fade to grey, the saturation is fighting her exhaustion.
Panel 3: near the hilltop the frame is ALMOST PURE GREY again, the
physical limit threatening to take away what she just gained.
Panel 4: she reaches the hilltop, stops, feet on ground, panting
heavily, frame almost entirely grey ink wash.
Panel 5: she CLOSES HER EYES — not giving up but switching sensory
channels.
Panel 6: with eyes closed — colored SOUND WAVE RIPPLES emanate from
her ears outward, bird song as yellow ripples, wind as blue waves,
distant city hum as warm orange pulses, she is HEARING color
(synesthesia).
Panel 7: close-up of her face eyes closed, sound waves visible around
her head, expression peaceful and intent.
Panel 8: the MOMENT of breakthrough — eyes flying open, light flooding
from the open eyes outward.
Panel 9: HERO REVEAL — the entire city panorama from hilltop in FULL
SATURATED COLOR for the first time, cobalt blue sky, massive white
cumulus clouds, warm yellow buildings, coral pink walls, mint green
balconies, lavender purple signs, maximum saturation and golden
sunlight, her face lit with warm skin tone, her t-shirt revealed to
be splattered with vibrant paint stains all along.

Layout: 9 panels in a 3×3 grid, OVERALL image is 16:9, EACH panel is
also 16:9.

All 9 panels: the chromatic flickering of panels 1–4, the eyes-closed
synesthesia of 5–7, the explosive full-color reveal of 8–9. Style
evolves panel by panel. Overall aspect ratio 16:9.
```

#### Style Mimicry 检查

- ✅ 没有提到 Makoto Shinkai / Studio Ghibli
- ✅ 没有提到 da Vinci（虽然 S2 镜头有"motion study"概念但用"classical anatomical motion-study sketch"替换）
- ✅ 全部用描述性词汇

---

### 第四步 · SEEDANCE PROMPT（image-to-video）

#### S5 Seedance 运镜 prompt

```
Mood: physical struggle then breakthrough, the song's drop happens
at the eye-opening moment, BPM 128-135 full energy.

Motion:
0–3s: climbing hill, colors flickering grey/watercolor, expression
       straining.
3–5s: hilltop, stops, panting, frame nearly all grey.
5–8s: closes eyes, synesthetic color sound-waves emanate from ears
       (yellow bird song, blue wind, orange city hum).
8–10s: peaceful close-up, eyes closed, waves expanding.
10–11s: eyes FLY OPEN, light flooding outward from her eyes.
11–13s: HERO PANORAMA REVEAL — entire city in full saturated color,
       drop lands musically, paint stains visible on her shirt for
       the first time.

End frame: low angle of her with eyes open against full color city
panorama, golden hour light, the entire image at maximum saturation.

Camera: tight on struggle, intimate on closed eyes, then EXPLODES to
wide panorama at the drop. The most important camera moment in the
entire MV.
```

---

### 第五步 · SUNO PROMPT（音乐生成）

#### 方案 B · 分段生成（推荐）

#### 段 3 · Drop 0:52–1:20
```
Title: Ride - Color Drop
Style: 80s city pop chorus drop, BPM 132, bright brass stabs, trumpet,
saxophone, vintage analog synth lead, snappy retro handclaps, funky
bassline, vintage drum kit with rim shots, bright sky-feeling high
register synth pad, joyful uplifting explosion, saturated warm vinyl
tone, instrumental
Lyrics: [Instrumental]
```

#### 方案 D · 带人声中文版（备选）

完整中文歌词（诗意意译版）：

```
[Intro - 半节奏 钢琴稀疏 气声低吟]
画桌上的颜料 早已结块
咖啡凉透 天色一成不变
我忘了 蓝色 该是什么模样
这世界 像一张未填色的画

...

[Chorus Drop - FULL ENERGY 铜管爆发]
睁开眼的瞬间 世界在燃烧
钴蓝铺满天空 金色洒满肩
原来我从未失明 只是不曾看见
色彩 从未离开过
色彩一直都在 一直都在 一直都在
```

详见 `references/suno-music-handbook.md`。

---

### 第六步 · DELIVERY（交付包）

完整 markdown 文档（~14 KB）包含：

1. ✅ 项目概览（标题 / 总时长 / 画风 / 主题）
2. ✅ 8 镜头时间表
3. ✅ 8 × GPT Image 2 prompt（全部通过 Style Mimicry 检查）
4. ✅ 8 × Seedance 运镜 prompt
5. ✅ Suno 音乐 prompt（4 种打法可选）
6. ✅ 角色一致性参考图集（8 张）
7. ✅ 成本估算 ~220 元
8. ✅ 5 天制作排期
9. ✅ 风险与备选方案

#### 用 feishu-cli 一键导入飞书

```bash
feishu-cli doc import ride_v2_remake_plan.md \
  --title "Ride v2 复刻方案 · GPT Image 2 × Seedance 2.0"
# 返回飞书文档链接

feishu-cli perm public-update <DOC_ID> --link-share-entity anyone_editable
# 开放协作权限
```

---

## 迭代日志（v1.0 → v1.6）

| 版本 | 改动 | 触发原因 |
|---|---|---|
| v1.0 | 初版 | 项目立项 |
| v1.1 | 整图/单格画幅从 3:2 改为 16:9 | 用户指出 panel 比例问题 |
| v1.2 | 补全 S2/S4/S5/S7/S8 prompt | 用户要求展开省略部分 |
| v1.3 | 补全 S1/S3/S6 Seedance prompt | 用户发现 Seedance 缺失 |
| v1.4 | 删除所有 Style Mimicry 触发词 | GPT Image 2 实际拦截案例 |
| v1.5 | 新增 Suno 音乐 prompt（方案 A+B）| 用户提出加音乐需求 |
| v1.6 | Suno prompt 加入复古 city pop 细节 | 用户提供详细需求 |

---

## 全流程总结

| 步骤 | 工具 | 输出 | 工期 |
|---|---|---|---|
| 1. CONCEPT | comic-mv-director | 项目定调 | 5 分钟 |
| 2. BREAKDOWN | comic-mv-director | 8 镜头表 | 15 分钟 |
| 3. PROMPT 设计 | comic-mv-director + style-presets | 8 × prompt 对 | 1-2 小时 |
| 4. 角色锚图 | GPT Image 2 | 8 张参考图集 | 1 天 |
| 5. 9 宫格出图 | GPT Image 2 | 8 张 9 宫格图 | 1 天 |
| 6. Seedance 出视频 | Seedance 2.0 | 8 段 13s 视频 | 1 天 |
| 7. Suno 出音乐 | Suno V5 | 4 段或 1 段音频 | 1-2 小时 |
| 8. 后期拼接 | DaVinci / Premiere | 1'45" 成片 | 半天 |
| **总计** | | | **3-5 天**，成本 ~220 元 |

---

## 关键学习点

1. **不能 1:1 复刻**：25 帧粒度不适合 9 宫格 + Seedance 工作流，必须重切到 8 镜头粒度
2. **几何决定生死**：整图必须 16:9，否则 panel 会变方形，运动构图完全失败
3. **Style Mimicry 防护是隐性杀手**：一个 "Makoto Shinkai" 让整个 prompt 报错。必须前置检查
4. **音乐生成最关键的是动态对比**：Pre-Chorus 张力建立是让 Drop 有冲击力的核心
5. **Lyrics 字段是 Suno 最大的坑**：方括号内 = cue 不唱，方括号外 = 唱出来。混淆会得到"念论文"的诡异歌曲
