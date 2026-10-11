# 视觉风格分类框架调研：可用于 AI 人像画风「分类轴」设计的理论/学术/工业框架

> 调研日期：2026-10-11。目标：为「非 anime 的 AI 文生图人像画风」设计多轴分类（realism level × rendering/medium × shading × linework × proportion × cultural lineage），收集现有把「视觉风格」拆成维度的框架。
>
> **方法说明与限制**：本轮调研只能使用 WebSearch 返回的页面级摘要；本会话的出站代理（egress proxy）对 arxiv.org、wikipedia.org、helpx.adobe.com、recraft.ai、siggraph.org、beforesandafters.com 等全部返回 403，WebFetch 亦 DNS 失败，且共享的 WebSearch 配额在第 2 轮后耗尽。因此：(1) 所有 Cited Findings 均来自搜索摘要而非原文全文；(2) 未能核实的「背景记忆」一律放入 Gaps 并明确标注，报告撰写者引用前须自行核对；(3) 若需补查，可在下一轮继续（建议清单见各节 Gaps）。

---

## Key Question 1 — Scott McCloud 的 "Big Triangle"（Understanding Comics, 1993）：三个顶点与 realism–iconic 光谱，及其在角色美术 / CG 分类中的应用

### Takeaway
McCloud 的三角形把图像表征放在一个**二维关系空间**中：底边是「写实 ↔ 图标化/卡通化」光谱（reality → language/meaning），顶点是「picture plane」即纯抽象（图像不再指涉任何事物，只剩形状/线条/色块）。它是目前最常被引用、最适合作为「realism level」轴与「abstraction/graphic-ness」轴的理论原型；但它是**相对定位**工具而非绝对刻度，且各二手资料对第三个顶点的命名不一致（language / meaning / 文字）。本轮未能找到把它直接用于 CG 角色或游戏美术分类的权威文献（见 Gaps）。

### Cited Findings
- *Understanding Comics* (1993) 中的三角形是用来思考漫画美术风格的工具：**写实表征位于左下角，图标化/卡通化（iconic / cartoony）位于右下角，抽象（abstraction）位于顶点** — [Wikipedia: Understanding Comics](https://en.wikipedia.org/wiki/Understanding_Comics)；[EBSCO Research Starters](https://www.ebsco.com/research-starters/literature-and-writing/understanding-comics-invisible-art-scott-mccloud)
- 第三个顶点的命名在不同来源中不一致：一处描述三角为 **reality / the pictorial plane / meaning**；一份西班牙语导读列为 **reality / language / the picture plane**。"Picture Plane" 是最一致的命名，"language" 与 "meaning" 互换使用 — [EBSCO](https://www.ebsco.com/research-starters/literature-and-writing/understanding-comics-invisible-art-scott-mccloud)；[foro3d 西语导读](https://foro3d.com/articulos/entender-comic-arte-invisible-scott-mccloud.html)
- Kevin Brooks 2005 年的演示（"Scott McCloud's Big Triangle and New Media Composition"）指出：**三角形上的项目没有绝对位置，只有关系位置**；McCloud 还展示了文字与图像在三角形上「互相推挤」；并为文字另画了一个平面，认为文字同样可以写实地、图标化地、抽象地使用 — [SlideShare: Kevin Brooks 2005](https://www.slideshare.net/slideshow/scott-mcclouds-big-triangle-and-new-media-composition/20175)
- 一篇日文评论（夏目房之介，2019）把三角形简化描述为「左为图像、右为文字、底边写实、顶点图标化」——这与英文来源「顶点 = 抽象」的描述**不一致**，提示二手概述常常混淆 iconic 与 abstract 两个方向 — [ITmedia blog 夏目房之介 2019](https://blogs.itmedia.co.jp/natsume/2019/06/undestanding_comics.html)；对照 [Wikipedia](https://en.wikipedia.org/wiki/Understanding_Comics)
- 设计界曾把 Big Triangle 作为「与漫画相关事物的地图」加以改造（BERG London, 2007），说明它被用作一般性的视觉表征分类骨架而非仅限漫画 — [BERG London 2007](https://berglondon.com/blog/2007/02/22/a-map-of-things-kind-of-related-to-comics/)
- 漫画理论博客（Ad Astra Comix）将 McCloud 三角归入「art theory」标签，并作为讨论画风抽象程度的常用参照 — [Ad Astra Comix tag: scott mccloud](https://adastracomix.com/tag/scott-mccloud/)

### Inferences
- 对 AI 人像分类的直接启发：McCloud 的三角实际上编码了**两条可分离的轴**：(a) **写实 ↔ 图标化**（形体/比例/细节的简化与符号化程度，对应「proportion / stylization」轴），(b) **再现 ↔ 抽象/picture plane**（画面在多大程度上「暴露材料/笔触/平面性」，对应「medium / mark-making」轴）。一张高度写实但笔触强烈的油画人像位于三角内部靠左上；一张平涂 vector 头像位于右下偏上。
- 因为三角只给相对位置，直接用它做离散分类需要人为设定刻度点（例如 photoreal / painterly-real / stylized-real / stylized / cartoon / graphic）；三角形本身不提供阈值。
- 二手资料对顶点命名的混乱提示：报告中应明确采用 McCloud 原文的三角标注（reality — language — picture plane），并解释 iconic（符号化、保留指涉）与 abstract（不再指涉）的区别，避免读者把「卡通化」误等同于「抽象化」。

### Gaps
- **未能核实原著措辞**：三个顶点在原书第二章的精确命名、以及 McCloud 把具体漫画家放入三角的示例图（本会话无法访问原书或 Wikipedia 全文）。
- **未找到**把 Big Triangle 系统性应用于 3D 角色/游戏美术/CG 分类的学术论文或业界讲座（搜索配额在相应查询前耗尽）。建议下一轮查询："McCloud triangle game character design stylization"、"McCloud iconic abstraction 3D character realism scale"。
- 相关概念 "amplification through simplification"、"masking effect"（简化角色 + 写实背景 → 读者代入）在搜索摘要中未出现，无法引用；这两点是把三角用于**人像**（观者认同）时最有用的论证，须回原书核实。

---

## Key Question 2 — Mori 的 Uncanny Valley 及其后续：数字人类写实度常见分级（cartoon / stylized / semi-realistic / realistic / hyper-realistic / digital double）

### Takeaway
Mori 1970 年的 "Bukimi no Tani" 给出「human-likeness → affinity」曲线：好感随类人程度上升，在接近但未达完全写实处陡降，再于不可分辨处回升；2012 年 IEEE RAM 刊出 MacDorman & Kageki 的授权英译。CG/游戏业据此形成「用风格化绕开谷底 vs. 用极高写实度跨越谷底（digital double）」两条路线，并普遍区分 cartoon / stylized / semi-realistic / realistic 四档；但**本轮未找到任何一份权威文献给出被广泛采用的正式分级定义**——分级主要是实践约定，且近年研究显示顶尖数字人已被评为「不再处于谷底」。

### Cited Findings
- 英译版 "The Uncanny Valley [From the Field]" 刊于 *IEEE Robotics & Automation Magazine* Vol. 19, Issue 2（June 2012），pp. 98–100，作者列为 Masahiro Mori, Karl F. MacDorman, Norri Kageki — [IEEE Xplore 6213238](https://ieeexplore.ieee.org/document/6213238/references)
- IEEE Spectrum 版本称这是**首个经 Mori 本人授权并审阅的英译**；原文 1970 年刊于日本小众期刊 *Energy*；MacDorman 的首个英译版本为 2005 年与同事 Takashi Minato 合作、供个人参考，后修订；原题 "Bukimi No Tani" 更准确的译法是 "Valley of Eeriness" — [IEEE Spectrum: The Uncanny Valley](https://spectrum.ieee.org/the-uncanny-valley)；[LiveScience 2012](https://livescience.com/20909-robotics-uncanny-valley-translation.html)
- 对该概念的再评估（"No Place for Robots: Reassessing the Bukimi no Tani"）发表于 *Asia-Pacific Journal*（Cambridge Core），说明学界对原假说的文化语境与证据基础存在重审 — [Cambridge Core](https://resolve.cambridge.org/core/journals/asia-pacific-journal/article/no-place-for-robots-reassessing-the-bukimi-no-tani-uncanny-valley/DAC64F8544868825C7738F7EDF20B8B0)
- 曲线描述（业界词条）：Mori 观察到角色越像人、我们越感舒适，但只到某一点；在达到完全写实前舒适度陡降（"the valley"），当表征与真人无法区分时回升。游戏与 VR 开发者常**选择风格化角色而非近写实人类来完全规避**该风险；写实面孔配僵硬机械的动作是最常见触发因素；眼睛、表情、口型承担了不成比例的效应 — [Unity Glossary: Uncanny Valley](https://unity.com/glossary/uncanny-valley)
- 实证研究汇编：**风格化卡通渲染的虚拟角色比「更写实但显病态」的版本评价更好**；另有研究报告「更写实的人类动画可能比卡通版本引发更少信任」，且写实角色「比 semi-realistic 角色更容易被人类归类」 — [UAL student research PDF, 2023](https://rstolk.myblog.arts.ac.uk/files/2023/01/Uncanny-Valley-1.pdf)
- 较新研究结论：**当前最先进（state-of-the-art）的虚拟人已不再陷于 uncanny valley**，被评为比低质量表征更有吸引力、更像人、更不怪异 — [Trinity College Dublin TARA repository](https://www.tara.tcd.ie/bitstreams/dca55b6e-8821-46f2-9dd7-cb1272e15996/download)
- VFX 行业视角（Image Engine 视效总监）：跨越谷底「需要更少的炫技、更多的躲在幕后」；制作完全写实的 digital double 仍「极其昂贵且耗时」 — [Image Engine: The secrets of creating real-looking CG digital doubles](https://image-engine.com/insight/the-secrets-of-creating-real-looking-cg-digital-doubles/)；另见 [IEEE Spectrum: Digital Actors Go Beyond the Uncanny Valley](https://spectrum.ieee.org/computing/software/digital-actors-go-beyond-the-uncanny-valley)
- 游戏学术会议 SBGames 2012 有专文讨论 CG 角色写实度与 uncanny valley（计算方向论文） — [SBGames 2012 comp-full_14](https://www.sbgames.org/sbgames2012/proceedings/papers/computacao/comp-full_14.pdf)
- **Epic MetaHuman（2021-02 发布）**：被媒体描述为生成「hyperrealistic virtual humans」的工具 — [Voicebot.ai 2021-02-15](https://voicebot.ai/2021/02/15/epic-games-launches-metahuman-creator-to-generate-hyperrealistic-virtual-humans/)；发布时 PC Gamer 评论标题直接称其为 "pure uncanny valley" — [PC Gamer](https://www.pcgamer.com/uk/epics-new-metahuman-tool-is-pure-uncanny-valley)
- MetaHuman 的设计中心是写实：因基于真人 3D 扫描，Creator 只能产出「可信的人类」，**没有过度夸张特征、没有风格化角色、没有幻想生物**；外星/科幻设计需用其他工具 — [Puget Systems: MetaHumans, a look past the hype](https://www.pugetsystems.com/labs/articles/metahumans-a-look-past-the-hype-2139/)
- Epic 官方 spotlight《Daughter of the Inner Stars》：MetaHuman「强项在写实」，团队以 MetaHuman 面部/身体为基底，通过头发、服装、面部定制得到「更风格化、手绘感（hand-painted）的美学」；非人形生物需完全自定义 — [Unreal Engine Spotlight](https://www.unrealengine.com/spotlights/crafting-stylized-digital-humans-on-daughter-of-the-inner-stars-with-metahuman-and-ue5)
- Epic 数字人技术 VP Vladimir Mastilovic 将目标表述为构建「truly convincing digital humans」 — [Freethink: MetaHuman](https://www.freethink.com/hard-tech/metahuman)
- 一项韩国研究比较 MetaHuman 写实动画与卡通风格动画，认为写实动画需要「与现有动画镜头选择不同的方法」 — [KoreaScience JAKO202228453749636](https://koreascience.or.kr/article/JAKO202228453749636.pdf)

### Inferences
- 业界对写实度的分级是**连续谷线上的工作区段**，而非正式分类：(1) cartoon/stylized（谷左侧安全区，Pixar/Illumination/游戏多数角色），(2) semi-realistic/stylized-realistic（谷缘，风险区——写实比例+简化材质，或反之），(3) realistic（谷底或谷右坡，MetaHuman 默认区），(4) digital double / hyper-real（谷右侧，需 VFX 级投入）。这一四档划分与搜索到的词汇（cartoon / semi-realistic / realistic / digital double / hyperrealistic）一致，但**没有单一来源给出全部四档的定义**。
- 对 AI 人像而言，uncanny valley 文献最有价值的贡献是提醒：**写实度不是单轴**——面部几何（shape）写实度、材质/皮肤渲染（material/texture）写实度、动作写实度可以分离，不匹配（例如写实皮肤 + 卡通眼睛）才是「怪异」的主要来源。因此分类轴至少应把「形体/比例写实度」与「材质/渲染写实度」拆开。
- MetaHuman 的经验（写实底模可被推向手绘风格化）说明「3D 写实基底 + 风格化表面」是一个真实存在的中间类别（对应下文 Q3 的 hybrid look），应在 taxonomy 中有位置。

### Gaps
- **未能找到**任何 Epic / Weta / ILM / Pixar / Disney / Illumination 的 SIGGRAPH/GDC 讲座原文，其中明确定义 cartoon→stylized→semi-realistic→realistic→digital double 的分级；搜索配额耗尽前未查到。建议下一轮查询："Pixar believability vs realism stylized Up Toy Story 4 skin shading talk"、"realism spectrum character design chart Disney stylized"、"Weta digital human Alita Gemini Man SIGGRAPH"。
- **背景记忆（未核实）**：Zell, Aliaga, Jarabo, Zibrek, Mastilovic, McDonnell 等 2015 年 SIGGRAPH 论文 "To Stylize or not to Stylize? The Effect of Shape and Material Stylization on the Perception of Computer-Generated Faces" 把面部写实度拆为 **shape realism × material realism** 两轴并做了知觉实验（并有 Zibrek/McDonnell 的后续 VR 研究）。这是把 uncanny valley 二维化、与本报告「比例轴 × 渲染轴」最直接对应的学术工作，**强烈建议核实并引用**（本轮查询被配额截断）。
- **背景记忆（未核实）**：MacDorman & Chattopadhyay 2016 "Reducing consistency in human realism increases the uncanny valley effect; increasing category uncertainty does not"（Cognition）——即「写实度一致性」比绝对写实度更重要。建议核实。
- Mori 原文中的例子（industrial robot、toy robot、bunraku puppet、prosthetic hand、corpse、zombie）、movement 对曲线的放大作用、以及「以适度类人程度为设计目标」的建议，均因无法读取 Spectrum 全文而未能引用；这些是原始论文的核心内容，报告引用前需回原文核对。

---

## Key Question 3 — 计算机图形学渲染分类：Photorealistic（PBR/SSS/ray tracing）vs Non-Photorealistic Rendering（NPR），以及 "3D that looks 2D" 混合风格的具体技术（Arcane / Spider-Verse / Guilty Gear Xrd / Puss in Boots 2 / TMNT Mutant Mayhem / The Bad Guys / Wolfwalkers）

### Takeaway
NPR 文献（Lansdown & Schofield 1995；Kyprianidis, Collomosse, Wang & Isenberg 2013 等）把「艺术化风格化」按技术路径分类（笔触/区域/滤波/示例驱动等），而业界 2015–2023 年的「3D 看起来像 2D」作品则显示 hybrid look 由**一组可拆分的技术开关**组成：(1) 手绘/绘画式贴图取代 PBR 材质，(2) 自定义 cel/threshold 着色取代物理光照，(3) 显式线稿层（inking / 3D ribbon lines / inverted hull），(4) 降帧与变帧率（on 2s/3s、stepped animation），(5) 2D 手绘 FX 与印刷/介质伪影（halftone、speed lines、pencil texture），(6) 不用运动模糊。这些开关正是人像 taxonomy 中 shading、linework、texture/medium、motion（静态图可忽略）等轴的工业原型。

### Cited Findings

**NPR 学术分类**
- Kyprianidis, Collomosse, Wang & Isenberg, "State of the 'Art': A Taxonomy of Artistic Stylization Techniques for Images and Video", *IEEE TVCG* 19(5): 866–885, May 2013, doi 10.1109/TVCG.2012.160：覆盖 2D 图像/视频的 NPR，**按各技术的设计特征与行为组织分类**，追溯自 1990 年代初的半自动绘画系统到 1990 年代末梯度驱动的 painterly rendering，结尾讨论用户与美学评估等开放问题 — [Isenberg 作者页](https://tobias.isenberg.cc/p/Kyprianidis2013SAT)；[HAL hal-00781502](https://hal.archives-ouvertes.fr/hal-00781502)；[Surrey 作者版 PDF](https://personalpages.surrey.ac.uk/j.collomosse/pubs/Collomosse-TVCG-2012.pdf)
- Lansdown & Schofield (1995), "Expressive Rendering: A Review of Nonphotorealistic Techniques", *IEEE CG&A*：综述 15+ 种方案并据此**定义了一个把 NPR 系统与写实渲染系统区分开的框架**（早期、偏 3D 的框架） — [sci.utah.edu 文献条目](https://sci.utah.edu/~kpotter/Library/Papers/lansdown:1995:RNPR/index.html)
- Sayeed & Howard (2006), "State of the Art Non-Photorealistic Rendering (NPR) Techniques", TPCG 2006，聚焦可视化方向的 NPR — [Eurographics DL](https://diglib.eg.org/xmlui/handle/10.2312/LocalChapterEvents.TPCG.TPCG06.089-098)
- Al-Rousan et al. (2015), "Interactive non-photorealistic rendering", *Jurnal Teknologi*：给出交互式 NPR 技术分类，聚焦 **stylized shading 与 line drawing** 两大类 — [LJMU repository](https://researchonline.ljmu.ac.uk/id/eprint/8072/)

**Cel shading 的定义（渲染侧）**
- Cel shading 把光分成少数几个平坦、边界明确的区域（亮部、暗部、有时加一处受控的高光），而非连续渐变；名称源于传统动画把角色画在透明醋酸片（cel）上 — [UDIT: Cel shading 定义与步骤](https://www.udit.es/en/cel-shading-que-es-su-proceso-paso-a-paso-y-10-ejemplos-imprescindibles/)
- 术语原本仅指平坦着色本身；**人们如今联想到的黑色轮廓线是后来加入的**："the term 'cel-shading' is popularly used to refer to the application of this 'ink' outlining process … although originally the term referred to the flat shading technique regardless of whether the outline was applied" — [Wikipedia: Cel shading（2022 存档）](https://webcf.waybackmachine.org/web/20220430094050/https://en.wikipedia.org/wiki/Cel_shading)；另见 [Adobe: Cel shading](https://www.adobe.com/uk/creativecloud/animation/discover/cel-shading.html)

**Guilty Gear Xrd（Arc System Works，2014 游戏；Motomura 讲座 2015）— anime 边界参照**
- 技术美术 Junya C. Motomura 的讲座：团队「摒弃数学准确性」，以在复杂 3D 角色上获得完全一致的 cel shading；同时讲解可缩放贴图与 anime 风格烟雾技法 — [BlenderNation 2015-07-26](https://www.blendernation.com/2015/07/26/junya-c-motomura-behind-the-scenes-of-guilty-gear-xrd/)
- Motomura 幻灯片：团队已用 2D 做过 BlazBlue，想做不同的东西；cel-shaded 3D 是最有前景的选项；外观来自**自定义 cel shader + 专为该 shader 建模的 3D 模型**；相机在特殊攻击时在 3D 空间移动 — [Motomura 幻灯片 PDF (ggxrd.com)](https://www.ggxrd.com/Motomura_Junya_GuiltyGearXrd.pdf)
- 第三方分析："GuiltyGearXrd's Art Style: The X Factor Between 2D and 3D"：归功于角色建模设计、贴图技法、复现传统 anime 角色着色的自定义 cel shader；**每个角色有独立的自定义光源**，只影响自身 — [VideoHighlight 摘要](https://videohighlight.com/v/yhGjCzxJV3E)
- 营销材料描述为 "Limited 3D Animation" 系统：看起来像 2D 但在所有角度保持一致；粉丝分析：cel shader + 定格式 limited animation 使 3D 模型实际呈现为 2D sprite — [New Frame Plus 字幕 (Amara)](https://amara.org/videos/bDmpkclvfB5I/en/3103527)；[Polycount 讨论](https://polycount.com/discussion/comment/2344470)

**Spider-Man: Into the Spider-Verse（2018）/ Across the Spider-Verse（2023）— Sony Pictures Imageworks**
- befores & afters（2023-06-28）：这是「第一部有专门 inking 团队的 CG 动画电影」；团队为线稿构建了 Houdini 工具 **Kismet**，线稿需随角色运动更新并与**变化的动画帧率**同步 — [befores & afters 2023-06-28](https://beforesandafters.com/2023/06/28/this-was-the-first-cg-animated-movie-ive-ever-heard-of-that-actually-had-a-dedicated-inking-team/)
- SIGGRAPH 2023 Talk "Linework in Spider-Man: Across the Spider-Verse"（Grochola, Maccari, Lee, Boulet-Gilly）：在 3D 中生成艺术线稿、允许美术重画线条且线条仍跟随底层动画 — [SIGGRAPH History](https://history.siggraph.org/learning/linework-in-spider-man-across-the-spider-verse-by-grochola-maccari-lee-and-boulet-gilly)；DOI 10.1145/3587421.3595413 — [Unpaywall](https://unpaywall.org/10.1145%2F3587421.3595413)
- SIGGRAPH 2023 Talk "Fitting Variable Rate Animation into a Modern Feature Film Pipeline"（Oskarsson & Chazot）：stepped animation 与需要逐帧恒定求值的模拟部门冲突；第一部只部分解决，续集建立了端到端非破坏性 pipeline 层 — [SIGGRAPH History](https://history.siggraph.org/learning/fitting-variable-rate-animation-into-a-modern-feature-film-pipeline-by-oskarsson-and-chazot)；DOI 10.1145/3587421.3595456
- SIGGRAPH 2023 Talk "Repainting the Spider-Verse"：模拟笔触运动与颜料流动的 painting FX，而非后期合成叠加 — DOI 10.1145/3587421.3595463 [Unpaywall](https://unpaywall.org/10.1145%2F3587421.3595463)
- fxphd 对 Spider-Verse SIGGRAPH 分享的报道（"realism and design"） — [fxphd](https://www.fxphd.com/fxblog/spider-verse-at-siggraph/)
- 二手博客描述「粗颗粒 halftone」为漫画感的一部分，并称 Imageworks 用 stepped animation / animating on twos 实现 — [Prolific Studio blog（非一手）](https://blog.prolificstudio.co/blog/spiderman-into-the-spiderverse/)

**Arcane（Fortiche，2021/2024）**
- Arcane 以 3D 模型为基底，美术在其上进行 2D 绘制（贴图、细节、表现性线稿）；**阴影与高光由美术手工绘制在 3D 模型上，而非由软件计算光照** — [Dark Skies Film: Deconstructing Arcane's animation style](https://darkskiesfilm.com/what-style-of-animation-is-arcane/)；[Dark Skies Film: Is Arcane 2D or 3D](https://darkskiesfilm.com/is-arcane-2d-or-3d-animation/)
- 叠加的 2D 元素：烟雾/爆炸等手绘 FX、油画风环境、角色表情的 cel-shading；Fortiche 刻意把这些元素以 **12 fps** 动画化，造成 Jinx 特效的「卡顿感」 — [Red Shark News](https://redsharknews.com/why-netflixs-arcane-looks-so-good-how-fortiche-ramped-up-the-animation-pipeline)；[Dark Skies Film](https://darkskiesfilm.com/what-style-of-animation-is-arcane/)
- 常被提及的工具：Photoshop 与 Substance Painter 绘制贴图，Nuke / After Effects 合成；据报道 Fortiche 自研 shader 工具把手绘贴图与 3D 模型整合 — [Red Shark News](https://redsharknews.com/why-netflixs-arcane-looks-so-good-how-fortiche-ramped-up-the-animation-pipeline)（**注意**：搜索结果中多条为低质量/疑似 AI 生成博客，工具与流程细节应以 Fortiche 官方访谈为准）

**Puss in Boots: The Last Wish（DreamWorks，2022）**
- 导演 Joel Crawford 称风格为 "fairy tale painting" look；模型起点相同，但**完成度/细节层级按「想要多 painterly」而变化**；美术设计 Nate Wragg：把表面简化到「插画级细节」而非写实 — [TheWrap](https://www.thewrap.com/puss-in-boots-the-last-wish-behind-the-scenes-video/)；[AWN: returns to its fairy tale illustration roots](https://www.awn.com/animationworld/puss-boots-last-wish-returns-its-fairy-tale-illustration-roots)
- 大量使用 **stepped animation**（不逐帧动画、按动作段落改变 step）；视效总监 Mark Edwards 描述 2D 手绘的 "scalping" 外观以在体积特效上获得硬边+柔和；动作场面更 graphic、受 anime 影响 — [AWN: Mark Edwards talks visual development](https://awn.com/animationworld/mark-edwards-talks-visual-development-puss-boots-last-wish)；[VFX Voice](https://vfxvoice.com/wishing-upon-a-star-for-puss-in-boots-the-last-wish/)；[Deccan Herald](https://deccanherald.com/entertainment/entertainment-news/puss-in-boots-the-last-wish-revels-in-fairy-tale-style-animation-1190105.html)

**TMNT: Mutant Mayhem（Mikros Animation / Cinesite，2023）**
- Mikros 视效总监 Matthieu Rouxel：风格化 2D 与写实摄影感的混合；2D 外观要像「青少年在速写本里画的电影」，匹配参考画的**铅笔质感与松散感**；**刻意在透视、比例、轮廓中加入不完美**，避免数字感 — [befores & afters: 'We wanted to imply teenage imperfection everywhere'](https://beforesandafters.com/2023/09/07/we-wanted-to-imply-teenage-imperfection-everywhere/)
- 轮廓线作为 **Maya 中的 3D ribbon** 建立、经 Katana 渲染；Rouxel：「没有这些线，角色显得赤裸」 — [befores & afters: Crafting new tools](https://beforesandafters.com/2023/09/07/crafting-new-tools-and-hacking-existing-ones-to-hit-a-stylized-aesthetic/)；[Creative Bloq](https://creativebloq.com/features/tmnt-VFX)
- FX 以 Toon Boom Harmony 2D 排版起步（火、烟、水花）再整合进 3D 环境；Houdini + Arnold 负责破坏与最终渲染；**用 3D speed lines 取代传统 motion blur**；动画具 choppy 手绘感 — [Mikros Animation news](https://www.mikrosanimation.com/en/news/behind-the-mikros-magic-crafting-explosive-fx-in-tmnt-mutant-mayhem/)
- Cinesite 承担约 25 分钟镜头，需自研工具匹配 Mikros；动作线「在 3D 中绘制、以 2D 渲染处理」，并组建专门的 2D FX 部门 — [Cinesite](https://cinesite.com/tmntmutantmayhem/)；[Kidscreen](https://kidscreen.com/?p=203592)

### Inferences
- 把上述作品并置可以提炼出一张「hybrid look 技术开关表」，其中与**静态人像**相关的轴有：
  1. **Shading model**：物理光照（PBR/SSS） → 手绘光影贴图（Arcane） → 阈值 cel（GGXrd，anime 边界） → 区域简化 painterly（Puss in Boots）。
  2. **Linework**：无线（多数 PBR/Pixar） → 可选局部线（Spider-Verse 的手绘 inking） → 全轮廓线（GGXrd inverted-hull 式；TMNT 3D ribbon）；线的质感再分：干净矢量线 / 铅笔松散线（TMNT） / 笔刷线（Spider-Verse）。
  3. **Texture / medium**：扫描级皮肤材质 → 油画/厚涂质感（Arcane、Puss in Boots） → 印刷伪影（halftone、misprint；Spider-Verse） → 铅笔颗粒（TMNT）。
  4. **Geometric fidelity / imperfection**：精确透视与比例 → 刻意的比例/透视不完美（TMNT）。
  5. **Motion**（帧率、speed lines）对静态人像不适用，但提示「运动风格化」是动画风格的第 5 维，可在 taxonomy 中明确排除。
- Guilty Gear Xrd 代表「3D 彻底伪装成 anime 2D」的极端；其 per-character 光源、阈值 cel、无插值动画是 anime 边界的技术定义——对本报告（排除 anime）而言可作为**边界参照点**：凡 shading 为硬阈值双色/三色 + 干净等宽轮廓 + 大眼小鼻的比例，归入 anime 侧。
- NPR 学术分类是**按生成算法**（stroke-based、region-based、filtering、example-based）而非按视觉结果分类；对 AI 人像分类更有用的是其隐含的输出维度：笔触尺度/方向性、区域平坦化程度、边缘/线提取、色彩量化。报告可引用 Kyprianidis 2013 作为「技术分类 ≠ 风格分类」的论据。

### Gaps
- **The Bad Guys（DreamWorks 2022）与 Wolfwalkers（Cartoon Saloon 2020）**：未能检索（配额在相关查询前耗尽）。背景记忆（未核实）：The Bad Guys 以 2D 插画感、手绘线稿叠加、简化光照为特点；Wolfwalkers 为纯 2D 手绘，以「城镇=直线/木刻几何、森林=圆润水彩、狼视角=炭笔线稿」的三套视觉语言著称。建议下一轮查询："The Bad Guys DreamWorks look development linework Pierre Perifel"、"Wolfwalkers woodcut town vs forest visual language Tomm Moore"。
- Spider-Verse 的 **Ben-Day dots / halftone、misprint 色差（chromatic offset）、无 motion blur、Kirby krackle、手绘 hatching** 等具体伪影在一手来源中未得到确认（仅二手博客提及 halftone）。背景记忆（未核实）：Imageworks 的 Danny Dimian / Josh Beveridge 等在 2019 年 SIGGRAPH/GDC 讲座中讨论过这些；可查 "Spider-Verse look of picture Dimian Beveridge SIGGRAPH 2019"。
- Guilty Gear Xrd 讲座的会议归属（GDC 2015）未在搜索结果中得到官方确认；BlenderNation 文章日期为 2015-07-26。背景记忆（未核实）：GDC 2015 讲题为 "GuiltyGearXrd's Art Style: The X Factor Between 2D and 3D"，关键技术包括 vertex color 控制阴影阈值偏移与轮廓线粗细、以 ILM（inner line map）贴图承载内线、无插值的 limited animation、对相机的透视矫正变形。需 GDC Vault 核实。
- Pixar / Disney / Illumination 的 "stylized realism" / "believable not realistic" 讲座未检索到。
- Arcane 的一手来源（Fortiche 艺术总监/CG 总监访谈、Annecy/FMX 讲座）未检索到；现有来源多为二手且质量不均。

---

## Key Question 4 — 动画/插画行业关于角色着色与渲染的词汇：flat shading、cel shading、soft shading、rendered/painterly、line-and-color vs lineless、semi-realism、stylized realism；中文术语 厚涂 / 平涂 / 赛璐璐

### Takeaway
行业词汇大致沿「着色离散程度 × 线稿存在与否 × 介质拟真度」三个方向分布：cel/平涂/赛璐璐（硬边分区着色，通常带线）→ soft shading（渐变过渡，常与 cel 混用）→ painterly/厚涂/rendered（多层叠色、笔触、常趋 lineless）。中文社群（萌娘百科）明确把「平涂」视为与「赛璐璐」同义的**技法而非画风**，并指出主流插画多为「赛璐璐为主 + 厚涂/水彩局部」的混合。**semi-realism、stylized realism、lineless 等术语在本轮未找到任何正式定义来源**，属于社群约定。

### Cited Findings
- Cel shading = 把光分成平坦明确的区域（亮/暗/受控高光），非连续渐变；源于透明醋酸片（cel）动画 — [UDIT](https://www.udit.es/en/cel-shading-que-es-su-proceso-paso-a-paso-y-10-ejemplos-imprescindibles/)；[Adobe](https://www.adobe.com/uk/creativecloud/animation/discover/cel-shading.html)
- 术语原指平坦着色本身，黑色轮廓线是后来才被绑定进该词的 — [Wikipedia: Cel shading（存档）](https://webcf.waybackmachine.org/web/20220430094050/https://en.wikipedia.org/wiki/Cel_shading)
- Soft shading：仅有部分定义——「与 cel 相比更易混合颜色、形成更柔和的外观」；一位画师描述折中做法：**面部等细微阴影用 soft shading，硬阴影用 cel shading**；另一帖描述「soft cel」——更多渲染与平滑使其读作 painterly，暗示 painterly 位于 flat cel 与 full rendering 之间 — [UDIT](https://www.udit.es/en/cel-shading-que-es-su-proceso-paso-a-paso-y-10-ejemplos-imprescindibles/)；[Artfol 画师帖](https://artfol.app/a/oBA9KMM)（非正式）
- 中文术语「赛璐璐/赛璐珞（Celluloid）」：原为用赛璐珞材料制作动画的技法，后引申为**线条清晰、颜色分明**的整体画面风格；现今基本指该画风及其上色技法，**又称平涂**；多数彩色漫画几乎全为赛璐璐风，因连载时限难以逐帧使用厚涂等长周期技法；常用正片叠底/线性加深图层上色；严格说该词适用于数字（CG）作品 — [萌娘百科：赛璐璐](https://zh.moegirl.org.cn/%E8%B5%9B%E7%92%90%E7%92%90)；[萌娘百科：平涂](https://zh.moegirl.org.cn/%E5%B9%B3%E6%B6%82)
- 萌娘百科编辑讨论：把「平涂」当作独立于赛璐璐的画风是「近乎过时的概念，只有少数网络画班仍在用」；并主张平涂是**技法而非画风**，不应放进画风分类 — [萌娘百科 Template_talk:绘画](https://zh.moegirl.org.cn/Template_talk:%E7%BB%98%E7%94%BB)
- 「厚涂」在来源中与赛璐璐对举（多层叠色、柔和混合、带笔触质感、耗时更长）；**插画中最常见的是「赛璐璐为主，混合厚涂或水彩」**，游戏 CG、角色立绘、小说封面常用此混合；起稿方式不定义风格（厚涂画师也可有整洁线稿，或直接从色块起手） — [萌娘百科：厚涂](https://zh.moegirl.org.cn/%E5%8E%9A%E6%B6%82)；[萌娘百科：赛璐璐](https://zh.moegirl.org.cn/%E8%B5%9B%E7%92%90%E7%92%90)
- 渲染侧 NPR 文献把 sketch / oil painting / ink painting 外观并列为可模拟的目标介质 — [UDIT](https://www.udit.es/en/cel-shading-que-es-su-proceso-paso-a-paso-y-10-ejemplos-imprescindibles/)

### Inferences
- 中文社群「平涂是技法不是画风」的立场对 taxonomy 设计有直接意义：**shading 应作为独立轴**（flat/cel → soft/blended → painterly/厚涂 → photoreal rendering），而不是与「画风名」混为一层；同一「画风」（如 Western comic）可以出现在该轴的多个刻度上。
- 赛璐璐（硬边分区着色 + 清晰线）在中英文语境中几乎等同于 anime/漫画着色法，可用作本报告的 anime 边界指标之一；但要注意 cel shading 也存在于非 anime 作品（Western toon shading、vector 插画），因此**线稿风格 + 比例**才是把 anime 与非 anime 区分开的关键，而非 shading 本身。
- 「soft shading」在实践中常是混合策略（面部柔和、衣物硬边），因此分类时应允许「主导 shading」+「次要 shading」双标签，或用连续量（硬边比例）而非单一类目。

### Gaps
- **semi-realism / semi-realistic**：未检索到任何定义性来源（搜索配额耗尽）。背景记忆（未核实）：社群通常用它指「写实的光影/材质渲染 + 风格化（放大眼睛、简化鼻唇）的比例」，或反之；DeviantArt/ArtStation 社群与 Clip Studio 教程常用此词。建议下一轮查询："semi-realism definition art community stylized features realistic shading"。
- **stylized realism**（游戏业，如 Blizzard Overwatch、Riot）：未检索到；背景记忆（未核实）：Overwatch 美术常被描述为 "stylized realism / painterly-handpainted PBR"，GDC 2017 讲座中有相关论述。建议核实 GDC Vault。
- **lineless / line-and-color** 二分：未检索到定义来源。
- **艺术教育机构（Proko、Schoolism、ArtStation Learning、Ctrl+Paint）** 的标准定义：未检索到；本轮无来源可引。
- 「rendered」在插画社群中作「高完成度、多层光影」之意的用法：无来源。

---

## Key Question 5 — 生成模型与计算机视觉中的风格分解：Somepalli et al. 2024（CSD）、WikiArt/ArtBench 分类、StyleDrop、StyleAligned、IP-Adapter/InstantStyle 对 style 的界定、风格综述；复现的维度

### Takeaway
学术侧对「style」有两种取向：(a) **以标签为锚**（WikiArt/ArtBench 用艺术史流派当类别；CSD 用 LAION-Styles 多标签对比学习得到可检索的风格嵌入），(b) **以属性为描述**（StyleDrop 把 style 描述为 color schemes、shading、design patterns、local/global effects、textures、3D appearance）。两者共同暗示的可复用维度是：色彩方案、着色方式、纹理/笔触、图案/设计语言、整体与局部效果、介质/3D 感；但**没有一篇被检索到的论文给出正式的风格维度本体**，CSD 的 LAION-Styles 标签构成细节与 InstantStyle/StyleAligned/IP-Adapter 的措辞本轮均未能核实。

### Cited Findings
- Somepalli et al., "Measuring Style Similarity in Diffusion Models", arXiv 2404.01292（2024-04），ECCV 2024 刊出题为 "Investigating Style Similarity in Diffusion Models"：动机是现有检索工具主要匹配**语义内容**，故提出可把生成图风格归因到训练数据的风格描述子（style descriptors）；引入风格归因数据集 **LAION-Styles** 与**多标签对比学习**方案；在 **WikiArt** 与 **DomainNet** 上做零样本评估；模型名 **CSD** — [arXiv 2404.01292](https://arxiv.org/abs/2404.01292v1)；[ECCV 2024 PDF](https://www.ecva.net/papers/eccv_2024/papers_ECCV/papers/08294.pdf)；[ECCV 页面](https://www.ecva.net/papers/eccv_2024/papers_ECCV/html/8294_ECCV_2024_paper.php)
- CSD 与 CLIP 对比：在作者示例中 CSD 即使没有共同内容、只有风格相同也能匹配到正确艺术家，而 CLIP 仍优先内容导致错配 — [arXiv HTML v1](https://arxiv.org/html/2404.01292v1)
- 分数解释（ECCV 版）：作者基于对 96 位艺术家生成结果的人工检查提出启发式阈值——**单图 Style Similarity < 0.5 表示艺术家风格缺失，> 0.8 强烈表示存在** — [ECCV 2024 PDF](https://www.ecva.net/papers/eccv_2024/papers_ECCV/papers/08294.pdf)
- 代码：github.com/learn2phoenix/CSD — [arXiv](https://arxiv.org/abs/2404.01292v1)
- **ArtBench-10**（Liao, Li, Liu, Keutzer；arXiv 2206.11404，2022-06；CMU / UC Berkeley）：60,000 张艺术作品、**10 种风格、每风格 6,000 张（5,000 训练 / 1,000 测试）**；卖点是**类别平衡**（此前艺术数据集多为长尾分布）；提供 32×32、256×256、原尺寸三种版本；GitHub 发布、Fair Use 许可 — [arXiv PDF 2206.11404v1](https://arxiv.org/pdf/2206.11404v1.pdf)；[Hugging Face papers](https://huggingface.co/papers/2206.11404.md)；[Papers with Code: ArtBench-10](https://PapersWithCode.com/dataset/artbench-10)
- ArtBench-10 的部分风格名可从 HF 镜像文件名确认：Baroque、Realism、Ukiyo-e、Surrealism、Art Nouveau（完整 10 项未在搜索结果中确认） — [Hugging Face](https://huggingface.co/papers/2206.11404.md)
- **StyleDrop**（Google Research，NeurIPS 2023；arXiv 2306.00983）：目标是捕获参考图的 style 而非主体；论文把 style 的细节描述为 **"color schemes, shading, design patterns, and local and global effects"**；图注称生成图捕获了 **"colors, shading, textures and 3D appearance"** 等细微差别；只微调 <1% 参数、可从单张参考图工作；命名取自「吸管/取色器」隐喻 — [NeurIPS 2023 poster](https://neurips.cc/virtual/2023/poster/71988)；[NeurIPS 论文 PDF](https://papers.neurips.cc/paper_files/paper/2023/file/d33b177b69425e7685b0b1c05bd2a5e4-Paper-Conference.pdf)；[arXiv 2306.00983](https://www.arxiv.org/abs/2306.00983)
- NPR 侧的「艺术风格化」分类综述 Kyprianidis et al. 2013 按技术设计特征组织（见 Q3） — [Isenberg 作者页](https://tobias.isenberg.cc/p/Kyprianidis2013SAT)

### Inferences
- 从 ArtBench/WikiArt 到 CSD 的演进说明：学界已承认「以艺术史流派为类」的扁平标签不足以刻画生成图风格（CSD 转向多标签 + 连续嵌入）。这为本报告「多轴而非扁平名单」的主张提供了直接的学术先例。
- 把 StyleDrop 的属性清单与 Q3 的工业技术开关对照，可得到跨领域一致的维度集合：**color palette / shading / texture & brush / pattern & design language / global vs local effects / 3D-ness（体积与材质感）**。再加上 McCloud 的 realism–iconic 轴与 uncanny valley 文献的 shape vs material 拆分，便构成人像 taxonomy 的候选主轴。
- CSD 的 0.5/0.8 阈值提示：未来若用嵌入做自动分类，可用「风格相似度分布」校准轴刻度（例如把一组参考人像两两相似度聚类，看自然断点是否对应 shading/linework 的离散刻度）。

### Gaps
- **CSD 的 LAION-Styles 标签构成**（标签数量、是否由艺术家名 + 介质 + 流派组成、如何从 LAION 文本抽取）——搜索摘要未给出，原文无法访问。背景记忆（未核实）：标签来自 LAION-Aesthetics 字幕中出现的艺术家/流派/介质词表（约数千个），并用 Nearest-neighbor 做多标签对比。**需核实**。
- **WikiArt 的 27 个 style 类别 / 10 genre / 23 artist 划分**（Tan et al. ArtGAN 2016 版本）：查询被配额截断，无来源可引。
- **InstantStyle（2024）、StyleAligned（Hertz et al., CVPR 2024）、IP-Adapter（2023）** 对 style 的措辞：未检索到。背景记忆（未核实）：InstantStyle 论文把 style 描述为涵盖 "color, material, atmosphere, design, structure" 等因素并承认其「under-determined」；StyleAligned 强调跨图共享注意力以保持风格一致，未给维度定义；IP-Adapter 以图像提示整体注入、不区分内容与风格。**均需核实**。
- **2024–2026 年的 style-conditioned generation benchmark（如任何名为 "StyleBench" 的工作）**：查询未执行，无结果；不能确认是否存在。
- **艺术风格在 CV 中的综述**（style transfer survey、"artistic style representation" 综述）：未检索到。
- 任何论文中出现的**显式维度列表**（color / texture / line / shape-geometry / lighting / composition / medium）的逐篇统计：本轮仅 StyleDrop 一篇有可引措辞，不足以做「复现频次」统计。

---

## Key Question 6 — 已发布的 AI 生成图像风格分类体系：Adobe Firefly Styles、Recraft 风格树、Oppenlaender 的 prompt modifier taxonomy（2022/2023）

### Takeaway
三个体系代表三种组织逻辑：**Adobe Firefly** 以「效果」为单位分成 Popular / Movements / Themes / Techniques / Effects / Materials / Concepts 七组（扁平多选、无正式定义，200+ 项），并把 Color、Lighting、Camera angle 作为独立的「extended style components」；**Recraft** 采用两层树：4 个 base class（realistic_image / digital_illustration / vector_illustration / icon，各有文字定义）→ substyle；**Oppenlaender** 则从使用者实践出发把 prompt 中的修饰词分成 6 类（其中 style modifiers 只是一类）。三者都没有把「人像写实度」作为显式轴，但 Recraft 的 base class 定义（以纹理简化程度与色彩数量区分）最接近一条「渲染写实度」轴。

### Cited Findings

**Adobe Firefly**
- 官方帮助页把 Effects 分为若干类并各举例：**Movements**（Art deco、Art nouveau、Baroque、Fantasy 等）；**Techniques**（Acrylic paint、Bold lines、Digital fractal、Doodle drawing 等）；**Effects**（Antique photo、Bokeh effect、Bioluminescence、Color explosion 等）；**Materials**（3d patterns、Charcoal、Claymation 等，「赋予特定材质的观感」）；**Concepts**（Bohemian、Chaotic、Dais、Electric 等） — [Adobe Help: Effects for generated images](https://helpx.adobe.com/ae_ar/firefly/web/work-with-images/generate-images/effects-for-generated-images.html)；[Adobe Help（移动端）: Set effects for image generation](https://helpx.adobe.com/ee/firefly/mobile/generate-images-with-text-to-image/customize-generated-images/set-effects-for-image-generation.html)
- 帮助页还列出 **Popular** 与 **Themes**（例如 3D、Anime、Cinematic）两组 — [Adobe Help](https://helpx.adobe.com/ae_ar/firefly/web/work-with-images/generate-images/effects-for-generated-images.html)；[Adobe Learn: Generate images with built-in Effects](https://www.adobe.com/learn/firefly/web/generate-gorgeous-images)
- 「Extended style components，如 Effects、Color、Lighting、Camera angle，仅对 Adobe 原生图像模型可用；合作伙伴模型不支持」 — [Adobe Help](https://helpx.adobe.com/ae_ar/firefly/web/work-with-images/generate-images/effects-for-generated-images.html)
- Adobe 社区 2025-08 的求助帖询问各类别的详细定义，回复称「尚未创建逐项详细指南」 — [Adobe Community thread](https://community.adobe.com/t5/adobe-firefly-discussions/guide-to-firefly-movements-themes-techniques-effects-materials-and-concepts/m-p/15458865)
- 第三方手册声称涵盖 Firefly「200+ style effects」的演示 — [Gutenberg 书目：Master Generative AI Art … with Adobe Firefly](https://www.self.gutenberg.org/wplbn0100750234-master-generative-ai-art-content-creation-with-adobe-firefly-by-kolenkina-anna-ms-.aspx)（非官方数字）

**Recraft**
- API 文档：**四类 base style——realistic image、digital illustration、vector illustration、icon** — [Recraft API: Styles](https://www.recraft.ai/docs/api-reference/styles)
- 定义：**realistic** = 「看起来就像普通数码相机/手机/胶片相机拍的照片」；**digital illustration** = 涵盖大多数非照片艺术，「与写实图像的主要区别在于使用简化的纹理（如 3D 渲染或手绘图像那样），或以某种创意方式风格化」；**vector illustration** = 类矢量图形，「通常同时只用少数几种颜色，形状以纯色或简单渐变填充」 — [Recraft API: Styles](https://www.recraft.ai/docs/api-reference/styles)
- V3 的 realistic substyles 含 b_and_w、hdr、natural_light、**studio_portrait** 等；第三方文档列出 digital illustration substyles 如 pixel_art、hand_drawn、grain、2d_art_poster；可用 substyle 随模型而异；**styles 尚不支持 V4 模型** — [Recraft API: Appendix](https://www.recraft.ai/docs/api-reference/appendix)；[moda.app: Recraft V3（第三方）](https://moda.app/resources/models/recraft-v3)
- Web 应用的风格面板分组与 API 不同：Photorealism、Illustration、Vector art、Vector icon、Graphic design、Vector logo、Other styles — [Recraft Docs: Selecting a style](https://docs.recraft.ai/using-recraft/image-generation/selecting-a-style)
- Recraft 博客宣布一次性新增 60 种风格 — [Recraft blog: Unlocking 60 new styles](https://www.recraft.ai/blog/unlocking-60-new-styles-for-more-engaging-visual-narratives)

**Oppenlaender — A Taxonomy of Prompt Modifiers for Text-To-Image Generation**
- 基于对线上 text-to-image 社群 **3 个月的民族志研究**，识别出 **六类 prompt modifiers**；作者定位其为研究者的概念起点，也可帮助实践者改进图像；进一步描述 modifiers 在 "prompt engineering" 实践中的应用并讨论 HCI 研究机会 — [arXiv 2204.13988](https://arxiv.org/abs/2204.13988)；[DeepAI 镜像](https://deepai.org/publication/a-taxonomy-of-prompt-modifiers-for-text-to-image-generation)
- 版本：arXiv 预印本首发 2022-04，最后修订 2023-06（v3）；同行评审版刊于 *Behaviour & Information Technology*（2023），DOI 10.1080/0144929X.2023.2286532；于韦斯屈莱大学（JYU）机构库亦有存档 — [arXiv v3 HTML](https://arxiv.org/html/2204.13988v3)；[JYU repository](https://jyx.jyu.fi/handle/123456789/92405)

### Inferences
- Firefly 的七组实为**混合粒度**：Movements（文化谱系/艺术史）、Techniques 与 Materials（介质/技法）、Effects（后期/摄影效果）、Themes（大类媒介如 3D/Anime/Cinematic）、Concepts（氛围/语义）。它暴露了商业产品常见的做法——把本应正交的轴（谱系、介质、光照、氛围）压成一个多选菜单——这正是本报告要避免的「扁平名单」；但其把 Color / Lighting / Camera angle 单列为 style components 的做法，支持把**光照**与**色彩**作为独立轴。
- Recraft 的 base-class 定义实际上是一条**「表面纹理拟真度 + 色彩量化程度」的单轴**：photo（连续纹理、连续色）→ digital illustration（简化纹理）→ vector（少量纯色/简单渐变）→ icon（极简）。这与 Q3/Q4 的 shading 轴（photoreal → painterly → cel/flat）高度对应，可作为工业化命名的参考；且 studio_portrait 等 substyle 显示其承认人像是独立子域。
- Oppenlaender 的分类是**关于 prompt 文本**而非关于图像外观，因此对画风 taxonomy 的价值在于提醒：实际使用者用艺术家名、流派名、介质名、质量词混杂地描述风格，一个好的轴系应能把这些异质修饰词映射到少数正交维度上。

### Gaps
- **Oppenlaender 六类的名称与定义**在搜索摘要中未列出，原文无法访问。背景记忆（未核实）：六类为 **subject terms、style modifiers、image prompts、quality boosters、repeating terms、magic terms**，其中 style modifiers 包含艺术家名、艺术流派、介质/技法、渲染引擎等子类。**引用前必须核实 arXiv v3 或 BIT 期刊版**。
- Firefly 的完整效果清单与每组项目数、以及「Styles」在 2025–2026 年界面中的最新组织（是否仍为七组）未能确认；官方亦无逐项定义。
- Recraft digital_illustration 下的完整 substyle 列表只来自第三方页面，官方 Appendix 页面无法访问核对。
- 其他平台（Midjourney 的 `--style`/sref、Leonardo 的 preset styles、Ideogram 的 style 选项、Stable Diffusion 社群的 style 分类如 SDXL styles JSON）本轮未覆盖。

---

## 跨框架综合（对应 Key Question 5 的「哪些维度复现」）：可直接用于人像 taxonomy 轴设计的归纳

### Takeaway
把本轮六组框架并置，复现频次最高的维度是：**(1) 形体/比例写实度（McCloud 的 reality↔language 轴；uncanny valley 的 shape realism）、(2) 渲染/着色写实度与离散度（PBR→painterly→soft→cel/flat；Recraft 的 base class；萌娘百科的 厚涂↔赛璐璐）、(3) 线稿（有/无、质感；Spider-Verse inking、TMNT ribbon lines、GGXrd outline）、(4) 介质/纹理与笔触（Firefly Techniques/Materials；StyleDrop textures；Arcane 手绘贴图）、(5) 色彩方案与色彩量化（StyleDrop color schemes；Firefly Color；Recraft vector 的少色）、(6) 光照/氛围（Firefly Lighting；GGXrd per-character light）、(7) 文化谱系/艺术史流派（WikiArt/ArtBench；Firefly Movements）**。抽象度（picture plane）与「不完美/手工痕迹」（TMNT）是两个较少被明确命名、但对人像风格区分很有用的补充轴。

### Cited Findings
- （本节为对上文已引用来源的综合；逐条来源见各节。关键锚点：McCloud 三角 [Wikipedia](https://en.wikipedia.org/wiki/Understanding_Comics)；Recraft base-class 定义 [Recraft API](https://www.recraft.ai/docs/api-reference/styles)；StyleDrop 的 style 属性措辞 [NeurIPS 2023](https://papers.neurips.cc/paper_files/paper/2023/file/d33b177b69425e7685b0b1c05bd2a5e4-Paper-Conference.pdf)；Firefly 类别 [Adobe Help](https://helpx.adobe.com/ae_ar/firefly/web/work-with-images/generate-images/effects-for-generated-images.html)；萌娘百科的技法/画风区分 [Template_talk:绘画](https://zh.moegirl.org.cn/Template_talk:%E7%BB%98%E7%94%BB)；TMNT 的刻意不完美 [befores & afters](https://beforesandafters.com/2023/09/07/we-wanted-to-imply-teenage-imperfection-everywhere/)；Spider-Verse 线稿 [SIGGRAPH 2023](https://history.siggraph.org/learning/linework-in-spider-man-across-the-spider-verse-by-grochola-maccari-lee-and-boulet-gilly)。）

### Inferences
- 建议的最小正交轴集（供报告讨论）：
  - **A. Proportion / shape realism**（写实 → 轻度风格化 → 强风格化/卡通 → 图标化）— 理论来源 McCloud；知觉证据来自 uncanny valley 文献中 shape 与 material 的分离。
  - **B. Rendering / shading realism & discreteness**（photoreal PBR/SSS → painterly 厚涂 → soft blended → cel 多阶 → flat 平涂）— 工业来源 Recraft base class、GGXrd/Arcane/Puss in Boots 技术；中文术语映射 厚涂/赛璐璐/平涂。
  - **C. Linework**（无线 → 局部/松散线 → 全轮廓干净线），并记录线的质感（铅笔/墨线/矢量）— 来源 Spider-Verse、TMNT、GGXrd、cel-shading 词源考。
  - **D. Medium / texture & mark-making**（摄影/CG 表面 → 油画/水彩/粉彩等传统介质 → 印刷伪影/颗粒 → 矢量平面）— 来源 Firefly Techniques/Materials、StyleDrop textures、NPR 介质目标。
  - **E. Color & lighting**（色彩方案、色彩量化、光照设定）— 来源 Firefly Color/Lighting components、StyleDrop color schemes。
  - **F. Cultural lineage / movement**（艺术史流派、地域传统、当代商业流派）— 来源 WikiArt/ArtBench 标签体系、Firefly Movements；此轴与 A–E 非正交但用户检索常用。
  - **Boundary flag: anime/manga**（由 A 的大眼比例 + B 的硬阈值 cel + C 的干净等宽线共同判定）— 来源 GGXrd 技术描述与赛璐璐词条。
- 与扁平「风格名单」相比，上述轴系的优势有学术先例支持：CSD 已证明以艺术家/流派标签做单一类别不足以刻画风格，转向多标签嵌入（见 Q5）。

### Gaps
- 以上轴集是**本调研的归纳**，不是任何单一文献提出的体系；没有找到一篇文献同时覆盖这 6 条轴。
- 「composition / framing」（构图、取景）在人像中是常见变量，但本轮来源仅 Firefly 的 Camera angle 组件有所涉及，无学术来源。
- 缺少对**人像特定**维度（如皮肤质感处理、眼睛的写实度、面部特征夸张方式）的框架性文献；uncanny valley 文献最接近，但 Zell et al. 2015 等关键论文未能核实（见 Q2 Gaps）。
- 由于搜索配额与网络限制，以下建议的补查清单留给下一轮：Zell et al. 2015（shape × material）；Oppenlaender 六类原文；CSD 的 LAION-Styles 构成；InstantStyle/StyleAligned 措辞；WikiArt 27 类；ArtBench 10 类全名；Spider-Verse 2019 SIGGRAPH/GDC 讲座（halftone/misprint/no motion blur）；GGXrd GDC 2015 Vault 记录；The Bad Guys 与 Wolfwalkers 的 look development 访谈；Pixar/Disney/Blizzard 关于 stylized realism 的讲座；semi-realism 的社群定义来源。
