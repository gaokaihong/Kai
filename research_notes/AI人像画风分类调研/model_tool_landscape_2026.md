# 2026年10月 文生图模型与工具版图（人像 / 角色艺术，非二次元）

> 调研日期：2026-10-11。调研方法说明：本轮仅能使用 WebSearch（搜索结果含页面摘录），沙箱代理对 docs.midjourney.com、recraft.ai、helpx.adobe.com、docs.ideogram.ai、freepik.com、artificialanalysis.ai、arena.ai、civitai.com 等官方域名的 CONNECT 请求一律返回 403，WebFetch/curl 无法读取原页面；且本轮共享搜索预算在第 5 轮搜索后耗尽。因此：(1) 所有"官方文档"引文均来自搜索引擎对该官方页面的摘录，而非完整页面；(2) 若干预设列表只拿到"示例"而非全集，已在 Gaps 中标明；(3) 二次元专用模型（Niji、Illustrious、NoobAI、Animagine 等）按任务要求仅一句带过：它们存在且在 anime 人像上占主导，但不在本笔记范围内。
>
> 产品名、参数名、风格预设名一律保留原文。

---

## 关键问题 1：2026年10月的旗舰模型及其最新版本 / 发布时间

### Takeaway
到 2026 年 10 月，人像文生图的"第一梯队"已从扩散模型的参数竞赛转向"统一生成+编辑、带推理（thinking）、多参考图"的多模态模型：OpenAI gpt-image-2（2026-04-21）、Google Nano Banana 2 / Gemini 3.1 Flash Image（2026-02-26 预览，2026-05-28 GA）、ByteDance Seedream 5.0 Lite/Pro（2026-02 / 2026-06~07）、Alibaba Qwen-Image-2.0（2026-02-10）、Midjourney V8.1（2026-04-30，可能已有 V8.2）、Black Forest Labs FLUX.2（2025-11-25）构成主流；开源侧由 HunyuanImage 3.0（80B MoE）、Z-Image（6B）、FLUX.2 [dev]/[klein]、以及仍然活跃的 SDXL 社区 checkpoint 支撑。

### Cited Findings

**Midjourney**
- 官方 Models 文档：V8.0 Alpha 于 2026-03-17 在 alpha.midjourney.com 上线；V8.1 于 2026-04-30 在 midjourney.com 发布，被称为"our fastest model so far"，标准任务渲染速度约为早期版本的 4–5 倍；V8.1 支持 "HD images"，可直接生成 2K 分辨率而无需 upscaling；使用 V8.1 需要先解锁 "Global V7/V8 Personalization Profile"。 — [docs.midjourney.com/docs/models](https://docs.midjourney.com/docs/models)（搜索摘录）
- 第三方博客称 Midjourney 8.2 已于 2026-07-24 成为默认模型（预览期自 2026-06-25 开始），改进点为 "bolder aesthetics, better personalization"；官方 Models 页摘录中未出现 8.2，**此条未经官方确认**。 — [VidMuse: Midjourney 8.2](https://vidmuse.ai/blog/midjourney-8-2)
- 旁证：官方 Omni Reference 帮助文章中"指向一个 V8.2 版本的文章"（搜索摘录转述），说明官方文档体系中已存在 V8.2 条目，但本轮未能读取。 — [docs.midjourney.com Omni Reference](https://docs.midjourney.com/hc/en-us/articles/36285124473997)
- 第三方指南称 V8.1 已在官方 Version 文档中取代 V7 成为默认版本（V7 仍可选），并称官方兼容表将 Omni Reference 标记为 V8.1 不支持。 — [blakecrosley.com Midjourney 8.1 Guide](https://blakecrosley.com/en/guides/midjourney)
- 部分 CometAPI 页面仍称 V8 未发布、默认仍是 V7，属过期信息。 — [cometapi.com](https://www.cometapi.com/what-is-midjourney-v8-when-will-it-be-released/)

**Black Forest Labs / FLUX**
- FLUX.2 系列于 2025-11-25 发布（Wikipedia 列为 stable release）；变体为 Pro、Flex、Dev、Klein；许可：Schnell 与 Klein 为 Apache，Dev 为非商业，Pro/Flex 为专有。 — [Wikipedia: Flux (text-to-image model)](https://en.wikipedia.org/wiki/Flux_(text-to-image_model))
- 日本媒体报道：FLUX.2 可生成/编辑最高 4 megapixel 图像，改进排版/信息图文字渲染，可同时参考最多 10 张图并保持构图与细节；FLUX.2 把 FLUX.1 的生成与 FLUX.1 Kontext 的编辑合并为一个模型；2025-12-17 更新发布了更高质量的 FLUX.2 [max]。 — [design-offset.com 2025-11-25](https://design-offset.com/20251125-black-forest-labs-flux-2-image-model/)
- 另一词条称 FLUX 2 沿用 Pro/Dev/Schnell 结构，与 Wikipedia 不一致，可信度较低。 — [morphic.com FLUX 2](https://morphic.com/ai-glossary/FLUX-2)
- 社区已出现基于 "Flux 2 Klein 9B" 的 ComfyUI 换脸工作流。 — [aistudynow.com](https://aistudynow.com/how-i-fixed-face-swaps-the-ultimate-flux-2-klein-9b-comfyui-workflow/)

**Google（Imagen / Gemini image / Nano Banana）**
- Imagen 4 于 2025-06-24（PureAI 2025-06-25 报道"on Tuesday"）通过 Gemini API 与 Google AI Studio 发布；Imagen 4 Ultra 面向更精确的 prompt adherence，定价 $0.06/图。 — [PureAI](https://pureai.com/Articles/2025/06/25/Google-Launches-Imagen-4.aspx)
- Nano Banana 原版 = Gemini 2.5 Flash Image，2025 年 8 月发布。Nano Banana Pro = Gemini 3 Pro Image，2025-11-20 发布，模型 ID `gemini-3-pro-image-preview`；支持 2K/4K 输出、最多 14 张参考图、最多 5 人角色一致性、Search grounding。 — [iThome](https://www.ithome.com.tw/news/172380); [marigold.cz](https://www.marigold.cz/tech-news/2025-11-21/nano-banana-pro-launches-as-gemini-3-pro-image-mod)
- Nano Banana 2 = Gemini 3.1 Flash Image，2026-02-26 以预览发布，"Pro quality at Flash speeds"，在 Gemini 应用中取代 Nano Banana Pro；Google Cloud 文档列出 GA 日期 2026-05-28；输出 512/1K/2K，4K 仍为预览；独有 video-to-image 输入；支持 Google Image Search grounding。 — [Neowin](https://www.neowin.net/news/google-launches-nano-banana-2-pro-quality-at-flash-speeds/); [Google Cloud docs](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/models/gemini/3-1-flash-image?authuser=2); [Vercel AI Gateway](https://vercel.com/ai-gateway/models/gemini-3.1-flash-image/about)

**OpenAI（GPT Image）**
- GPT Image 1.5 于 2025-12-16 发布，比 gpt-image-1 快 4 倍、单图便宜约 20%；通过 API 和 ChatGPT 提供。 — [datanorth.ai](https://datanorth.ai/news/openai-gpt-image-1-5-released); [PCWorld](https://www.pcworld.com/article/3014153/openai-launches-gpt-image-1-5-with-faster-generation-and-smarter-edits.html); [apiyi docs](https://docs.apiyi.com/en/news/gpt-image-1-5-launch)
- ChatGPT Images 2.0 / `gpt-image-2` 于 2026-04-21 发布，覆盖 ChatGPT、Codex 与 API；核心特性是生成前的 reasoning（规划构图、核对数量与约束）；最高 2K 输出，宽高比 3:1 到 1:3，单次最多 8 张；显著改善密集文字与非拉丁文字；Thinking 模式限 Plus/Pro/Business；DALL·E 2 与 DALL·E 3 于 5 月 12 日退役。 — [Thurrott](https://thurrott.com/a-i/openai-a-i/335196/openai-announces-chatgpt-images-2-0); [neurohive](https://neurohive.io/en/news/chatgpt-images-2-0-openai-launches-image-generation-model-with-reasoning-2k-resolution-and-multilingual-text/); [designcompass](https://designcompass.org/en/2026/04/22/chatgpt-image-2-0-public/)
- API 定价存在冲突：一说 1024×1024 high 约 $0.21/图，一说 $30/M output tokens（对比 gpt-image-1.5 的 $32/M）。 — 同上 neurohive / designcompass
- 一篇 Dreamina（字节）文章提到 "ChatGPT Images 2.5"，**未在其他来源得到确认**。 — [dreamina.capcut.com](https://dreamina.capcut.com/ai-model/best-ai-image-generation-models-2026-comparison)

**ByteDance Seedream / 即梦 (Dreamina)**
- Seedream 4.0 模型快照日期为 2025-08-28（非 9 月），提供 4K 输出，现处维护状态；Seedream 4.5 为 4.x 系列最后一版。 — [apiyi historical versions](https://docs.apiyi.com/en/api-capabilities/seedream-image/historical-versions.md); [moda.app](https://moda.app/resources/models/seedream)
- Seedream 5.0 Lite 于 2026-02-13 发布，为首个"先推理再渲染"且可用实时联网搜索做 grounding 的 Seedream；编辑可合并最多 14 张参考图；直出 2K，AI 增强到 4K。 — [mindstudio.ai](https://www.mindstudio.ai/models/seedream-v5-0-lite); [howaiworks.ai](https://howaiworks.ai/models/seedream); [Newsquawk](https://www.newsquawk.com/headlines/-bytedance-launches-seedream-50-lite-image-generation-model-which-is-first-with-online-search-capability)
- Seedream 5.0 Pro 发布日期三说并存：2026-06-23 火山引擎 FORCE 大会（36kr）、2026-06-28（apiyi 按模型 ID 推断）、2026-07-08（CapCut 官方资源页）。功能：点选/套索局部精修、图层分离、密集信息图、14 种语言原生文字、最多 10 张参考图；渠道为 CapCut/即梦(Dreamina)、Volcengine Ark、BytePlus ModelArk。 — [36kr](https://eu.36kr.com/en/p/3677025348395653); [CapCut](https://www.capcut.com/resource/seedream-5-0-pro-key-features-explained); [atlascloud](https://www.atlascloud.ai/pt/blog/guides/seedream-4.5-to-5.0-pro-upgrade)

**Tencent HunyuanImage**
- HunyuanImage 3.0 于 2025 年 9 月底开源（9/25 与 9/28 两说）；80B 参数、13B 激活、MoE 64 专家；可解析超过 1000 字符的指令并渲染长文本；本地部署建议 4×80GB GPU、权重约 170GB。 — [comfyui-wiki](https://comfyui-wiki.com/en/news/2025-09-27-tencent-open-source-hunyuan-image-3-0); [TechNode](https://technode.com/2025/09/28/tencent-open-sources-hunyuanimage-3-0-an-80b-multimodal-image-generation-model/); [immers.cloud](https://en.immers.cloud/ai/tencent/HunyuanImage-3.0/)
- HunyuanImage-3.0-Instruct 于 2026-01-26 发布，加入推理、图生图编辑、多图融合、提示词自改写。 — [lmlearning.cn](https://www.lmlearning.cn/ai-models/pretrained-models/tencent-hunyuanimage-3-0-instruct); [jimmysong.io](https://jimmysong.io/ai/hunyuanimage-3-0)

**Alibaba Qwen-Image / 通义万相 / Z-Image**
- Qwen-Image-2.0 于 2026-02-10 发布，生成与编辑统一于单一模型；原生 2K；可接受最长约 1000 token 的指令（PPT/海报场景）；API 于 2026-03-03 在 Alibaba Cloud Model Studio 上线；发布时权重未开源；架构说法冲突（8B Qwen3-VL 编码器 + 7B 扩散解码器 vs. 单一 7B）；Pro 版有 2026-04 与 2026-06 快照。 — [Analytics Vidhya](https://www.analyticsvidhya.com/blog/2026/02/qwen-image-2-0-is-here/); [alternativeto](https://alternativeto.net/news/2026/2/alibaba-launches-qwen-image-2-0-with-improved-typography-rendering-and-lighter-architecture); [llmreference](https://www.llmreference.com/model/qwen-image-2.0-pro)
- Artificial Analysis 收录条目 "qwen-image-2-0-pro-alibaba-cloud-may-2026"。 — [artificialanalysis.ai](https://artificialanalysis.ai/image/explore/model/qwen-image-2-0-pro-alibaba-cloud-may-2026)
- Z-Image（Tongyi-MAI，阿里）：6B 参数 S3-DiT，Apache-2.0。Z-Image-Turbo 2025-11 发布，8 步蒸馏、H800 亚秒级、约 16GB VRAM 可跑，以写实与中英双语文字见长，曾列 Artificial Analysis 开源模型第一；Z-Image-Base（非蒸馏）2026-01-27/28 发布，28–50 步 + CFG，支持 LoRA 训练与负向提示；Z-Image-Edit 与 Z-Image-Omni-Base 截至来源成文仍未发布；"Turbo V2" 仅 invideo 一处提及，未证实。 — [NYU Shanghai RITS](https://rits.shanghai.nyu.edu/ai/z-image-alibabas-efficient-6b-open-source-image-generation-model/); [comfyui-wiki Z-Image-Base](https://comfyui-wiki.com/en/news/2026-01-28-alibaba-z-image-base-release); [comfyui-wiki Z-Image family](https://comfyui-wiki.com/en/models/z-image); [GIGAZINE](https://gigazine.net/gsc_news/en/20260128-z-image-image-generation-ai/); [invideo](https://invideo.io/blog/z-image-ai-image-generator/)

**Kuaishou Kling / Kolors**
- KOLORS 2.0 图像模型与 KLING 2.0 于 2025-04-15 北京发布会一同全球发布；宣称 prompt adherence 显著提升、"cinematic aesthetic expression" 增强、支持 "over 60 stylizations"；具备局部重绘、扩图、修复、元素修改与 style transfer；Kling 2.1 于 2025-05 底发布。"排名行业第一"为快手内部评测。 — [VentureBeat/BusinessWire](https://venturebeat.com/business/from-vision-to-screen-how-kling-ai-2-0-ushers-in-new-era-of-content-creation); [Plivo](https://www.plivo.com/blog/exploring-kling-ai-2-0-innovations-and-challenges-in-video-and-image-modeling)

**Ideogram**
- Ideogram 3.0 的风格选项为 Auto / General / Realistic / Design（见关键问题 2）；Ideogram 2.0 曾有 Anime 与 3D 风格。 — [docs.ideogram.ai style](https://docs.ideogram.ai/using-ideogram/generation-settings/style); [docs.ideogram.ai styles in older models](https://docs.ideogram.ai/using-ideogram/features-and-tools/reference-features/style-reference/styles-in-older-models)
- 2025 年法语媒体将 Ideogram 3.0 与 ChatGPT、Midjourney、Reve 对比评测。 — [blogdumoderateur](https://www.blogdumoderateur.com/ia-ideogram-3-0-face-a-chatgpt-midjourney-reve/)

**Recraft**
- Recraft V4 于 2026 年 2 月发布，V4.1 于 2026-05-14 发布（博文标题 "more beautiful by nature"）；官方文档称 V4 比 V4.1 "more opinionated"、更偏风格化；官方宣传 "photorealism that actually looks real"；vector 变体输出可编辑 SVG；Comfy 文档称输出 2048×2048。 — [recraft.ai blog V4.1](https://recraft.ai/blog/recraft-v4-1-more-beautiful-by-nature); [recraft.ai docs V4.1](https://www.recraft.ai/docs/recraft-models/recraft-v4-1.md); [docs.comfy.org recraft-v4](https://docs.comfy.org/tutorials/partner-nodes/recraft/recraft-v4); [Scenario help](https://help.scenario.com/articles/2892961047-recraft-v4-suite-the-essentials)
- Artificial Analysis 收录 "Recraft V4.1 Utility Pro"。 — [artificialanalysis.ai](https://artificialanalysis.ai/image/explore/model/wan_wan-2-6)

**Adobe Firefly**
- Firefly Image Model 5 于 2025-10-28 发布：支持图层（layered editing）、自定义模型（custom models）、原生最高 4 megapixel；自定义风格模型先为公测/封测，后开放全部用户，宣称可保持 line weight、color palette、lighting、character features 一致；Firefly 现捆绑约 30 个 AI 模型（含合作方模型）；2026-03-19 Adobe 官方博客再次扩展图像/视频能力与自定义模型。 — [TechCrunch](https://techcrunch.com/2025/10/28/adobe-firefly-image-5-brings-support-for-layers-will-let-creators-make-custom-models/); [The Decoder](https://the-decoder.com/adobe-firefly-now-bundles-30-ai-models-and-lets-users-train-custom-styles-on-their-own-images/); [Adobe Blog 2026-03-19](https://blog.adobe.com/en/publish/2026/03/19/adobe-firefly-expands-video-image-creation-with-new-ai-capabilities-custom-models); [nocode.mba tracker](https://www.nocode.mba/ai-release-tracker/providers/adobe)

**Leonardo.ai / Canva**
- Leonardo 自研模型为 Lucid Origin（ID `7b592283-e8a7-4c5a-9ba6-d18c31f258b9`）与 Leonardo Phoenix 1.0（ID `de7d3faf-762f-48e0-b3b7-9d0ac3a3fcf3`）；Style UUID 仅兼容 Flux、Lucid Origin/Realism 与 Phoenix 模型，SDXL 模型使用另一套 preset。 — [docs.leonardo.ai legacy-generation](https://docs.leonardo.ai/docs/legacy-generation); [docs.leonardo.ai Lucid Origin](https://docs.leonardo.ai/docs/lucid-origin); [leonardo.ai news](https://leonardo.ai/news/ai-image-models/)
- Canva Dream Lab 基于 Leonardo.Ai（Phoenix 模型）；Magic Media 为 Canva 原生工具。 — [ITdaily](https://itdaily.com/news/software/canva-introduceert-leonardo-ai); [pasqualepillitteri.it](https://pasqualepillitteri.it/en/news/601/canva-ai-magic-studio-guide)

**Krea**
- Krea 1 为 Krea 自研模型，面向消除常见的 "AI look"（soft textures、flat repetitive compositions）；最强于 "artistic photorealism"（stylized photography、editorial）；支持最多 3 张参考图 + style weight 滑杆；支持 LoRA 自定义风格；原生 1.5K、可放大到 4K；文档中未见发布日期。 — [docs.krea.ai Krea 1](https://docs.krea.ai/features/krea-1); [hunted.space](https://hunted.space/product/krea-1)

**Freepik Mystic（现 Magnific）**
- Freepik 文档列出 Mystic 1.0、Mystic 2.5、Mystic 2.5 Flexible、Mystic 2.5 Fluid 四版（1.0 高质量/细节纹理，2.5 最通用，2.5 Flexible 最佳 prompt adherence，2.5 Fluid 更快）；Freepik 已品牌更名为 Magnific（"Freepik is now Magnific"）。 — [freepik.com image-ai-models](https://www.freepik.com/ai/docs/image-ai-models); [magnific.com custom-styles](https://www.magnific.com/ai/custom-styles)

**Luma Photon / HiDream / Reve / Playground**
- Luma Photon 于 2024-11-25 随 Dream Machine 发布，基于 Luma "Universal Transformer"，自称比同类快/便宜 800%；Segmind 称其在 "Instruction Following" 与 "Composition" 偏好评分最高（厂商口径）；第三方平台定价 $0.015/图。 — [BusinessWire](https://www.businesswire.com/news/home/20241125632294/en/People-Can-Show-the-World-What-They-See-With-Launch-of-New-Luma-AI-Dream-Machine-Service); [Segmind](https://www.segmind.com/models/luma-photon-txt-2-img); [atlascloud](https://www.atlascloud.ai/zh/models/luma/photon)
- HiDream-I1 为 17B 参数开源基础模型，fal 的 dev 端点 $0.03/MP。 — [fal.ai](https://fal.ai/models/fal-ai/hidream-i1-dev/playground)
- Reve 出现在 arena.ai 文生图榜 Top 14 厂商名单中（2026-05）。 — [arena.ai](https://arena.ai/leaderboard/text-to-image)

**Stable Diffusion 生态（本地）**
- 2026 年本地写实仍以 SDXL 为默认：Juggernaut XL 被反复列为第一写实 checkpoint（"Juggernaut XL Ragnarok" 2026-02 更新；"Juggernaut XL v10" 被称 photorealistic SDXL 金标准），RealVisXL V4.0 为亚军；Juggernaut 长期居 Civitai 下载榜前列。 — [insiderllm](https://insiderllm.com/guides/best-photorealism-checkpoints-local-image-generation/); [promptzone](https://www.promptzone.com/tara_suzuki/best-sdxl-models-in-2026-realistic-anime-and-all-purpose-checkpoints-116)
- 一篇博客称 Civitai 上 Flux 2 的 "portrait finetunes" 是最拥挤的子类。 — [picassoia blog](https://blog.picassoia.com/best-flux-2-checkpoints-and-models-on-civitai)
- 2026-05 Reddit 讨论认为 Z-Image 与 Klein 需要微调者"从零教起"，SDXL 在某些写实场景仍更好（单一观点）。 — [Reddit snapshot](https://reddit.sentinel-team.org/posts/1t71cs5/snapshots/2026-05-08T22%3A29%3A22.49338Z)

### Inferences
- 2026 年人像生成的"旗舰"标准已包含：原生 2K+、多参考图（10–14 张）、角色一致性、推理式提示理解、生成/编辑一体；纯文生图扩散模型（SDXL、FLUX.1）转为本地/可微调层。
- 中国厂商（字节 Seedream、阿里 Qwen-Image/Z-Image、腾讯 Hunyuan）在 2025Q3–2026Q2 密集发布，开源权重（HunyuanImage 3.0、Z-Image）填补了 FLUX.1 之后的开源空档。
- Midjourney 走的是"个性化配置 + 风格参考"路线（V8.1 强制解锁 Personalization Profile），而非多模态推理路线。

### Gaps
- 未能读取 docs.midjourney.com 原页，V8.2 存在与否、默认模型是否为 V8.1/V8.2、`--sref`/`--oref`/`--p` 在 V8 的兼容表均未官方确认。
- Ideogram 3.0 的发布日期（据训练知识为 2025-03-26）未在本轮搜索结果中出现，标为未验证。
- Stable Diffusion 3.5 及 Stability AI 2026 年新模型状态：本轮无结果（搜索预算耗尽）。
- Reve Image、Playground v3 的版本与日期：搜索无相关结果。
- Seedream 5.0 Pro 的官方发布日（seed.bytedance.com）未能读取；三方日期冲突已列出。
- Kling/Kolors 2026 年是否有新图像模型：未找到 2025-05 之后的信息。
- 即梦（国内版）当前模型版本（3.0 / 3.5 / Seedream 5.0）说法不一，未能核实。

---

## 关键问题 2：各产品官方 UI / 文档中的风格预设分类（原文）

### Takeaway
行业自身对"风格"的分类并不统一，但可归纳为四种主导逻辑：(a) **按输出管线/媒介大类**（Recraft 的 realistic image / digital illustration / vector illustration；Ideogram 的 Realistic / General / Design；Firefly 的 Content type）；(b) **按摄影子体裁**（Recraft realistic 子风格 studio_portrait、hard_flash、hdr；Leonardo 的 Bokeh / Cinematic / Portrait / Stock Photo）；(c) **按技法 / 材料 / 艺术运动 / 主题的多轴标签**（Adobe Firefly 的 Popular / Techniques / Movements / Effects / Concepts / Themes / Materials）；(d) **中文工具按"媒介 + 文化 + 写实度"平铺**（通义万相：素描、水彩、油画、中国风、二次元、3D卡通、扁平插画、摄影、人像写真）。

### Cited Findings

**Adobe Firefly（Styles / Effects 面板）**
- Adobe 帮助页列出七个风格分类：**Popular, Techniques, Movements, Effects, Concepts, Themes, Materials**；Effects 区还包含 color and tone、lighting、camera angle 设置。 — [helpx.adobe.com effects-for-generated-images](https://helpx.adobe.com/firefly/web/work-with-images/generate-images/effects-for-generated-images.html)
- 各类示例预设（官方页面摘录，非全集）：Movements → Art deco, Art nouveau, Baroque；Themes → 3d, Anime, Cartoon；Techniques → Acrylic paint, Bold lines, Doodle drawing；Effects → Antique photo, Bokeh effect, Bioluminescence；Materials → 3d patterns, Charcoal, Claymation；Popular → Minimalism, Scandinavian, Flat design；Concepts → Bohemian, Chaotic, Dais, Electric。 — [helpx.adobe.com mobile set-effects](https://helpx.adobe.com/firefly/mobile/generate-images-with-text-to-image/customize-generated-images/set-effects-for-image-generation.html)
- 移动端帮助页注明这些扩展风格组件 "only available for Adobe's native image models"，合作方模型（Firefly 内置的第三方模型）不支持。 — 同上
- Adobe 社区指南对 Image 5 的建议：先写 expression、lighting、mood，再加 lens type、depth、framing 以增强写实。 — [community.adobe.com firefly image guide](https://community.adobe.com/p/firefly-image-guide)

**Recraft（style 树）**
- 顶层风格：realistic image / digital illustration / vector illustration（Recraft 文档与 ComfyUI 伙伴节点 RecraftStyleV3RealisticImage / RecraftStyleV3DigitalIllustration / RecraftStyleV3VectorIllustration 对应）。 — [docs.comfy.org RecraftStyleV3DigitalIllustration](https://docs.comfy.org/built-in-nodes/RecraftStyleV3DigitalIllustration.md); [docs.comfy.org RecraftStyleV3VectorIllustrationNode](https://docs.comfy.org/ja/built-in-nodes/RecraftStyleV3VectorIllustrationNode)
- 已确认的子风格 ID（写法为 `顶层/子风格`）：`realistic_image/hard_flash`（"harsh, direct lighting"）、`realistic_image/studio_portrait`（"professional studio-style portrait images"）；digital_illustration 下含 `hand_drawn`、`grain`、`pixel_art`（"retro-style pixelated images"）、`2d_art_poster`、`bold_fantasy`、`child_book`、`digital_engraving`、`expressionism`、`modern_folk`、`pop_art`、`street_art` "and many more"。 — [intercom.help/scadepro recraft](https://intercom.help/scadepro/en/articles/10717846-recraft); [runcomfy Recraft Style - Digital Illustration](https://www.runcomfy.com/comfyui-nodes/ComfyUI/recraft-style-v3-digital-illustration)
- Recraft 提供 "Recraft Create Style" 节点/功能：上传参考图创建自定义风格。 — [runcomfy Recraft Create Style](https://www.runcomfy.com/comfyui-nodes/ComfyUI/recraft-create-style-node)
- Recraft 官方博文以"同一角色的不同艺术风格"演示其风格体系。 — [recraft.ai blog character-in-different-art-styles](https://www.recraft.ai/blog/character-in-different-art-styles)

**Ideogram（Style 设置）**
- Ideogram 3.0 官方风格为 **Auto, General, Realistic, Design**："Auto lets the AI decide which style—General, Realistic, or Design—to apply"；General："A versatile style that can handle just about anything, ideal for artistic works like abstract paintings, pencil sketches, digitally manipulated images, and more"；Realistic："Best used when aiming for lifelike, photographic images, with an emphasis on realism and detail"；Design："Suited to logos, print-on-demand products, promotional materials, flyers, menus, and graphic design work"。 — [docs.ideogram.ai style](https://docs.ideogram.ai/using-ideogram/generation-settings/style)
- 旧版（2.0）风格列表含 Anime 与 3D（已在 3.0 中并入）；Ideogram 文档中有 "Style Reference" 功能页。 — [docs.ideogram.ai styles-in-older-models](https://docs.ideogram.ai/using-ideogram/features-and-tools/reference-features/style-reference/styles-in-older-models)
- "Fiction" 并非 Ideogram 3.0 风格，而是 Scenario 第三方 API 中的 character style 类型（Auto / Realistic / Fiction）。 — [docs.scenario.com](https://docs.scenario.com/docs/third-party-model-generation-ideogram)

**Leonardo.ai（preset styles）**
- Lucid Origin（v1 API）preset 表含 **Bokeh, Cinematic, Cinematic Close-Up, Creative, Dynamic, Fashion, Film** 等；Lucid Origin（v2 API）为较短列表：**Cinematic, Creative, Dynamic, Fashion, None, Portrait, Stock Photo, Vibrant**。两表不一致，取决于 API 版本。 — [docs.leonardo.ai Lucid Origin](https://docs.leonardo.ai/docs/lucid-origin); [docs.leonardo.ai v1.0 lucid-origin](https://docs.leonardo.ai/v1.0/docs/lucid-origin)
- Phoenix 1.0 页面有 "List of Style UUIDs" 标题，但表格未进入搜索摘录。 — [docs.leonardo.ai phoenix](https://docs.leonardo.ai/v1.0/docs/phoenix)

**Freepik（Style 标签页）**
- 官方 style 文档："the Style tab shows a list of predefined styles ready to use"，但摘录未列名称；第三方目录列出 Photo, Digital Art, Painting, 3D, Anime 等（疑为部分）。 — [freepik.com/ai/docs/style](https://www.freepik.com/ai/docs/style); [tooljunction](https://www.tooljunction.io/ai-tools/freepik-ai-image-generator)
- 自定义风格（Custom Styles）：可由 prompt、单张参考图或一组图片构建，可公开分享；FAQ 称其为基于 LoRA、约 10–50 张图训练。 — [freepik.com FAQ styles](https://www.freepik.com/ai/faq/freepik-styles-and-custom-styles); [magnific.com custom-styles](https://www.magnific.com/ai/custom-styles)

**Canva（Dream Lab / Magic Media）**
- Canva 官方 AI art generator 页面提及 Magic Media 预设 **Watercolor, Filmic, Neon, Color Pencil, Retrowave**。 — [canva.com/ai-art-generator](https://canva.com/ai-art-generator)
- 2026 年第三方指南称 Magic Media 有 25 种风格，含 Filmic, Dreamy, Concept Art, Retrowave, Anime, Photography；Dream Lab 发布时报道为"十五种以上"，含 3D renderings 与 illustrations。 — [pasqualepillitteri.it](https://pasqualepillitteri.it/en/news/601/canva-ai-magic-studio-guide); [mac4ever](https://www.mac4ever.com/divers/184888-canva-devoile-dream-lab-un-nouvel-outil-ia-de-generation-d-images)
- Dream Lab 实测文章列出 Cinematic, Creative, Bokeh, Illustration，另一文补充 3D Render, Moody（与 Leonardo preset 命名高度重合，符合其基于 Leonardo Phoenix 的事实）。 — [paul-r-evans newsletter](https://paul-r-evans-newsletter.beehiiv.com/p/it-s-a-dream-using-dream-lab); [pxz.ai](https://pxz.ai/blog/canva-ai-image-generator-guide)

**Microsoft Designer / Bing Image Creator**
- 未找到官方穷举的风格列表；Bing 官方建议的提示公式为 "Adjective + Noun + Verb + Style"；Designer 对已生成图片提供 "style filters"（未列名）；一份 2023 博客自行测试了 acrylic、anime、comic book、pixel art、pop art、watercolor 等关键词（DALL·E 2/3 时代）。 — [create.microsoft.com](https://create.microsoft.com/ar-sa/learn/articles/things-you-can-do-with-designer-and-image-creator); [habrador blog](https://blog.habrador.com/2023/04/bing-image-creator-ai-art-styles-materials.html); [office-watch](https://office-watch.com/2023/bing-image-creation-better-results/)
- 第三方目录称其现运行于 DALL-E 3 与 GPT-4o 等多模型。 — [neura.market](https://neura.market/ai-tools-directory/image-generators/bing-image-creator)

**Krea**
- Krea 1 文档未给出命名预设；风格控制靠参考图（最多 3 张）+ style weight 滑杆 + LoRA。 — [docs.krea.ai](https://docs.krea.ai/features/krea-1)

**Midjourney（官方风格词汇）**
- Midjourney 没有命名式风格预设，官方"风格词汇"是参数：`--stylize`（默认 100，范围 0–1000，控制"内置审美偏好"的强度）、`--style raw`（减弱默认审美）、`--sref`（Style Reference，`--sw` 0–1000 默认 100）、`--oref`（Omni Reference）、Personalization（`--p`，V8.1 必须解锁 Global V7/V8 Personalization Profile）、Moodboards。 — [aituts stylize](https://aituts.com/midjourney-stylize-command/); [nerdschalk --style](https://nerdschalk.com/how-to-use-the-style-parameter-to-fine-tune-images-generated-on-midjourney/); [CometAPI --sw](https://www.cometapi.com/?p=25326); [docs.midjourney.com Omni Reference](https://docs.midjourney.com/hc/en-us/articles/36285124473997); [docs.midjourney.com models](https://docs.midjourney.com/docs/models)

**即梦 AI（字节，国内版 Dreamina）**
- 评测页称即梦支持 **写实、3D 卡通、插画、数字艺术** 等风格；另一教程列出 **写实、二次元、水墨、油画、赛博朋克**，并可选"无"让 AI 自由发挥；操作流程为选文生图 → 输入提示词 → 选择风格与画幅。 — [aitoollab.cn 即梦](https://www.aitoollab.cn/tools/jimeng-ai/index.html); [tixiaolu.com](https://www.tixiaolu.com/v2/posts/v2-6be4eedb.html)
- SEO 向教程称即梦 3.0（2026-03）提供 "50+ 预设视觉风格"/"53 种官方风格"，可信度低。 — [tixiaolu.com](https://www.tixiaolu.com/v2/posts/v2-e787fbc4.html)
- 可调"图片精细度（1–50）"等参数。 — [thepaper.cn](https://www.thepaper.cn/newsDetail_forward_27327564)

**通义万相（阿里云百炼官方文档）**
- 官方文档："支持多种风格，包括但不限于**素描、水彩、油画、中国风、二次元、3D卡通、扁平插画、摄影以及人像写真**图像等"，并支持自定义修饰词与**参考图风格迁移**。 — [help.aliyun.com text-to-image](https://help.aliyun.com/zh/model-studio/user-guide/text-to-image)
- 2023 年上线时界面提供 8 个画面风格（含默认）：水彩、油画、中国画、扁平插画、二次元、素描、3D卡通。 — [cs.com.cn](https://cs.com.cn/ssgs/gsxw/202307/t20230707_6354638.html); [developer.aliyun.com](https://developer.aliyun.com/article/1276905)
- 2026 年 tixiaolu 博客提到 "写实""水墨""4K" 与"万相-3.0"，内容前后矛盾，无官方来源。 — [tixiaolu.com](https://www.tixiaolu.com/v2/posts/v2-fb372e1e.html)

**Kuaishou Kolors 2.0**
- 官方口径 "support for over 60 stylizations"，未列具体名称。 — [VentureBeat/BusinessWire](https://venturebeat.com/business/from-vision-to-screen-how-kling-ai-2-0-ushers-in-new-era-of-content-creation)

### Inferences
- **分类轴的归纳**：
  - 按**渲染管线 / 输出类型**：Recraft（raster realistic vs. digital illustration vs. vector SVG）、Ideogram（Realistic vs. Design，General 兜底）、Firefly Themes 中的 3d / Anime / Cartoon。
  - 按**写实度**：几乎所有产品都把 "Realistic / Photo / 写实 / 摄影 / 人像写真" 单列为一档，作为与"艺术/插画"的二元对立。
  - 按**摄影子体裁**（人像最相关）：Recraft realistic 子风格（studio_portrait、hard_flash、hdr 等）、Leonardo（Bokeh、Cinematic、Cinematic Close-Up、Portrait、Stock Photo、Fashion、Film）、Firefly Effects（Bokeh effect、Antique photo）。这实际上是把"人像摄影师的用光/镜头术语"产品化。
  - 按**技法与材料**：Firefly Techniques（Acrylic paint、Doodle drawing）、Materials（Charcoal、Claymation）；Recraft digital_illustration 子风格（hand_drawn、grain、pixel_art、digital_engraving）；中文工具的素描/水彩/油画/水墨。
  - 按**艺术运动**：仅 Firefly Movements（Art deco、Art nouveau、Baroque）与 Recraft 的 expressionism、pop_art 等显式使用。
  - 按**文化语境**：中文产品独有 "中国风/中国画/水墨/国风" 一类。
- Midjourney 与 Krea 代表另一条路线：**不给命名预设**，用连续参数（--stylize）、参考图（--sref、style weight）与个性化画像（--p）取代离散分类。
- Firefly 的"扩展风格仅对 Adobe 原生模型可用"说明：命名预设本质上是厂商对自家模型做的提示词模板/条件注入，难以跨模型迁移。

### Gaps
- 未能获取 Firefly Styles 面板的**完整**预设名单及 "Content type: Art / Photo" 开关的官方描述（页面被代理拦截，仅有示例）。
- Recraft realistic_image 与 vector_illustration 的完整子风格列表未获取；`linocut` 等是否存在未确认。
- Leonardo Phoenix 的 preset style 全表未获取。
- Freepik Style 标签页的官方预设名未获取。
- Canva Dream Lab / Magic Media 的官方完整列表未获取；仅有官方页面 5 个名称 + 第三方补充。
- Microsoft Designer / Bing Image Creator 无官方列表（可能确实不存在穷举列表）。
- 即梦当前 UI 的完整风格列表未获取（仅第三方转述）；Kolors 2.0 的 60+ 风格名单未公开。

---

## 关键问题 3：哪些模型在各类人像风格上被公认最强（含榜单）

### Takeaway
2026 年中的两大盲测榜（Artificial Analysis、LMArena/arena.ai）均由 OpenAI gpt-image-2 领跑，Google Nano Banana 2 / Nano Banana Pro 紧随；但针对"人像写实"这一细分，评测文章意见分裂于 Nano Banana 2、FLUX.2、Imagen 4 Ultra 与 Midjourney/Flux Pro 之间；"3D/Pixar 风"与"绘画/插画风人像"缺乏公认榜单，主要靠 Recraft digital illustration、Firefly 预设、以及 SDXL/Flux 社区 LoRA。

### Cited Findings

**Artificial Analysis Text-to-Image Arena**
- 2026-06 快照：GPT Image 2 (high) 以 Elo 1338 居首（fal.ai 版本写 1,339），领先第二名约 64 分；Nano Banana 2 为 1,260，Nano Banana Pro 为 1,219。 — [fal.ai best text-to-image APIs 2026](https://fal.ai/learn/tools/best-text-to-image-apis-2026); [techsy.io](https://techsy.io/en/blog/best-ai-image-models)
- 榜单页面收录 GPT Image 1.5 (high)、Riverflow 2.0、Recraft V4.1 Utility Pro、Wan 2.6、Qwen-Image 2.0 Pro（2026-05）等条目。 — [artificialanalysis.ai wan-2-6](https://artificialanalysis.ai/image/explore/model/wan_wan-2-6); [artificialanalysis.ai qwen-image-2-0-pro](https://artificialanalysis.ai/image/explore/model/qwen-image-2-0-pro-alibaba-cloud-may-2026)
- Z-Image-Turbo 于 2025-11 发布时居该榜开源模型第一。 — [NYU Shanghai RITS](https://rits.shanghai.nyu.edu/ai/z-image-alibabas-efficient-6b-open-source-image-generation-model/)

**LMArena / arena.ai Text-to-Image Arena**
- 2026-05-12 快照：#1 OpenAI 1393±7；#2 Google 1268；#3 Google 1242；#4 OpenAI 1241；#6 xAI 1223；Luma AI、Microsoft AI、Alibaba、Reve 进入 Top 14；累计 5,169,154 票、60 个模型。2026-02 快照 OpenAI 1249、Google 1239。 — [arena.ai text-to-image](https://arena.ai/leaderboard/text-to-image); [lmarena.ai](https://lmarena.ai/ar/leaderboard/text-to-image)
- arena.ai 提供分类榜：Photorealistic & Cinematic Imagery、3D Modeling 等（本轮未能读取分类榜内容）。 — [arena.ai photorealistic](https://arena.ai/leaderboard/text-to-image/photorealistic); [arena.ai 3d-modeling](https://arena.ai/leaderboard/text-to-image/3d-modeling)
- DataLearner 镜像显示不同榜首（Seedream 4 2K，1,140，2026-05-22），与 arena.ai 快照冲突，无法调和。 — [datalearner](https://www.datalearner.com/en/leaderboards/external/text-to-image)
- HunyuanImage 3.0 发布时第三方称其在"主要公开榜单"超越 Nano Banana 居首；另一来源称其在 LMArena image-edit 榜列第 6。 — [TechNode](https://technode.com/2025/09/28/tencent-open-sources-hunyuanimage-3-0-an-80b-multimodal-image-generation-model/); [gaga.art](https://gaga.art/blog/?p=1792)

**写实人像（photoreal）评测意见**
- Atlas Cloud：Imagen 4 Ultra 是 "the most photorealistic output of any publicly available image generation API in 2026"，同时也是最贵、最慢之一。 — [atlascloud](https://www.atlascloud.ai/blog/best-ai-image-generation-models-2026)
- Cliprise 实测：Flux 2 在 photorealism（含人像）"wins this category by a meaningful margin in 2026"；Nano Banana 2 领先于文字渲染、编辑与角色一致性。 — [cliprise](https://www.cliprise.app/learn/comparisons/models/nano-banana-2-vs-imagen-4-vs-flux-2-image-model-comparison-2026)
- Motionbox（2026-03-04）：Nano Banana 2 为 "our top pick for photorealistic portraits and character generation"。 — [motionbox](https://motionbox.io/blog/best-ai-image-generators-2026)
- Dreamina（字节自家）：Midjourney v6–v7 与 Flux Pro 被广泛认为在 faces、skin texture、lighting 上最写实。 — [dreamina.capcut.com](https://dreamina.capcut.com/ai-image/best-ai-image-generators-realistic-portraits-2026)
- Krea 1 定位 "artistic photorealism"（stylized photography、editorial looks；"dreamy, grainy B&W, or clean studio shots"）。 — [docs.krea.ai](https://docs.krea.ai/features/krea-1)
- Recraft V4 官方宣传 "photorealism that actually looks real"；Scenario 称 V4 raster 面向 "rich textures, complex lighting, and photographic realism"。 — [recraft.ai docs](https://www.recraft.ai/docs/recraft-models/introduction); [Scenario](https://help.scenario.com/articles/2892961047-recraft-v4-suite-the-essentials)
- Freepik Mystic 1.0 面向人像与细节纹理（文档口径）。 — [freepik.com image-ai-models](https://www.freepik.com/ai/docs/image-ai-models)
- 本地写实：Juggernaut XL（v10 / Ragnarok）为 SDXL 写实金标准，RealVisXL V4.0 亚军。 — [insiderllm](https://insiderllm.com/guides/best-photorealism-checkpoints-local-image-generation/); [promptzone](https://www.promptzone.com/tara_suzuki/best-sdxl-models-in-2026-realistic-anime-and-all-purpose-checkpoints-116)

**3D / Pixar 风人像**
- 无权威榜单。SiliconFlow（厂商）2026 "3D image generation" 推荐 FLUX.1.1 Pro Ultra 与 FLUX.1 Kontext 变体，侧重几何准确而非卡通风。 — [siliconflow](https://www.siliconflow.com/articles/best-ai-models-for-3d-image-generation)
- Pixar 风主要依赖社区资产：SDXL 基础的 Pixar 专训模型（触发词 "Pixar-style"）、Civitai "Disney Pixar Cartoon" checkpoint。 — [promptlayer canopus-pixar-art](https://www.promptlayer.com/models/canopus-pixar-art-af6bb); [neura.market Disney Pixar Cartoon](https://neura.market/ai-tools-directory/image-generators/disney-pixar-cartoon-on-civitai)
- 产品内对应预设：Firefly Themes → 3d；Materials → Claymation；Canva Dream Lab → 3D Render；Leonardo → Raytraced / Render 3D（Phoenix 列表未证实）；通义万相 → 3D卡通；即梦 → 3D 卡通。 — 见关键问题 2 来源

**绘画 / 插画风人像**
- Ideogram General 风格官方定位为 "abstract paintings, pencil sketches, digitally manipulated images"。 — [docs.ideogram.ai](https://docs.ideogram.ai/using-ideogram/generation-settings/style)
- Recraft digital_illustration 子风格（hand_drawn、grain、2d_art_poster、digital_engraving、expressionism、pop_art 等）是商用工具中最细的插画分类；Recraft Studio 示例含 "smooth vector portraits" 与 "airbrush-style digital illustrations"。 — [runcomfy](https://www.runcomfy.com/comfyui-nodes/ComfyUI/recraft-style-v3-digital-illustration); [recraft.ai ai-image-generator](https://webflow.recraft.ai/ai-image-generator)
- Firefly Image 5 自定义模型面向 "illustration, character design, or photographic looks"。 — [TechCrunch](https://techcrunch.com/2025/10/28/adobe-firefly-image-5-brings-support-for-layers-will-let-creators-make-custom-models/)

**风格指令的 prompt adherence**
- gpt-image-2 的 reasoning 步骤被描述为"生成前规划构图、核对数量与约束"，并 "significantly better at following detailed instructions"。 — [neurohive](https://neurohive.io/en/news/chatgpt-images-2-0-openai-launches-image-generation-model-with-reasoning-2k-resolution-and-multilingual-text/)
- Imagen 4 Ultra 为 "more precise prompt adherence" 而设。 — [PureAI](https://pureai.com/Articles/2025/06/25/Google-Launches-Imagen-4.aspx)
- Midjourney 社区经验：低 `--stylize` 值 prompt 理解更好，高值审美更好但偏离提示。 — [aituts](https://aituts.com/midjourney-stylize-command/)
- Luma Photon 自称 "Instruction Following" 偏好最高（厂商口径）。 — [Segmind](https://www.segmind.com/models/luma-photon-txt-2-img)

### Inferences
- 综合榜（AA、LMArena）衡量"整体偏好"，与"人像写实"并不等价；评测文章的分歧表明：**写实人像没有单一赢家**，Nano Banana 2 / gpt-image-2 强在一致性与指令遵循，FLUX.2 / Imagen 4 Ultra / Midjourney 强在皮肤与光影质感。
- 3D-Pixar 与绘画风人像在 2026 年仍是"基础模型 + 预设/LoRA"的组合题，而非基础模型本身的竞争点；这也是为什么产品方（Firefly、Recraft、Leonardo、即梦、万相）都把 3D / 插画做成**预设**而不是**模型**。

### Gaps
- 未能读取 arena.ai 的 Photorealistic 与 3D Modeling 分类榜，无法给出 2026-10 这两个细分的模型排名。
- imgsys.org 现状未查（搜索预算耗尽）。
- 缺少 2026 年针对 Seedream 5.0 Pro、Midjourney V8.x、gpt-image-2 的**人像皮肤/光影**专项横评。
- 没有找到任何专门针对"绘画风人像"的榜单或系统评测。

---

## 关键问题 4：各模型的默认审美 / 已知偏差及其中和方法

### Takeaway
2026 年最被广泛讨论的"模型指纹"有三类：Midjourney 的高对比高精修"pretty"默认风（用 `--style raw`、低 `--stylize` 中和）；FLUX 系的"Fluxia"同脸、裂颏（cleft chin）与塑料皮肤（用 Chin Fixer 2000、UnFlux 等 LoRA 或写实 LoRA 中和）；GPT-image 的暖黄/棕褐色偏（用 RGB 缩放后处理中和，OpenAI 无官方解释）。Krea 1 与 Recraft V4.1 等新模型直接把"去 AI 味"写进产品定位。

### Cited Findings

**Midjourney look**
- "every Midjourney model is biased towards a certain 'look', and stylize will change how strongly this bias is applied"；默认 100，范围 0–1000；默认 look 旨在 "pretty"，但 "also generic and gets old after a while"。 — [aituts stylize](https://aituts.com/midjourney-stylize-command/); [midlibrary.io](https://midlibrary.io/midguide/midjourney-v4-stylize-breakdown)
- `--style raw` "tones down the influence of Midjourney's default aesthetic"；同种子对比下默认风格会 "increase contrast and level of detail"，raw 则 "simpler, less polished"；另有来源称 raw 更 photorealistic。 — [nerdschalk](https://nerdschalk.com/how-to-use-the-style-parameter-to-fine-tune-images-generated-on-midjourney/); [bensbites catalog](https://catalog.bensbites.com/tutorial/midjourney-parameters-and-settings)
- V8.2 被第三方描述为 "bolder aesthetics"（未经官方确认）。 — [VidMuse](https://vidmuse.ai/blog/midjourney-8-2)

**FLUX 的脸 / 颏 / 皮肤**
- "Fluxia"：博客将 FLUX 反复出现的同一张脸命名为 Fluxia，指出即便提示不同族裔/年龄，"that distinct dimple often remains"；成因推测（高端时尚数据集让模型把 cleft chin 当作"专业品质"信号）未证实。 — [budgetpixel Who is Fluxia](https://budgetpixel.com/blog/who-is-fluxia-the-mystery-behind-the-worlds-most-famous-non-existent-face)
- 社区 LoRA：Chin Fixer 2000（触发词 "cleft chin"、"jawbone"，有工作流以 2.00 强度与 skin-detail LoRA 叠加）；UnFlux（针对 "overly defined jawlines and chins and plastic-like skin without texture or tone variation"，v2 计划加入皮肤纹理恢复）。 — [civarchive 1732024](https://civarchive.com/models/1732024); [HF Flux.1-Fill-dev Super-Realism LoRA](https://huggingface.co/spaces/X-HighVoltage-X/Flux.1-Fill-dev-Inpainting-Super-Realism-LoRA/blob/b53c891b9a19c5eee0885c2a111006ac241c3862/loras.py)
- SeaArt 写实 LoRA 说明：中等强度（0.42）下用于局部重绘人脸/皮肤 "to get rid of the plastic look of flux"，作者称可消除 "the infamous 'flux chin' issue"。 — [civarchive seaart](https://civarchive.com/seaart/models/c714b5eacad522f00813648402cd481e/versions/c6af9753d71daeb94216bafac9123163)
- 直接 inpaint 消除裂颏效果不佳（HF 讨论）。 — [HF SkalskiP FLUX.1-inpaint-dev](https://huggingface.co/spaces/SkalskiP/FLUX.1-inpaint-dev/discussions/3)
- 修 Flux 塑料皮肤的教程。 — [stable-diffusion-art Fix Flux Plastic Skin](https://stable-diffusion-art.com/?p=17219)

**GPT-image 的黄/棕褐色偏**
- Freepik 技术分析：让 GPT-4o 复刻参考图，输出 "consistently lean warm"，结论是色偏属于模型本身而非提示词；提出用简单 RGB 缩放校正。 — [Freepik blog](https://www.freepik.com/blog/fixing-openais-color-bias-with-simple-rgb-scaling)
- TechRadar（西语）给出色彩校正修法。 — [TechRadar](https://global.techradar.com/es-mx/ai-platforms-assistants/chatgpt/cansado-de-ese-tono-amarillento-en-las-imagenes-de-chatgpt-aqui-te-explicamos-como-solucionarlo-con-una-sencilla-correccion-de-color)
- Know Your Meme 收录 "AI Art Becoming Yellow" 现象；成因有训练数据偏差、模型坍缩（训练于 Ghibli 风 AI 图）、有意为之（提示词重写加暖色）三种**未证实**猜测；OpenAI 无官方解释。 — [knowyourmeme](https://knowyourmeme.com/memes/ai-art-becoming-yellow/photos); [lemmy](https://lemmy.4d2.org/post/2071780/2764919); [meme.com](https://meme.com/memes/ai-art-becoming-yellow)

**通用 "AI look" 与产品化的中和**
- Krea 1 官方定位：针对多数 AI 图的 "soft textures and flat, repetitive compositions"。 — [docs.krea.ai](https://docs.krea.ai/features/krea-1)
- Recraft 文档：V4 "more opinionated"、更风格化，V4.1 相对收敛（"more beautiful by nature"）。 — [recraft.ai docs V4.1](https://www.recraft.ai/docs/recraft-models/recraft-v4-1.md); [recraft.ai blog](https://recraft.ai/blog/recraft-v4-1-more-beautiful-by-nature)
- Adobe 社区指南建议用镜头/景深/构图等摄影参数提升 Image 5 写实度。 — [community.adobe.com](https://community.adobe.com/p/firefly-image-guide)
- Civitai 上 Flux 2 的人像微调最拥挤，说明"修脸/修皮肤"仍是社区首要需求。 — [picassoia](https://blog.picassoia.com/best-flux-2-checkpoints-and-models-on-civitai)

### Inferences
- 三类偏差的中和手段分层：**参数级**（Midjourney `--style raw` / 低 `--stylize`）、**权重级**（FLUX LoRA：Chin Fixer、UnFlux、realism/skin LoRA；SDXL 换写实 checkpoint）、**后处理级**（GPT-image 的 RGB 校色）。闭源多模态模型只能用后两者或提示词绕行。
- "去 AI 味"已成卖点（Krea 1、Recraft V4.1、FLUX.2 对 Kontext 的合并），预示 2026 的审美竞争点是"像不像业余真实照片"而非"够不够精修"。

### Gaps
- "SDXL plastic skin / AI shine" 的具体来源与 "amateur photo" 提示词技巧：搜索预算耗尽前未命中，训练知识中存在（如 amateur photography LoRA、"shot on iPhone" 提示），但本轮无法给出 URL，**不列为事实**。
- FLUX.1 Krea [dev]（Krea 与 BFL 合作的"去 AI 味"模型）相关来源未获取。
- Midjourney V8.x 默认审美的具体变化（相对 V7）无可靠评测来源。
- Nano Banana / Seedream / Qwen-Image 的"厂牌审美偏差"（如过度磨皮、偏亚洲审美等）未找到可引用来源。

---

## 关键问题 5：风格参考功能如何改变用户对"风格"的理解

### Takeaway
2025–2026 年几乎所有主流产品都把"风格"从**关键词/预设**迁移到了**参考图**乃至**个人化模型**：Midjourney 的 `--sref`/`--sw`、Omni Reference 与 Personalization Profile；FLUX 的 Redux / IP-Adapter / Kontext，以及 FLUX.2 原生 10 图参考；Nano Banana Pro 14 图、Seedream 5.0 Lite 14 图 / Pro 10 图；Recraft Create Style、Firefly 自定义模型、Freepik 自定义风格（LoRA，10–50 图）、Krea 1 的 3 图 + style weight；通义万相的"参考图风格迁移"。用户心智随之从"我要一个 watercolor 预设"转为"我要像这几张图这样"。

### Cited Findings

**Midjourney**
- Omni Reference（`--oref`）官方说明：在 Imagine 栏加入 Omni Reference 图会自动用 V7 运行；GPU 用时为常规 V7 的 2 倍；与 Vary Region、Pan、Zoom Out 不兼容；可与 Personalization、Moodboards、stylize、Style References 组合使用。 — [docs.midjourney.com Omni Reference](https://docs.midjourney.com/hc/en-us/articles/36285124473997)
- V7 把 `--sref` 开放给所有用户；`--sw`（style weight）0–1000，默认 100。 — [hyper.ai](https://hyper.ai/en/stories/c77ff6f992fd8f34deda80696e980d55); [CometAPI](https://www.cometapi.com/?p=25326)
- V8.1 要求解锁 Global V7/V8 Personalization Profile（即风格个性化成为默认入口）；第三方称 V8.1 不支持 Omni Reference。 — [docs.midjourney.com models](https://docs.midjourney.com/docs/models); [blakecrosley](https://blakecrosley.com/en/guides/midjourney)

**FLUX 系（Redux / IP-Adapter / InstantStyle / Kontext / FLUX.2）**
- FLUX Redux 被 Runware 描述为 "an IP-Adapter built for the FLUX architecture"，用于参考图变体；**没有 weight 参数，正向提示词对输出无效**。 — [runware IP Adapters](https://runware.ai/docs/learn/ip-adapters)
- 中文 ComfyUI 教程：Redux 能力约为 IP-Adapter 的一半，IP-Adapter 可调强度与遮罩，Redux 不可。 — [lilys.ai notes](https://lilys.ai/notes/zh/ai-image-generation-20251230/flux-redux-style-transfer-comfyui-advanced-control)
- InstantX FLUX.1-dev IP-Adapter（2024-11-22 发布）作者声明：不适合细粒度 style transfer 或角色一致性，存在 content leakage 与 style transfer 的权衡；仅限非商业。 — [HF InstantX README](https://huggingface.co/InstantX/FLUX.1-dev-IP-Adapter/blame/5df0af74c89f666ef6435d3964ed265d04e5604b/README.md); [comfyui-wiki](https://comfyui-wiki.com//en/news/2024-11-22-instantx-flux-ipadapter-release)
- InstantStyle 在 IP-Adapter 之上实现（FLUX 与 SDXL 均有 demo）；ICAS 论文（arXiv 2504.13224，2025）评测：InstantStyle 在简单场景风格化好，但多主体多视角下缺乏灵活性；原版 IP-Adapter 通过权重调节在近写实输入上表现较好，但可能欠风格化或风格"泄漏"。 — [HF InstantStyle-FLUX-SDXL](https://huggingface.co/spaces/Hatman/InstantStyle-FLUX-SDXL/blob/main/app.py); [arXiv 2504.13224](https://arxiv.org/pdf/2504.13224)
- FLUX.2 原生支持最多 10 张参考图并合并了 Kontext 的编辑能力。 — [design-offset](https://design-offset.com/20251125-black-forest-labs-flux-2-image-model/)

**多模态模型的多参考**
- Nano Banana Pro 最多 14 张参考图、5 人一致性；Nano Banana 2 加入 Google Image Search grounding（生成时拉取实时视觉参考）与 video-to-image。 — [marigold.cz](https://www.marigold.cz/tech-news/2025-11-21/nano-banana-pro-launches-as-gemini-3-pro-image-mod); [Neowin](https://www.neowin.net/news/google-launches-nano-banana-2-pro-quality-at-flash-speeds/); [Google Cloud docs](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/models/gemini/3-1-flash-image?authuser=2)
- Seedream 5.0 Lite 可合并最多 14 张参考图；5.0 Pro 最多 10 张。 — [howaiworks](https://howaiworks.ai/models/seedream); [atlascloud](https://www.atlascloud.ai/pt/blog/guides/seedream-4.5-to-5.0-pro-upgrade)
- Qwen-Image-2.0 把生成与编辑统一于单一模型。 — [Analytics Vidhya](https://www.analyticsvidhya.com/blog/2026/02/qwen-image-2-0-is-here/)

**产品级"自定义风格"**
- Recraft：Create Style（上传参考图建风格）。 — [runcomfy Recraft Create Style](https://www.runcomfy.com/comfyui-nodes/ComfyUI/recraft-create-style-node)
- Firefly Image 5：用自己的图片训练自定义模型，保持 line weight、color palette、lighting、character features 一致；已开放全部用户。 — [The Decoder](https://the-decoder.com/adobe-firefly-now-bundles-30-ai-models-and-lets-users-train-custom-styles-on-their-own-images/); [blogdumoderateur](https://www.blogdumoderateur.com/adobe-firefly-peut-copier-reproduire-votre-style-visuel/)
- Freepik/Magnific：自定义风格可由 prompt、单图或图集构建并公开，底层为 LoRA，约 10–50 张图。 — [freepik FAQ](https://www.freepik.com/ai/faq/freepik-styles-and-custom-styles); [magnific custom-styles](https://www.magnific.com/ai/custom-styles)
- Krea 1：最多 3 张参考图 + style weight 滑杆 + LoRA。 — [docs.krea.ai](https://docs.krea.ai/features/krea-1)
- Leonardo：风格以 Style UUID 形式绑定特定模型族。 — [docs.leonardo.ai](https://docs.leonardo.ai/docs/legacy-generation)
- 通义万相官方文档：支持"参考图风格迁移"。 — [help.aliyun.com](https://help.aliyun.com/zh/model-studio/user-guide/text-to-image)
- Kolors 2.0：style transfer 为官方功能之一。 — [Plivo](https://www.plivo.com/blog/exploring-kling-ai-2-0-innovations-and-challenges-in-video-and-image-modeling)
- Ideogram 文档有 Style Reference 功能页（含旧模型风格说明）。 — [docs.ideogram.ai](https://docs.ideogram.ai/using-ideogram/features-and-tools/reference-features/style-reference/styles-in-older-models)

### Inferences
- 三代"风格接口"并存：(1) **离散预设**（Firefly/Recraft/Leonardo/万相/即梦）——可枚举、可统计，是行业分类学的显性证据；(2) **参考图 + 权重**（`--sref --sw`、IP-Adapter、Krea style weight、Recraft Create Style）——风格成为连续向量，不再有名字；(3) **个人化模型**（Midjourney Personalization Profile、Firefly 自定义模型、Freepik LoRA）——风格成为用户资产。
- 对"人像画风分类"研究的含义：官方预设体系（第 2 节）仍是最可靠的"行业共识分类"，但 2026 年头部模型的实际用法已越来越多地绕过这些分类；分类体系应同时容纳"命名风格"与"参考图可达的风格空间"。
- 技术约束影响心智：Redux "提示词无效、无权重"使用户把它当作"变体器"而非"风格器"；IP-Adapter/InstantStyle 的 content leakage 让"风格 vs 内容"的解耦成为用户显性关注点。

### Gaps
- 未能读取 Midjourney 官方 Style Reference 页面（`--sref random`、sref codes、`--sv` 版本参数等细节无官方来源）。
- FLUX.1 Kontext 的发布日期与风格迁移能力细节未在本轮结果中出现。
- GPT-image / Nano Banana 以参考图做"风格迁移"（而非角色一致性）的官方说明或系统评测未找到。
- Recraft 自定义风格的官方参数（所需图片数、是否 LoRA）未获取。
