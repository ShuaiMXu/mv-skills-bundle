# Suno 音乐生成 4 种打法手册

> 漫剧 MV 配乐的完整决策树和 prompt 模板。本文档是 SKILL.md 第五步的展开。

---

## 一、决策树（先看这个）

```
要不要人声？
├─ 不要 → 纯器乐
│   ├─ 严格卡 MV 时间点 → 方案 A: 分段生成
│   └─ 整体氛围优先   → 方案 B: 一次成片
└─ 要   → 带歌词
    ├─ 英文 → 方案 C: 带人声英文版
    └─ 中文 → 方案 D: 带人声中文版（需诗意翻译）
```

### 各方案 trade-off

| | 时长精度 | 段间转场 | 工期 | 适用场景 |
|---|---|---|---|---|
| A 分段生成 | ✅ 精确卡帧 | ⚠️ 需手动 crossfade | 30 分钟拼接 | MV 镜头必须卡音乐节拍 |
| B 一次成片 | ❌ ±10-20s 浮动 | ✅ 模型自处理 | 5 分钟出片 | 音乐先做、视频再剪去贴 |
| C 带人声英文 | ❌ ±10s | ✅ | 5 分钟出片 | 想要 Hook 强化记忆点 |
| D 带人声中文 | ❌ ±10s + 中文出片质量参差 | ✅ | 10 分钟出片（多生成几版选优）| 中文情感更直接 |

---

## 二、Suno UI 通用设置

### 必备
- **Custom Mode** ✓（一定不能用 Auto）
- **Model** = `chirp-v5` 或更新
- **Length** = 接近目标时长 + 5-15s 余量（用于后期 trim）

### 纯器乐 vs 带人声
- 纯器乐：**Make Instrumental** ✓ ON
- 带人声：**Make Instrumental** ✗ OFF，**Vocal Gender** 按需选（Female / Male）

### Lyrics 字段铁律 ⚠️

**这是最容易踩坑的地方**：

| 写法 | Suno 怎么理解 |
|---|---|
| `[Verse] When the night falls...` | 唱出歌词「When the night falls...」|
| `[Verse - rising tension, brass enters]` | section 是 Verse，描述当 production cue（不唱）|
| `Mellow piano solo, sparse and quiet` | **直接唱出来！** 重大踩坑 |
| `[Instrumental]` | 整段纯器乐 |
| `[piano solo]` | production cue（纯 cue，不唱）|

**核心规则**：方括号 `[...]` 里的内容是 cue（结构标签 + 简短描述），方括号外的英文是歌词。

---

## 三、方案 A · 分段生成（纯器乐 / 卡时间）

适用：MV 镜头必须严格卡音乐节拍（如 Drop 落下时镜头睁眼）

### 操作流程

1. 把整曲拆成 N 段（推荐 4 段对应四阶段视觉进化）
2. 每段独立 Custom 生成，长度设 25-30s（留剪辑余量）
3. 把所有段拖进 DaVinci / Premiere / Logic
4. 按 MV 时间轴精确卡到镜头切换点
5. 段间加 1-2 拍 crossfade

### 4 段标准模板（以 City Pop 漫剧为例）

#### 段 1 · Intro 0:00–0:26
```
Title: Ride - Sketch World Intro
Style: lo-fi city pop intro, BPM 128, mellow upright piano solo, warm tape hiss, vinyl crackle, aged cassette mood, minor key melancholy, faint train bell chimes, sparse, no drums, no bass, instrumental
Lyrics: [Instrumental]
```

#### 段 2 · Verse 0:26–0:52
```
Title: Ride - Ink Wash Awakening
Style: lo-fi city pop verse, BPM 130, vintage piano, brushed jazz drums, warm electric bass, light shaker, 80s analog synth pad, distant wind chimes, faint cicada, tape saturation, building, instrumental
Lyrics: [Instrumental]
```

#### 段 3 · Drop 0:52–1:20
```
Title: Ride - Color Drop
Style: 80s city pop chorus drop, BPM 132, bright brass stabs, trumpet, saxophone, vintage analog synth lead, retro handclaps, funky bassline, rim shots, uplifting explosion, warm vinyl, instrumental
Lyrics: [Instrumental]
```

#### 段 4 · Outro 1:20–1:45
```
Title: Ride - Sunset Outro
Style: lo-fi city pop outro, BPM 110, clean upright piano solo, subtle vinyl crackle, soft 80s synth pad, distant ocean breeze, tidal waves, contemplative warm, gradual fade, ride cymbal swell, instrumental
Lyrics: [Instrumental]
```

### 拼接技巧

- 段间用 0.5-1 拍 crossfade，不要硬切
- 段 2 → 段 3 之间可以加 0.5s 的 silence（Drop 前的「呼吸」感）
- 段 4 末尾用 fade-out 至 0db，预留 1s 静音留白

---

## 四、方案 B · 一次成片（纯器乐 / 氛围）

适用：音乐先做、视频再剪去贴音乐（节奏可灵活）

### 完整 prompt 模板

```
Title: Ride

Style of Music:
lo-fi city pop instrumental, 80s vintage, dynamic four-part journey,
BPM 130, upright piano, brass section, analog synth, drum kit, tape
hiss, vinyl crackle, anthemic drop, warm nostalgic, instrumental

Lyrics:
[Intro - half-time, sparse piano, tape hiss, no drums]

[Verse - gentle build, brushed drums enter, electric bass]

[Pre-Chorus - RISING TENSION, snare roll, riser, build up]

[Chorus Drop - FULL ENERGY anthemic euphoric, brass stabs, handclaps, full kit]

[Second Drop - EVEN HIGHER peak, double-time hihat, stacked brass]

[Outro - tempo pulls back to half-time, clean piano, ocean breeze, ride cymbal swell]

[End]
```

### 让节奏不平的 5 个关键词

| 位置 | 关键词 | 作用 |
|---|---|---|
| Style | `dynamic range from intimate whispered piano to anthemic brass euphoria` | 模型预知**动态范围大** |
| Intro | `half-time slow feel` + `breathy and quiet` | 强制慢且小声 |
| **Pre-Chorus** ⭐ | `RISING TENSION` + `build up` + `suspenseful pause` | 爆发前的能量建立（最缺这个）|
| Drop | `FULL ENERGY anthemic euphoric` + `explode in` | Drop 必须狂 |
| Second Drop | `EVEN HIGHER` + `peak intensity` | 第二波再高一阶 |
| Outro | `sudden tempo pulls back to half-time` | 急刹对比 |

**大写关键词**（`FULL ENERGY` / `RISING TENSION`）Suno V5 实测能更显著影响模型注意力。

---

## 五、方案 C · 带人声英文版

适用：想要 Hook 强化记忆点 / 海外发布 / 英文歌词出片质量比中文稳

### 完整模板（以 Ride v2 为例）

```
Title: Color Was Here

Style of Music:
warm lo-fi city pop, 80s vintage, dynamic four-part journey, BPM
130, soft female vocals building from whisper to anthem, upright
piano, brass section, analog synth, drum kit, tape hiss, vinyl
crackle, nostalgic uplifting

Lyrics:
[Intro - half-time, sparse piano, soft whispered vocal]
Black and white desk, paint gone dry
Coffee cold, the same dull sky
I forgot how blue could feel
Maybe nothing here is real

[Verse - brushed jazz drums enter, electric bass]
Push the bike out, hit the street
Sketch lines drawing under my feet
Wheels rolling through a paper world
Wind picks up, I don't know why

[Pre-Chorus - RISING TENSION, build up]
A blue line breaks beneath my hand
First color in a long, long time
Hold my breath and start to climb
Something's coming, something's coming

[Chorus Drop - FULL ENERGY anthemic, brass explosion]
Open my eyes, the world's on fire
Cobalt sky and golden light
I was blind, now I can see it
Color was here all this time
Color was here, color was here, color was here

[Second Drop - peak intensity, stacked vocals]
Pedal harder, faster, higher
Paint stains on my shirt I never saw
Every face I passed had a story
I just wasn't looking, now I see

[Outro - tempo pulls back to half-time, intimate piano]
Back to the desk, the brush in hand
Paint the road I rode today
Grey at the start, gold at the end
Tomorrow I'll ride again

[End]
```

### 歌词设计要点

| 段 | 字数 | 韵脚 | 情绪 |
|---|---|---|---|
| Intro | 4 行 | AABB | 麻木 / 失落 |
| Verse | 4 行 | AABB | 觉醒铺垫 |
| Pre-Chorus | 4 行 | ABAB | 张力建立 |
| Chorus | 5 行（Hook 三连）| 自由 | 爆发 |
| Second Drop | 4 行 | 自由 | 高潮延续 |
| Outro | 4 行 | 自由 | 归静 |

### Hook 设计

- **三连重复**：`Hook, Hook, Hook` Suno 会处理成 chant-style 副歌
- **核心立意压缩到一句**：本案例的「Color was here all this time」浓缩了整个 MV 的主题
- **可对位 MV 关键画面**：Hook 落下的瞬间对应 Drop 落下 + 全彩睁眼

---

## 六、方案 D · 带人声中文版

适用：本土发布 / 情感更直接 / 文化语境贴合

### 中文歌词诗意翻译方法论

**不能直译**，要做意译，保留意境而不是字面：

| 英文原句 | 直译（不好）| 诗意意译（推荐）| 改动逻辑 |
|---|---|---|---|
| `I forgot how blue could feel` | 我忘了蓝色是什么感觉 | 我忘了 蓝色 该是什么模样 | "模样" 比 "感觉" 具象 |
| `Sketch lines drawing under my feet` | 速写线条画在脚下 | 脚下是没画完的速写街 | 加"街"增加空间感 |
| `Wind picks up, I don't know why` | 风起，不知为何 | 风忽然吹来 像一句问候 | 拟人化，呼应「身体感受唤回感知」 |
| `Color was here all this time` | 色彩一直都在这里 | 色彩从未离开过 / 色彩一直都在 | 「离开」比「在这里」有情感重量 |
| `I just wasn't looking, now I see` | 我没在看，现在我看见 | 原来我一直在看 只是从未看见 | **反转句式**强调"看与看见的差别" |
| `Tomorrow I'll ride again` | 明天我会再骑 | 明天的清晨 我还想再骑一次 | 加「清晨」呼应 MV 开场，叙事闭环 |

### 押韵收口策略

- **Intro / Pre-Chorus**：故意不押 → 营造"麻木无序"或"张力期"
- **Verse / Chorus**：押 ai / e / ang 等开放韵 → 便于演唱
- **Outro**：不押 → 收尾归静，回到口语

### Style of Music 字段加普通话标记

```
soft Mandarin female vocals building from whisper to anthem
```

**关键词**：`Mandarin` / `Cantonese` / `Japanese` 等明确语种，让 Suno 选对发音模型。

### ⚠️ 中文 Suno 出片注意

1. 中文发音偶有怪：每段建议生成 4 版选优
2. 声调控制差：「色彩」可能唱成生硬 "ce cai"
3. Hook 重复处易出错：保留备选
4. **保底方案**：如果中文出不来满意的，回到英文版 + 中文字幕（听感和文化感都顾到）

---

## 七、Style Mimicry 防护（音乐侧）

### 禁用词汇

| 类别 | 禁止词例 | 替换 |
|---|---|---|
| City Pop 艺人 | Tatsuro Yamashita / 山下达郎、Anri / 杏里、Mariya Takeuchi | `lo-fi city pop`, `80s vintage Japanese citypop aesthetic` |
| Hyperpop 艺人 | Charli XCX、A. G. Cook、PinkPantheress | `hyperpop`, `bubblegum chiptune`, `chopped vocal stabs` |
| Lo-fi 艺人 | Nujabes、Tom Misch | `lo-fi hip hop`, `mellow jazzy beats`, `tape saturation` |
| 日系动画 OST | "新海诚 OST"、"Joe Hisaishi style" | `warm cinematic anime OST mood`, `Japanese animation soundtrack aesthetic` |
| 电子音乐 | Daft Punk、Aphex Twin | `french house`, `IDM`, `glitch electronic` |
| K-Pop | NewJeans、BLACKPINK style | `K-Pop bubblegum`, `synth-pop K-Pop aesthetic` |

### 替换原则

**用流派 + 乐器 + 情绪 + BPM 描述，不用具体艺人**：

```
❌ "in the style of Tatsuro Yamashita"
✅ "80s Japanese city pop, vintage analog synths, warm electric bass, brass stabs, BPM 130"
```

---

## 八、后期剪辑指南

### Suno 输出后的工序

1. **下载原始 WAV**（不是 MP3，保留动态范围）
2. **响度统一**：所有段调到 -14 LUFS（Spotify / YouTube 标准）
3. **均衡 EQ**：低切 80 Hz 以下（消除磁带噪的低频垃圾）
4. **段间过渡**：crossfade 0.5-2 拍
5. **MV 卡点**：把 Suno 输出与视频时间轴对齐，必要时 trim 镜头
6. **导出**：48kHz / 24-bit WAV → 视频压制时再转码

### 常见后期问题

| 问题 | 原因 | 解决 |
|---|---|---|
| Drop 太弱 | Suno 没识别到 "FULL ENERGY" | prompt 加 `maximalist production`, `wall of sound`, `gated reverb snare` |
| 段间情绪跳跃 | 分段生成段间风格不一致 | 加更长的 crossfade，或在某段 prompt 里加 reference 上一段的关键词 |
| 总时长偏差大 | 一次成片版无法精确控制 | 改用分段生成 |
| 人声发音怪 | Suno 中文模型不稳 | 多生成几版选优 / 改英文版 |
| 段末突然 fade-out | Suno 在 Length 接近时自动收尾 | Length 多设 5-10s 余量 |

---

## 九、Suno API 接入（进阶）

如果用户想批量生成（如尝试 10 个变体选优），可以走 Suno API：

- 官方 API：https://suno.com/api（需要 Pro / Premium 订阅）
- 第三方代理：siliconflow、replicate 等也有 Suno 模型
- 关键参数：`prompt`, `tags`, `make_instrumental`, `wait_audio`

但**MV 配乐通常一次出 4-8 版就够**，不建议大规模 API 调用。手工 UI 操作 + 人工选优更适合此场景。
