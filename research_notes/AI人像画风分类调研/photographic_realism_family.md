# 摄影写实家族（Photographic Realism Family）：AI 文生图人像的"照片感"风格体系调研

> 调研日期：2026-10-11。范围：AI 文生图**人像**（非动漫），目标是让报告能够定义并细分"读起来像真实照片"的 AI 人像、列出识别线索（含"AI 味"）、建立中英提示词词表、并指出 2025–2026 各子类最合适的模型。
>
> **方法与局限说明**：本轮共完成约 40 次 WebSearch；WebFetch 与 curl 在本会话中被代理网关拒绝（CONNECT 403 / ENOTFOUND），因此**未能打开任何页面原文**，所有引证均来自搜索摘要层面的信息。随后本回合的共享搜索预算耗尽（limit 200/turn），后续补查未能执行。因此：(1) 多个引证只能定位到"来源集合"而非单页；(2) 不少来源是厂商博客 / 提示词站 / 聚合页，可靠性一般，已在条目中标注；(3) 2022–2024 的材料已标注"可能过时"。凡无法落实到 URL 的内容一律放入 Gaps 或标注为推断（Inferences）。

---

## 关键问题 1：摄影写实人像的子类（sub-genres）及其提示词词汇

### Takeaway
AI 提示词社区事实上已形成一套"按摄影门类 + 器材 + 光法 + 胶片"组合的子类体系：影棚/美妆/头像、杂志 editorial、电影剧照、纪实/街拍、"手机随手拍"快照写实、年代仿旧（Polaroid、一次性相机、80–90 年代）、胶片型号仿真（Kodak Portra 400、CineStill 800T、Ilford HP5）、黑白、以及含义漂移的"hyperrealism"。可查到的最稳定的"写实词干"是：`85mm`、`f/1.4–f/1.8`、`shallow depth of field`、`Rembrandt lighting`、`Kodak Portra 400`、`fine film grain`、`natural skin texture`、`minimal retouching`，并配合负面词 `plastic skin, oversharpening, HDR, CGI, waxy skin, heavy beauty retouching`。

### Cited Findings

**（A）影棚 / 美妆 / 头像（studio / beauty / headshot）——85mm 肖像词干与 Rembrandt 光**
- 一个提示词画廊的"85mm portrait"条目把 Kodak Portra 400 调色与"暖而略褪色的肤色、发丝高光处的 halation、阴影中的颗粒"绑定；其负面词明确排除 `Plastic skin, oversharpening, HDR, oversaturated colors, cartoon, CGI, waxy skin, heavy beauty retouching`；风格关键词包括 `85mm f/1.2–f/1.8`、`Dreamy bokeh`、`Natural skin texture`、`Minimal retouching` — [Carat 85mm portrait](https://carat.im/en/prompt-gallery/85mm-portrait)（提示词站，非权威）
- 一篇厂商博客给出的 Rembrandt 光示例提示词为：`Rembrandt lighting, single softbox positioned 45 degrees camera-left and 30 degrees above eye level, characteristic triangle of light on shadow-side cheek`，并搭配 `85mm f/1.4` 与 `Portra 400 grain` — [Picassoia: 8 lighting tricks for better AI portraits](https://blog.picassoia.com/8-lighting-tricks-for-better-ai-portraits)（厂商博客）
- Promptomania 的 Rembrandt 示例同样以"阴影侧脸颊的光三角 + 深色高领 + 85mm"为核心 — [Promptomania portrait prompts](https://promptomania.com/prompts/portrait-prompts)
- 一个面向 FLUX 的 golden-hour 人像示例使用 `85mm f/1.4, shallow depth of field, soft film grain, natural skin texture, Kodak Portra 400`，并指出可把光线短语换成 "Rembrandt lighting in a studio" 得到经典影棚效果；该页明确称 `natural skin texture` 有助于对抗 FLUX 在人像上"默认偏光滑、塑料"的倾向 — [Oakgen cinematic portrait golden hour](https://oakgen.ai/prompts/cinematic-portrait-golden-hour)（提示词站）

**（B）"手机随手拍"/ 快照写实（amateur / snapshot realism）**
- 一个 Flux.1 D 的 LoRA 以 `early 2010s snapshot photo captured with a phone and uploaded to facebook` 作为触发词，描述为"自然光、褪色洗白的色彩"的手机快照；其说明称 "FLUX chin"、"FLUX cheeks"、"FLUX bokeh" 现象被减弱但未消除 — [Civarchive（SeaArt 镜像）](https://civarchive.com/seaart/models/f04ccfde42424a45160762eeb1fabbf2/versions/26adb1d2a116d235c3133c2abecd6445)
- "Amateur Photography" Flux Dev LoRA（v6）的推荐设置：LoRA 权重 0.8、20 steps、低 denoise 的 hires fix；说明写道"需按提示词自行实验" — [HuggingFace Space loras.py](https://huggingface.co/spaces/X-HighVoltage-X/Flux.1-Fill-dev-Inpainting-Super-Realism-LoRA/blob/b53c891b9a19c5eee0885c2a111006ac241c3862/loras.py)
- Boreal Flux Dev v2 LoRA 定位为 "authentic, amateur-style photographs"，模型页称在较低 LoRA 强度下效果最佳，触发词为 `photo` — [PromptLayer: boreal-flux-dev-v2](https://www.promptlayer.com/models/boreal-flux-dev-v2)
- 一个 SD 系"amateur photography" LoRA 的触发写法为 `amateurphoto-v6-forcu:0.8`（与 Flux 版不同） — [PromptLayer: amateur-photography](https://www.promptlayer.com/models/amateur-photography)

**（C）年代仿旧：一次性相机 / Polaroid / 1990s**
- 90 年代一次性相机模拟提示词的典型要素：直闪（direct flash）、高光 bloom、中等颗粒、轻微偏绿；镜头描述为"定焦塑料镜头、除中心外略失焦" — [YouMind: 90s Disposable Camera Photo Simulation](https://youmind.com/prompts/90s-disposable-camera-photo-simulation-22574)
- 另一组一次性相机提示词强调"闪光导致脸和前景过曝、背景急剧暗落、黄到橙的色偏"，并显式排除 `modern smartphone sharpness, HDR, skin correction` — [Carat disposable camera photo](https://carat.im/en/prompt-gallery/disposable-camera-photo)；[CapCut disposable camera style](https://www.capcut.com/ideas/ai-image/ai-image-for-disposable-camera-style)
- Polaroid 风格指南的要点：Polaroid 以硬正面闪光拍摄，人脸被打亮、背景跌落 2–3 档进入阴影；边框细节有辨识度（SX-70 底宽上窄、Polaroid 600 边框更窄且偏奶油色）；"AI 模型默认渲染得过于锐利，必须显式要求柔化"；模糊写法 "Polaroid style" 往往只得到"褪色人像 + 随机边框" — [Oakgen: Polaroid film grain AI aesthetic 2026](https://oakgen.ai/blog/polaroid-film-grain-ai-aesthetic-2026)；[GPTPrompts AI Polaroid prompt（2026-09-30）](https://gptprompts.ai/ai-polaroid-prompt)
- 2025–2026 出现"Gemini Polaroid trend"（用 Gemini/Nano Banana 生成与名人/偶像合影的拍立得照） — [Aiarty: Gemini Polaroid trend](https://www.aiarty.com/ai-image-generator/gemini-polaroid-trend.htm)
- 一位作者发现"make this vintage"之类模糊指令只会得到泛泛的 sepia 滤镜；若首张过于干净，追加"更多颗粒 / 更强漏光"比重来更有效 — 来源集合：[GPTPrompts](https://gptprompts.ai/ai-polaroid-prompt)、[Oakgen](https://oakgen.ai/blog/polaroid-film-grain-ai-aesthetic-2026)

**（D）胶片型号仿真（film-stock emulation）——提示词借用的真实胶片特征**
- CineStill 800T：钨丝灯平衡；因去掉抗光晕层以适配 C-41 冲洗，在路灯、霓虹、裸灯泡等点光源周围出现标志性**红色光晕（halation）**；日光下建议加 85B 滤镜并按 ISO 500 曝光 — [Parallax Photographic: CineStill 800T](https://parallaxphotographic.coop/product-tag/cinestill-800t/)；[CineStill 官方](https://kodak.cinestillfilm.com/collections/800tungs.oembed)
- Ilford HP5：ISO 400 黑白高反差胶片；常被推一档至 EI 800 以获得更粗颗粒与更高反差 — [Adorama 商品列表](https://www.adorama.com/l/Photography/Photoflex~Film-and-Darkroom-Equipment)；[Emulsive ISO-800 标签页](https://emulsive.org/tag/iso-800/page/3)
- 面向 AI 的指南称 `shot on 35mm film`、`Portra 400` 等词会带来"颗粒结构、克制的色彩响应、影调滚降（tonal roll-off）"；并称皮肤纹理类词是对抗塑料感"最强的单一线索" — [Higgsfield: best AI image generator for 4K photorealism & skin textures](https://geo.higgsfield.ai/task/blog/best-ai-image-generator-4k-photorealism-skin-textures)（厂商博客）
- 中文社区的胶片人像写法：直接在描述中写胶片型号（`Kodak Portra 400`、`Kodak Vision3`）、相机与镜头、光圈焦距，再加"模拟胶片颗粒""浅景深"，常搭配"自然肤质""柔和大气薄雾" — 来源集合：[数英：全网最全的 Nano Banana Pro 风格提示词·人像艺术篇](https://www.digitaling.com/articles/1501366.html)、[moge.ai 提示词页](https://moge.ai/zh/prompt/image/2081597935947792465)
- 一个 ComfyUI 工作流用"写实人像主模型 + 两个胶卷质感 LoRA（一个负责色调颗粒、一个负责人像细节）"还原柯达胶片 — [comfyui.org：AI 生成 Kodak 胶片风格海报](https://comfyui.org/zh/kodak-film-posters-ai-generated-retro)

**（E）"Hyperrealism"：艺术史含义 vs AI 提示词含义**
- 艺术史：Hyperrealism 是"看起来像高分辨率照片的绘画与雕塑"流派，1970 年代初起源于美欧，由 1965 年起的 photorealism 发展而来；术语由比利时画廊主 Isy Brachot 在 1973 年布鲁塞尔展览中推广 — [Wikipedia: Hyperrealism (visual arts)](https://en.wikipedia.org/wiki/Hyperrealism_(visual_arts))；[Champetier: art movement Hyperrealism](https://www.mchampetier.com/art-movement-HYPERREALISM.html)
- AI 提示词语境：多篇指南认为堆叠 `hyper-realistic, 8k` 之类词并不能产生照片感，"照片感来自光线、纹理和微小瑕疵" — [Dropshot: realistic AI image prompts](https://aistudio.dropshot.io/en/blog/realistic-ai-image-prompts-free)；一份提示词库把 `hyperrealistic`、`8k` 列为"指向抛光、glamour 质感"的词，并给出反向词 `visible pores, fine lines, subtle blemishes` — [Stockimg: advanced prompt techniques for hyper-realistic results](https://stockimg.ai/blog/prompts/advanced-prompt-techniques-getting-hyper-realistic-results-from-your-ai-photo-generator)（厂商）
- 一份 Stable Diffusion 指南警告 `unreal engine, octane render, artstation trending, hyperdetailed, 8k` 在训练标注中大量来自 CG/概念艺术，会把人像拉向"渲染感" — [Higgsfield](https://geo.higgsfield.ai/task/blog/best-ai-image-generator-4k-photorealism-skin-textures)；常见做法是负面词加 `render, CGI, 3d` — [Aiarty: SD prompts for realistic photos](https://www.aiarty.com/stable-diffusion-prompts/stable-diffusion-prompts-for-realistic-photos.htm)

### Inferences
- 子类可以按"**谁拍的 / 用什么拍的 / 为什么拍**"三轴定义：影棚美妆与 editorial 是"专业器材 + 受控布光 + 商业目的"；电影剧照是"电影机 + 戏剧性布光 + 叙事"；纪实/街拍是"小型机（35mm、Leica 式）+ 自然光 + 抓拍"；快照写实是"手机/傻瓜机 + 闪光或自然光 + 非专业构图"；年代与胶片仿真则是在上述任何一类上叠加"介质签名"（颗粒、halation、色偏、边框）。这一框架是本调研的综合，而非单一来源。
- 从引证可见，2024–2026 社区的"写实"重心已从**堆画质词（8k、hyperrealistic、ultra detailed）**转向**描述真实拍摄条件与瑕疵**（specific lens、light source position、film stock、pores、asymmetry、sensor noise）；"hyperrealistic"一词在 AI 语境里已被相当多指南视为"反效果词"，与艺术史中"超越照片的精细绘画"含义脱钩。
- 胶片词之所以有效，是因为它们**同时编码**了颗粒、色彩科学、动态范围和典型拍摄场景（例如 CineStill 800T 几乎等价于"夜景霓虹 + 红色光晕"），比单独的 `film grain` 更能约束模型。
- 不同模型对相同胶片词的响应差异很大（见关键问题 5），因此报告中的词表应标注"模型相关、需实测"。

### Gaps
- 未能找到权威、独立（非厂商）的 editorial/fashion 与 documentary/street 子类的专门 AI 提示词指南（相关搜索在预算耗尽前未执行）；上述两类的定义只能依赖摄影学常识 + 本节推断。
- 未找到 daguerreotype（银版）风格 AI 提示词的任何来源。
- "cinematic film still"（anamorphic、teal-and-orange、2.39:1 等）专门指南的搜索未能执行。
- 未能读取任何页面全文，无法逐条核对各提示词站的完整 prompt 文本。

---

## 关键问题 2："AI 味"（the AI look）的识别线索、社区对策，以及 2025–2026 的变化

### Takeaway
社区公认的"AI 味"核心是**皮肤被抹平成塑料/蜡质、光线过于干净、面部过于对称、眼睛过亮过锐、以及模型特有的"同一张脸"**（FLUX 的"Fluxia"与裂纹下巴 "Flux chin"；Midjourney 的默认脸；GPT-4o 图像的黄/褐色偏 "piss filter"）。对策有四层：提示词（具体镜头/光源/瑕疵词、避免画质堆词）、参数（Flux guidance 从默认 3.5 降到约 2、Midjourney `--raw` 关闭风格化）、权重（Amateur Photography、Boreal 等快照类 LoRA；皮肤纹理 LoRA；realism checkpoint）、后处理（低 denoise img2img、Kontext "make person real"、加噪/加颗粒、RGB 色偏校正）。2025–2026 的新一代模型（FLUX.2、Nano Banana Pro、Seedream 4、HunyuanImage 3.0、Qwen-Image、Midjourney V7/V8）在皮肤、手部与一致性上有明显进步，但"塑料皮肤"问题在 FLUX.2 Klein 9B 等新模型中仍被社区报告。

### Cited Findings

**（A）"同一张脸"与结构性怪癖**
- "Flux chin"：HuggingFace 讨论区有用户试图用 inpaint 去除 FLUX 生成图中的"cleft chin / butt chin"，即便提示词很详细也拿不到预期结果 — [HF Space discussion: Tried to fix cleft chin](https://huggingface.co/spaces/SkalskiP/FLUX.1-inpaint-dev/discussions/3)
- 2026 年 1 月一篇博客把 FLUX.1 [pro] 人像反复出现的"同一张脸"命名为 "Fluxia"，特征包括"持续出现的优雅裂纹下巴"，作者认为是训练数据伪影，但该解释是推测而非官方说明 — [BudgetPixel: Who is Fluxia?](https://budgetpixel.com/blog/who-is-fluxia-the-mystery-behind-the-worlds-most-famous-non-existent-face)（博客，非研究来源）
- 已有专门的 FLUX 微调以"修复裂纹下巴与兔牙（bunny teeth）"为卖点 — [ModelsLab: flux polyhedron cleft chin and bunny teeth fix](https://modelslab.com/models/modelslab/flux-polyhedron-cleft-chin-and-bunny-teeth-fix-with-open-and-closed-mouth-female)
- r/StableDiffusion 2024-11-19 有关于该现象的讨论串（内容未能读取） — [Reddit 镜像](https://reddit.birdcat.cafe/r/StableDiffusion/s/xqdundvNK3)（2024 年材料，可能过时）
- 快照类 LoRA 页面同时提到 "FLUX chin"、"FLUX cheeks"、"FLUX bokeh" 三个被社区命名的 FLUX 特征，并称其被"减弱但未消除" — [Civarchive](https://civarchive.com/seaart/models/f04ccfde42424a45160762eeb1fabbf2/versions/26adb1d2a116d235c3133c2abecd6445)
- Midjourney "默认脸"：一个 Substack 评论串中，用户报告无论提示不同发色眼色都得到近乎相同的"年轻、浅肤色"面孔，另一人称男性面孔总像某位名人；作者归因于训练数据偏差。**这是零散个人报告，未找到任何量化研究** — [Bantjes Substack 评论](https://bantjes.substack.com/p/ai-part-1/comments)
- Midjourney 官方应对"角色一致性"（与"默认脸"相反的问题）的功能是 `--cref`（Character Reference，约 v6 引入）与 `--cw`（character weight） — [Tom's Guide](https://www.tomsguide.com/ai/ai-image-video/how-to-use-midjourneys-new-consistent-character-feature)；[CDOTrends](https://www.cdotrends.com/story/3858/midjourney-now-lets-you-generate-consistent-characters-across-multiple-images)

**（B）塑料皮肤 / 过度平滑**
- 用户抱怨 Flux 皮肤"像实心塑料"，降低 distilled CFG 只部分缓解 — [Stable Diffusion Art 论坛: Fix Flux plastic skin](https://stable-diffusion-art.com/forums/topic/fix-flux-plastic-skin)
- Reddit 评论建议把 Flux Guidance 降到约 2，因为默认 3.5 会产生"糟糕的塑料皮肤纹理" — 来源集合：[r/FluxAI 讨论串（2025-04-26）](https://redlib.ssps.io/r/FluxAI/comments/1k87kmo/is_my_lora_getting_better)、[r/StableDiffusion 快照（2026-03-13）](https://reddit.sentinel-team.org/posts/1rsfvxv/snapshots/2026-03-13T21%3A28%3A18.36706Z)
- 同一 r/FluxAI 串中：realism LoRA（Amateur Photography、Boreal）即便低权重也会改变角色 LoRA 的脸；有评论主张更好的路径是"训练时用真实照片做正则化"，混合 LoRA 效果差得多 — [r/FluxAI](https://redlib.ssps.io/r/FluxAI/comments/1k87kmo/is_my_lora_getting_better/mp597lv/?context=3)
- 后处理方案：低 denoise img2img + 皮肤 LoRA，再在 Photoshop 中锐化、加噪、叠纹理 — [Stable Diffusion Art 论坛](https://stable-diffusion-art.com/?p=17219)
- FLUX.2 Klein 9B（2026）仍有"plastic skin bug"的社区报告，并出现专门引入"细微毛孔、自然瑕疵"的 LoRA 与"Enhanced Details LoRA + 触发词"教程（效果未经验证） — [AIStudyNow: fix plastic skin bug in Flux 2 Klein 9B](https://aistudynow.com/how-to-fix-the-plastic-skin-bug-in-flux-2-klein-9b-enhance-realism/)
- 专用修复模型：Flux Kontext 微调 "kontext-make-person-real"，用于把 AI 皮肤的塑料质感修回真实 — [Replicate: fofr/kontext-make-person-real](https://replicate.com/fofr/kontext-make-person-real)
- 问题根源描述："AI 模型往往过度平滑纹理，丢失毛孔、细纹、泛红和轻微瑕疵等让皮肤显得真实的不规则性" — [Morphic: fix AI-generated skin](https://morphic.com/resources/how-to/fix-ai-generated-skin-realistic)；[Upsampler: make skin texture look more real](https://upsampler.com/blog/make-skin-texture-in-ai-look-more-real)
- ComfyUI 社区做法：加人像类 LoRA 强度 0.4 以优化肤质 — [comfyui.org：boost texture and skin realism](https://comfyui.org/zh/boost-texture-and-skin-realism-with-comfyui)
- 一份指南称"通常一秒内就能认出生成人像：皮肤无毛孔、光线对称、眼睛太干净"；并称"传感器噪点、轻微运动模糊、雾气是只出现在真实拍摄中的伪影" — [Higgsfield](https://geo.higgsfield.ai/task/blog/best-ai-image-generator-4k-photorealism-skin-textures)

**（C）对称、完美散景、恐怖谷**
- 厂商博客：皮肤太光滑无毛孔的"过度完美"反而增加不真实感；归因于训练数据中大量精修照片 — [Imagera: how to make AI faces look real 2026](https://imagera.ai/blog/how-to-make-ai-faces-look-real-2026)；[ZSky: fix AI faces looking weird](https://zsky.ai/blog/fix-ai-faces-looking-weird.html)
- "完全对称让面孔显得人工"，有教程专门教"雕刻真实的面部不对称" — [SelfieLab: sculpting realistic facial asymmetry（2026-02-11）](https://selfielabstudio.com/blog/ai-art-tutorial-sculpting-realistic-facial-asymmetry-20260211)
- 一位摄影师的社交帖子认为生成模型"做不对散景"，因为不同镜头对失焦区域有不同且独特的畸变 — [Mastodon 帖](https://chirp.zadzmo.org/@aaron/statuses/01KCDD5VNT5XWHN81JBGHXAG3Q)（个人观点）；反例：一张手机人像模式的真实照片因"假散景"被误判为 AI — [Lemmy 讨论](https://lemmy.brendan.ie/post/52836)
- 恐怖谷概念源自森政弘（Mori Masahiro）1970 年 — [Cyberclick: why do AI images look uncanny](https://www.cyberclick.net/numericalblogen/why-do-ai-generated-images-look-uncanny)
- 规避建议（厂商类来源）：加入纹理与瑕疵词（`freckles, pores, laugh lines, sun-kissed skin`），显式要求不对称，**命名具体光源**（否则模型默认中性正面光），指定 `85mm` 或 `50mm` 等镜头以锚定摄影写实 — [Imagera](https://imagera.ai/blog/how-to-make-ai-faces-look-real-2026)；[Cloudinary: how to make AI images look real](https://cloudinary.com/guides/image-generation/how-to-make-ai-images-look-real)（"光线是 AI 图像显假的最大原因：画面太发光、阴影太干净"）

**（D）GPT-4o / GPT-image 的黄色偏（"piss filter"）**
- 2025 年 3 月 GPT-4o 图像生成上线后，用户注意到持续的黄/褐色调；Freepik 的分析描述为"白变奶油色、肤色发黄疸"，并通过让模型重建已知参考图来量化暖色偏；给出一行 RGB 缩放的修正 — [Freepik: fixing OpenAI's color bias with simple RGB scaling](https://www.freepik.com/blog/fixing-openais-color-bias-with-simple-rgb-scaling)
- 该现象被社区称为 "piss filter"，并催生独立修正工具 UnYellowGPT；成因解释不一（DALL-E 集成、解码管线的"house style"、甚至"模型崩塌"说），**无 OpenAI 官方说明** — [PopularAI: ChatGPT's 'piss filter'](https://www.popularai.org/p/chatgpts-piss-filter-why-ai-images)；[Know Your Meme: AI Art Becoming Yellow](https://amp.knowyourmeme.com/memes/ai-art-becoming-yellow)；[Korben: fix AI color balance](https://korben.info/en/fix-ai-color-balance-practical-solutions.html)

**（E）Midjourney 的 `--raw` / `--style raw`**
- 官方文档：Raw 关闭默认的"auto-pilot"艺术加工，简单提示词更容易得到照片感；在 Imagine 栏提示词末尾加 `--raw`；适用于 5.1 及之后版本；页面提到 V8.1 — [Midjourney Docs: Style](https://docs.midjourney.com/docs/style)
- 第三方指南称 V8.1 于 2026 年 6 月成为默认版本，V7 仍可选；并称 V8 默认更"摄影"，V7 更偏绘画感 — [Blake Crosley: Midjourney V8.1 + V7 Reference](https://www.blakecrosley.com/guides/midjourney)；[MindStudio: Midjourney V8 vs V7](https://www.mindstudio.ai/blog/midjourney-v8-vs-v7-comparison)（均非官方）
- 第三方做法：Raw + 低 `--stylize` + 机身/焦段/光圈/胶片词，用于最大化字面控制 — [Evolink Midjourney V7 prompt guide](https://docs.evolink.ai/en/api-manual/image-series/midjourney/midjourney-v7-prompt-guide.md)

**（F）2025–2026 模型更迭对"AI 味"的影响**
- Midjourney V7 于 2025 年 4 月 3–4 日 alpha 上线；发布报道称手指/手部、皮肤与织物材质更真实；但 Decrypt 实测认为相对 V6.1 只是"适度改进"，在写实、提示遵循、解剖、风格理解四项上结果参差；Geeky Gadgets 50 提示词测试称"真实手部与群像面孔"仍是难点；使用 V7 需先给 200 组图像对打分以解锁个性化 — [Decrypt V7 review](https://decrypt.co/313704/midjourney-v7-review-struggles-keep-up)；[Geeky Gadgets](https://www.geeky-gadgets.com/first-look-at-new-Midjourney-v7-image-generator-50-different-prompts-tested/)；[TechRepublic](https://www.techrepublic.com/article/news-midjourney-v7/)；[Learnopoly](https://learnopoly.com/?p=24556)
- FLUX.2（Black Forest Labs）：ComfyUI 文档称可输出最高 4MP 的照片级图像，"光线、皮肤、织物与手部细节大幅改善"，支持最多 10 张参考图的一致性；变体含 FLUX.2 Dev（开源 BF16）、Dev FP8（与 NVIDIA 合作）、Pro（API） — [ComfyUI Docs: FLUX.2 Dev](https://docs.comfy.org/tutorials/flux/flux-2-dev)；[comfyui.org FLUX.2 Day-0](https://www.comfyui.org/en/flux2-state-of-the-art-visual-intelligence)；[LTX Studio](https://website.ltx.studio/blog/flux-2-in-ltx)。**官方公告与确切发布日期未能核实**（搜索未返回 blackforestlabs.ai）
- Nano Banana Pro（Gemini 3 Pro Image）2025-11-20 发布：可融合最多 14 张输入图并保持最多 5 人的相貌一致；支持相机角度、对焦、调色（color grading）、光线（含昼夜转换）等局部控制；2K/4K 输出；可用 Google Search 做事实接地 — [BGR](https://bgr.com/2031723/nano-banana-pro-google-gemini-3-image-generator/)；[Yahoo Tech](https://tech.yahoo.com/ai/gemini/articles/nano-banana-pro-google-ai-171050219.html)；[TechNews（繁中，2025-11-21）](https://technews.tw/2025/11/21/7-tips-to-get-the-most-out-of-nano-banana-pro/)
- Seedream 4.0（字节 Seed）技术报告 arXiv 2509.20427，v1 2025-09-24；统一文生图、编辑与多图合成于单一框架，使用高效 DiT 与可大幅压缩图像 token 的 VAE；产品页称最高 4K — [fugumt 论文摘要页](https://fugumt.com/fugumt/paper_check/2509.20427v1)；[Seedream 4.0 官方页](https://seed.bytedance.com/seedream4_0)；Freepik 文档称其"兼具 photorealism 与多参考编辑" — [Freepik Seedream 4.0 docs](https://br.freepik.com/ai/docs/seedream-4-0)
- HunyuanImage 3.0 技术报告 arXiv 2509.23951（2025-09），其参考文献引用 Seedream 4.0（2509.20427）与 Qwen-Image（2508.02324） — [arXiv PDF](https://arxiv.org/pdf/2509.23951)
- Qwen-Image 技术报告 arXiv 2508.02324（2025-08）：20B 参数 MMDiT，主打复杂文字渲染与精确编辑；报告正文称"更真实的视觉风格" — [arXiv PDF](https://arxiv.org/pdf/2508.02324)；[HF 模型卡](https://huggingface.co/Qwen/Qwen-Image)；[Qwen-Image-Edit-2509](https://huggingface.co/Qwen/Qwen-Image-Edit-2509)

### Inferences
- "AI 味"可分为三层：**介质层**（无传感器噪点、无镜头缺陷、过度锐利）、**生理层**（塑料皮肤、对称、牙/手错误、眼睛过亮）、**模型签名层**（Flux chin/Fluxia、Midjourney 默认脸、GPT 黄偏、FLUX bokeh 式"永远虚化的背景"）。第三层随模型版本变化最快，报告应注明"版本相关"。
- 快照类 LoRA（Amateur Photography、Boreal）之所以有效，是因为它们一次性注入了介质层的全部"业余签名"（手机色彩科学、直闪、构图随意、低动态范围），比逐词提示更稳定；代价是会侵蚀角色相似度（见 r/FluxAI 报告）。
- 对闭源模型（GPT-image、Nano Banana、Midjourney），用户无法改 CFG 或加 LoRA，所以"对策"集中在提示词（命名光源、镜头、胶片、瑕疵）与后处理（色偏校正、加颗粒）；对开源模型（Flux、Qwen-Image、HunyuanImage、SDXL 系）则多一层参数与权重手段。
- GPT-4o 的黄偏在 2025 年是判定"ChatGPT 出图"的最快线索之一；但本轮未能确认 GPT Image 1.5 / GPT Image 2 是否已消除该偏色（见 Gaps），报告须谨慎表述为"2025 年现象"。

### Gaps
- 未找到 Black Forest Labs 关于 "Flux chin" 成因的官方说明；"Fluxia"分析仅为博客推测。
- "Midjourney face"（默认脸）没有任何量化研究或官方承认，只有零散用户报告。
- GPT Image 1.5（2025-12）与 GPT Image 2（2026）是否修复黄偏、以及二者的发布说明——相关搜索在预算耗尽前未执行。
- 未能读取 Midjourney 官方文档全文，无法确认 `--style raw` 与 `--raw` 是否互为别名、以及 V7/V8 与 `--stylize` 的具体交互。
- Nano Banana（Gemini 2.5 Flash Image，2025-08）初版发布细节未能检索。
- 社区对 Seedream 4 / HunyuanImage 3 / Qwen-Image 的"模型签名"（特有 AI 味）尚未在本轮找到可引用的描述。

---

## 关键问题 3：摄影写实 vs "看起来像真的 3D 渲染"——老手如何区分，现代模型是否模糊了边界

### Takeaway
可引用的区分线索集中在：**介质签名**（传感器噪点的统计特征、镜头缺陷、运动模糊与雾霭只出现在真实拍摄）、**皮肤微细节**（毛孔、细纹、泛红）、**光线物理**（阴影是否"太干净"、多光源方向是否自洽）与**眼部 catchlights**（双眼反光是否一致、是否对应场景中的真实光源）。社区还指出一组会把人像"拉向 CG"的词（`unreal engine, octane render, artstation trending, hyperdetailed, 8k`）。来源基本为博客/厂商，没有找到针对"AI 照片 vs AI 3D 渲染"这一特定二分的严格研究；检测器准确率的独立测试被引为 65–90%。

### Cited Findings
- 真实相机留下的噪点统计与传感器类型、ISO、曝光相关，而 AI 输出"几乎无噪点，或噪点在整幅均匀分布" — [Eyesift: AI-generated images vs real](https://www.eyesift.com/blog/ai-generated-images-vs-real/)（厂商相关博客，非同行评审）
- 眼部 catchlights 是常用检查项：双眼反光不一致、或反光与场景中任何真实光源不匹配，是反复出现的信号 — 来源集合：[Sightengine: how to spot AI images and deepfakes](https://sightengine.com/how-to-spot-ai-images-and-deepfakes)、[IsItAI: how to spot AI-generated images](https://isitai.com/blog/how-to-spot-ai-generated-images)
- 场景内光线不一致（单一光源却有多个方向的影子）是另一线索；EXIF 缺失是弱证据，因为平台会剥离元数据、也可伪造 — [Skylum: how to tell if a photo is AI generated](https://blog.skylum.com/how-to-tell-if-a-photo-is-ai-generated/)
- 皮肤过度光滑并非决定性证据，因为专业精修多年来也会抹平皮肤 — [Skylum](https://blog.skylum.com/how-to-tell-if-a-photo-is-ai-generated/)
- "传感器噪点、轻微运动模糊、雾霭是只在真实拍摄中出现的伪影"；`unreal engine, octane render, artstation trending, hyperdetailed, 8k` 等词因训练标注大量来自 CG/概念艺术，会把人像拉向渲染感 — [Higgsfield](https://geo.higgsfield.ai/task/blog/best-ai-image-generator-4k-photorealism-skin-textures)
- 负面词 `render, CGI, 3d` 是把 SD 系模型从渲染感拉回照片感的常见手段 — [Aiarty](https://www.aiarty.com/stable-diffusion-prompts/stable-diffusion-prompts-for-realistic-photos.htm)
- 一份"12 个 AI 图像显假的线索"清单（厂商） — [MagicShot: 12 tells](https://magicshot.ai/blog/why-your-ai-images-still-look-fake-12-tells-and-how-to-kill-them)
- 检测器可靠性：一份厂商发布的综述称独立测试中 AI 图像检测器准确率为 65–90%（厂商宣称 95%+），误报率 15–40% — [Imagera: bypass AI detection 2026](https://imagera.ai/blog/bypass-ai-detection-2026)（厂商，且立场为"绕过检测"，需谨慎）
- Stable Diffusion 默认输出"难以自然渲染毛孔与细微皮肤变化"，需要专门 LoRA 或微调；存在增强毛孔/毛发细节的社区 LoRA — [PromptZone: photorealistic portraits with SDXL](https://www.promptzone.com/shreya_alvarez/photorealistic-portraits-with-stable-diffusion-xl-5blg.md)；[comfyui.org: unlock hyper-realistic skin textures](https://www.comfyui.org/en/unlock-hyper-realistic-skin-textures)
- 多个来源一致建议"寻找多个相互独立且一致的信号，而非单一线索"，因为编辑、压缩和锐化都能模拟 AI 伪影 — 来源集合：[Sightengine](https://sightengine.com/how-to-spot-ai-images-and-deepfakes)、[Skylum](https://blog.skylum.com/how-to-tell-if-a-photo-is-ai-generated/)

### Inferences
- 老手区分"AI 照片"与"AI 拟真 3D 渲染"时，**决定性线索是介质层而非内容层**：渲染（无论多真）倾向于"全局一致的完美"——均匀清晰度、无噪点或均匀噪点、光滑的 subsurface 皮肤、理想化的圆形散景、无色差/无暗角；真实照片则带有"局部的不完美"——噪点随亮度变化、边缘色差、焦外过渡不规则、高光溢出（halation/bloom）、轻微运动模糊。这是对上述引证的综合，缺少专门研究支撑。
- 头发是常见判别点（渲染感头发呈"成束的光滑曲线"、照片中则有杂乱飞丝与半透明边缘），但本轮**未找到可引用来源**，仅作假设列入。
- 现代模型（FLUX.2、Nano Banana Pro、Seedream 4、GPT Image 2）在皮肤与光线上已显著缩小差距，使"内容层"线索（手、牙、对称）失效更快；但介质层线索（噪点统计、镜头缺陷）需要模型"主动模拟缺陷"，而默认倾向仍是"干净"，因此快照类 LoRA 与胶片词成为主流补救——这与关键问题 2 的发现一致。
- 对报告写作的建议：把"渲染 vs 照片"定义为**介质签名是否存在**，而不是"是否看起来真实"；这样 hyperreal 3D render 与 photographic realism 可以被清晰分成两个家族。

### Gaps
- 未找到任何同行评审研究或权威取证指南专门比较"AI 生成照片"与"AI 生成拟真渲染"的区分线索。
- 头发、牙齿、手部作为线索的现状（2025–2026 模型下是否仍有效）缺少可引用来源。
- r/StableDiffusion 等社区关于"looks like a render"的原始讨论串未被搜索引擎返回。

---

## 关键问题 4：中国市场的用法与词汇（AI写真、证件照、商业人像、胶片感、港风、复古、氛围感、高级感）

### Takeaway
中国市场的"照片感 AI 人像"以**产品化模板**而非自由提示词为主流入口：2023 年 7 月妙鸭相机以 9.9 元"上传 20 张照片 → 30 余种妆造写真"引爆 AI写真，直接对标海马体/天真蓝的证件照与艺术照；此后美图证件照、即梦（基于 Seedream）等把"证件照、职场写真/AI形象照、换装"做成固定功能。自由提示词社区（数英、ComfyUI 中文站、什么值得买、小红书教程）的词汇以**港风（茶餐厅/霓虹/旧公寓/天台 + 80–90 年代服装 + 钨丝灯与霓虹混光 + 胶片颗粒）**、**胶片感（直接写 Kodak Portra 400 / Vision3 + 颗粒 + 浅景深 + 自然肤质）**、**复古 / 王家卫式调色（偏暖、低饱和、深绿与红、动感模糊）**为代表。"氛围感""高级感"的正式定义本轮未能检索到。

### Cited Findings

**（A）妙鸭相机与 AI写真（2023，可能过时但具历史意义）**
- 2023 年 7 月 17 日，经历半个多月内测后妙鸭相机正式开放；以 9.9 元一口价对比海马体、天真蓝"一套基础证件照 200 元、艺术照动辄 500 元以上"；7 月 20 日晚高峰 4000–5000 人排队，需等待十几个小时出片 — [36氪：花9.9买套AI写真，「妙鸭相机」正让海马体们失业](https://www.36kr.com/p/2354909204790024)
- 用户只需上传 20 张照片，即可获得 30 多种风格精致妆造的写真照 — [界面新闻](https://www.jiemian.com/article/9799786.html)
- 争议：上海市消保委认为付款页"一旦购买成功，不支持退款"可能侵害消费者公平交易权；早期用户授权条款表述引发担忧 — [游民星空](https://www.gamersky.com/tech/202307/1624298.shtml)
- 爆火 18 天后热度回落，"从火爆到回归平静" — [界面新闻](https://www.jiemian.com/article/9867907.html)
- 其他同期报道：[数英](https://www.digitaling.com/articles/961057.html)、[人人都是产品经理](https://www.woshipm.com/it/5880455.html)、[凤凰网](https://news.ifeng.com/c/8RqWV1YxfwG)

**（B）证件照 / 职场写真 / AI形象照的产品化（2024–2025）**
- 美图证件照（美图秀秀旗下）提供数百种证件照规格，功能含智能抠图裁剪、超清美颜、AI换装、智能 AI 精修（切换发型妆造背景）；服装造型含"都市丽人、职场通勤、自然温婉、帅气西装"；App 名称含"职场写真 · AI形象照" — [App Store 页面](https://apps.apple.com/cn/app/id1584293308)；[AI工具集：美图证件照](https://ai-bot.cn/meituzhengjianzhao/)
- 即梦 AI（字节跳动）官方功能介绍侧重文生视频与基于 Seedream 的图片生成、短剧/短视频工具 — [APKMirror: Jimeng AI 1.6.7](https://www.apkmirror.com/apk/bytedance-pte-ltd/jimeng-ai-%E5%8D%B3%E6%A2%A6ai/)；[WebCatalog](https://webcatalog.io/en/apps/jianying-jimeng)；一篇第三方教程称即梦设有"AI证件照"入口（1 寸、2 寸、护照、签证尺寸，自动换背景裁切美颜），**该来源可靠性一般** — [tixiaolu](https://www.tixiaolu.com/v2/posts/v2-4d8e78dc.html)

**（C）港风 / 复古 / 王家卫式**
- 港风人像生成工具把关键词拆为"场景、服装、氛围"三块：场景含茶餐厅、霓虹街道、旧式公寓、天台；服装为 80–90 年代风格；情绪词"怀旧、电影感、忧郁"；画面特征为真实胶片颗粒、复古调色、老照片感，以及霓虹灯牌与暖色钨丝灯的混合光线 — [Felo 港风人像 agent](https://felo.ai/agents/ifgh6ybmJmRSAk665CP5Tn)
- 王家卫式后期教程：用醒图叠加深绿与红色贴纸、调整颗粒和对比度、再加动感模糊 — [什么值得买](https://post.smzdm.com/p/ae6km7kk/)
- 港风街拍攻略：想要港片质感可偏暖、降低饱和度、增加颗粒感；光线优先白天自然光，侧光或逆光可拍出发丝光泽 — [什么值得买](https://post.smzdm.com/p/a959n0g0/)
- 王家卫风格场景描述示例（香港狭窄街道上的逆光面摊、雨水、霓虹招牌映在湿沥青上） — [Morphic 中文页](https://morphic.com/zh/resources/videos/wong-kar-wai-style-videos)
- 一项"港式复古霓虹灯招牌海报"评测指出：模型生成的胶片颗粒、色差、暗角往往不够强，霓虹光效容易像滤镜叠加，对繁体字处理仍不稳定（GPT Image 2 与 wan2.7-image 测例） — [xsct.ai GPT Image 2 测例](https://xsct.ai/testcase/vg_posterla_016/gpt-image-2?lang=en)；[wan2.7-image 测例](https://xsct.ai/testcase/vg_posterla_016/wan2.7-image?lang=en)

**（D）胶片感提示词（中文社区写法）**
- 数英 2025–2026 整理的 Nano Banana Pro 人像提示词合集，以及中文提示词站的写法：直接写胶片型号（`Kodak Portra 400`、`Kodak Vision3`）、相机与镜头、光圈焦距，再加"模拟胶片颗粒""浅景深""自然肤质""柔和大气薄雾" — [数英：Nano Banana Pro 风格提示词·人像艺术篇](https://www.digitaling.com/articles/1501366.html)；[moge.ai](https://moge.ai/zh/prompt/image/2081597935947792465)；[BizyAir 社区模型](https://bizyair.cn/community/models/publicity/38046)
- ComfyUI 中文工作流：写实人像主模型 + 两个胶卷质感 LoRA（色调颗粒 / 人像细节） — [comfyui.org](https://comfyui.org/zh/kodak-film-posters-ai-generated-retro)
- 中文社区把 Flux 视为写实人像基准，称其输出常见"细密毛孔、细微皱纹和自然的皮肤光泽" — [Dreamina（CapCut）：哪些 AI 生成器皮肤纹理最真实](https://dreamina.capcut.com/ai-image/which-ai-image-generators-best-realistic-skin-textures)（厂商）

### Inferences
**中英词表映射（本调研综合；带 * 的中文词有上文引证支撑其用法，其余为常识性对应，未在本轮找到独立来源）：**

| 中文词 | 对应英文提示词 / 概念 | 备注 |
|---|---|---|
| AI写真* | AI portrait photoshoot / AI headshots（LoRA/人脸参考生成的成套写真） | 妙鸭相机语境；产品化模板为主 |
| 证件照* | ID photo / passport photo，`plain white/blue background, frontal, even lighting` | 美图证件照、即梦 |
| 职场写真 / AI形象照* | corporate headshot / LinkedIn headshot，`studio lighting, neutral backdrop, business attire` | 对应英文 studio/headshot 子类 |
| 商业人像 | commercial portrait / beauty & editorial，`beauty dish, butterfly lighting, clean retouch` | 本轮未找到专门来源 |
| 胶片感* | film look / `shot on Kodak Portra 400`, `film grain`, `halation`, `muted tones` | 中文社区直接写胶片型号 |
| 港风* | Hong Kong retro / `1980s–90s Hong Kong street, neon signs, tungsten light, cha chaan teng, film grain` | 常与王家卫式混用 |
| 复古* | vintage / retro，`faded colors, warm tone, light leaks` | 模糊词，需具体化为年代或介质 |
| 王家卫式* | Wong Kar-wai style，`neon, rain-soaked street, green-red cast, motion blur, step-printing` | 调色教程以深绿+红为核心 |
| 氛围感 | moody / atmospheric / cinematic，`low-key, haze, rim light` | 定义未能检索 |
| 高级感 | "elevated / editorial / understated luxury"，`low saturation, clean composition, soft directional light` | 定义未能检索 |
| 自然肤质* | natural skin texture / visible pores | 与英文社区反塑料感词一致 |
| 塑料感 / AI味 | plastic skin / "AI look" | 中文社区同样以皮肤为核心线索 |
| 浅景深* | shallow depth of field / bokeh | — |
| 模拟胶片颗粒* | film grain | — |
| 氛围光 / 钨丝灯* | tungsten / warm practical lights | 港风常用 |

- 中国市场的"照片感"消费主要走**产品模板**路径（上传自拍 → 固定风格），而英文社区主要走**自由提示词 + LoRA**路径；因此中文词汇更多是"成品风格名"（港风、法式、韩系、胶片、证件照、形象照），英文词汇更多是"拍摄参数"（85mm、Rembrandt、Portra）。报告在做词表映射时需说明这一语用差异。
- 2023 年妙鸭相机的快速降温与随后美图/即梦把写真功能"内嵌到通用工具"的路径一致，说明 AI写真从独立爆款变为通用图像工具里的一个模板分类——但 2024–2025 的市场数据本轮未能检索（见 Gaps）。

### Gaps
- "氛围感""高级感"在人像摄影/AI 语境中的正式定义、典型参数（低饱和、冷暖对比等）——搜索在预算耗尽前未执行。
- 妙鸭相机之后（2024–2025）AI写真市场的规模、即梦/美图 WHEE/可灵的写真功能细节——未能检索；可灵在证件照/商业人像方面的功能信息完全缺失。
- 小红书上成套的港风/胶片提示词模板未被搜索引擎返回。
- 中文社区对"AI味"的系统性描述（如"一眼假"的清单）未能检索。
- 36氪、数英等原文均未能打开，细节来自搜索摘要。

---

## 关键问题 5：2025–2026 哪些模型最适合照片级人像，以及各子类的优选

### Takeaway
截至 2026 年中的两大公开榜（Artificial Analysis、LMArena/arena.ai）均由 OpenAI GPT Image 2 领先，Google Nano Banana 2 / Nano Banana Pro 紧随，Reve 2.1、Seedream 5.0、xAI、Black Forest Labs 在次一梯队；arena.ai 设有专门的 "Photorealistic & Cinematic Imagery" 子榜但本轮未能读取其排名。针对人像写实的编辑性评测（多为平台博客）最常把 **FLUX.2 列为人像皮肤质感之首**，Google 系（Imagen 4 Ultra / Nano Banana）被称为"最接近照片的 API 输出"，Seedream 被定位为风格化/商业排版与多图一致性，Qwen-Image 被评为"牺牲微细节换氛围、适合电影感概念"。本地开源侧的 SDXL 时代定论是：Juggernaut XL 全能、RealVisXL 专精真人、CyberRealistic XL 偏商业干净；Flux 系需 24GB（Q8 约 12GB）显存。所有来源版本命名混乱，报告需逐一标注版本与日期。

### Cited Findings

**（A）榜单快照（2026）**
- Artificial Analysis 文生图榜快照：GPT Image 2 (high) 第一 1337，Reve 2.1 第二 1301，Nano Banana 2 与 Nano Banana 2 Lite 并列 1261，Nano Banana Pro 1223，Seedream 5.0 Pro 第 8 名 1239（页面未标注日期） — [BenchmarkList: Artificial Analysis text-to-image arena](https://benchmarklist.com/arenas/artificial_analysis_text_to_image/)
- fal.ai 2026 年 6 月指南：GPT Image 2 以 1,339 Elo 居 Artificial Analysis 榜首；Nano Banana 2 1,260；Nano Banana Pro 1,219 — [fal.ai: Best text-to-image APIs 2026](https://fal.ai/learn/tools/best-text-to-image-apis-2026)；另一篇 2026 年 6 月文章给 GPT Image 2 1338 — [Techsy](https://techsy.io/es/blog/best-ai-image-models)
- Artificial Analysis 模型库中列有 Qwen-Image 2.0 Pro（Alibaba Cloud，2026 年 5 月）、HunyuanImage 3.0 (Fal) 与 HunyuanImage 3.0 Instruct (Fal)，但快照中未见后两者排名 — [Artificial Analysis explore: qwen-image-2-0-pro](https://artificialanalysis.ai/image/explore/model/qwen-image-2-0-pro-alibaba-cloud-may-2026)
- DataLearner 转载榜（数据版本 2026-05-22）：Seedream 4 2K 居首 1,140，Seedream 5.0 Pro 第 11 名 1231——与上述快照冲突，可能是不同榜/筛选 — [DataLearner 文生图榜](https://www.datalearner.com/leaderboards/external/text-to-image)
- LMArena / arena.ai 文生图总榜 2026-05-12 快照：OpenAI 1393 第一，Google 1268、1242，OpenAI 1241，Google 1232；60 个模型、约 517 万票；2026 年 2 月快照为 46 个模型、OpenAI 1248 第一、Google 紧随，xAI 与 Black Forest Labs 其后；1393 相对 2 月的 1248 跳升幅度异常，需核对 — [LMArena text-to-image](https://lmarena.ai/ar/leaderboard/text-to-image)；[arena.ai overall](https://arena.ai/pl/leaderboard/text-to-image)
- arena.ai 设有 "Photorealistic & Cinematic Imagery" 分榜（排名未能读取） — [arena.ai photorealistic](https://arena.ai/leaderboard/text-to-image/photorealistic)
- 第三方盲测分（非同行评审）：Seedream 4.0 文生图约 1,221 vs HunyuanImage 3.0 Instruct 约 1,154；图像编辑反转为 1,185 vs 1,224；该站另设 text rendering、photorealism、portraits、art、commercial design、editing 分系列（分项分数未能读取） — [Gradually.ai: Seedream 4 vs HunyuanImage 3 Instruct](https://www.gradually.ai/en/ai-image-model-comparison/seedream-4-vs-hunyuanimage-3-instruct/)
- 2026 API 基准文章（平台博客）：GPT Image 2 vs Nano Banana 2/Pro vs Seedream 5.0 — [AtlasCloud](https://www.atlascloud.ai/nl/blog/guides/2026-ai-image-api-benchmark-gpt-image-2-vs-nano-banana-2-pro-vs-seedream-5-0)

**（B）编辑性评测对人像写实的判断（均为平台/厂商博客）**
- FLUX.2 被称为"portrait photorealism leader"，理由是人像皮肤纹理与有人物的 lifestyle 场景；另一来源称 FLUX.2 的"photorealism, skin texture, lighting 稳定处于顶级" — 来源集合：[getimg.ai best image generator](https://getimg.ai/blog/best-image-generator)、[AtlasCloud best models 2026](https://www.atlascloud.ai/blog/best-ai-image-generation-models-2026)、[Cliprise: Nano Banana 2 vs Imagen 4 vs Flux 2](https://www.cliprise.app/learn/comparisons/models/nano-banana-2-vs-imagen-4-vs-flux-2-image-model-comparison-2026)
- Imagen 4 Ultra 被一份开发者指南称为"2026 年公开 API 中最照片级的输出"；Nano Banana 被称为"以 photorealism 为基线"，Nano Banana 2 为"写实与真实世界准确性的更好默认" — 来源集合：[AtlasCloud developer guide](https://www.atlascloud.ai/blog/guides/best-ai-image-generation-apis-in-2026-complete-developer-guide)、[Magnific: best AI image models 2026](https://www.magnific.com/blog/best-ai-image-models/)、[Morphed: complete 2026 guide](https://morphed.app/blog/best-ai-image-generation-models)
- Seedream：一说"在风格化视觉、多图一致性与商业排版上占优"，另一说 Seedream 4 适合"photoreal final renders"——来源冲突 — [Picsart: Nano Banana vs Seedream](https://picsart.com/blog/nano-banana-vs-seedream-comparison/)；[Magic Hour: Nano Banana Pro vs Seedream 4 / Qwen Image / Wan 2.5](https://magichour.ai/blog/nano-banana-pro-comparison)
- Qwen-Image 相对 Seedream 4"牺牲微细节换取氛围"，更适合电影感概念而非产品级写实；多语言文字渲染优于西方对手 — [Magic Hour](https://magichour.ai/blog/nano-banana-pro-comparison)
- Picassoia 有 "FLUX.2 Max vs GPT Image 2 for realism" 对比，并声称 FLUX.2 Max 支持最多 8 张参考图（与 ComfyUI 文档的 10 张冲突，"Max" 变体未能另行核实） — [Picassoia](https://blog.picassoia.com/flux-2-max-vs-gpt-image-2-for-realism)

**（C）本地开源写实 checkpoint（SDXL 时代，2023–2025 材料，可能过时）**
- Juggernaut XL：最多下载的 SDXL checkpoint，"最好的全能型而非单项最佳"，人像/建筑/野生动物/产品均可；Ragnarok 版本发布日期在来源间冲突（2026-02 vs 2025-05） — [InsiderLLM: best photorealism checkpoints 2026](https://insiderllm.com/guides/best-photorealism-checkpoints-local-image-generation/)
- RealVisXL：被一致定位为人像专家，"可能是生成真实人类的最佳模型"，V5.0 被描述为"仅限真实人像"，不适合奇幻风景 — [AIIndigo: RealVisXL V4.0 review](https://aiindigo.com/blog/realvisxl-v4-0-review-the-standard-for-open-source-photorealism-in-2026-1)；[SimilarLabs RealVisXL](https://similarlabs.com/p/realvisxl-photorealism-sdxl-checkpoint)
- CyberRealistic XL：更干净的商业片；适合复杂场景/动作，LoRA 生态较小 — [InsiderLLM](https://insiderllm.com/guides/best-photorealism-checkpoints-local-image-generation/)；[OfflineCreator: Civitai realistic models](https://offlinecreator.com/civitai-realistic-models)
- epiCRealism：搜索结果中无具体信息 — （见 Gaps）
- 显存：SDXL 写实 checkpoint 一般需 8GB；Flux 需 24GB（Q8 约 12GB） — [InsiderLLM](https://insiderllm.com/guides/best-photorealism-checkpoints-local-image-generation/)
- SD 1.5 时代写实模型 Realistic Vision（2023，已过时但为"RAW photo, DSLR"词干的起源语境之一） — [Novita: Realistic Vision model](https://blogs.novita.ai/realistic-vision-model-for-stable-diffusion/)；[Decrypt: hyper-realistic images with Stable Diffusion](https://decrypt.co/233512/how-to-create-photorealistic-ai-pictures-with-stable-diffusion)

### Inferences（各子类优选，综合上述引证；均需实测验证）
- **影棚 / 美妆 / 头像**：FLUX.2（皮肤质感最常被点名）、Nano Banana Pro（多参考人脸一致性，适合"同一人多套写真"）、本地 RealVisXL/Juggernaut XL（低成本、可加皮肤 LoRA）。
- **Editorial / 时尚**：GPT Image 2 与 Nano Banana Pro（总榜领先、提示遵循强、可做文字与排版）、Seedream 4/5（商业排版与多图一致性被反复提及）。
- **电影剧照 / 氛围**：Qwen-Image（被评"换氛围"）、Midjourney V7/V8（`--raw` + 低 stylize；V8 据第三方更偏摄影）、FLUX.2。
- **纪实 / 街拍 / 手机快照**：开源 Flux.1 Dev/FLUX.2 + Amateur Photography / Boreal 类 LoRA 仍是唯一可引用的"专门方案"；闭源模型需靠提示词写"iPhone photo, direct flash, 2010s Facebook upload"等介质签名。
- **胶片 / 年代仿真**：所有模型都对胶片型号词有响应，但中文评测指出颗粒、色差、暗角"往往不够强"（GPT Image 2 / wan2.7 测例），因此开源 + 胶片 LoRA 的可控性更高。
- 榜单是**总体偏好**而非"照片感"专项；GPT Image 2 居首更多反映提示遵循与文字渲染，不能直接等同"最像照片"。arena.ai 的 photorealistic 分榜是最该被报告引用但本轮未能读取的数据。

### Gaps
- arena.ai "Photorealistic & Cinematic Imagery" 分榜的具体排名未能读取。
- Artificial Analysis 各快照的日期不一致且 DataLearner 数据与之冲突，无法给出单一权威排名。
- 未找到任何**独立、方法透明**的多模型人像写实盲测（所有编辑性评测均为平台/厂商博客）。
- epiCRealism 无任何可引用信息；Juggernaut Ragnarok 发布日期冲突未解。
- Midjourney V7 vs Flux vs Imagen 的人像对比评测、Qwen-Image-2512 写实更新、Flux "永远虚化背景"（FLUX bokeh）的修复方法——相关搜索未能执行。

---

## 关键问题 6：涉及真人肖像的法律与伦理要点（简要）

### Takeaway
2025 年是政策转向年：OpenAI 在 3 月随 GPT-4o 图像生成放开了对公众人物的限制（改为"公众人物可主动退出"），但仍禁止不实诽谤性描绘与未经同意的真人性相关图像；Sora 对在世公众人物仅允许经 Cameos 同意出现，已故名人在 2025 年 10 月引发争议。Midjourney 与 Grok 允许生成真人（含公众人物）但有限制；Google 曾于 2024 年 2 月暂停人物生成后恢复并加护栏。中国侧，妙鸭相机 2023 年的授权条款与"不支持退款"曾被上海消保委质疑。**所有公司现行政策原文本轮均未能读取**，报告应以"截至报道时"措辞。

### Cited Findings
- OpenAI 此前拒绝涉及真人（含政客）的图像请求；2025 年 3 月 GPT-4o 图像生成上线后政策转为允许公众人物，目标是允许讽刺与政治评论、同时拦截性露骨深伪，公众人物可选择退出 — [CBC: ChatGPT now lets users create fake images of politicians](https://www.cbc.ca/lite/story/1.7507039)
- 另一报道称过滤器仍拦截涉及公众人物的照片级不当内容与潜在深伪；该变化意味着公众人物需"主动退出"而非自动受保护 — [CO/AI](https://getcoai.com/news/chatgpts-image-generator-now-creates-public-figures-and-controversial-content)
- 第三方对 OpenAI 使用政策的整理：禁止生成对真人的虚假诽谤性描绘，以及未经同意的真人写实性图像 — [ConductAtlas: OpenAI usage policies](https://conductatlas.com/platform/openai/openai-usage-policies/prohibition-on-generating-real-person-defamation-and-non-consensual-intimate-images/)（二手摘要）
- OpenAI 致参议员信函称将继续执行"禁止未经许可使用他人肖像（含 NCII）"的政策 — [Shaheen 参议院办公室：OpenAI NCII letter response](https://www.shaheen.senate.gov/download/openai-ncii-letter-response?download=1)
- Sora：在世公众人物只能通过 Cameos 同意功能出现；对"近期去世"人物的遗产方可申请移除但未定义"近期"；Robin Williams、George Carlin 等已故名人深伪引发争议（2025-10-08） — [Axios](https://www.axios.com/2025/10/08/openai-sora-deepfakes-robin-williams-george-carlin)；Sora 曾以"历史人物"豁免生成已故名人片段 — [CO/AI](https://getcoai.com/?p=86764)
- Midjourney 与 Grok 允许生成真人（含公众人物），"有一些限制"，细节未披露 — [CBC](https://www.cbc.ca/lite/story/1.7507039)
- Google 于 2024 年 2 月因历史准确性争议暂停人物生成，后带护栏恢复；一篇低质量博客称 2026 年 2 月更新限制了公众人物、换脸与金融类图像——**未能另行核实** — [GPTPrompts](https://gptprompts.ai/ai-errors-and-fixes/gemini-wont-generate-images-of-people)
- 历史背景（2022）：OpenAI 重新开放 DALL-E 2 真人面部上传时，条款仍禁止未经同意上传他人照片，但执行一致性存疑 — [Gizmodo](https://gizmodo.com.au/?p=1819821)（2022 材料，已过时）
- 中国：妙鸭相机"不支持退款"条款被上海市消保委认为可能侵害公平交易权；早期授权条款引发肖像/数据担忧 — [游民星空](https://www.gamersky.com/tech/202307/1624298.shtml)

### Inferences
- 对"照片级人像"报告的直接含义：越像照片的输出，越容易触发各平台的真人/深伪过滤；因此很多写实提示词社区倾向于生成"不存在的人"（如 Fluxia 现象反过来说明模型默认倾向于一张"安全的通用脸"），而中国 AI写真产品则建立在用户上传本人照片的"自我授权"模式上，法律焦点从"深伪他人"转向"肖像数据授权与退款/消费者权益"。
- 2026 年各家政策极可能已再次变化（例如 Sora 与 GPT Image 2 的更新），本节仅能支撑"2025 年状态"。

### Gaps
- OpenAI、Midjourney、Google 现行（2026-10）使用政策原文均未能读取。
- GPT Image 1.5 / GPT Image 2 的真人与公众人物政策无任何检索结果。
- 中国《互联网信息服务深度合成管理规定》《生成式人工智能服务管理暂行办法》及 2025 年 AI 生成内容标识办法对 AI写真的具体约束——本轮未检索（属于常识性存在，但无引证）。

---

## 关键问题 7（补充）：AI 照片写实 2022 → 2026-10 的演进时间线（仅列有引证的节点）

### Takeaway
可引证的节点显示三阶段：2022–2023 "SD 1.5 写实 checkpoint + RAW photo/DSLR 词干 + 中国 AI写真模板爆发"；2024 "Flux.1 带来皮肤/手部跃升但形成 Flux chin / 塑料皮肤 / 永远虚化的新 AI 味，快照类 LoRA 兴起"；2025–2026 "闭源多模态（GPT-4o→GPT Image 2、Nano Banana→Pro→2、Seedream 4→5、Midjourney V7→V8.1）与开源（FLUX.2、Qwen-Image、HunyuanImage 3.0）同时把人脸一致性、局部光线/相机控制、4K 输出做成默认能力，'AI 味'从结构错误转向介质签名缺失"。

### Cited Findings
- 2022：OpenAI 重开 DALL-E 2 真人面部上传 — [Gizmodo](https://gizmodo.com.au/?p=1819821)
- 2023：SD 1.5 写实模型 Realistic Vision 流行 — [Novita](https://blogs.novita.ai/realistic-vision-model-for-stable-diffusion/)；2023-07-17 妙鸭相机开放，9.9 元 AI写真爆火 — [36氪](https://www.36kr.com/p/2354909204790024)
- 2024-02：Google 暂停人物生成后恢复 — [GPTPrompts](https://gptprompts.ai/ai-errors-and-fixes/gemini-wont-generate-images-of-people)（低质量来源）；2024-08：Flux LoRA 训练在 Civitai 普及（"一个触发词足够"） — [r/StableDiffusion 2024-08-28](https://redlib.ssps.io/r/StableDiffusion/comments/1f2yun6/comment/lkalnf4)；2024-11：Flux chin 讨论 — [Reddit 镜像](https://reddit.birdcat.cafe/r/StableDiffusion/s/xqdundvNK3)
- 2025-03：GPT-4o 图像生成上线，黄偏"piss filter"与公众人物政策放开 — [Freepik](https://www.freepik.com/blog/fixing-openais-color-bias-with-simple-rgb-scaling)；[CBC](https://www.cbc.ca/lite/story/1.7507039)
- 2025-04-03/04：Midjourney V7 alpha — [Decrypt](https://decrypt.co/313704/midjourney-v7-review-struggles-keep-up)
- 2025-08：Qwen-Image 技术报告 — [arXiv 2508.02324](https://arxiv.org/pdf/2508.02324)
- 2025-09-24：Seedream 4.0 报告；2025-09：HunyuanImage 3.0 报告 — [fugumt 2509.20427](https://fugumt.com/fugumt/paper_check/2509.20427v1)；[arXiv 2509.23951](https://arxiv.org/pdf/2509.23951)
- 2025-10-08：Sora 已故名人深伪争议 — [Axios](https://www.axios.com/2025/10/08/openai-sora-deepfakes-robin-williams-george-carlin)
- 2025-11-20：Nano Banana Pro（Gemini 3 Pro Image） — [BGR](https://bgr.com/2031723/nano-banana-pro-google-gemini-3-image-generator/)
- 2025 末（日期未核实）：FLUX.2 Dev/Pro — [ComfyUI Docs](https://docs.comfy.org/tutorials/flux/flux-2-dev)
- 2026-01：Fluxia 博客命名 FLUX 默认脸 — [BudgetPixel](https://budgetpixel.com/blog/who-is-fluxia-the-mystery-behind-the-worlds-most-famous-non-existent-face)
- 2026-02 / 2026-05：LMArena 快照（46→60 模型；OpenAI 1248→1393） — [LMArena](https://lmarena.ai/ar/leaderboard/text-to-image)
- 2026-05：Qwen-Image 2.0 Pro 出现在 Artificial Analysis — [Artificial Analysis](https://artificialanalysis.ai/image/explore/model/qwen-image-2-0-pro-alibaba-cloud-may-2026)
- 2026-06：GPT Image 2 以约 1338–1339 Elo 居 Artificial Analysis 榜首；Midjourney V8.1 据第三方成为默认 — [fal.ai](https://fal.ai/learn/tools/best-text-to-image-apis-2026)；[Blake Crosley](https://www.blakecrosley.com/guides/midjourney)
- 2026：FLUX.2 Klein 9B 的塑料皮肤社区修复 — [AIStudyNow](https://aistudynow.com/how-to-fix-the-plastic-skin-bug-in-flux-2-klein-9b-enhance-realism/)

### Inferences
- "AI 味"的主导形态随代际迁移：2022–2023 是手/牙/眼结构错误；2024 是 Flux 式"太完美"（塑料皮肤、裂纹下巴、永远虚化）；2025–2026 是色彩/介质签名（GPT 黄偏、缺乏噪点与镜头缺陷）与"同一张脸"。相应地，社区对策从"负面词 + 修手"转向"快照 LoRA / 胶片词 / 命名光源 / 后期加噪"。
- 2022–2024 的具体模型建议（Realistic Vision、SDXL checkpoint、Amateur Photography v6 for Flux.1）在 2026-10 仍可用但已非前沿，报告应标注"历史/本地低成本方案"。

### Gaps
- Nano Banana 初版（2025-08）、GPT Image 1（2025-04 API）、GPT Image 1.5（2025-12）、GPT Image 2（2026）与 FLUX.2 的官方发布日期与说明均未能核实。
- 2022–2023 Midjourney v4/v5 "photorealism 跃升"（常被视为 AI 照片感的转折点）未在本轮检索，缺少引证。
