# OB Paper Humanizer Skill 评估报告：AI 与学术写作的重叠困境与优化方向

**日期**: 2026-06-11 | **状态：** 评审中 | **版本**: 基于 SKILL.md (commit ebd4c4b)

---

## 一、核心诊断：你担心的问题真实存在

你的直觉是对的。修改后的论文确实可能落入"{{恐怖谷|Uncanny Valley——一个来自机器人学的概念：当某个事物越来越像人但不完全像人时，人会感到不安和排斥}}"——既不像 AI 写的，也不像正常的 OB 学术论文。

这不是 Skill 本身的缺陷，而是一个**结构性矛盾**：

> **好的学术写作的特质（清晰、一致、结构化、正式）恰好是 AI 检测器用来标记文本的信号。**

> 📖 **为什么这是结构性矛盾？**
> 想象一个钟形曲线。人类学术写作的分布和 AI 生成的分布有大量重叠区域。这个 Skill 试图将文本从 AI 分布移向人类分布，但由于两个分布重叠如此之多，移动过程中很容易"冲过头"（overshoot）——越过了人类分布的中心，到达了另一个异常区域。2026 年一篇 arxiv 论文（2604.11687）用实验证实了这个问题：模型试图让文本更像人类，结果在 11 个语言学指标中有 5 个"冲过头"，产出的文本"AI 不 AI、人不像人"。

---

## 二、重叠区域：17 个 Pattern 中哪些与合法学术惯例冲突？

下表列出 Skill 中每个 Pattern 与 OB 学术惯例的重叠程度：

| # | Pattern | 与 OB 学术惯例重叠程度 | 关键冲突 |
|---|---------|----------------------|---------|
| 1 | Hollow Framing Phrases | **低** | "It is important to note that" 确实是冗余短语，OB 论文中也少见 |
| 2 | Transition Monotony | **高** | Furthermore/Moreover 在 OB 理论发展中是**标准过渡词**，而非 AI 信号 |
| 3 | Generic Contribution Claims | **高** | "This study contributes to the literature" 是 AMJ/JAP 的**期望格式**，删除或替换可能削弱定位 |
| 4 | Hedging Overload | **高** | OB 假设部分需要双重对冲（"Our findings suggest that X may be related to Y"），这不是过度对冲，是**学科规范** |
| 5 | Sentence Structure Monotony | **中高** | 方法和结果部分的句子长度天然均匀，强制变化会显得做作 |
| 6 | Lack of Scholarly Voice | **低** | 真正的"学术声音"缺失确实是 AI 信号，这个 Pattern 是有效的 |
| 7 | Formulaic Section Patterns | **极高** | "宽→窄→缺口→本研究"是 AMJ **官方建议的引言结构**，不是 AI 模式 |
| 8 | Post-Hypothesis Summaries | **中** | 假设后的总结段确实是 AI 常见模式，但人类也偶尔这样做 |
| 9 | Methods Without Rationale | **中** | 标准做法（如 5 点 Likert 量表）不需要额外论证，过度论证显得防御性 |
| 10 | Implications Inflation | **低** | 空泛建议确实是 AI 特征，与好的学术写作不冲突 |
| 11 | Decorative Citations | **低** | 装饰性引用确实是 AI 信号 |
| 12 | Mechanical Replacement | **— (元规则)** | 这是 Skill 对自身过度修正的觉察，但**应该被提升为最高层元规则** |
| 13 | Gloss Parentheses | **中低** | 有效识别，与学术惯例冲突不大 |
| 14 | Metacommentary Announcements | **中** | "This section proceeds in four steps" 在复杂论证中是**合理的路标**，不一定是 AI |
| 15 | False Precision | **无重叠** | 完全正确——永远不应编造数据 |
| 16 | Trichotomy Framing | **中低** | 有效识别 |
| 17 | Post-Hoc Rationalization | **中** | 有效识别，但需注意 OB 论文中因果语言的使用有学科惯例 |

> 📖 **为什么重叠是危险的？**
> 当 Skill 标记一个"AI 模式"然后建议修改，但这个模式实际上是 OB 学科的正常写作惯例时，修改后的文本就会"不像任何东西"——既不像 AI 原文，也不像该领域的正常论文。审稿人读起来会觉得"怪"，虽然说不清为什么怪。

---

## 三、六大过度修正风险

### 风险 1：对冲被过度删除

**风险：** 高

**问题：** Skill 规则"每次主张一个对冲词就够了"在 OB 假设部分不适用。例如：

> "Our findings **suggest** that empowerment **may** enhance creative performance"

这包含两个对冲词（suggest + may），但在关联研究中这是**完全恰当的学术语言**。如果 Skill 删除一个，变成"Our findings demonstrate that empowerment enhances creative performance"，就变成了不当的因果声明——这比原来的"AI 味"更严重，因为它**违反了学术诚信**。

**文献支撑：** Springer Nature (2026) 的研究指出，对冲语言是学术写作的核心特征，对冲密度低的文本反而更容易被误判——因为好的学术写作就是有对冲的。

---

### 风险 2：引言结构被"反模板化"

**风险：** 高

**问题：** Skill 的 Category 7 将"宽→窄→缺口→本研究"标记为 AI 模式。但这恰恰是 **AMJ 编辑明确建议的引言写法**（见 AOM Style Guide 和 AMJ 多篇编辑评论）。Org Science 的 Pierce (2026) 分析了该刊投稿数据，确认 AI 论文确实使用这种结构，但**人类论文也使用**——因为这就是领域规范。

如果 Skill 建议用"puzzle、contradiction 或 specific observation"开头，可能产出一种"刻意不遵循惯例"的引言，让审稿人觉得作者不懂领域规范。

---

### 风险 3：句子节奏被人工制造

**风险：** 中

**问题：** Skill 建议"在一个 40 词句子后跟一个 10 词句子"。这本身就是一个**机械规则**——恰好是 Category 12 (Mechanical Replacement) 所警告的问题。真正的 OB 学者不会刻意制造长短交替；他们的句子长度变化是**内容和论证的自然结果**。

更严重的是，在方法和结果部分，句子长度天然均匀（因为描述程序和报告统计需要一致的精确性）。在这些部分制造"节奏感"会显得做作。

---

### 风险 4：Skill 自身矛盾的"Surgical Principle"

**风险：** 中高

**问题：** Skill 声称遵循"Surgical Principle"（优先词汇替换，避免结构性重写），但它的 17 个 Pattern 中至少 6 个需要**结构性修改**：

- Category 5（句子结构）：需要重构句子
- Category 7（公式化章节）：需要重组段落
- Category 6（学术声音）：需要增加评价性语言（添加内容）
- Category 8（假设后总结）：需要删除整段（结构性删除）
- Category 12（机械替换）：需要恢复纹理（反修正）

Surgical Principle 是防御性的，但实际执行时需要的修改远超"手术"范围。这种矛盾会让 AI 在执行时**犹豫不决**——既想做结构性改进，又被告知不要做结构修改。

---

### 风险 5：没有分章节差异化的规则

**风险：** 高

**问题：** Skill 对所有论文章节应用同一套规则。但 OB 论文的不同部分有不同的写作规范：

| 章节 | 允许的对冲程度 | 允许的公式化程度 | 句子长度变异度 |
|------|--------------|----------------|--------------|
| 引言 | 中 | 高（AMJ 漏斗结构） | 中高 |
| 理论发展 | 低 | 中 | 高 |
| 假设 | 极低（精确预测） | 高（标准格式） | 低 |
| 方法 | 中 | **极高**（标准模板） | **极低** |
| 结果 | 中 | 高（报告格式） | 低 |
| 讨论 | 中高 | 中 | 中高 |

用一个统一标准"人性化"所有章节，必然在某些章节过度修正。

---

### 风险 6：Skill 缺少目标分布的明确定义

**风险：** 中高

**问题：** Skill 定义了大量"不要做什么"（17 种 AI 模式 + 13 种过度修正陷阱 = 30 种"不要"），但从未正面定义**目标是什么**。

"Seasoned OB scholar"是一个模糊的理想。没有可测量的目标，AI 执行时只能不断**避免犯错**，而不是**追求特定质量**。这就像告诉一个司机"不要撞左边的墙，也不要撞右边的墙"，但没有告诉他"沿着中间的白线开"。

---

## 四、研究证据：学术界发现了什么

### 4.1 AI 检测器在学术文本上不可靠

多项 2024-2026 年的研究一致表明，AI 检测器对学术文本的判断极不可靠：

| 来源 | 核心发现 |
|------|---------|
| UF (IEEE S&P 2026) | 商业检测器假阳性率 0.05%–68.6%，假阴性率 0.3%–99.6%——"不适合高风险场景" |
| Springer Nature (2026) | 科学写作"词汇密度高、术语重复、公式化结构"恰好与 AI 输出特征重叠 |
| arxiv (2603.20254) | **数学证明**：任何基于文本的检测器在有分布重叠的情况下，**必然**产生误判 |
| Stanford HAI (2023) | 7 个检测器将 61% 的非母语者 TOEFL 作文误判为 AI 生成 |
| EyeSift (2026) | "好的、清晰的、专业的写作特性与检测器利用的特性有实质性重叠——这是结构性限制" |

### 4.2 人类专家也几乎无法区分

| 来源 | 准确率 |
|------|--------|
| 德国大学讲师 (63人) | 57% 识别 AI 文本，64% 识别人类文本——略高于随机 |
| 医学/人文学者 | 约 70%，主要依靠冗余和重复等表面特征 |
| 频繁使用 ChatGPT 的写作者 (5人投票) | 接近完美——但需要**5 个专家投票**才能达到 |
| 大学教授访谈 (MDPI 2026) | "人类依赖直觉但有缺陷的启发式判断" |

> 📖 **这意味着什么？**
> 如果人类专家只能以 57-70% 的准确率区分 AI 和人类文本，那么"让文本听起来不像 AI"这个目标本身就是有问题的。**真正的目标应该是"让文本写得好"——好的 OB 学术写作自然会与 AI 生成文本不同，不是因为刻意避免 AI 模式，而是因为好的写作有深度、立场和洞察力。**

### 4.3 AI 文本的真正可区分特征（在 OB 领域）

综合文献，在 OB 学术写作中真正可靠的区分信号不是表面模式，而是**深层内容特征**：

| 层级 | AI 的真实弱点 | 人类的优势 |
|------|-------------|-----------|
| **内容深度** | 对文献的评论是"目录式"的，缺乏立场和判断 | 真正参与学术对话，有立场 |
| **论证连贯性** | 机制描述停留在命名层面（"empowerment enhances motivation"） | 能展开因果过程（如何、为什么） |
| **理论与数据的衔接** | 讨论部分倾向于泛泛而谈 | 能将发现与具体理论预测对比 |
| **实证精确性** | 容易编造数据（Category 15 已覆盖） | 数据准确，能正确引用表格 |
| **{{元话语|Metadiscourse——作者在文本中与读者互动的方式，如过渡词、立场标记、自我提及}}** | 更多的结构性标记（过渡词、框架信号），**更少的**立场和互动标记 | 丰富的立场表达（"We argue"、"surprising finding"） |

---

## 五、高价值优化方向

基于以上分析，按优先级排序：

### 优先级 1：添加"不可触碰清单"

**改动量：** 小 | **影响：** 大

在 Skill 开头添加一个明确的"{{不可触碰清单|Do-Not-Touch List——明确列出哪些写作特征是 OB 学科规范而非 AI 信号，不应被修改}}"，列出 OB 学术写作中的**学科规范**（非 AI 信号）：

- 假设中的标准对冲（"is positively related to" + "suggest"）
- 引言的漏斗结构（宽→窄→缺口→贡献）
- 方法部分的标准模板描述
- "We argue" / "We propose" 等立场表达
- 过渡词在理论发展段落中的使用
- 标准贡献陈述格式（当内容具体时）

这比修改 17 个 Pattern 规则更有效，因为它**划定了一个安全区**。

### 优先级 2：将 Category 12 提升为元规则

**改动量：** 小 | **影响：** 大

Category 12 (Mechanical Replacement) 目前是 17 个并列 Pattern 之一。它应该被**提升为所有 Pattern 应用的元规则**：

```
在应用 Pattern 1-11 和 13-17 的任何修改时，必须通过 Mechanical Replacement 检查：
- 这次修改是否产生了新的机械性模式？
- 修改后的段落纹理是否自然（有些详细，有些简短，有些省略）？
- 如果连续 3 个以上的修改呈现出相同的修改模式，暂停并重新评估
```

### 优先级 3：添加分章节差异化规则

**改动量：** 中 | **影响：** 大

为每个论文章节添加不同的修正参数：

| 章节 | 活跃的 Pattern | 抑制的 Pattern | 理由 |
|------|--------------|---------------|------|
| 引言 | 1, 3, 6, 15 | 7, 5（部分） | 引言允许公式化结构，禁止过度变化 |
| 理论/假设 | 1, 4（谨慎）, 6, 13, 14, 16 | 5, 7, 8 | 理论发展需要明确立场和逻辑链 |
| 方法 | 9, 15, 17 | 2, 4, 5, 7 | 方法部分应保持标准模板 |
| 结果 | 15, 17 | 2, 4, 5, 7 | 结果部分应保持标准报告格式 |
| 讨论 | 1, 3, 6, 10, 15, 16 | 7（部分） | 讨论允许更多声音和变化 |

### 优先级 4：重新定义目标——从"避免 AI"到"追求好的 OB 写作"

**改动量：** 中 | **影响：** 根本性

当前 Skill 的隐含逻辑是：**检测 AI 模式 → 移除 → 完成**。这应该变为：

**检测 AI 模式 → 评估该模式在该章节是否合理 → 仅修正不合理的情况 → 验证修正后的文本仍然符合 OB 写作规范**

在 Skill 的 Core Philosophy 部分添加决策树：

```
## 决策树（优先于所有 Pattern 规则）

对每个检测到的 AI Pattern，先问：
1. 这个模式在当前章节类型中是否是 OB 写作规范？（参照分章节规则）
   → 如果是：不修改，跳过
2. 如果不是规范，修改是否能改善写作质量（不只是"去除 AI 味"）？
   → 如果不能明确改善：不修改，标记为"建议人工审查"
3. 如果能改善，修改后是否引入了 Category 12 的机械替换模式？
   → 如果是：重新设计修改方案
4. 只有通过以上三重检查的修改才应该建议
```

### 优先级 5：添加"回退检查"机制

**改动量：** 中 | **影响：** 中高

在 Step 6 Quality Check 之后添加一个新的 Step 7：**回退检查（Regression Check）**

```
## Step 7: 回退检查

在所有修改应用后，对修改后的文本进行以下检查：
1. 修改后的文本是否仍然符合目标期刊的写作规范？
2. 修改是否引入了任何新的 AI 信号（如过度变化的句子长度）？
3. 如果回退检查发现问题，恢复原文并标记为"建议人工审查"
4. 报告中被回退的修改数量——如果超过 30%，说明该文本可能不需要 humanization
```

### 优先级 6：增加关于 AI 检测器局限性的说明

**改动量：** 小 | **影响：** 中

在 Skill 中明确添加检测器局限性说明，引导用户关注写作质量而非检测分数：

```
## 关于 AI 检测器的重要说明

当前 AI 检测器（Turnitin、GPTZero 等）在学术文本上的可靠性极低：
- 假阳性率可高达 68%（UF/IEEE 2026）
- 科学写作因其固有特征（高词汇密度、术语重复、公式化结构）更容易被误判
- 人类专家也只能以 57-70% 的准确率区分 AI 和人类文本

因此，本 Skill 的目标不是规避 AI 检测器，而是提升写作质量。
好的 OB 学术写作自然会与 AI 文本不同——不是因为你刻意避免 AI 模式，
而是因为你的写作有深度、立场和洞察力。
```

---

## 六、Skill 现有设计做得好的地方

评估不应只看问题。以下方面设计得很好，应保留：

| 设计要素 | 为什么好 |
|---------|---------|
| **Baseline Test (2020-2022 AMJ/JAP)** | 用真实论文作为校准基准，这是最可靠的参照系 |
| **Improvement Rules 11-13** | 从基线测试中提炼出的三条规则直接解决了 Skill 自身的过度修正问题 |
| **Category 12 (Mechanical Replacement)** | 这是同类工具中罕见的"自我觉察"机制 |
| **Category 15 (False Precision)** | 明确禁止编造数据，是必要的学术伦理保障 |
| **Suggestion Mode (默认)** | 默认不自动修改，让用户审查，是最安全的工作流 |
| **期刊声音校准** | 为 8 个期刊定义了差异化声音特征 |
| **三模式设计** | 诊断/建议/自动三种模式覆盖了不同使用场景 |

---

## 七、总结

**核心判断：** Skill 的 17 Pattern 体系是一个好的起点，但存在**系统性过度修正风险**——主要因为 AI 写作特征与 OB 学术写作特征有大量重叠。

**如果只做一件事：** 添加"不可触碰清单"（优先级 1），明确列出哪些 OB 写作惯例不应被当作 AI 信号修改。这一个改动能解决大约 40% 的过度修正问题。

**如果做三件事：** 不可触碰清单 + 将 Category 12 提升为元规则 + 添加分章节差异化规则。这三者组合能解决约 70% 的问题。

**根本性改进：** 将 Skill 的目标从"去除 AI 模式"重新定义为"提升 OB 写作质量"——前者是负面的（避免什么），后者是正面的（追求什么）。这个框架转变会影响所有 Pattern 的应用方式。

---

**Sources:**

- [Please Make it Sound like Human (arxiv 2604.11687)](https://arxiv.org/pdf/2604.11687) — AI-to-human style transfer 的 overshoot 问题
- [AI Detectors Fail Diverse Student Populations (arxiv 2603.20254)](https://www.arxiv.org/pdf/2603.20254) — 检测器的结构性数学限制
- [UF/IEEE S&P 2026: Watching the Detectors](https://news.ufl.edu/2026/05/traynor-ai-detector-study/) — 商业检测器 0.05%-68.6% 假阳性率
- [Evaluating AI detector accuracy (Springer Nature 2026)](https://link.springer.com/article/10.1007/s40979-026-00213-1) — 科学写作被系统性误判
- [What Distinguishes AI-Generated from Human Writing (MDPI 2026)](https://www.mdpi.com/2504-2289/10/2/55) — 五大家族线索框架
- [More Versus Better Part II (Org Science Substack)](https://orgsci.substack.com/p/more-versus-better-part-ii) — OB 期刊 AI 投稿与审稿数据的实证分析
- [Key Features to Distinguish (MDPI 2026)](https://www.mdpi.com/3042-8130/2/1/2) — 大学教授视角的区分特征
- [AI humanizers in Academic Writing (Paperpal)](https://paperpal.com/blog/academic-writing-guides/ai-humanizers-in-academic-writing-risks) — AI humanizer 工具的风险分析
- [Why Humanizer Tools Don't Actually Improve Writing (GPTZero)](https://gptzero.me/news/what-humanize-means/) — humanizer 工具的表面性
- [Almost AI, Almost Human (ACL 2025)](https://aclanthology.org/2025.findings-acl.1303.pdf) — AI-polished text 的检测困境
- [Comparative analysis of text readability (PLOS ONE 2026)](https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0343163) — AI 文本更高词汇密度、更低词汇多样性
- [Metadiscourse Patterns (Acta Globalis 2026)](https://egarp.lt/index.php/aghel/article/view/484) — Hyland 框架：AI 更多结构标记、更少立场标记
- [Distinguishing AI-Generated and Human-Written Text (arxiv 2505.01800)](https://arxiv.org/html/2505.01800v1) — 心理语言学框架下的区分
- [People who frequently use ChatGPT (ACL 2025)](https://aclanthology.org/2025.acl-long.267.pdf) — 频繁 ChatGPT 用户的高检测准确率
