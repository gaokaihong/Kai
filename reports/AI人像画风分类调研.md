# AI 文生图人像画风分类调研：非二次元人像到底有多少种画风，以及如何用一套坐标系把它们管起来

> 调研日期：2026-10-11　|　综合自 7 份分路调研笔记（框架与分类轴、摄影写实家族、3D 家族、2D 体积家族、英文社区分类法、中文社区分类法、2026 模型与工具版图）
>
> **读者**：用中文思考、给文生图模型写提示词的实践者。所有画风名、提示词、模型/产品名、参数名、影视/游戏/画家名均保留英文原文，可直接复制进提示词。
>
> **证据标注约定**（全文沿用）：
> - 不带标记的陈述 = 有来源支撑（来源多为搜索引擎摘要层面的页面摘录，见文末「方法与局限」）；
> - 【背景知识·未核实】= 调研者的常识性补充，本轮未能取得来源，引用前须自行核对；
> - 【推断】= 本报告对多条来源的综合归纳，不是任何单一文献的原话；
> - 带日期的模型/功能信息均以「截至该日期」理解，2026 年下半年可能已变化。

---

## 0. 一页摘要：问题的答案

**问：除了二次元，AI 文生图人像到底有多少种画风？**

**答：如果数「名字」，本报告目录收录了 6 大家族、约 40 个可命名的画风（另有 6 个与二次元接壤的边界类目）；但更有用的答案是：画风不是一张名单，而是一个 6 维坐标系里的若干「聚落」。** 同一个词（如 2.5D、半写实、厚涂、3D）在不同社区指向坐标系里完全不同的位置，这正是「画风太复杂」的真正原因——不是种类多，而是命名乱。

本报告给出的坐标系有六条轴（§2 详述）：

| 轴 | 问的是什么 | 刻度（从左到右越「风格化」） |
|---|---|---|
| **A. 形体/比例写实度**（proportion / shape realism） | 脸和身体的几何像不像真人 | 写实 → 轻度理想化 → 明显风格化（大眼、小鼻） → 卡通/Q 版 → 图标化 |
| **B. 着色/渲染方式**（shading / rendering model） | 光影是怎么「算」出来或「画」出来的 | 照片级 PBR/SSS → 厚涂 painterly → 柔和渐变 soft → 多阶 cel → 平涂 flat |
| **C. 线稿**（linework） | 有没有线、线是什么质感 | 无线 → 局部/松散线 → 全轮廓干净线；线质：铅笔 / 墨线 / 矢量 |
| **D. 介质与笔触/工艺痕迹**（medium / texture / mark-making） | 画面「材料」是什么 | 传感器照片 → CG 表面 → 油画/水彩等传统媒材 → 印刷伪影（网点、套印错位、纸纹） → 矢量平面 |
| **E. 色彩与光照**（color & lighting） | 配色方案、色阶数、光源设定 | 连续色/自然光 → 电影调色 → 马卡龙/高饱和 → 2–3 色专色 |
| **F. 文化谱系**（cultural lineage） | 这套审美从哪条传统来 | 摄影门类 / 好莱坞 CG / 游戏美术 / 美漫 / 欧漫 / 韩漫 / 国风 / 艺术史流派 / 潮玩设计…… |

再加一个**边界旗标**：anime/二次元 =「A 轴大眼小鼻比例 + B 轴硬阈值 cel + C 轴干净等宽线」三者同时满足。只要有一项不满足，就落回本报告范围。

**用户观察到的四种观感，用这套坐标一句话安放（§3 详述）：**

1. 「3D 建模做到和真人一模一样」= **超写实数字人 / Hyperreal Digital Human（digital double）**：A 写实 + B 照片级 PBR/SSS + C 无线 + D「CG 表面」（没有传感器噪点、镜头缺陷）。它和「AI 照片」的区别只在 D 轴。
2. 「不那么像真人、带 CG 感的 3D」= **风格化 3D / Stylized 3D CG**（Pixar/Disney 电影风、游戏风格化、盲盒潮玩、黏土、C4D 软 3D 等）：A 轻–强风格化 + B 简化了的 PBR + D CG 表面。这一族内部主要靠 A 轴（头身比）和 D 轴（材质：皮肤 / 搪胶 / 黏土 / 毛毡 / 磨砂塑料）再分。
3. 「3D 转 2D 感觉的」= **三维转二维混合 / 3D-to-2D Hybrid**（Arcane、Spider-Verse、Puss in Boots: The Last Wish、TMNT: Mutant Mayhem、Wish 一脉）：几何与透视是 3D 的（处处自洽），但 B 轴换成手绘光影或区域简化、C 轴加了线、D 轴加了笔触/网点/纸纹等 2D 工艺痕迹。
4. 「2D 画风但不失 3D 立体感」= **有体积感的 2D / 2D with Volume**（厚涂 painterly、西式 semi-realism、概念设计 concept art、painted comic realism）：B 轴是柔和混色/厚涂、C 轴无线或弱线、D 轴有笔触——但**没有 3D 的几何一致性**（有刻意的丢失边、不合理补光、笔触方向与形体不完全吻合）。

**最快的看图判断法（§6 详述）**：先看阴影是否被切成色块（是→cel/三渲二，多为二次元边界）；再看皮肤和眼睛（有传感器噪点和随机瑕疵→照片；过于均匀的 SSS 蜡感 + 完美对称反光→超写实 3D）；再看比例与材质（大头 Q 版 + 搪胶→盲盒；指纹→黏土）；再看 2D 工艺痕迹（网点/排线→Spider-Verse 路线；可见笔触贴图但无硬阴影→Arcane 路线；纸纹/水彩边→绘本路线）；最后用「几何是否处处自洽」区分 3D 渲 2D 与纯 2D 绘画。

---

## 1. 为什么要用多轴坐标系，而不是一张平铺的名词清单

### 1.1 平铺清单的四个病灶（来源与现象）

**（1）同一个词在不同社区指向不同的东西。** 最典型的是「2.5D」：西方游戏语境指「3D 图形 + 2D 玩法/固定视角」（Wikipedia: 2.5D；Giant Bomb；Unity Manual）；西方 Stable Diffusion/Civitai 社区指「介于平面二次元与写实之间的半写实二次元」（Novita AI 博客；Hugging Face 上 `anime, realistic, semirealistic, 2.5D` 并列的模型标签）；中文 ACGN 的「2.5 次元」指 cosplay、手办、舞台剧等现实中的二次元载体（萌娘百科「二次元」词条）；中文设计圈的「2.5D 插画」指 C4D/Blender 做的轴测 UI 插画（Dribbble 上 `c4d / 2.5d / ui` 标签共现）；中文模型社区（吐司 TusiArt）又把「2.5D」设为与「真实」「动漫」并列的一级频道，解释为「质感接近建模软件或 3D 游戏渲染图」（CSDN 2024 模型盘点）。一个词，至少五个位置。

**（2）同一个词在同一社区内部也有两条含义。** 英文「semi-realistic」既用于 Pony/Illustrious 生态的「半写实二次元」（anime→real 轴），又用于 Artgerm、Sakimichan、Loish 一脉的西式光泽半写实人像（digital painting→photo 轴）；2026 年的 Krea2 风格手册把前者（"Pony 2.5D Realism"）放在 anime 组、把后者（"Glossy Semi-Realistic"）放在 digital painting 组——同一个词，两个家族（Krea2 prompt book, 2026）。写实派甚至把 `semi-realistic` 列为负向词：Fooocus 的 `Fooocus Photograph` 与 `Fooocus Enhance` 风格把 "semi-realistic, cgi, 3d, render, cartoon, anime" 一起排除（Fooocus `sdxl_styles_fooocus.json`）。

**（3）技法词与画风词被混在一层。** 中文板绘圈的「平涂 / 赛璐璐 / 厚涂 / 伪厚涂」是上色技法，萌娘百科的编辑讨论明确主张「平涂是技法而非画风，不应放进画风分类」，并指出主流插画多为「赛璐璐为主 + 厚涂/水彩局部」的混合（萌娘百科 Template_talk:绘画；「赛璐璐」「厚涂」词条）。把技法当画风，会让「西方漫画」这一个画风在清单里出现三次（平涂版、渐变版、厚涂版）。

**（4）商业产品的风格面板本身就是「压扁的多轴」。** Adobe Firefly 把效果分成 Popular / Movements / Themes / Techniques / Effects / Materials / Concepts 七组（200+ 项、无逐项定义，Adobe 社区 2025-08 的求助帖得到「尚未创建逐项详细指南」的回复），其中 Movements 是艺术史、Techniques/Materials 是介质、Effects 是后期、Themes 是媒介大类（3D / Anime / Cinematic）、Concepts 是氛围——本应正交的维度被压成一个多选菜单。但 Firefly 把 Color、Lighting、Camera angle 单列为独立的 "extended style components"，反过来支持了「光照与色彩应作为独立轴」。

### 1.2 多轴坐标系的理论与工业先例

- **Scott McCloud 的 Big Triangle**（*Understanding Comics*, 1993）把图像表征放进一个二维关系空间：底边是「写实 ↔ 图标化/卡通化」光谱，顶点是 picture plane（纯抽象）。它编码了两条可分离的轴：形体的符号化程度（对应本报告 A 轴）与画面暴露材料/笔触/平面性的程度（对应 D 轴）。注意它只给**相对位置**，不给阈值；二手资料对第三顶点的命名不一致（language / meaning / picture plane），报告建议采用 reality — language — picture plane 的原文标注，并区分 iconic（符号化、仍有指涉）与 abstract（不再指涉）。
- **Uncanny Valley**（Mori 1970；MacDorman & Kageki 英译刊于 *IEEE Robotics & Automation Magazine* 2012）及其后续研究最有价值的提醒是：**写实度不是单轴**——面部几何写实度、材质/皮肤渲染写实度、动作写实度可以分离，不匹配（写实皮肤 + 卡通眼睛）才是「怪异」的主要来源。【背景知识·未核实】Zell 等 2015 年 SIGGRAPH 论文 "To Stylize or not to Stylize?" 把面部写实度拆为 shape realism × material realism 两轴并做了知觉实验，是与本报告「A 轴 × B 轴」最直接对应的学术工作，强烈建议核实后引用。
- **NPR 学术分类**（Kyprianidis, Collomosse, Wang & Isenberg, "State of the 'Art': A Taxonomy of Artistic Stylization Techniques for Images and Video", *IEEE TVCG* 2013；Lansdown & Schofield 1995）按生成算法分类（stroke-based / region-based / filtering / example-based），说明「技术分类 ≠ 风格分类」，但其隐含的输出维度——笔触尺度、区域平坦化、边缘/线提取、色彩量化——正是 B、C、D、E 轴的工业原型。
- **「3D 看起来像 2D」的工业实践**（2014–2023）证明 hybrid look 是一组可拆分的技术开关：手绘贴图取代 PBR 材质（Arcane，Fortiche）、显式线稿层（Spider-Verse 的 Houdini 工具 Kismet 与 SIGGRAPH 2023 "Linework in Spider-Man: Across the Spider-Verse"；TMNT 在 Maya 中建的 3D ribbon 线）、阈值 cel 着色（Guilty Gear Xrd，Arc System Works，Motomura 2015）、区域简化到「插画级细节」（Puss in Boots: The Last Wish，美术总监 Nate Wragg）、印刷/介质伪影（halftone、纸纹）、降帧（on twos、stepped animation——对静态人像不适用）。这些开关一一对应 B、C、D 轴。
- **生成模型侧**：Somepalli 等的 CSD（"Measuring Style Similarity in Diffusion Models", arXiv 2404.01292, 2024-04；ECCV 2024）放弃以艺术史流派为单一类别，转向 LAION-Styles 多标签对比学习得到连续风格嵌入，并给出 Style Similarity <0.5 / >0.8 的启发式阈值；ArtBench-10（2022-06，10 类各 6,000 张）代表旧的扁平流派标签路线；StyleDrop（NeurIPS 2023）把 style 描述为 "color schemes, shading, design patterns, local and global effects" 及 "colors, shading, textures and 3D appearance"。学界已承认扁平标签不足以刻画生成图风格——这是「多轴而非名单」最直接的学术先例。
- **工业产品的分类骨架**：Recraft API 的四个 base style（`realistic_image` / `digital_illustration` / `vector_illustration` / `icon`）有文字定义，本质是一条「表面纹理拟真度 + 色彩量化程度」的单轴（照片连续纹理 → 简化纹理 → 少量纯色/简单渐变 → 极简），与 B 轴高度对应；Civitai 开源仓库 2026-09 的内部枚举 `styleFamily = anime_manga / photorealistic / illustration_cartoon / render_3d / pixel_retro / other` 是目前唯一可考的平台级「画风家族」枚举，但它**没有 semi-realistic 的位置**——平台方似乎认为「半写实」不是稳定可标注的家族；Stability AI 官方 `style_preset` 的 17 项（`3d-model, analog-film, anime, cinematic, comic-book, digital-art, enhance, fantasy-art, isometric, line-art, low-poly, modeling-compound, neon-punk, origami, photographic, pixel-art, tile-texture`）用互斥的负向词彼此划界（photographic 排斥 drawing/painting；digital-art 排斥 photo/realism；3d-model 排斥 painting/low poly），可视为社区对「写实 / 绘画 / 3D / 漫画」四分法的操作性定义。

### 1.3 本报告的做法

把上述先例并置，复现频次最高的维度是：形体/比例写实度、着色/渲染写实度与离散度、线稿、介质/笔触、色彩与光照、文化谱系——即 §0 的 A–F 六轴【推断】。在此之上，**「家族」= 坐标空间里的聚落**，**「画风」= 聚落里一个有名字的点**。好处是：

- 每个画风可以被写成一条「坐标向量」，直接翻译成提示词（A 轴 → 比例词，B 轴 → 着色/渲染词，C 轴 → 线稿词，D 轴 → 介质词，E 轴 → 配色/光照词，F 轴 → 作品/流派/地域词）；
- 用户的四种观感可以被精确安放，而不是硬塞进某个名词；
- 二次元边界可以用三条轴的联合条件判定，而不是靠感觉。

需要坦白的限制：这套六轴是本调研的归纳，没有任何单一文献同时覆盖这六条轴；F 轴（文化谱系）与 A–E 并不正交，保留它只因为用户检索时离不开它。

---

## 2. 分类框架：六条轴 + 一个边界旗标

每条轴给出刻度、判断依据、来源、以及「写进提示词时对应哪类词」。刻度是为离散分类人为设定的工作点（McCloud 三角本身不给阈值），实际作品常落在两档之间，允许「主导刻度 + 次要刻度」双标签（例如 soft shading 在实践中常是「面部柔和、衣物硬边」的混合——UDIT cel shading 教程、Artfol 画师帖）。

### A 轴：形体/比例写实度（Proportion / Shape Realism）

| 刻度 | 识别依据 | 典型落点 |
|---|---|---|
| A1 写实 | 真人解剖与头身比（约 7–8 头身），面部特征不放大 | 照片、超写实数字人、Alex Ross 式 painted realism、韩系网漫的**身体** |
| A2 轻度理想化 | 比例仍真实，但脸更「美型」、瑕疵更少、下巴更尖 | 影楼写真、韩系半写实、Artgerm 式半写实 |
| A3 明显风格化 | 眼睛放大、鼻唇简化、头略大，但仍是「人」 | Pixar/Disney 3D、游戏风格化 3D、西方半写实、Loish |
| A4 卡通 / Q 版 | 1–3 头身、超大头、极简五官 | 盲盒/潮玩、Funko Pop、Chibi、Corporate Memphis 的弯曲长肢 |
| A5 图标化 | 只剩符号（点眼、圆头） | 贴纸、极简线稿、icon |

来源：McCloud 的 reality↔language 底边；uncanny valley 文献对 shape 与 material 的分离（Unity Glossary；UAL 2023 研究汇编）；韩漫「身体写实、脸不写实」的描述（Tropedia: Manhwa）。**提示词对应**：`realistic proportions` / `naturalistic proportions` / `idealized face` / `big expressive eyes, slightly exaggerated features` / `chibi, 1 头身, 大头小身` / `minimal facial features`。

### B 轴：着色/渲染方式（Shading / Rendering Model）

| 刻度 | 识别依据 | 中文对应 |
|---|---|---|
| B1 照片级物理渲染 | 连续光影、次表面散射（SSS）皮肤、各向异性头发高光、全局光 | 照片级 / 写实渲染 |
| B2 简化物理渲染 | 仍连续，但材质被简化（皮肤更光滑、毛孔减少、高光更规整） | 风格化 3D、「C4D 感」 |
| B3 厚涂 / painterly | 连续但由笔触塑形，边缘软硬交替，暗部有色相偏移 | 厚涂 |
| B4 柔和渐变 soft | 过渡平滑、无明显笔触、无硬边 | 半厚涂、韩漫上色、Artgerm 式光泽 |
| B5 多阶 cel | 光被切成 2–3 个平坦色阶（亮/暗/高光），边界明确 | 赛璐璐 / 三渲二 |
| B6 平涂 flat | 几乎无阴影或仅一阶投影 | 平涂、矢量、ligne claire |

来源：cel shading 定义（UDIT；Adobe；Wikipedia 2022 存档——术语原指平坦着色本身，黑色轮廓线是后来才被绑定进该词的）；萌娘百科「平涂 = 赛璐璐」「厚涂是独立画风」；Recraft base class 定义；卡通渲染「以阈值把明暗切成两块」（wellstsai 三渲二技术概览）。**提示词对应**：`subsurface scattering skin, physically-based materials, global illumination` / `smooth shading, soft studio render` / `painterly, visible brushstrokes, blended brushwork, impasto` / `soft shading, smooth gradient rendering` / `cel shading, toon shading, two-tone shadows, hard-edged tonal division` / `flat color, no shadows`。

### C 轴：线稿（Linework）

| 刻度 | 识别依据 |
|---|---|
| C0 无线 | 轮廓完全由明暗/色块区分（PBR 渲染、Pixar、厚涂、水彩、油画） |
| C1 局部 / 松散线 | 只在转折处或特定区域有线；线可能是手绘 inking（Spider-Verse）、铅笔松散线（TMNT）、「线被颜色吃掉」的伪厚涂 |
| C2 全轮廓线 | 连续包边：干净等宽矢量线（ligne claire、赛璐璐）、粗细变化的墨线（美漫）、3D ribbon 线（TMNT）、inverted-hull 描边（Guilty Gear Xrd） |

线的**质感**另记：pencil / ink / brush / vector。来源：Spider-Verse「第一部有专门 inking 团队的 CG 电影」（befores & afters 2023-06-28）；TMNT「没有这些线，角色显得赤裸」（Mikros 视效总监 Rouxel，befores & afters 2023-09-07）；ligne claire「线几乎等粗、无排线」（Aesthetics Wiki；Comics Odyssey on Hergé）。**提示词对应**：`lineless` / `no outlines` / `partial visible lineart` / `bold black ink outlines` / `clean line art, uniform line weight` / `sketchy pencil lines` / `brush inking`。

### D 轴：介质与工艺痕迹（Medium / Texture / Mark-making）

| 刻度 | 识别依据 |
|---|---|
| D1 传感器照片 | ISO 噪点随亮度变化、镜头畸变与色差、高光溢出（halation/bloom）、轻微运动模糊、焦外过渡不规则 |
| D2 CG 表面 | 零噪点或均匀噪点、理想圆形散景、处处均匀的清晰度、无镜头缺陷 |
| D3 传统媒材 | 画布织纹与颜料厚度（油画）、水渍与纸纹（水彩）、炭粉涂抹（素描）、宣纸晕染（水墨） |
| D4 印刷/屏幕伪影 | 网点 halftone、Ben-Day dots、套印错位 misregistration、riso 颗粒、像素格、贴纸白边 |
| D5 矢量平面 | 边缘绝对锐利、无纹理、可缩放感 |

来源：真实相机噪点与 AI「几乎无噪点或均匀分布」的对比（Eyesift）；「传感器噪点、轻微运动模糊、雾霭只出现在真实拍摄」（Higgsfield）；Spider-Verse 的 halftone 与 hatching（Prolific Studio 博客，二手）；Wish 全片一致的水彩纸纹（SideFX）；risograph 的「荧光专色 + 套印错位 + 粗颗粒」（Morphic）。**D 轴是区分「AI 照片」与「AI 超写实渲染」的决定性轴**【推断】：渲染无论多真都倾向「全局一致的完美」，照片带「局部的不完美」。

### E 轴：色彩与光照（Color & Lighting）

- 色彩：连续自然色 → 电影调色（teal-and-orange、王家卫式深绿+红）→ 马卡龙/高饱和原色 → 2–3 色专色（riso、noir 的黑白+单点色）。
- 光照：具名摄影布光（Rembrandt lighting 的阴影侧光三角、butterfly、beauty dish、direct flash 直闪）→ 三点布光式「完美」CG 光 → 手绘光（每个角色独立光源，Guilty Gear Xrd）→ 无光（平涂）。

来源：Firefly 把 Color / Lighting / Camera angle 单列为 style components；StyleDrop 的 "color schemes"；Rembrandt 光示例提示词（Picassoia；Promptomania）；Cloudinary「光线是 AI 图像显假的最大原因」。**提示词对应**：`Rembrandt lighting, single softbox 45° camera-left` / `three-point lighting, rim light` / `teal and orange color grading` / `macaron palette, 马卡龙配色` / `fluorescent pink over teal blue, slight misregistration offset`。

### F 轴：文化谱系（Cultural Lineage）

非正交，但用户离不开：摄影门类（影棚/editorial/纪实/快照/胶片）、好莱坞与欧洲 CG 动画（Pixar / Disney / DreamWorks / Illumination / Sony Imageworks / Fortiche / Cartoon Saloon）、游戏美术（Blizzard、Riot、Epic）、美漫（Golden/Silver Age、现代数字漫画）、欧漫（ligne claire、Moebius）、韩漫（manhwa/webtoon）、国风（水墨、工笔、国潮、新中式）、艺术史流派（WikiArt/ArtBench 标签；Firefly Movements）、潮玩设计（Pop Mart、Funko、Labubu）。「美系」「日系」只是大众按地域印象做的简化归类，与画师国籍无关、无官方定义（萌娘百科「厚涂」）。

### 边界旗标：anime / 二次元

判定条件为 **A 轴 ≥ A3 的大眼小鼻比例 + B5 硬阈值 cel + C2 干净等宽轮廓线 三者同时成立**【推断】。依据：Guilty Gear Xrd 的技术定义（自定义 cel shader + 每角色独立光源 + 「kill anything that looks 3D」+ 关键帧有限动画）是「3D 彻底伪装成 anime 2D」的极端参照；赛璐璐在中英语境几乎等同于 anime 着色法。注意 cel shading 也存在于非 anime 作品（西方 toon shading、矢量插画），所以**线稿 + 比例**才是把 anime 与非 anime 分开的关键，而非 shading 本身。四个边界类目（2.5D、半写实、三渲二、韩系）在 §4 单独处理。

---

## 3. 用户的四种观感，精确安放到坐标系

| 观感（用户原话） | 本报告命名 | A | B | C | D | E/F | 一句话判别 |
|---|---|---|---|---|---|---|---|
| 把 3D 动画人物建模做到和真人一模一样 | **超写实数字人** Hyperreal Digital Human / digital double | A1 | B1（SSS、strand 发丝） | C0 | **D2 CG 表面** | 三点布光式完美光；UE5 / MetaHuman / Unity Enemies / VFX 谱系 | 像照片，但「太干净」：零噪点、均匀蜡感、完美对称眼反光 |
| 不那么像真人、带 CG 感的 3D | **风格化 3D** Stylized 3D CG | A3–A4 | B2（简化 PBR） | C0 | D2 | 柔光、马卡龙或高饱和；Pixar / 游戏 / 潮玩谱系 | 比例夸张 + 光滑塑料/搪胶/黏土材质 + 全局光自洽 |
| 3D 转 2D 感觉的 | **三维转二维混合** 3D-to-2D Hybrid（广义「三渲二」） | A1–A3 | B3/B4（手绘光影贴图、区域简化）或 B5（狭义三渲二） | C1–C2 | **D3/D4 叠加在 D2 之上** | Fortiche / Imageworks / DreamWorks / Mikros / Disney *Wish* 谱系 | 几何与透视处处自洽（3D 底子），但表面有笔触、网点、纸纹或线稿 |
| 2D 画风但不失 3D 立体感 | **有体积感的 2D** 2D with Volume | A1–A3 | B3/B4 | C0–C1 | D3（数字笔触） | 戏剧性手绘光；厚涂 / semi-realism / concept art / painted comic 谱系 | 体积靠笔触「画」出来：有丢失边、不合理补光、高光随笔触断续 |

**三点说明：**

1. **观感 1 与「AI 照片」只差一条轴（D）。** 超写实 3D 的技术构成——Unity *Enemies*（2022-03）的 tension 皱纹贴图、虹膜焦散、strand-based 毛发；Epic MetaHuman（2021-02）的 strand 发丝、peach fuzz 面部绒毛——已把「面片头发 / 无绒毛 / 眼睛无焦散」这些 2015–2020 年游戏 CG 的标志消灭；2022 年后的破绽主要留在皮肤高光（PC Gamer 评 MetaHuman Creator 为 "pure uncanny valley"，指出「奇怪的皮肤光泽 strange skin shine」）、瑕疵缺失（r/blender 评论「皮肤太均匀、灯光太完美」）和「完美感」。因此报告把「渲染 vs 照片」定义为**介质签名是否存在**，而不是「是否看起来真实」【推断】。

2. **观感 2 内部必须用 D 轴材质再分，否则会把「写实玩具渲染」误归为「卡通 3D」。** 2025 年两大闭源模型潮流——GPT-4o 图像（2025-03 上线）的 "action figure / Barbie Box" 潮流（用户生成自己装在塑料泡壳包装中的收藏玩具，所有来源均描述为**写实收藏玩具渲染**，无来源称其为 Pixar 风）与 Google Nano Banana（Gemini 2.5 Flash Image，2025-08）2025-09 的「1/7 比例 PVC 手办 + 亚克力底座 + 显示器建模过程 + BANDAI 风包装盒」潮流——输出的是**写实材质（PVC/塑料/亚克力）下的卡通比例物体**。在坐标上它们是 A4 + B1 + D2，而 Pixar 风是 A3 + B2 + D2：前者材质写实、比例卡通，后者两者都「可信而非真实」。

3. **观感 3 与观感 4 最容易混，区分靶心是「几何一致性」。** 3D 底子的标志：体积/透视/光照在所有部位绝对一致，同一角色在不同角度完全同构，贴图在转折处被拉伸，景深是渲染器式圆形光斑；纯 2D 绘画则有透视与解剖的人工偏差、笔触方向与形体不完全吻合、刻意的软边/丢失边（lost edges）【背景知识·未核实】。Arcane 是观感 3 的典型（Maya 3D 角色 + Photoshop 手绘含阴影高光的贴图、不用 toon shader、无硬阴影边——RedShark News；UAL 学生博客），而 WLOP 式厚涂是观感 4 的典型（大面积柔光渐变、线稿几乎不存在——【背景知识·未核实】）。两者在 B 轴都是 B3/B4，差别全在 D 轴底层是 D2 还是 D3。

---

## 4. 边界说明：与二次元接壤的四个类目，以及「2.5D」的中西分裂

二次元/anime/manga 不在本报告范围内，但有四个词横跨边界，不说清楚就会让目录失效。

### 4.1 「2.5D」至少有五个意思

| 语境 | 含义 | 与本报告的关系 | 来源 |
|---|---|---|---|
| 西方游戏 / 图形学 | 3D 图形 + 2D 玩法或固定视角；等轴测 isometric 伪 3D；正交摄像机下的 3D 几何 | 与画风无关 | Wikipedia: 2.5D；Giant Bomb；Unity Manual |
| 西方 SD / Civitai 社区 | 半写实二次元：anime 线稿基底 + 3D/照片式体积光影；还有「2.8D」表示更写实 | **二次元边界**，不属 3D 家族 | Novita AI；HF 模型标签 `anime, realistic, semirealistic, 2.5D`；`real-cartoon-pony-28d`；Krea2 "Pony 2.5D Realism" |
| 中文 ACGN「2.5 次元」 | 现实中的二次元载体：cosplay、手办、布偶装、舞台剧 | 与「手办/盲盒」题材词义交叉，但指实物 | 萌娘百科「二次元」；MATCHA 日本动漫用语 |
| 中文模型社区（吐司等） | 「质感接近建模软件或 3D 游戏渲染图」、位于真实系与二次元之间的模型档位；GuoFeng3、XXMix_9realistic 被归此类 | 与「半写实」混用；一半是二次元边界，一半是「国风 CG 感人像」 | CSDN 2024 模型盘点；吐司 Tusi.Art 一级标签 |
| 中文设计圈「2.5D 插画」 | C4D / Blender 制作的轴测 UI 运营插画 | 与 3D 家族的「C4D 软 3D」重叠 | Dribbble `c4d / 2.5d / ui` 标签共现 |

另有中文技术词「三渲二 / 3D 渲 2D / 3D 转 2D」= 3D 模型 + 卡通渲染（toon shading），萌娘百科定义卡通渲染为「把三维模型与仿二维渲染手法结合的画面表现方式」；B 站 2020 年有观点认为「卡通渲染包含三渲二」、原神更准确是卡通渲染而非严格三渲二（个人观点）。「3D 转 2D」作为「三渲二」的口语同义词为【背景知识·未核实】。

**实务建议**：在英文提示词里**不要用 `2.5D`** 表达「有立体感的 2D」或「3D 转 2D」——英文模型会把它理解为半写实二次元（Flux "Toonic 2.5D" LoRA 即此义）或游戏视角词。改用坐标描述：`painterly 3D render with hand-painted textures`（观感 3）或 `digital painting with soft volumetric shading, no outlines`（观感 4）【推断】。

### 4.2 「半写实 / semi-realistic」有两条轴

- **anime → real 轴上的 semi-realistic**：Pony / Illustrious 生态主导，2026-05 r/StableDiffusion 帖 "Semi-realistic is truly amazing for anime" 即此义；Flux "Semi-Realistic Anime Art Style" LoRA（2024-09，触发词 `semi-realistic`）同义。→ 二次元边界，本报告不收。
- **digital painting → photo 轴上的 semi-realistic**：Artgerm、Sakimichan、Loish 一脉的西式光泽半写实人像（Krea2 "Glossy Semi-Realistic"、"Sharp-Lined Glossy Semi-Realistic Portrait"）；Flux "RBStyle" LoRA（2025-04 更新，把真人照片重绘为 semi-realistic digital painting，明示 "not designed for anime"）。→ **本报告收录**，见家族四。
- 英文 SEO 页面给出的定义「naturalistic proportions and lighting principles + exaggerated features like stylized eyes, flowing silhouettes, or painterly brushwork」，强调 gestalt 而非毛孔级细节（Autodesk Origin Exchange，权威性弱）。
- 中文「半写实」偏向「真人往插画方向走」，「2.5D」偏向「二次元往 3D/真人方向走」，但社区实际混用【推断】。
- 技术上这一中间态最难稳定命中：HF 论坛用户试用大量 Civitai LoRA 后「either get an oil painting result at one extreme, or a photorealistic result at the other extreme」。

### 4.3 「三渲二 / cel-shaded 3D」

狭义三渲二 = 阈值化光照（两段或多段色阶）+ 描边。Guilty Gear Xrd（2014 游戏；Motomura GDC 2015 讲座 "GuiltyGearXrd's Art Style: The X Factor Between 2D and 3D"）与原神为代表，服务于日式动画画风 → **二次元边界**。而 Arcane / Spider-Verse / Puss in Boots 路线保留了平滑光照，只在贴图、线条、后期上加 2D 手工痕迹 → **本报告家族三**。判别：看阴影有没有被切成硬边色块。

### 4.4 「韩系 / 韩漫（manhwa / webtoon）」

共识：比日系更写实——身体比例接近真人、面部仍风格化但眼小于日系、鼻嘴刻画完整（Tropedia: Manhwa「bodies realistically proportioned, faces remain unrealistic」；90 Day Korean「more realistic than manga」）；立体感强于日式、细腻度高于美式，「混血感」面孔（机核 GCORES）；色彩比日系内敛浓厚、肤色饱满偏肉色（B 站专栏）；网漫全彩、竖向滚动。日韩边界「近年越来越模糊」（B 站）。中文来源对「色彩饱和度」说法冲突（网易称高饱和；塔猴称低饱和高级灰）。→ 本报告把**韩系半写实**放入家族四作边界条目：身体 A1、脸 A2–A3、B4 soft、C2 干净线、F 韩漫。

### 4.5 中文技法词「伪厚涂 / 半厚涂 / 日系厚涂」

介于平涂与厚涂之间：比平涂用色更丰富、立体感更明显，但没有厚涂写实的结构表达；通常保留线稿但线稿作用减弱；判别关键为「成品是否有清晰线稿」+「明暗过渡是平滑还是边缘清晰」（轻微课；知乎 p/500536943；蓝铅笔）。萌娘百科描述的对应现象是「厚涂与赛璐璐/水彩杂糅、画面清爽色块整洁」，并认为「以现在的眼光看属于厚涂」。本轮**没有找到「伪厚涂」的正式定义来源**。因其基本等同于二次元/半写实边界，本报告只在家族四末尾列为边界条目。英文无对应词，若必须英译只能描述为 `anime-style with retained lineart and soft rendered shading`【推断】。

---

## 5. 画风目录（按家族组织）

**条目格式**：中文名 / English name｜坐标（A–F）｜视觉识别要点｜代表参考｜提示词（EN / CN）｜擅长的模型或工具（带日期）｜易混淆的邻近画风。提示词中**加粗**者为来源中逐字出现的词，其余为综合归纳；带 † 的模型/LoRA 信息来自社区页面摘要，参数需实测。

### 家族一：摄影写实 Photographic Realism

坐标特征：A1–A2、B1、C0、**D1（传感器签名）**。本家族内部不按「画风」而按「谁拍的 / 用什么拍的 / 为什么拍」三轴细分【推断】：影棚美妆与 editorial 是「专业器材 + 受控布光 + 商业目的」；电影剧照是「电影机 + 戏剧布光 + 叙事」；纪实/街拍是「小型机 + 自然光 + 抓拍」；快照是「手机/傻瓜机 + 直闪或自然光 + 非专业构图」；年代与胶片仿真是在任何一类上叠加「介质签名」。2024–2026 社区共识：写实重心已从堆画质词（`8k, hyperrealistic, ultra detailed`）转向描述真实拍摄条件与瑕疵（具体镜头、光源位置、胶片型号、毛孔、不对称、传感器噪点）；`hyperrealistic` 在 AI 语境里被多篇指南视为「指向抛光 glamour 质感」的反效果词（Stockimg；Dropshot），与艺术史中「超越照片的精细绘画」（1970 年代由 photorealism 发展而来，Isy Brachot 1973 年推广）脱钩。

**1.1 影棚 / 美妆 / 头像　Studio · Beauty · Headshot**
- 识别：受控单光源或多光源、干净背景、85mm 式压缩透视、浅景深、皮肤有毛孔但精修克制。
- 参考：商业人像摄影；中文语境的「职场写真 / AI形象照」（美图证件照 App 名称含此词）。
- EN：**85mm f/1.4–f/1.8**, **shallow depth of field**, **Rembrandt lighting, single softbox positioned 45 degrees camera-left and 30 degrees above eye level, characteristic triangle of light on shadow-side cheek**, butterfly lighting, beauty dish, **natural skin texture**, **minimal retouching**, **Kodak Portra 400**, **fine film grain**；负向 **plastic skin, oversharpening, HDR, CGI, waxy skin, heavy beauty retouching**（Carat 85mm portrait；Picassoia；Oakgen）。
- CN：影棚人像、商业人像、形象照、伦勃朗光、85mm 定焦、浅景深、自然肤质、不过度磨皮。
- 模型（2026）：FLUX.2（2025-11-25 发布；多篇平台评测称其 "portrait photorealism leader"，皮肤纹理最常被点名）、Nano Banana Pro（2025-11-20；14 张参考、5 人一致，适合同一人多套写真）、本地 RealVisXL V5.0（「仅限真人人像」）/ Juggernaut XL（全能，Ragnarok 版 2026-02）。Recraft 的 `realistic_image/studio_portrait` 子风格表明商用工具承认人像是独立子域。
- 易混：超写实数字人（家族二 2.1）——看 D 轴：有没有噪点、镜头缺陷；「AI 味」（见 §6.3）。

**1.2 杂志 / 时尚 Editorial · Fashion**
- 识别：造型与服装主导、戏剧化或极简布光、构图留白给版式、精修到「理想化但不抹去个性」（Krea2 "Editorial Photography" 定义："magazine-grade retouching finish that idealizes without erasing character"）。
- EN：**fashion editorial style, high fashion, trendy, stylish, editorial, magazine style**（twri `ads-fashion editorial`）；**glamorous photo, haute couture**（twri `photo-glamour`；diva `High Fashion`）；Vogue Magazine, GQ Photoshoot（Krea2 风格名）。
- CN：时尚杂志大片、高级感、editorial 风。注意「高级感」「氛围感」在中文语境无正式定义（本轮未检索到）；2026 年知乎文章认为「电影感 / 大片感 / 高级感」已太泛，建议拆成「真实皮肤纹理，自然毛孔细节，不过度磨皮」等具体质感词。
- 模型：GPT Image 2 / gpt-image-2（2026-04-21；总榜领先、提示遵循与文字排版强）、Nano Banana Pro、Seedream 4.x/5.0（商业排版与多图一致性被反复提及）、Krea 1（定位 "artistic photorealism"：stylized photography、editorial）。
- 易混：影棚美妆（更干净、无版式意识）；电影剧照（有叙事与宽画幅）。

**1.3 电影剧照 Cinematic Film Still**
- 识别：宽画幅（cinemascope、2.39:1）、暗角、戏剧性侧光/逆光、电影调色（teal-and-orange 等）、颗粒、叙事性瞬间。
- EN：**cinematic film still, shallow depth of field, vignette, highly detailed, high budget, bokeh, cinemascope, moody, epic, gorgeous, film grain, grainy**（SAI `sai-cinematic` 逐字）；anamorphic lens, color grading, **電影燈光、變形鏡頭、膠片顆粒、色彩調校**（Adobe Firefly 繁中示例）。
- CN：电影感、电影质感、电影剧照、变形镜头、暗角、胶片颗粒。
- 模型：Midjourney V7/V8（`--style raw` + 低 `--stylize`；第三方称 V8 默认更「摄影」、V7 更偏绘画感——非官方）、Qwen-Image（被评「牺牲微细节换氛围」，适合电影感概念）、FLUX.2。
- 易混：Editorial（无叙事）；港风/王家卫式（见 1.8，是电影剧照的地域子类）。

**1.4 纪实 / 街拍 Documentary · Street**
- 识别：自然光、抓拍姿态、35mm 或 50mm 视角、环境信息多、黑白常见。
- EN：**35mm photograph, film, bokeh**（SAI `sai-photographic`）、candid, street photography, available light, Leica-style, **shot on 35mm film**, Ilford HP5（ISO 400 黑白，常推一档至 EI 800 获得更粗颗粒）。
- CN：街头纪实、黑白摄影、高反差、粗颗粒、大师感（即梦写法）。
- 模型：所有闭源模型可达；开源 Flux.1 Dev / FLUX.2 + 快照类 LoRA 更可控。本轮未找到独立的纪实/街拍专门 AI 指南（Gap）。
- 易混：快照写实（更「业余」：直闪、构图随意）。

**1.5 快照 / 手机随手拍写实 Snapshot · Amateur Phone Photo**
- 识别：手机色彩科学、直闪或室内混光、低动态范围、随意构图、轻微过曝、无精修——即把 D1 介质签名推到最强。
- EN：**early 2010s snapshot photo captured with a phone and uploaded to facebook**（Flux LoRA 触发词）、**iphone photo, large depth of field**（twri；注意负向 **shallow depth of field, bokeh**）、**spontaneous picture … taken by talented amateur, natural look**（mre）、direct flash, candid。
- CN：手机直出、生活照、极度真实、自然日常、直出图集（小红书 Flux LoRA 触发词 `xhs`，2024）。
- 模型 / LoRA†：Flux "Amateur Photography" LoRA v6（权重 0.8、20 steps、低 denoise hires fix）；Boreal Flux Dev v2（触发词 `photo`，低强度最佳）；SD 系 `amateurphoto-v6-forcu:0.8`。社区报告：这些 realism LoRA 即便低权重也会改变角色 LoRA 的脸（r/FluxAI 2025-04）。闭源模型需靠提示词写介质签名。
- 易混：纪实街拍（有摄影意识）；年代仿旧（叠加了特定介质签名）。

**1.6 年代仿旧 Vintage · Disposable Camera · Polaroid**
- 识别：直闪导致脸部过曝、背景急剧暗落、黄到橙或偏绿色偏、高光 bloom、中等颗粒、塑料定焦镜头边缘失焦；Polaroid 有可辨识边框（SX-70 底宽上窄、600 边框更窄偏奶油色）。
- EN：90s disposable camera, **direct flash**, flash bloom, slight green tint, light leaks, Polaroid style（模糊写法往往只得到「褪色人像 + 随机边框」，须显式要求柔化与边框细节——Oakgen 2026；GPTPrompts 2026-09-30）；负向 **modern smartphone sharpness, HDR, skin correction**（Carat）。
- CN：复古、一次性相机、拍立得、漏光、褪色。「复古」是模糊词，需具体化为年代或介质【推断】。
- 模型：2025–2026 有 "Gemini Polaroid trend"（用 Gemini / Nano Banana 生成与名人合影的拍立得）；一位作者发现「make this vintage」只得到泛泛 sepia，追加「更多颗粒 / 更强漏光」比重来更有效。
- 易混：胶片型号仿真（更「专业」的介质签名）。

**1.7 胶片型号仿真 Film-stock Emulation**
- 识别：胶片词同时编码颗粒结构、色彩科学、动态范围与典型场景——CineStill 800T = 钨丝灯平衡 + 点光源周围标志性**红色光晕 halation**（因去掉抗光晕层）；Kodak Portra 400 = 暖而略褪色的肤色、发丝高光 halation、阴影颗粒；Ilford HP5 = 黑白高反差。
- EN：**shot on Kodak Portra 400**, **Kodak Vision3**, **CineStill 800T, red halation around neon**, **Ilford HP5 pushed to 800**, **Kodachrome, Lomography**（Fooocus Photograph）、tonal roll-off, muted tones。
- CN：胶片感、胶片人像、柯达 Portra 400 胶片质感、柯达金 200、模拟胶片颗粒、浅景深、侧逆光、柔和大气薄雾（数英 Nano Banana Pro 人像提示词合集；塔猴模板）。
- 模型：所有模型对胶片词有响应，但中文评测指出颗粒、色差、暗角「往往不够强」（xsct.ai 对 GPT Image 2 与 wan2.7-image 的港式霓虹海报测例）；开源 + 胶片 LoRA 更可控（ComfyUI 中文工作流：写实主模型 + 两个胶卷质感 LoRA）。
- 易混：电影剧照（1.3）——胶片词常被叠加其上。

**1.8 中国市场的产品化子类：AI写真 · 证件照 · 港风**
- **AI写真 / 证件照**：2023-07-17 妙鸭相机以 9.9 元「上传 20 张照片 → 30 余种妆造写真」引爆，对标海马体/天真蓝（36氪；界面新闻），18 天后热度回落；此后美图证件照（数百种规格、AI 换装、「职场写真·AI形象照」）与即梦等把证件照/形象照做成固定功能；开源替代 EasyPhoto（LoRA + ControlNet）。这里的「AI写真」不是提示词而是**模板**（古风、都市、证件照、休闲）。坐标上它仍是 1.1 影棚头像，只是入口不同。EN：ID photo, passport photo, `plain white/blue background, frontal, even lighting`；corporate headshot, LinkedIn headshot。
- **港风 / 王家卫式**：场景（茶餐厅、霓虹街道、旧式公寓、天台）+ 80–90 年代服装 + 钨丝灯与霓虹混光 + 胶片颗粒 + 复古调色（Felo 港风 agent）；王家卫式后期 = 深绿与红、颗粒、动感模糊（什么值得买教程）。EN：**1980s–90s Hong Kong street, neon signs, tungsten light, cha chaan teng, film grain**, Wong Kar-wai style, rain-soaked street, green-red cast, motion blur, step-printing。模型：中文评测显示繁体字招牌仍不稳定（xsct.ai）。
- 语用差异：中文词汇多是「成品风格名」（港风、法式、韩系、胶片、证件照、形象照），英文词汇多是「拍摄参数」（85mm、Rembrandt、Portra）【推断】。

**1.9（旁注）超写实绘画 Hyperrealism as painting**
艺术史上的 hyperrealism / photorealism 是「看起来像高分辨率照片的绘画与雕塑」；AI 风格文件里仍有 twri `artstyle-hyperrealism`（"hyperrealistic art, realism pushed to extreme, fine texture, incredibly lifelike"），Krea2 区分 "Hyperrealism"（photographic conviction over visible brushwork）与 "Ultrarealism"（surpasses photographic fidelity, uncanny, hyper-vivid）。坐标上它是 A1 + B1 + **D3（画布/颜料）**——归入家族六的油画条目更合适；作为人像提示词时请避免把 `hyperrealistic` 当成「更像照片」的加强词。

### 家族二：3D 家族 3D CG Family

坐标特征：**D2（CG 表面）** 贯穿全族；内部靠 A 轴（头身比）与 D 轴材质（皮肤 / 搪胶 / 塑料 / 黏土 / 毛毡 / 磨砂）再分。渲染器名（`octane render / unreal engine 5 / cinema 4d / redshift / arnold`）在 2022 年 SD1.5 / Midjourney v4 时代是强风格锚点（200 万条 SD 提示词数据集中 "octane render" 出现 120,940 次），2025–2026 自然语言模型（FLUX.2、gpt-image、Nano Banana、Midjourney V7+）下它们仍可作「这是 CG」的弱锚点，但主路径变为描述材质、光照、镜头与场景道具（3DAI Studio 2025-12 Flux 3D 指南未提渲染器名；Nano Banana 官方手办提示词本身即是样本）【推断，缺乏受控 A/B 测试】。

**2.1 超写实数字人 / 数字替身　Hyperreal Digital Human · Digital Double**
- 坐标：A1 · B1 · C0 · D2。
- 识别（正向线索 = 2022 年后实时管线的技术构成）：strand-based 单根发丝 + 面部绒毛 peach fuzz（MetaHuman groom 组件含 hair / eyebrows / eyelashes / peach fuzz / beard）、tension 皱纹贴图与虹膜焦散（Unity *Enemies*，GDC 2022）、SSS 皮肤。（破绽线索）皮肤蜡感或均匀油亮 "skin shine"、毛孔/瑕疵/汗过于均匀或缺失、眼反光完美对称且不对应场景光源、三点布光式「完美」打光、零噪点、理想圆形散景。注意：PC Gamer 称牙齿「通常是常见破绽」但 MetaHuman 处理得好。
- 参考：Epic MetaHuman（2021-02；基于真人扫描，只能产出「可信的人类」，无风格化角色）、Unity *Enemies*（2022-03）、Love, Death + Robots 中 Blur Studio 的 *Sonnie's Edge*（V-Ray 渲染，"cinematic digital humans … highly stylized photoreal"）；Weta / ILM 数字替身、Final Fantasy 写实 CG（*Kingsglaive*）为经典名称但本轮无来源。
- EN：**photoreal 3D render of a digital human, subsurface scattering skin, strand-based hair, cinematic three-point lighting, shallow depth of field, no film grain**【推断】；`unreal engine 5 render`, `octane render`（弱锚点）；"metahuman" 作为提示词**效果未经证实**。
- CN：超写实数字人、3D 超写实、数字替身、写实 CG、虚幻 5 渲染。中文数字人行业分级：2D 真人 / 2D 卡通 / 3D 卡通 / 3D 半写实 / 3D 写实 / 3D 超写实（InfoQ；腾讯新闻 2024；百度智能云）——但没有任何权威文献给出 cartoon → stylized → semi-realistic → realistic → digital double 的正式定义，分级是实践约定。
- 模型 / LoRA†：Flux "Unreal Engine Render Flux v1" LoRA（ModelsLab，说明 UE 外观已被当作训练目标而非仅靠关键词）；Midjourney V7/V8 写实提示；闭源模型默认倾向照片感，需显式写 `3D render / CG` 才会得到本类而非照片。
- 易混：**AI 照片**（家族一，只差 D 轴）；Pixar 风（比例不同）。

**2.2 皮克斯 / 迪士尼电影式风格化 3D　Pixar / Disney Feature-Film Stylized 3D**
- 坐标：A3 · B2 · C0 · D2 · E 柔和主光 + 环境反射。
- 识别：头身比接近真人或略卡通化（约 1:5–1:7）【背景知识·未核实】，大眼但保留写实虹膜，皮肤有 SSS 与细微毛孔，毛发 strand 级，材质追求「可信而非真实」；Epic 官方 spotlight *Daughter of the Inner Stars* 显示 MetaHuman 写实底模可被推向「手绘感 hand-painted」风格化——说明「3D 写实基底 + 风格化表面」是真实存在的中间类别。中文画风指南的区分：皮克斯 = 圆润可爱 + 先进渲染 + 情感化叙事；梦工厂 = 「融合 2D 和 3D 的美学，大胆的色彩和图形化表现」、夸张化、高对比（知乎 41 种风格；一起学AI 50+ 画风）。
- EN：**Pixar style 3D character, big expressive eyes, soft lighting, colorful background**（GPT-4o 2025-04 Pixar 化潮流用法；若过于写实追加 **more animated and cartoon-like**）；**expressive large eyes, slightly exaggerated features, warm cinematic lighting, subtle facial asymmetry, soft skin subsurface scattering**（社区模板；并称 "Photorealistic face = uncanny valley"）；**(pixar|disney:1.2) style, 3D**（A1111 风格文件）；**3D render, adorable character, 3D art**（diva `Adorable 3D Character`）；Krea2 "Pixar Animation" 定义 "soft, warm subsurface-scattered lighting … appealing, rounded proportion … gentle, cinematic three-point lighting"。
- CN：皮克斯风、迪士尼 3D、3D 卡通、3D 动画风格；中文平台预设名：通义万相「3D卡通」（2023 首发）、混元「3D」（编号 116）/「3D 渲染」、即梦「3D 卡通」。
- 模型 / LoRA†：GPT-4o / GPT Image 的 "Pixar-style" 照片转绘是 2025 年最大众化入口；Flux "live-3D"（Shakker-Labs，推荐权重 0.9–1.3，非商用）、Flux CToon / cflux-cartoon LoRA；SD 时代 Civitai "Disney Pixar Cartoon" 合并检查点（声明与 Disney/Pixar 无关）；Midjourney sref 目录 "3D Design" 类（Midlibrary 5,000+ 代码）。注意：OpenAI 自 DALL·E 3（2023-10）至 GPT-4o 图像（2025-03）「拒绝在世个人艺术家风格、允许工作室风格」，Pixar/Ghibli 一类工作室风格原则上允许但 2025-03 后曾出现对 Ghibli 请求的模糊拒绝。
- 易混：盲盒/手办（比例更极端、材质是搪胶/PVC）；写实玩具渲染（2.4，材质写实）；游戏风格化（2.3，更硬朗、手绘贴图）。

**2.3 游戏风格化 3D　Game Stylized 3D（Overwatch / Fortnite / Valorant / LoL cinematics）**
- 坐标：A2–A3 · B2（PBR + 手绘感贴图）· C0 · D2。
- 识别：介于 Pixar 与写实之间，夸张轮廓与手绘感贴图，常被 AI 社区混称 "stylized 3D / Blizzard cinematic style"。【背景知识·未核实】Overwatch 美术常被描述为 "stylized realism / painterly hand-painted PBR"，GDC 2017 有相关讲座，本轮未执行搜索。
- EN：stylized 3D character, hand-painted PBR textures, **3D cartoon, colorful, Fortnite Art Style**（diva）、Overwatch concept art（Krea2 风格名）。
- CN：游戏 3D 风格、3D 游戏人物风格（即梦示例）、风格化写实。
- 模型：无专项来源；靠闭源模型自然语言引用作品名 + Flux 3D LoRA。
- 易混：Pixar 风（更圆润、更软）；超写实数字人（无手绘贴图）。

**2.4 盲盒 / 潮玩 / 搪胶玩具　Blind Box · Designer Toy · Vinyl Figure**
- 坐标：**A4（1–3 头身）** · B2 · C0 · D2（搪胶哑光或微光泽）· E 马卡龙 / 纯色、商品摄影式棚光。
- 识别：超大头、极简五官（小嘴或无嘴、点状眼或大圆眼）、vinyl 哑光或微光泽表面、干净背景、常带底座或包装盒；Labubu 特征为尖耳、毛绒质感、大眼、小身体、尖牙、坏笑（Vmake；Labubu 是 Pop Mart 与 Kasing Lung "The Monsters" 的授权商标角色，商用提示直接点名有法律风险）。
- EN：**blind box, designer toy aesthetic, vinyl toy style, cute collectible figure**, chibi figure, PVC figure, **3d toy design**（ToyBox 触发词 `t0yb0x`）；"糖果色、雕塑感 3D，停格黏土动画 + 设计师玩具美学，橡胶质感、搪胶光泽"（Midjourney sref 整理，无具体代码）。`blind box style` 在英文模型中识别度不确定；中文用户事实上用 `POP MART style, 3D cartoon character, C4D, Octane render, clay material, glossy` 等物件/材质词绕开【推断】。
- CN：**盲盒风格、泡泡玛特风格、潮玩、Q 版手办、1 头身 / 大头小身、干净背景、马卡龙配色、C4D 渲染、OC 渲染、ip 设计、柔和棚拍光、哑光材质**（小红书「潮玩盲盒」教程把提示词拆为「风格词、材质词、渲染词、画质词、类型词」；WildChat 记录中的 Midjourney 盲盒模板）。
- 模型 / LoRA†：吐司 TusiArt「泡泡玛特-盲盒风 LORA」（触发词 `PPMT`，Flux 与 Illustrious 双底模）、「Chibi-Figure」（Flux，3D Q 版手办）；Civarchive/Shakker「3D 潮玩盲盒 IP 手办 LoRA（Z1.0）」；renderartist "ToyBox Flux"（强度 0.7–0.9，Euler/DEIS，动物不稳定）；Scenario "3D Blocky Elements"；SD1.5 时代 LiblibAI「3D超萌IP形象设计|盲盒|revAnimated」检查点。中文平台（TusiArt / LiblibAI / Shakker）是该子风格 LoRA 的主要产地——盲盒风在中文社区是独立、高需求的子风格。
- 易混：Funko Pop（方块化头 + 黑纽扣眼，固定公式，【背景知识·未核实】）；Chibi/Q 版二次元（线稿 + cel 则归 anime）；写实手办渲染（2.5）。

**2.5 写实玩具 / 手办渲染　Realistic Collectible Figure · Action Figure Render**
- 坐标：A4（或保留真人比例）· **B1（写实材质）** · C0 · D2（PVC / 塑料泡壳 / 亚克力）· F 商品摄影。
- 识别：卡通或缩比的「物体」被放进**写实场景**——桌面、显示器、包装盒、底座、泡壳；材质是真实塑料。这是 2025 年把该审美带入「人像」范畴的关键一步（真人照片 → 手办）。
- 参考与时间线：GPT-4o "action figure / Barbie Box Challenge"（2025 春，"realistic action figure in collectible toy-style plastic packaging"，依赖 4o 擅长渲染包装文字；TikTok #actionfigure 29.7 万+ 帖）；Nano Banana 3D 手办潮流（2025-09，Google India 示范、Sundar Pichai 2025-09-25 参与；Google 因热度调整每日限额）；衍生「手办图 → Tripo / Meshy / Hunyuan3D 转可旋转 3D 模型」链路（Sloyd）。
- EN（逐字模板）：**"Use the nano-banana model to create a 1/7 scale commercialized figure of the character in the illustration, in a realistic style and environment. Place the figure on a computer desk, using a circular transparent acrylic base without any text."**；**"turn this photo into a character figure. Behind it, place a box with the character's image printed on it, and a computer showing the Blender modeling process on its screen. In front of the box, add a round plastic base with the character figure standing on it."**；长版加 PVC material, BANDAI-style packaging box behind, indoor background, full body even from half-body input。
- CN：手办化、一键做手办、1/7 比例手办、亚克力底座、包装盒、真人手办（直接上传全身照；还原动漫角色则同时上传真人照与角色图并要求「让图1角色完全像图2」）；2026 年 Banana2「女性像拿钥匙扣一样手中拿着一个自己的小型 3D 卡通版本」玩法（站酷）。
- 模型：Nano Banana / Nano Banana Pro / Nano Banana 2（2026-02-26）、GPT-4o → GPT Image 1.5（2025-12-16）→ gpt-image-2（2026-04-21）。
- 易混：盲盒/潮玩（2.4，材质「可信」而非写实、无场景道具）；Pixar 风（无实物感）。**报告建议把本类定义为「写实渲染的玩具题材」而非「卡通 3D 画风」，否则分类会在材质维度失配。**

**2.6 黏土 / 定格动画　Claymation · Stop-motion Clay**
- 坐标：A3–A4 · B2 · C0 · **D2+ 可见指纹与捏塑痕、哑光微粒** · E 停格动画式布光。
- 识别：手工不完美、略不规则轮廓、哑光；Krea2 "Claymation" 定义 "soft, rounded forms carrying visible handcrafted imperfection, gentle fingerprint-like dents … Influenced by: Aardman"。
- EN：**play-doh style, sculpture, clay art, centered composition, Claymation**（SAI `sai-craft clay`；Stability 预设名 `modeling-compound`）、Aardman style, Laika style, stop-motion。
- CN：黏土风、黏土定格动画（墨图 AI 头像模板「照片变卡通·黏土定格动画」）、定格动画（即梦 4.0 速查表风格词）、Firefly Materials「Claymation」。
- 模型 / LoRA†：Flux "Claymation XC" LoRA；Midjourney「黏土/设计师玩具」sref。
- 易混：盲盒（表面光滑无指纹）；毛毡（纤维边）。

**2.7 毛毡 / 羊毛毡　Felt · Needle-felted Wool**
- 坐标：A4 · B2 · C0 · D2+ 绒毛边缘与纤维纹理、几乎无高光。
- EN：**wool texture, needle felt, wool needle felting**（灵图 AI；以物件/场景为主）、felted wool character, fuzzy fiber edges。
- CN：羊毛毡 3D、毛毡风（2026 年「10 种 AI 转绘风格」把画面变成「柔软、带绒毛质感的手工微缩场景，边缘圆润、色调温暖、背景浅景深」）；即梦材质词「毛绒」。
- 模型：通用模型可达；无专项 LoRA 来源。
- 易混：黏土（哑光但无纤维）；毛绒玩具写实渲染。

**2.8 C4D 风 / Blender 软 3D 插画　C4D-style Soft 3D Illustration**
- 坐标：A3–A4 · B2 · C0 · D2（哑光塑料 / 磨砂玻璃）· E 柔和双色渐变、浅景深；常为轴测构图。
- 识别：圆角几何、简洁场景、UI/运营/电商用途；Dribbble 上 `c4d / ui / 插图 / 2.5d / 图标` 标签大量共现，说明该风格主要用于配图、图标、Banner。
- EN：**3D render, C4D style, soft matte materials, cute cartoon character, commercial illustration quality**（即梦提示词整理的英译）、frosted glass, isometric 3D graphic（Krea2）。
- CN：**3D 渲染，C4D 风格，柔光材质，可爱卡通角色，商业插画质感**（知乎即梦提示词大全 2026）、OC 渲染、2.5D 插画。中文里 C4D / Blender / OC 渲染是**质感指示词**（软件名 → 柔光、PBR、高光泽黏土、极简背景），不是独立画风，几乎总与「盲盒 / IP 形象 / Q 版 / 3D 卡通」连用。
- 模型：即梦、通义万相「3D卡通」、Midjourney、Flux 3D LoRA。
- 易混：盲盒（有角色 IP 属性）；低多边形（2.9）。

**2.9 低多边形 / 像素 3D　Low Poly · Voxel · PS1 Graphics**
- 坐标：A4–A5 · B2/B5 · C0 · D2（可见多边形面 / 体素格）。
- EN：**low-poly style, low-poly game art, polygon mesh, jagged, blocky, wireframe edges**（SAI `sai-lowpoly`）、voxel, PS1 Graphics（Krea2）。
- CN：低多边形、低面数、体素。
- 易混：像素画（家族五，2D）；C4D 软 3D（光滑圆角）。

**2.10 真 3D 资产生成（旁注）**
Tripo（速度与拓扑，Smart Mesh P1.0）、Meshy（综合平台，自称 Meshy 6 获 63.8% 专业评审偏好——自报数据）、腾讯 Hunyuan3D（开源、PBR 贴图，权重有地域限制；Krea 运行 Hunyuan3D 3.1 Pro 与 2.1）；Krea 建议 2026 年最佳流程为「先生成干净参考图（单主体 + 纯背景）再 image-to-3D」。所有对比来自厂商页或竞品站，未见独立基准。

### 家族三：三维转二维混合 3D-to-2D Hybrids（广义「三渲二」）

坐标特征：底层 D2（3D 几何、处处自洽的透视与体积），表层叠加 D3/D4 工艺痕迹，B 轴离开物理光照，C 轴出现线稿。「3D 看起来像 2D」在业界（2015–2023）由一组可拆分的技术开关组成：(1) 手绘/绘画式贴图取代 PBR 材质，(2) 自定义 cel/threshold 着色或手绘光影取代物理光照，(3) 显式线稿层，(4) 降帧与变帧率（静态图不适用），(5) 2D 手绘 FX 与印刷/介质伪影，(6) 不用运动模糊。至少三条路线：

**3.1 手绘贴图路线　Hand-painted Texture Route（Arcane）**
- 坐标：A1–A2 · **B3（光影手绘在贴图上）** · C0–C1 · D2+D3。
- 识别：**无硬阴影分界**（区别于 cel）、皮肤上有画出来的高光/阴影笔触、写实比例与解剖、油画感背景、2D 手绘特效（烟、爆炸为平面图形）。
- 技术来源：Fortiche 以 3D 模型为基底，美术在其上进行 2D 绘制；**阴影与高光由美术手工绘制在 3D 模型上，而非由软件计算光照**（Dark Skies Film；RedShark News）；不依赖 toon shader，没有硬阴影边（UAL 学生博客）；叠加的 2D 元素以 12 fps 动画化；社区复刻经验：roughness / normal / bump 也手绘，Substance 3D Painter 方形 alpha 低不透明度画笔（80.lv；Blender Artists）。注意：搜索结果中多条为低质量/疑似 AI 生成博客，工具与流程细节应以 Fortiche 官方访谈为准（本轮未取得一手来源）。
- 参考：*Arcane*（Fortiche，2021 / 2024）。
- EN：**Arcane style, Fortiche style, hand-painted textures, painterly 3D**【推断，社区用法未直接取证】、painted shadows and highlights, no hard shadow edges, oil-painted background。
- CN：Arcane 风、双城之战风、手绘贴图 3D、绘画感 3D。
- 模型：主要靠闭源模型自然语言引用作品名（推断）；无专项 LoRA 来源。
- 易混：**厚涂 2D**（家族四 4.2）——看几何一致性：Arcane 的体积、透视、光照在所有部位绝对一致，贴图在转折处被拉伸；厚涂有丢失边与「为了好看」的不合理补光。

**3.2 漫画印刷路线　Comic-print Route（Spider-Verse）**
- 坐标：A1–A3 · B2/B5 混合 · **C1（3D 空间中绘制的线、可选是否响应光照）** · **D4（网点、排线、无运动模糊）**。
- 识别：半色调网点 halftone、交叉排线 hatching 做阴影、粗细变化的墨线、无运动模糊、漫画拟声词与分镜感；【背景知识·未核实】套印偏移 misregistration / Ben-Day dots / Kirby krackle / 色差（一手来源仅明确 halftone、hatching、二拍、3D 线条、去运动模糊）。
- 技术来源：导演称全片按「二拍」on twos 动画，线条在 3D 空间中绘制于角色之上，全片去除运动模糊（Dark Horizons）；SIGGRAPH 2023 Talk "Linework in Spider-Man: Across the Spider-Verse"（Grochola 等，DOI 10.1145/3587421.3595413）允许美术重画线条且线条仍跟随底层动画；Houdini 工具 Kismet；"Repainting the Spider-Verse" 模拟笔触运动与颜料流动的 painting FX。
- 参考：*Spider-Man: Into the Spider-Verse*（2018）、*Across the Spider-Verse*（2023），Sony Pictures Imageworks。
- EN：**Spider-Verse style, comic halftone, Ben-Day dots, offset ink lines, chromatic aberration**【推断】、cross-hatching shadows, no motion blur, 3D-drawn linework。
- CN：蜘蛛侠平行宇宙风、漫画印刷感 3D、网点 3D。
- 易混：**真正的美式漫画 / 平面插画**（家族五 5.1）——看体积与透视是否 3D 自洽、人物转面是否同构。

**3.3 绘本 / 速写路线　Storybook · Sketchbook Route（Puss in Boots 2 / TMNT / Wish / Nimona / The Bad Guys）**
- 坐标：A2–A3 · B3（区域简化到「插画级细节」）· C1–C2（画笔质感边缘线、速写抖动线、3D ribbon 线）· D2+D3（纸纹、水彩边、铅笔颗粒）。
- 识别：表面细节被简化、边缘线有画笔或铅笔质感、纸纹或水彩纹理、stepped 动画造成的「定格感」（静态图不适用）、刻意的透视/比例不完美。
- 技术来源：*Puss in Boots: The Last Wish*（DreamWorks 2022）导演 Joel Crawford 称 "fairy tale painting" look，美术总监 Nate Wragg 把表面简化到「插画级细节」而非写实，体积模拟 pass 转网格获得硬的手绘边（TheWrap；AWN；VFX Voice）；*TMNT: Mutant Mayhem*（Mikros / Cinesite 2023）像「青少年在速写本里画的电影」，匹配参考画的铅笔质感与松散感，**刻意在透视、比例、轮廓中加入不完美**，轮廓线为 Maya 3D ribbon 经 Katana 渲染，用 3D speed lines 取代运动模糊（befores & afters 2023-09-07；Mikros；Cinesite）；*Wish*（Disney 2023）开发了让每一帧都有一致水彩纸纹理的系统，环境与角色周围有线条（SideFX）；*Nimona*（DNEG 2023）把 2D 关键姿势动画原则带入 3D（Creative Bloq）。*The Bad Guys*（2022）与 *Wolfwalkers*（2020）未能检索，仅【背景知识·未核实】：前者 2D 插画感 + 手绘线稿叠加 + 简化光照；后者为纯 2D 手绘。
- EN：**painterly 3D, storybook illustration 3D, sketchy 3D render, watercolor CG**【推断】、fairy-tale painting look, sketchbook pencil texture, imperfect perspective, watercolor paper texture。
- CN：绘本感 3D、童话绘画风、速写本质感 3D、水彩纸纹 CG。
- 易混：水彩/绘本 2D（家族六）；Pixar 风（无纸纹与线）。

**3.4（边界）狭义三渲二 / cel-shaded 3D　Toon-shaded 3D**
- 坐标：A3+ · **B5 阈值 cel** · C2 · D2。
- 识别：阴影被切成界线分明的两块色块（写实渲染按法线与光线夹角平滑过渡，卡通渲染设阈值——wellstsai），干净等宽描边，每个角色独立光源（Guilty Gear Xrd）。
- 参考：*Guilty Gear Xrd*（Arc System Works 2014；Motomura 讲座 2015——「摒弃数学准确性」以获得完全一致的 cel shading；营销称 "Limited 3D Animation"）、原神（归属有争议）。
- EN：**cel shading, toon shading, 2D, flat color, cel shaded style**（diva）、**hard-edged tonal division … confident bold outline … within a fully dimensional render**（Krea2 "Cel Shading"）。
- CN：三渲二、卡通渲染、赛璐璐渲染。
- 定位：服务于日式动画画风时 → **二次元边界，本报告不展开**；西方 toon shading（如 *The Legend of Zelda: The Wind Waker* 式、【背景知识·未核实】）若比例与线稿不符合 anime 旗标，则仍属本家族。

**判别三条路线的速记**：网点/排线/墨线 → 3.2；可见笔触贴图 + 无硬阴影 → 3.1；纸纹/水彩边/速写线 → 3.3；硬阈值色块 + 等宽描边 → 3.4（多为二次元边界）。

### 家族四：有体积感的 2D　2D with Volume

坐标特征：B3/B4（厚涂或柔和混色）、C0–C1、**D3（数字笔触，无 3D 几何一致性）**。这是用户观感 4 的家。中文术语的锚点来自板绘教学而非 AI 社区：「厚涂」源自油画技法，数字绘画中常把「写实立体的绘画风格」叫厚涂，颜色层层堆叠，通常不画线稿（蓝铅笔；知乎）；萌娘百科把厚涂视为「对画面影响很大的上色手法，可归为一种广泛使用的画风」，并把「有厚涂笔触但色块干净」者也归入厚涂。**最易误译的词**：「厚涂」的词典英译是 `impasto`（AAT-Taiwan 首选词），但那只覆盖「颜料堆叠」的技法义；直译会把 AI 推向梵高式笔触堆叠，而中文用户想要的「厚涂人像」更接近 `painterly realistic portrait, soft blended shading, no lineart`【推断】。

**4.1 西式光泽半写实　Western Glossy Semi-Realism（Artgerm / Sakimichan / Ross Tran 一脉）**
- 坐标：A2–A3 · B4 · C0 · D3（高完成度、无可见笔触或少量装饰性笔触）。
- 识别：皮肤与头发高光极亮、偏写实比例但眼睛放大、整体「光滑渲染」。Krea2（2026）把 "Glossy Semi-Realistic"、"Sharp-Lined Glossy Semi-Realistic Portrait"、"Artgerm Style"、"Charlie Bowater Style"、"RossDraws Style"、"Loish Ultrarealism" 放在 digital painting 组。
- 画家特征【以下均为背景知识·未核实，页面抓取被拦截】：Artgerm（Stanley Lau）= 光滑渲染、无可见笔触、DC/Marvel 变体封面；Ross Tran（Rossdraws）= 高饱和多色光（粉/青/橙撞色）、可见笔触带「颜料飞溅」；Sakimichan = 半写实二次元/游戏同人，处在日系边界；Loish = 流动发丝、风格化长颈大眼、有限色阶带柔和体积，更接近风格化插画；Charlie Bowater = 幻想小说封面、柔和厚涂、低饱和暖灰调。
- EN：**semi-realistic**, painterly digital illustration, soft blended shading, glossy highlights, no hard outlines, glowing rim light, naturalistic proportions；Krea2 风格名 "Glossy Semi-Realistic"。**艺术家名的使用**：2022 年 Greg Rutkowski 被 Lexica 统计为 SD 上被 prompt 最多的艺术家（约 93,000 次，MIT Technology Review 2022-09-16），Midjourney 2022-02 的 "Style List" 含 16,000+ 艺术家名（2024-01 作为 Andersen v. Stability AI 诉讼附件公开）；随后 SD 2.0（2022-11）削弱艺术家风格复现、ArtStation "No to AI" 抗议（2022-12）、Stability 为 SD3 接受 Spawning opt-out（约 8,000 万张，占 LAION 约 3%）、OpenAI 自 DALL·E 3（2023-10）起拒绝在世艺术家风格并在 GPT-4o 图像 system card（2025-03）沿用。**实务：以描述性词汇为主，艺术家名标注为「历史用法」**；Midjourney 未搜到禁用艺术家名的官方规则，但平台转向 `--sref` 风格码作为去名化替代。
- CN：欧美半写实、半写实、厚涂人像、光泽感。
- 模型 / LoRA†：Flux "RBStyle"（Civitai #1461162，2025-04 更新，照片 → semi-realistic digital painting，保持五官比例）；Z-Image Turbo 时代 "Visionarys Semi-Realism (ZIT)"（Civitai #2311515，2025 末–2026）；Midjourney `--sref`；注意易滑向油画/照片两端（HF 论坛）。
- 易混：**韩系半写实**（4.5，面部模板更统一、线稿常保留）；超写实 3D（看 D 轴：3D 的高光模型处处一致、2D 高光随笔触断续）；伪厚涂（有线稿 + anime 比例 → 边界）。

**4.2 厚涂 / 绘画感数字绘画　Painterly Digital Painting（厚涂）**
- 坐标：A1–A3 · **B3** · C0 · D3（可见笔触、边缘软硬交替、暗部有色相偏移）。
- 识别：笔触塑形、线稿弱化或被颜色吞掉、高光与笔触融合有「刮出」感、连续渐变并带色相偏移（冷暗部暖亮部）【背景知识·未核实的快速检查】；WLOP 式（大面积柔光渐变、低对比暗部、发光边缘光、线稿几乎不存在）与 Rutkowski 式（史诗奇幻、宽笔触、强体积光、暖金冷蓝对比）为两个常见锚点【背景知识·未核实】。
- EN：**digital painting, thick paint, visible brushstrokes, impasto**（仅在要「颜料堆叠」时用）, blended brushwork, lost edges, painterly, **textured brushstrokes, visible brushwork, palette knife marks**（AIGC.cn 厚涂关键词文：单独 `thick paint` 不足以指代该技法）；Krea2 "Digital Painting" = "confident brushwork translated through digital tools while retaining the tactile logic of traditional painting"。
- CN：厚涂、厚涂幻想风（中文 AI 风格清单把它与「日系赛璐璐风」并列为独立 prompt 类目）、笔触感、无线稿。
- 模型 / LoRA†："Zavy's Rough Paint (Flux)"（impasto 厚笔触方向）、"Painted World"（SDXL/Pony）；Midjourney 被 2026 综述普遍列为「风格/艺术方向」首选（Magnific；Atlas Cloud），Flux 2 在 "stylized and illustrative" 上不领先（Switas）。
- 易混：**油画**（家族六 6.1）——厚涂通常没有真实画布纹理、颜料厚度与裂纹，色彩更鲜亮、边缘更数码化、常混赛璐璐式干净块面；加 `canvas texture, impasto, varnish sheen` 会把厚涂推向油画【推断】。**Arcane 式 3D**（3.1）——看几何一致性。

**4.3 概念设计人像　Character Concept Art · Character Sheet**
- 坐标：A1–A3 · B3 · C0–C1 · D3；构图特征：3/4 半身 + 道具标注、中性背景或色卡、多视角。
- 识别：设计可读性优先（剪影、材质分区、功能性道具），焦点细节 + 松散边缘（Craig Mullins 传统：大块面值阶优先、细节集中于焦点【背景知识·未核实】）。"trending on artstation" 是 SD1.x 时代的质量咒语（200 万条提示词中出现 153,785 次），并非真实趋势信号；2026 年 Krea2 把其语义改写为 "ArtStation Masterpiece"（high-production concept-art illustration style, portfolio-ready）。
- EN：**concept art, digital artwork, illustrative, painterly, matte painting**（SAI `sai-digital art`）、**ethereal fantasy concept art … painterly, epic, cover art**（SAI `sai-fantasy art`）、**character design sheet with multiple views (Front, Side, and Back views), consistent lighting across all views, orthographic camera, neutral A-pose**（Scenario turnaround 指南；视角会漂移需迭代）。
- CN：角色概念设计、三视图 / 角色设定图、立绘、概念厚涂、游戏美宣。
- 模型：Scenario 等 turnaround 工具；GPT Image 2 被厂商页用于 turnaround sheet；中文来源称 Z-Image-Turbo 适合快速草图和概念设计（Krene，2025–2026）。
- 易混：半写实人像（4.1，追求整幅完成度与氛围而非设计可读性）。

**4.4 实画漫画写实　Painted Comic Realism（Alex Ross 一脉）**
- 坐标：A1 · B1/B3（以实画颜料达到的照片写实光影）· C0 · D3（水粉/不透明颜料）。
- 识别：无墨线、真人模特感、Norman Rockwell 式美式插画传统【背景知识·未核实】；与「墨线 + 平涂」的传统漫画相反。Krea2 风格名 "American Comic Realism"、"Photorealistic Comic Ink-and-Paint Hybrid"。
- EN：painted comic cover, gouache, photorealistic superhero, Rockwell lighting【推断】。
- CN：实画漫画写实、美漫油画风。
- 易混：现代数字漫画渲染（家族五 5.2，保留墨线）；写实油画（家族六）。

**4.5（边界）韩系半写实 / 韩漫　Korean Semi-Realism · Manhwa / Webtoon**
- 坐标：身体 A1 · 脸 A2–A3 · B4 · **C2 干净线** · E 低饱和粉肉肤色 · F 韩漫。
- 识别（韩系 vs 日系快速检查【推断】）：眼睛占脸比例明显更小、眼型细长、有睫毛双眼皮刻画；鼻有完整鼻梁鼻翼；7.5–8 头身、肩颈真实；皮肤柔和体积渲染而非赛璐璐硬阴影；都市时尚服装；网漫原图为竖长画幅与对话气泡。韩系 vs 西方半写实：面部理想化模板高度统一（「美型」、小脸尖下巴、「混血感」）、线稿常保留且干净（网漫量产工作流），西方半写实更常无线稿、面部特征更多样。【背景知识·未核实】韩国游戏插画（NCSoft、Pearl Abyss、Nexon 宣传图）为高完成度厚涂、华丽服饰材质，常被中文圈称「韩式厚涂」。
- EN：**Korean manhwa art style, webtoon, clean lines, expressive faces, full color**（Carat.im）、**modern manhwa style, clean lineart, vertical scroll composition**（Morphic）、soft cel shading, semi-realistic proportions, fashion illustration, glossy hair。
- CN：**韩漫风格、韩国网络漫画、清晰线稿、柔和上色**（网易）、韩系半写实、韩式厚涂、韩风半写实。
- 模型 / LoRA†：吐司 "SOLO LEVELING (style)"（SD1.5，作者自述质量一般；《Solo Leveling》漫画绘者 Jang Sung-rak / DUBU）；LiblibAI「漫画韩漫系头像工作流」；专用 manhwa 生成器（LlamaGen 等厂商页）。
- 定位：线稿 + 柔和上色 + 风格化脸 → 这是**二次元边界**；但身体比例写实、脸偏写实的「韩系真人向半写实」仍落在本家族。

**4.6（边界）伪厚涂 / 半厚涂　Cel-painterly Hybrid**
坐标：A3+ · B4（块面内柔化过渡）· C1–C2（保留但减弱的线稿）· D3。见 §4.5 的定义讨论；基本等同二次元范畴。EN 无对应词：line art with soft painterly shading, semi-cel, anime-realism hybrid【推断】；LoRA†："Zavy's Detail Anime/Digital Realism (Flux)"（线稿 + 写实明暗，触发词 `zavy-dtlnm`，0.7–1.3，主要为风景训练）；SD1.5 2.5D checkpoints（Dark Sushi 2.5D 等）。

### 家族五：平面与图形　Flat & Graphic

坐标特征：B5/B6（无体积渲染或仅两阶阴影）、C2 或 C0（轮廓明确或完全省略）、**D4/D5（印刷/屏幕工艺纹理或矢量平面）**、E 色块干净。社区观察到的 AI 常见失败：像素格不一致、贴纸白边不闭合、flat vector 混入体积阴影（故社区依赖 Midjourney `--sref` 与负向词 "no 3D render"）。

**5.1 美式经典漫画　American Comic（Golden / Silver Age · Pop Art）**
- 坐标：A2–A3 · B5/B6 · **C2 粗细变化墨线** · **D4 网点 + 纸纹** · E 高饱和原色。
- 识别：粗黑墨线轮廓 + 平涂原色 + Ben-Day / halftone 印刷网点 + 动态线 + 新闻纸质感。
- EN：**bold black contour lines, flat saturated colors, dense halftone dot shading to evoke vintage comic printing**（Carat.im comic cover）、**thick ink outlines, cel shading, action lines, vivid flat colors**（gptprompts.ai）、**halftone printing texture, strong primary color palette**, newsprint texture, 1960s pop art；负向 **no 3D render**。注意：DALL·E 3 曾拒绝已故艺术家 Roy Lichtenstein 风格请求（Pearl Cohen），pop art 锚点在 OpenAI 产品中可能被拒。
- CN：美漫风（「欧美漫画的粗犷线条、立体感、夸张的人物特征」——网易；「厚重线条和强烈明暗对比」——HANYUAI）、墨线 + 平涂、网点、波普艺术；即梦 4.0 速查表风格词含「美漫」。
- 模型 / LoRA†：SAI 预设 `comic-book`（"comic, graphic illustration, comic art, graphic novel art, vibrant"）；HF "RealisticComicbookStyle"（Flux）；中文来源称 Flux-Kontext 适合美漫和写实风格（Krene）。
- 易混：Spider-Verse 路线（3.2，3D 底子）；ligne claire（5.3，等粗线无网点无投影）。

**5.2 现代数字漫画渲染　Modern Digital Comic Rendering**
- 坐标：A2 · B4（柔和渐变、光效、材质贴图）· C2 墨线保留 · D3/D5（网点消失、出现镜头光晕）。
- 识别：介于 cel 与 painterly 之间——相当于中文「伪厚涂」的美式对应【推断】；Krea2 风格名 "Marvel Comics Style"。
- 易混：painted comic realism（4.4，无墨线）；美式经典漫画（有网点）。无权威描述来源（Gap）。

**5.3 欧漫清线派　Ligne Claire（Hergé / Moebius）**
- 坐标：A3（卡通人物）· **B6（阴影极少、投影被「照亮」）** · **C2 等粗干净线、无排线** · D5 · E 强色块；人物置于写实背景。
- 识别：「clear strong lines sometimes of varied width and no hatching」、「contrast is downplayed, and cast shadows are often illuminated」、「cartoonish characters against a realistic background」（Aesthetics Wiki）；Hergé 作品「几乎所有线等粗」（Comics Odyssey）；名称由 Joost Swarte 1977 年提出。【背景知识·未核实】Moebius 一脉常在 ligne claire 骨架上加细密排线与迷幻配色。
- EN：**ligne claire, clear line, uniform line weight, no hatching, flat colors, minimal shadows**, Hergé style, Moebius style, fine ink lines, pastel sci-fi palette。
- CN：欧漫清线派、丁丁历险记风。
- 易混：美式漫画（有网点与投影）；flat vector（无手绘线质感）。

**5.4 黑色电影式墨绘　Graphic Noir · Noir Ink（Sin City）**
- 坐标：A1–A2 · **B6 两值（无中间灰阶）** · C2 · E 黑白 + 单一饱和色点睛。
- 识别：Frank Miller 的 Sin City「eliminate gradients and midtones, sculpting the world purely through stark light and deep shadow」；电影版（2005）黑白拍摄、后期局部加色于「red lips, blood, or a single object」。
- EN：**stark black-and-white contrast, bold linework, monochrome**（Tensor.Art "Graphic Noir: Sin City Style v2.0" 推荐 tokens）、heavy solid blacks, no midtones, spot color red。
- CN：黑白高反差墨绘、罪恶之城风、黑色电影墨线。
- 模型 / LoRA†：Flux "Graphic Noir: Sin City Style v2.0"（Tensor.Art）；SD1.5 Sin City LoRA 权重 0.5–0.6（超过会扭曲面部），点睛色红/黄/绿偶尔蓝；2026 年有 "Sin City photo generator" 类工具。
- 易混：黑白素描（家族六，有连续灰阶与纸纹）。

**5.5 扁平插画 / 矢量　Flat Illustration · Flat Vector**
- 坐标：A3–A4 · B6（无渐变或仅微渐变、2 阶阴影）· C0/C2 · **D5（边缘绝对锐利、无纹理）**。
- 识别：几何化造型、可缩放感；Recraft `vector_illustration` 定义「通常同时只用少数几种颜色，形状以纯色或简单渐变填充」，V4 的 vector 变体可输出可编辑 SVG。
- EN：**flat vector, clean vectors, bold colors, clear silhouettes, color blocking**（Underwood Xie；Neura Market）、**flat vector art style, thick outlines, crisp uniform edges**（Krea feed）、**simple flat color, 2-dimensional**（diva `Flat 2D Art`，负向 "3D, photo, realistic"）；Recraft `vector_illustration`。
- CN：扁平插画、矢量插画、矢量人物；通义万相预设「扁平插画」（2023）；Firefly Popular「Flat design」。
- 模型：Midjourney（"flat vector is surprisingly easy to get wrong"，好的 `--sref` 码给出更强的 visual grammar）、Recraft V4/V4.1（2026-02 / 2026-05-14）vector 输出。
- 易混：Corporate Memphis（5.6，是其子类）。

**5.6 企业扁平人物　Corporate Memphis · Alegria**
- 坐标：A4（长而弯曲的四肢、极简面部）· B6 · C0 · D5 · E 明亮粉彩、非写实肤色（蓝/紫/橙）、无阴影。
- 识别与来源：2017 年 Facebook 委托 Buck 设计的 "Alegria" 系统（插画师 Xoana Herrera）；「flat human characters in action, with disproportionate features such as long and bendy limbs」、「bright colors without any blending」（shots.net；Branded Agency）；批评为「generic, overused」。
- EN：**Corporate Memphis, Alegria style, long bendy limbs, minimal faces, bright pastel, no blending**。
- CN：企业扁平人物风、Alegria 风、大厂插画风。
- 易混：通用 flat vector（5.5）。

**5.7 孔版 / 丝网印刷　Risograph · Screen Print**
- 坐标：A3 · B6 · C0/C2 · **D4（粗颗粒、套印错位、纸色透出）** · **E 2–3 色荧光专色**。
- 识别：「a limited set of soy spot inks (often fluorescent pink and blue), deliberate misregistration where the colour layers do not quite line up, and heavy mottled grain with the paper showing through」（Morphic）。
- EN：**risograph, spot inks fluorescent pink / blue, misregistration, mottled grain, halftone, overprint**；显式写 **fluorescent pink over teal blue, slight misregistration offset**（Media.io）；**bold fluorescent spot-color overprinting, visible ink layering, coarse halftone dots, paper grain**（Magic Hour）。
- CN：Riso 孔版风、丝网印刷、套印错位；混元旧表有「版画」。
- 易混：pop art 网点（5.1，网点规则、黑线粗、原色）。

**5.8 贴纸风　Die-cut Sticker**
- 坐标：A4–A5 · B6 · C2（白色描边）· D5 · 透明/纯色背景、轻微光泽。
- EN：**sticker design, die-cut, white background, clean edges, vector style, flat illustration, no shadows**（PromptSpace 2026 "magic words"）、**thick white die-cut border that follows its outline**, glossy vinyl finish（God of Prompt；与 "no shadows" 冲突，取决于要不要实体感）。
- CN：贴纸风、白边贴纸、表情包贴纸。
- 易混：flat vector（无白边）。

**5.9 像素画　Pixel Art**
- 坐标：A4–A5 · B5 · C2（像素级轮廓）· **D4 像素格对齐网格、限色板、无抗锯齿**。
- EN：**pixel art, pixel style, 8-bit style, 8-bit pixel art, 16-bit, 24-bit, 4-color palette, NES color palette, front-facing, isometric**（OpenArt；QuillBot；Stockimg）；Recraft `digital_illustration/pixel_art`；Stability 预设 `pixel-art`；Civitai 家族 `pixel_retro`。
- CN：像素画、像素风（文心一格关键词）、8-bit；混元旧表「像素」。
- 模型：Adobe Firefly pixel art generator 功能页；Midjourney 像素提示词合集；AI 失败品常有不等大像素，需后期量化。
- 易混：低多边形 / voxel（家族二 2.9，3D）。

**5.10 极简线稿 / 一笔画　Minimal Line Art · Continuous Line**【背景知识·未核实】
- 坐标：A3–A5 · B6 · C2 单线 · D5 · 无填色或单点色。EN：minimal line art, single continuous line, one-line drawing；Stability 预设 `line-art`。CN：极简线条画、一笔画。配额耗尽前未检索专项来源。

**5.11 海报艺术　Poster Art**【背景知识·未核实】
- 大块面 + 强对比 + 文字排版位；Recraft `digital_illustration/2d_art_poster`；Firefly/混元旧表的「波普」「极简」。EN：poster art, graphic poster composition, bold typography space。CN：海报风。

### 家族六：传统媒材模拟　Traditional Media Emulation

坐标特征：**D3（真实媒材的物理签名）** 主导；A 轴可从写实到风格化。提示词核心原则：**命名媒材 + 命名其物理特征**（水彩写透明叠色、水花 blooms、纸纹；油画写 impasto、笔触方向、画布纹理；水墨写留白、墨色浓淡、宣纸晕染；工笔写细线勾勒、层层渲染、绢本设色——BudgetPixel 媒材指南；本报告综合）。2025–2026 模型综述普遍把 Midjourney 列为「风格/艺术方向」首选，Flux 2 在「stylized and illustrative」上不领先，Nano Banana 2/Pro、Seedream、GPT-image 更以指令遵循与文字见长——**但本轮未找到任何对油画/水彩质感的横向实测**。以下媒材的「快速视觉检查」均为【背景知识·未核实】。

**6.1 油画　Oil Painting**（古典写实 / 印象派 / Sargent 式）
- 识别：不透明、可见笔触堆叠与画布织纹、暗部深沉、高光厚涂突起（impasto）；古典写实 = 光滑罩染、Rembrandt 三角光、暗背景；印象派 = 断续色点、无线性轮廓、冷暖并置；Sargent 式 = 大笔触「一笔成形」的湿画法。
- EN：**oil painting, impasto technique, rich textures, bold and expressive brushstrokes**（Midjourney V7 示例）、canvas texture, **Rembrandt lighting**, chiaroscuro, classical realism, alla prima, Sargent-style loose brushwork, Impressionism；twri `artstyle-impressionist`；Krea2 "Contemporary Oil Painting / Impasto / Chiaroscuro / Tenebrism"。
- CN：油画、古典写实、伦勃朗光、印象派、厚重笔触、画布纹理；中文平台预设：通义万相「油画」、混元「油画 / 梵高 / 莫奈」、文心一格「油画」。
- 模型 / LoRA†：Midjourney（`--sref` / `--p` + 媒材词）；Flux "Zavy's Rough Paint"（impasto）；Flux 2 不以此见长（Switas 2026）。
- 易混：**厚涂**（4.2，无真实画布与颜料厚度、色彩更鲜、边缘数码化）；hyperrealism 绘画（1.9）。

**6.2 水彩　Watercolor**
- 识别：透明、白纸作高光、边缘水渍/水花（blooms）、颗粒沉积（granulation）、留白。
- EN：**watercolor, transparency, blooms of pigment, paper-grain texture**（BudgetPixel）、wet-on-wet, granulation, white space；Firefly Techniques 示例。
- CN：水彩、湿画法、水渍、纸纹、留白；通义万相 / 混元 / 文心一格均有「水彩」预设；Canva Magic Media 预设 "Watercolor"。
- 易混：绘本路线 3D（3.3，Wish 的纸纹叠在 3D 几何上）；水墨（6.6）。

**6.3 水粉　Gouache**
- 识别：不透明、哑光、平整色块、边缘干净——接近「平涂但手绘」。EN：gouache, opaque matte, flat planes。CN：水粉、不透明哑光。
- 易混：flat vector（无笔触与纸纹）；painted comic realism（4.4 用水粉达到写实）。

**6.4 炭笔 / 铅笔素描　Charcoal · Graphite Sketch**
- 识别：单色、纸纹、涂抹与橡皮提亮、排线、连续灰阶。EN：charcoal sketch, graphite, cross-hatching, smudged, pencil drawing；Firefly Materials "Charcoal"；Stability `line-art`。CN：炭笔素描、素描、排线；通义万相「素描」预设。「彩铅」在所有检索结果中均未出现（Gap）。
- 易混：noir ink（5.4，无灰阶）；TMNT 速写路线（3.3，3D 底子）。

**6.5 色粉　Soft Pastel**
- 识别：粉质颤动笔触、高饱和、颗粒纸纹、边缘毛糙。EN：soft pastel, chalky texture；Midjourney 社区参考 "Crayon, Chalk, and Pastel" 子类。CN：色粉、粉彩。无专项 AI 来源（Gap）。

**6.6 水墨（写意）　Chinese Ink Wash · Sumi-e**
- 识别：留白、墨分五色、宣纸晕染、少数几笔定形。
- EN：**Chinese Ink Wash Painting**（中文画风指南的标准英译）、**Chinese ink wash painting style illustration of a graceful woman wearing pale hanfu holding an oil-paper umbrella in gentle rain**（Media.io Gemini 示例），加 **xuan paper** texture、朱砂印章（vermilion seal）、留白（negative space）、85mm 景深等修饰；sumi-e, xieyi, rice paper bleed。
- CN：**国风水墨，远山近水，留白，墨色晕染，意境悠远**；人像：**白衣仙子，长发飘逸……水墨淡彩风格，柔光，国风仙侠**（知乎即梦提示词大全 2026）；中文平台预设：混元「水墨画」（编号 101）、通义万相「中国画」、吐司「国风」频道。「国风」在所有中国平台都是独立一级类目——这是中国平台相较 Civitai 等海外社区最显著的分类差异。
- 模型 / LoRA†：FLUX fp8 + Taomitown 自定义水墨 LoRA（权重 0.8，1024×1536，ComfyUI.org 2025-03-26）；SD1.5 "inkColor·墨彩 0.10"（0.5–0.8，「works exceptionally well for any model except real human models」）；"ShuimohuaAnime"（水墨 + 动漫，GyozaMix 系）；新一代中文原生模型（即梦 4.0、Seedream、混元图像 3.0、可图 2.0）对中文风格词理解良好，「如何英译」的重要性下降，只在用 Midjourney / Flux / Nano Banana 等英文优先模型时才需拆解。
- 易混：工笔（6.7，细线 + 多层薄染、无写意笔墨）；水彩（6.2）。

**6.7 工笔　Gongbi**
- 识别：先以细劲均匀的墨线勾勒轮廓，再逐层叠加墨色与颜色（Wikipedia: Gongbi）；绢/纸本、装饰性设色、无西式明暗；【背景知识·未核实】「三矾九染」。
- EN：**Chinese traditional gongbi painting, court-lady portrait**（CreateIO，标注适合 Nano Banana、Hunyuan）、**hanfu, chinese, traditional**, gongbi, fine-line brushwork, layered mineral pigments, silk scroll, Tang dynasty court lady。
- CN：工笔、勾线渲染、绢本设色、唐风、国风、汉服、古风、新中式。「国风」是伞形词，英文必须按子类拆：水墨 ink wash、工笔 gongbi、汉服 hanfu；「国潮」「新中式」**无稳定英译且无来源证实**（可能写 `neo-Chinese graphic style`，未验证）。本次检索未找到 `guofeng` 作为英文提示词的用法。
- 模型 / LoRA†：Flux.1（「基础算法_F.1」）+「唐风工笔娃娃_v1.0」（权重 1.0，1024×1920，≤8GB 显存，ComfyUI.org 2025-04-17）；SD1.5 时代 GuoFeng3（xiaolxl，被归「2.5D 模型」，适合古风人物服饰，吐司/海艺预设榜单常见）；LiblibAI「国风-中国武侠风|传奇色彩」LoRA；Seedream 4.0「电影感国风海报」（《洛神赋》）与古风/民国风模板（Apiyi）。
- 易混：水墨写意（6.6）；韩系古风（F 轴不同）；敦煌壁画风（`Dunhuang Murals`，混元旧表「敦煌壁画」）。

**6.8 其他印刷与手工艺（一句带过）**
剪纸（混元「剪纸 / 新年剪纸画」；Flux Paper-cut_v1.0 LoRA 偏装饰图案；Stability `origami`）、刺绣、皮影、版画（混元旧表）、浮世绘 Ukiyo-e（ArtBench 类别；文心一格关键词）、cyanotype / chromolithography / fayum portrait 等（marc_k3nt3l 的 62 项风格包全部是传统媒介/印刷工艺）。它们在人像上多为题材装饰而非主流，故不展开。

---

## 6. 速查法：如何看图判断画风

### 6.1 五步判别流程（按顺序执行）【推断，综合各来源】

```
第 1 步  看阴影的边界
        ├─ 阴影被切成界线分明的色块（2–3 阶）────────────► cel / 三渲二 / 赛璐璐
        │     └─ 再看比例与线：大眼小鼻 + 干净等宽线 ──► 二次元边界（本报告不收）
        │        否则 ─────────────────────────────► 西方 toon shading（家族三 3.4）/ 美漫（5.1）/ ligne claire（5.3）
        ├─ 几乎没有阴影 ────────────────────────────► 家族五（flat / vector / Corporate Memphis / sticker / pixel）
        └─ 阴影是连续的 ─────────────────────────────► 进入第 2 步

第 2 步  看皮肤与眼睛（决定「照片 vs 渲染」）
        ├─ 毛孔随机、ISO 噪点随亮度变化、镜头色差/畸变、焦外不规则、
        │  有 halation/bloom、轻微运动模糊 ────────────► 家族一 摄影写实（再按 1.1–1.8 细分）
        ├─ 皮肤有 SSS 感但过于均匀、统一油亮高光、瑕疵缺失、
        │  双眼反光完美对称、零噪点、理想圆形散景 ──────► 家族二 2.1 超写实数字人
        └─ 皮肤不是「写实皮肤」（光滑塑料 / 搪胶 / 黏土 / 笔触）► 进入第 3 步

第 3 步  看比例与材质（3D 家族内部细分）
        ├─ 大眼大头、皮肤仍有 SSS 与发丝、全局光自洽 ──► 2.2 Pixar/Disney 风 或 2.3 游戏风格化
        ├─ 1–3 头身、搪胶哑光、极简五官、底座/包装 ─────► 2.4 盲盒/潮玩（有写实桌面场景 + PVC → 2.5 写实手办渲染）
        ├─ 指纹与捏痕、哑光微粒 ─────────────────────► 2.6 黏土
        ├─ 纤维绒边、几乎无高光 ─────────────────────► 2.7 毛毡
        ├─ 圆角几何 + 磨砂 + 双色渐变 + 轴测 ──────────► 2.8 C4D 软 3D
        ├─ 可见多边形面 / 体素格 ────────────────────► 2.9 低多边形
        └─ 不是以上任何「3D 材质」，而是有笔触/纸纹/网点 ─► 进入第 4 步

第 4 步  看 2D 工艺痕迹是叠在 3D 几何上，还是本身就是 2D
        先判「几何是否处处自洽」：体积/透视/光照在所有部位绝对一致、同一角色转面完全同构、
        贴图在转折处被拉伸、景深为渲染器式圆形光斑 ───► 3D 底子 → 家族三
        │     ├─ 网点 / 排线 / 墨线 / 套印错位 ──────► 3.2 Spider-Verse 路线
        │     ├─ 可见笔触贴图但无硬阴影 ───────────► 3.1 Arcane 路线
        │     └─ 纸纹 / 水彩边 / 速写线 / 刻意不完美 ─► 3.3 绘本/速写路线
        否则（有透视与解剖的人工偏差、笔触方向与形体不完全吻合、
        刻意丢失边、「为了好看」的不合理补光）──────────► 2D 底子 → 进入第 5 步

第 5 步  区分 2D 体积画法与传统媒材
        ├─ 数字笔触、色彩鲜亮、边缘软硬交替、无真实画布/纸张物理 ─► 家族四
        │     ├─ 光滑高光、无可见笔触、眼睛放大 ──────► 4.1 西式光泽半写实
        │     ├─ 笔触塑形、线稿被颜色吞掉 ───────────► 4.2 厚涂
        │     ├─ 设计可读性、道具标注、松散边缘 ──────► 4.3 概念设计
        │     ├─ 保留干净线稿 + 柔和上色 + 统一美型脸 ─► 4.5 韩系（边界）
        │     └─ 保留减弱线稿 + anime 比例 ──────────► 4.6 伪厚涂（边界，不收）
        └─ 有真实媒材物理签名 ────────────────────────► 家族六
              ├─ 画布织纹 + 颜料厚度 ─► 6.1 油画      ├─ 透明 + 水渍 + 纸纹 ─► 6.2 水彩
              ├─ 不透明哑光平整 ─────► 6.3 水粉      ├─ 单色 + 纸纹 + 排线 ─► 6.4 素描
              ├─ 留白 + 宣纸晕染 ───► 6.6 水墨      └─ 细线勾勒 + 多层薄染 ─► 6.7 工笔
```

### 6.2 八对最易混淆的邻近画风与「一眼靶心」

| 混淆对 | 一眼靶心 | 来源/性质 |
|---|---|---|
| AI 照片 vs 超写实 3D 渲染 | 介质签名：噪点统计、镜头缺陷、halation 只在照片有；渲染是「全局一致的完美」 | Eyesift；Higgsfield；【推断】 |
| Pixar 风 3D 角色 vs 写实手办渲染 | 材质：前者皮肤「可信」有 SSS；后者是真实 PVC/塑料 + 桌面/包装/底座 | Nano Banana、GPT-4o 潮流提示词 |
| Arcane 式 3D vs 2D 厚涂 | 几何一致性；Arcane 无硬阴影但转面同构，厚涂有丢失边 | UAL 博客；【背景知识】 |
| Spider-Verse 式 3D vs 美式漫画 | 体积与透视是否 3D 自洽；网点在前者是叠加层 | Dark Horizons；Carat.im |
| 三渲二 vs 手绘二次元 | 阈值阴影在所有角度完全一致、描边等宽；手绘有线条粗细与阴影形状的人为变化 | wellstsai；【推断】 |
| 厚涂 vs 油画 | 真实画布织纹、颜料厚度与裂纹、受颜料限制的偏灰色彩 → 油画 | 【推断】 |
| 韩漫 vs 日漫 | 眼睛大小 / 鼻子完整度 / 身体比例 / 全彩竖版 | Tropedia；90 Day Korean；机核 |
| Ligne claire vs 美式漫画 | 阴影几乎不存在 + 等粗线 + 无排线 → ligne claire | Aesthetics Wiki |

### 6.3 识别「AI 味」的三层线索（判断「是不是 AI、是哪个模型」，而非画风）

- **介质层**：无传感器噪点或均匀噪点、无镜头缺陷、过度锐利、前景光相对背景过强（Sightengine；Eyesift）。
- **生理层**：塑料/蜡质皮肤、完全对称的脸（SelfieLab 2026-02 有专门教「雕刻真实面部不对称」的教程）、牙/手错误、眼睛过亮过锐、双眼反光不一致（Skylum；IsItAI）。皮肤过度光滑并非决定性证据，因为专业精修多年来也会抹平皮肤（Skylum）；多个来源一致建议「寻找多个相互独立且一致的信号，而非单一线索」。
- **模型签名层（版本相关，变化最快）**：FLUX 的「Fluxia」同脸与裂纹下巴 "Flux chin"、"Flux cheeks"、"Flux bokeh" 永远虚化的背景（2024-11 起社区讨论；2026-01 博客命名 Fluxia，成因为博客推测非官方说明）；Midjourney「默认脸」（零散个人报告，无量化研究）；GPT-4o 图像（2025-03）的黄/褐色偏 "piss filter"（Freepik 用 RGB 缩放量化并修正；OpenAI 无官方说明；GPT Image 1.5 / 2 是否消除未能确认）。
- 对策分层【推断】：**提示词**（命名具体光源、镜头、胶片、瑕疵词 `freckles, pores, laugh lines`，避免 `8k, hyperrealistic` 类堆词）→ **参数**（Flux guidance 从默认 3.5 降到约 2；Midjourney `--style raw` + 低 `--stylize`）→ **权重**（Amateur Photography / Boreal 快照 LoRA；Chin Fixer 2000、UnFlux 等修脸 LoRA；皮肤纹理 LoRA 强度约 0.4）→ **后处理**（低 denoise img2img、Flux Kontext "kontext-make-person-real"、加噪/加颗粒、RGB 色偏校正）。闭源模型只有提示词与后处理两层。
- 代际迁移【推断】：2022–2023「手/牙/眼结构错误」→ 2024「Flux 式太完美」→ 2025–2026「色彩/介质签名缺失 + 同一张脸」；FLUX.2 Klein 9B（2026）仍有 "plastic skin bug" 社区报告。

---

## 7. 中英提示词词表

### 7.1 按坐标轴组织（把「坐标」翻译成词）

| 轴 / 刻度 | English | 中文 | 备注 |
|---|---|---|---|
| A1 写实比例 | realistic proportions, naturalistic anatomy, 7.5–8 heads tall | 真人比例、写实解剖 | — |
| A2 轻度理想化 | idealized face, subtle facial asymmetry（防过度对称） | 美型、精致五官 | asymmetry 用于对抗 AI 对称感 |
| A3 明显风格化 | **big expressive eyes, slightly exaggerated features**, stylized facial proportion | 大眼、夸张五官、风格化 | Pixar 潮流用法 |
| A4 卡通/Q 版 | **chibi**, 1-head-tall, big head small body, **adorable character** | Q 版、1 头身、大头小身 | — |
| B1 物理写实渲染 | **subsurface scattering** skin, **physically-based materials**, global illumination, strand-based hair | 次表面散射、PBR 材质、发丝级毛发 | 2.1 / 2.2 |
| B2 简化 PBR | smooth shading, soft matte materials, polished specular response | 柔光材质、哑光、光滑 | 2.2–2.8 |
| B3 厚涂 | **painterly**, **visible brushstrokes**, **blended brushwork**, **impasto**（仅颜料堆叠义）, lost edges | 厚涂、笔触感、丢失边 | 直译 impasto 会偏油画 |
| B4 柔和渐变 | soft shading, smooth gradient rendering, glossy highlights | 柔和上色、半厚涂、光泽 | 4.1 / 4.5 |
| B5 多阶 cel | **cel shading, toon shading**, two-tone shadows, **hard-edged tonal division** | 赛璐璐、三渲二、二分阴影 | 边界 |
| B6 平涂 | **flat color**, no shadows, **simple flat color, 2-dimensional** | 平涂、无阴影 | 5.x |
| C0 无线 | lineless, no outlines | 无线稿 | — |
| C1 局部线 | partial visible lineart, sketchy pencil lines, loose inking | 局部线稿、速写线 | 3.x / 4.6 |
| C2 全轮廓线 | **bold black ink outlines**, **clean line art**, **uniform line weight**, thick outlines | 粗墨线、清晰线稿、等粗线 | 5.1 / 5.3 |
| D1 照片介质 | **film grain**, sensor noise, chromatic aberration, **halation**, vignette, slight motion blur, **natural skin texture, visible pores** | 胶片颗粒、噪点、色差、光晕、暗角、自然肤质、毛孔 | 对抗塑料感「最强的单一线索」是皮肤纹理词（Higgsfield） |
| D2 CG 表面 | **3D render**, **octane render**, **unreal engine 5**, cinema 4d, redshift, **ambient occlusion**, **volumetric lighting** | 3D 渲染、OC 渲染、C4D、虚幻 5 | 写实照片场景中是反效果词 |
| D3 传统媒材 | canvas texture, **paper-grain texture**, impasto, **blooms**, granulation, rice paper bleed | 画布纹理、纸纹、水渍、宣纸晕染 | 6.x |
| D4 印刷伪影 | **halftone dots**, **Ben-Day dots**, **misregistration**, **mottled grain**, newsprint texture, pixel grid | 网点、套印错位、粗颗粒、新闻纸、像素格 | 5.1 / 5.7 / 5.9 |
| D5 矢量平面 | **flat vector**, **clean vectors**, crisp uniform edges, scalable | 矢量、锐利边缘 | 5.5 |
| E 摄影布光 | **Rembrandt lighting**, butterfly lighting, beauty dish, **direct flash**, golden hour, **tungsten light** | 伦勃朗光、蝴蝶光、直闪、钨丝灯 | 命名具体光源可对抗「中性正面光」默认 |
| E CG 布光 | **three-point lighting**, **rim light**, soft studio light | 三点布光、轮廓光、柔和棚光 | — |
| E 配色 | **teal and orange** color grading, macaron palette, **flat saturated primary colors**, **fluorescent pink / blue spot inks**, monochrome + spot color red | 青橙调色、马卡龙配色、高饱和原色、荧光专色、黑白单点色 | — |
| 镜头 | **85mm f/1.4**, 50mm, 35mm, **shallow depth of field**, large depth of field, anamorphic lens, cinemascope | 85mm 定焦、浅景深、大景深、变形镜头 | 「加入相机与镜头参数会立即提升写实感」（oakgen） |
| 胶片 | **Kodak Portra 400**, Kodak Vision3, **CineStill 800T**, Ilford HP5, **Kodachrome, Lomography** | 柯达 Portra 400、柯达金 200、胶片型号 | 胶片词同时编码颗粒、色彩科学、动态范围与典型场景 |

### 7.2 按家族组织的「一行提示词骨架」【推断，综合来源的逐字词】

| 家族 / 画风 | English 骨架 | 中文骨架 |
|---|---|---|
| 1.1 影棚头像 | portrait photo, 85mm f/1.4, Rembrandt lighting, shallow depth of field, natural skin texture, fine film grain, Kodak Portra 400 — negative: plastic skin, HDR, CGI, waxy skin | 影棚人像，85mm，伦勃朗光，浅景深，自然肤质，细腻胶片颗粒，不过度磨皮 |
| 1.3 电影剧照 | cinematic film still, shallow depth of field, vignette, cinemascope, moody, film grain | 电影剧照，变形镜头，暗角，胶片颗粒，电影调色 |
| 1.5 快照 | early 2010s snapshot photo captured with a phone, direct flash, large depth of field, candid | 手机直出生活照，直闪，大景深，随手拍 |
| 1.8 港风 | 1980s–90s Hong Kong street, neon signs, tungsten light, cha chaan teng, film grain, green-red cast | 港风人像，茶餐厅/霓虹街道/天台，80–90 年代服装，钨丝灯霓虹混光，胶片颗粒 |
| 2.1 超写实数字人 | photoreal 3D render of a digital human, subsurface scattering skin, strand-based hair, three-point lighting, no film grain, unreal engine 5 | 超写实数字人 3D 渲染，次表面散射皮肤，发丝级毛发，三点布光，虚幻 5 |
| 2.2 Pixar 风 | Pixar style 3D character, big expressive eyes, soft lighting, colorful background, subsurface scattering, three-point lighting | 皮克斯风 3D 角色，大眼，柔光，彩色背景 |
| 2.4 盲盒 | blind box designer toy, vinyl toy style, chibi figure, matte vinyl, macaron palette, clean background, soft studio light, C4D render | 盲盒风格，泡泡玛特风格，Q 版手办，1 头身，马卡龙配色，干净背景，C4D/OC 渲染，哑光材质 |
| 2.5 写实手办 | 1/7 scale commercialized figure, realistic style and environment, computer desk, circular transparent acrylic base, packaging box behind, PVC material | 1/7 比例手办，写实场景，电脑桌，透明亚克力底座，包装盒，PVC 材质 |
| 2.6 黏土 | claymation, play-doh style, clay art, visible fingerprint dents, stop-motion lighting | 黏土定格动画风，可见指纹捏痕 |
| 2.8 C4D 软 3D | 3D render, C4D style, soft matte materials, rounded geometry, frosted glass, soft two-tone gradient, isometric | 3D 渲染，C4D 风格，柔光材质，圆角几何，磨砂玻璃，双色渐变 |
| 3.1 Arcane 路线 | painterly 3D render, hand-painted textures, painted shadows and highlights, no hard shadow edges, oil-painted background | 手绘贴图 3D，绘画感光影，无硬阴影边，油画感背景 |
| 3.2 Spider-Verse 路线 | 3D animation with comic halftone dots, cross-hatching shadows, bold ink lines drawn in 3D, offset printing misregistration, no motion blur | 漫画印刷感 3D，网点，排线阴影，墨线，套印错位 |
| 3.3 绘本路线 | painterly 3D, storybook illustration look, watercolor paper texture, sketchy pencil edge lines, simplified surface detail | 绘本感 3D，水彩纸纹，速写铅笔边线，简化表面细节 |
| 4.1 西式半写实 | semi-realistic digital painting, soft blended shading, glossy highlights, no hard outlines, glowing rim light, naturalistic proportions | 欧美半写实，柔和混色，光泽高光，无线稿，轮廓光 |
| 4.2 厚涂 | painterly digital painting, visible brushstrokes, blended brushwork, lost edges, dramatic volumetric light, no lineart | 厚涂人像，可见笔触，丢失边，强体积光，无线稿 |
| 4.3 概念设计 | character concept art, digital painting, matte painting, character sheet with front/side/back views, orthographic, consistent lighting, neutral A-pose | 角色概念设计，三视图，正交视角，统一光照，A 字站姿 |
| 4.5 韩漫（边界） | Korean manhwa style, clean lineart, soft shading, semi-realistic proportions, full color, fashion illustration | 韩漫风格，清晰线稿，柔和上色，修长比例，全彩 |
| 5.1 美漫 | comic book style, bold black ink outlines, flat saturated primary colors, halftone dots, action lines, newsprint texture — negative: no 3D render | 美漫风，粗墨线，平涂原色，网点，动态线 |
| 5.3 ligne claire | ligne claire, clear line, uniform line weight, no hatching, flat colors, minimal shadows | 欧漫清线派，等粗线，无排线，极少阴影 |
| 5.4 noir ink | graphic noir, stark black-and-white contrast, heavy solid blacks, no midtones, spot color red | 黑白高反差墨绘，无中间调，红色点睛 |
| 5.5 flat vector | flat vector illustration, clean vectors, bold colors, clear silhouettes, color blocking, no gradients | 扁平矢量插画，色块分明，无渐变 |
| 5.7 risograph | risograph print, two-color fluorescent pink over teal blue, slight misregistration offset, coarse halftone, paper grain | Riso 孔版风，荧光双色，套印错位，粗颗粒 |
| 5.8 sticker | sticker design, die-cut, thick white border, white background, flat illustration, no shadows | 白边贴纸风，纯色背景，无阴影 |
| 5.9 pixel | pixel art, 16-bit, limited NES color palette, front-facing, no anti-aliasing | 像素画，16 位，限色板 |
| 6.1 油画 | oil painting portrait, impasto, visible brushstrokes, canvas texture, Rembrandt lighting, chiaroscuro | 油画肖像，厚重笔触，画布纹理，伦勃朗光 |
| 6.2 水彩 | watercolor portrait, transparent washes, pigment blooms, paper-grain texture, white space | 水彩人像，透明叠色，水渍，纸纹，留白 |
| 6.6 水墨 | Chinese ink wash painting, xieyi brushwork, rice paper bleed, negative space, vermilion seal | 国风水墨，写意，宣纸晕染，留白，朱砂印章 |
| 6.7 工笔 | Chinese traditional gongbi painting, fine-line brushwork, layered mineral pigments, silk scroll, hanfu court lady | 工笔人物，勾线渲染，绢本设色，汉服 |

### 7.3 没有精确英文对应的中文术语及其处理

| 中文词 | 问题 | 建议写法 | 性质 |
|---|---|---|---|
| 厚涂 | 词典英译 `impasto` 只覆盖「颜料堆叠」技法义，画风义是「写实立体、无线稿的绘画感」 | 技法义 → `impasto, textured brushstrokes, palette knife marks`；画风义 → `painterly digital painting, soft blended shading, no lineart` | AAT-Taiwan；AIGC.cn；【推断】 |
| 伪厚涂 / 半厚涂 | 无通用英译；属二次元边界 | `anime-style with retained lineart and soft rendered shading` | 【推断】 |
| 平涂 / 赛璐璐 | 技法而非画风 | `cel shading, flat color, clean line art` | 萌娘百科 |
| 盲盒风 / 潮玩风 | `blind box style` 在英文模型中识别度不确定 | 拆成物件/材质词：`designer toy, vinyl toy style, chibi collectible figure, matte vinyl, C4D render` | 【推断】 |
| 手办 | — | `character figure`, `1/7 scale commercialized figure` + 场景道具（包装盒、Blender 建模屏幕、亚克力底座） | 2025 潮流提示词 |
| 国风 / 国潮 / 新中式 | 伞形词；国潮、新中式无稳定英译 | 按子类拆：`Chinese ink wash` / `gongbi` / `hanfu` / `Dunhuang murals`；国潮可试 `neo-Chinese graphic style`（未验证） | 中文画风指南；【推断】 |
| 2.5D | 中文直接用；英文多义 | 不要用；改用坐标描述 | §4.1 |
| 电影感 / 高级感 / 氛围感 | 太泛 | 拆成 `cinematic lighting, anamorphic lens, film grain, color grading` / `low saturation, clean composition, soft directional light` / `moody, low-key, haze, rim light` | Adobe 繁中示例；知乎 2026；【推断】 |
| AI写真 / 证件照 / 形象照 | 产品模板名，不是提示词 | `AI portrait photoshoot` / `ID photo, plain white background, frontal, even lighting` / `corporate headshot, studio lighting, neutral backdrop` | 妙鸭、美图语境 |
| 港风 | — | `1980s–90s Hong Kong street, neon signs, tungsten light, cha chaan teng, film grain`；常与 `Wong Kar-wai style` 混用 | Felo agent |
| 三渲二 / 3D 转 2D | 英文 `cel-shaded 3D` 只对应狭义；广义应按三条路线写 | 狭义 `cel-shaded 3D, toon shader`；广义见 7.2 的 3.1–3.3 | §4.3 |

### 7.4 已过时与仍有效的词（用法而非词本身决定）【推断】

- `trending on artstation`、`masterpiece, best quality`、`8k`、`ultra detailed`：SD1.x（CLIP）时代的质量咒语，Flux / FLUX.2 / Midjourney V7+ 指南普遍建议省去；FLUX.2 不支持负向提示（Black Forest Labs 文档经第三方转引）。但 "ArtStation" 的语义以 "ArtStation Masterpiece"（概念艺术作品集风格）形式存活于 2026 风格手册。
- `octane render / unreal engine 5`：作为**3D 外观的描述词**仍被保留在 2025–26 的 Flux 3D 关键词簇里；作为**写实照片的质量后缀**则被视为反效果（2026 电影写实负向模板把 "CGI look, game render, unreal engine look, 3D render, octane render" 整体列为写实的反面）。
- `hyperrealistic`：AI 语境下常把人像推向抛光 glamour 质感，多篇指南视为反效果；要照片感改写 `visible pores, fine lines, subtle blemishes`。
- `score_9, score_8_up, score_7_up`：Pony/Illustrious 系列特有的质量前缀，对其他模型无意义。
- 没有找到任何受控对比实验证明上述词在 SDXL / Flux / Midjourney V7 上「无效」；「过时」判断均为指南作者的经验陈述。

---

## 8. 2026-10 模型与工具快照：哪种画风该用什么（所有信息带日期，均为「截至该日期」）

### 8.1 旗舰模型版本与日期（据搜索摘要，官方页多数未能直接读取）

| 厂商 / 模型 | 最新版本与日期 | 与人像画风相关的要点 |
|---|---|---|
| OpenAI GPT Image | GPT-4o 图像 2025-03-25；GPT Image 1.5 2025-12-16（快 4 倍、便宜约 20%）；**gpt-image-2 / ChatGPT Images 2.0 2026-04-21**（生成前 reasoning、最高 2K、单次最多 8 张；DALL·E 2/3 于 2026-05-12 退役） | 2026-06 Artificial Analysis 榜首（Elo 约 1338–1339）；提示遵循与文字排版强；Pixar 化 / action figure 潮流入口；2025 年黄色偏「piss filter」（GPT Image 1.5/2 是否消除未确认）；「拒绝在世个人艺术家风格、允许工作室风格」 |
| Google Imagen / Nano Banana | Imagen 4 / 4 Ultra 2025-06-24；Nano Banana（Gemini 2.5 Flash Image）2025-08；**Nano Banana Pro（Gemini 3 Pro Image）2025-11-20**（14 张参考、5 人一致、2K/4K、Search grounding）；**Nano Banana 2（Gemini 3.1 Flash Image）2026-02-26 预览、2026-05-28 GA**（video-to-image、Image Search grounding） | Imagen 4 Ultra 被一份开发者指南称「2026 公开 API 中最照片级输出」；Nano Banana 2 被 Motionbox（2026-03-04）列为写实人像首选；手办化潮流（2025-09）与 Polaroid 潮流的载体 |
| Black Forest Labs FLUX | FLUX.1 2024-08；**FLUX.2 2025-11-25**（Pro / Flex / Dev / Klein；最高 4MP；最多 10 张参考；合并 Kontext 编辑；单一 24B VLM 文本编码器，不支持负向提示）；FLUX.2 [max] 2025-12-17；Klein 9B（2026） | 多篇评测称 FLUX.2 "portrait photorealism leader"（皮肤质感）；但「stylized and illustrative」不领先；Klein 9B 仍有 plastic skin 社区报告；Civitai 上 Flux 2 人像微调最拥挤；LoRA 生态（live-3D、ToyBox、Claymation XC、PPMT 盲盒、RBStyle、UE render、Amateur Photography、Boreal、Chin Fixer 2000、UnFlux）承担细分风格 |
| Midjourney | V7 alpha 2025-04-03/04（需评 200 组图解锁个性化）；V8.0 alpha 2026-03-17；**V8.1 2026-04-30**（最快、原生 2K、需解锁 Global V7/V8 Personalization Profile）；V8.2 据第三方 2026-07-24 成为默认（**未经官方确认**） | 风格靠参数而非预设：`--style raw`（关掉默认美化）、`--stylize 0–1000`（默认 100）、`--sref` + `--sw`（V7 旧码需 `--sv 4`，默认 `--sv 6`）、`--oref`、`--p`；2026 综述普遍列为「风格/艺术方向」首选；写实建议 `--style raw --s 50` |
| ByteDance Seedream / 即梦 Dreamina | Seedream 4.0 2025-08-28 快照（技术报告 arXiv 2509.20427 v1 2025-09-24；30+ 风格、单张人像生成多风格角色图、2D 草图转 3D）；4.5 为 4.x 末版；**5.0 Lite 2026-02-13**（先推理再渲染、联网 grounding、14 张参考）；5.0 Pro 2026-06-23 / 06-28 / 07-08 三说并存 | 商业排版与多图一致性被反复提及；中文风格词理解良好；国风海报、古风/民国风模板；腾讯新闻 2025-09-29 实测称混元图像 3.0「不敌即梦 4.0」 |
| Tencent HunyuanImage | **3.0 开源 2025-09 末**（80B MoE、13B 激活、权重约 170GB）；3.0-Instruct 2026-01-26 | 无固定风格编号表，靠自然语言；旧版混元有「写实 / 3D / 水墨 / 国潮 / 剪纸 …」风格表（2024，约 660 天未更新） |
| Alibaba Qwen-Image / Z-Image / 通义万相 | Qwen-Image 2025-08（20B MMDiT，文字渲染）；**Qwen-Image-2.0 2026-02-10**（生成编辑统一、原生 2K）；Qwen-Image 2.0 Pro 2026-05 快照；**Z-Image-Turbo 2025-11**（6B、8 步、约 16GB VRAM、曾列 AA 开源第一）；Z-Image-Base 2026-01-27/28（可训 LoRA） | Qwen-Image 被评「牺牲微细节换氛围」适合电影感；Z-Image 以写实与中英双语文字见长，LiblibAI 已有「Z-Image-真人拍摄，写实风格」LoRA；通义万相官方文档支持「素描、水彩、油画、中国风、二次元、3D卡通、扁平插画、摄影、人像写真」及参考图风格迁移 |
| Kuaishou Kling / Kolors | KOLORS 2.0 2025-04-15（「60 多种风格化转绘」，名单未公开）；Kling 2.1 2025-05 | 官方文档示例以写实摄影参数为主（「柯达 Portra 400，f/8 光圈……绝对写实」） |
| Recraft | V3（styles 支持；V4 初期不支持）；**V4 2026-02；V4.1 2026-05-14** | 四 base style `realistic_image / digital_illustration / vector_illustration / icon`；realistic 子风格 `studio_portrait, hard_flash, hdr, b_and_w, natural_light`；digital_illustration 子风格 `hand_drawn, grain, pixel_art, 2d_art_poster, bold_fantasy, pop_art, street_art …`；vector 输出可编辑 SVG；Create Style 自定义风格 |
| Adobe Firefly | **Image Model 5 2025-10-28**（图层、自定义模型、4MP）；2026-03-19 再扩展 | 风格面板七组 Popular / Techniques / Movements / Effects / Concepts / Themes / Materials；扩展风格组件仅对 Adobe 原生模型可用；自定义模型保持 line weight、palette、lighting、character features |
| Ideogram | 3.0（发布日期未在本轮结果出现，据训练知识约 2025-03，未验证） | 风格仅 Auto / General / Realistic / Design（2.0 曾有 Anime 与 3D） |
| Leonardo / Canva | Lucid Origin、Phoenix 1.0；Canva Dream Lab 基于 Leonardo Phoenix | 预设按摄影子体裁：Bokeh / Cinematic / Cinematic Close-Up / Portrait / Stock Photo / Fashion / Film（两套 API 版本表不一致） |
| Krea | Krea 1（日期未见） | 定位「artistic photorealism」、消除 "AI look"（soft textures、flat repetitive compositions）；3 张参考 + style weight + LoRA |
| Stability / SDXL 本地 | SDXL 时代 checkpoint 仍为本地写实默认：Juggernaut XL（Ragnarok 2026-02；下载量各源差异巨大 18M+ / 2.5M / 520K+）、RealVisXL V5.0（仅真人人像）、CyberRealistic XL；Flux 需 24GB（Q8 约 12GB），SDXL 约 8GB | SD 3.5 与 Stability 2026 新模型状态：本轮无结果 |

### 8.2 榜单怎么读

- Artificial Analysis（2026-06）：GPT Image 2 (high) 约 1338 居首，Reve 2.1 1301，Nano Banana 2 1261，Nano Banana Pro 1223，Seedream 5.0 Pro 1239（第 8）；DataLearner 转载榜（2026-05-22）却以 Seedream 4 2K 居首，与之冲突，无法调和。
- LMArena / arena.ai（2026-05-12）：OpenAI 1393 第一，Google 1268 / 1242，60 个模型约 517 万票；2 月快照 OpenAI 1248——跳升幅度异常需核对。arena.ai 设 "Photorealistic & Cinematic Imagery" 与 "3D Modeling" 分榜，**是最该引用但本轮未能读取的数据**。
- 结论【推断】：综合榜衡量「整体偏好」，与「人像写实」不等价；写实人像没有单一赢家——GPT Image 2 / Nano Banana 2 强在一致性与指令遵循，FLUX.2 / Imagen 4 Ultra / Midjourney 强在皮肤与光影质感；3D-Pixar 与绘画风人像仍是「基础模型 + 预设/LoRA」的组合题，而非基础模型的竞争点。所有编辑性评测均为平台/厂商博客，缺少独立、方法透明的多模型人像盲测。

### 8.3 按画风的工具选择速查【推断】

| 画风 | 首选（2026-10） | 低成本 / 可控替代 |
|---|---|---|
| 影棚 / 美妆 / 头像 | FLUX.2；Nano Banana Pro（同一人多套写真） | RealVisXL / Juggernaut XL + 皮肤 LoRA |
| Editorial / 时尚 | GPT Image 2；Nano Banana Pro；Seedream 5 | Krea 1 |
| 电影剧照 | Midjourney V8 `--style raw --s 50`；Qwen-Image；FLUX.2 | — |
| 纪实 / 快照 | Flux.1 Dev / FLUX.2 + Amateur Photography / Boreal LoRA（唯一可引用的专门方案） | 闭源模型写介质签名词 |
| 胶片 / 年代 | 开源 + 胶片 LoRA（颗粒、色差、暗角更可控） | 闭源模型直接写胶片型号 |
| 超写实数字人 | Flux + UE render LoRA；Midjourney 写实提示 + `3D render` | — |
| Pixar / 3D 卡通 | GPT Image "Pixar-style" 转绘；Flux live-3D / CToon；MJ sref "3D Design" | 即梦 / 万相「3D 卡通」预设 |
| 盲盒 / 手办 | Nano Banana（手办化）；Flux ToyBox / PPMT / Chibi-Figure / Z1.0 | 即梦 + 中文盲盒提示词骨架 |
| 黏土 | Flux Claymation XC；MJ 黏土 sref；Stability `modeling-compound` 预设 | Firefly Materials「Claymation」 |
| 3D 渲 2D（Arcane / Spider-Verse） | 闭源模型自然语言引用作品名（推断）；Flux Toonic 2.5D 实为半写实二次元定义 | — |
| 半写实 / 厚涂 | Midjourney `--sref`；Flux RBStyle；ZIT Visionarys Semi-Realism | 注意易滑向油画/照片两端 |
| 美漫 / noir | Flux RealisticComicbookStyle；Flux Graphic Noir Sin City v2.0；Stability `comic-book` | SD1.5 Sin City LoRA 0.5–0.6 |
| flat / vector / sticker | Midjourney flat-vector `--sref`；Recraft V4/V4.1 vector（可编辑 SVG） | 通用模型 + 负向 "no 3D render" |
| 油画 / 水彩 | Midjourney（艺术方向首选，无质感实测） | Flux Zavy's Rough Paint（impasto） |
| 水墨 / 工笔 / 国风 | 即梦 4.0 / Seedream / 混元图像 3.0（中文风格词理解好）；Flux + Taomitown 水墨 LoRA / 唐风工笔娃娃 | SD1.5 GuoFeng3 / inkColor·墨彩（不适配真人底模） |

### 8.4 「风格接口」的三代并存及其对分类的含义

(1) **离散预设**（Firefly / Recraft / Leonardo / 万相 / 即梦）——可枚举，是行业分类学的显性证据；(2) **参考图 + 权重**（Midjourney `--sref --sw`、IP-Adapter / InstantStyle、Flux Redux（无权重参数、正向提示词无效）、FLUX.2 原生 10 图、Nano Banana Pro 14 图、Seedream 5.0 Lite 14 图、Krea style weight、Recraft Create Style）——风格成为连续向量，不再有名字；(3) **个人化模型**（Midjourney Personalization Profile、Firefly 自定义模型、Freepik/Magnific 自定义风格 LoRA 10–50 图）——风格成为用户资产。2023–2024 代中文产品用固定风格枚举（万相 1.x、混元旧版、文心一格、WHEE），2025–2026 代（即梦 4.0、Seedream 4.0、混元图像 3.0、可图 2.0）转为自然语言 + 参考图。**含义**：本报告的坐标系应同时容纳「命名风格」与「参考图可达的风格空间」；InstantX FLUX.1-dev IP-Adapter（2024-11-22）作者承认的 content leakage 与 style transfer 权衡，说明「风格 vs 内容」解耦已成用户显性关注点。

### 8.5 法律与伦理要点（2025 年状态，2026 政策极可能已变）

OpenAI 2025-03 随 GPT-4o 图像放开公众人物（改为可主动退出），仍禁止不实诽谤性描绘与未经同意的真人性相关图像；Sora 对在世公众人物仅允许经 Cameos 同意出现，已故名人 2025-10-08 引发争议；Midjourney 与 Grok 允许真人（含公众人物）但有限制；Google 2024-02 暂停人物生成后恢复并加护栏。中国侧：妙鸭相机 2023 年的授权条款与「不支持退款」被上海市消保委质疑；小红书对真人类 AI 笔记加「AI 创作」标识影响流量，创作者转向非真人（头像、国风插画）或「极度真实到不被识别」两极。艺术家名作为提示词：OpenAI 明文拒绝在世艺术家；Stability 自 SD 2.0 起效力大减并为 SD3 接受 opt-out；Midjourney 未搜到禁用规则；Flux 对艺术家名的处理本轮无来源（社区普遍称 Flux「不认识大多数艺术家名」，不要作为事实引用）。**所有公司现行（2026-10）政策原文本轮均未能读取。**

---

## 9. 方法与局限

### 9.1 调研方式

- 调研于 **2026-10-11** 一天内完成，分 7 路并行（理论/工业分类框架；摄影写实家族；3D 家族；2D 体积家族；英文社区分类法；中文社区分类法；2026 模型与工具版图），每路约 35–45 次网页搜索，合计约 250 次。
- **绝大多数来源只能以搜索引擎返回的页面摘要形式读取**：本会话的出站代理对 arxiv.org、wikipedia.org、helpx.adobe.com、recraft.ai、docs.midjourney.com、midlibrary.io、civitai.com、huggingface.co、reddit 及其镜像、80.lv、siggraph.org、beforesandafters.com，以及所有中国大陆托管域名（zhihu.com、csdn.net、qq.com、liblib.art、tusi.art、cloud.tencent.com、jimeng.jianying.com 等）均返回 403 或 DNS 失败；唯一可读全文的一手材料来自 GitHub raw 文件（Fooocus / SAI / twri / diva 风格 JSON、Stability SDK README、Civitai 开源仓库、Midjourney 官方文档 2023–24 镜像、willwulfken 关键词参考、Krea2 风格手册、Reddit r/StableDiffusion 每日摘要仓库）。各路的共享搜索配额均在中途耗尽，若干计划中的补查未能执行。
- 因此：(1) 所有引用均为摘要层面，逐字引用的提示词已原样保留，但完整 prompt 文本与页面上下文未核对；(2) 不少来源是厂商博客、提示词站、聚合页、SEO 页面，可靠性一般，正文已逐条标注；(3) 2022–2024 的材料（SD1.5/SDXL 时代模型分类、妙鸭相机、通义万相首发版、混元旧风格表）可能已过时，正文以日期标注；(4) 凡无法落实到来源的内容一律标为【背景知识·未核实】或【推断】。

### 9.2 本报告框架本身的限制

- 六轴坐标系是本调研的归纳，没有任何单一文献同时提出这六条轴；刻度点是为离散分类人为设定的。
- F 轴（文化谱系）与 A–E 不正交；「composition / framing」（构图取景）、「面部特定维度」（眼睛写实度、特征夸张方式、皮肤处理）未纳入——uncanny valley 文献最接近，但关键论文未能核实。
- 「流行度」判断均基于文章标题与摘要中的「爆款 / 爆火 / 涨粉」措辞，无平台级统计数据支撑；LiblibAI / 吐司 / 海艺 / Civitai 当前热门榜单与下载量均未取得。
- 没有任何来源提供「3D 渲染 vs 照片 vs 2D 绘画」或「厚涂 vs 油画」的系统性判别指南；§6 的流程为综合推断。

### 9.3 值得后续核实的主要缺口（按优先级）

**理论与定义**
1. Zell, Aliaga, Jarabo, Zibrek, Mastilovic, McDonnell 2015 SIGGRAPH "To Stylize or not to Stylize? The Effect of Shape and Material Stylization on the Perception of Computer-Generated Faces"（shape realism × material realism 两轴）；MacDorman & Chattopadhyay 2016（写实度一致性比绝对写实度更重要）。
2. McCloud 原著第二章三顶点的精确命名与 "amplification through simplification"、"masking effect"。
3. Oppenlaender "A Taxonomy of Prompt Modifiers for Text-To-Image Generation"（arXiv 2204.13988 v3 / *Behaviour & Information Technology* 2023）六类的名称与定义。
4. CSD 的 LAION-Styles 标签构成；WikiArt 27 类；ArtBench-10 全部 10 类名；InstantStyle / StyleAligned / IP-Adapter 对 style 的措辞。
5. semi-realism、stylized realism、lineless、伪厚涂 的任何定义性来源；Proko / Schoolism / Ctrl+Paint 对 cel vs soft vs painterly 的教学定义。

**工业参考作品**
6. Spider-Verse 2019 SIGGRAPH/GDC 讲座（Dimian / Beveridge）中 Ben-Day dots、misregistration、no motion blur、Kirby krackle 的确认。
7. Guilty Gear Xrd GDC 2015 Vault 记录（vertex color 控制阈值、ILM 内线贴图、法线编辑）。
8. Fortiche 一手访谈（Pascal Charrue、Arnaud Delord；《The Art of Arcane》）；The Bad Guys、Wolfwalkers、Entergalactic 的 look development 访谈。
9. Pixar / Disney / Blizzard 关于 "believable not realistic" / "stylized realism" 的 SIGGRAPH/GDC 讲座。

**模型与平台（时效性最强）**
10. arena.ai "Photorealistic & Cinematic Imagery" 与 "3D Modeling" 分榜的实际排名。
11. Midjourney 官方文档当前版本：V8.2 是否存在、默认模型、`--sref / --sv / --oref / --p` 在 V8 的兼容表、`--style raw` 与 `--raw` 是否互为别名。
12. GPT Image 1.5 / gpt-image-2 是否消除黄色偏；其真人与公众人物政策；Nano Banana Pro 之后是否出现新的 3D 潮流。
13. FLUX.2 官方发布说明与提示词文档（Black Forest Labs 页面未能打开）；Flux 对艺术家名的实际响应。
14. 针对 `octane render / unreal engine 5 / trending on artstation / 8k` 在 SDXL、Flux、Midjourney V7+ 上有/无差异的受控 A/B 实验（本轮一个也没找到）。
15. 任何独立、方法透明的多模型人像写实盲测，以及油画/水彩质感的横向实测。
16. 中文平台（即梦、可灵、豆包、海艺、美图设计室、元宝、LiblibAI）当前 UI 风格面板的官方完整列表；妙鸭相机之后（2024–2026）AI写真市场现状；「氛围感」「高级感」的定义与典型参数。
17. 中国《互联网信息服务深度合成管理规定》《生成式人工智能服务管理暂行办法》及 2025 年 AI 生成内容标识办法对 AI写真的具体约束。

---

## 10. 主要来源索引（精选；完整逐条来源见 `research_notes/AI人像画风分类调研/` 下 7 份笔记）

**理论与学术框架**
- Scott McCloud, *Understanding Comics* (1993) — Wikipedia: Understanding Comics；EBSCO Research Starters；Kevin Brooks 2005 演示（SlideShare）
- Mori, MacDorman & Kageki, "The Uncanny Valley [From the Field]", *IEEE RAM* 19(2), 2012 — IEEE Xplore 6213238；IEEE Spectrum；Unity Glossary: Uncanny Valley；Trinity College Dublin TARA
- Kyprianidis, Collomosse, Wang & Isenberg, "State of the 'Art': A Taxonomy of Artistic Stylization Techniques", *IEEE TVCG* 19(5), 2013 — tobias.isenberg.cc；HAL hal-00781502
- Lansdown & Schofield, "Expressive Rendering", *IEEE CG&A* 1995 — sci.utah.edu
- Somepalli et al., "Measuring / Investigating Style Similarity in Diffusion Models", arXiv 2404.01292, ECCV 2024
- Liao et al., ArtBench-10, arXiv 2206.11404 (2022)
- StyleDrop, NeurIPS 2023, arXiv 2306.00983
- Oppenlaender, prompt modifier taxonomy, arXiv 2204.13988 / *BIT* 2023

**工业参考作品**
- Spider-Verse：befores & afters 2023-06-28；SIGGRAPH 2023 Talks（DOI 10.1145/3587421.3595413 / .3595456 / .3595463）；Dark Horizons
- Arcane：RedShark News；Dark Skies Film；80.lv Texturing in Arcane；UAL 学生博客
- Puss in Boots: The Last Wish：TheWrap；AWN（Mark Edwards；fairy tale illustration roots）；VFX Voice
- TMNT: Mutant Mayhem：befores & afters 2023-09-07（两篇）；Mikros Animation；Cinesite；Creative Bloq；SIGGRAPH "Oozing Hand Crafted 2D Illustration Into a 3D Ninja Turtle World"
- Wish：SideFX；Nimona：Creative Bloq（Ted Ty）
- Guilty Gear Xrd：GDC Vault 1022031；ggxrd.com Motomura 幻灯片；BlenderNation 2015-07-26
- 三渲二 / 卡通渲染：萌娘百科「卡通渲染」「三渲二」；wellstsai 技术概览
- MetaHuman / Enemies：Epic MetaHuman docs（Assets Overview）；Unreal Engine Tech Blog 2018-11-02；Unreal Engine Spotlight *Daughter of the Inner Stars*；PC Gamer（pure uncanny valley）；Puget Systems；Unity Blog / Game Developer / TechSpot / Dsogaming（GDC 2022）

**术语与社区分类**
- 萌娘百科：赛璐璐、平涂、厚涂、Template_talk:绘画、二次元；蓝铅笔；轻微课；知乎 p/500536943、p/139285596；AAT-Taiwan 300053368（厚塗 = impasto）；AIGC.cn 厚涂关键词
- 2.5D：Wikipedia 2.5D；Giant Bomb；Unity Manual；Novita AI；MATCHA；吐司 Tusi.Art；CSDN 139146436
- 韩漫：机核 GCORES 153920；Bilibili opus/337641994918252136；Tropedia: Manhwa；90 Day Korean
- Civitai 开源仓库：docs/resource-intent-primitive.md；src/server/schema/resource-intent.schema.ts；migration 20230210200501_add_iscategory_tag
- Stability AI stability-sdk README（`style_preset` 17 项）；Fooocus `sdxl_styles/*.json`（sai / fooocus / twri / diva / mre / marc_k3nt3l）；ComfyUI_MileHighStyler
- Midjourney：docs.midjourney.com（models；style；style-reference；Omni Reference）；twardoch 文档镜像；willwulfken MidJourney-Styles-and-Keywords-Reference；Midlibrary（llms.txt、Beginner's Guide、SREF deep-dive）；Aedelon midjourney-expert.md；prompt-to-asset SYNTHESIS.md
- Krea2 prompt book（johnatas-henrique/overdrive，2026）
- Recraft API: Styles / Appendix；Recraft Docs: Selecting a style；docs.comfy.org RecraftStyleV3*
- Adobe Firefly：helpx.adobe.com effects-for-generated-images；Adobe Community thread（2025-08）
- 中文平台：腾讯云混元风格列表（1729/105846；108992）；help.aliyun.com text-to-image；百度 AI 作画指南；即梦官网；可灵 docs-v2；LiblibAI / 吐司 / 海艺模型页；知乎 41 种 / 42 种 / 50+ 画风帖；苏米客即梦 4.0 速查表

**摄影写实与「AI 味」**
- Carat.im（85mm portrait；disposable camera；comic cover；webtoon）；Picassoia；Promptomania；Oakgen（golden hour；Polaroid 2026）；Higgsfield；Stockimg；Dropshot；Aiarty
- CineStill 官方 / Parallax Photographic；Wikipedia: Hyperrealism (visual arts)
- Flux chin / Fluxia：HF SkalskiP discussion #3；BudgetPixel "Who is Fluxia?"（2026-01）；Civarchive 1732024（Chin Fixer 2000）；Stable Diffusion Art 论坛；AIStudyNow（Klein 9B）；Replicate fofr/kontext-make-person-real
- GPT 黄偏：Freepik RGB scaling；Know Your Meme；PopularAI
- 识别指南：Sightengine；Skylum；Eyesift；IsItAI；Veritas arXiv 2508.21048
- 中国市场：36氪（妙鸭）；界面新闻；游民星空；美图证件照 App Store；Felo 港风 agent；什么值得买；数英 Nano Banana Pro 人像提示词；塔猴模板

**3D / 潮玩 / 手办**
- Flux LoRA：PromptLayer（live-3D；Claymation XC；Toonic 2.5D；castor 3D portrait）；HF renderartist/toyboxflux；TusiArt 768175383859374303（Chibi-Figure）/ 852511266923615983（PPMT）；Civarchive Z1.0；ModelsLab UE render
- 潮流：Tom's Guide；MonetizeAI；WION；Blavity（action figure）；Jang；Amar Ujala；Techjockey；DEV Community；Storyboard18；Sloyd；CyberLink 2025-12（Nano Banana 手办）；The Digital Librarian 2025-04-08（Pixar 化）
- 中文：知乎 p/43734357（潮玩盲盒教程）；知乎 p/1943739237913584104；博客园 19111963；搜狐 932837854；站酷 ZMTcxNDcyOA（Banana2 50 玩法）；可我AI；Vmake（Labubu）
- 真 3D：Krea 博客 2026；Meshy 对比页；Neural4D；droid.tools

**2D 体积 / 平面 / 媒材**
- 艺术家名争议：MIT Technology Review 2022-09-16 与 2022-12-16；Decrypt 150575；Hyperallergic（Rutkowski；16,000 名单）；Know Your Meme（ArtStation 抗议）；Gizmodo / Decrypt（DALL·E 3）；eWeek / Yahoo Tech（GPT-4o Ghibli）；The Decoder（SD3 opt-out）；RightsTech（Sam Yang）
- LoRA：Civitai #754435、#1461162（RBStyle）、#2311515（Visionarys）；civarchive #777325（Rough Paint）、#242763（Painted World）；HF Jonjew/RealisticComicbookStyle；Tensor.Art 842692258991013230（Graphic Noir）；ComfyUI.org 水墨 / 唐风工笔工作流；Tensor.Art 622213020292205951（inkColor）
- 平面：Aesthetics Wiki Ligne Claire；Comics Odyssey（Hergé）；Leaselab / tboake（Sin City）；shots.net / Branded Agency / art4d（Corporate Memphis）；Morphic / Media.io / Magic Hour（risograph）；PromptSpace / God of Prompt（sticker）；OpenArt / QuillBot / Stockimg（pixel）；Underwood Xie（flat vector sref）；Scenario Help（turnaround）
- 媒材：BudgetPixel（style/artist/medium）；TechDogs（MJ V7 impasto）；Magnific / Atlas Cloud / Switas / Dreamina / Cliprise（2026 模型综述）；CreateIO（gongbi）；Media.io（ink wash）；Wikipedia: Gongbi

**2026 模型版图**
- Thurrott / neurohive / designcompass（gpt-image-2）；datanorth / PCWorld（GPT Image 1.5）；Neowin / Google Cloud docs / Vercel（Nano Banana 2）；iThome / marigold.cz / BGR（Nano Banana Pro）；PureAI（Imagen 4）；Wikipedia: Flux；design-offset（FLUX.2）；docs.midjourney.com/docs/models（V8.1）；VidMuse（V8.2，未确认）；apiyi / mindstudio / 36kr / CapCut（Seedream 4.x–5.0）；comfyui-wiki / TechNode（HunyuanImage 3.0）；Analytics Vidhya（Qwen-Image-2.0）；NYU Shanghai RITS / comfyui-wiki / GIGAZINE（Z-Image）；VentureBeat（Kolors 2.0）；recraft.ai blog/docs（V4.1）；TechCrunch / The Decoder / Adobe Blog（Firefly Image 5）；docs.ideogram.ai；docs.leonardo.ai；docs.krea.ai；freepik.com docs；fal.ai / techsy / BenchmarkList（Artificial Analysis 快照）；arena.ai / lmarena.ai；DataLearner；insiderllm / promptzone（SDXL checkpoint）

---

*报告完。所有画风名、提示词与模型名保留英文原文以便直接粘贴；凡标注【背景知识·未核实】与【推断】的内容，引用前请自行核对。*
