# Seedance 2.0 · English Prompt Templates Library

> 来源：PDF《Seedance 2.0 使用手册》第六章「提示词库：80+ 专业模版」

## 使用原则

**这些模板仅供参考与改造，不要原封不动地由 Agent 代入 libtv-skill 调用。**

正确姿势：
1. 用户问「有哪些电商类的模板可以参考」→ 展示本文档相关分类
2. 用户挑选 / 改造后，**由用户决定**要发什么给 libtv-skill
3. Agent 的职责是搬运用户最终的描述，不是从这里选

---

## 通用公式回顾

```
[核心主体] + [动作/场景] + [风格/镜头] + [技术参数]
```

所有模板都遵循这个结构，`@` 前缀表示需要参考视频绑定的元素。

---

## 分类 1：电商产品类（E-commerce Products）

```
@product, a luxury watch, placed on a velvet cushion,
soft studio lighting, 8K, product photography, 3 seconds
```

```
@skincare_jar, opening to reveal cream, macro shot,
dewy skin aesthetic, 4K, 24fps
```

```
@sneakers, rotating 360 degrees, white background,
clean minimalism, 8K, 30fps
```

---

## 分类 2：生活方式类（Lifestyle）

```
@barista, pouring latte art into a cup, warm café lighting,
close-up, cozy vibe, 2K, 24fps
```

```
@yoga_pose, on a beach at sunrise, soft waves,
wide shot, serene, 4K, 30fps
```

```
@home_cooking, stirring a pot of soup, rustic kitchen,
warm tones, medium shot, 2K, 24fps
```

---

## 分类 3：影视剧情类（Film / Drama）

```
@detective, examining a crime scene, rain falling,
low-key lighting, suspenseful, 2K, 24fps
```

```
@couple, kissing in a rain-soaked street, cinematic,
shallow depth of field, romantic, 4K, 24fps
```

```
@superhero, flying over a city at night, neon lights,
dynamic angle, epic, 8K, 30fps
```

---

## 分类 4：音乐 MV 类（Music Video）

```
@singer, performing on a stage, pyrotechnics,
wide shot, energetic, 4K, 30fps
```

```
@dancer, contemporary dance in a white studio, slow motion,
fluid movement, 2K, 60fps
```

```
@band, playing in a garage, gritty aesthetic,
handheld camera, raw, 2K, 24fps
```

---

## 分类 5：旅游探险类（Travel / Adventure）

```
@hiker, standing on a mountain peak, panoramic view,
golden hour, epic, 8K, 24fps
```

```
@surfer, catching a wave at sunset, slow motion,
vibrant colors, 4K, 60fps
```

```
@backpacker, walking through a forest, misty atmosphere,
wide shot, tranquil, 2K, 24fps
```

---

## 分类 6：商业广告类（Commercial Ads）

```
@car, driving through a coastal road, golden hour light,
dynamic tracking shot, sleek, 8K, 24fps
```

```
@coffee_cup, steam rising, close-up,
warm tones, inviting, 4K, 30fps
```

```
@smartphone, screen lighting up in a dark room,
futuristic, close-up, 2K, 24fps
```

---

## 分类 7：特殊创意类（Special Creative）

```
@flower, blooming in reverse time, macro shot,
surreal, 4K, 30fps
```

```
@city, transforming from night to day in 5 seconds,
time-lapse, vibrant, 8K, 24fps
```

```
@ice_cube, melting into water, slow motion,
transparent, 2K, 60fps
```

---

## 分类 8：AI 短剧 / 短剧类（AI Short Drama）

```
@character1, a time traveler, appearing in a 1950s diner,
retro aesthetic, medium shot, 2K, 24fps
```

```
@robot, serving coffee in a futuristic café,
cyberpunk, close-up, 4K, 30fps
```

```
@princess, escaping a castle on a horse,
medieval, wide shot, epic, 8K, 24fps
```

---

## 进阶场景模板

### 场景 1：多镜头保持人物一致

```
@character1, same outfit and hairstyle as reference,
walking through a crowded market, medium shot, natural lighting
```

操作：在所有参考视频中绑定同一角色 `@character1`，开启「角色一致性」开关。

### 场景 2：多个片段无缝衔接

```
@character1 exits a café, camera follows her onto a busy street,
match cut, seamless transition, 24fps
```

操作：前一片段的尾帧作为后一片段的首帧，保持运镜方向一致。

### 场景 3：音乐卡点

```
@character1 dancing to the beat, sync with music at 1.5s and 3s,
dynamic camera movement, vibrant colors, music video style
```

操作：上传背景音乐，在提示词中指定卡点时间点。

---

## 技术参数速查

| 参数类 | 常用选项 | 适用场景 |
|--------|---------|---------|
| 分辨率 | `2K` / `4K` / `8K` | 2K 测试 / 4K 发布 / 8K 高端商业 |
| 帧率 | `24fps` / `30fps` / `60fps` | 电影感 / 社交媒体 / 慢动作 |
| 时长 | `3 seconds` / `5 seconds` | 短平快 / 有完整运镜 |
| 运动 | `smooth motion` / `slow motion` / `dynamic` | 稳定 / 唯美 / 动感 |
| 光影 | `soft studio lighting` / `golden hour light` / `low-key lighting` | 产品 / 唯美 / 悬疑 |
| 镜头 | `close-up` / `medium shot` / `wide shot` / `macro shot` | 细节 / 人物 / 场景 / 微距 |
| 运镜 | `dolly shot` / `tracking shot` / `handheld camera` / `Dutch angle` | 推拉 / 跟拍 / 手持 / 荷兰角 |
| 风格 | `cinematic` / `product photography` / `music video style` | 电影级 / 产品级 / MV 风 |
