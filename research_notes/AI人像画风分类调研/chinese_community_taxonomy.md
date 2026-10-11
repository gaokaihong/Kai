# 中文AI绘画社区与平台对非二次元人像画风（人像画风）的分类与命名

> **方法与局限说明（请报告撰写者务必阅读）**
> - 调研日期：2026-10-11。目标：梳理中文 AI 文生图社区/平台中用于描述**非二次元人像/角色**画风的词汇、平台风格面板的组织方式，以及中文术语 ↔ 英文提示词 ↔ 视觉效果的映射。
> - **技术限制**：本会话的出站代理按组织策略拒绝了所有中国大陆托管域名（zhihu.com、csdn.net、qq.com、liblib.art、tusi.art、cloud.tencent.com、jimeng.jianying.com、aliyun.com、uisdc.com、163.com 等均返回 CONNECT 403），且共享的 WebSearch 配额在第 3 轮检索后用尽。因此**所有引用均基于搜索引擎返回的页面摘要，而非全文阅读**。摘要中逐字引用的提示词已原样保留；凡摘要未明确归属到某一 URL 的说法，均在条目中标注「摘要归纳」或移入「推断/缺口」。
> - **时效标注**：2022–2024 年的资料（主要是 Stable Diffusion 1.5/SDXL 时代的模型分类、妙鸭相机、通义万相首发版、混元旧风格表）在条目中以 **[2023]**、**[2024]** 等标记，可能已过时；2025–2026 年的资料（即梦 3.0/4.0、Seedream 4.0、Nano Banana 手办化、混元图像 3.0、可图 2.0）以 **[2025]**、**[2026]** 标记。
> - 范围：排除二次元/日系动漫/漫画画风；仅在 2.5D、半写实、3D 二次元、韩系等「边界类目」处说明其与动漫的分界。

---

## 问题一：中文 AI 社区用哪些术语描述人像画风，各自如何定义，并与哪些英文提示词搭配？

### Takeaway
中文社区对人像画风的命名是三套词汇的叠加：(1) 来自传统板绘教学的技法词（厚涂/伪厚涂/平涂/赛璐璐），(2) 来自 Stable Diffusion 模型社区的「真实感梯度」词（真人/写实/真实系 → 半写实/2.5D → 二次元），(3) 来自商业设计与潮玩圈的产品化风格词（盲盒/潮玩/手办/C4D/OC渲染/皮克斯/国风/新中式/AI写真/电影感）。英文提示词方面，中文用户通常直接套用 `3D render`、`C4D`、`Octane render`、`impasto`、`Chinese ink wash painting`、`gongbi`、`manhwa`、`cinematic lighting`、`Kodak Portra 400` 等词，并常把中文风格词与英文渲染器/相机词混写在同一条提示词中。

### Cited Findings

**（A）真人 / 写实 / 真实系 / 超写实 / 照片级**
- 在 SD 模型分类中，「真实系」被概括为对现实世界还原度强的模型，代表如 Realistic Vision 一类；与之并列的是「二次元」（偏漫画插画、笔触感明显）和居中的「2.5D」 **[2024]** — [CSDN：关于AI绘画Stable diffusion的各种模型](https://blog.csdn.net/cxyxx12/article/details/139146436)
- majicMIX 被称为「国内名气比较大的一款真人写实系模型」 **[2024]** — [知乎：【AIGC系列】AI绘画模型类型介绍](https://zhuanlan.zhihu.com/p/682196143)
- 吐司 TusiArt 官网标签把「真实」与「真人」作为两个独立标签并列（另有「摄影」标签），说明社区把「真实（渲染质感）」和「真人（主体类型）」区分开 — [吐司 Tusi.Art](https://tusi.art/)
- LiblibAI 上有命名为「Z-Image-真人拍摄，写实风格」的 LoRA，体现当前（Z-Image 基座，2025–2026）社区仍以「真人拍摄 + 写实风格」作为真人向 LoRA 的标准命名 — [LiblibAI 模型页](https://www.liblib.art/modelinfo/39dee1b175d24d3f9f61ca415bc7f207?from=personal_page)
- 腾讯混元「文生图轻量版」预置风格表中有编号 401「通用写实风格」，标准版预置风格含「写实」「3D 渲染」「水墨画」「新年剪纸画」等 — [腾讯云：文生图轻量版风格列表](https://cloud.tencent.com.cn/document/product/1729/108992)；[腾讯云：混元生图产品页](https://cloud.tencent.cn/product/aiart)
- 百度文心一格官方「AI作画-高级版使用指南」把「写实风格」列为风格关键词之一（并列：古风、二次元、浮世绘、未来主义、像素风格、水彩画、油画、卡通画） — [百度AI：AI作画-高级版使用指南](https://ai.baidu.com/ai-doc/NLP/4libyluzs)
- 即梦官网示例提示词使用「超写实插画」「电影质感」「3D游戏人物风格」「文艺复兴风格」等描述方式 — [即梦AI官网](https://jimeng.jianying.com/)
- 可灵 AI 官方文档页的图片示例以写实摄影参数为主，示例片段为「柯达Portra 400，f/8光圈，清晰聚焦，原始风格，绝对写实」 — [可灵AI 文档](https://klingai.com/docs-v2)
- 一篇 **[2026]** 知乎文章认为「电影感」「大片感」「高级感」等词已太泛，建议拆成具体质感词，如「真实皮肤纹理，自然毛孔细节，不过度磨皮」等人像细节描述 — [知乎：“电影感”已经烂大街了！2026年AI视频更高级的质感词在这](https://zhuanlan.zhihu.com/p/2035456872304657933)
- 英文资料对 photorealism 与 hyperrealism 的区分：前者忠实还原照片所见，后者放大细节使画面比现实更完美；皮肤上，超写实呈现「完美细节」，照片级写实保留自然光下的瑕疵 — [ArchiVinci: What Is Photorealism?](https://www.archivinci.com/blogs/photorealism-and-how-ai-shapes-it)
- 英文提示词指南 **[2026]** 指出「8K」「hyperrealistic」「ultra-detailed」「masterpiece」等词常把模型推向过度锐化、过饱和的「假」渲染，建议改写相机机身 + 焦段 + 光线类型（摘要归纳，具体措辞未经全文核实） — [ArtSmart: Photorealistic AI Image Prompts 2026](https://artsmart.ai/blog/ai-image-prompts-photorealistic/)
- 一款面向「小红书式日常照片质感」的 Flux LoRA 触发词为 `xhs`，被描述为「极度真实，自然日常，直出图集」 **[2024]** — [CSDN：超真实的小红书AI绘图Flux大模型](https://blog.csdn.net/cxyxx12/article/details/142631089)

**（B）半写实 / 半真人 / 2.5D（边界类目）**
- 「2.5D」被描述为质感接近建模软件或 3D 游戏、CG 动画渲染图的风格，位于真实系与二次元之间 **[2024]** — [CSDN：关于AI绘画Stable diffusion的各种模型](https://blog.csdn.net/cxyxx12/article/details/139146436)
- 另一篇把 2.5D 解释为「半 3D」，即加入部分立体元素但并非完整 3D **[2024]** — [CSDN：ai绘画大模型介绍](https://blog.csdn.net/2401_85826318/article/details/139819550)
- 知乎有专文把「半写实/2.5D」并列为同一类风格来推荐模型，说明两个词在社区中常混用 **[2023]** — [知乎：给大家推荐一个半写实/2.5D 风格之间比较好的AI绘画模型](https://zhuanlan.zhihu.com/p/630671902)
- GuoFeng3（国风3，作者 xiaolxl）在模型盘点中被归类为「2.5D 模型」，适合古风人物和服饰 **[2024]** — [CSDN：StableDiffusion 大模型主流的有哪些？](https://blog.csdn.net/A2421417624/article/details/139176062)
- XXMix_9realistic 在多篇 SD 模型盘点中被称为「2.5D 人物模型，有油画质感」；majicMIX 则归「真实系」——同一模型在不同来源中可能被归入不同类别（摘要归纳） **[2023–2024]** — [CSDN：关于AI绘画Stable diffusion的各种模型](https://blog.csdn.net/cxyxx12/article/details/139146436)；[知乎：AI绘画模型推荐第二弹](https://zhuanlan.zhihu.com/p/647961589)
- 吐司官网与中文站均把「2.5D」设为一级标签/频道，与「真实」「动漫」「国风」并列 — [吐司 Tusi.Art](https://tusi.art/)；[吐司中文站 tusi.cn](https://tusi.cn/)
- 数字人行业的风格分类中出现「3D 半写实」一档，位于「3D 写实」与「3D 卡通」之间 — [InfoQ：火爆出圈，站上风口的数字人到底是什么“人”？](https://www.infoq.cn/article/svhlgvhggpvlrfqlckug)

**（C）3D渲染 / 3D卡通 / C4D风 / Blender风 / OC渲染**
- 即梦提示词整理中的 3D 类写法：「3D 渲染，C4D 风格，柔光材质，可爱卡通角色，商业插画质感」 **[2026]** — [知乎：即梦 AI 提示词大全：人物、场景、风格](https://zhuanlan.zhihu.com/p/2071960585068139511)
- 小红书「潮玩盲盒」风格教程把提示词拆为「风格词、材质词、渲染词、画质词、类型词」，常用词包括「迪士尼、泡泡玛特、皮克斯风格」以及「盲盒」「3D渲染」「OC渲染」「ip设计」 — [知乎：爆款咒语！小红书“潮玩盲盒”风格ai绘画教程！](https://zhuanlan.zhihu.com/p/43734357)
- 盲盒手办风 3D Q 版案例的描述：「采用C4D和Octane渲染，模拟盲盒手办的高光泽粘土质感」 — [可我AI：盲盒手办风3D Q版魔法学徒男孩：C4D极简全身渲染图](https://www.krwoo.com/mang-he-shou-ban-feng-3dq-ban-mo-fa-xue-tu-nan-hai-c4d-ji-jian-quan-shen-xuan-ran-tu/)
- 「41种AI绘画风格」系列文章把「3D渲染风格」归入「现代数字艺术」大类，示例偏材质与光照描述（如 PBR 材质、HDR 环境光） **[2025]** — [知乎：41种AI绘画风格提示词+实战案例](https://zhuanlan.zhihu.com/p/1920952360831813473)；[镜像页](https://book.huanzhou.art/books/agi/page/41ai)
- 腾讯混元旧版风格表「动漫艺术类」含「3D风格」；轻量版编号 116 为「3D」；混元图像 3.0 第三方指南把「3D 渲染」列为四大类之一（另三类：摄影写实、插画设计、艺术创作） **[2024/2025]** — [腾讯云：混元生图风格列表](https://cloud.tencent.com/document/product/1729/105846)；[博客园：腾讯混元图像3.0完全指南](https://www.cnblogs.com/sing1ee/p/19116886/hunyuan-image-3-guide)
- 通义万相 **[2023]** 首发时的预设风格之一为「3D卡通」 — [腾讯新闻：阿里云AI绘画创作大模型来了！我们测了测“通义万相”](https://news.qq.com/rain/a/20230707A07WTQ00)
- 字节 Seedream 4.0 官方博客称可在 30 多种艺术风格间切换，并能把 2D 草图转为 3D 风格、从单张人像生成不同风格的角色图 **[2025]** — [ByteDance Seed：Seedream 4.0 图像创作模型正式发布](https://seed.bytedance.com/en/blog/%E4%B8%8D%E6%AD%A2%E4%BC%9A-%E7%94%BB-%E6%9B%B4%E4%BC%9A-%E6%83%B3-seedream-4-0-%E5%9B%BE%E5%83%8F%E5%88%9B%E4%BD%9C%E6%A8%A1%E5%9E%8B%E6%AD%A3%E5%BC%8F%E5%8F%91%E5%B8%83)

**（D）皮克斯风 / 迪士尼风 / 梦工厂风**
- 画风指南系列对三者的区分：皮克斯=「3D动画视觉标准，以先进的渲染技术、圆润可爱的角色和情感化叙事闻名」；迪士尼（经典）=手绘 2D、鲜艳饱和色、清晰轮廓线、柔和渐变阴影、戏剧化表情；梦工厂=「融合2D和3D的美学，以大胆的色彩和图形化表现闻名」、夸张化、高对比、动态肢体 **[2025]** — [知乎：41种AI绘画风格提示词+实战案例](https://zhuanlan.zhihu.com/p/1920952360831813473)；[一起学AI：AI绘画风格全指南：50+画风提示词](https://ai.meiweihui.cn/1002/ai%E7%BB%98%E7%94%BB%E9%A3%8E%E6%A0%BC%E5%85%A8%E6%8C%87%E5%8D%97%EF%BC%9A50%E7%94%BB%E9%A3%8E%E6%8F%90%E7%A4%BA%E8%AF%8D%E5%AE%9E%E6%88%98%E6%A1%88%E4%BE%8B%EF%BC%8C%E8%A7%A3%E9%94%81%E4%BD%A0/)
- 即梦被用于「3D卡通皮克斯风格」人物叙事创作（《木兰辞》案例，配合 DeepSeek 写提示词） **[2025]** — [知乎：DeepSeek + 即梦AI，融合打造3D卡通皮克斯风格《木兰辞》](https://zhuanlan.zhihu.com/p/27693228552)
- 第三方导航站称可图 AI 含「皮克斯风格、卡通盲盒、动漫3D、新海诚、怀旧动漫、电子游戏、水彩插画、莫奈油画、高清写实」等风格（**可靠性低**，且可能早于当前版本） — [aig123：可图大模型](https://www.aig123.com/sites/2893.html)

**（E）厚涂 / 伪厚涂（半厚涂、日系厚涂）/ 平涂（薄涂）/ 赛璐璐**
- 平涂也叫薄涂；赛璐璐是平涂上色中最常见的一种；线条结构清晰、色块关系切割明确、先线稿再铺色 — [蓝铅笔：如何区分平涂厚涂半厚涂](https://www.lanqb.com/graphic/1742)
- 厚涂源自油画技法；数字绘画中常把「写实立体的绘画风格」叫厚涂；以古典写实绘画为原理，颜色层层堆叠，通常不画线稿，外轮廓看不到明显线条 — [蓝铅笔：如何区分平涂厚涂半厚涂](https://www.lanqb.com/graphic/1742)；[知乎：“萌新”如何选择和把控“画风”](https://zhuanlan.zhihu.com/p/373534639)
- 半厚涂（伪厚涂）介于平涂与厚涂之间：比平涂用色更丰富、立体感更明显，但没有厚涂那样写实的结构表达，用色更艳丽，是二次元中常见的风格 — [轻微课：平涂、厚涂、伪厚涂，这几种绘画技法的区别](https://www.qingwk.com/article/detail-54887.html)
- 伪厚涂也称「日系厚涂」，在平涂基础上细化过渡而不是简单的阴影「二分法」，通常保留线稿但线稿作用减弱；区分关键有二：成品是否有清晰线稿、明暗过渡是平滑还是边缘清晰 — [知乎：平涂、厚涂、伪厚涂、赛璐璐，到底有什么区别？](https://zhuanlan.zhihu.com/p/500536943)
- 赛璐璐源于动画行业的赛璐珞胶片，是「极端的平涂」，图层多、色块分明、明暗关系明显，常用于日系动画 — [轻微课：什么是日系赛璐璐风格？](https://www.qingwk.com/article/detail-12015.html)；[知乎：厚涂、平涂、赛璐璐都是什么鬼？](https://zhuanlan.zhihu.com/p/139285596)
- 有文章指出平涂和厚涂的定义并非泾渭分明，厚涂也不仅适用于写实项目 — [知乎：插画的平涂、厚涂、半厚涂等各种风格画法有哪些区别？](https://zhuanlan.zhihu.com/p/99763013)；[知乎：插画喵说插画风格的区别](https://zhuanlan.zhihu.com/p/544546706)
- 「厚涂」的标准英译为 **impasto**；台湾《艺术与建筑索引典》以 impasto 为首选词，impasto painting、pastose painting 为变体 — [AAT-Taiwan 藝術與建築索引典：厚塗](https://aat.teldap.tw/AATFullDisplay/300053368)；[海词词典：impasto](https://dict.cn/impasto)
- AI 提示词用法：以 `impasto` 为核心词，配合 `textured brushstrokes`、`visible brushwork`（笔触痕迹）、`heavy texture`、`raised paint texture`（立体厚度）、`oil paint texture`、`palette knife marks`（油彩/刮刀）；可写 `impasto oil painting in the style of Van Gogh`；单独 `thick paint` 不足以指代该技法 — [AIGC.cn：厚涂，从画布堆叠到AI画笔下的魔力纹理关键词](https://www.aigc.cn/96592.html)；[知乎：AI绘图每日一词｜Impasto 厚涂](https://zhuanlan.zhihu.com/p/644829533)

**（F）盲盒风 / 潮玩风 / 手办风**
- 「潮玩盲盒」风格提示词构成见上（C）；核心词：泡泡玛特、盲盒、3D渲染、OC渲染、ip设计 — [知乎：小红书“潮玩盲盒”风格ai绘画教程](https://zhuanlan.zhihu.com/p/43734357)
- LiblibAI 上有基于 revAnimated 的 Checkpoint「3D超萌IP形象设计|盲盒」，描述为对提示词较敏感、可生成人物与动物的立体 IP 形象 **[2023–2024, SD1.5 时代]** — [LiblibAI 模型页](https://www.liblib.art/modelinfo/fe8a50878bed444d9049b079b466ea1c)
- **[2025]** Nano Banana（Gemini 2.5 Flash Image）引发「手办化」热潮，经典短提示词：`turn this photo into a character figure. Behind it, place a box with the character's image printed on it, and a computer showing the Blender modeling process on its screen. In front of the box, add a round plastic base with the character figure standing on it.` — [知乎：Nano Banana太好玩了!附上提示词](https://zhuanlan.zhihu.com/p/1943739237913584104)
- **[2025]** 1/7 比例模板：`Use the nano-banana model to create a 1/7 scale commercialized figure of the character in the illustration, in a realistic style and environment. Place the figure on a computer desk, using a circular transparent acrylic base without any text.` — [博客园：Nano-Banana免费使用指南：一键生成专属3D手办](https://www.cnblogs.com/yfceshi/p/19111963)
- 真人手办做法：直接上传一张全身照；若要还原动漫角色则同时上传真人照与角色图并要求「让图1角色完全像图2」 **[2025]** — [搜狐：手把手教你Nano Banana的10种玩法](https://www.sohu.com/a/932837854_99954671)；[知乎同文](https://zhuanlan.zhihu.com/p/1948350988156133870)
- **[2026]** 站酷「Banana2 50 个人像玩法」中有「女性像拿钥匙扣一样手中拿着一个自己的小型3D卡通版本」的玩法 — [站酷：全网最全，Banana2 50个炸裂人像玩法大合集](https://www.zcool.com.cn/article/ZMTcxNDcyOA==.html)
- 另有 Nano Banana 手办场景提示词指南（角色→完整产品展示） — [Apiyi：Nano Banana 手办场景生成神级提示词](https://help.apiyi.com/nano-banana-character-figure-prompt-guide-creative-scene-generation.html)；[B站专栏：Nano Banana 最新5大类 20+创意提示词](http://www.bilibili.com/read/cv42961374/)

**（G）黏土风 / 毛毡风 / 羊毛毡 / 定格动画**
- 「羊毛毡 3D」转绘提示词的思路：把画面变成柔软、带绒毛质感的手工微缩场景，边缘圆润、色调温暖、背景浅景深（该文整理 10 组转绘风格，从梵高油画到国潮剪纸） **[2026]** — [知乎：承包你的朋友圈！10种AI转绘风格提示词](https://zhuanlan.zhihu.com/p/2050679127087362160)
- 墨图 AI 的头像模板库含「照片变卡通 · 黏土定格动画（头像 / 短视频封面）」 — [墨图AI：头像、自拍 AI 提示词 75 个中文模板](https://www.motuart.com/prompts/avatar)
- 灵图 AI 提供的羊毛毡英文关键词：`wool texture`、`needle felt`、`wool needle felting`（以物件/场景为主，非人像） — [灵图AI：羊毛毡与3D渲染](https://www.lingvisions.com/news/433)；[灵图AI：羊毛毡3D风格场景](https://www.lingvisions.com/news/219)
- 即梦 4.0 提示词速查表的风格词含「Q版、像素、水墨、美漫、定格动画」，材质词含「毛绒、金属、玻璃、大理石、皮革」 **[2025]** — [苏米客：即梦4.0提示词手册快速上手版](https://www.xmsumi.com/detail/1550)

**（H）国风 / 新中式 / 古风 / 工笔 / 水墨 / 国潮**
- 即梦提示词整理中的国风写法：「国风水墨，远山近水，留白，墨色晕染，意境悠远」；人像：「白衣仙子，长发飘逸……水墨淡彩风格，柔光，国风仙侠」 **[2026]** — [知乎：即梦 AI 提示词大全](https://zhuanlan.zhihu.com/p/2071960585068139511)
- 画风指南的中英对照：中国水墨风 = `Chinese Ink Wash Painting`；敦煌壁画风 = `Dunhuang Murals`；41 种版本把两者归入「文化地域」大类，示例「中国水墨风格，群山夕阳」 **[2025]** — [一起学AI：50+画风提示词](https://ai.meiweihui.cn/1002/ai%E7%BB%98%E7%94%BB%E9%A3%8E%E6%A0%BC%E5%85%A8%E6%8C%87%E5%8D%97%EF%BC%9A50%E7%94%BB%E9%A3%8E%E6%8F%90%E7%A4%BA%E8%AF%8D%E5%AE%9E%E6%88%98%E6%A1%88%E4%BE%8B%EF%BC%8C%E8%A7%A3%E9%94%81%E4%BD%A0/)；[知乎：41种AI绘画风格](https://zhuanlan.zhihu.com/p/1920952360831813473)
- 腾讯混元旧版风格表区分「中国风」「国潮」「水墨」（动漫艺术类）与「剪纸」「刺绣」「皮影」「敦煌壁画」「版画」（通用艺术类） **[2024]** — [腾讯云：混元生图风格列表](https://cloud.tencent.com/document/product/1729/105846)
- 百度文心一格官方关键词用「古风」；通义万相 **[2023]** 用「中国画」；吐司标签用「汉服」「国风」「武侠」 — [百度AI作画指南](https://ai.baidu.com/ai-doc/NLP/4libyluzs)；[腾讯新闻：通义万相实测](https://news.qq.com/rain/a/20230707A07WTQ00)；[吐司 Tusi.Art](https://tusi.art/)
- LiblibAI 有「国风-中国武侠风|传奇色彩」LoRA — [LiblibAI 模型页](https://www.liblib.art/modelinfo/a8f5e203244d4fdcabd2015aa7db3011?from=personal_page)
- 吐司官方「想法」整理过「6个国风AI模型」，含「国风3 GuoFeng3」系列及汉服、中国门神画风格等 LoRA **[2023]** — [知乎想法：吐司 TusiArt 懒人必备！6个国风AI模型](https://www.zhihu.com/pin/1662121171599638528)
- 小红书 AI 绘画爆款类型中列出「渐变风」（东方极简、新中式渐变插画）和「赛博朋克国风」 **[2024]** — [CSDN：单周涨粉过万，这9种AI绘画风格也太火了！](https://blog.csdn.net/A2421417624/article/details/143253499)
- 英文提示词：汉服人像示例关键词 `hanfu, chinese, traditional`，风格 `Chinese traditional gongbi painting, court-lady portrait`（标注适合 Nanobanana、Hunyuan 等模型） — [CreateIO: Traditional Gongbi Ink Wash Painting](https://www.createio.ai/showcase/traditional-gongbi-style-ink-painting-481)
- 水墨人像英文示例：`Chinese ink wash painting style illustration of a graceful woman wearing pale hanfu holding an oil-paper umbrella in gentle rain`，并加 xuan paper（宣纸）纹理、朱砂印章、留白、85mm 景深等修饰 — [Media.io: Gemini AI Chinese Ink Wash Painting Prompt](https://www.media.io/ai-prompts/gemini-ai-chinese-ink-wash-painting-prompt.html)
- 工笔定义：先以细线勾勒轮廓，再逐层叠加墨色与颜色 — [Wikipedia: Gongbi](https://en.wikipedia.org/wiki/Gongbi)
- Seedream 4.0 教程给出「电影感国风海报」写法（《洛神赋》水雾与流金丝缎场景）；Apiyi 指南给出「古风」「民国风」模板，结构为「人物与服饰 + 发型 + 场景 + 风格 + 画质」 **[2025]** — [知乎：用字节Seedream4.0直出4K中文海报的22种懒人方法](https://zhuanlan.zhihu.com/p/1952050930926200719)；[Apiyi：Seedream 4.0热门风格完全指南：13种主流艺术风格](https://help.apiyi.com/seedream-4-0-popular-styles-prompt-guide.html)

**（I）韩系 / 韩漫（边界类目）**
- 韩漫风关键词：「韩漫风格、韩国网络漫画、清晰线稿、柔和上色」；视觉特征：五官精致、身材比例修长、穿搭时尚、色彩饱和度高，适合霸总甜宠、都市恋爱题材 — [网易：AI 文生图：主流动漫风格及提示词示例](https://www.163.com/dy/article/JS689UJ20536FE6V.html)
- 另一来源描述韩漫为「人体比例修长、五官精致、低饱和高级灰」（与上一条「高饱和」说法冲突） — [塔猴：AI短剧18种画风提示词模板](https://www.tahou.com/article/203087022786924549)
- 英文：`modern manhwa style`、`clean lineart`、`vertical scroll composition` — [Morphic：用AI制作韩漫的方法](https://morphic.com/zh/resources/images/manhwa-ai)
- LiblibAI 有「漫画韩漫系头像工作流」 — [LiblibAI 工作流页](https://www.liblib.art/modelinfo/dbe0ecde4c164da6b6743c3b63fb8739)
- 一个真人向案例提示词同时用了 `cinematic lighting` 与「半写实绘画风」描述韩系男性角色（摘要归纳，来源页未核实） — [Krene：AI 美术提示词素材库](https://www.krene.com/prompt)

**（J）美漫 / 欧美插画 / 概念设计**
- 美漫风：欧美漫画的粗犷线条、立体感、夸张的人物特征，适合超级英雄、动作冒险 — [网易：主流动漫风格及提示词示例](https://www.163.com/dy/article/JS689UJ20536FE6V.html)
- 另一平台称美漫「厚重线条和强烈明暗对比」适合海报 — [HANYUAI：漫画风海报](https://www.hanyuai.com/zh/more/comic-poster)
- 模型层面：Z-Image-Turbo 被描述为适合快速草图和概念设计，Flux-Kontext 适合美漫和写实风格 **[2025–2026]** — [Krene：AI 美术提示词素材库](https://www.krene.com/prompt)
- 即梦 4.0 速查表风格词含「美漫」；即梦官网示例含「文艺复兴风格」 — [苏米客：即梦4.0提示词手册](https://www.xmsumi.com/detail/1550)；[即梦AI官网](https://jimeng.jianying.com/)

**（K）数字人 / 虚拟人**
- 百度智能云按图形维度与外形风格把虚拟数字人分为「二次元、3D卡通、3D超写实、真人形象」四类 — [百度智能云：虚拟数字人形象分类详解](https://cloud.baidu.com/article/3400159)
- 另一分类为「2D真人、2D卡通、3D卡通、3D写实、3D超写实」五类；2D真人=真人在录影棚录制视频再经 AI 训练 **[2024]** — [腾讯新闻：越来越像“人”的数字人](https://news.qq.com/rain/a/20240207A01WDU00)
- 行业访谈的分类：「2D 卡通、3D 超写实、3D 写实、3D 半写实、3D 卡通」 — [InfoQ：十问大咖](https://www.infoq.cn/article/svhlgvhggpvlrfqlckug)
- 自媒体用 3D 卡通数字人代替真人出镜；做法是在即梦上传自己的照片作为角色特征，提示词公式「【画面风格】+【主体形象】+【场景】」 **[2025]** — [知乎：手把手教你做AI数字人，用AI定制自己的3D卡通数字人](https://zhuanlan.zhihu.com/p/1918239047006008420)

**（L）AI写真 / 商业写真 / 证件照 / 影棚人像 / 胶片感**
- 妙鸭相机 **[2023]**：9.9 元上传 20 余张照片生成「数字分身」，再在模板中选择写真效果；30 多种模板含古风、都市、证件照、休闲 — [知乎问题：妙鸭相机 9.9 元 AI 写真火爆](https://www.zhihu.com/question/613829938)；[证券时报：爆火！9.9元，AI写真](https://www.stcn.com/article/detail/929093.html)
- 评论指出妙鸭把提示词换成了「预期效果更明确的模板」，用户点击即生成 **[2023]** — [人人都是产品经理：妙鸭相机摸着石头过河](https://www.woshipm.com/it/5880289.html)
- 开源 EasyPhoto 的流程：用最正的参考图与模板图人脸融合作 canny 图，结合 LoRA 与 ControlNet 多次生成，可做证件照、写真、模特换装 **[2024]** — [CSDN：AI一键部署本地“妙鸭”](https://blog.csdn.net/Coo123_/article/details/144541389)
- 支付宝上线「AI写真馆」（妙鸭同款），上传 1 张图生成 AI 证件照 — [AI奇点网](https://m.aieva.cn/review/1242.html)
- 「电影质感人像」模板：「柯达Portra 400胶片质感」「景深虚化」「8K」；人像提示词公式「[人物描述] + [服装与造型] + [动作与表情] + [场景与环境] + [镜头与光影] + [风格要求] + [画质与细节要求]」 — [塔猴：AI生成人像提示词：爆款模板合集](https://www.tahou.com/article/208406468588155909)
- 「电影胶片感修图」核心词：「柯达金200胶片质感，浅景深，侧逆光，柔和阴影，电影镜头眩光，复古色调」 — [塔猴：AI人像修图提示词全攻略](https://www.tahou.com/article/208406093128854533)
- **[2025–2026]** 「10 大影楼质感」教程用 Nano Banana + 即梦做高级感肖像照 — [知乎：教你白嫖10大影楼质感！](https://zhuanlan.zhihu.com/p/1966148393756767096)
- 即梦第三方模板含「日常清新人像」「复古港风人像」「帅气男生头像」并附正/反向提示词 **[2026-04]** — [123AI：即梦AI提示词大全：万能公式+全场景模板](https://www.123ai.org/post/2026-04-19-jimeng-ai-prompt-template-collection.html)
- 即梦写实类写法：「黑白摄影，高反差，粗颗粒，街头纪实，大师感」「胶片人像摄影」 — [知乎：即梦 AI 提示词大全](https://zhuanlan.zhihu.com/p/2071960585068139511)

**（M）电影感**
- Adobe Firefly 繁中示例：电影风格常用「電影燈光」「變形鏡頭」「膠片顆粒」「色彩調校」，人像用「林布蘭光」「眼神光」「四分之三視角」 — [Adobe Firefly：AI 影像提示詞範例](https://www.adobe.com/tw/products/firefly/ai-generated-examples/image-prompts.html)
- 优设网整理「23套电影美学提示词模板」 — [优设网：23套电影美学提示词模板](https://www.uisdc.com/ai-cinema-prompts)
- 混元通用艺术类含「胶片电影」「复古」风格 **[2024]** — [腾讯云：混元生图风格列表](https://cloud.tencent.com/document/product/1729/105846)

**（N）油画 / 水彩 / 素描 / 彩铅**
- 通义万相 **[2023]** 预设：水彩、扁平插画、二次元、油画、中国画、3D卡通、素描 — [腾讯新闻：通义万相实测](https://news.qq.com/rain/a/20230707A07WTQ00)
- 混元旧表：水彩、素描（动漫艺术类）；油画、梵高、莫奈、版画、波普、极简（通用艺术类） **[2024]** — [腾讯云：混元生图风格列表](https://cloud.tencent.com/document/product/1729/105846)
- 画风指南中英对照：印象派 `Impressionism`、油画风格 `Oil Painting`、水彩风格 `Watercolor`；41 种版本给出油画女性肖像提示词并提到伦勃朗式光线 **[2025]** — [一起学AI：50+画风提示词](https://ai.meiweihui.cn/1002/ai%E7%BB%98%E7%94%BB%E9%A3%8E%E6%A0%BC%E5%85%A8%E6%8C%87%E5%8D%97%EF%BC%9A50%E7%94%BB%E9%A3%8E%E6%8F%90%E7%A4%BA%E8%AF%8D%E5%AE%9E%E6%88%98%E6%A1%88%E4%BE%8B%EF%BC%8C%E8%A7%A3%E9%94%81%E4%BD%A0/)；[知乎：41种AI绘画风格](https://zhuanlan.zhihu.com/p/1920952360831813473)
- 中英对照速查（WayToAGI 问答）：A站趋势风格、超现实风格、油画风格、赛博朋克风格、后印象主义风格、废土风格、东方山水画、浮世绘等 — [WayToAGI：有AI绘画的风格化提示词吗](https://www.waytoagi.com/question/61433)

### Inferences
- 中文社区的「真实感梯度」实际上是三段式而非二分：**真人/真实系/写实**（照片级）→ **半写实/2.5D**（CG/游戏渲染感、油画质感人像，常见于 GuoFeng3、XXMix_9realistic 一类）→ **二次元**。「半写实」偏向「真人往插画方向走」，「2.5D」偏向「二次元往 3D/真人方向走」，但社区实际混用。
- 「厚涂/伪厚涂/平涂/赛璐璐」的定义全部来自板绘教学，AI 社区直接借用。在 AI 人像语境下，「厚涂」≈ 无明显线稿、笔触堆叠的写实立体绘画感（接近英文 `painterly`/`impasto portrait`），「伪厚涂」则基本等同于二次元/半写实边界，严格来说属于本调研的排除范围。
- 「C4D 风」「Blender 风」「OC 渲染」在中文提示词里是作为**质感指示词**使用的（软件/渲染器名 → 柔光、PBR、高光泽粘土、极简背景），并非独立画风；它们几乎总是与「盲盒」「IP 形象」「Q 版」「3D 卡通」连用。
- 「写实」在中文平台 UI 中有两种角色：既是风格下拉项（混元「写实」、文心一格「写实风格」），也是模型类别（吐司「真实」、LiblibAI「写实」）。2025 年后新一代原生多模态模型（即梦 4.0、Seedream 4.0、混元图像 3.0、可图 2.0）更多以自然语言描述风格，预置风格编号表趋于淡出。

### Gaps
- 无法读取《一文搞懂 AI 绘画风格》（腾讯新闻，2025-03-28）全文，其完整分类表未能提取 — [腾讯新闻](https://news.qq.com/rain/a/20250328A0AMPI00)
- 「半真人」「照片级」作为独立术语的社区定义未找到专门资料；「彩铅」风格在所有检索结果中均未出现。
- 「Blender 风」作为中文独立风格词的用法未见资料；仅见于 Nano Banana 手办提示词中的「Blender modeling process」。
- 「概念设计/概念艺术」在中文人像语境中的系统资料几乎没有，仅有模型适配性的零散提及。
- 没有找到任何来源对 AI 语境下「厚涂」与「写实」的边界做专门讨论。

---

## 问题二：中国平台如何组织风格选择器 / 模型分类？

### Takeaway
国内平台分为两类组织方式：**大厂文生图产品**（即梦、通义万相、可灵/可图、豆包/Seedream、混元、文心一格）以「预置风格」下拉/编号或自然语言为主，风格表通常以「写实 / 3D / 国风（中国风、水墨、国潮）/ 油画水彩素描 / 二次元 / 赛博朋克」为骨架；**模型社区**（LiblibAI、吐司、海艺、WHEE）以模型标签/频道组织，骨架为「真实（真人）/ 2.5D / 动漫 / 国风 / 3D·游戏 / 插画·设计 / 建筑空间」。目前没有一家平台的官方完整风格列表能被本次调研直接读取。

### Cited Findings

**即梦（Jimeng，字节跳动）**
- 第三方工具汇总称即梦涵盖「动漫、写实、3D渲染、国风、赛博朋克等 30+ 艺术风格」，未逐一列出 — [飞书文档：AI 绘画工具精选](https://docs.feishu.cn/article/wiki/TgvDwdbhfiZXzakCGngc5yGyngc)
- 官网示例提示词含「3D游戏人物风格」「插画风格」「超写实插画」「文艺复兴风格」「电影质感」 — [即梦AI官网](https://jimeng.jianying.com/)
- 即梦 3.0 **[2025-04]** 被称为「最强中文AI绘图模型」；另有「100 张图测试即梦 6 个模型」的横评 **[2025]** — [知乎：最强中文AI绘图模型即梦3.0上线](https://zhuanlan.zhihu.com/p/1891053828742295949)；[知乎：测试 100 张图，即梦 6 个模型哪个最好？](https://zhuanlan.zhihu.com/p/1953224615380879115)
- 即梦 4.0 提示词手册（官方/半官方整理）在多处转载，速查表结构为「风格词 / 光影词 / 材质词」 **[2025]** — [搜狐：即梦4.0提示词手册！完整！](https://www.sohu.com/a/999370262_121124358)；[苏米客：即梦4.0提示词手册快速上手版](https://www.xmsumi.com/detail/1550)；[AIGC.cn：即梦AI提示词手册](https://www.aigc.cn/sites/100663.html)
- 腾讯新闻 **[2025-09-29]** 实测称混元图像 3.0 「不敌即梦 4.0」 — [腾讯新闻：腾讯开源混元图像3.0，实测不敌即梦4.0](https://view.inews.qq.com/a/20250929A0234X00)

**豆包 / Seedream（字节）**
- Seedream 4.0 官方博客：30 多种艺术风格与场景切换；单张人像生成多风格角色图；2D 草图转 3D **[2025-09]** — [ByteDance Seed 博客](https://seed.bytedance.com/en/blog/%E4%B8%8D%E6%AD%A2%E4%BC%9A-%E7%94%BB-%E6%9B%B4%E4%BC%9A-%E6%83%B3-seedream-4-0-%E5%9B%BE%E5%83%8F%E5%88%9B%E4%BD%9C%E6%A8%A1%E5%9E%8B%E6%AD%A3%E5%BC%8F%E5%8F%91%E5%B8%83)
- 优设网「万字教程 10 个案例速通 Seedream 4.0」；教程提到连续生成 6 张后人脸 ID 保持良好，参考脸部上传大头照、参考服装上传全身/半身照 **[2025]** — [优设网：万字教程速通 Seedream 4.0](https://www.uisdc.com/seedream-4-0)；[知乎转载](https://zhuanlan.zhihu.com/p/1949478296057275439)
- Apiyi 整理 Seedream 4.0「13 种主流艺术风格」模板（含古风、民国风） — [Apiyi：Seedream 4.0热门风格完全指南](https://help.apiyi.com/seedream-4-0-popular-styles-prompt-guide.html)
- Seedream 3.0 技术报告（arXiv） — [arXiv: Seedream 3.0 Technical Report](https://arxiv.org/pdf/2504.11346)

**通义万相（阿里）**
- **[2023-07]** 首发：基础文生图支持「水彩、扁平插画、二次元、油画、中国画、3D卡通、素描」；文本框下方有 8 个可选画风 — [腾讯新闻：阿里云AI绘画创作大模型来了！](https://news.qq.com/rain/a/20230707A07WTQ00)；[广东财经大学资源页](https://resource.gdufe.edu.cn/2024/1204/c11797a213754/page.htm)
- 较新第三方介绍：内置模型含「写实、插画、国风、二次元、油画、水墨、3D建模风格」；另一来源称「写实、动漫、水墨、油画、赛博朋克等 20 多种风格」（第三方，可靠性一般） — [AIWW：通义万相介绍](https://www.aiww.com/aitool/tongyiwanxiang)；[eyeofai：通义万相](https://eyeofai.cn/app/tongyiwanxiang)
- 万相 2.1 深度使用教程 **[2025]** — [CSDN：通义万相2.1 深度使用教程](https://blog.csdn.net/Liudef06/article/details/148845976)

**可灵 / 可图（快手）**
- 可图 2.0 **[2025-04]** 支持 60 多种风格化效果转绘 — [腾讯新闻：可灵AI发布2.0版基座模型](https://news.qq.com/rain/a/20250415A09FQF00)
- 第三方：风格含赛博朋克、梵高油画、国风水墨；支持「写实照片转赛博朋克」「二次元插画转油画质感」等风格转绘 — [AIGC.cn：可图AI 2.0](https://www.aigc.cn/sites/90411.html)
- 官方文档示例以写实摄影参数为主（见问题一 A） — [可灵AI 文档](https://klingai.com/docs-v2)

**LiblibAI（哩布哩布）**
- 第三方介绍的风格筛选项：「国风、二次元、写实、赛博朋克、水墨、复古」 — [AI入口：LiblibAI官网介绍](https://www.airukou.cn/liblibai.html)
- LoRA 定义：微调插件，体积小（通常 100MB–2GB），可叠加在基础模型上 — [知乎：AI绘画模型类型介绍](https://zhuanlan.zhihu.com/p/682196143)
- 模型命名惯例样本：「Z-Image-真人拍摄，写实风格-LoRA」「国风-中国武侠风|传奇色彩-LoRA」「3D超萌IP形象设计|盲盒|revAnimated-Checkpoint」「漫画韩漫系头像工作流」 — [LiblibAI 模型页 1](https://www.liblib.art/modelinfo/39dee1b175d24d3f9f61ca415bc7f207?from=personal_page)；[模型页 2](https://www.liblib.art/modelinfo/a8f5e203244d4fdcabd2015aa7db3011?from=personal_page)；[模型页 3](https://www.liblib.art/modelinfo/fe8a50878bed444d9049b079b466ea1c)；[工作流页](https://www.liblib.art/modelinfo/dbe0ecde4c164da6b6743c3b63fb8739)

**吐司 TusiArt**
- 官网标签：全部、动漫、美女、真实、3D、建筑、汉服、摄影、国风、真人、动物、2.5D、风景、Q版、机甲、武侠、科技、设计、风格 — [吐司 Tusi.Art](https://tusi.art/)
- 中文站频道：真实、动漫、2.5D、国风、游戏设计、插画、电商设计、科幻、建筑&空间设计 — [tusi.cn](https://tusi.cn/)
- 另一介绍的分类：写实、二次元、国风、奇幻、游戏&3D、插画&广告设计、建筑&空间设计 — [易班：吐司TusiArt](https://ad.yiban.io/operate/tool/532)

**海艺 SeaArt**
- 第三方描述覆盖「二次元、3D、油画、写实」或「写实、二次元、插画、设计、摄影」等风格；举例预设模型「GuoFeng3 国风」；官网更新说明曾提到「广场新增标签分类」；各来源模型数量说法差异极大（80 万+ / 12000+ / 21 万+），不宜采信 — [AIGC.cn：海艺](https://www.aigc.cn/sites/12550.html)；[AITOP100：海艺AI国内版](https://www.aitop100.cn/tools/detail/1839.html)；[Hello123：海艺AI](https://www.hello123.com/seaart/)；[非猪AI导航：海艺](https://feizhuke.com/sites/haiyiai.html)
- 教程类博客用海艺生成「真人照片一样质感」的图 **[2023]** — [CSDN：手把手教你用海艺AI](https://blog.csdn.net/CCEEHM/article/details/134816917)

**美图 WHEE / 美图设计室**
- WHEE 当时只有一个 MiracleVision 4.0 基础模型，画风靠「风格模型」组合；图生图可选一个或多个风格模型并调「风格强度」「颜色饱和度」；支持自训练专属风格模型（需内测） **[2024]** — [AI奇点网：美图whee教程](https://www.aieva.cn/edu/1706.html)
- **[2024-03]** 五款工具横评（含 WHEE、文心一格） — [中华网：Midjourney、文心一格、WHEE等五款主流AI绘画工具横向测评](https://hea.china.com/hea/xinwen/2024/0325/032024_1497266.html)

**腾讯混元 / 元宝**
- 旧版「混元生图风格列表」分「动漫艺术类」（暗黑、素描、中国风、国潮、水墨、水彩、3D、像素、赛博朋克、日本动画、手绘日漫）与「通用艺术类」（剪纸、刺绣、梵高、莫奈、油画、皮影、波普、胶片电影、复古、极简、版画、敦煌壁画等数十种） **[2024，页面约 660 天未更新]** — [腾讯云：混元生图风格列表](https://cloud.tencent.com/document/product/1729/105846)
- 轻量版编号表：水墨画 101、剪纸风格 108、3D 116、通用写实风格 401；传 000 为不限定风格并在 Prompt 中写「xx 风格 + 其他提示词」 — [腾讯云：文生图轻量版风格列表](https://cloud.tencent.com.cn/document/product/1729/108992)
- 标准版预置：水墨画、写实、3D 渲染、新年剪纸画等十几种，也可在 Prompt 开头写风格词自定义（国潮、皮影、传统剪纸作为可写描述词出现） — [腾讯云：混元生图产品页](https://cloud.tencent.cn/product/aiart)；[腾讯云开发者社区：混元文生图操作指南](https://cloud.tencent.com/developer/article/2352869)
- 混元图像 3.0 **[2025-09]** 开源，80B，无固定风格编号表，靠自然语言理解 — [ModelScope：腾讯混元图像3.0正式开源](https://modelscope.csdn.net/68db3f7b8867235e138a8d74.html)；[博客园：混元图像3.0完全指南](https://www.cnblogs.com/sing1ee/p/19116886/hunyuan-image-3-guide)

**百度文心一格**
- 官方指南风格关键词：古风、二次元、写实风格、浮世绘、未来主义、像素风格、水彩画、油画、卡通画 — [百度AI：AI作画-高级版使用指南](https://ai.baidu.com/ai-doc/NLP/4libyluzs)
- 第三方 **[2026]** 评测：文生图可选「国风、油画、水彩、动漫、写实」；称提供「128 种艺术风格迁移」（未经官方核实） — [mfyyy：文心一格官网入口及使用教程 2026](https://mfyyy.com/sites/141.html)
- **[2024]** 横评：支持油画、水彩、素描、卡通、动漫等 — [智能公会：2024年国内主流AI绘画工具横向测评](https://www.zngh.com/mobile_articleshow.php?cid=15&id=11910)

### Inferences
- 两代产品的组织逻辑不同：**2023–2024 代**（万相 1.x、混元旧版、文心一格、WHEE）用固定风格枚举（下拉/编号/风格模型），风格名高度重合于「写实 / 3D / 国风·水墨 / 油画·水彩·素描 / 二次元 / 赛博朋克 / 像素」；**2025–2026 代**（即梦 4.0、Seedream 4.0、混元图像 3.0、可图 2.0）转为「自然语言 + 参考图」，风格知识迁移到官方「提示词手册」和「风格转绘」功能里。
- 模型社区的标签体系（吐司最清晰）把「真实/真人」「2.5D」「动漫」作为真实感三档，再叠加题材标签（汉服、国风、武侠、Q版、机甲）和用途标签（摄影、设计、电商、建筑）。「国风」在所有平台都是独立一级类目，这是中国平台相较 Civitai 等海外社区最显著的分类差异。
- 「3D」在模型社区常与「游戏」合并（吐司「游戏&3D」），说明 3D 类目的主要用户是游戏/IP 设计，而非纯人像。

### Gaps
- 未能获取任何平台当前（2026-10）UI 中风格面板的**官方完整截图或列表**；即梦、可灵、豆包、海艺、美图设计室、元宝均无官方风格清单可引。
- 元宝（腾讯）与美图设计室的生图风格分类完全没有检索结果。
- LiblibAI 当前模型广场的官方一级分类名（是否含「真人」「3D」「盲盒」「厚涂」）无法确认，仅有第三方转述的筛选项。

---

## 问题三：小红书 / B站 / 知乎 / 公众号创作者如何解释 写实 / 半写实 / 2.5D / 3D / 厚涂 / 平涂 的差别？有哪些「画风大全」帖，结构如何？

### Takeaway
中文平台上的解释帖分两条脉络：**技法脉络**（知乎/蓝铅笔/轻微课的「平涂·厚涂·伪厚涂·赛璐璐」科普，以「有无线稿 + 明暗过渡方式」为判别法）和**模型脉络**（CSDN/知乎的 SD 模型推荐帖，以「真实系 / 2.5D / 二次元」三档归类模型）。「画风大全」帖的典型结构是「N 种风格 × 同一主体对照 + 中英提示词」，大类多为「艺术流派 / 动画影视 / 文化地域 / 现代数字艺术」，并以苹果、海边村庄等固定主体做对照。

### Cited Findings

**技法差异的解释方式**
- 蓝铅笔/轻微课/知乎系列科普以「平涂—半厚涂（伪厚涂）—厚涂」线性排列，并以赛璐璐为平涂极端；判别法：成品是否有清晰线稿、明暗过渡是平滑还是边缘清晰 — [蓝铅笔](https://www.lanqb.com/graphic/1742)；[知乎 p/500536943](https://zhuanlan.zhihu.com/p/500536943)；[轻微课 54887](https://www.qingwk.com/article/detail-54887.html)；[CG导航：上色知识科普](https://hao.shenyecg.com/Article/948137)
- 这些帖子面向绘画初学者，常附「哪一种最适合初学者」的建议 — [搜狐：平涂、厚涂、赛璐璐风格的插画都是怎样的？](https://www.sohu.com/a/454600616_120715188)
- 「【零基础】平涂、厚涂如何区分，具体该怎么画？」为分上下篇的教程体 — [知乎 p/103170017](https://zhuanlan.zhihu.com/p/103170017)

**真实感梯度的解释方式（SD 模型推荐帖）**
- CSDN 模型盘点以「真实系 / 二次元 / 2.5D」三类组织 Checkpoint 推荐，并给出各类定义 **[2024]** — [CSDN：关于AI绘画Stable diffusion的各种模型](https://blog.csdn.net/cxyxx12/article/details/139146436)；[CSDN：主流大模型动漫、写实大模型推荐](https://blog.csdn.net/cxyxx12/article/details/141057966)
- 「二次元 + 真人向精品模型推荐」类帖子把模型按「二次元 / 真人向」二分，再列 2.5D 模型 **[2025]** — [CSDN：AI绘画模型全攻略：二次元+真人向精品模型推荐](https://blog.csdn.net/a2421417624/article/details/147999365)；[CSDN：SD 零基础入门 03 AI 绘画模型推荐](https://blog.csdn.net/qq_41314882/article/details/138301115)；[CSDN：自用大模型分享（麦橘写实）](https://blog.csdn.net/weixin_44792197/article/details/136511092)

**「画风大全」帖的结构**
- 《一个苹果带你了解42种AI绘画风格特征、适用场景、生成效果》：以同一个苹果为主体展示 42 种风格 — [知乎 p/700376351](https://zhuanlan.zhihu.com/p/700376351)
- 《41种AI绘画风格提示词+实战案例》：分「艺术流派、动画影视、文化地域、现代数字艺术」四大类，用同一海边村庄场景演示各流派写法 **[2025]** — [知乎 p/1920952360831813473](https://zhuanlan.zhihu.com/p/1920952360831813473)；[镜像](https://book.huanzhou.art/books/agi/page/41ai)
- 《AI绘画风格全指南：50+画风提示词+实战案例》：按艺术流派（印象派、油画、水彩）与文化地域（中国水墨、敦煌壁画）等分组，给中英对照 **[2025]** — [一起学AI](https://ai.meiweihui.cn/1002/ai%E7%BB%98%E7%94%BB%E9%A3%8E%E6%A0%BC%E5%85%A8%E6%8C%87%E5%8D%97%EF%BC%9A50%E7%94%BB%E9%A3%8E%E6%8F%90%E7%A4%BA%E8%AF%8D%E5%AE%9E%E6%88%98%E6%A1%88%E4%BE%8B%EF%BC%8C%E8%A7%A3%E9%94%81%E4%BD%A0/)；[知乎转载](https://zhuanlan.zhihu.com/p/1894989148978390250)
- 《AI绘画Midjourney绘画提示词Prompt大全，风格提示词大全》：按 UI、插画、二次元、国风等场景分组，英文提示词附中文翻译 — [知乎 p/676955175](https://zhuanlan.zhihu.com/p/676955175)
- 《AI绘画 关键词手册》：把提示词分为「前缀、画风词」等结构，画风词用于凸显图片画风 **[2023]** — [知乎 p/625855158](https://zhuanlan.zhihu.com/p/625855158)
- 《AI绘画提示词-摄影、3D、卡通、中式、立体等都在这里》：按「摄影 / 3D / 卡通 / 中式 / 立体」分组 **[2023]** — [知乎 p/661854045](https://zhuanlan.zhihu.com/p/661854045)
- 《小白必学的AI绘画10大高阶风格（附提示词模板与生成效果）》 **[2025]** — [CSDN](https://blog.csdn.net/2401_83048197/article/details/146203738)
- 《16个很火的画风提示词，拿去直接用》 **[2025–2026]** — [知乎 p/1963991157412466759](https://zhuanlan.zhihu.com/p/1963991157412466759)
- 《承包你的朋友圈！10种AI转绘风格提示词》：以「转绘（图生图风格迁移）」为组织方式，范围从梵高油画到国潮剪纸、羊毛毡 3D **[2026]** — [知乎 p/2050679127087362160](https://zhuanlan.zhihu.com/p/2050679127087362160)
- 《AI短剧18种画风提示词模板》《AI漫剧核心提示词大全：7大题材高频词库》：面向 AI 短剧/漫剧的画风模板，按题材（甜宠/古风/悬疑）组织 — [塔猴 18种画风](https://www.tahou.com/article/203087022786924549)；[塔猴 7大题材](https://www.tahou.com/article/201633590593081349)
- 《爆肝整理！AI绘画关键词分享（关键词结构与具体案例）》 **[2022–2023]** — [知乎 p/578597288](https://zhuanlan.zhihu.com/p/578597288)
- 《AI绘画提示词：从入门到精通》设「风格关键词宝库」章节 **[2026]** — [知乎 p/1995431090278658669](https://zhuanlan.zhihu.com/p/1995431090278658669)
- 《ChatGPT 4o出图提示词大全》 **[2025]** — [知乎 p/1890096031124931580](https://zhuanlan.zhihu.com/p/1890096031124931580)
- 《50 个绘画提示词解锁你的数字艺术潜能》（火山引擎开发者社区转载） — [火山引擎](https://developer.volcengine.com/articles/7530117896815509540)
- B 站专栏《Nano Banana 最新5大类 20+创意提示词分享》按玩法大类组织 **[2025]** — [哔哩哔哩专栏](http://www.bilibili.com/read/cv42961374/)
- UIED 用户体验学习平台的「AI绘画常用提示词」 — [UIED](https://www.uied.cn/24177.html)

**小红书生态的说法**
- 做小红书 AI 绘画账号的「7 个赛道」帖提到「头像号」「风格号」，并指出「小红书对真人类的，目前笔记上会出现 AI 创作的提示，比较影响账号的流量和涨粉」 — [知乎：如果你想做小红书ai绘画账号，必须知道这7个赛道！](https://zhuanlan.zhihu.com/p/358478135)
- 「单周涨粉过万，这 9 种 AI 绘画风格也太火了」列出渐变风（东方极简、新中式渐变插画）、赛博朋克国风等 **[2024]** — [CSDN 143253499](https://blog.csdn.net/A2421417624/article/details/143253499)；[CSDN 143861062](https://blog.csdn.net/m0_59162559/article/details/143861062)
- 「3 大热门 AI 绘画风格助力一周涨粉过万」 **[2025]** — [CSDN 147731481](https://blog.csdn.net/m0_56144365/article/details/147731481)
- 较早帖子称「某书最火的是复古旧漫、极简插画风格的头像」（**[2023–2024]**，可能过时） — [CSDN 143253499](https://blog.csdn.net/A2421417624/article/details/143253499)

### Inferences
- 中文社区解释「写实 vs 半写实 vs 2.5D」时几乎不给可操作的视觉判据，而是通过**代表模型**来定义（majicMIX=写实，XXMix_9realistic/GuoFeng3=2.5D）；相反，「厚涂 vs 平涂」有清晰的技法判据（线稿、明暗过渡）。这意味着报告在给出定义时，前者应以「模型/样图」举例，后者可直接写判别规则。
- 「画风大全」帖在 2025 年后明显从 SD 模型推荐转向「提示词模板 + 新模型（即梦 4.0、Seedream、Nano Banana、GPT-4o）」，组织方式从「按模型类别」变为「按风格流派 / 按用途（头像、短剧、转绘）」。
- 小红书上人像类 AI 内容受平台「AI 创作」标识影响，创作者转向非真人（头像、风格号、国风插画）或「极度真实到不被识别」（`xhs` LoRA）两极。

### Gaps
- 未找到任何可确认存在的「一张图看懂 真人/3D/厚涂/国风/皮克斯」小红书对比图或 B 站视频；检索结果多为账号运营文章。
- 公众号文章无法被搜索引擎直接索引，本次没有获得公众号原文链接。
- 知乎《42 种》与腾讯新闻《一文搞懂》的完整类目表因无法读全文而缺失。

---

## 问题四：哪些中文画风术语没有精确英文对应，通常如何翻译或用英文提示？

### Takeaway
最典型的「无精确英文对应」术语是：厚涂（技法义 impasto ≠ 风格义「写实立体绘画感」）、伪厚涂/半厚涂（无通用英译）、盲盒风/潮玩风（需拆成 `blind box`/`POP MART`/`3D render`/`C4D`/`Octane`）、手办（`character figure`/`1/7 scale figure`）、国风/国潮/新中式（无单词对应，拆为 `Chinese ink wash`/`hanfu`/`gongbi`/`traditional Chinese`）、2.5D（中文社区直接用，英文无同义风格词）、AI写真（≈ portrait photo template 而非 prompt 术语）。中文用户的通行做法是**把中文风格词保留在中文提示词里，而在需要英文时改用「材质 + 渲染器 + 文化物件」的组合词**。

### Cited Findings
- 厚涂的词典/术语库英译为 `impasto`（AAT 首选词；变体 `impasto painting`、`pastose painting`），但该词只覆盖「颜料堆叠」的技法义 — [AAT-Taiwan](https://aat.teldap.tw/AATFullDisplay/300053368)；[海词词典](https://dict.cn/impasto)；[艺见 ArtMatters：厚涂 Impasto](https://www.artmatters.tech/terms/term-impasto)
- 中文板绘圈对「厚涂」的风格义是「写实立体的绘画风格」「不依赖线稿、明暗过渡柔和」，这与 impasto 的技法义不同 — [蓝铅笔](https://www.lanqb.com/graphic/1742)；[知乎 p/500536943](https://zhuanlan.zhihu.com/p/500536943)
- AI 提示词中 `impasto` 需配 `textured brushstrokes`、`visible brushwork`、`palette knife marks` 等才能表达；`thick paint` 单用不准确 — [AIGC.cn：厚涂关键词](https://www.aigc.cn/96592.html)
- 盲盒风在中文提示词里以「泡泡玛特」「盲盒」「3D渲染」「OC渲染」「ip设计」「迪士尼/皮克斯风格」组合表达 — [知乎 p/43734357](https://zhuanlan.zhihu.com/p/43734357)
- 手办在 2025 年英文提示词中写作 `character figure` 或 `1/7 scale commercialized figure`，并用「包装盒 + Blender 建模屏幕 + 圆形亚克力底座」的场景描述代替风格词 — [知乎 p/1943739237913584104](https://zhuanlan.zhihu.com/p/1943739237913584104)；[博客园](https://www.cnblogs.com/yfceshi/p/19111963)
- 国风的英文提示通常拆为 `Chinese Ink Wash Painting`（水墨）、`Dunhuang Murals`（敦煌壁画）、`hanfu`/`traditional Chinese`/`gongbi painting`（服饰与技法） — [一起学AI 50+](https://ai.meiweihui.cn/1002/ai%E7%BB%98%E7%94%BB%E9%A3%8E%E6%A0%BC%E5%85%A8%E6%8C%87%E5%8D%97%EF%BC%9A50%E7%94%BB%E9%A3%8E%E6%8F%90%E7%A4%BA%E8%AF%8D%E5%AE%9E%E6%88%98%E6%A1%88%E4%BE%8B%EF%BC%8C%E8%A7%A3%E9%94%81%E4%BD%A0/)；[CreateIO](https://www.createio.ai/showcase/traditional-gongbi-style-ink-painting-481)；[Media.io](https://www.media.io/ai-prompts/gemini-ai-chinese-ink-wash-painting-prompt.html)
- 水墨人像英文提示中的中国文化物件词：`xuan paper`（宣纸）、朱砂印章、留白（negative space）、油纸伞 — [Media.io](https://www.media.io/ai-prompts/gemini-ai-chinese-ink-wash-painting-prompt.html)
- 本次检索未找到「guofeng」作为英文提示词的用法 — [搜索结论见 AIGC.cn 厚涂文与词典类结果](https://www.aigc.cn/96592.html)
- 2.5D 在中文平台被直接用作一级标签（吐司「2.5D」频道），而英文资料中 2.5D 为多义词（游戏/图形学术语），无对应画风义 — [吐司](https://tusi.art/)；[Wikipedia: 2.5D (disambiguation)](https://en.wikipedia.org/wiki/2.5D_(disambiguation))
- 赛璐璐来自「赛璐珞胶片」（celluloid），日系动画术语 — [轻微课 12015](https://www.qingwk.com/article/detail-12015.html)
- 韩漫的英文为 `manhwa`（`modern manhwa style`） — [Morphic](https://morphic.com/zh/resources/images/manhwa-ai)
- 电影感在繁中/英文资料中对应 `cinematic lighting`、`anamorphic lens`、`film grain`、`color grading`（Adobe 繁中页：電影燈光、變形鏡頭、膠片顆粒、色彩調校） — [Adobe Firefly 繁中](https://www.adobe.com/tw/products/firefly/ai-generated-examples/image-prompts.html)
- 「AI写真」在妙鸭体系中不是提示词而是「模板」（古风、都市、证件照、休闲） — [人人都是产品经理](https://www.woshipm.com/it/5880289.html)；[证券时报](https://www.stcn.com/article/detail/929093.html)
- 混元把「国潮」「皮影」作为可在 Prompt 中写的中文描述词而非预置项，说明这类词在平台内也以中文直写 — [腾讯云产品页](https://cloud.tencent.cn/product/aiart)

### Inferences
- 「厚涂」是最易误译的词：直译 `impasto` 会把 AI 推向梵高式笔触堆叠，而中文用户想要的「厚涂人像」更接近 `painterly realistic portrait, soft blended shading, no lineart, oil painting texture`。报告应明确区分「厚涂（技法）= impasto」与「厚涂（画风）≈ painterly/semi-realistic digital painting」。
- 「伪厚涂/半厚涂」实际是二次元范畴的中间风格，英文社区没有对应词；若必须英译，只能描述为「anime-style with soft rendered shading and retained lineart」——但这超出本调研范围。
- 「盲盒风」在英文里无单词对应，`blind box style` 在英文模型中识别度不确定；中文用户事实上用 `POP MART style`、`3D cartoon character, C4D, Octane render, clay material, glossy` 等物件/材质词绕开。
- 「国风」是一个伞形词，英文必须按子类拆解：水墨（ink wash）、工笔（gongbi）、汉服（hanfu）、国潮（没有稳定英译，可能写 `Chinese trendy/neo-Chinese graphic style`，未经来源证实）、新中式（无来源证实的英译）。
- 新一代中文原生模型（即梦 4.0、Seedream、混元图像 3.0、可图 2.0）对中文风格词理解良好，使「如何英译」的问题重要性下降；只有在使用 Midjourney/Flux/Nano Banana 等英文优先模型时才需要上述拆解。

### Gaps
- 「国潮」「新中式」「半写实」「伪厚涂」「盲盒风」「AI写真」的**英文提示写法均无来源证实**；上面给出的英译为推断，不应作为事实引用。
- 没有找到任何中文「提示词词典/风格词库」页面能被读取全文（WayToAGI 问答仅有片段），因此无法给出系统的中英对照表。
- 未能验证 `blind box style`、`guofeng` 等词在 Midjourney/Flux 等英文模型中的实际效果。

---

## 问题五：哪些画风在中文 AI 人像应用中特别流行？关联哪些模型/LoRA？

### Takeaway
中文 AI 人像的流行画风随时间迭代：**2023**（SD 时代）以「真人写实（majicMIX）+ 国风 2.5D（GuoFeng3）+ AI写真（妙鸭/EasyPhoto）+ 小红书潮玩盲盒」为主；**2024** 出现小红书「极度真实」Flux LoRA（`xhs`）与新中式/渐变风插画账号；**2025** 热点转向「真人变手办」（Nano Banana）、即梦 4.0/Seedream 4.0 的多风格人像与「影楼质感」肖像、3D 卡通数字人出镜；**2026** 延续 Banana2 人像玩法、羊毛毡/黏土转绘、以及对「电影感」泛词的反思（转向皮肤纹理、胶片型号等具体质感词）。

### Cited Findings

**真人写实 / 极度真实**
- majicMIX：国内知名真人写实系模型 **[2023–2024]** — [知乎 p/682196143](https://zhuanlan.zhihu.com/p/682196143)；[CSDN：自用大模型分享（麦橘写实）](https://blog.csdn.net/weixin_44792197/article/details/136511092)
- Realistic Vision 作为真实系代表 **[2024]** — [CSDN 139146436](https://blog.csdn.net/cxyxx12/article/details/139146436)
- 小红书日常照片质感 Flux LoRA，触发词 `xhs`，「极度真实，自然日常，直出图集」，用于「假期打卡照」 **[2024]** — [CSDN 142631089](https://blog.csdn.net/cxyxx12/article/details/142631089)
- Z-Image 基座上的「真人拍摄，写实风格」LoRA **[2025–2026]** — [LiblibAI](https://www.liblib.art/modelinfo/39dee1b175d24d3f9f61ca415bc7f207?from=personal_page)
- 可灵官方以「柯达Portra 400，f/8光圈……绝对写实」为示例 — [可灵文档](https://klingai.com/docs-v2)

**国风 / 古风人像**
- GuoFeng3（国风3，xiaolxl）：2.5D 国风人物/服饰模型，在吐司、海艺均作为预设/榜单模型出现 **[2023–2024]** — [CSDN 139176062](https://blog.csdn.net/A2421417624/article/details/139176062)；[知乎想法：吐司 6 个国风模型](https://www.zhihu.com/pin/1662121171599638528)；[Hello123：海艺](https://www.hello123.com/seaart/)
- 「国风-中国武侠风|传奇色彩」LoRA（LiblibAI）；汉服、中国门神画风格 LoRA（吐司） — [LiblibAI](https://www.liblib.art/modelinfo/a8f5e203244d4fdcabd2015aa7db3011?from=personal_page)；[知乎想法](https://www.zhihu.com/pin/1662121171599638528)
- 小红书爆款：新中式渐变插画、东方极简、赛博朋克国风 **[2024]** — [CSDN 143253499](https://blog.csdn.net/A2421417624/article/details/143253499)
- 即梦国风仙侠人像写法「水墨淡彩风格，柔光，国风仙侠」 **[2026]** — [知乎 p/2071960585068139511](https://zhuanlan.zhihu.com/p/2071960585068139511)
- Seedream 4.0 电影感国风海报（《洛神赋》）与古风/民国风模板 **[2025]** — [知乎 p/1952050930926200719](https://zhuanlan.zhihu.com/p/1952050930926200719)；[Apiyi](https://help.apiyi.com/seedream-4-0-popular-styles-prompt-guide.html)

**盲盒 / 潮玩 / 3D IP / 手办**
- 小红书「潮玩盲盒」风格教程（泡泡玛特/盲盒/3D渲染/OC渲染/ip设计） — [知乎 p/43734357](https://zhuanlan.zhihu.com/p/43734357)
- revAnimated 系「3D超萌IP形象设计|盲盒」Checkpoint **[SD1.5 时代]** — [LiblibAI](https://www.liblib.art/modelinfo/fe8a50878bed444d9049b079b466ea1c)
- 「盲盒手办风 3D Q 版……C4D 极简全身渲染图」案例 — [可我AI](https://www.krwoo.com/mang-he-shou-ban-feng-3dq-ban-mo-fa-xue-tu-nan-hai-c4d-ji-jian-quan-shen-xuan-ran-tu/)
- **[2025-08 起]** Nano Banana「一键做手办」成为全网热点，衍生「手办变现」教程 — [搜狐](https://www.sohu.com/a/932837854_99954671)；[知乎：Nano Banana 一键做手办只是开胃菜！12 种用法](https://zhuanlan.zhihu.com/p/1945925457871640231)；[知乎：Nano-banana官方地址与提示词](https://zhuanlan.zhihu.com/p/1945256307859911884)
- 中文 SD 社区试图用「手办、高光、精致细节」等关键词在其他工具复现手办风（该来源还声称 nano banana 有 Pro/2 版本，**可靠性低**） — [Stable Diffusion中文网](https://www.stablediffusion-cn.com/aist/12914.html)
- **[2026]** Banana2「50 个人像玩法」（含手持自己的 3D 卡通小人） — [站酷](https://www.zcool.com.cn/article/ZMTcxNDcyOA==.html)

**AI写真 / 证件照 / 影楼感**
- 妙鸭相机 **[2023-07]** 一夜爆红：9.9 元、数千人排队、30 多种模板（古风、都市、证件照、休闲）；被认为对标「海马体」照相馆 — [知乎问题 613829938](https://www.zhihu.com/question/613829938)；[中新网：妙鸭相机一夜爆红的背后](https://www.chinanews.com.cn/life/2023/07-27/10050584.shtml)；[证券时报](https://www.stcn.com/article/detail/929093.html)
- 一年后回顾「妙鸭相机现在活得还好吗」 **[2024]** — [知乎 p/710339081](https://zhuanlan.zhihu.com/p/710339081)
- 开源替代：EasyPhoto（LoRA + ControlNet），可做证件照、写真、模特换装 **[2024]** — [CSDN 144541389](https://blog.csdn.net/Coo123_/article/details/144541389)
- 支付宝「AI写真馆」上传 1 张图生成证件照 — [AI奇点网](https://m.aieva.cn/review/1242.html)
- **[2025–2026]** 「10 大影楼质感」（Nano Banana + 即梦）与「AI人像摄影天花板 10 组高端提示词」 — [知乎 p/1966148393756767096](https://zhuanlan.zhihu.com/p/1966148393756767096)；[知乎 p/1971987196882981478](https://zhuanlan.zhihu.com/p/1971987196882981478)
- 「10 条爆款 AI 人像写真级提示词（2026）」 — [oimi.ai](https://oimi.ai/zh/blog/ai-portrait-prompts)

**3D 卡通头像 / 数字人**
- 自媒体用 3D 卡通数字人代替真人出镜；即梦上传照片 + 「【画面风格】+【主体形象】+【场景】」 **[2025]** — [知乎 p/1918239047006008420](https://zhuanlan.zhihu.com/p/1918239047006008420)
- 墨图 AI 头像模板库（75 个中文模板，含黏土定格动画头像） — [墨图AI](https://www.motuart.com/prompts/avatar)
- 即梦第三方模板「帅气男生头像」 **[2026-04]** — [123AI](https://www.123ai.org/post/2026-04-19-jimeng-ai-prompt-template-collection.html)
- LiblibAI「漫画韩漫系头像工作流」（边界类目） — [LiblibAI](https://www.liblib.art/modelinfo/dbe0ecde4c164da6b6743c3b63fb8739)

**皮克斯 3D 卡通**
- DeepSeek + 即梦做「3D卡通皮克斯风格」人物叙事 **[2025]** — [知乎 p/27693228552](https://zhuanlan.zhihu.com/p/27693228552)

**平台级风格转绘**
- 可图 2.0 「60 多种风格化转绘」 **[2025-04]** — [腾讯新闻](https://news.qq.com/rain/a/20250415A09FQF00)
- Seedream 4.0 从单张人像生成不同风格角色图 **[2025-09]** — [ByteDance Seed](https://seed.bytedance.com/en/blog/%E4%B8%8D%E6%AD%A2%E4%BC%9A-%E7%94%BB-%E6%9B%B4%E4%BC%9A-%E6%83%B3-seedream-4-0-%E5%9B%BE%E5%83%8F%E5%88%9B%E4%BD%9C%E6%A8%A1%E5%9E%8B%E6%AD%A3%E5%BC%8F%E5%8F%91%E5%B8%83)
- 新模型适配：Z-Image-Turbo（草图/概念设计）、Flux-Kontext（美漫/写实） **[2025–2026]** — [Krene](https://www.krene.com/prompt)

### Inferences
- 「真人写实」始终是中文人像需求的底座，但其载体从 SD Checkpoint（majicMIX）→ Flux LoRA（`xhs`）→ Z-Image LoRA → 原生多模态模型（即梦 4.0、Seedream 4.0）迁移；2026 年社区更关注「不被识别为 AI」的皮肤纹理、胶片型号等具体质感词，而非「超写实/8K」类泛词。
- 「盲盒/潮玩」与「手办」是同一审美谱系的两代表达：2023 年靠 C4D/OC 渲染词 + revAnimated 类模型生成「IP 形象」，2025 年靠 Nano Banana 的图生图把**真人照片**直接变成「手办 + 包装盒 + 底座」产品图——后者才真正把该风格带入「人像」范畴。
- 「国风」是中文独有且长期稳定的高需求类目，从 GuoFeng3（2.5D）到即梦国风仙侠、Seedream 国风海报一直存在，并在小红书上以「新中式/东方极简」变体做账号增长。
- 「AI写真」在产品化层面（妙鸭、支付宝）用模板替代提示词，在创作者层面则演化为「影楼质感 / 胶片人像」提示词模板，两者共同构成中文「商业写真」类目的内涵。

### Gaps
- 没有获得 LiblibAI / 吐司 / 海艺当前（2026）**热门榜单**的实际模型名称和下载量，无法确认哪些真人/国风/盲盒 LoRA 目前最流行（最后一次检索因配额用尽未执行）。
- 妙鸭相机 2025–2026 年的现状、以及「AI写真」类产品当前的主流玩家未能确认。
- 「皮克斯风人像」「3D 卡通头像」在中文平台的具体模型/LoRA 名称缺失，仅有即梦/Nano Banana 的工作流级描述。
- 所有「流行度」判断均基于文章标题与摘要中的「爆款」「爆火」「涨粉」措辞，没有平台级统计数据支撑。
