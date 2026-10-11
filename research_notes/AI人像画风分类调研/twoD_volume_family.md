# AI 人像/角色画风：「2D 家族」（非日系动画）——从带 3D 体积感的 2D 绘画到平面图形化插画

> 研究日期：2026-10-11。范围：AI 文生图人像/角色，**排除日系动画/漫画**（仅在划界处提及）。
> 研究方法说明（务必阅读）：本轮共执行约 45 次网页搜索；之后共享搜索配额耗尽，且本环境的出站 HTTPS 被代理策略拦截（对 wikipedia / moegirl / civitai / decrypt / midlibrary / openai.com 等全部 403），**无法抓取任何页面全文**。因此下列「Cited Findings」均来自搜索引擎返回的页面摘要与引文（已逐条附 URL），而非整页阅读；凡摘要未覆盖、仅凭通识补充的内容，一律放在「Inferences」并标注「通识，未经本轮来源验证」。报告撰写者引用时请区分这两类。

---

## KQ1. 「2D 但有 3D 体积感」：半写实 / 厚涂（painterly digital painting）vs 平涂·赛璐璐（cel/flat）vs 伪厚涂（cel+painterly 混合）——社区与美术教育如何定义，视觉识别线索是什么

### Takeaway
中文社区（以萌娘百科为代表）现在把「平涂」与「赛璐璐」视为同义——线条清晰、色块分明的上色法/画风；把「厚涂」视为影响整体画面的独立画风（CG 中模拟油画式堆叠、笔触塑造体积、通常弱化或无线稿）；「薄涂」只是小手法而非画风。「伪厚涂」在本轮来源中**没有找到正式定义**，但萌娘百科描述了对应现象：厚涂与赛璐璐/水彩技法杂糅、画面清爽色块整洁但笔触接近厚涂的插画，「以现在的眼光看属于厚涂」。英文社区中与之平行的概念是 semi-realism / semi-realistic（介于 anime-cartoon 与 photorealism 之间）及 SD 模型圈的 "2.5D"（"2.8D"）。

### Cited Findings
- 赛璐珞（Celluloid）「原是使用名为赛璐珞的材料制作动画的技法，后被引申为一类**线条清晰、颜色分明**的整体画面风格。现今赛璐珞基本指画风及这种画风所使用的上色技法，**又称平涂**。」 — [萌娘百科·赛璐璐](https://zh.moegirl.org.cn/%E8%B5%9B%E7%92%90%E7%92%90)；同文见 [萌娘百科·平涂](https://zh.moegirl.org.cn/%E5%B9%B3%E6%B6%82)
- 「平涂」原义只是手绘中平稳均匀的涂色小技巧，「无法决定整幅画的风格」；前十几年用「平涂」指代整体画风可能受部分网络绘画课机构不严谨说辞影响；「如今一般认为平涂就指赛璐珞画风」。 — [萌娘百科·厚涂](https://zh.moegirl.org.cn/%E5%8E%9A%E6%B6%82)
- 「现在一般认为厚涂是一种对画面影响很大的上色手法，可以归为一种广泛使用的画风」；「薄涂」等词与「平涂」类似只是小手法，不足以决定整体画风。 — [萌娘百科·厚涂](https://zh.moegirl.org.cn/%E5%8E%9A%E6%B6%82)
- 「现今一般提到厚涂均指 CG 绘画中的上色技法及画风。」 — [萌娘百科·厚涂](https://mzh.moegirl.org.cn/%E5%8E%9A%E6%B6%82)
- 边界争议：过去有一类「画面干净、色块整洁，但笔触更接近厚涂」的插画曾争议属于厚涂还是赛璐珞；「以现在的眼光看，这些插画都属于厚涂」。 — [萌娘百科·厚涂](https://zh.moegirl.org.cn/%E5%8E%9A%E6%B6%82)
- 「二次元角色插画本身不追求写实或夸张细节，因此所呈现出的一些画面特点便与赛璐珞画风有一定的结合，但最终仍然呈现为厚涂风格」；「也有一些画师在厚涂的插图中将厚涂与赛璐珞、水彩等技法杂糅，总体呈现画面清爽、色块整洁的画面特点」。 — [萌娘百科·厚涂](https://mzh.moegirl.org.cn/%E5%8E%9A%E6%B6%82)
- 草稿精细度不是厚涂/赛璐璐的区分标准：「很多主要画厚涂的画师在草稿阶段也非常精细，草稿的完成度和起稿方式只取决于画师个人的作画习惯」。 — [萌娘百科·厚涂](https://zh.moegirl.org.cn/%E5%8E%9A%E6%B6%82)
- 「『厚涂』『赛璐珞』这类画风说法并不官方和正式，使用时需要注意」；「厚涂与写实、二次元之间的界限有时也很难划清」。 — [萌娘百科·厚涂](https://mzh.moegirl.org.cn/%E5%8E%9A%E6%B6%82)
- Clip Studio 官方教程示例：同一幅画中，前景以「部分可见线稿」方式绘制，背景用厚涂（thick paint）——说明线稿+厚涂混用是常见工作流（对应中文「伪厚涂/半厚涂」的操作形态）。 — [Clip Studio Tips #942 "Organizing Layers & Choosing a Painting Style"](https://tips.clip-studio.com/en-us/articles/942)
- 一份中文 AI 风格清单把当前流行动漫系风格列为：「日系赛璐璐风、轻小说插画风、新海诚电影风、**厚涂幻想风**、Q 版萌系、赛博朋克风、吉卜力风和国风水墨风」——可见中文 AI 社区把「厚涂」作为与「赛璐璐」并列的独立 prompt 风格类目。 — [CSDN/gitcode 风格清单](https://gitcode.csdn.net/6aa0dd4a1a35784c8420829e.html)
- 英文 semi-realism 定义（注意：来源为 SEO 质量页面，权威性弱）：「utilize naturalistic proportions and lighting principles while incorporating exaggerated features like stylized eyes, flowing silhouettes, or painterly brushwork」；「semi-realism focuses on the gestalt—the unified whole of an image」而非毛孔/发丝级细节；是「a bridge between the highly stylised nature of anime or cartoon and the strict study of photorealism」。数字绘画建议：用自定义笔刷/噪点暗示皮肤质感；阴影避免纯黑，用深紫/低饱和棕。 — [Autodesk Origin Exchange "Semi Realistic Art"](https://origin-exchange.autodesk.com/semi-realistic-art)；[同站 "Semi Realism"](https://origin-exchange.autodesk.com/semi-realism)
- SD 社区术语「2.5D / 2.8D」：Hugging Face 论坛用户描述一种「would be called 2.5D or 2.8D」的风格，并称「there are quite a few semi-realistic models」；但他们试用大量热门 Civitai LoRA 后「either get an oil painting result at one extreme, or a photorealistic result at the other extreme」——说明「半写实中间态」是模型最难稳定命中的区间。 — [Hugging Face Discuss: "Stable Diffusion - Can't figure out this Style"](https://discuss.huggingface.co/t/stable-diffusion-cant-figure-out-this-style/112706)
- SD1.5 时代日本社区把 checkpoint 分为三档：illustration（二次元）/ **2.5D** / photorealistic。 — [digitalcreativeai: SD1.5 recommended checkpoint models](https://www.digitalcreativeai.net/en/post/sd15-recommended-checkpoint-models)
- 「Dark Sushi 2.5D」被作为 2.5D 类 checkpoint 的例子提及。 — [Novita AI blog: AI Anime SD Basics](https://blogs.novita.ai/ai-anime-stable-diffusion-basics/)
- ReV Animated（SD1.5 融合模型）作者建议：想要「anime-2.5D type output」时在 prompt 开头加质量 tag。 — [Tusiart: ReV Animated](https://tusiart.com/models/714674823089033070)
- SDXL 时代示例：Obsession IllustriousXL v1.0 被定位为 "anime semi realistic"。 — [aiindigo 教程](https://aiindigo.com/tutorials/getting-started-with-obsession-illustriousxl-v10-mastering-anime-semi-realistic)
- Flux 时代 LoRA 示例：「Flux: Semi-Realistic Anime Art Style LoRA」（2024-09，触发词 `semi-realistic`，生成「semi-realistic anime-style character illustrations」）；「RBStyle」（Flux.1 D，2025-04 更新，把真人照片重绘为「semi-realistic digital painting style」，保持五官比例，明示「not designed for anime, fantasy, or surreal styles」）；「Zavy's Detail Anime/Digital Realism (Flux)」（动画线稿+写实明暗，触发词 `zavy-dtlnm`，强度 0.7–1.3，主要为风景训练）。 — [Civitai #754435](https://civitai.com/models/754435)；[Civitai #1461162](https://civitai.com/models/1461162)；[civarchive Zavy's Detail](https://civarchive.com/seaart/models/656939eb6dd9ef57d2d5bb559eb56dfb/versions/b570ec54ff2008dbd06218e3f47cf9f0)
- Z-Image Turbo 时代示例（2025 末–2026）：「Visionarys Semi-Realism (ZIT)」LoRA，面向女性角色肖像，「balances the line between photorealism and digital art」。 — [Civitai #2311515](https://civitai.com/models/2311515/visionarys-semi-realism-adult-theme-zit)

### Inferences
- 术语映射（综合上述来源）：
  - 平涂 = 赛璐璐 = cel shading / flat color（有清晰线稿，色块分明，阴影为硬边色阶）。
  - 厚涂 ≈ painterly / digital painting / "thick paint"（EN 社区还会说 impasto-like、blended brushwork）；特征为笔触塑形、边缘软硬交替、线稿弱化或被颜色吞掉；萌娘百科把「有厚涂笔触但色块干净」者也归入厚涂。
  - 伪厚涂（亦称半厚涂）：**本轮无正式定义来源**；根据萌娘百科描述的「厚涂与赛璐璐/水彩杂糅、画面清爽色块整洁」与 Clip Studio 「线稿可见+厚涂」混用工作流，可操作性定义为：保留（部分）线稿与赛璐璐式的大块面/干净边缘，但在块面内部用柔化/笔触过渡制造体积感——即「有线稿的厚涂」或「渐变化的赛璐璐」。
  - 半写实（semi-realism）是更上位的概念，描述「比例/光影偏写实、局部特征（眼睛、轮廓、笔触）仍风格化」的结果，而非具体技法；厚涂、伪厚涂、韩系、西方 Artgerm 式等都可落在半写实区间。
- 快速视觉检查（通识，未经本轮来源验证）：
  1. 有无连续线稿包边？有→平涂/赛璐璐或伪厚涂；无或线被颜色吃掉→厚涂/半写实。
  2. 阴影边缘：全部硬边色阶→赛璐璐；硬软混合、块面内有笔触过渡→伪厚涂；边缘随形体转折软化、可见笔触方向→厚涂。
  3. 高光：赛璐璐常用形状化高光块；厚涂高光与笔触融合、有「刮出」感。
  4. 色彩过渡：赛璐璐 2–3 阶；厚涂连续渐变并带色相偏移（冷暗部暖亮部）。
- AI 模型侧：SD 社区「2.5D」概念实质 = 半写实的二次元变体；同一词在 Flux/ZIT 时代被 "semi-realistic" 取代。半写实中间态难以稳定命中（HF 论坛），因此社区倾向用专门 LoRA 或 checkpoint，而非仅靠 prompt。

### Gaps
- 「伪厚涂」的正式定义（知乎/B站/公众号教程）未能获取：搜索到的结果不含该词的定义页，且无法抓取知乎/B站全文。
- 萌娘百科「厚涂」词条全文未抓取（DNS/代理拦截），仅获得搜索引文；词条中的代表画师名单、油画渊源段落未见。
- Proko / Ctrl+Paint / Schoolism / Paintable 关于 cel vs soft vs painterly shading 的英文教育页面：搜索配额耗尽前未检索到，本轮无来源。

---

## KQ2. 西方半写实插画作为 AI 风格锚点：Artgerm、WLOP、Ross Tran、Sakimichan、Loish、Sam Yang、Charlie Bowater、Alex Ross、Greg Rutkowski、Craig Mullins、Ilya Kuvshinov——各自面貌、AI 社区用法、反弹与平台级过滤

### Takeaway
2022 年 Stable Diffusion 1.x 时代，艺术家名是最核心的风格锚点：Greg Rutkowski 被 Lexica 统计为 SD 上被 prompt 最多的艺术家（约 93,000 次，远超米开朗基罗/毕加索/达芬奇的 ≤2,000 次），Midjourney 2022-02 由 CEO 公开的「Style List」含 16,000+ 艺术家名。反弹随之而来：SD 2.0（2022-11）削弱对特定艺术家风格的复现、Stability 为 SD3 接受 Spawning 的 opt-out（约 8,000 万张，占 LAION 约 3%）、ArtStation「No to AI」抗议（2022-12）、Sam Yang 等画师遭「风格模仿模型」骚扰；平台层面 OpenAI 自 DALL·E 3（2023-10）到 GPT-4o 图像（2025-03）明确「拒绝在世艺术家风格、允许工作室风格」。Midjourney 则没有搜到任何禁止艺术家名的官方规则（其禁词主要是政治类，并于 2023-05 转为 AI 审核）。个别艺术家的视觉特征本轮未能从权威页面验证，见 Gaps。

### Cited Findings
**Rutkowski 案例与数字**
- MIT Technology Review（2022-09-16）：据追踪 SD 图片与提示词的 Lexica，Rutkowski 的名字被用作 prompt 约 93,000 次；「Michelangelo, Pablo Picasso, and Leonardo da Vinci, brought up around 2,000 prompts each or less」；其名在 Midjourney Discord 也出现数千次；Disco Diffusion 甚至把他的名字作为示例 prompt。 — [MIT Technology Review](https://www.technologyreview.com/2022/09/16/1059598/this-artist-is-dominating-ai-generated-art-and-hes-not-happy-about-it/)；转述见 [Artnet](https://news.artnet.com/news/a-i-should-exclude-living-artists-from-its-database-says-one-painter-whose-works-were-used-to-fuel-image-generators-2178352)
- Creative Bloq 报道其为「the most prompted artist on Stable Diffusion」，Rutkowski 称「It's terrifying」。 — [Creative Bloq](https://www.creativebloq.com/features/greg-rutkowski-ai-art-prompts)
- Decrypt（2023）：其风格被请求超过 400,000 次（与 Artnet/MIT 的 93,000 口径不同，统计时间与平台不同）；SD 2.0 移除了对其风格的模仿能力，用户抱怨；社区随后在 Civitai 发布复现其风格的 LoRA，作者称其名曾是 SD1.5 最常用 prompt 之一。 — [Decrypt](https://decrypt.co/150575/greg-rutkowski-removed-from-stable-diffusion-but-brought-back-by-ai-artists)
- Hyperallergic 标题：「He's Bigger Than Picasso on AI Platforms, and He Hates It」。 — [Hyperallergic](https://hyperallergic.com/766241/hes-bigger-than-picasso-on-ai-platforms-and-he-hates-it/)
- Rutkowski 立场：AI 生成器「using names of artists as a reference or guide for the AI algorithm to follow a specific style without asking anyone for permission」；被误标为他作品的 AI 图挤占了搜索结果。 — [Artnet](https://news.artnet.com/news/a-i-should-exclude-living-artists-from-its-database-says-one-painter-whose-works-were-used-to-fuel-image-generators-2178352)
- SD 2.0（2022-11-24）更新「stopped the creation of porn and the generation of images in the style of specific artists」。 — [Mezha](https://mezha.ua/en/2022/11/25/the-stable-diffusion-version-2-update-stopped-the-creation-of-porn-and-the-generation-of-images-in-the-style-of-specific-artists/)
- 2022-10 r/StableDiffusion 帖子推荐社区艺术家风格站，目的是「expand your list of artists to more than Greg Rutkowski and Alphonse Mucha」——反映当时 prompt 中艺术家名的高度集中。 — [Reddit r/StableDiffusion (redlib 镜像)](https://redlib.ssps.io/r/StableDiffusion/comments/y3les9/stable_diffusion_artist_list)
- 有关 Rutkowski 的学术/伦理讨论：社区自制 LoRA 的争议（有人认为不道德，有人以「SD1.5 已广泛使用」为由辩护）。 — [UAL 学生论文（Kaiyue Wang, 2022-12）](https://kaiyuewang.myblog.arts.ac.uk/files/2022/12/On-possible-infringement-issues-arising-from-the-use-of-Artificial-intelligence-in-the-field-of-painting-and-visualization.docx)

**Sam Yang（SamDoesArts）**
- 加拿大插画师/内容创作者 Sam Yang 在 2022-12 收到陌生人「阴阳怪气的邮件」，邀他评审一场「哪个自定义生成器最像他风格」的 AI 比赛；当时 AI 爱好者已能用约一百张样图把 SD 适配到特定艺术家风格。 — [RightsTech（2023-05，转载）](https://rightstech.com/2023/05/artists-are-suing-artificial-intelligence-companies-and-the-lawsuit-could-upend-legal-precedents-around-art/)

**ArtStation "No to AI" 抗议（2022-12）**
- 2022-12-09 画师 Dan Eder 发推抗议 ArtStation 首页出现 AI 图（一周内 1,800+ 转发、14,600 赞）；「No to AI Generated Images」图由 Alexander Nanitchkov 设计，Imogen Chayes 12-12 发布，Nicolas Kole 12-13 转发并呼吁官方政策；12-13 该图占据 Trending 页；12-14 ArtStation（Epic Games 旗下）发 FAQ 称内容准则不禁止 AI，并表示不想做「gatekeeper」；之后推出 opt-in 的「NoAI」标签，反对者认为应默认开启。 — [Know Your Meme](https://knowyourmeme.com/memes/events/artstation-anti-ai-protest)；[Game World Observer](https://gameworldobserver.com/2022/12/15/artstation-ai-art-remains-despite-artists-protests)；[Mezha](https://mezha.ua/en/2022/12/15/artists-revolt-against-artificial-intelligence-artists-boycott-artstation/)

**Midjourney：艺术家名单与审核**
- 「Midjourney Style List」电子表格含 16,000+ 艺术家名，含 Banksy、David Hockney、Yayoi Kusama、KAWS 等在世者；法庭文件称该表由 CEO David Holz 于 2022-02 发布并说明这些名字可作 text prompt；该表作为集体诉讼（Andersen v. Stability AI, Midjourney, DeviantArt, Runway）修正诉状附件在 2024-01 公开。 — [Hyperallergic](https://hyperallergic.com/database-of-artists-used-to-train-ai-leaks-to-the-public/)；[File770](https://file770.com/court-exhibit-names-artists-midjourney-scraped-to-train-its-ai-includes-many-hugo-winners/)；[Art Critique](https://art-critique.com/en/2024/01/dredging-list-to-train-midjourney-ai-contains-16000-names)；[Dazed](https://www.dazeddigital.com/art-photography/article/61677/1/midjourney-ai-16000-artists-andy-warhol-frida-kahlo-yayoi-kusama-picasso-disney)
- Midjourney 2023-05 以前使用禁词表审核，之后改为 AI 内容审核（读整句 prompt）。 — [Wikipedia: Midjourney](https://en.wikipedia.org/wiki/Midjourney)
- Midjourney 禁止的具名 prompt 示例是政治人物（「The phrase 'President Xi' is banned」），CEO 称「We just want to minimize drama」。 — [PetaPixel 2023-04](https://petapixel.com/2023/04/03/midjourney-bans-ai-images-of-chinese-president-xi-jinping)
- Midlibrary 有专门的「Mimetic Style Emulation in Midjourney」指南页（内容未能抓取）。 — [Midlibrary](https://midlibrary.io/midguide/mimetic-style-emulation-in-midjourney)
- 一篇伦理 prompting 文章称「many artists' styles and color palettes have been excluded from Midjourney」，但未给日期与来源（可信度低）；另一文建议不要用在世艺术家名字作灵感，属建议非平台规则。 — [Estudio Patagon blog](https://ghost.estudiopatagon.com/gicon/ethical-prompting-how-to-credit-and-respect-existing-artists-in-your-creations/)；[Daniel W. Davison Substack](https://danielwdavison.substack.com/p/ai-art-in-style-of-modern-masters)

**OpenAI：DALL·E 3 → GPT-4o 图像**
- DALL·E 3（2023-09/10）「will reject prompts in which users ask the AI to create a piece of art that is modeled after a living artist's style while dead artists are fair game」；OpenAI 公告称模型「designed to decline requests that ask for an image in the style of a living artist」；艺术家 opt-out 需逐张提交。 — [Gizmodo](https://gizmodo.com/openai-adds-chatgpt-to-new-dall-e-3-image-generator-1850857929)；[Metastellar](https://metastellar.com/?p=30575)；[Voicebot.ai](https://voicebot.ai/?p=30018)；[Decrypt](https://decrypt.co/198035/new-dall-e-3-image-generator-is-a-big-upgrade-with-guardrails)
- 实测 DALL·E 3 也拒绝已故艺术家 Roy Lichtenstein 风格（说明实际过滤比「在世」口径更宽）。 — [Pearl Cohen](https://www.pearlcohen.com/?p=13892)
- GPT-4o 图像生成于 2025-03-25 上线；其 system card 写明新增一条拒绝：「triggers when a user attempts to generate an image in the style of a living artist」；OpenAI 发言人：继续阻止「individual living artists」风格，但「do permit broader studio styles」（如 Ghibli）；随后 ChatGPT 开始拒绝部分 Ghibli 请求但是否有意干预存在「significant ambiguity」；评论指出同样措辞早已出现在 2023 年 DALL·E 3 的 system card。 — [eWeek](https://www.eweek.com/de/news/openai-studio-ghibli-ai-art-copyright/)；[AI Magazine](https://aimagazine.com/articles/how-openais-new-image-model-sparked-the-studio-ghibli-trend)；[Yahoo Tech](https://tech.yahoo.com/articles/chatgpt-starts-blocking-studio-ghibli-192741491.html)

**Stability AI：SD3 opt-out**
- 2022-12 Stability 宣布与 Spawning（HaveIBeenTrained）合作，允许艺术家在 SD3 训练前 opt-out。 — [MIT Technology Review 2022-12-16](https://www.technologyreview.com/2022/12/16/1065247/artists-can-now-opt-out-of-the-next-version-of-stable-diffusion/)
- Spawning 报告艺术家 opt-out 约 8,000 万张，「a drop in the bucket, or about three percent」相对 LAION 20 亿+。 — [The Decoder](https://the-decoder.com/artists-remove-80-million-images-from-stable-diffusion-3-training-data/)

**社区应对：LoRA 替代艺术家名**
- Rutkowski 风格 LoRA 在 Civitai 免费可得（见上）；Flux 时代社区给「Realistic Comicbook Style」等建 LoRA 并托管于 Hugging Face。 — [Decrypt](https://decrypt.co/150575/greg-rutkowski-removed-from-stable-diffusion-but-brought-back-by-ai-artists)；[HF Jonjew/RealisticComicbookStyle](https://huggingface.co/Jonjew/RealisticComicbookStyle/blob/main/README.md)

### Inferences
- 平台梯度（综合来源）：**OpenAI** = 明文拒绝在世艺术家名（2023 起）并实际上会误拒部分已故名人；**Stability** = 从 SD2.0 起通过训练数据/文本编码器更换（OpenCLIP）导致艺术家名效力大减，SD3 再加 opt-out；**Midjourney** = 未搜到禁用艺术家名的规则，艺术家名在 prompt 中仍是公开可用的风格手段（其 2022 的 16,000 名单正是为此目的发布），平台转向 `--sref` 风格码作为去名化的替代；**Flux（Black Forest Labs）** = 本轮无任何来源说明其对艺术家名的处理（见 Gaps）。
- 由此形成的 2024–2026 实务趋势：艺术家名 → ①描述性关键词（"painterly digital illustration, soft blended brushwork, glowing rim light"）、②风格码（Midjourney `--sref`、`--p`）、③风格 LoRA/参考图（IP-Adapter、Flux Redux、Nano Banana/GPT-image 的图生图参考）。报告中若需给 prompt 关键词，应以描述性词汇为主、艺术家名为「历史用法」标注。
- 各艺术家的视觉特征——**以下为通识归纳，本轮未能从 Wikipedia/官方页面核验**（页面抓取被拦截），请报告标注为「常见描述」：
  - Artgerm（Stanley Lau，新加坡/香港）：高完成度光滑渲染、无可见笔触、皮肤与头发高光极亮、偏写实比例但眼睛放大，DC/Marvel 变体封面常见；AI prompt 中常与 "glossy, highly detailed, smooth shading, comic cover" 并列。
  - WLOP（王凌，中国）：《鬼刀》作者；大面积柔光渐变、低对比暗部、发光边缘光、逆光/薄雾氛围，边缘极软、线稿几乎不存在——是「厚涂/半写实无线稿」的典型锚点。
  - Ross Tran（Rossdraws）：高饱和、多色光（粉/青/橙撞色）、笔触可见且带「颜料飞溅」装饰，面部圆润卡通化但光影写实。
  - Sakimichan：半写实二次元/游戏角色同人，皮肤柔光渲染、面部写实化的 anime 比例，Patreon 教程体系；处在「日系—半写实」边界。
  - Loish（Lois van Baarle，荷兰）：流动的发丝与曲线、风格化长颈/大眼、偏 flat-ish 的有限色阶但带柔和体积，动画式造型；比上述更接近「风格化插画」而非写实。
  - Sam Yang（SamDoesArts）：柔和厚涂、粉嫩肤色、放大眼睛与小巧鼻口、暖色主光；因其风格被 SD 模型刻意模仿而成为 2022-12 反 AI 争议焦点（见 RightsTech 引文）。
  - Charlie Bowater（英国）：幻想小说封面/角色肖像，柔和厚涂、精致五官、低饱和暖灰调、丝绸与花饰细节。
  - Alex Ross（美国）：以水粉/不透明颜料实画的超级英雄，照片写实光影、真人模特、Norman Rockwell 式美式插画传统——是「painted comic realism」的代名词（与墨线+平涂的传统漫画相反）。
  - Greg Rutkowski（波兰）：史诗奇幻（龙、骑士、城堡），厚涂宽笔触、强体积光、暖金与冷蓝对比、大气透视；AI 时代被用作「epic fantasy painterly」通用词。
  - Craig Mullins（美国）：数字绘画先驱，概念设计式 speed painting、大块面值阶（value）优先、边缘松散、细节集中于焦点——是「concept art painterly」的祖师级锚点。
  - Ilya Kuvshinov（俄罗斯，居日本）：anime 比例的面部+写实柔光与皮肤质感、亮粉/青配色、简洁背景；明确位于「日系—半写实」边界（本报告只作划界用）。
- 「反弹时间线」可归纳为：2022-08 SD1.4 公开 → 2022-09 Rutkowski 报道 → 2022-11 SD2.0 削弱艺术家风格 → 2022-12 ArtStation 抗议 + Sam Yang 事件 + SD3 opt-out 宣布 → 2023-01 Andersen 集体诉讼 → 2023-10 DALL·E 3 在世艺术家拒绝 → 2024-01 Midjourney 16,000 名单曝光 → 2025-03 GPT-4o 图像沿用「在世艺术家拒绝/工作室风格允许」。

### Gaps
- 各艺术家维基/官网页面均无法抓取（en.wikipedia.org 被代理 403），上面的视觉特征描述未经本轮来源验证。
- Sam Yang 事件的原始报道（Kotaku/Reddit 帖）未能检索到；仅有 RightsTech 的二手叙述。
- Artgerm、WLOP 等在 Lexica/DiffusionDB 中的 prompt 频次：无来源。
- Midjourney 2024–2026 的现行 ToS 对艺术家名的规定：未找到官方页面；Midlibrary「Mimetic Style Emulation」页面未能抓取。
- Flux（BFL）与 SD3 的文本编码器对艺术家名的实际响应（社区普遍称 Flux「不认识大多数艺术家名」）：本轮无来源，不要作为事实引用。
- Nano Banana（Gemini 图像）与 Seedream、Qwen-Image、Z-Image 等 2025–2026 模型关于艺术家名的政策：搜索配额耗尽前未检索到。

---

## KQ3. 韩系 webtoon/漫画半写实（韩系、韩漫，《Solo Leveling》《True Beauty》类）与韩国游戏插画——如何区别于日系动画与西方半写实

### Takeaway
中英文社区的共识：韩系（漫画与游戏插画）比日系更写实——身体比例接近真人、面部仍风格化但较日系眼小、鼻嘴刻画完整；立体感（体积/厚涂）强于日系、细腻度高于美式块面；色彩比日系更内敛浓厚、肤色饱满偏肉色；网漫全彩、竖向滚动、服饰与背景细节多。与西方半写实的区别更多在面部理想化（「混血感」、高度统一的美型模板）与时尚/都市题材，而非技法。AI 侧：现成的 webtoon/manhwa LoRA 多为 SD1.5 时代作品，质量参差；专门的 manhwa 生成器以「clean lines + soft shading + 全彩 + 竖版分镜」为卖点。

### Cited Findings
- 游戏媒体机核分析：韩式人物辨识点是「混血感的面孔、夸张的身材比例，以及强调性感曲线的刻画」；韩式风格「融合了日式的柔美华丽与美式的块面张力，立体感比日式强，细腻程度比美式高」。 — [机核 GCORES #153920](https://www.gcores.com/articles/153920)
- B 站专栏：韩风「人物的体态张力很强，色彩比魔幻写实更内敛浓厚，肤色普遍偏饱满的肉色，并常把古风与现代元素融合」；对比日系「色块变化较少，但对线稿要求更高；色彩通常更明艳……人物头部和眼睛常被夸张化，嘴和鼻子则相对简略」；并承认「日风与韩风的界限近年越来越模糊」。 — [Bilibili 专栏 opus/337641994918252136](https://www.bilibili.com/opus/337641994918252136)
- 「美系」「日系」等标签「只是大众按地域印象做的简化归类，与画师国籍不一定有关，也没有官方定义」。 — [萌娘百科·厚涂](https://mzh.moegirl.org.cn/%E5%8E%9A%E6%B6%82)
- 英文来源：manhwa 中「the bodies of characters are often realistically proportioned, while the faces remain unrealistic. Manhwas also often have very detailed clothing on their characters as well as intricate backgrounds」。 — [Tropedia: Manhwa](https://tropedia.fandom.com/wiki/Manhwa)
- 与日漫对比：manhwa「more realistic than manga, with less over-the-top cartoon-like features」；anime「large, vibrant eyes and exaggerated features」而 manhwa「intricate facial features and body proportions」；日系发型夸张、韩系发型「more natural and down to earth」；manhwa 对背景投入同等精力。 — [90 Day Korean](https://www.90daykorean.com/?p=64020)；[Koreabridge](https://koreabridge.net/post/manhwa-–-korean-comics-entertainment-and-learning-90daykorean)
- 格式：「Unlike the traditional black-and-white art style of manga, manhwa/webtoons are often (though not always) in full color」；webtoon 为手机竖向滚动而设计；「most contemporary Korean comics are published in the webtoon format」。 — [Free Library of Philadelphia: Manga 101](https://libwww.freelibrary.org/blog/post/5196)；[Wikipedia: Manhwa](https://en.wikipedia.org/wiki/Manhwa)
- 《Solo Leveling》漫画绘者为 Jang Sung-rak（DUBU）。 — [Vikidia (fr)](https://fr.vikidia.org/wiki/Solo_Leveling)
- AI 资源：Tusiart 上有「SOLO LEVELING (style)」LoRA（基础模型 SD1.5），作者自述「may not be the best Lora style」。本轮**未**在 Civitai 搜到对应 LoRA 页。 — [Tusiart #661145468857808300](https://tusiart.com/models/661145468857808300)
- Prompt 示例（社区 gallery）：「simple clean Korean manhwa art style — expressive faces, office setting, Korean speech bubbles」。 — [Carat.im webtoon gallery](https://carat.im/en/prompt-gallery/webtoon)
- Prompt 写法：把 prompt 当分镜脚本写（机位、光线、情绪词、锁定发型/服装/道具以保持角色一致）；示例如「wide shot of a chaebol heir against a glass office wall with warm amber rim light」。 — [CapCut: AI Image for Korean Webtoon Style (2026 guide)](https://www.capcut.com/ideas/ai-image/ai-image-for-korean-webtoon-style)；[Morphic: How to make manhwa with AI](https://morphic.com/resources/images/manhwa-ai)
- 专用工具：LlamaGen「AI Manhwa Generator」等以 manhwa 风格为卖点（厂商页）。 — [LlamaGen](https://llamagen.ai/en-in/features/ai-manhwa-generator)

### Inferences
- 韩系 vs 日系快速检查：①眼睛占脸比例（韩系明显更小、眼型细长、有睫毛与双眼皮刻画）；②鼻子有完整鼻梁/鼻翼而非一点；③身体 7.5–8 头身、肩颈真实；④皮肤有柔和体积渲染（soft shading / 半厚涂）而非赛璐璐硬阴影；⑤色调偏低饱和、肤色粉肉、都市时尚服装；⑥若为网漫原图，竖长画幅与对话气泡。
- 韩系 vs 西方半写实（Artgerm/WLOP 等）：技法重叠（都是柔和厚涂/半写实），差别在面部理想化模板高度统一（「美型」、小脸尖下巴、「混血感」）、线稿常保留且干净（网漫需量产，线稿+柔和上色是主流工作流），而西方半写实更常无线稿、个体面部特征更多样。
- 韩国游戏插画（通识，未经本轮来源验证）：如 NCSoft、Pearl Abyss（Black Desert）、Nexon 等的宣传图以高完成度厚涂、华丽服饰材质、戏剧性打光为特征，常被中文圈称「韩式厚涂/韩风游戏插画」，比网漫更写实、更接近西方 concept art 的完成度。
- EN prompt 关键词（综合社区用法）：`Korean webtoon style`, `manhwa style`, `clean line art`, `soft cel shading`, `semi-realistic proportions`, `full color`, `vertical scroll panel`, `fashion illustration`, `glossy hair`；CN：`韩漫风`, `韩系网漫`, `韩风半写实`, `韩式厚涂`。

### Gaps
- 无来源直接描述《True Beauty》（女神降临）的视觉特征；关于《Solo Leveling》画风的描述仅限绘者归属。
- 韩国游戏插画（韩式厚涂）的权威定义与代表作品：机核文章全文未能抓取，仅有摘要。
- Civitai 上 webtoon/manhwa 相关 LoRA 的下载量与质量排名：Civitai API 被拦截，无数据。
- 「webtoon vs anime」的任何艺术史/学术分析：未找到。

---

## KQ4. 漫画谱系：美式漫画（墨线+平涂+网点）、现代数字漫画渲染、欧漫 BD / ligne claire（Hergé、Moebius）、graphic novel、黑色电影式墨绘（noir ink）——视觉线索与 prompt 关键词

### Takeaway
美式经典漫画 = 粗黑墨线轮廓 + 平涂高饱和原色 + 网点/Ben-Day 印刷纹理 + 动态线与纸张质感；ligne claire = 清晰等粗（或微变）线、无排线、极少阴影、投影被「照亮」、强色块、卡通人物置于写实背景；noir ink = 消灭中间灰阶，纯黑与纯白雕塑形体，偶以单一饱和色（红唇/血）点睛。Alex Ross 式「painted comic realism」则是以实画颜料达到的照片写实，属于前文「2D 有 3D 体积」区而非线稿漫画。社区 prompt 关键词已高度标准化（见 Findings）。

### Cited Findings
**美式漫画 / pop art 关键词**
- 社区 gallery 建议：「bold black contour lines, flat saturated colors, and dense halftone dot shading to evoke vintage comic printing」，并留空标题区、禁文字；模板加入「clean vector look」「action lines」与负面词「no 3D render」「no existing characters」。 — [Carat.im comic book cover](https://carat.im/en/prompt-gallery/comic-book-cover)；[法文版](https://carat.im/fr/prompt-gallery/comic-book-cover)
- 风格指南列出：thick ink outlines、cel shading、action lines、vivid flat colors，并给 Midjourney/DALL·E/SD 的模型提示。 — [gptprompts.ai Comic Book style guide](https://gptprompts.ai/ai-image-styles/comic-book)
- 对经典漫画 prompt 的拆解强调「halftone printing texture」「bold black ink outlines」「action lines」「strong primary color palette」是锚定词。 — [Roberto Dias Duarte（葡语）](https://www.robertodiasduarte.com.br/?p=95274)
- 「Halftone comic book」被列为一种 UI/插画趋势（Ben-Day 点、粗轮廓、CMYK 风格）。 — [daisyUI trends: halftone comic book](https://trends.daisyui.com/trend/halftone-comic-book/)
- 「1960s Pop-Art Comic Book Portrait」prompt 模板存在（Lichtenstein 式人像）。 — [YouMind prompt](https://youmind.com/prompts/1960s-pop-art-comic-book-portrait-live-announcement-1787)
- DALL·E 3 曾拒绝 Roy Lichtenstein 风格请求（pop art 锚点在 OpenAI 产品中可能被拒）。 — [Pearl Cohen](https://www.pearlcohen.com/?p=13892)
- Flux 时代存在「Realistic Comicbook Style」LoRA（Hugging Face 托管）。 — [HF Jonjew/RealisticComicbookStyle](https://huggingface.co/Jonjew/RealisticComicbookStyle/blob/main/README.md)

**Ligne claire（欧漫清线派）**
- 「clear line」，由 Hergé 开创；名称由 Joost Swarte 1977 年提出；「clear strong lines sometimes of varied width and no hatching」；阴影极少、「contrast is downplayed, and cast shadows are often illuminated」；「strong colours and a combination of cartoonish characters against a realistic background」。 — [Aesthetics Wiki: Ligne Claire](https://aesthetics.fandom.com/wiki/Ligne_Claire)
- Hergé 作品中「almost all lines… are more or less the same weight」；早期受美国 1920–30 年代连环画（Gluyas Williams、George McManus）影响；成熟形态在二战期间重印时加平涂色。 — [Comics Odyssey: Artist Profile Hergé](https://comicsodyssey.substack.com/p/artist-profile-herge-the-master-artist)
- ligne claire 与 Marcinelle 学派的边界在粉丝圈有争议（「in the eye of the beholder」）。 — [Tintinologist forums](https://www.tintinologist.org/forums/msg.php?id=44816)

**Noir ink / Sin City**
- Frank Miller 的 Sin City「eliminate gradients and midtones, sculpting the world purely through stark light and deep shadow」。 — [Leaselab: Frank Miller's art style](https://api-reach.leaselab.com.au/post/you-wont-believe-the-hidden-secrets-of-frank-millers-iconic-art-style)
- 2005 电影以黑白拍摄、后期局部加色；颜色用于「one or two specific elements rendered in saturated color, typically red lips, blood, or a single object」。 — [tboake: Sin City](https://tboake.com/443_sincity_f07.html)
- FLUX LoRA「Graphic Noir: Sin City Style v2.0」建议搭配 tokens：「stark black-and-white contrast」「bold linework」「monochrome」，作者自认「pales in comparison to the work of the great Frank Miller」。 — [Tensor.Art #842692258991013230](https://tensor.art/models/842692258991013230)
- SD1.5 Sin City LoRA：建议权重 0.5–0.6，超过 0.6 会扭曲面部；适合的点睛色为红、黄、绿、偶尔蓝。 — [civarchive SeaArt 模型](https://civarchive.com/seaart/models/35101434d9b3423a1ed44e34b7f8e9df/versions/13da8555e50c133ecdaf8a034d52370d)
- 2026 年有「Sin City photo generator」类工具把照片转为高对比 noir。 — [DEV Community](https://dev.to/ai_tools_directory/free-ai-sin-city-photo-generator-turn-any-photo-into-high-contrast-noir-art-2026-f19)

### Inferences
- 谱系与视觉检查（综合）：
  - 美式 Golden/Silver Age：粗墨线 + 平涂原色 + 网点 → 看网点与纸纹。
  - 现代数字漫画渲染（Marvel/DC 2010s 后）：墨线保留，但上色用柔和渐变、光效、材质贴图；网点消失、出现镜头光晕——介于 cel 与 painterly 之间（相当于中文「伪厚涂」的美式对应）。
  - Painted comic realism（Alex Ross 一脉，通识）：无墨线、实画水粉、照片级光影；AI 中用 `painted comic cover, gouache, photorealistic superhero, Norman Rockwell lighting` 类描述；它应归入「2D 有体积」区。
  - Ligne claire：线等粗、无排线、无投影或极淡、平涂色 → 看「阴影是否几乎不存在」。Moebius 一脉（通识，本轮无来源）常在 ligne claire 骨架上加细密排线与迷幻配色，AI prompt 多用 `Moebius style, ligne claire, fine ink lines, pastel sci-fi palette`。
  - Graphic novel（通识）：无统一技法，AI 社区用它指「成人向、灰暗、墨水+水彩/数字淡彩、叙事感」的漫画插画。
  - Noir ink：只有黑白两值（无灰阶）+ 单色点睛 → 看是否存在中间调。
- EN 关键词汇总：`comic book style, bold ink outlines, halftone dots, Ben-Day dots, flat primary colors, action lines, newsprint texture, 1960s pop art`；`ligne claire, clear line, uniform line weight, no hatching, flat colors, minimal shadows, Hergé style`；`graphic noir, stark black and white, heavy solid blacks, no midtones, spot color red`；CN：`美漫风`, `墨线+平涂`, `网点`, `波普艺术`, `欧漫清线派`, `黑白高反差墨绘`, `图像小说风`。

### Gaps
- Moebius 的 ligne claire 变体与 prompt 关键词：搜索结果未提及 Moebius（配额耗尽前未补搜）。
- Alex Ross 的媒介与手法（水粉、真人模特、Rockwell 影响）：Wikipedia 未能抓取，上述为通识。
- 「现代数字漫画渲染」的权威描述：无来源。
- Civitai 上 comic/noir LoRA 的下载量：API 被拦截。

---

## KQ5. 传统媒材模拟（人像）：油画（古典写实、印象派、Sargent/Rembrandt 光）、水彩、水粉、炭笔/铅笔素描、色粉、水墨与工笔/国风——视觉线索、prompt 关键词、2025–2026 哪些模型质感可信

### Takeaway
媒材模拟的 prompt 核心是「命名媒材 + 命名其物理特征」：水彩要写透明叠色、水花（blooms）、纸纹；油画要写 impasto、笔触方向、画布纹理；水墨要写留白、墨色浓淡、宣纸晕染；工笔要写细线勾勒、层层渲染、绢本设色。2025–2026 的模型综述普遍把 Midjourney 列为「风格/艺术方向」首选，Flux 2 在「stylized and illustrative」上不领先，Nano Banana 2/Pro、Seedream、GPT-image 更以指令遵循与文字见长——但**本轮未找到任何对油画/水彩质感的横向实测**。国风方向主要靠 Flux/F.1 与 SD1.5 的 LoRA（如「唐风工笔娃娃」「inkColor·墨彩」），且作者自述对真人写实底模效果差。

### Cited Findings
**媒材描述与 prompt 原则**
- 媒材命名指南：指出 watercolor「introduces transparency, 'blooms' of pigment, and a distinct paper-grain texture」，油画可写 impasto；该文不比较模型。 — [BudgetPixel: The Art of the Instruction: Style, Artist, and Medium](https://budgetpixel.com/blog/the-art-of-the-instruction-style-artist-and-medium)
- Midjourney V7 文章示例 prompt：「vivid oil painting style with impasto technique, rich textures, bold and expressive brushstrokes」（无效果评估）。 — [TechDogs: Midjourney V7](https://www.techdogs.com/td-articles/trending-stories/midjourney-v7)
- Decrypt 对 V7 alpha 的评测：相对 V6.1「a modest improvement」，alpha 缺少 remix 等功能，放大/局部重绘回落到 V6.1——未专门测绘画质感。 — [Decrypt: Midjourney v7 review](https://decrypt.co/313704/midjourney-v7-review-struggles-keep-up)
- Artsology（宣传性）称 V7 的「hair strands, fabric textures, reflections… skin tones are much more realistic」，可按 prompt 偏向照片或绘画。 — [Artsology 2025-04](https://artsology.com/blog/2025/04/midjourney-v7-ai-art-generator-update/)
- Flux 的 impasto 方向 LoRA：「Zavy's Rough Paint (Flux)」= 厚笔触 impasto 外观（与半写实相反方向）。 — [civarchive #777325](https://civarchive.com/models/777325/zavys-rough-paint-flux)
- SDXL/Pony 的「Painted World」= 绘画感 checkpoint/LoRA。 — [civarchive #242763](https://civarchive.com/models/242763/painted-world-or-pony-and-sdxl)

**国风：水墨 / 工笔**
- FLUX 水墨工作流（2025-03-26）：FLUX fp8 底模 + Taomitown 自定义 LoRA（权重 0.8），分辩率 1024×1536。 — [ComfyUI.org: Chinese ink painting with FLUX](https://comfyui.org/zh/chinese-ink-painting-with-flux)
- 唐风工笔人物工作流（2025-04-17）：LoraLoader 加载「唐风工笔娃娃_v1.0」，权重 1.0，底模「基础算法_F.1」（Flux.1），1024×1920，推荐 ≤8GB 显存；面向唐代汉服少女等人物。 — [ComfyUI.org: Tang dynasty portrait painting workflow](https://comfyui.org/zh/tang-dynasty-portrait-painting-workflow)
- 「inkColor·墨彩 0.10」（SD1.5 LoRA）：水墨/水彩/工笔之间的过渡风格，建议权重 0.5–0.8，推荐搭配 CGArt Butterfly 等底模；作者称「works exceptionally well for any model except real human models」。 — [Tensor.Art #622213020292205951](https://tensor.art/models/622213020292205951)；[Tusiart 同模型](https://tusiart.com/models/622213020292205951)
- 「ShuimohuaAnime」= 水墨 + 动漫风融合，基于 GyozaMix 系列，许可 CreativeML OpenRAIL-M。 — [PromptLayer: shuimohuaanime](https://www.promptlayer.com/models/shuimohuaanime)
- 相关：剪纸风 LoRA（Paper-cut_v1.0）可配 FLUX，偏装饰图案；传统中国艺术生成综述页。 — [ComfyUI.org paper-cut](https://comfyui.org/en/ai-generated-chinese-paper-cut-art)；[ComfyUI.org traditional Chinese art](https://comfyui.org/en/traditional-chinese-art-generation)

**2025–2026 模型格局（厂商/聚合评测，需谨慎）**
- 「distinctive art direction: Midjourney」；Midjourney「remains compelling when visual taste is the brief」。 — [Magnific: Best AI image models 2026](https://www.magnific.com/blog/best-ai-image-models/)；[Atlas Cloud 2026 comparison](https://www.atlascloud.ai/blog/best-ai-image-generation-models-2026)
- 「Where Flux 2 doesn't lead: Stylized and illustrative output」。 — [Switas: 40+ models comparison 2026](https://switas.com/articles/the-best-ai-image-and-video-generators-of-2026-a-massive-comparison-of-40-models)
- Nano Banana 2 被一处列为「best for creative styles」，Nano Banana Pro 被另一处称适合「dense instructions and information-rich scenes」；Seedream 被定位为「information, text, editing, and polished marketing visuals」；ChatGPT Images 为「broadest first stop」。 — [Dreamina/CapCut 2026 comparison](https://dreamina.capcut.com/ai-model/best-ai-image-generation-models-2026-comparison)；[Cliprise 2026 ranked](https://www.cliprise.app/learn/comparisons/features/best-ai-image-generator-2026-tested-ranked)
- 开源数字绘画模型 2026 指南（SiliconFlow，厂商）。 — [SiliconFlow: Best open source AI for digital painting 2026](https://www.siliconflow.com/articles/best-open-source-ai-for-digital-painting)

### Inferences
- 媒材快速视觉检查（通识，未经本轮来源验证）：
  - 油画：不透明、可见笔触堆叠与画布织纹、暗部深沉、高光厚涂突起（impasto）；古典写实 = 光滑罩染、Rembrandt 三角光、暗背景；印象派 = 断续色点、无线性轮廓、冷暖并置；Sargent 式 = 大笔触「一笔成形」的湿画法、低饱和灰调中的高光。
  - 水彩：透明、白纸作高光、边缘水渍/水花（blooms）、颗粒沉积（granulation）、留白。
  - 水粉（gouache）：不透明、哑光、平整色块、边缘干净，接近「平涂但手绘」。
  - 炭笔/铅笔：单色、纸纹、涂抹与橡皮提亮、排线。
  - 色粉（pastel）：粉质颤动笔触、高饱和、颗粒纸纹、边缘毛糙。
  - 水墨（写意）：留白、墨分五色、宣纸晕染、少数几笔定形；工笔：细劲均匀的墨线勾勒 + 多层薄染（「三矾九染」）、绢/纸本、装饰性设色、无西式明暗。
- 「厚涂 vs 油画」区分（见 KQ8）：厚涂是 CG 对油画塑形逻辑的借用，但通常没有真实画布纹理、颜料厚度与裂纹，色彩更鲜亮、边缘更数码化（柔化/锐化不均），且常混有赛璐璐式干净块面。
- 模型选择（综合）：Midjourney（`--sref`/`--p` + 媒材词）仍是艺术化媒材的首选；Flux/Flux 2 走 LoRA 路线（厚笔触 impasto、水墨 LoRA 成熟度尚可）；GPT-image/Nano Banana 擅长按文字精确指令改媒材并保持人物一致（参考图→「改成水彩」），但绘画「物理真实感」缺乏公开实测；国风人像目前最可靠的是 Flux/F.1 + 专项 LoRA（唐风工笔类），SD1.5 LoRA 不适配写实底模。
- EN/CN 关键词：`oil painting, impasto, visible brushstrokes, canvas texture, Rembrandt lighting, chiaroscuro, classical realism, alla prima, Sargent-style loose brushwork`／`油画, 厚重笔触, 画布纹理, 伦勃朗光, 古典写实`；`watercolor, wet-on-wet, blooms, paper grain, granulation, white space`／`水彩, 湿画法, 水渍, 纸纹, 留白`；`gouache, opaque matte, flat planes`／`水粉, 不透明哑光`；`charcoal sketch, graphite, cross-hatching, smudged`／`炭笔素描, 排线`；`soft pastel, chalky texture`／`色粉`；`Chinese ink wash, sumi-e, xieyi, rice paper bleed, negative space`／`水墨, 写意, 宣纸晕染, 留白`；`gongbi, fine-line brushwork, layered mineral pigments, silk scroll, Tang dynasty court lady`／`工笔, 勾线渲染, 绢本设色, 国风`。

### Gaps
- 没有任何来源对 Midjourney V7、GPT-image、Nano Banana、Seedream、Flux 2、Qwen-Image 的油画/水彩质感做并排实测；上述模型定位全部来自厂商或聚合站的 2026 综述。
- 工笔 vs 写意的中文权威定义页面：配额耗尽前未检索到；上述为通识。
- 水粉、炭笔、色粉在 AI 中的专项 LoRA/模型：无来源。
- Midjourney V7 之后的版本状态（2026-10 是否有 V8）：本轮无来源，不要臆断。

---

## KQ6. 平面/图形端：flat illustration、vector art、企业「Alegria/Corporate Memphis」、pop art、risograph/丝网、海报艺术、极简线稿、pixel art、「sticker」风——视觉线索与 prompt 关键词

### Takeaway
该端的共同特征是：无体积渲染或仅两阶阴影、色块干净、轮廓明确或完全省略、常带印刷/屏幕媒介的「工艺」纹理（网点、riso 颗粒、套印错位、像素格、贴纸白边）。Corporate Memphis（Alegria）源自 2017 Buck 为 Facebook 设计的系统，特征是长而弯曲的四肢、极简面部、非写实肤色、无阴影；risograph 的关键是 2–3 色荧光专色 + 套印错位 + 粗颗粒；sticker 风关键词已固化为「die-cut, thick white border, flat vector, no shadows」；pixel art 靠「8-bit/16-bit、限色板、front-facing/isometric」控制。Midjourney 侧有 Midlibrary（5,500+ 风格、2,800+ `--sref` 码）作为风格字典。

### Cited Findings
**Corporate Memphis / Alegria**
- 起源：2017 年 Facebook 委托 Buck 设计的「Alegria」系统（插画师 Xoana Herrera）；「Memphis」指 1980 年代 Memphis Milano 设计组，「Corporate」指其由 Alegria 复兴并商业普及。 — [Wikipedia (kiwix 镜像): Corporate Memphis](https://kiwix.gnuisnotunix.com/wikipedia_en_all_maxi_2021-12/A/Corporate_Memphis)；[art4d 2025-03](https://art4d.com/en/2025/03/corporate-memphis-a-simple-style-for-corporate)
- 特征：「flat human characters in action, with disproportionate features such as long and bendy limbs」；「bright colors without any blending」；极简几何、可缩放对象、明亮粉彩；「Alegria is a system of design principles that can be copy and pasted to fit any scenario」。 — [shots.net](https://shots.net/news/view/corporate-memphis-the-design-style-that-quietly-took-over-the-internet)；[Branded Agency](https://brandedagency.com/blog/corporate-graphic)；[daisyUI trend](https://trends.daisyui.com/trend/corporate-memphis/)
- 批评：「generic, overused, and attempting to sanitize public perception」。 — [shots.net](https://shots.net/news/view/corporate-memphis-the-design-style-that-quietly-took-over-the-internet)；[Stuyvesant Spectator: Stop copying Facebook](https://stuyspec.com/article/stop-copying-facebook)

**Flat vector（Midjourney）**
- Flat vector「ideal for simple and modern designs, particularly suitable for logos, icons, and infographics」。 — [Friflex Midjourney guide](https://friflex.com/en/blog/design/kak-rabotat-s-midrourney)
- 「flat vector is surprisingly easy to get wrong」；好的 `--sref` 码给 Midjourney「a stronger visual grammar: clearer silhouettes, better color blocking, cleaner compositions」（文章给出 3 个 flat vector sref 码）。 — [Underwood Xie Substack: 3 Flat Vector SREF Codes](https://underwoodxie.substack.com/p/3-flat-vector-sref-codes-for-cleaner)
- 「Flat Design」预设：「modern flat design illustration with clean vectors and bold colors」。 — [Neura Market Midjourney styles directory](https://neura.market/directories/midjourney/styles)
- Midlibrary：非营利教育项目，收录 5,500+ 精选 Midjourney 风格与 2,800+ SREF 码，并出版风格指南。 — [Midlibrary: Inside](https://midlibrary.io/midlibrary/inside)；[Gigazine 2024-01](https://gigazine.net/gsc_news/en/20240121-midlibrary/)

**Risograph / 丝网**
- 定义性特征：「a limited set of soy spot inks (often fluorescent pink and blue), deliberate misregistration where the colour layers do not quite line up, and heavy mottled grain with the paper showing through」。 — [Morphic: Risograph illustration AI images](https://morphic.com/resources/images/risograph-illustration-image)
- Prompt 建议：限 2–3 色专色、halftone dots、grainy paper、slight misregistration；显式写 overprint（如「fluorescent pink over teal blue, slight misregistration offset」）才像手工印刷。 — [Media.io: Gemini AI risograph prompt](https://www.media.io/ai-prompts/gemini-ai-risograph-style-prompt.html)
- 模板关键词：「bold fluorescent spot-color overprinting, visible ink layering, coarse halftone dots, paper grain」+ imperfect registration、ink-density variation。 — [Magic Hour: Riso Print template](https://magichour.ai/templates/details/cmtadidom0601jl0143bt1xue-riso-print)
- 一个社区 `--sref` 风格被描述为 risograph 外观：visible grain、halftone shading、distressed ink、worn edges，关键词「risograph grain」。 — [Patreon: best Midjourney SREF codes](https://www.patreon.com/posts/159949848)

**Sticker 风**
- 「magic words」：`sticker design, die-cut, white background, clean edges, vector style, flat illustration, no shadows`。 — [PromptSpace: AI sticker design prompts 2026](https://www.promptspace.in/blog/ai-sticker-design-prompts-create-cute-custom-stickers-2026)
- 边框写法：「thick white die-cut border that follows its outline」；该模板另加「thin shadow under each sticker」「glossy vinyl finish」（与「no shadows」建议相冲突，取决于要不要实体感）。 — [God of Prompt: Die-Cut Vinyl Sticker Trio](https://godofprompt.ai/prompt-library/die-cut-vinyl-sticker-trio)
- flat vector 写法：「flat vector art style」+ thick outlines、crisp uniform edges。 — [Krea feed 示例](https://www.krea.ai/k2-feed/3d427d51-502c-5675-ad69-2c76eac56acb)

**Pixel art**
- 核心词：`pixel art`, `pixel style`, `8-bit style`, `video game style`, `8-bit pixel art`；更平滑用 `16-bit`/`24-bit`；限色板 `4-color palette`、`NES color palette`；视角词 `front-facing`、`isometric`。 — [OpenArt: SD prompts for pixel art](https://openart.ai/blog/post/stable-diffusion-prompts-for-pixel-art)；[QuillBot: pixel art with AI](https://quillbot.com/blog/image-tools/ai-pixel-art-generator/)；[Stockimg.ai](https://stockimg.ai/blog/design-and-creativity/how-to-generate-pixel-art-with-ai)
- Adobe Firefly 提供 pixel art generator 功能页；有「50 Midjourney Pixel Art Prompts」合集。 — [Adobe Firefly](https://www.adobe.com/products/firefly/features/pixel-art-generator.html)；[Notion 合集](https://excited-edge-f5d.notion.site/50-Midjourney-Pixel-Art-Prompts-d4d15718c0514637853903ba7456d27c)

### Inferences
- 快速视觉检查：flat illustration = 无渐变或仅微渐变、2 阶阴影、几何化造型；vector = 边缘绝对锐利、无纹理、可缩放感；Corporate Memphis = 上述 + 弯曲长肢 + 蓝/紫/橙非写实肤色 + 无面部细节；pop art = 粗黑线 + 网点 + 高饱和原色 + 印刷感；risograph = 颗粒 + 2–3 荧光色 + 套印错位 + 纸色透出；poster art（通识）= 大块面 + 强对比 + 常有文字排版位；minimal line art（通识）= 单线/连续线、无填色或单点色；pixel art = 可见像素格、限色板、无抗锯齿；sticker = 白色描边 + 透明/纯色背景 + 轻微光泽。
- 注意 AI 模型的常见失败：像素艺术的像素格不一致（需后期量化）；sticker 白边不闭合；flat vector 混入体积阴影（故社区依赖 `--sref` 与负面词「no 3D render」）。
- CN 关键词：`扁平插画`, `矢量插画`, `扁平人物（企业风/Alegria 风）`, `波普艺术`, `孔版印刷/Riso 风`, `丝网印刷`, `海报风`, `极简线条画/一笔画`, `像素画/8-bit`, `贴纸风/白边贴纸`。

### Gaps
- Midlibrary 上 flat/vector/risograph 分类页本身未能抓取（仅有第三方 sref 码文章）。
- poster art 与 minimal line art 的专项来源：配额耗尽前未检索。
- 来源多为 prompt 模板/厂商页，缺少设计史权威定义（Corporate Memphis 除外）。

---

## KQ7. 概念设计人像（character concept art、character sheet/turnaround、「ArtStation style」）——定义性特征

### Takeaway
「Concept art」在 AI prompt 中指游戏/影视前期的职业插画风：厚涂数字绘画、焦点细节 + 松散边缘、中性或戏剧性打光、常配多视角/道具分解。「trending on artstation」是 SD1.x 时代的质量咒语，并非真实趋势信号。Character sheet/turnaround 的有效 prompt 要显式写布局（front/side/back、orthographic、consistent lighting、neutral A-pose），且各视角一致性仍需迭代。

### Cited Findings
- 概念设计风格定义：「professional illustration style used in game and film production, featuring detailed environments, characters, and props with painterly digital techniques」。 — [gptprompts.ai Concept Art style guide](https://gptprompts.ai/ai-image-styles/concept-art)
- Midjourney 建议追加「concept art, digital painting, matte painting, artstation, detailed」。 — [Luma Labs: AI art prompts](https://lumalabs.ai/news/ai-art-prompts)
- SD prompt 数据集中大量出现「trending on artstation」「highly detailed」「digital painting」组合（质量 tag 习惯而非真实趋势）。 — [HF dataset gokaygokay/prompt_description_stable_diffusion_1k](https://huggingface.co:443/datasets/gokaygokay/prompt_description_stable_diffusion_1k)；[HF dataset diffusiondb-prompt-upscale](https://huggingface.co/datasets/adams-story/diffusiondb-prompt-upscale/viewer/default/train?p=25)
- 用途决定渲染：精细厚涂肖像适合角色卡封面，但缩成 VTT token 会不可读；小尺寸需强剪影与清晰色块。 — [NoteGPT: How to create a D&D character in 2026](https://notegpt.io/guides/how-to-create-a-dd-character-in-2026)
- 角色肖像 prompt 公式：art style、角色身份/职业、外貌、表情与性格、服装/护甲、装备、光线、背景、构图。 — [zsky.ai: AI character portraits guide](https://zsky.ai/blog/how-to-create-ai-character-portraits.html)
- Turnaround 写法：「character design sheet with multiple views (Front, Side, and Back views), consistent lighting across all views」；加「orthographic camera」帮助对齐；中性 A-pose 便于 rigging 参考；视角会漂移需迭代，检查比例、五官、服装细节、姿势对齐；也可从单图逐视角编辑生成。 — [Scenario Help: Generate Character Turnarounds](https://help.scenario.com/en/articles/generate-character-turnarounds/)；[Scenario blog](https://www.scenario.com/blog/generate-character-turnarounds-scenario)；[FlexClip turnaround tool](https://www.flexclip.com/tools/ai-character-turnaround-sheet-generator/)；[BudgetPixel turnaround](https://budgetpixel.com/features/character-turnaround-generator)
- Dreamina 教程页提到用「GPT Image 2」做 turnaround sheet（厂商页；表明 2026 年 OpenAI 图像模型已迭代到此命名，细节未核实）。 — [Dreamina: GPT Image 2 for character turnaround sheets](https://dreamina.capcut.com/resource/gpt-image-2-for-character-turnaround-sheets)
- 社区有专门的「character design sheet」skill/模板。 — [claudeskills.info character-design-sheet](https://claudeskills.info/skills/inference-sh/skills/character-design-sheet/)

### Inferences
- 概念设计人像与「半写实插画」的区别（通识）：concept art 强调设计可读性（剪影、材质分区、功能性道具）、中性背景或色卡、常见 3/4 半身 + 道具标注，笔触在非焦点区域刻意松散（Craig Mullins 传统）；而 Artgerm/WLOP 式半写实追求整幅画面的完成度与氛围。
- EN 关键词：`character concept art, character sheet, turnaround, front/side/back view, orthographic, neutral A-pose, consistent lighting, costume breakdown, prop callouts, painterly digital painting, matte painting, ArtStation`；CN：`角色概念设计`, `三视图/角色设定图`, `立绘`, `概念厚涂`, `游戏美宣`。
- 「trending on artstation / 8k / masterpiece」类咒语对 SD1.x（CLIP）有效，对 Flux/GPT-image/Nano Banana 这类自然语言模型基本无意义（通识，推断自模型架构差异，未经来源验证）。

### Gaps
- ArtStation 当前真实的概念设计趋势：无来源。
- 「GPT Image 2」的官方发布信息与能力：仅见厂商页提及，未核实。

---

## KQ8. 常见混淆（半写实 vs 3D 渲染；厚涂 vs 油画；韩漫 vs 日漫 等）与快速视觉判别

### Takeaway
来源直接讨论的混淆有两处：(a) SD 社区试图命中「半写实」时模型会滑向油画或照片两端（HF 论坛）；(b) 日韩画风边界日益模糊（B 站）、厚涂与写实/二次元边界难划（萌娘百科）、「美系/日系」只是地域印象标签。其余判别法为综合推断。

### Cited Findings
- 用户试用大量热门 Civitai LoRA 后「either get an oil painting result at one extreme, or a photorealistic result at the other extreme」，目标风格「would be called 2.5D or 2.8D」。 — [Hugging Face Discuss](https://discuss.huggingface.co/t/stable-diffusion-cant-figure-out-this-style/112706)
- 「厚涂与写实、二次元之间的界限有时也很难划清」；「美系」「日系」标签与画师国籍无关、无官方定义。 — [萌娘百科·厚涂](https://mzh.moegirl.org.cn/%E5%8E%9A%E6%B6%82)
- 「日风与韩风的界限近年越来越模糊，两者互相借鉴的情况很常见」。 — [Bilibili 专栏](https://www.bilibili.com/opus/337641994918252136)
- 漫画封面模板显式加负面词「no 3D render」以防模型滑向 CG。 — [Carat.im comic cover (fr)](https://carat.im/fr/prompt-gallery/comic-book-cover)
- 曾争议归属的「画面干净、色块整洁但笔触接近厚涂」插画，今归入厚涂。 — [萌娘百科·厚涂](https://zh.moegirl.org.cn/%E5%8E%9A%E6%B6%82)

### Inferences
以下判别法为综合推断（通识，未经本轮来源验证），供报告以「实用检查表」形式呈现：
- **半写实 2D vs 3D 渲染**：看①皮肤——3D 常有均匀次表面散射的「蜡/塑料」感与完全一致的高光模型，2D 厚涂皮肤高光随笔触断续、有色相跳变；②边缘——3D 轮廓处处锐利且几何正确，2D 存在刻意的软边/丢失边（lost edges）；③头发——3D 为成束几何体与一致各向异性高光，2D 为笔触走向的发丝与「块状」归纳；④背景与景深——3D 景深模糊均匀，2D 多为笔触弱化；⑤光照一致性——3D 全局光完全自洽，2D 常有「为了好看」的不合理补光；⑥若存在肉眼可见的笔触纹理或画布纹理即为 2D。
- **厚涂（CG）vs 油画**：油画有画布织纹、颜料厚度与反光、裂纹/漫反射不均、色彩受颜料限制偏灰；厚涂颜色更鲜、过渡更数码化、常掺赛璐璐式干净块面、无颜料物理厚度。AI 中加 `canvas texture, impasto, varnish sheen` 会把厚涂推向油画。
- **厚涂 vs 伪厚涂 vs 赛璐璐**：见 KQ1 四步检查（线稿连续性、阴影边缘硬软、高光形态、色阶数）。
- **韩漫 vs 日漫**：眼睛大小/鼻子完整度/身体比例/色彩饱和/全彩竖版（见 KQ3）。
- **韩系半写实 vs 西方半写实**：面部理想化模板统一度、线稿是否保留、题材（都市时尚 vs 奇幻/漫画 IP）。
- **Ligne claire vs 美式漫画**：阴影几乎不存在 + 等粗线 + 无排线 → ligne claire；网点 + 粗细变化墨线 + 投影 → 美式。
- **Noir ink vs 黑白素描**：noir 无灰阶（两值）；素描有连续灰阶与纸纹。
- **Flat vector vs Corporate Memphis**：后者多弯曲长肢与非写实肤色、极简面部；前者更广义。
- **Risograph vs pop art 网点**：riso 有颗粒、套印错位、荧光专色、纸色透出；pop art 网点规则、黑线粗、原色。
- **Pixel art vs 低分辩率图**：pixel art 像素格对齐网格、限色板、无抗锯齿；AI 失败品常有不等大像素。

### Gaps
- 关于「AI 图像为何看起来像 3D 渲染（plastic skin）」的来源：配额耗尽前未检索到。
- 没有任何来源提供「厚涂 vs 油画」的直接对比定义。

---

## 附：按子风格汇总的 prompt 关键词表（EN / CN）与模型/LoRA 指引（综合，来源见各 KQ；标 * 者为通识推断）

| 子风格 | EN 关键词（来源内出现者加粗） | CN 关键词 | 2025–2026 模型/LoRA 线索 |
|---|---|---|---|
| 半写实（western semi-realism） | **semi-realistic**, painterly digital illustration, soft blended shading, no hard outlines*, glowing rim light*, naturalistic proportions | 半写实, 厚涂人像, 欧美半写实 | Flux LoRA「RBStyle」(Civitai 1461162)、ZIT LoRA「Visionarys Semi-Realism」(2311515)；Midjourney `--sref`；注意易滑向油画/照片两端 |
| 厚涂（painterly） | digital painting, **thick paint**, visible brushstrokes, **impasto**, blended brushwork, lost edges* | 厚涂, 厚涂幻想风, 笔触感 | 「Zavy's Rough Paint (Flux)」(impasto)、「Painted World」(SDXL/Pony) |
| 伪厚涂（cel+painterly） | line art with soft painterly shading*, semi-cel*, anime-realism hybrid | 伪厚涂/半厚涂, 有线稿厚涂 | 「Zavy's Detail Anime/Digital Realism (Flux)」(线稿+写实明暗)；2.5D checkpoints (Dark Sushi 2.5D 等) |
| 平涂/赛璐璐 | **cel shading**, flat color, clean line art, two-tone shadows* | 平涂, 赛璐璐 | （日系范围，仅划界） |
| 韩系网漫 | Korean **manhwa** art style, **webtoon**, clean lines, expressive faces, full color, soft shading* | 韩漫风, 韩系半写实, 韩式厚涂 | Tusiart「SOLO LEVELING (style)」SD1.5（质量自述一般）；专用 manhwa 生成器 |
| 美式漫画 | **bold black ink outlines**, **halftone dots**, **flat saturated primary colors**, **action lines**, newsprint texture, 1960s pop art | 美漫风, 墨线平涂, 网点, 波普 | HF「RealisticComicbookStyle」(Flux) |
| Painted comic realism* | painted comic cover, gouache, photorealistic superhero, Rockwell lighting | 实画漫画写实 | 无专项来源 |
| Ligne claire | **ligne claire**, **clear line**, uniform line weight, **no hatching**, minimal shadows, flat colors | 欧漫清线派 | 无专项来源 |
| Noir ink | **stark black-and-white contrast**, **bold linework**, **monochrome**, no midtones, spot color red | 黑白高反差墨绘 | Tensor.Art「Graphic Noir: Sin City Style v2.0」(Flux)；SD1.5 LoRA 权重 0.5–0.6 |
| 油画 | oil painting, **impasto**, **expressive brushstrokes**, canvas texture, Rembrandt lighting*, chiaroscuro* | 油画, 古典写实, 伦勃朗光 | Midjourney 为艺术方向首选（综述）；无质感实测 |
| 水彩 | watercolor, **transparency**, **blooms**, **paper-grain texture**, wet-on-wet* | 水彩, 水渍, 留白 | 同上 |
| 水墨/工笔 | Chinese ink wash, sumi-e*, rice paper*, gongbi*, fine-line, Tang dynasty* | 水墨, 写意, 工笔, 国风, 唐风 | Flux + Taomitown 水墨 LoRA (0.8)；F.1 +「唐风工笔娃娃_v1.0」(1.0)；SD1.5「inkColor·墨彩」(0.5–0.8，不适配真人底模) |
| Flat / vector | **flat vector**, clean vectors, bold colors, clear silhouettes, color blocking | 扁平插画, 矢量 | Midjourney flat-vector `--sref` 码（Underwood Xie） |
| Corporate Memphis | **Corporate Memphis**, Alegria style, **long bendy limbs**, minimal faces, bright pastel, no blending | 企业扁平人物风 | 无专项来源 |
| Risograph | **risograph**, **spot inks fluorescent pink/blue**, **misregistration**, **mottled grain**, halftone, overprint | Riso 孔版风, 丝网 | 社区 `--sref`；Gemini/Magic Hour 模板 |
| Sticker | **sticker design, die-cut, white background, clean edges, vector style, flat illustration, no shadows**, thick white border, glossy vinyl | 贴纸风, 白边贴纸 | 通用模型即可 |
| Pixel art | **pixel art, 8-bit, 16-bit, NES color palette, isometric, front-facing** | 像素画 | Firefly pixel art；Midjourney prompt 合集 |
| Concept art | **concept art, digital painting, matte painting, artstation**, character sheet, **front/side/back views, orthographic, consistent lighting**, A-pose | 角色概念设计, 三视图, 立绘 | Scenario 等 turnaround 工具；GPT Image 2（厂商页提及） |
