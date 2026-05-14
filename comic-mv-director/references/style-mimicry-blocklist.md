# Style Mimicry 防护清单

> OpenAI（GPT Image 2 / GPT-4o image）和 Suno 都启用了"style mimicry"防护，prompt 中具名引用**在世艺术家 / 知名 IP / 工作室**会被拦截。本文档是黑名单 + 替换策略。

---

## 一、为什么会被拦

### OpenAI 的策略
- 2025 年起强化「Style Mimicry Protection」
- 一旦 prompt 中出现在世艺术家姓名、工作室名、知名 IP 名，拦截理由：「关于与第三方内容相似性的防护限制」
- 错误信息长这样：`非常抱歉，该提示可能违反了关于与第三方内容相似性的防护限制。`

### Suno 的策略
- 类似 OpenAI 但更宽松
- 不会直接拒绝生成，但可能：① 生成质量降级；② Style 字段中的艺人名被静默忽略
- 偶尔会返回「too closely resembles existing copyrighted work」

---

## 二、视觉侧黑名单（GPT Image 2）

### 在世日系艺术家 / 导演

| 禁止词 | 触发原因 | 替换 |
|---|---|---|
| Makoto Shinkai / 新海诚 | 大热在世导演 | `cinematic anime golden-hour palette, deep cobalt skies, soft volumetric light, painterly clouds` |
| Mamoru Hosoda / 细田守 | 同上 | `hand-painted 2D animation, lush environments, expressive character design` |
| Naoko Yamada / 山田尚子 | 同上 | `delicate slice-of-life anime aesthetic, soft pastel palette, intimate framing` |
| Hayao Miyazaki / 宫崎骏 | 极敏感词 | `hand-painted 2D animation aesthetic, lush natural environments, whimsical creature design` |
| Yoshitaka Amano | 同上 | `ethereal painterly fantasy illustration, delicate ink lines, watercolor wash` |

### 知名动画工作室

| 禁止词 | 替换 |
|---|---|
| Studio Ghibli / 吉卜力 | `hand-painted 2D animation, lush natural environments, painterly clouds, warm nostalgic mood` |
| Kyoto Animation / 京阿尼 | `polished 2D anime with detailed character animation, slice-of-life aesthetic` |
| A-1 Pictures | `modern Japanese 2D animation, clean character design, vibrant color palette` |
| Madhouse | `2D anime with dynamic action choreography, expressive frame-by-frame animation` |
| Wit Studio / Mappa | `cinematic dark fantasy anime, dynamic camera angles, dramatic lighting` |
| Disney / Pixar | `3D animated film aesthetic with stylized shading and rounded character design` |

### 二次元亚文化画师

| 禁止词 | 替换 |
|---|---|
| Avogado6 | `surreal kawaii-horror illustration, simplified character design with eerie undertones` |
| 嫌儿（Xian Er） | `Chinese internet doodle illustration, minimalist cute character design` |
| 深爪（Shenzhua） | `Twitter-style chibi manga illustration, simple linework, expressive faces` |
| Yoshitomo Nara | `wide-eyed innocent yet unsettling character illustration, simplified portrait style` |

### IP 画风

| 禁止词 | 替换 |
|---|---|
| Tokidoki | `kidcore sticker-collage aesthetic, kawaii character mascots, candy palette` |
| Aggretsuko | `kawaii office-life cartoon, chibi character design, expressive simple faces` |
| Sanrio | `cute mascot character design, pastel kawaii aesthetic` |
| Adventure Time | `flat 2D cartoon aesthetic, simple geometric character design, vibrant flat colors` |
| Pokemon | `creature design with simple geometric forms, expressive faces, bold outlines` |
| Genshin Impact | `anime-style fantasy game character art, detailed costume design` |

### 摄影 / 电影风格艺术家

| 禁止词 | 替换 |
|---|---|
| Wes Anderson | `symmetrical centered composition, pastel palette, vintage props, dollhouse aesthetic` |
| Wong Kar Wai | `slow motion blurred neon city, melancholic mood, saturated colors, intimate close-ups` |
| Christopher Doyle | `handheld cinematography with saturated film grain, neon urban nightscape` |

### 古典 / 已故艺术家（保险起见也避免）

| 禁止词 | 触发原因 | 替换 |
|---|---|---|
| Leonardo da Vinci | 偶尔触发 | `classical anatomical motion-study sketch aesthetic, Renaissance drawing technique` |
| Van Gogh | 偶尔触发 | `post-impressionist swirling brushstrokes, thick impasto texture` |
| Hokusai | 偶尔触发 | `ukiyo-e woodblock print aesthetic, flat color planes, bold outlines` |

> 注：古典已故艺术家通常不会被拦，但偶尔会触发。保险起见用描述替换。

---

## 三、音乐侧黑名单（Suno）

### City Pop / Lo-fi 艺人

| 禁止词 | 替换 |
|---|---|
| Tatsuro Yamashita / 山下达郎 | `80s Japanese city pop, vintage analog synths, warm electric bass, brass stabs, BPM 130` |
| Anri / 杏里 | `80s Japanese city pop with female vocals, mellow piano, smooth bass` |
| Mariya Takeuchi / 竹内まりや | 同上 |
| Casiopea | `Japanese fusion jazz instrumental, technical drumming, smooth synth lead` |
| Tom Misch | `lo-fi jazzy guitar, mellow electric bass, warm vinyl tone` |
| Nujabes | `lo-fi hip hop, mellow jazzy beats, jazz piano samples, tape saturation` |
| FKJ | `lo-fi neo-soul instrumental, warm electric piano, smooth jazz harmonies` |

### Hyperpop / 电子艺人

| 禁止词 | 替换 |
|---|---|
| Charli XCX | `hyperpop bubblegum, pitched-up vocal chops, glitchy synths` |
| A. G. Cook / 100 gecs | `hyperpop maximalist production, chopped vocals, distorted synth stabs` |
| PinkPantheress | `bedroom pop dnb, breakbeat with sweet vocals, lo-fi production` |
| SOPHIE | `experimental hyperpop, metallic synth textures, pitched-up vocal chops` |

### J-Pop / K-Pop 艺人

| 禁止词 | 替换 |
|---|---|
| Kenshi Yonezu / 米津玄师 | `modern J-pop with introspective male vocals, alternative rock arrangement` |
| YOASOBI | `upbeat J-pop with female vocals, vivid synth-pop production, storytelling lyrics` |
| Kyary Pamyu Pamyu | `J-pop hyperactive kawaii, bubbly synths, chipmunk vocals` |
| BTS / NewJeans / BLACKPINK | `K-Pop synth-pop, female vocals, anthemic chorus, electronic production` |
| 初音未来 / Hatsune Miku | `vocaloid electronic, robotic female vocals, j-rock arrangement` |

### 古典 / 配乐

| 禁止词 | 替换 |
|---|---|
| Joe Hisaishi / 久石让 | `warm cinematic anime OST mood, Japanese animation soundtrack aesthetic, piano-led orchestral` |
| Hans Zimmer | `epic cinematic orchestral, dramatic brass and percussion, film score` |
| Ryuichi Sakamoto / 坂本龙一 | `minimalist contemporary classical piano, ambient atmospheric textures` |

### 电子 / EDM

| 禁止词 | 替换 |
|---|---|
| Daft Punk | `french house, vocoder vocals, funky disco basslines, vintage analog synths` |
| Aphex Twin | `IDM, glitchy intricate drum programming, ambient electronic` |
| Skrillex | `dubstep, heavy bass wobbles, distorted electronic drops` |

---

## 四、替换原则

### 4.1 三步法

1. **去掉所有专有名词**：艺人名、工作室名、IP 角色名
2. **抽取本质特征**：描边？调色？比例？笔触？氛围？乐器？BPM？
3. **用客观描述重组**：用流派 + 乐器 + 情绪 + 颜色 + 构图描述

### 4.2 反面 → 正面例子

```
❌ "Studio Ghibli style watercolor anime scene"
✅ "hand-painted 2D animation aesthetic, watercolor textures, lush
   natural environments, painterly clouds, warm cinematic golden-hour
   lighting, soft volumetric sunlight"

❌ "in the style of Avogado6"
✅ "surreal kawaii illustration with simplified character design,
   thick outlines, candy palette, slightly unsettling cute-horror
   undertone"

❌ "Tatsuro Yamashita inspired city pop"
✅ "80s Japanese city pop, vintage analog synths Roland Juno tone,
   warm electric bass, brass stabs trumpet sax, snappy handclaps,
   funky disco influence, BPM 130, vinyl tape saturation"
```

### 4.3 微妙的边界

以下词汇**通常可以用**（不是艺人 / IP）：

| 可以用 | 为什么 |
|---|---|
| `cyberpunk` | 流派词，不是某个 IP |
| `vaporwave` | 同上 |
| `cottagecore` / `kidcore` | 美学流派 |
| `Y2K aesthetic` | 时代风格 |
| `studio quality` / `cinematic` | 通用质量描述 |
| `Roland Juno-style` | 硬件型号，不是艺人 |
| `Marshall amp tone` | 同上 |
| `8K / HDR / RAW` | 技术参数 |

---

## 五、被拦后的诊断流程

### 5.1 如果生成失败

1. **看错误信息**：是否包含「与第三方内容相似性」「style mimicry」「resembles existing work」字样？
2. **扫 prompt**：哪些词可能是触发点？
3. **逐个去掉测试**：每次去掉一个可疑词，再生成，找到真正的触发词
4. **用描述替换**：参考本清单替换策略
5. **重试**

### 5.2 常见误判

某些词组合可能触发，但单独都不触发：

- `Makoto + sky` 通常没事，`Makoto Shinkai sky` 必被拦
- `Ghibli forest` 通常被拦，但 `Ghibli-inspired forest` 也被拦
- `anime` 安全，`anime in the style of [artist]` 被拦

**规则**：任何 `style of X` / `X-inspired` / `like X` 句式 + 艺人名都会被拦，**没有例外**。

---

## 六、最佳实践

### 6.1 prompt 写作流程

1. 先用画风**描述词**写完整 prompt
2. 全文搜一遍是否出现任何**专有名词**（人名、IP 名、工作室名）
3. 用本清单替换
4. 再生成

### 6.2 描述词选择

最稳的关键词类型：

- **流派词**（不带人名）：anime, manga, cyberpunk, vaporwave, kawaii, lo-fi
- **技术词**：watercolor, ink wash, pencil sketch, oil painting, digital art
- **构图词**：wide shot, close-up, low angle, symmetrical, rule of thirds
- **光线词**：golden hour, blue hour, rim lighting, chiaroscuro, soft volumetric
- **调色词**：cobalt, vermilion, ochre, pastel, saturated, muted
- **氛围词**：melancholic, nostalgic, euphoric, eerie, intimate, anthemic
- **时代词**：80s, Y2K, retro, vintage, modern, futuristic

### 6.3 检查清单

每次发 prompt 前问自己：

- [ ] 是否提到了任何**人名**（包括姓 / 名 / 简称）？
- [ ] 是否提到了任何**工作室 / 公司**名？
- [ ] 是否提到了任何**已存在的 IP / 作品**名？
- [ ] 是否用了 `style of X` / `inspired by X` / `like X` 句式（X 是人 / IP）？
- [ ] 描述词是否能让模型理解风格本质（而不是依赖参考人名）？

全部通过 → 安全。

---

## 七、本清单持续更新

OpenAI 和 Suno 的防护规则会随时间变化。新发现的触发词请追加到对应章节，注明发现日期。

最近更新：
- 2026-05-14：初版，基于 Ride v2 复刻项目踩坑总结
