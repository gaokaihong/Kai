# 3D 家族画风调研：超写实数字人 / 风格化 3D CG / 3D 渲 2D 混合（AI 文生图人像·非二次元）

> 调研截止：2026-10-11。方法说明：本轮共完成约 35 次 WebSearch；WebFetch 与代理 curl 对绝大多数站点（80.lv、history.siggraph.org、unity.com、pcgamer.com、moegirl、tusiart、huggingface 等）返回 DNS 失败 / 403，因此所有引用均基于搜索结果摘要而非全文；本轮会话的共享搜索配额在最后一批查询前耗尽（The Bad Guys、Entergalactic、Overwatch/Fortnite、claymation/毛毡/Funko 提示词、2.5D 插画、Nano Banana Pro 2026 等 8 个查询未执行），相关内容已列入各节 Gaps。文中标注"背景知识，本轮未取得来源"的条目为常识性补充，报告撰写者引用时需自行核实或降级表述。

---

## 关键问题 (a)：超写实 3D / 数字人（MetaHuman、UE5 cinematics、Unity Enemies、数字替身、写实 CG）——视觉识别、恐怖谷破绽、提示词及其 2025–2026 有效性

### Takeaway
"像真人的 3D 渲染"与照片的差别集中在皮肤（次表面散射不足→塑料感、高光过亮的"skin shine"、毛孔/瑕疵过于均匀）、眼睛（湿润度、虹膜焦散、反光一致性）、毛发（strand 级发丝 + 绒毛 peach fuzz 是否存在）和"过于完美"的灯光与零传感器噪点；2022 年后 Epic MetaHuman / Unity Enemies 已把 strand hair、tension 皱纹贴图、虹膜焦散等纳入实时管线，使破绽主要残留在皮肤高光、微表情与瑕疵缺失上。AI 提示词方面，"unreal engine 5 / octane render / 8k / subsurface scattering" 等渲染器标签源自 2022 年 SD 时代，2025–2026 年自然语言模型（Flux、GPT-image、Nano Banana、Midjourney V7）更依赖对光照、材质、镜头的描述；本轮未找到针对 2025–2026 模型的受控 A/B 测试来证明渲染器标签仍有效或已失效。

### Cited Findings

**数字人的技术构成（判定"3D"的正向线索）**
- Unity《Enemies》演示（2022-03，GDC 2022）在 4K 实时渲染中引入新皮肤着色器、"tension" 技术（皱纹贴图 + 血流模拟，无需专门面部绑定即可增加细节）、GPU skin-attachment 支持高密度网格、虹膜焦散（caustics on the iris）— [Dsogaming](https://www.dsogaming.com/news/next-gen-unity-engine-enemies-tech-demo-available-for-download/)
- Enemies 的毛发为三部分 strand-based 方案：作者/蒙皮/模拟、随光照变化的着色、以及针对极细发丝抗锯齿的渲染 — [TechSpot](https://static.techspot.com/news/93863-unity-newly-launched-tech-demo-shows-off-lifelike.html)；Unity 官方称用 multisampled visibility buffer 降低细发丝锯齿、在独立 shading atlas 中着色 — [Unity Blog](https://blog.unity.com/preview/5A3CFNZmduLBx02MoysDheJ2yy_Z9atu1-9Af3HiMcs)；底层使用 HDRP、Adaptive Probe Volumes、SSGI、光追反射与 AO、DLSS，毛发由 Maya XGen 作者、Alembic 导入 — [Game Developer](https://www.gamedeveloper.com/gdc2022/unity-provides-glimpse-of-super-realistic-digital-humans-with-enemies-demo)；官方介绍页 — [Unity](https://unity.com/blog/news/introducing-enemies-the-latest-evolution-in-high-fidelity-digital-humans-from-unity)
- Epic MetaHuman 文档：高 LOD 使用 strand-based 发丝、低 LOD 使用 card/mesh 发片；每个角色的 groom 组件包含 hair、eyebrows、eyelashes、peach fuzz（面部绒毛）、mustache、beard，且 groom binding 使毛发随头部变形 — [Epic MetaHuman docs: Assets Overview](https://dev.epicgames.com/documentation/metahuman/assets-overview)；自定义 groom 可在 Houdini/Maya 中制作 — [Houdini Groom Starter Kit](https://dev.epicgames.com/documentation/metahuman/houdini-groom-starter-kit)
- MetaHuman 皮肤材质 API 暴露的参数包括指甲 TintColor/TintIntensity/Metallic/Roughness、手掌 Lightness/Tint/Cavity Darkness 等 — [FMetaHumanCharacterSkinMaterials](https://dev.epicgames.com/documentation/unreal-engine/API/Plugins/MetaHumanCharacterEditor/FMetaHumanCharacterSkinMaterials)（说明官方管线对皮肤细分区域做了独立材质控制）
- Epic 官方博客（2018-11-02，UE4 数字人直播回顾）明确表述："如果数字人看起来哪怕稍微有点不对，就会进入所谓的恐怖谷（uncanny valley）" — [Unreal Engine Tech Blog](https://www.unrealengine.com/tech-blog/creating-realistic-digital-humans-using-ue4-livestream-recap)

**恐怖谷破绽 / 3D 渲染 vs 照片的判别线索**
- 皮肤次表面散射（SSS）是"塑料感"的核心原因：许多游戏把皮肤渲染得像塑料，是因为未模拟次表面散射；UMBC 研究者称 SSS 是让皮肤真实的首要问题 — [UMBC CSEE News](https://news.cs.umbc.edu/?p=30435)
- 数字人综述：皮肤透光度（translucency）或眼睛湿润度（eye moisture）的微小错误会被立即感知；毛孔、皱纹、绒毛（peach fuzz）等表面微细节与眼睛渲染并列为难题 — [Metavert: Digital Humans](https://metavert.io/digital-humans)
- PC Gamer 评测 MetaHuman Creator（标题即 "pure uncanny valley"）：MetaHuman 面部准确，但仍带有困扰现代角色创建工具的"奇怪的皮肤光泽（strange skin shine）"；牙齿处理得好（牙齿通常是常见破绽） — [PC Gamer](https://www.pcgamer.com/uk/epics-new-metahuman-tool-is-pure-uncanny-valley)
- Blender 社区对一张 3D 肖像的评论："皮肤太均匀、灯光太完美"，另一人指出缺少皮肤瑕疵与汗水 — [r/blender（redlib 镜像）](https://redlib.ssps.io/r/blender/comments/isj71r/final_3d_portrait_of_kevin_malone)
- AI 图像识别指南中与 3D 渲染同构的破绽：皮肤缺少毛孔/过度抛光、前景光照相对背景过强 — [Sightengine](https://sightengine.com/how-to-spot-ai-images-and-deepfakes)；眼睛反光异常或缺失、两眼反光颜色/大小不一致、颈部与手臂也应检查毛孔皱纹 — [Skylum](https://blog.skylum.com/how-to-tell-if-a-photo-is-ai-generated/)；皮肤模糊而旁边头发锐利 — [Veritas (arXiv 2508.21048)](https://arxiv.org/pdf/2508.21048)；表情略显死板、眼睛缺乏深度、面部对称感微妙失真 — [Deseret News 2024-03-21](https://www.deseret.com/u-s-world/2024/03/21/how-to-spot-ai-images/)；2026 年观察者指南 — [Speculative Chic](https://speculativechic.com/visual-tells-of-ai-generated-images-a-guide-for-critical-viewers-in-2026/)
- 这些破绽日益不可靠：Skylum 指出人工修图也会出现同样特征；Sightengine 称识别 AI 图像越来越难 — 同上两源

**经典参考作品（写实 CG 侧）**
- Love, Death + Robots：Chaos 博客案例称《Sonnie's Edge》中"电影级数字人以高度风格化的照片级写实方式与环境融合"，全片使用 V-Ray 渲染；Blur Studio 负责该集 CG — [Chaos Blog](https://www.chaos.com/blog/the-render-tricks-behind-netflixs-nsfw-love-death-robots)；Blur 的《Shape-Shifters》CG 主管称目标是"尽可能照片级写实"（狼人全 3D，写实皮肉与毛发）— [Animation Magazine](https://dev.animationmagazine.net/?p=254714)；各集工作室清单：《Jibaro》《The Witness》= Pinkman.TV（Alberto Mielgo）；《Snow in the Desert》一处记为 Unit Image、另一处记为 Passion Animation Studios，归属未解决 — [What's on Netflix 工作室清单](https://www.whats-on-netflix.com/news/list-of-animation-studios-involved-with-netflixs-love-death-and-robots/)；Blur 发起该系列 — [Post Magazine 2019](https://www.postmagazine.com/Press-Center/Daily-News/2019/Blur-launches-I-Love-Death-Robots-I-series-of-an.aspx)

**提示词关键词及其有效性**
- SD 时代（Hugging Face stabilityai 讨论区）示例关键词列表中包含 "unreal engine 5, octane render" — [Hugging Face discussion #8585](https://huggingface.co/spaces/stabilityai/stable-diffusion/discussions/8585)
- 2025-12 的 Flux 3D 风格指南称 Flux 可通过提示中的深度、光照、材质线索产生可信的 3D 外观，未提及 Octane/Unreal 等渲染器名 — [3DAI Studio](https://www.3daistudio.com/blog/3d-styled-image-generation-with-flux-ai-image-gen-3d-model)
- 一篇 2026 年商业推广性质文章声称现代生成器已能解析自然语言与摄影术语，堆叠 "hyper-detailed 8k render" 类标签不再有用；该文使用了可疑的 "FLUX 3" 名称，可信度低 — [IPS News](https://ipsnews.net/business/?p=250069)
- 存在专门的 "Unreal Engine Render Flux v1" LoRA（ModelsLab），说明 UE 渲染外观在 Flux 生态中已被作为训练目标而非仅靠关键词触发 — [ModelsLab](https://modelslab.com/models/modelslab/unreal-engine-render-flux-v1)
- Higgsfield 博客（营销性质）讨论其生成器的"真实人类皮肤光照" — [Higgsfield](https://geo.higgsfield.ai/blog/higgsfield-ai-generator-realistic-human-skin-lighting)

### Inferences
- 判定"3D 写实渲染而非照片"的快速检查清单（综合上述来源）：(1) 皮肤：有无塑料/蜡感（SSS 不足）、是否有统一的油亮高光（"skin shine"）、毛孔/瑕疵/汗/绒毛是否过于均匀或缺失；(2) 眼睛：角膜湿润反光是否存在且两眼一致、虹膜是否有焦散层次；(3) 毛发：是否为 strand 级单根发丝且有 peach fuzz，还是面片感；(4) 光照：三点布光式"完美"打光、前景比背景亮得不自然；(5) 图像层：零 ISO 噪点、零镜头畸变、景深过于干净（渲染器 DoF 的圆形光斑整齐）。(5) 为背景知识，本轮未取得专门来源。
- 2022 年后（Enemies、MetaHuman）strand hair、tension 皱纹、虹膜焦散已进入实时管线，因此"面片头发/无绒毛/眼睛无焦散"更像 2015–2020 年游戏 CG 的标志，而 2022 年后的 UE5/Unity 数字人破绽更多留在皮肤高光、微表情时序与"完美感"上。
- 提示词演化推断：渲染器名（"octane render / unreal engine 5 / cinema 4d / redshift / arnold"）在 2022 SD1.5/MJ v4 时代是强风格锚点；2025–2026 自然语言理解更强的模型（Flux、GPT-image、Nano Banana、MJ V7）下，这些词仍能作为"这是 CG"的弱锚点，但描述性语句（"photoreal 3D render of a digital human, subsurface scattering skin, strand-based hair, cinematic three-point lighting, shallow depth of field, no film grain"）与专用 LoRA（如 UE render LoRA）成为主路径。此为推断，缺乏受控测试证据。
- "metahuman" 作为提示词：本轮未找到任何来源证明它在任一模型中是有效风格词；建议报告中将其列为"社区使用但效果未证实"。

### Gaps
- 未找到 Epic 官方 MetaHuman 皮肤/眼睛着色器的技术文档（SSS profile、specular 层、眼睛湿润层），搜索只返回 groom 与材质 API 页面。
- 未找到任何针对 Midjourney V7 / Flux / GPT-image / Nano Banana 的受控 A/B 测试，证明 "octane render / unreal engine 5 / 8k / subsurface scattering" 等关键词在 2025–2026 年仍有或已无效果；此问题应标注为"无可靠证据"。
- Weta/ILM 数字替身（digital double）、Final Fantasy 写实 CG（如 FF VII Advent Children / Kingsglaive）在本轮无搜索结果覆盖，仅能作为经典参考名称列出，无可引用来源。
- Unity Enemies 的 Digital Human 2.0 包是否最终发布，来源未确认。

---

## 关键问题 (b)：风格化 3D CG（Pixar/Disney/DreamWorks/Illumination/Sony；游戏风格化；3D 卡通头像；盲盒/潮玩；Funko；黏土；毛毡；搪胶玩具；C4D/Blender 软 3D 插画）——比例、材质、光照、提示词、LoRA 与 2025 趋势

### Takeaway
风格化 3D 在 AI 社区已分化为可独立触发的子风格：Flux 生态有 "live-3D"（Shakker-Labs，卡通 3D 渲染）、"ToyBox"（触发词 t0yb0x / 3d toy design，玩具感）、"Claymation XC"（黏土）、"Chibi-Figure"（大头 Q 版手办）、"泡泡玛特-盲盒风"（触发词 PPMT，Flux 与 Illustrious 双底模）、"3D 潮玩盲盒 IP 手办"（Z1.0）等 LoRA；SD1.5 时代以 Civitai "Disney Pixar Cartoon" 合并模型为代表。2025 年两大闭源模型潮流把该家族推向大众：春季 GPT-4o 图像的 "action figure / Barbie Box"（真实收藏玩具包装渲染，非 Pixar 风）与 "Pixar-style 3D 角色化"，以及 2025-09 Google Gemini 2.5 Flash Image（Nano Banana）的 "1/7 比例 PVC 手办 + 亚克力底座 + 显示器建模过程 + BANDAI 风包装盒" 3D 手办潮流。盲盒风的中文提示词骨架为"盲盒风格、泡泡玛特风格、Q 版、1 头身/大头小身、干净背景、马卡龙配色、C4D 渲染、柔和棚拍光、哑光材质"。

### Cited Findings

**LoRA / 模型（Flux 与 SD 生态）**
- Shakker-Labs FLUX.1-dev-LoRA-live-3D：为 FLUX.1-dev 增强 3D 元素，具备卡通风 3D 渲染能力；推荐权重 0.9–1.3；非商用许可 — [PromptLayer 镜像](https://www.promptlayer.com/models/flux1-dev-lora-live-3d)
- ToyBox Flux（renderartist）：结合 3D 渲染能力与玩具美学；触发词 `t0yb0x`、`3d toy design`；推荐强度 0.7–0.9；建议 Euler 或 DEIS 采样器；动物类不稳定 — [Hugging Face renderartist/toyboxflux](https://huggingface.co/renderartist/toyboxflux)、[PromptLayer](https://www.promptlayer.com/models/toyboxflux)、[Scenario 版本](https://www.scenario.com/models/toy-box-by-renderartist)（色彩明亮、形状圆润，擅长手办、玩具车、风格化人物）
- Scenario "3D Blocky Elements"：3D 块状主体、平滑圆润表面、鲜艳主色与夸张细节带来俏皮玩具感 — [Scenario](https://www.scenario.com/models/3d-blocky-elements)
- Flux Claymation XC LoRA：擅长黏土质感卡通人物 — [PromptLayer](https://www.promptlayer.com/models/flux-claymation-xc-lora)
- Flux CToon LoRA / cflux-cartoon LoRA：Flux 卡通风 — [PromptLayer](https://www.promptlayer.com/models/flux1-dev-ctoon-lora)、[Hugging Face Muapi](https://huggingface.co/Muapi/cflux-cartoon-lora/blob/main/README.md)
- Civitai "Disney Pixar Cartoon" 检查点（SD 时代）：由 "Disney Pixar Cartoon Type A" 与一枚用 Midjourney 图像训练的 LoRA 合并而成，声明与 Disney/Pixar 无关 — [Neura Market 目录页](https://www.neura.market/ai-tools-directory/image-generators/disney-pixar-cartoon-on-civitai)
- InvokeAI 3dVib3（3D 风格模型）— [Hugging Face](https://huggingface.co/InvokeAI/3dVib3)；Castor 3D Portrait Flux LoRA（3D 人像）— [PromptLayer](https://www.promptlayer.com/models/castor-3d-portrait-flux-lora)
- 吐司 TusiArt "Chibi-Figure"（Flux 底模）：生成 3D Q 版手办，头大身小、五官可爱、姿态多样 — [TusiArt](https://tusiart.com/models/768175383859374303)
- 吐司 TusiArt "泡泡玛特-盲盒风 LORA"：触发词 `PPMT`；分别给出 FLUX 与 Illustrious 两个底模的推荐参数；应用场景列出潮玩设计、个性化定制 — [TusiArt](https://tusiart.com/models/852511266923615983)
- Civarchive（Shakker 镜像）"3D 潮玩盲盒 IP 手办 LoRA（Z1.0）"：面向潮玩设计师/盲盒开发者，把 3D 立体质感、Q 版软萌与潮玩盲盒 IP 属性结合，覆盖多种姿态表情 — [Civarchive](https://civarchive.com/shakker/models/0c377b01dea24ea2955d879f5fa49716/versions/4bcfc94aaf1d4961b0629a2b79c4df6d)
- BizyAir 的 FLUX 电商 LoRA 页面提供中英对照提示词，如"可爱的 3D 萌系游戏主机，马卡龙配色方案" — [BizyAir](https://bizyair.cn/community/models/publicity/21019)

**中文提示词骨架（盲盒 / 潮玩 / C4D）**
- 公开聊天日志中的 Midjourney 盲盒模板："盲盒风格、泡泡玛特风格、……、1 头身比例、干净的背景、粉色调、高清画质"（随手示例，非验证教程）— [WildChat 记录](https://wildvisualizer.com/conversation/wildchat/2588875)
- 少数派：Midjourney 提示词可拆为"内容描述 + 风格描述 + 属性描述" — [少数派](https://sspai.com/post/78355)；IT 之家：Midjourney `/describe` 可上传盲盒作品图反推 4 条提示词 — [IT之家](https://www.ithome.com/0/684/518.htm)
- Labubu/Pop Mart 类提示词指南推荐 "cute collectible figure"、"designer toy aesthetic"、"vinyl toy style" 来引导比例与材质；Labubu 特征为尖耳、毛绒质感、大眼、小身体、尖牙、坏笑；Labubu 是 Pop Mart 与 Kasing Lung "The Monsters" 的授权商标角色，商用提示中直接点名有法律风险 — [Vmake](https://vmake.ai/blog/labubu-ai)；Gumroad 售卖 "3D vinyl figure style" Labubu 提示词模板（称适用 Midjourney/DALL·E/Leonardo）— [Gumroad](https://ravirafa.gumroad.com/l/LabubuDollCharacterPrompt)；36kr 英文报道 — [36kr](https://eu.36kr.com/en/p/3358456729700359)
- C4D 风格在中文设计圈的用途：Dribbble 上大量作品同时打 "c4d / ui / 插图 / 2.5d / 图标" 标签，表明该风格主要用于 UI 配图、图标、Banner、运营插画 — [Dribbble TANGLINZI](https://dribbble.com/TANGLINZI)、[Dribbble wuwuwuda](https://dribbble.com/wuwuwuda)、[Dribbble Blueshero](https://dribbble.com/Blueshero/shots)；2020 年 UI 趋势文称渐变更微妙柔和、双色渐变结合模糊 — [腾讯云社区](https://cloud.tencent.com/developer/article/1646376)；C4D 可在一个软件内完成建模、材质、灯光、动画 — [Lesterbanks](https://lesterbanks.com/?p=58027)

**Midjourney sref 与 3D 风格**
- Midlibrary 的 sref 指南称收录 5000+ 代码，按风格分类，含 "3D Design" 类目 — [Midlibrary](https://midlibrary.io/midguide/deep-dive-into-midjourney-sref-codes)
- 一份 sref 整理把黏土/3D 风描述为"糖果色、雕塑感 3D，停格黏土动画 + 设计师玩具美学，橡胶质感、搪胶光泽、黏土体积感"，更接近 Tim Burton/Laika 而非 Pixar；未给出具体代码 — [HackMD romainsimon](https://hackmd.io/@romainsimon/midjourney-sref)
- V7 使用旧 sref 代码需加 `--sv 4`；V7 默认 Style Reference 系统为 `--sv 6` — [Gumroad woollyfern styles4](https://woollyfern.gumroad.com/l/midjourney_sref_styles4)、[Gumroad woollyfern bundle1](https://woollyfern.gumroad.com/l/midjourney_sref_bundle1)；售卖 "96 个 3D 风格 sref" 合集 — [Gumroad olgavolosin](https://olgavolosin.gumroad.com/l/96_3d_style_sref_code)

**2025 年闭源模型潮流**
- GPT-4o 图像 "action figure" 潮流（2025 春）：被称为 "Barbie Box Challenge" / "ChatGPT Action Figure Trend"，用户生成自己装在塑料泡壳包装中的收藏玩具，配以职业/爱好配件与个性化包装 — [MonetizeAI Substack](https://monetizeai.substack.com/p/ai-action-figures-are-trending)；提示要求"真实感动作人偶装在收藏玩具式塑料包装中"— [Tom's Guide](https://www.tomsguide.com/ai/ai-image-video/this-viral-chatgpt-trend-lets-you-turn-yourself-into-an-action-figure-heres-how-to-do-it)；常以 1990s/2000s Barbie 或 Marvel 人偶为模板 — [Main Street GPT Substack](https://mainstreetgpt.substack.com/p/the-action-figure-thing)；该潮流紧随 Ghibli 风潮，依赖 4o 模型，且 4o 擅长渲染包装上的文字 — [WION](https://embed.wionews.com/trending/chatgpts-action-figure-is-the-new-trend-after-ghibli-how-to-create-it-8946706)；#actionfigure 在 TikTok 超 29.7 万帖 — [Blavity](https://blavity.com/chatgpt-action-figure-prompt)；德语、葡语媒体亦覆盖 — [Mimikama](https://www.mimikama.org/?p=372866)、[Exame（含动画版）](https://exame.com/pop/fez-a-trend-do-boneco-na-caixa-no-chatgpt-veja-como-fazer-a-versao-animada-do-action-figure/)。**注意：搜索到的来源均描述为写实收藏玩具渲染，无来源称其为 Pixar 风。**
- GPT-4o "Pixar-style" 照片转 3D 角色（2025-04 起）：方法为上传正面清晰照片，要求"Pixar 风 3D 角色"，描述大而有表现力的眼睛、柔光、彩色背景；若过于写实则追加 "more animated and cartoon-like"；同一方法亦用于 Ghibli、Simpsons、Marvel/DC 风 — [The Digital Librarian 2025-04-08](https://thedigital-librarian.com/2025/04/08/)、[WhatPlugin 2025-04](https://blog.whatplugin.ai/blog/best-gpts-for-turning-yourself-into-a-cartoon)、[Creatoor HQ](https://creatoorhq.beehiiv.com/p/how-to-turn-yourself-into-a-pixar-character)、[AI Tools for Kids](https://www.aitoolsforkids.com/p/pixar-ai-cartoon-kids)、[Amit Das 博客](https://amitdas.is-a.dev/blog/how-to-create-trending-images-turn-your-photos-into-pixar-manga-marvel-dc-styles-using-chatgpt-125)
- Nano Banana（Google Gemini 2.5 Flash Image）3D 手办潮流（2025-09）：Google India 发帖示范并在评论中公布提示词；官方示例要求"1/7 比例商品化手办置于电脑桌上，圆形透明亚克力底座，显示器显示建模过程，旁有二维插画包装盒" — [Jang](https://jang.com.pk/en/47372-gemini-nano-banana-viral-trend-try-these-prompts-to-create-3d-figurine-models-news)；Sundar Pichai 2025-09-25 亦参与 — [Amar Ujala](https://www.amarujala.com/technology/tech-diary/sundar-pichai-joins-gemini-ai-nano-banana-trend-shares-3d-figurine-2025-09-25)；社区长版模板指定 PVC 材质、BANDAI 风包装盒置于后方、室内背景、半身照也输出全身 — [Techjockey](https://www.techjockey.com/blog/?p=59300)、[DEV Community](https://dev.to/koolkamalkishor/how-to-create-trending-3d-figurine-images-with-nano-banana-hidden-prompts-540i)；Google 因热度调整每日生成限额 — [Storyboard18](https://www.storyboard18.com/amp/digital/google-geminis-nano-banana-prompts-how-many-images-can-you-create-with-nano-banana-ai-81624.htm)；衍生出用 image-to-3D 工具把手办图转为旋转 3D 模型/视频 — [Sloyd](https://www.sloyd.ai/llms/blog/the-indian-nano-banana-figurine-trend-now-in-video.md)；同期还有 saree 复古照等非 3D 潮流 — [Storyboard18](https://www.storyboard18.com/brand-makers/-80942.htm)；CyberLink 指南 2025-12 更新 — [CyberLink](https://www.cyberlink.com/blog/trending-topics/4208/gemini-ai-3d-figure)、[PerfectCorp](https://www.perfectcorp.com/consumer/blog/generative-AI/nano-banana-trends)

### Inferences
- 子风格区分维度（基于上述 LoRA 描述与潮流提示词归纳；具体数值与工作室内部规范为背景知识，无来源）：
  - **Pixar/Disney 3D 电影风**：头身比接近真人或略卡通化（约 1:5–1:7），大眼但保留写实虹膜、皮肤有 SSS 与细微毛孔、毛发为 strand 级、全局光照 + 柔和主光 + 环境反射，材质追求"可信而非真实"；AI 提示常用 "Pixar style 3D character, big expressive eyes, soft lighting, colorful background"（来源见 GPT-4o Pixar 潮流）。
  - **游戏风格化（Overwatch/Fortnite/Valorant/LoL cinematics）**：介于 Pixar 与写实之间，夸张轮廓与手绘感贴图，常被 AI 社区混称为 "stylized 3D / Blizzard cinematic style"。本轮未执行相关搜索，无来源。
  - **盲盒 / 潮玩 / Pop Mart 风**：1–3 头身、超大头、极简五官（小嘴或无嘴、点状眼或大圆眼）、搪胶（vinyl）哑光或微光泽表面、纯色/马卡龙配色、干净背景、商品摄影式棚光，常带底座或包装盒；中文关键词：盲盒风格、泡泡玛特风格、潮玩、Q 版手办、1 头身、马卡龙配色、C4D 渲染、哑光材质；英文：blind box, designer toy, vinyl toy style, collectible figure, chibi figure, PVC figure。
  - **Funko Pop 风**：方头大黑圆眼无嘴的固定公式，与盲盒风的区别在于头部为方块化与黑色纽扣眼。无来源，背景知识。
  - **黏土 / claymation（Aardman/Laika）**：可见指纹与捏塑痕、哑光微粒表面、略不规则轮廓、停格动画式布光；Flux Claymation XC LoRA 对应。
  - **毛毡 / 羊毛（毛毡风）**：绒毛边缘、纤维纹理、柔和漫反射、几乎无高光。无来源，背景知识。
  - **C4D 风 / Blender 软 3D 插画**：用于 UI/运营/电商：圆角几何、哑光塑料或磨砂玻璃、柔和双色渐变、浅景深、简洁场景、常为 2.5D 轴测构图（Dribbble 标签佐证"c4d + 2.5d + ui"共现）。
- 2025 年闭源模型潮流对分类的影响：GPT-4o action figure 实际属于"写实玩具产品摄影渲染"（偏 (a) 的材质写实 + (b) 的玩具题材），而 Nano Banana 手办潮流是"写实场景中的手办"（PVC 材质 + 亚克力底座 + 桌面环境），两者都不是 Pixar 式角色动画风；报告中应把"玩具/手办写实渲染"与"卡通 3D 角色"分列。
- 2025 年后 LoRA 命名高度本土化：中文站（TusiArt/LiblibAI/Shakker 中文社区）直接以"泡泡玛特""盲盒""潮玩手办"命名并给出 Flux + Illustrious 双版本，说明盲盒风在中文社区是一个独立、高需求的子风格。

### Gaps
- 未能在 LiblibAI 站内取得盲盒/潮玩 LoRA 页面（搜索未返回 liblib 结果，站点亦无法直接抓取）。
- 未找到 Civitai 官方页面（Civitai 域名未出现在结果中，均为 PromptLayer/Scenario/HF/civarchive 镜像）。
- Funko Pop、毛毡（felt/wool）、Aardman/Laika 黏土、Overwatch/Fortnite/Valorant/LoL 风格化的专门来源：相关搜索因配额耗尽未执行。
- 未找到具体的 Midjourney "Pixar/黏土/盲盒" sref 代码（来源仅为付费合集与分类目录）。
- Pixar/Disney/DreamWorks/Illumination/Sony 各自的比例、材质、光照差异无一手来源；上文属背景知识。
- 未核实 GPT-4o Pixar 潮流的 Reuters 原始报道，以及"免费用户每日 3 张"限额。

---

## 关键问题 (c)：3D 渲 2D 混合（3D转2D / 三渲二 / 2.5D）——Arcane、Spider-Verse、Puss in Boots 2、TMNT、Wish、Nimona；技术与提示词；Guilty Gear/Genshin 二次元边界；"2.5D" 的中西差异

### Takeaway
"3D 渲 2D"内部至少有三条技术路线：(1) **手绘贴图路线**（Arcane：Maya 3D 角色 + Photoshop 手绘含阴影高光的贴图、全手绘背景与 2D 特效、不用 toon shader、无硬阴影边）；(2) **漫画印刷路线**（Spider-Verse：角色二拍 on twos、3D 空间中绘制线条、半色调网点、交叉阴影线、去除运动模糊、Across 版用可显式重绘的线条系统）；(3) **插画/绘本路线**（Puss in Boots 2 的"童话绘画"+ 分段 stepped 动画 + 体积模拟转网格的硬边线；TMNT 的"概念图/速写本"质感 + 风格化绘画式运动模糊；Wish 的全片一致水彩纸纹 + 环境与角色线稿；Nimona 的 2D 关键姿势动画原则进 3D）。**三渲二（cel shading）** 则是用阈值把光照切成明暗两块的 NPR 技术，以 Guilty Gear Xrd（每角色独立光照、"杀掉一切看起来像 3D 的东西"、关键帧有限动画）和原神为代表，属于二次元边界。"2.5D" 一词在西方游戏语境指"3D 图形 + 2D 玩法/视角"，在西方 SD 社区指"介于 2D 动漫与写实之间的半写实二次元"，在中文语境则分裂为 "2.5 次元"（cosplay、手办、舞台剧等二次元与三次元之间的事物）、"2.5D 游戏"（斜 45 度/正交俯视）与 "2.5D 插画"（轴测 UI 插画），而"三渲二"才是对应 toon shading 的技术术语。

### Cited Findings

**Arcane（Fortiche，2021/2024）**
- Fortiche 由美术师直接在 3D 模型上手绘阴影与高光；角色为 3D 建模与绑定，贴图、服装、环境特效为 2D 手绘 — [RedShark News](https://redsharknews.com/why-netflixs-arcane-looks-so-good-how-fortiche-ramped-up-the-animation-pipeline)、[ExpertBeacon](https://expertbeacon.com/how-is-arcane-so-well-animated/)
- 不依赖 toon shader，外观来自手绘贴图，且没有硬阴影边 — [UAL 学生博客（Arcane 贴图测试）](https://kxmola.myblog.arts.ac.uk/?p=291)
- 烟、爆炸等特效手绘，Piltover/Zaun 背景全手绘，魔法特效为霓虹感矢量风 — [ExpertBeacon](https://expertbeacon.com/how-is-arcane-so-well-animated/)；软件：Photoshop 绘制贴图与手绘特效，Maya 负责 3D — 同源
- 社区复刻经验：贴图不仅颜色，roughness/normal/bump 也手绘 — [Blender Artists](https://blenderartists.org/t/does-anyone-have-any-ideas-on-how-this-pesron-did-this/1571065)、[r/3Dmodeling（镜像）](https://lr.in.psf.lt/r/3Dmodeling/comments/1gzb8le/arcane_style)；80.lv 报道艺术家用 Substance 3D Painter 内置画笔 + Blender 复刻 Ekko，技巧为方形 alpha 低不透明度 — [80.lv](https://80.lv/articles/3d-artist-recreates-arcane-s-ekko-with-substance-3d-blender)；80.lv 另有 Arcane 贴图幕后系列，点名 Jinx/Caitlyn/Scar 贴图师 — [80.lv Texturing in Arcane Part 2](https://80.lv/articles/a-closer-look-at-texturing-in-arcane-part-2)；粉丝项目在 Nuke 中分层合成与调色模拟关键光 — [The Rookies](https://www.therookies.co/entries/42547)；法语幕后 — [3DVF](https://3dvf.com/redaction/arcane-les-coulisses-de-la-serie-evenement-issue-de-league-of-legends/)；Alexis Wanneroy 访谈 — [SyncSketch 博客](https://blog.syncsketch.com/?p=75788)

**Spider-Man: Into / Across the Spider-Verse（Sony Pictures Imageworks，2018/2023）**
- 导演 Persichetti、Ramsey、Rothman 称全片按"二拍"（on twos）动画，由此可丢帧并为头发/布料写新算法；线条在 3D 空间中绘制于角色之上，可选择是否响应光照；全片去除运动模糊 — [Dark Horizons](https://www.darkhorizons.com/?p=109512)
- Imageworks 表述：stepped 动画适合快动作，每帧像一幅漫画分镜；半色调（halftone）与线条排线（hatching）强化漫画感——排线用于阴影，网点模拟光 — [Prolific Studio 博客](https://blog.prolificstudio.co/blog/spiderman-into-the-spiderverse/)
- 把 2D 线稿转为 3D 几何极耗工：艺术家把点附着到绘制上并逐帧移动 — [FHS Post](https://fhspost.com/8660/arts-entertainment/spider-man-into-the-revolution-of-animated-films/)
- SIGGRAPH 关于 Across the Spider-Verse 线条的演讲（Grochola、Maccari、Lee、Boulet-Gilly）：方法允许显式重绘线条同时仍跟随底层动画 — [ACM SIGGRAPH History](https://history.siggraph.org/learning/linework-in-spider-man-across-the-spider-verse-by-grochola-maccari-lee-and-boulet-gilly)
- 一份学生研究称角色二拍、背景与镜头运动一拍——与"全片二拍"说法冲突，仅为个人解读 — [UAL 学生博客](https://3danimationcrystal.myblog.arts.ac.uk/2021/01/19/research-presentation/)；技术细节汇总 — [Marila Jane Substack](https://marilajane.substack.com/p/into-the-spider-verse-animation-techniques)

**Puss in Boots: The Last Wish（DreamWorks，2022）**
- 导演 Joel Crawford 以"童话绘画（fairy tale painting）"描述其外观，与 DreamWorks 此前 3DCG 作品明显不同 — [TheWrap](https://www.thewrap.com/puss-in-boots-the-last-wish-behind-the-scenes-video/)、[AWN](https://www.awn.com/animationworld/puss-boots-last-wish-returns-its-fairy-tale-illustration-roots)
- Stepped 动画：可在一拍基础上按需保持多帧，步进率随段落变化；视觉开发总监 Mark Edwards 称 stepped 管线是第一场大动作戏必须解决的问题 — [AWN: Mark Edwards](https://awn.com/animationworld/mark-edwards-talks-visual-development-puss-boots-last-wish)
- 图形化线条：特效团队把体积模拟 pass 转为网格以获得硬的手绘边，并可直接添加额外线条实现 2D 效果；美术总监 Nate Wragg 简化表面细节到"插画级别"而非照片级 — [VFX Voice](https://vfxvoice.com/wishing-upon-a-star-for-puss-in-boots-the-last-wish/)
- 评论将其速写感与翻书式快节奏打斗与 Into the Spider-Verse 相联系 — [Cartoon Brew 影评汇总](https://cartoonbrew.com/feature-film/puss-in-boots-the-last-wish-reviews-roundup-224385.html)；另见 [Skwigly 访谈](https://skwigly.co.uk/puss-in-boots-the-last-wish-interview)

**TMNT: Mutant Mayhem（Mikros Animation，2023）**
- 评论描述为"3D 动画 + 2D 纹理"，类似 Arcane 与 The Mitchells vs. the Machines，但更粗糙、速写本感，每帧带涂鸦/街头艺术质感（Variety 的 Peter Debruge）— [Cartoon Brew 影评汇总](https://www.cartoonbrew.com/feature-film/teenage-mutant-ninja-turtles-mutant-mayhem-reviews-roundup-230940.html)
- 导演 Jeff Rowe 要求成片强烈接近概念图 — [Yahoo/Variety](https://malaysia.news.yahoo.com/why-tmnt-animators-chose-hand-190000956.html)；Rowe 邀请 Mikros 提出服务于"手绘、不完美"美学的点子，Mikros 提出的风格化绘画式运动模糊被全片采用 — [AWN: Jeff Rowe](https://awn.com/animationworld/jeff-rowe-talks-tmnt-mutant-mayhem-teen-boy-tussles)
- SIGGRAPH 演讲题为 "Oozing Hand Crafted 2D Illustration Into a 3D Ninja Turtle World" — [ACM SIGGRAPH History](https://history.siggraph.org/?p=163057)；Mikros 为主动画供应商并发布 breakdown reel（角色、背景、灯光、FX、手绘外观、matte painting、群集）— [Mikros Animation](https://www.mikrosanimation.com/en/news/teenage-mutant-ninja-turtles-mutant-mayhem-breakdown-reel/)、[3DVF](https://3dvf.com/en/teenage-mutant-ninja-turtles-mutant-mayhem-mikros-animation-unveils-a-breakdown/)；Cinesite 温哥华/蒙特利尔提供 21.5 分钟/20 段落 — [Cinesite](https://cinesite.com/?p=13551)

**Wish（Disney，2023）与 Nimona（DNEG，2023）**
- Wish：3D 与水彩绘本外观结合；美术总监称水彩技法用于背景以及环境与角色周围的线条；VFX 总监称开发了一套系统让每一帧都有一致的水彩纸纹理；特效更多依赖程序化而非模拟，并把 2D 特效动画技法与 3D 程序结合 — [SideFX: Wish](https://www.sidefx.com/wish/)、[The Walt Disney Company](https://thewaltdisneycompany.com/wish-disney-animation/)、[Blavity](https://blavity.com/entertainment/the-creatives-behind-disneys-wish-tee-up-the-landmark-film-led-by-ariana-debose)
- Nimona：Netflix 接手后 DNEG 按自身管线从零重做动画；外观把 2D 风格化推进 3D，呈"独特插画感"；DNEG 全球角色动画负责人 Ted Ty 称重点是把老派 2D 感性带入 3D，强调关键姿势与核心动画原则 — [Creative Bloq: Ted Ty](https://www.creativebloq.com/features/nimona-ted-ty-interview)、[Animation Magazine](https://animationmagazine.net/?p=326369)、[Keyframe Magazine](https://keyframemagazine.org/?p=14510)

**三渲二 / toon shading 与二次元边界（Guilty Gear Xrd、原神）**
- 萌娘百科定义卡通渲染（Cel-shading）为"把三维模型与仿二维渲染手法结合的画面表现方式"，名称源自赛璐珞动画质感，动画师尝试将 3D 模型去真实化渲染以模仿 2D 动画 — [萌娘百科：卡通渲染](https://zh.moegirl.org.cn/%E5%8D%A1%E9%80%9A%E6%B8%B2%E6%9F%93)、[萌娘百科：三渲二](https://zh.moegirl.org.cn/%E4%B8%89%E6%B8%B2%E4%BA%8C)
- 技术原理：写实渲染按法线与光线夹角平滑过渡；卡通渲染设阈值把明暗切成界线分明的两块色块 — [wellstsai 卡通渲染(三渲二)技术概览](https://wellstsai.com/single-page-conclusion/%E5%8D%A1%E9%80%9A%E6%B8%B2%E6%9F%93(%E4%B8%89%E6%B8%B2%E4%BA%8C)%E6%8A%80%E8%A1%93%E6%A6%82%E8%A6%BD-%E8%BC%AA%E5%BB%93%E7%B7%9A%E8%88%87%E8%B3%BD%E7%92%90%E7%8F%9E%E5%85%89%E5%BD%B1.html)；原神角色 Shader 还原分析 — [掘金（转载）](https://juejin.cn/post/7207631397094948920)
- 归属争议：CSDN 文称原神、崩坏 3 均运用三渲二技术 — [CSDN](https://damodev.csdn.net/6a424457662f9a54cb85b01f.html)；B 站 2020 年一文认为"卡通渲染包含三渲二"，原神更准确是卡通渲染而非严格三渲二（个人观点）— [Bilibili](https://www.bilibili.com/opus/453497651103088679)
- Guilty Gear Xrd（Arc System Works，GDC 2015，Junya C. Motomura "GuiltyGearXrd's Art Style: The X Factor Between 2D and 3D"）：目标是在现代全 3D 框架内重建经典 2D 格斗游戏并保留其全部 2D 魅力 — [GDC Vault](https://gdcvault.com/play/1022031)；团队定制 cel shader 模仿传统动画着色，每个角色拥有独立自定义光照，打破"同一场景同一光照"的 3D 惯例 — [VideoHighlight 摘要](https://videohighlight.com/v/yhGjCzxJV3E)；为在复杂 3D 角色上得到完美一致的 cel shading 而放弃数学准确性，另涉及可缩放贴图与动画风烟雾 — [BlenderNation 2015-07-26](https://www.blendernation.com/2015/07/26/junya-c-motomura-behind-the-scenes-of-guilty-gear-xrd/)；演讲 PDF — [ggxrd.com](https://www.ggxrd.com/Motomura_Junya_GuiltyGearXrd.pdf)；与会者转述团队目标为"kill anything that looks 3D"，包括像动画一样把动画限制为关键帧（二手信息）— [Steam 社区讨论](https://steamcommunity.com/app/520440/discussions/0/2595630410185653356)

**"2.5D" 的多重含义**
- 西方游戏语境：Wikipedia 定义 2.5D 为玩法/移动限制在二维平面而空间看起来三维、通常在 3D 环境中渲染；并区分"真 3D""真 2D"与伪 3D（pseudo-3D）— [Wikipedia: 2.5D](https://en.wikipedia.org/wiki/2.5D)；Giant Bomb：现代主要指使用 3D 多边形但视角固定为 2D 的游戏，玩家很少能控制镜头；等轴测（isometric）亦可称 2.5D — [Giant Bomb](https://www.giantbomb.com/25d/3015-660/)；Unity 文档：正交摄像机下的 3D 几何（俯视/鸟瞰）有时被称为 "2.5D" — [Unity Manual](https://docs.unity.com/en-us/engine/6000.6/manual/get-started/first-time-user/2dor3d.md)；动画行业词典中的 2.5D 效果 — [ESMA](https://www.esma-artistique.com/en/lexique/2-5-d-effect/)、[Darvideo](https://darvideo.tv/dictionary/animation-2-5d/)
- 西方 SD/Civitai 社区语境："2.5D" 是社区标签，指介于平面 2D 动漫与 3D 感渲染之间、比纯 2D 更写实的风格 — [Novita AI 博客](https://blogs.novita.ai/ai-anime-stable-diffusion-basics/)；模型页将 anime / semi-realistic / 2.5D 标签混用 — [Hugging Face John6666 SDXL 检查点](https://huggingface.co/John6666/xl-caulkinum-animeline-standard-aq-sdxl)、[Hugging Face Stableyogi Semi-Real](https://huggingface.co/Stableyogi/Semi-Real-Checkpoints/blob/main/README.md)；TusiArt 模型称以 "((best quality)), ((masterpiece)), (detailed)" 开头有助于得到 "anime-2.5D" 结果 — [TusiArt](https://tusiart.com/models/601030293110915532)；Flux "Toonic 2.5D" LoRA 触发词为 `toonic 2.5D`，推荐 768×1024 — [PromptLayer](https://www.promptlayer.com/models/flux-toonic-25d-lora-85b68)
- 中文/日文 ACGN 语境："2.5 次元"指现实中的手办、Cosplay、布偶装、ACGN 舞台剧等介于二次元与三次元之间的事物 — [萌娘百科：二次元](https://zh.moegirl.org.cn/%E4%BA%8C%E6%AC%A1%E5%85%83)；真人 Cosplay 是最常见的 2.5 次元类型，该说法源自 niconico 上不露脸、用二次元头像与假名发布作品的歌手 — [MATCHA 日本动漫用语](https://matcha-jp.com/cn/2826)；台湾来源把 VTuber/VOCALOID 归入二次元，而 2.5 次元指真人表演、真人化改编与手办玩偶 — [uptogo](https://uptogo.com.tw/?p=1590340)；另见 [Fiction Passion 专栏](https://fictionpassion.substack.com/p/25-81d)
- 中文设计圈："2.5d illustration / 2.5D 插图"作为 UI 插画标签与 "c4d" 共现 — [Dribbble wuwuwuda](https://dribbble.com/wuwuwuda)、[Dribbble TANGLINZI](https://dribbble.com/TANGLINZI)

### Inferences
- 三条 3D 渲 2D 技术路线的 AI 识别线索：
  - **Arcane 路线**：无硬阴影分界（区别于 cel shading）、可见笔触的贴图（皮肤上有画出来的高光/阴影笔触）、写实比例与解剖、绘画感背景、2D 手绘特效（烟火为平面图形）。AI 提示词通常为 "Arcane style, Fortiche style, hand-painted textures, painterly 3D"。
  - **Spider-Verse 路线**：半色调网点、交叉排线阴影、色彩错位/套印偏移（offset printing misregistration）、粗细变化的墨线、无运动模糊、漫画拟声词与分镜。AI 提示词常为 "Spider-Verse style, comic halftone, Ben-Day dots, offset ink lines, chromatic aberration"。（套印偏移/Ben-Day 为背景知识，本轮来源仅明确提到 halftone 与 hatching。）
  - **绘本/速写路线**（Puss in Boots 2 / TMNT / Wish / Nimona / The Bad Guys）：画笔质感的边缘线、纸纹或水彩纹理、简化的表面细节、stepped 动画造成的"定格感"、速写式线条抖动。AI 提示词："painterly 3D, storybook illustration 3D, sketchy 3D render, watercolor CG"。
- 三渲二 / cel shading 与上面三条路线的本质区别：cel shading 的核心是**阈值化光照（两段或多段色阶）+ 描边**，而 Arcane/Spider-Verse/Puss 路线保留了平滑光照，只是在贴图、线条、后期上加入 2D 手工痕迹。Guilty Gear Xrd 与原神在此划入二次元边界，因其 cel shading 服务于日式动画画风。
- "2.5D" 术语对照表（供报告使用）：
  | 语境 | 含义 | 与本调研的关系 |
  |---|---|---|
  | 西方游戏 | 3D 图形 + 2D 玩法/固定视角，或等轴测伪 3D | 与画风无关 |
  | 西方 SD/Civitai | 半写实二次元（2D 与写实之间） | 属于二次元/半写实分类，非 3D 家族 |
  | 中文 ACGN "2.5 次元" | cosplay、手办、舞台剧等现实中的二次元载体 | 与"手办/盲盒"题材有词义交叉但指实物 |
  | 中文游戏 "2.5D 游戏" | 斜 45 度/正交俯视（本轮仅有 Unity 文档间接支持） | 与画风无关 |
  | 中文设计 "2.5D 插画" | 轴测 UI 插画（常用 C4D/Blender 制作） | 与 (b) 的 C4D 风重叠 |
  | 中文技术 "三渲二 / 3D渲2D / 3D转2D" | 3D 模型 + 卡通渲染 | 对应 toon shading，二次元边界 |
  "3D转2D"作为"三渲二"的同义口语说法为背景知识，本轮未找到专门定义来源。

### Gaps
- The Bad Guys（DreamWorks，2022）与 Entergalactic（DNEG，2022）的技术来源：相关搜索因配额耗尽未执行，仅可作为名称列出。
- 未取得 Fortiche 创始人（Pascal Charrue、Arnaud Delord）或《The Art of Arcane》的一手访谈；Arcane 技术细节均为二手（RedShark、ExpertBeacon、学生博客、论坛）。
- Spider-Verse 的套印偏移（misregistration）、Ben-Day dots、Kirby krackle 等常被引用的元素在本轮搜索摘要中未明确出现（仅 halftone、hatching、二拍、3D 线条、去运动模糊有来源）。
- Guilty Gear Xrd 的法线编辑（normal editing）与有限动画细节未在搜索结果中得到一手确认。
- AI 社区对 "Arcane style / Spider-Verse style / toon shading / cel shaded 3D / painterly 3D" 提示词的实际用法与效果（Civitai/Reddit 讨论）：未找到直接来源；上文提示词为推断。
- 中文"2.5D 游戏 = 斜 45 度"与"2.5D 插画"的权威定义：搜索未返回中文一手来源。

---

## 关键问题 (d)：(a)/(b)/(c) 与摄影写实、2D 绘画之间的常见混淆及快速视觉检查

### Takeaway
最常见的混淆有五类：超写实数字人 vs 真实照片；Pixar 式 3D 角色 vs 盲盒/手办写实渲染（题材相近但材质与比例不同）；Arcane 式手绘贴图 3D vs 2D 油画/厚涂插画；Spider-Verse 式漫画 3D vs 真正的漫画/平面插画；三渲二 vs 手绘二次元。来源指出的可操作线索集中在皮肤均匀度与高光、眼睛反光、毛发表现、光照完美度，以及是否存在阈值化阴影、半色调/排线、纸纹、笔触贴图等 2D 工艺痕迹。

### Cited Findings
- 皮肤过于均匀、灯光过于完美、缺少瑕疵与汗水是 3D 肖像被识破的典型评论 — [r/blender（镜像）](https://redlib.ssps.io/r/blender/comments/isj71r/final_3d_portrait_of_kevin_malone)
- "奇怪的皮肤光泽"是现代角色创建工具的通病，牙齿是常见破绽 — [PC Gamer](https://www.pcgamer.com/uk/epics-new-metahuman-tool-is-pure-uncanny-valley)
- 未模拟 SSS 的皮肤看起来像塑料 — [UMBC](https://news.cs.umbc.edu/?p=30435)
- 眼睛反光缺失/不一致、皮肤缺毛孔、前景光过强 — [Skylum](https://blog.skylum.com/how-to-tell-if-a-photo-is-ai-generated/)、[Sightengine](https://sightengine.com/how-to-spot-ai-images-and-deepfakes)
- 卡通渲染以阈值把光照切成明暗分明的色块，写实渲染为平滑过渡 — [wellstsai](https://wellstsai.com/single-page-conclusion/%E5%8D%A1%E9%80%9A%E6%B8%B2%E6%9F%93(%E4%B8%89%E6%B8%B2%E4%BA%8C)%E6%8A%80%E8%A1%93%E6%A6%82%E8%A6%BD-%E8%BC%AA%E5%BB%93%E7%B7%9A%E8%88%87%E8%B3%BD%E7%92%90%E7%8F%9E%E5%85%89%E5%BD%B1.html)
- Arcane 没有硬阴影边、不用 toon shader，靠手绘贴图 — [UAL 学生博客](https://kxmola.myblog.arts.ac.uk/?p=291)
- Spider-Verse 以半色调与排线强化漫画感、去除运动模糊、线条绘制于 3D 之上 — [Prolific Studio](https://blog.prolificstudio.co/blog/spiderman-into-the-spiderverse/)、[Dark Horizons](https://www.darkhorizons.com/?p=109512)
- Wish 全片有一致的水彩纸纹理，角色周围有线条 — [SideFX](https://www.sidefx.com/wish/)
- 盲盒/手办潮流提示词强调 PVC 材质、亚克力底座、包装盒等实物线索 — [Techjockey](https://www.techjockey.com/blog/?p=59300)、[Jang](https://jang.com.pk/en/47372-gemini-nano-banana-viral-trend-try-these-prompts-to-create-3d-figurine-models-news)；action figure 潮流强调塑料泡壳包装的写实感 — [Tom's Guide](https://www.tomsguide.com/ai/ai-image-video/this-viral-chatgpt-trend-lets-you-turn-yourself-into-an-action-figure-heres-how-to-do-it)
- 西方 SD 社区的 "2.5D" 指半写实二次元而非 3D — [Novita AI](https://blogs.novita.ai/ai-anime-stable-diffusion-basics/)

### Inferences
- 快速判别流程（综合上述来源，顺序执行）：
  1. **先看光照连续性**：阴影是否被切成色块（→ 三渲二/cel shading，多为二次元边界）；若平滑则进入下一步。
  2. **看皮肤与眼睛**：有 SSS 感但过于均匀、统一油亮高光、瑕疵缺失、眼反光完美对称、零噪点 → (a) 超写实 3D；有真实毛孔随机性、传感器噪点、镜头畸变 → 照片。
  3. **看比例与材质**：大眼大头、皮肤仍有 SSS 与发丝 → Pixar/Disney 3D；1–3 头身、搪胶哑光、极简五官、底座/包装 → 盲盒/手办/Funko；指纹与捏痕 → 黏土；纤维绒边 → 毛毡；圆角几何 + 磨砂 + 双色渐变 + 轴测 → C4D/Blender 软 3D。
  4. **看 2D 工艺痕迹**：半色调/排线/墨线/套印错位 → Spider-Verse 路线；可见笔触贴图但体积与透视严格一致、无硬阴影 → Arcane 路线；纸纹/水彩边缘/速写线 → 绘本路线。
  5. **区分 3D 渲 2D 与纯 2D 绘画**：3D 底子的标志是体积/透视/光照在所有部位绝对一致、同一角色在不同角度完全同构、贴图在转折处被拉伸、景深为渲染器式圆形光斑；纯 2D 绘画则有透视与解剖的人工偏差、笔触方向与形体不完全吻合。（此条为背景知识推断。）
- 最易混淆的一对是 **(b) 的 Pixar 风 3D 角色 vs (a) 的"写实玩具渲染"**：2025 年 GPT-4o action figure 与 Nano Banana 手办潮流输出的是**写实材质（PVC/塑料/亚克力）下的卡通比例物体**，报告应将其定义为"写实渲染的玩具题材"而非"卡通 3D 画风"，否则分类会在材质维度上失配。

### Gaps
- 未找到任何系统性的"3D 渲染 vs 照片 vs 2D 绘画"判别指南一手来源；上述流程为综合推断。
- 未找到 AI 社区（Reddit r/StableDiffusion、r/midjourney）关于 "Pixar style 被误生成为写实/盲盒" 之类混淆的讨论来源（配额耗尽前未搜索到）。

---

## 关键问题 (e)：2025–2026 年与各子风格强关联的 AI 工具与趋势（GPT-4o/GPT-image、Nano Banana、Midjourney V7、Flux LoRA、Tripo/Meshy/Hunyuan3D）

### Takeaway
2025 年的两次大众潮流（GPT-4o 的 action figure/Pixar 化，Nano Banana 的 3D 手办）把"玩具/手办写实渲染"与"Pixar 式角色化"变成闭源模型的默认能力；开源侧 Flux LoRA 生态（live-3D、ToyBox、Claymation、PPMT 盲盒、Chibi-Figure、Toonic 2.5D、UE render）承担细分风格；Midjourney V7 以 sref（`--sv 6` 默认，旧码需 `--sv 4`）与 "3D Design" 分类目录承载 3D 风格；真正的 3D 资产生成则由 Tripo（速度、拓扑）、Meshy（综合平台，自称 Meshy 6 获 63.8% 专业评审偏好，为自报数据）、腾讯 Hunyuan3D（开源、PBR 贴图，权重有地域限制）三家主导，2026 年主流做法是"先生成干净参考图，再 image-to-3D"。

### Cited Findings
- GPT-4o action figure（2025 春）与 Pixar 化潮流：见 (b) 节引用 — [MonetizeAI](https://monetizeai.substack.com/p/ai-action-figures-are-trending)、[WION](https://embed.wionews.com/trending/chatgpts-action-figure-is-the-new-trend-after-ghibli-how-to-create-it-8946706)、[The Digital Librarian 2025-04-08](https://thedigital-librarian.com/2025/04/08/)
- Nano Banana（Gemini 2.5 Flash Image）3D 手办潮流（2025-09），Google 调整每日限额，衍生 image-to-3D 视频 — [Jang](https://jang.com.pk/en/47372-gemini-nano-banana-viral-trend-try-these-prompts-to-create-3d-figurine-models-news)、[Storyboard18](https://www.storyboard18.com/amp/digital/google-geminis-nano-banana-prompts-how-many-images-can-you-create-with-nano-banana-ai-81624.htm)、[Sloyd](https://www.sloyd.ai/llms/blog/the-indian-nano-banana-figurine-trend-now-in-video.md)、[CyberLink（2025-12 更新）](https://www.cyberlink.com/blog/trending-topics/4208/gemini-ai-3d-figure)
- Flux 3D LoRA 生态：Shakker-Labs live-3D（0.9–1.3，非商用）— [PromptLayer](https://www.promptlayer.com/models/flux1-dev-lora-live-3d)；ToyBox（t0yb0x，0.7–0.9）— [Hugging Face](https://huggingface.co/renderartist/toyboxflux)；Claymation XC — [PromptLayer](https://www.promptlayer.com/models/flux-claymation-xc-lora)；Toonic 2.5D — [PromptLayer](https://www.promptlayer.com/models/flux-toonic-25d-lora-85b68)；Unreal Engine Render Flux v1 — [ModelsLab](https://modelslab.com/models/modelslab/unreal-engine-render-flux-v1)；泡泡玛特-盲盒风 PPMT（Flux + Illustrious）— [TusiArt](https://tusiart.com/models/852511266923615983)；3D 潮玩盲盒 IP 手办 Z1.0 — [Civarchive](https://civarchive.com/shakker/models/0c377b01dea24ea2955d879f5fa49716/versions/4bcfc94aaf1d4961b0629a2b79c4df6d)；Flux 3D 风格指南（2025-12）— [3DAI Studio](https://www.3daistudio.com/blog/3d-styled-image-generation-with-flux-ai-image-gen-3d-model)
- Midjourney V7：sref 系统默认 `--sv 6`，旧代码需 `--sv 4`；售卖 V7 3D 风格代码（如棕褐色调拟人动物 3D 渲染）— [Gumroad woollyfern bundle1](https://woollyfern.gumroad.com/l/midjourney_sref_bundle1)、[Gumroad woollyfern styles4](https://woollyfern.gumroad.com/l/midjourney_sref_styles4)；5000+ 代码目录含 "3D Design" 类 — [Midlibrary](https://midlibrary.io/midguide/deep-dive-into-midjourney-sref-codes)；2026 年 Midjourney 提示词汇编（含 photoreal/illustration）— [unil.ink](https://unil.ink/blog/best-midjourney-prompts-2026)
- 真 3D 生成（2026 年综述）：Tripo 以几何精度与速度见长（约 20 秒生成、4K 放大）；Tripo v3.1 被称"速度冠军"，Smart Mesh P1.0 约 2 秒产出干净低多边形拓扑 — [Neural4D](https://newsletter.neural4d.com/p/best-meshy-alternative-free-online)、[Pixazo](https://www.pixazo.ai/blog/?p=2759170)；Meshy 被多源称为最完整的独立平台，Meshy 官方对比页自称 Meshy 6 获 63.8% 专业评审偏好（自报）并指出 Hunyuan3D 开源权重有地域限制 — [Meshy 对比页（中文）](https://www.meshy.ai/zh/compare)；Hunyuan3D 被称为最高保真的开源模型并带 PBR 贴图，Krea 运行 Hunyuan3D 3.1 Pro 与 Hunyuan3D-2.1；Krea 建议 2026 年最佳流程为先生成干净参考图再转网格，单一主体 + 纯背景效果最好 — [Krea 博客](https://www.krea.ai/blog/best-ai-3d-model-generators-2026)、[droid.tools](https://droid.tools/best-ai-3d-modeling-tool-2026)
- 这些 3D 工具的对比多来自厂商页或竞品站，未见独立基准 — [Krea](https://www.krea.ai/blog/best-ai-3d-model-generators-2026)、[Meshy](https://www.meshy.ai/zh/compare)

### Inferences
- 工具—子风格映射（基于上述来源推断）：
  - (a) 超写实数字人：Flux + UE render LoRA、Midjourney V7 photoreal 提示、Higgsfield 类"真实皮肤"卖点；闭源模型默认倾向照片感，需显式写 "3D render / CG" 才会得到 (a) 而非照片。
  - (b) Pixar/3D 卡通：GPT-4o/GPT-image "Pixar-style" 转绘是 2025 年最大众化入口；Flux live-3D / CToon；MJ sref "3D Design" 类。
  - (b) 盲盒/手办/玩具：Nano Banana 手办潮流、GPT-4o action figure；Flux ToyBox、PPMT、Chibi-Figure、Z1.0 盲盒 LoRA；中文平台（TusiArt/Shakker）是该子风格 LoRA 的主要产地。
  - (b) 黏土：Flux Claymation XC；MJ 的"黏土/设计师玩具"sref。
  - (c) 3D 渲 2D：Flux Toonic 2.5D（注意它实际是半写实二次元定义的 2.5D）；Arcane/Spider-Verse 风主要靠闭源模型的自然语言引用作品名（推断，无来源）。
  - 真 3D：Nano Banana 手办图 → Tripo/Meshy/Hunyuan3D 转网格，是 2025-09 后被社区验证的"2D 风格图 → 可旋转 3D"链路（Sloyd 来源）。
- 2026 年趋势判断：图像模型的"3D 外观"已不再依赖渲染器关键词而依赖对材质（PVC/vinyl/clay/felt）、比例（1/7 scale、chibi）与场景道具（acrylic base、packaging box）的描述——Nano Banana 官方示例提示词本身即是这一范式的样本。

### Gaps
- Nano Banana Pro（2025-11 之后的 Gemini 3 Pro Image）及 2026 年是否出现新的 3D 潮流：搜索因配额耗尽未执行，无来源。
- Midjourney V7 之后（如 V8）是否发布及其 3D 表现：无来源。
- GPT-image-1 / 后续 GPT 图像模型在 2026 年的 3D 风格能力：无来源。
- 未找到独立的 Tripo / Meshy / Hunyuan3D 同输入基准测试。
- 腾讯 Hunyuan3D 的最新版本号与许可细节仅来自 Krea/Meshy 二手页面。
