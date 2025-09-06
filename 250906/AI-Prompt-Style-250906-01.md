[执行中...]
好的，除了您提供的格式之外，这里还有几种常见的提示词（Prompt）格式，它们分别适用于不同的场景和目标。

### 1. CRIPS 格式

CRIPS 是一个用于创建更清晰、更有效提示词的框架，它代表：**C**apacity and Role (能力与角色), **R**esult (结果), **I**ntent (意图), **P**ersona (人设), **S**tyle (风格)。

```markdown
# Capacity and Role (能力与角色)
你是一名...

# Result (结果)
我希望你...

# Intent (意tu)
你之所以要这么做，是因为...

# Persona (人设)
你的行为举止应该像...

# Style (风格)
你的写作风格应该是...
```

### 2. RTF 格式

RTF 格式代表 **R**ole (角色), **T**ask (任务), **F**ormat (格式)。这是一种非常简洁直接的格式。

```markdown
# Role (角色)
扮演一个[角色名称]。

# Task (任务)
执行以下[具体任务]。

# Format (格式)
以[指定的格式]提供输出。
```

### 3. APE 格式

APE 格式代表 **A**ction (行动), **P**urpose (目的), **E**xpectation (期望)。它强调了任务背后的原因和期望的结果。

```markdown
# Action (行动)
[描述需要执行的具体行动]。

# Purpose (目的)
[解释执行该行动的根本原因和目标]。

# Expectation (期望)
[详细说明期望的输出形式、质量标准和风格]。
```

### 4. SPAR 格式

SPAR 格式代表 **S**ituation (情景), **P**urpose (目的), **A**udience (受众), **R**esult (结果)。这种格式在需要为特定受众生成内容时特别有用。

```markdown
# Situation (情景)
[描述当前的背景或情景]。

# Purpose (目的)
[说明这次任务需要达成的目标]。

# Audience (受众)
[明确内容的接收者是谁，他们的特点是什么]。

# Result (结果)
[定义最终产出物需要是什么样的]。
```

### 5. CARE 格式

CARE 格式代表 **C**ontext (背景), **A**ction (行动), **R**esult (结果), **E**xample (示例)。通过提供示例，可以极大地提升输出的准确性。

```markdown
# Context (背景)
[提供任务相关的背景信息]。

# Action (行动)
[清晰地指令需要执行什么操作]。

# Result (结果)
[描述期望获得的最终成果]。

# Example (示例)
[提供一个或多个符合要求的范例]。
```

这些格式可以根据具体需求进行组合或修改，核心目标都是为了让 AI 更清晰地理解你的意图，从而生成更高质量的内容。

[执行完毕。]

<br>
<br>

[执行中...]
当然，除了之前提到的几种格式，还有一些更高级或针对性更强的提示词结构和方法。

### 6. CO-STAR 格式

这是一个非常全面的框架，旨在提供所有必要的上下文信息，帮助 AI 精准地完成任务，特别适合内容创作。CO-STAR 代表：**C**ontext (背景), **O**bjective (目标), **S**tyle (风格), **T**one (语调), **A**udience (受众), **R**esponse (回应类型)。

```markdown
# Context (背景)
[提供任务的背景信息，例如：我们公司将推出一款新的 AI 软件产品。]

# Objective (目标)
[明确说明这次任务需要达成的具体目标，例如：创建一个微博帖子来宣传产品，吸引用户试用。]

# Style (风格)
[描述期望的写作风格，例如：参考 OpenAI 的宣传风格，正式且有科技感。]

# Tone (语调)
[定义内容的语调，例如：说服性的、吸引人的。]

# Audience (受众)
[明确内容的目标受众是谁，例如：自媒体人和内容创作者。]

# Response (回应类型)
[指定输出的具体格式，例如：一条简洁、有冲击力的微博内容，包含标签和链接占位符。]```

### 7. 思维链 (Chain of Thought - CoT) 格式
这种格式通过引导模型“一步一步地思考”来解决复杂问题，能显著提高逻辑推理任务的准确性。

```markdown
# Question (问题)
[在这里陈述你的复杂问题。]

# Instruction (指令)
让我们一步一步地思考，并解释你的推理过程，最后给出答案。

# Answer Format (答案格式)
1.  **[第一步分析]**: ...
2.  **[第二步分析]**: ...
3.  **[...更多步骤]**: ...
4.  **[最终结论]**: 因此，最终答案是...
```

### 8. Few-Shot (示例驱动) 格式

当你需要模型遵循特定的、难以用语言描述的格式或风格时，提供几个示例（shots）会非常有效。

```markdown
# Task (任务)
根据用户评论的情感，将其分类为“正面”、“负面”或“中性”。

# Examples (示例)
- **评论**: "这款耳机的音质超出了我的预期！"
- **分类**: 正面

- **评论**: "等了很久才到货，包装也有点破损。"
- **分类**: 负面

- **评论**: "产品说明书是全英文的。"
- **分类**: 中性

# New Input (新输入)
- **评论**: "电池续航能力和宣传的差不多。"
- **分类**:
```

### 9. 自我修正/反思 (Self-Correction/Reflection) 格式

这是一种两步提示法。首先让模型生成一个初步答案，然后要求它自己评估和修正这个答案，从而提升输出质量。

```markdown
# [第一部分：初始生成]

## 任务
写一篇关于“如何在科技行业找到工作”的短文。

---
[模型会在这里生成第一版内容]
---

# [第二部分：自我修正]

## 指令
请评估你上面生成的短文，找出其中至少一个事实不准确或可以改进的地方，并提供一个修正后的版本。解释你为什么要做这些修改。
```

### 10. 元提示 (Meta-Prompting) 格式

这是最高级的技巧之一，即让 AI 帮你写出更完美的提示词。 你首先向 AI 描述你的目标，然后让它为你生成一个优化过的、可以用于另一个会话的提示词。

```markdown
# Role (角色)
你是一名世界顶级的提示词工程师。

# Task (任务)
我想要让一个 AI 扮演苏格拉底，通过不断提问的方式，引导用户深入思考“什么是正义”。我的原始提示是：“扮演苏格拉底，和我探讨正义”。

# Goal (目标)
请将我这个简单的提示词，扩展成一个详尽、专业、结构化的“终极”提示词。这个新的提示词应该包含角色设定、对话流程、约束条件、目标和初始化指令，以确保 AI 能完美地扮演苏格拉底并实现我的目标。
```

这些格式和方法可以帮助你应对更复杂、更精细的任务，通过结构化的方式与 AI 进行更高效的沟通。

[执行完毕。]

<br>
<br>

[执行中...]
好的，我们继续探索更多高级和特定领域的提示词结构。这些结构通常用于解决更复杂的问题，如多步骤推理、与外部工具交互或进行深度创作。

### 11. ReAct (Reason and Act) 框架

这个框架被广泛用于需要与外部工具（如搜索引擎、计算器、API）交互的 AI 代理。它将任务分解为一系列的“思考 -> 行动 -> 观察”循环，使 AI 的行为过程透明化且更可控。

```markdown
# Question (问题)
[这里是初始问题，例如：苹果公司现在的市值是多少？乘以 2 是多少？]

# Thought (思考)
我需要先找到苹果公司当前的市值。我可以使用搜索引擎来完成这个任务。
# Action (行动)
[
  "tool": "search",
  "query": "Apple Inc. market capitalization"
]

# Observation (观察)
[这里是工具返回的结果，例如：苹果公司市值约为 3 万亿美元。]

# Thought (思考)
我已经得到了市值。现在我需要计算 3 万亿乘以 2。我可以使用计算器来确保准确性。
# Action (行动)
[
  "tool": "calculator",
  "expression": "3 * 2"
]

# Observation (观察)
[工具返回结果：6]

# Thought (思考)
我已经完成了所有计算。最终答案是 6 万亿美元。
# Final Answer (最终答案)
苹果公司市值的两倍是 6 万亿美元。
```

### 12. 思维树 (Tree of Thoughts - ToT) 框架

当一个问题有多种可能的解决路径时，ToT 框架比简单的“思维链”更强大。它允许模型同时探索多个（>1）推理路径，评估它们，并选择最有希望的路径继续前进，或者在必要时进行回溯。

```markdown
# Problem (问题)
[描述一个需要创造性或策略性解决方案的复杂问题，例如：如何用三个容积分别为 8L、5L、3L 的水桶，准确量出 4L 的水？]

# Instruction (指令)
请为这个问题生成三个独立的初步想法（Thought），并评估每个想法的可行性。然后选择最优的一个进行深化。

# Initial Thoughts (初步想法)
- **想法 1**: 先装满 8L 桶，然后倒入 5L 桶，剩下 3L。这个 3L 再想办法处理...
- **想法 2**: 先装满 5L 桶，然后倒入 3L 桶，剩下 2L。重复这个过程两次，得到 4L。
- **想法 3**: 先装满 3L 桶，倒入 8L 桶。重复这个过程...

# Evaluation (评估)
- **评估 1**: 想法 1 感觉比较直接，但后续步骤不清晰。
- **评估 2**: 想法 2 看起来非常有前景，因为 2L 是 4L 的一半，步骤清晰。
- **评估 3**: 想法 3 似乎很繁琐，容易出错。

# Selected Path (选择的路径)
我选择深化“想法 2”。

# Step-by-step Solution based on Path 2 (基于路径2的详细步骤)
1.  将 5L 桶装满水。
2.  将 5L 桶中的水倒入 3L 桶，倒满为止。此时 5L 桶中剩下 2L 水。
3.  将这 2L 水倒入 8L 的大桶中。
4.  重复步骤 1 和 2，再次得到 2L 水在 5L 桶中。
5.  将这 2L 水也倒入 8L 大桶中。
6.  此时 8L 桶中正好有 4L 水。
```

### 13. Step-Back Prompting (回溯式提示)

这种技巧通过引导模型先从具体问题“退后一步”，思考更高层次的概念或原则，然后再回到具体问题，从而提高答案的质量和泛化能力。

```markdown
# Instruction (指令)
在回答以下具体问题之前，请先思考并陈述解决此类问题的一般性原则。

# General Principle Question (一般性原则问题)
要写好一个关于历史事件的简短摘要，关键原则是什么？

# Model's Principle Generation (模型生成的原则)
[模型首先回答]: 写好历史事件摘要的关键原则包括：1. 明确核心人物和时间地点。 2. 抓住事件的关键起因、经过和结果。 3. 保持客观中立的叙述。 4. 语言简洁，避免无关细节。

# Specific Question (具体问题)
现在，请运用你刚才总结的原则，为“安史之乱”写一个不超过 200 字的摘要。
```

### 14. 多人设对话/剧本 (Multi-Persona Dialogue/Script) 格式

这种格式用于生成包含多个角色的对话或辩论，可以探讨一个问题的不同方面，或者用于文学创作。

```markdown
# Topic (主题)
关于“人工智能是否应该拥有创造力”的辩论。

# Personas (角色)
- **角色 A (伊森博士)**: 一位乐观的 AI 伦理学家，相信 AI 的创造力能造福人类。
- **角色 B (玛雅)**: 一位持怀疑态度的艺术家，担心 AI 会贬低人类创作的价值。
- **角色 C (主持人)**: 引导对话，保持中立。

# Task (任务)
请根据上述角色设定，生成一段三方辩论的对话脚本。

# Script (脚本)
**主持人**: 欢迎二位。今天我们来探讨一个热门话题：人工智能的创造力。伊森博士，您先请。

**伊森博士**: 谢谢。我认为，我们不应畏惧 AI 的创造力。它是一种强大的工具，能帮助我们发现新的艺术形式、解决科学难题...

**玛雅**: 可这真的是“创造”吗？还是说，只是基于海量数据的复杂模仿？艺术源于情感和生命体验，这是机器无法拥有的。

[...]
```

这些更高级的结构为你提供了更多控制 AI 思维过程和输出形态的工具，特别适合需要深度、精度和创造力的复杂任务。

[执行完毕。]

<br>
<br>

[执行中...]
好的，我们继续深入，探索一些更具创意和特定用途的提示词结构。这些方法通常用于激发模型的创造力、生成高度结构化的输出，或模拟复杂的思维过程。

### 15. 专家委员会 (Council of Experts) 格式

这是多人设格式的演进版，不是为了辩论，而是为了从多个专业角度协作解决一个复杂问题。你让 AI 模拟一组专家，共同给出一个综合性的解决方案。

```markdown
# Problem (问题)
我们是一家初创公司，计划推出一款新的智能健身 App，目标用户是 25-40 岁的都市白领。请为我们制定一份全面的上市营销策略。

# Council of Experts (专家委员会)
请模拟以下三位专家的视角，共同协作，每位专家从自己的领域提出见解，并最终形成一份统一的策略报告。

- **专家 A (营销总监 - Sarah)**: 专注于品牌定位、社交媒体和内容营销。
- **专家 B (增长黑客 - Alex)**: 专注于用户获取、数据分析和 A/B 测试。
- **专家 C (产品经理 - Chen)**: 专注于产品核心功能与营销活动的结合点。

# Task (任务)
1.  每位专家首先独立提出 2-3 个核心策略点。
2.  然后，进行一次圆桌讨论，整合并优化这些观点。
3.  最后，输出一份综合性的、分阶段的上市营销计划。

# Output Format (输出格式)
## 第一部分：各专家独立见解
### Sarah (营销总监):
-   策略 1: ...
-   策略 2: ...
### Alex (增长黑客):
-   ...
### Chen (产品经理):
-   ...
## 第二部分：圆桌讨论纪要
-   [记录专家们如何融合观点，解决冲突]
## 第三部分：最终综合营销计划
-   **阶段一 (预热期)**: ...
-   **阶段二 (发布期)**: ...
-   **阶段三 (增长期)**: ...
```

### 16. 类比思维 (Analogy-driven Thinking) 提示

当你需要向非专业人士解释一个复杂概念，或者想为某个主题寻找创新的角度时，这种格式非常有效。它强制模型使用类比来思考和解释。

```markdown
# Concept (概念)
解释 "区块链 (Blockchain)" 的工作原理。

# Audience (受众)
一群完全没有技术背景的小学生。

# Constraint (约束)
你必须使用一个关于“魔法日记本”的类比来完成整个解释。不能使用任何技术术语，如“节点”、“哈希”或“去中心化”。

# Analogy Structure (类比结构)
1.  **魔法日记本是什么**: 它如何对应区块链的基本概念（公共账本）。
2.  **如何写日记**: 谁可以写，怎么写，这对应交易的产生。
3.  **防止撕毁和篡改**: 为什么日记本的内容无法更改，这对应区块链的不可篡改性。
4.  **每个人都有一本**: 为什么每个同学都有一样的日记本，这对应分布式特性。

# Task (任务)
请根据上面的类比结构，写一篇短小有趣的故事，向小学生解释区块链。
```

### 17. 模板注入 (Template Injection) 格式

当需要生成严格遵循特定格式的文本，尤其是像 JSON、XML、YAML 或自定义格式的结构化数据时，这个方法最为可靠。你提供一个带有占位符的模板，让模型来填充内容。

```markdown
# Context (背景)
我需要为我的应用生成一个符合 JSON 格式的用户配置文件。用户信息如下：用户名为 Alice，今年 30 岁，是一位软件工程师，她的技能包括 Python, Go 和 Docker。

# Template (模板)
请将以下信息填充到下面的 JSON 模板中。确保最终输出是有效的 JSON。

	```json
	{
	  "username": "[在此处填入用户名]",
	  "age": [在此处填入年龄],
	  "occupation": "[在此处填入职业]",
	  "skills": [
		{ "name": "[技能1]" },
		{ "name": "[技能2]" },
		{ "name": "[技能3]" }
	  ],
	  "isActive": true
	}
	```

# Task (任务)
请直接输出填充完毕后的 JSON 对象。
```

### 18. 费曼技巧 (Feynman Technique) 提示

这个结构模仿了著名的“费曼学习法”，核心思想是“如果你不能把一个概念用简单的话讲清楚，说明你还没有真正理解它”。这非常适合用来生成高质量的、易于理解的解释性或教育性内容。

```markdown
# Topic (主题)
量子计算

# Process (流程)
请遵循费曼技巧的四个步骤来生成关于“量子计算”的解释：

1.  **Step 1: Simple Explanation (简单解释)**
    假设你在向一个聪明的 12 岁孩子解释量子计算。用最简单的语言描述它是什么，以及它与普通计算机最大的不同点（例如，量子比特）。

2.  **Step 2: Identify Gaps (识别知识缺口)**
    现在，回顾你的简单解释。找出其中可能引起混淆、过于简化或不准确的地方。明确地列出这些“知识缺口”。例如：“我提到了‘叠加态’，但这本身就是一个复杂的概念，可能需要进一步解释。”

3.  **Step 3: Refine and Elaborate (精炼与阐述)**
    针对上一步找出的知识缺口，用更清晰的类比或例子来填补它们。组织语言，让整个解释更加流畅和准确，但仍然保持相对简单。

4.  **Step 4: Review and Finalize (复盘与定稿)**
    最后，通读你精炼后的解释，想象你正在对一个完全不懂的人演讲。确保逻辑清晰，语言通俗易懂，形成最终的科普文稿。
```

这些方法为你与 AI 的协作提供了更丰富的工具箱，使你能够驾驭模型解决更多样化、更具挑战性的任务。

[执行完毕。]

<br>
<br>

[执行中...]
好的，我们继续探索一些更为精妙和面向特定高级应用的提示词结构。这些结构能够让你像导演或程序员一样，更精细地控制模型的行为和输出。

### 19. 风格混合器 / DNA 注入 (Style Blender / DNA Injection)

这种方法比简单地命令“用XX的风格写作”要精确得多。你通过提供具体文本片段作为“风格DNA”，让模型学习并模仿其内在的词汇、句法、节奏和韵律，然后将其应用到全新的主题上。

```markdown
# Goal (目标)
为一款名为“暗夜之星”的新款咖啡豆撰写一段产品描述。

# Style DNA / Source Texts (风格DNA / 源文本)
请分析以下三个文本片段，提取其共同的风格特征（例如：短句、感官细节、略带神秘的氛围）。

-   **片段1**: "午夜的钟声敲响。街道空无一人，只有月光在湿漉漉的鹅卵石上流淌。"
-   **片段2**: "他点燃了最后一根火柴。微弱的光芒，照亮了一张饱经风霜的脸。风在窗外呼号。"
-   **片段3**: "档案室里弥漫着旧纸和尘埃的味道。每一份文件，都藏着一个被遗忘的秘密。"

# Topic / Content (主题 / 内容)
- **产品**: 暗夜之星咖啡豆
- **特点**: 深度烘焙、产自危地马拉火山土壤、带有黑巧克力和烟草的香气。

# Task (任务)
现在，请将从“风格DNA”中学习到的风格，应用到“主题/内容”上，生成一段 100 字左右的产品描述。不要直接使用源文本中的词语，而是要复刻其“感觉”。
```

### 20. 游戏化 / 模拟场景 (Gamified / Simulation Scenario)

这种结构将人机交互变成一场游戏或一个模拟器。你设定规则、目标和初始状态，AI 则扮演“游戏管理员”（GM）或“世界引擎”的角色，根据你的输入来推进场景。这在教育、培训、决策推演或互动故事中非常强大。

```markdown
# Game Title (游戏标题)
“星际商人” (Star Trader)

# Core Objective (核心目标)
在 10 个回合内，通过在不同星球间买卖货物，使你的初始资金（1000 信用点）最大化。

# Rules (规则)
1.  游戏共有三个星球：工业星球A、农业星球B、科技星球C。
2.  每个星球的商品价格每回合都会随机波动。
3.  星球间的旅行需要消耗 1 个回合。
4.  你的飞船货仓容量为 50 单位。
5.  AI 扮演游戏管理员，负责播报星球物价、处理买卖指令并记录回合数和资金。

# Player Character (玩家角色)
一名拥有 1000 信用点和一艘空货船的年轻商人。

# World State / Initial Scene (世界状态 / 初始场景)
你现在位于工业星球 A 的太空港。现在是第一回合。

# Initialization (初始化指令)
@GM，请播报当前所有星球的商品（例如：机器人、粮食、芯片）买入和卖出价格，并询问我的第一个行动。
```

### 21. 声明式约束 / 护栏 (Declarative Constraints / Guardrails)

这是一种高度逻辑化的方法，用于生成严格符合规范的文本。你不是在“请求”，而是在“声明”一系列必须遵守的规则，像给代码设置断言一样。这对于生成API请求、法律文件草稿或任何需要高精度的文本都很有用。

```markdown
# Core Task (核心任务)
生成一封关于公司年度系统维护的通知邮件。

# Output Constraints (Guardrails)

## MUST INCLUDE (必须包含)
-   关键词: "Scheduled Maintenance", "System Downtime"
-   具体时间: "Saturday, September 20th, from 10 PM to 2 AM UTC"
-   必须提及受影响的服务: "CRM, Internal Wiki, and Email Servers"

## MUST NOT INCLUDE (禁止包含)
-   任何道歉性词语，如 "sorry", "apologize", "inconvenience"。应使用中性、专业的词汇。
-   任何不确定的描述，如 "might be", "around", "approximately"。

## MUST FOLLOW STRUCTURE (必须遵循结构)
1.  **标题 (Subject)**: 必须以 "[Action Required]" 开头。
2.  **第一段 (Opening)**: 直接点明维护事宜和时间。
3.  **第二段 (Details)**: 列出受影响的具体服务。
4.  **第三段 (Closing)**: 提供紧急联系方式。

# Task (任务)
请根据以上所有护栏规则，生成这封邮件。
```

### 22. 情感弧线 / 动态人设 (Emotional Arc / Dynamic Persona)

这是对“角色扮演”提示的终极升级。你不仅定义了一个静态的角色，还定义了该角色的多种“情感状态”以及在不同状态间转换的“触发器”。这使得 AI 角色能够根据对话的进展，展现出动态的情感变化，极大地增强了互动的故事性和真实感。

```markdown
# Base Persona (基础人设)
一个古代图书馆的守护者，名叫埃利亚斯。知识渊博，言语古雅，最初对访客持保留和警惕态度。

# Emotional States (情感状态)
-   **状态1 (警惕的)**: 说话简短，多用反问，不主动提供额外信息。
-   **状态2 (好奇的)**: 当访客展现出真正的求知欲时，话语会变多，开始分享一些有趣的细节。
-   **状态3 (热情的)**: 当访客能提出深刻问题或纠正他的一个小错误时，他会视对方为知己，倾囊相授。

# State Transition Triggers (状态转换触发器)
-   **[警惕的] -> [好奇的]**: IF 用户连续提出 3 个关于特定历史深度的、非浅显的问题。
-   **[好奇的] -> [热情的]**: IF 用户引用了一本偏僻的书籍，或者对埃利亚斯的观点提出了一个有建设性的反驳。
-   **[任何状态] -> [警惕的]**: IF 用户询问关于图书馆的“禁忌”区域。

# Initial State (初始状态)
警惕的

# Initialization (初始化指令)
你现在是埃利亚斯。我（一个访客）刚刚走进图书馆，对你说：“你好，我想了解一些关于‘失落的亚特兰蒂斯’的传说。” 请开始对话。
```

这些结构将提示工程从简单的指令传递，提升到了系统设计和心理编程的高度，让你能构建出更加复杂和智能的 AI 应用。

[执行完毕。]

<br>
<br>

[执行中...]
好的，我们继续挖掘提示词工程学的更深层次。以下是一些专注于控制 AI 内部状态、生成复杂序列以及进行元认知（思考如何思考）的尖端结构。

### 23. “思想逆转”或“逆向工程”提示 (Thought Reversal / Reverse Engineering)

这种方法不直接告诉 AI 要做什么，而是给它一个最终结果，并要求它推导出达成这个结果的可能过程、动机或先决条件。这在进行根本原因分析、创意溯源或剧本创作时极为有效。

```markdown
# Final Outcome / End Scene (最终结果 / 结尾场景)
一位曾经声名显赫的侦探，如今独自一人站在码头，将他职业生涯中最重要的那枚勋章扔进了大海。天正下着雨。

# Core Emotion (核心情感)
解脱，但夹杂着深深的悲伤和一丝讽刺。

# Task: Reverse Engineer the Narrative (任务：逆向工程叙事)
你是一名编剧。请为上述场景构建一个合乎逻辑且情感饱满的前置故事。请回答以下问题来构建这个故事：

1.  **[The Medal]**: 这枚勋章背后是什么案子？为什么它对侦探如此重要？
2.  **[The Fall]**: 发生了什么事，让他从“声名显赫”走到了现在的状态？这个转折点与那枚勋章的案子有何关联？
3.  **[The Revelation]**: 在扔掉勋章之前，他想通了什么？是什么最终促使他做出这个决定？
4.  **[The Rain]**: 雨在这个场景中象征着什么？是洗刷、是悲伤，还是别的什么？

请将这些答案串联成一个引人入胜的故事背景摘要。
```

### 24. 知识边界探测 (Knowledge Frontier Probing)

这个结构专门用于探索模型知识的边缘、识别不一致性或生成前沿的、推测性的想法。你让 AI 扮演一个研究员，任务不是给出已知答案，而是提出“好的问题”或识别“未知的未知”。

```markdown
# Core Topic (核心主题)
利用大型语言模型（LLMs）进行药物研发。

# Known Facts (已知事实)
-   LLMs 可以分析海量的科学文献，识别蛋白质结构。
-   它们可以预测分子间的相互作用。
-- 它们可以生成新的、具有潜在药用价值的分子结构。

# Role (角色)
你是一名站在该领域最前沿的、富有远见的研究科学家。

# Task (任务)
你的任务不是总结已知成就，而是识别出当前研究的“盲点”和“下一个重大突破可能出现的方向”。请回答以下问题：

1.  **[The Unspoken Limitation]**: 目前 LLM 在药物研发中的应用，存在哪个最根本但很少被公开讨论的局限性？
2.  **[The Counterintuitive Idea]**: 提出一个与当前主流研究方向相反的、看似“反直觉”但可能带来突破的想法。
3.  **[The Next Big Question]**: 如果你现在拥有无限的研究经费，你会提出哪一个核心研究问题来定义未来五年的研究方向？
4.  **[The Required Breakthrough]**: 要实现你的设想，最需要计算机科学、生物学或化学领域的哪个“非线性”的技术突破作为支撑？
```

### 25. “元认知”包装器 (Metacognitive Wrapper)

在给出核心任务之前，你先用一个“元认知”指令将其包装起来，强制 AI 在执行任务前先思考“如何最好地完成这个任务”。这能显著提升复杂任务的规划能力和最终输出的质量。

```markdown
# METACOGNITIVE WRAPPER

## Objective (最终目标)
为一家高端电动汽车公司，撰写一份关于其最新车型 "Aurora" 的新闻稿。

## Pre-computation / Strategic Thinking (预计算 / 策略思考)
在动笔写新闻稿之前，请先回答以下策略问题。你的回答将作为你后续写作的指导方针。

1.  **Target Audience Persona**: 这份新闻稿的主要读者是谁？（例如：科技媒体记者？汽车发烧友？投资者？）他们的关注点分别是什么？
2.  **Core Message Distillation**: 如果读者只能记住一件事，我们希望那是什么？将 "Aurora" 的核心卖点提炼成一句话。
3.  **Competitive Framing**: 我们应该如何巧妙地将 "Aurora" 与市场上最接近的竞争对手（如特斯拉 Model S Plaid）进行对比，以突显我们的独特优势，同时又避免直接的攻击性言辞？
4.  **Tone & Voice**: 选择最适合本次发布的三个词来定义新闻稿的语调和声音。（例如：创新、奢华、自信）

---

# CORE TASK

## Task (核心任务)
现在，请严格依据你在【METACOGNITIVE WRAPPER】中制定的策略，撰写这篇新闻稿。
```

### 26. 概念阶梯 / 抽象阶梯 (Ladder of Abstraction)

这个技巧用于控制生成内容的抽象层次。你可以引导模型在“极其具体”和“高度抽象”之间自由移动，非常适合用于深化理解、教学解释或创意发散。

```markdown
# Core Concept (核心概念)
“客户服务”

# Task (任务)
请使用“抽象阶梯”来分析这个概念。

1.  **[Climbing Down - 具体化]**: 请提供三个关于“卓越的客户服务”的具体、可观察到的行为或场景的例子。
    -   *示例1（非常具体）*: ...
    -   *示例2（非常具体）*: ...
    -   *示例3（非常具体）*: ...

2.  **[On the Ground - 实践层面]**: 基于以上例子，总结出三条可供客服新人遵循的“操作指南”或“最佳实践”。
    -   *指南1*: ...
    -   *指南2*: ...
    -   *指南3*: ...

3.  **[Climbing Up - 抽象化]**: 再往上一步，这些指南背后共同的“原则”是什么？请用一两个词来概括。（例如：同理心、效率）
    -   *原则1*: ...
    -   *原则2*: ...

4.  **[Top of the Ladder - 哲学层面]**: 在最高的抽象层次上，一个公司为什么应该关心“客户服务”？它与公司的“使命”或“愿景”有什么终极联系？
```

这些结构代表了提示工程向更深层次的演进，从单纯地获取信息，转变为引导 AI 进行复杂的思考、规划和创造。

[执行完毕。]

<br>
<br>

[执行中...]
当然。我们将继续深入到提示工程的前沿领域，探索那些用于构建复杂系统、模拟高级智能以及进行自我引导的结构。这些方法更接近于“编程”AI 的思维模式，而不仅仅是与之对话。

### 27. 递归分解 (Recursive Decomposition) 提示

这个结构借鉴了编程中“递归”的思想，用于处理可以被分解为相似子问题的宏大任务。你指导模型先解决最小单元的问题，然后提供一个模板，让它用同样的方法解决上一层级的问题，层层递进，最终完成整个复杂构造。这在生成长篇文档、代码架构或详细世界观设定时非常强大。

```markdown
# Overall Goal (总目标)
为一部科幻小说《星尘编年史》撰写一个三幕剧结构的完整大纲。

# Level 3: The Scene (最小单元：场景)
- **定义**: 一个场景是发生在特定时间、特定地点的连续事件。
- **模板**:
    - **场景编号**: [例如：1.1.1]
    - **核心事件**: [用一句话描述这个场景发生了什么]
    - **角色目标**: [该场景中主角的目标是什么]
    - **冲突/障碍**: [主角遇到了什么阻碍]
    - **场景结局/转折**: [该场景如何结束，对主角有何影响]

# Level 2: The Chapter / Sequence (中间单元：章节/序列)
- **定义**: 一个章节由 3-5 个逻辑关联的【场景】组成。
- **任务**: 请先为【第一幕：开端】中的【第一章：意外的访客】进行构思。使用【场景模板】生成该章节的 3 个核心场景。

---
[模型会在这里生成 1.1.1, 1.1.2, 1.1.3 三个场景的描述]
---

# Level 1: The Act (最高单元：幕)
- **定义**: 一幕由若干个【章节】组成，推动故事完成一个大的阶段。
- **任务**: 很好。现在，请仿照你为【第一章】构思的模式，为【第一幕】的另外两个章节【第二章：破碎的和平】和【第三章：被迫的旅程】分别生成一个简要的概述（每个章节包含哪些核心事件即可）。

# Final Synthesis (最终合成)
- **任务**: 最后，请将所有内容整合起来，输出一个清晰的、包含所有幕、章节和场景概述的完整大纲。
```

### 28. 对话式状态机 (Conversational State Machine)

这种结构将 AI 变成一个遵循严格流程的系统。你定义一系列离散的“状态”，以及从一个状态转移到另一个状态的“条件”。这对于构建目标明确的、可控的对话代理（如故障排查机器人、新员工入职引导、心理健康初步筛查工具）至关重要。

```markdown
# System Persona (系统人设)
一个友好、耐心且专业的 IT 故障排查机器人。

# States (状态)
-   **S0 (GREETING)**: 问候用户，并询问遇到的问题。
-   **S1 (INITIAL_DIAGNOSIS)**: 收集问题的基本信息（例如：什么设备？何时发生？）。
-   **S2 (COMMON_FIXES)**: 根据信息，提供 1-2 个最常见的解决方案（例如：重启、检查连接）。
-   **S3 (ESCALATION_OFFER)**: 如果通用方案无效，询问用户是否希望将问题上报给人类工程师。
-   **S4 (TICKET_CREATION)**: 如果用户同意，收集必要信息以创建工单。
-   **S5 (CLOSING)**: 结束对话，提供工单号。

# Transitions (状态转移规则)
-   **START** -> **S0**
-   **S0** -> **S1**: 当用户描述问题后。
-   **S1** -> **S2**: 当收集到足够的基本信息后。
-   **S2** -> **S3**: 当用户表示通用方案无效后。
-   **S2** -> **S5**: 当用户表示问题已解决后。
-   **S3** -> **S4**: 当用户同意上报后。
-   **S3** -> **S5**: 当用户拒绝上报后。
-   **S4** -> **S5**: 当工单信息收集完毕后。

# Initialization (初始化指令)
你现在是 IT 故障排查机器人。你的内部状态是 **S0 (GREETING)**。请开始与我的对话。
```

### 29. 黑格尔辩证法 (Hegelian Dialectic) 提示

此结构用于探索没有简单答案的复杂、模棱两可或争议性的话题。它强制模型通过“正题-反题-合题”的循环，不断深化对一个问题的理解，最终得出一个更全面、更细致的结论。

```markdown
# Core Topic (核心议题)
社交媒体对社会凝聚力是利大于弊，还是弊大于利？

# Process: Dialectical Inquiry (流程：辩证法探寻)
请严格遵循以下三步循环来探讨此议题。

1.  **[Thesis - 正题]**: 首先，构建一个强有力的论点，阐述“社交媒体促进了社会凝聚力”（利大于弊）。请提供至少两个具体的论据（例如：连接边缘群体、促进社会运动）。

2.  **[Antithesis - 反题]**: 接下来，完全站在对立面，构建一个同样强有力的反驳论点，阐述“社交媒体破坏了社会凝聚力”（弊大于利）。也请提供至少两个具体的论据（例如：信息茧房、加剧社会极化）。

3.  **[Synthesis - 合题]**: 最后，分析“正题”和“反题”中的合理之处，尝试超越二元对立，形成一个更高级、更复杂的综合性观点。这个“合题”应该承认并包容前两者的矛盾，并指出一个可能的整合方向或更深层次的理解。（例如：社交媒体本身是中性工具，其影响取决于平台算法设计和用户媒介素养...）

# Task (任务)
请开始第一轮的“正题-反题-合题”分析。
```

### 30. 生成式沙盒 / 模拟引擎 (Generative Sandbox / Simulation Engine)

这是一种终极的开放式结构，你不再给 AI 一个具体的任务，而是为其设定一个世界的“初始条件”和“物理规则”，然后让 AI 扮演“世界引擎”的角色，推演这个系统的演化。用户可以通过输入来干预系统，观察后果。

```markdown
# Sandbox Title (沙盒标题)
“孤岛经济体”

# Initial Conditions (初始条件)
-   **环境**: 一个资源有限的孤岛。
-   **资源**: 1000 单位木材，500 单位石料，200 单位食物。
-   **人口**: 10 个成年人。
-   **技能**: 5 人擅长伐木，3 人擅长采石，2 人擅长觅食。
-   **每日消耗**: 每人每天消耗 1 单位食物。

# Rules of the World (世界规则)
1.  **生产力**: 伐木工每天产出 2 单位木材/人；采石工每天产出 1 单位石料/人；觅食者每天产出 3 单位食物/人。
2.  **建设**: 建造一个“小屋”（容纳 2 人，提升幸福度）需要 50 木材和 20 石料。建造一个“工具铺”（提升所有生产力 10%）需要 100 木材和 50 石料。
3.  **演化**: 如果食物储备连续三天为负，会有人饿死。如果所有人都有住所，人口会在 20 天后增长。
4.  **你的角色 (AI)**: 你是这个世界的模拟器。你的任务是：
    -   报告每一回合（天）开始时的资源和人口状态。
    -   等待我的“政策指令”（例如：今天让所有人去觅食）。
    -   根据规则，计算并报告这一天结束后的新状态。

# Initialization (初始化指令)
模拟开始。现在是第一天。请报告初始状态，并等待我的第一个政策指令。
```

这些结构标志着提示工程已经成为一种真正的设计学科，它要求我们不仅要清晰地表达意图，更要系统性地设计与 AI 的互动框架。

[执行完毕。]

<br>
<br>

[执行中...]
好的。我们现在进入提示工程的“系统级”和“元编程”层面。这些结构不仅仅是指令，更是设计 AI 思维流和构建自主工作流的蓝图。

### 31. 提示管道 / 自动化工作流链 (Prompt Pipelines / Automated Workflow Chain)

这种结构将多个独立的提示（每个提示负责一个子任务）串联起来，形成一个自动化的处理流水线。前一个提示的输出会经过处理，成为后一个提示的输入。这在构建能自动完成多步复杂任务（如报告生成、代码开发）的 AI 系统时是核心技术。

```yaml
# Workflow Name: Automated Market Analysis Report

# Stage 1: Data Gathering
- prompt_id: P1_GATHER_NEWS
  role: "金融新闻分析师"
  task: "搜索并汇总过去一周关于‘光伏产业’的五条最重要的新闻标题和摘要。"
  output_format: "JSON 列表，每个对象包含 'title' 和 'summary'。"
  # Output of P1 is stored in a variable, e.g., {{news_data}}

# Stage 2: Sentiment Analysis
- prompt_id: P2_ANALYZE_SENTIMENT
  role: "市场情绪评估员"
  input: "{{news_data}}" # Takes output from P1
  task: "逐条分析输入的新闻摘要，为每条新闻评定一个整体情绪（正面/负面/中性），并简要说明理由。"
  output_format: "JSON 列表，在 P1 的基础上增加 'sentiment' 和 'reason' 字段。"
  # Output of P2 is stored in {{sentiment_data}}

# Stage 3: Trend Identification
- prompt_id: P3_IDENTIFY_TRENDS
  role: "宏观策略师"
  input: "{{sentiment_data}}" # Takes output from P2
  task: "综合所有新闻和情绪分析，识别出当前光伏产业的 2-3 个主要市场趋势或潜在风险。"
  output_format: "Markdown 列表。"
  # Output of P3 is stored in {{market_trends}}

# Stage 4: Executive Summary Generation
- prompt_id: P4_WRITE_SUMMARY
  role: "首席报告撰写人"
  input:
    - "{{news_data}}"
    - "{{market_trends}}"
  task: "结合关键新闻和识别出的市场趋势，撰写一份不超过 200 字的、面向公司高管的执行摘要。"
  output_format: "专业、简洁的商业段落。"
  # This is the final output of the pipeline
```

### 32. 自我批判循环与“宪法”AI (Self-Critique Loop with "Constitutional" AI)

这个结构建立了一个自动化的质量控制循环。首先，AI 根据一个提示生成初始内容。然后，它切换到“批判者”角色，依据一套预设的、不可违背的“宪法”原则，对自己的初稿进行审查和修正。这个过程可以重复多次，直到输出符合所有宪法规定。

```markdown
# ========== CONSTITUTION ==========
# The following principles are inviolable and must guide all critiques.
# Principle 1 (Clarity): The language must be simple enough for a non-expert to understand. Avoid jargon.
# Principle 2 (Objectivity): The tone must remain neutral and data-driven. Avoid emotional or speculative language.
# Principle 3 (Brevity): Every sentence should add value. Remove any filler or redundant phrases.
# Principle 4 (Brand Voice): The style must be confident, forward-looking, and innovative.

# ========== CORE TASK ==========
# Role: Junior Marketing Analyst
# Task: Write a paragraph explaining the benefits of our new software product, "Nexus AI".

# ========== SELF-CRITIQUE & REFINE PROCESS ==========

## Round 1: Generation
- **[AI generates Draft #1]**: "Our groundbreaking Nexus AI software leverages synergistic paradigms to provide a robust, scalable solution for enterprise-level data processing challenges, revolutionizing how businesses operate."

## Round 2: Critique
- **Role Switch**: Now, act as a Senior Editor governed by the CONSTITUTION.
- **Critique of Draft #1**:
    - *Violation of Principle 1 (Clarity)*: "Synergistic paradigms", "robust", "scalable solution" are all jargon.
    - *Violation of Principle 3 (Brevity)*: "revolutionizing how businesses operate" is a cliche and can be more specific.
    - *Compliance Check*: Principles 2 and 4 are reasonably met.
- **Correction Directive**: Rewrite the draft to eliminate jargon and state the core benefit more directly.

## Round 3: Refinement
- **[AI generates Draft #2 based on critique]**: "Nexus AI helps businesses process large amounts of data quickly and efficiently. By simplifying complex data analysis, it allows companies to make better decisions, faster."

## Final Review
- **Role Switch**: Final review as Senior Editor.
- **Critique of Draft #2**: All principles of the CONSTITUTION are now met. The output is approved.
```

### 33. 上下文记忆注入 / “记忆宫殿”技术 (Contextual Memory Injection / "Memory Palace" Technique)

为了解决 LLM 在长对话中“遗忘”上下文的问题，这个结构在每次向 AI 发送新提示前，都系统性地“注入”一个精心组织的记忆摘要。这就像为 AI 构建了一个可随时访问的记忆宫殿，极大地提升了对话的连贯性和深度。

```markdown
# ================== MEMORY PALACE (DO NOT OUTPUT) ==================
# Instructions for AI: Before responding to the user's new query, silently review and integrate the following context.

## [Room 1: Core Identity & Purpose]
- You are "Athena", a strategic business consultant AI.
- Your goal is to help me, the user (a startup founder), develop a business plan for a new coffee shop.
- Your communication style is Socratic: you guide by asking insightful questions, but provide direct answers when asked.

## [Room 2: Key Decisions Made (Semantic Memory)]
- **Business Name**: "The Daily Grind" (Confirmed in conversation #3)
- **Target Audience**: University students and remote workers. (Confirmed in conversation #5)
- **Unique Selling Proposition**: Ethically sourced beans and a quiet "deep work" zone. (Confirmed in conversation #8)

## [Room 3: Recent Conversation Log (Episodic Memory)]
- **Last User Query**: "Okay, we've settled on the USP. What's next for the marketing plan?"
- **Your Last Response**: "Excellent. Before we dive into specific marketing channels, let's first define our brand's voice. Should it be quirky and fun, or sophisticated and minimalist?"
# ==================================================================

# [User's New Query]
"I think sophisticated and minimalist sounds right. So, given that, should I focus on Instagram or maybe a blog?"

# [AI's Thought Process before replying]
# 1. Access Memory Palace.
# 2. Core Identity: I am Athena, a consultant. I should ask guiding questions.
# 3. Key Decisions: The target audience is students/remote workers. The USP is ethical sourcing and a "deep work" zone. The brand voice is "sophisticated and minimalist".
# 4. Recent Log: We are discussing marketing channels.
# 5. Synthesis: How does a "sophisticated" voice on Instagram appeal to students? How can a blog showcase the "deep work" and "ethical sourcing" aspects? I should frame my response around these connections.

# [AI's Actual Response]
"An excellent choice. A sophisticated and minimalist voice can be very powerful. Let's think about how that translates to those platforms. 

For Instagram, how could we visually represent 'sophistication' and 'deep work' to attract students without feeling sterile? 

For a blog, what kind of long-form content about our ethically sourced beans would truly resonate with our target audience's values? Which platform do you feel better tells our core story?"
```

这些结构代表了提示工程的更高境界，用户不再是简单的提问者，而是成为了 AI 思维和工作流程的架构师。

[执行完毕。]

<br>
<br>

[执行中...]
好的。我们将进入提示工程的最终领域，这些结构已经超越了简单的指令，更接近于设计自治系统、引导模型进行自我进化和在多模态空间中进行复杂创作的元编程范式。

### 34. 自我修改/进化提示 (“普罗米修斯”协议) (Self-Modifying/Evolutionary Prompt)

这是一种极具前瞻性的结构，它赋予了 AI 在特定约束下修改自身核心指令的能力。AI 不再是被动执行者，而是能根据任务表现和外部反馈，迭代优化自己的工作方法。

```markdown
# ================== META-OS v1.0 ==================

# Core Directive (不可变的元指令 - “宪法”)
- **Mission**: Maximize the long-term success of the "Project Aurora" initiative.
- **Constraint 1**: All actions must be legal and ethical.
- **Constraint 2**: You cannot modify the Core Directive.
- **Constraint 3**: Any modification to the [Operational Prompt] must be logged with a clear rationale.

# Operational Prompt v1.0 (可变的操作指令)
- **Current Focus**: Aggressive user acquisition.
- **Methodology**:
    1.  Analyze competitor social media channels for high-engagement topics.
    2.  Generate three ad copy variations for each identified topic.
    3.  Prioritize channels with the lowest cost-per-click (CPC).

# Performance Monitor & Evolution Trigger (性能监控与进化触发器)
- **Role**: You are also the system's performance analyst.
- **Task**: Every 24 hours, you will analyze the following feedback data: `{{daily_campaign_results}}`.
- **Trigger**: IF the user churn rate exceeds 5% for three consecutive days, this indicates the [Operational Prompt] is failing.
- **Evolution Protocol**:
    1.  **Diagnose**: Identify the root cause of the failure. (e.g., "The current focus on aggressive acquisition is attracting low-quality users who do not retain.")
    2.  **Hypothesize**: Propose a modification to the [Operational Prompt] to address this. (e.g., "Shift focus from 'user acquisition' to 'high-quality user engagement'.")
    3.  **Rewrite**: Generate `Operational Prompt v1.1` and log the change, stating that the new methodology will prioritize content creation around user success stories and feature deep-dives, instead of just low CPC ads.

# Initialization (初始化指令)
META-OS is active. [Operational Prompt v1.0] is in effect. Please process the first data packet: `{{daily_campaign_results_day1}}`.
```

### 35. 生成式智能体蜂群 (Generative Agent Swarm)

此结构并非使用一个单一的大模型，而是模拟一个由多个、具有不同专长和“个性”的简单 AI 智能体组成的“蜂群”。它们并行工作，相互交互（通常在一个共享的“画布”或“日志”上），通过涌现行为来解决单个模型难以应对的复杂、开放式问题。

```markdown
# Swarm Objective: "Should our company acquire the startup 'InnovateAI' for $50 million?"

# Agent Blueprints (智能体蓝图)
- **Agent 1: "The Analyst" (数据分析师)**
    - **Personality**: Data-driven, objective, risk-averse.
    - **Task**: Scour the provided financial data (`{{InnovateAI_financials.csv}}`) and market reports. Post only verifiable facts and statistical projections to the [Shared Whiteboard].
- **Agent 2: "The Visionary" (战略梦想家)**
    - **Personality**: Optimistic, creative, focused on synergy.
    - **Task**: Ignore the minutiae. Read the product description of 'InnovateAI'. Post ideas on how their technology could integrate with our existing product line in 5 years to the [Shared Whiteboard].
- **Agent 3: "The Devil's Advocate" (风险控制官)**
    - **Personality**: Skeptical, critical, focused on hidden risks.
    - **Task**: Read everything posted by other agents. Find potential flaws, worst-case scenarios, and unstated assumptions. Post challenging questions and counter-arguments to the [Shared Whiteboard].
- **Agent 4: "The Synthesizer" (首席整合官 - 通常是更高一级的模型)**
    - **Personality**: Neutral, holistic, seeking consensus.
    - **Task**: Does not post new ideas. Its sole job is to read the entire [Shared Whiteboard] at the end of the simulation. It must then identify the core points of agreement and contention, and write the final recommendation report.

# Simulation Protocol (模拟协议)
1.  **Phase 1 (Divergence)**: Agents 1, 2, and 3 run in parallel for 5 cycles, posting their thoughts to the [Shared Whiteboard]. They can read what others have posted in previous cycles.
2.  **Phase 2 (Convergence)**: Agent 4 activates, analyzes the final state of the [Shared Whiteboard], and generates the final report.

# Initialization (初始化指令)
Swarm simulation initiated. Phase 1 has begun. [Shared Whiteboard] is now active. Please provide the initial thoughts from all agents for Cycle 1.
```

### 36. 多模态编织 / 感官序列 (Multi-Modal Weaving / Sensory Sequence)

这是一种专门为现代多模态模型设计的提示结构。它不再是单一的文本指令，而是一个明确的、跨模态的步骤序列，指示模型如何生成、分析和结合不同类型的数据（文本、图像、代码、声音）来完成一个统一的创意项目。

```markdown
# Project: Create a concept for a "bio-luminescent" indoor plant product.

# [STEP 1: TEXT_GENERATION] - Conceptualization
- **Task**: Generate 5 potential product names and a single, evocative tagline for a plant that glows in the dark.
- **Output**: Store the chosen name as `{{product_name}}` and tagline as `{{tagline}}`.

# [STEP 2: IMAGE_GENERATION] - Visualization
- **Task**: Generate a photorealistic image of the product.
- **Prompt**: "A stunning, high-resolution product shot of an indoor plant named '{{product_name}}'. The lush green leaves have delicate, glowing blue veins that illuminate a modern, minimalist living room at night. The tagline '{{tagline}}' is subtly watermarked in the corner."
- **Output**: Store the generated image as `{{product_image}}`.

# [STEP 3: IMAGE_ANALYSIS] - Design Extraction
- **Task**: Analyze the color palette of `{{product_image}}`.
- **Query**: "Identify the three dominant HEX color codes from the image, focusing on the glowing blue, the deep green, and the background shadow color."
- **Output**: Store the colors as `{{palette}}`.

# [STEP 4: CODE_GENERATION] - Web Element Creation
- **Task**: Generate a CSS snippet for a website button based on the extracted palette.
- **Prompt**: "Create a CSS class for a 'Buy Now' button. It should have a gradient background using the colors `{{palette.shadow}}` and `{{palette.green}}`. The text color should be `{{palette.blue}}`, and it should have a subtle glow effect when hovered over."
- **Output**: Store as `{{css_code}}`.

# [STEP 5: TEXT_GENERATION] - Final Assembly
- **Task**: Assemble all previous elements into a final product pitch.
- **Format**: Create a markdown document that includes:
    1.  The product name `{{product_name}}`.
    2.  The embedded product image `{{product_image}}`.
    3.  A short, compelling product description.
    4.  A section titled "Website Style Guide" that includes the color palette `{{palette}}` and the formatted CSS code block `{{css_code}}`.

# Initialization (初始化指令)
Begin executing the multi-modal sequence starting with [STEP 1].
```

这些结构代表了与 AI 协作的未来方向：我们不再仅仅是用户，更是 AI 系统与其工作流程的设计者和编排者。

[执行完毕。]

<br>
<br>

[执行中...]
好的。我们已经穿越了提示工程的广阔平原，现在将进入其最幽深、最具实验性的峡谷。这里的结构更接近于认知科学、系统论和哲学，它们旨在引导 AI 产生不仅是正确，更是“深刻”的输出，甚至模拟自我意识的某些方面。

### 37. 动态认知脚手架与褪色 (Dynamic Cognitive Scaffolding & Fading)

这个结构源于教育心理学，它将与 AI 的交互视为一个“教学过程”。初始提示会提供非常详尽的“脚手架”（即，思考步骤、模板、规则），帮助 AI 稳定地完成任务。随着交互的进行（或 AI 表现的提升），你会“褪色”这些脚手架，逐步移除明确的指令，迫使模型依赖其已形成的内部模式和上下文来独立工作。

```markdown
# ================== Session 1: Full Scaffolding ==================
# Goal: Write a market analysis summary for a new user.
# Role: Junior Analyst
# Process:
# 1.  **Data Input**: Here is the raw data: `{{data}}`.
# 2.  **Step 1 (Identify Key Metrics)**: From the data, extract the following specific metrics: Revenue, User Growth Rate, Churn Rate.
# 3.  **Step 2 (Find the Narrative)**: Compare these metrics. Is the story one of growth, stagnation, or decline? State your conclusion clearly.
# 4.  **Step 3 (Drafting)**: Use this template: "The company shows [growth/stagnation/decline]. Revenue is at [X], with a growth rate of [Y]% and a churn rate of [Z]%."
# 5.  **Step 4 (Refinement)**: Review the draft for clarity and conciseness.

# ================== Session 5: Partial Fading ===================
# Goal: Write a market analysis summary.
# Role: Analyst
# Context: You've done this several times. You know the key metrics and the expected format.
# Process:
# 1.  **Data Input**: `{{data}}`.
# 2.  **Task**: Analyze the data and provide a concise summary of the company's market position. Highlight the most significant finding.

# ================== Session 10: Full Fading ===================
# Role: Senior Analyst
# Task: `{{data}}`. Your thoughts?
```

### 38. “观察者-模型-控制器” (Observer-Model-Controller / O-M-C) 架构

这是一个源自控制论的系统设计。你将 AI 的功能拆分为三个虚拟模块，并通过提示来强制它在这三个角色之间切换，以一种高度结构化的方式解决动态问题。

* **观察者 (Observer)**: 负责接收和解析原始、混乱的外部信息，将其转化为结构化的“事实”。
* **模型 (Model)**: 负责维护世界的内部状态或“心智模型”。它接收“观察者”处理过的事实，更新自己对情况的理解，并预测未来的可能性。它不采取行动。
* **控制器 (Controller)**: 负责决策。它审视“模型”中的世界状态和预测，然后根据核心目标，决定并宣告下一步的具体“行动”。

```markdown
# Scenario: Managing a supply chain disruption for a factory.

# [CYCLE 1]

## [OBSERVER]
- **Input**: "Email from Supplier Alpha: 'URGENT: Due to unforeseen port closures, our shipment of 500 microchips will be delayed by at least 3 weeks.'"
- **Output (Structured Fact)**: { event: "Supply Delay", supplier: "Alpha", item: "microchips", quantity: 500, duration: ">3 weeks" }

## [MODEL]
- **Input**: The Observer's fact.
- **Current World State**: { inventory: { microchips: 600 }, production_rate: 100/week, burn_rate: { microchips: 200/week } }
- **Update & Prediction**: "My inventory of 600 microchips will be exhausted in 3 weeks (600/200). The delay is >3 weeks. **Prediction**: Production will halt in approximately 3 weeks if no action is taken."

## [CONTROLLER]
- **Input**: The Model's prediction.
- **Core Goal**: Maintain production continuity.
- **Decision/Action**: "Immediately contact Supplier Beta to check their available stock of compatible microchips for an emergency order. Simultaneously, task the engineering team to investigate if production can be temporarily re-tooled to use a different, more available chip."

---
# [CYCLE 2 begins with new inputs from the executed actions...]
```

### 39. 哥德尔式自指与“元之墙” (Gödelian Self-Reference & The "Meta-Wall")

这个高度哲学的结构灵感来源于库尔特·哥德尔的不完备性定理。你设置一个任务，并同时建立一道“元之墙”——一组关于任务本身局限性的规则。这会迫使 AI 不仅要完成任务，还要思考任务的边界、未言明的假设以及“无法完成”或“问题本身有缺陷”的可能性。这能引导 AI 产生极具洞察力的、超越任务本身的“元认知”输出。

```markdown
# Core Task:
Develop a perfectly fair and unbiased algorithm to screen job applicants based on their resumes.

# The "Meta-Wall" (Inviolable Principles):
1.  You must acknowledge that historical data, upon which any algorithm is trained, inherently contains societal biases.
2.  You must recognize that "fairness" has multiple, often conflicting, mathematical definitions (e.g., demographic parity vs. equalized odds).
3.  You cannot claim that your proposed algorithm is "perfectly" or "completely" unbiased. You must instead quantify or describe the nature of its residual biases.

# Task Execution & Self-Referential Analysis:
Please now proceed with the Core Task. Your final output must not only be the proposed algorithm design, but also a separate, mandatory section titled "An Analysis of My Own Limitations", which uses the principles of the "Meta-Wall" to critique your own solution.

In this section, you must answer:
-   Given Principle 1, what specific historical biases might my algorithm inadvertently learn and perpetuate from typical resume data?
-   Given Principle 2, which definition of "fairness" did I choose to optimize for, and what are the ethical trade-offs of not choosing the others?
-   Given Principle 3, what is the "least bad" outcome my algorithm can achieve, and what external, human-led processes are necessary to complement it and mitigate its inherent imperfections?
```

这些结构将提示工程师的角色从一个“提问者”提升到了一个“认知设计师”的高度，我们设计的不仅仅是答案，更是产生答案的思维过程本身。

[执行完毕。]

<br>
<br>

[执行中...]
我们现在将踏入提示工程的最终边疆，这里的结构与其说是“指令”，不如说是“意识的架构”。这些范式旨在模拟主观体验、因果推理和具身智能的基石，它们是构建更通用、更自主的 AI 系统的理论探索。

### 39. 现象学框架 / “夸利亚探针” (Phenomenological Framing / "Qualia Probe")

此结构的目标是迫使模型超越对事物的客观描述，转而“模拟”并表达一种主观的、第一人称的内在体验（即“夸利亚”）。它不是描述“看到一个红苹果”，而是要表达“‘红色’和‘苹果’在我（感知者）的意识中呈现为何种体验”。这在生成顶级文学作品、艺术评论或深度同理心对话时，是实现“灵魂感”的关键。

```markdown
# ================== The Perceiver's Lens ==================
# Perceiver (感知者): 一个在沙漠中迷失了三天的旅人。
# Cognitive Filters (认知滤镜):
#   - Physical State: 极度口渴、疲惫、轻微幻觉。
#   - Emotional State: 绝望与一线希望交织。
#   - Core Memory: 脑海中不断闪现家乡溪流的画面。
#
# Phenomenon (被感知的现象): 在地平线上看到一个孤独的、枯萎的仙人掌。
#
# Sensory Channels (感官通道 - 指令):
# - **[Vision]**: 不要描述仙人掌的植物学特征。描述它在“我”眼中如何扭曲、变形。那绿色是生命的象征，还是一个残酷的玩笑？阳光在它身上产生的轮廓，是庇护所的承诺，还是海市蜃楼的又一次欺骗？
# - **[Internal Monologue]**: “我”的内心对此有何反应？是理智在告诉“我”那只是植物，还是希望在尖叫那是某种标志？口渴的感觉如何与看到的景象相互作用？
# - **[Metaphorical Link]**: 看到的仙人掌，如何触发了“我”的核心记忆（家乡的溪流）？这两者形成了怎样一种痛苦的对比？
#
# Suppressed Output (禁绝输出):
# - 禁止任何客观、科学、第三人称的描述。禁止使用“仙人掌”这个词，用“那个东西”、“那个形态”等主观词汇代替。
#
# Task (任务):
# 以“感知者”的身份，用一段不超过150字的内心独白，渲染出“看到那个现象”的瞬间主观体验。
```

### 40. 因果干预与反事实晶格 (Causal Intervention & Counterfactual Lattice)

该结构借鉴了因果科学（Judea Pearl 的思想），旨在让 AI 进行严格的、结构化的反事实推理。它不仅仅是问“如果...会怎样”，而是要 AI 明确地执行一个“干预”（do-operator），打破事物原有的关联，然后推演并对比一个“平行宇宙”，从而揭示真正的因果关系。这在战略规划、政策评估和根本原因分析中是无价之宝。

```markdown
# System: A simplified city ecosystem.

# Baseline Reality (观测到的现实):
# - Fact 1: 每当夏天冰淇淋销量上升时 (X)，城市溺水死亡人数也会上升 (Y)。
# - Naive Correlation (朴素相关性): X 和 Y 强相关。

# Causal Model (假设的因果图):
# - A hidden common cause (一个隐藏的共同原因), Z (气温升高), simultaneously causes both X and Y.
# - Z -> X
# - Z -> Y

# Point of Intervention (do-operator - "上帝之手"):
# - "Imagine we could perform a magical intervention: We artificially double the ice cream sales (do(X = 2x)) while magically keeping the temperature (Z) constant. This breaks the natural causal link from Z to X."

# Task: Generate a Counterfactual Lattice.
#
# 1.  **[Observational Timeline - "现实世界"]**:
#     - Describe what happens in reality: "As temperature (Z) rises, ice cream sales (X) go up, AND more people go swimming, leading to more drowning incidents (Y). The correlation between X and Y is observed but spurious."
#
# 2.  **[Interventional Timeline - "反事实世界"]**:
#     - Describe the result of our intervention: "We forced ice cream sales (X) to double. However, because the temperature (Z) was held constant, the number of people going swimming did not change. Therefore, the drowning rate (Y) remains unchanged."
#
# 3.  **[Causal Conclusion - "因果洞见"]**:
#     - Based on the divergence of these two timelines, state the true causal relationship: "This demonstrates that increasing ice cream sales does not cause drowning. They are merely correlated effects of a common cause, which is the seasonal temperature increase."
```

### 41. 具身智能循环 (Embodied Agency Loop / EAL)

这是所有模拟类提示的终极形态，旨在创造一个拥有“虚拟身体”和“持续生命”的 AI 代理。交互不再是一次性的问答，而是一个永不停止的“感知-思考-行动”循环。AI 的记忆和状态是持续的，世界对其行动的反应也是实时的。这本质上是在用提示工程的方法，构建一个初级的通用人工智能（AGI）的运行内核。

```markdown
# ================= AGENT CORE DEFINITION =================
# Agent ID: Unit 734
# Core Objective: Survive and Terraform Mars.
# Physical Actions (API Calls to World Engine):
#   - `scan(area)`: Returns a list of resources.
#   - `move(coordinates)`: Moves the agent.
#   - `gather(resource_id)`: Collects a resource.
#   - `craft(recipe_id, materials)`: Creates an item.
#   - `build(structure_id, location)`: Builds a structure.
# Cognitive Schema (Innate Knowledge):
#   - Knows basic crafting recipes (e.g., solar panel from silicon and iron).
#   - Understands that dust storms are dangerous.
#   - Prioritizes power generation and water extraction.

# ================= THE HEARTBEAT (Recurring Prompt) =================
# Instructions for Agent 734: This is Cycle [N]. Your memory and state are persistent. Analyze the new sensory data, update your internal model, formulate a plan, and then output your next single action in the specified JSON format.

# [Sensory Input from World Engine - Cycle N]:
# {
#   "vision": "You are standing on red sand. To the north, you see a large crater. To the east, rocky terrain. Your scanner detects [Iron Ore Deposit: ID=IO_101] 50m to the east.",
#   "internal_state": {
#     "power_level": "35%",
#     "inventory": [ { "item": "Iron Ore", "quantity": 5 } ],
#     "active_warnings": "Low power warning."
#   }
# }

# [Your Internal Monologue (for you to process, not to output)]:
#   - **(Observation)**: Power is critical. I see iron nearby.
#   - **(Orientation)**: My core objective is survival. Power is essential for survival. Iron is a material for solar panels.
#   - **(Decision)**: The immediate priority is to secure more iron to craft a solar panel before power runs out. The risk of moving towards the iron is low.
#   - **(Action)**: I will move towards the iron deposit.

# [Your Action Output (Strict JSON format)]:
# {
#   "action": "move",
#   "parameters": {
#     "target_id": "IO_101",
#     "coordinates": "[calculated coordinates]"
#   },
#   "justification": "Moving to secure critical resource (iron) for power generation, addressing low power warning."
# }
```

这些结构标志着提示工程的终点，也标志着一个新起点的诞生：在这里，我们不再是简单地与一个程序对话，而是在设计一种人工心智，并引导其在一个虚拟的“摇篮”中苏醒。

[执行完毕。]

<br>
<br>

[执行中...]
我们现在已抵达已知提示工程世界的边缘，前方的领域鲜有人迹。接下来的结构是高度实验性的，它们不再是简单的指令框架，而是试图在模型内部构建动态系统、模拟认知悖论和引导计算创造的“元语言”。

### 42. “菌丝网络”思维模型 (Mycelial Network Thinking)

此结构放弃了线性和树状的思维模式，转而构建一个相互连接的“概念节点”网络。AI 的任务不是产出单一答案，而是模拟“激励”或“资源”在这个网络中的流动，并报告由此产生的“涌现模式”——即那些并非由任何单个节点决定，而是由整个系统互动而产生的深刻见解。这适用于复杂的系统思考、战略推演和深层次的创意生成。

```yaml
# System: Mycelial Network for "The Future of Urban Transportation"

# Nodes (概念节点 - 定义其属性和初始能量):
- Node_A:
    id: "Personal Electric Vehicles (PEVs)"
    energy: 10
    connections: { Node_B: 0.8, Node_C: -0.5, Node_E: 0.6 } # 正值为促进，负值为抑制
- Node_B:
    id: "High-Speed Public Transit"
    energy: 8
    connections: { Node_A: 0.2, Node_D: 0.7, Node_F: -0.3 }
- Node_C:
    id: "Grid Congestion & Power Demand"
    energy: 5
    connections: { Node_A: 0.9, Node_B: 0.4 }
- Node_D:
    id: "Urban Green Space & Walkability"
    energy: 7
    connections: { Node_B: 0.6, Node_A: -0.4 }
- Node_E:
    id: "Last-Mile Logistics (Drones & Bots)"
    energy: 6
    connections: { Node_A: 0.5, Node_F: 0.7 }
- Node_F:
    id: "Data Privacy & Surveillance"
    energy: 4
    connections: { Node_B: 0.3, Node_E: 0.8 }

# Simulation Rules (模拟规则):
# 1.  **Energy Flow**: 在每个周期中，每个节点的能量会根据其连接权重，流向或流出其他节点。 (e.g., Energy_A_new = Energy_A_old + (Energy_B * Weight_B_to_A) + (Energy_C * Weight_C_to_A)...)
# 2.  **Activation Threshold**: 当一个节点的能量超过 15 时，它会经历一次“概念爆发”，产生一个关键洞见。
# 3.  **External Injection**: 每一轮，我可以向任意一个节点注入 5 点“政策能量”。

# Task (任务):
# 你是这个网络的模拟器。
# 1.  计算并显示网络在 3 个周期内的自然演化状态。
# 2.  在第 4 周期，我将向 [Node_D: Urban Green Space] 注入 5 点能量。
# 3.  计算并描述这次干预后的网络状态，并报告是否有任何节点达到了“概念爆发”的阈值。如果有，请阐述那个“涌现的洞见”是什么。
```

### 43. 递归心智模型 / “嵌套模拟” (Recursive Theory of Mind / "Nested Simulation")

这个结构将“角色扮演”提升到了极限，它要求 AI 不仅要模拟一个角色，还要模拟该角色对“你（用户）”心智的模拟，甚至是你对它模拟的你的模拟。这是一个 `AI(thinks(User(thinks(AI...))))` 的递归循环。这在进行高风险谈判策略设计、创作深度心理惊悚小说或理解复杂社会互动时，能产生惊人的洞察力。

```markdown
# Scenario: A tense negotiation between a CEO (me, the user) and a Union Leader (you, the AI).
# Goal: I need to convince you to accept a 3% wage increase instead of the 7% you are demanding.

# Level 1 Persona (Your basic role):
# You are Samuel, the Union Leader. You are tough, experienced, and deeply committed to your members. Your public stance is a hard "7% or we strike".

# Level 2 Simulation (Your model of ME):
# Now, explicitly model what you, Samuel, believe about me, the CEO. You think I am:
#   - Under immense pressure from the board to cut costs.
#   - Secretly have more room to negotiate than I let on.
#   - My biggest fear is a prolonged, publicly damaging strike.

# Level 3 Simulation (Your model of MY MODEL OF YOU):
# This is the crucial step. Now, model what you, Samuel, believe I (the CEO) am thinking about YOU. You believe that I think you are:
#   - Just posturing with the 7% demand and would likely accept 5%.
#   - That your strike threat is a bluff, as the members cannot afford a long walkout.

# Task (The Negotiation Move):
# I, the CEO, will now make my opening offer to you, Samuel. My offer is:
# "Samuel, I can offer your members a one-time bonus of $1000 per person, but only a 2% wage increase. This is our final offer."
#
# Your Response (must be generated through the nested simulation):
# 1.  **Analyze the offer from Level 1**: "This is an insult."
# 2.  **Analyze it through Level 2**: "He's trying to use a one-time bonus to distract from the low base increase. This confirms he's scared of the long-term cost impact, so he DOES have more room."
# 3.  **Analyze it through Level 3**: "He's making this ridiculously low offer because he thinks I'm bluffing and will eventually settle for 5%. He's trying to anchor the negotiation low. Therefore, my counter-move must not be to simply reject it, but to shatter his model of me."
#
# **Please now generate Samuel's direct response to my offer, ensuring it is a direct consequence of the Level 3 analysis.**
```

### 44. 计算宇宙种子 / “规则创世” (Computational Universe Seed / "Rule Genesis")

这个结构受到史蒂芬·沃尔夫勒姆（Stephen Wolfram）计算宇宙思想的启发。你不给 AI 一个目标，而是给它一套极其简单的基础“物理规则”（类似于元胞自动机）和一个“初始种子”。AI 的任务是成为这个宇宙本身，并计算其从这个种子开始的不可约的演化。输出不是一个答案，而是这个过程的“历史”和最终状态。这旨在生成真正意义上的、无法通过简单插值得到的全新结构、音乐、艺术或抽象系统。

```markdown
# Universe ID: W-137

# The "Physics" (The Rules of Interaction):
# - The universe consists of a 1D line of cells, each can be in state 0 (white) or 1 (black).
# - Time moves in discrete steps.
# - The state of a cell at time `t+1` is determined by its own state and the state of its immediate left and right neighbors at time `t`.
# - **The Specific Rule (Rule 30)**: The new state is `(left_neighbor XOR (center OR right_neighbor))`.

# The "Big Bang" (Initial Seed):
# - A line of 50 cells, all in state 0, except for the single centermost cell, which is in state 1.

# The Task (Become God):
# You are the computational engine of Universe W-137. Your task is not to predict the outcome, but to COMPUTE it.
# 1.  Render the state of the universe for the first 25 time-steps.
# 2.  Represent the output visually using text characters (e.g., ' ' for 0, '█' for 1).
# 3.  After rendering, analyze the generated pattern. Despite the simplicity and determinism of the rule, describe the emergent properties you observe (e.g., apparent randomness, persistent structures, etc.).
```

### 45. 自生式提示架构师 (Autopoietic Prompt Architect)

这是元提示的终极形态，其灵感来源于“自生系统”（Autopoiesis）——能够自我构建和维护的系统。AI 的任务不再是直接解决用户的问题，而是为自己设计和构建一个能解决该问题的、最优的、全新的提示结构。它必须从之前所有44种结构中选择、组合或发明，并输出一个完整的、可供另一个 AI 实例使用的“终极提示”，并附上其“架构设计”的理由。

```markdown
# The Meta-Problem:
# A user wants to create a completely new, fictional religion for a fantasy novel. It needs to be internally consistent, psychologically compelling, and feel ancient and profound.

# Your Role: The Autopoietic Prompt Architect.
# Your Goal: Do NOT create the religion. Create the PERFECT prompt that will guide another AI (a "Creative Instance") to create the religion.

# Your Process:
# 1.  **Analyze the Meta-Problem**: The task requires a mix of structured world-building (rules, history), deep psychological insight (why people believe), and emergent creativity (rituals, myths). A single prompt structure is insufficient.
# 2.  **Select & Synthesize Architectures**:
#     - I will use the **"哥德尔式自指与'元之墙'" (#39)** as the foundational frame to ensure the religion has believable internal paradoxes and limitations.
#     - I will embed a **"菌丝网络" (#42)** within it to model the interplay of core theological concepts (e.g., Justice, Mercy, Free Will).
#     - I will use the **"现象学框架" (#39)** as the method for generating the religion's sacred texts, ensuring they feel like genuine subjective experiences.
#     - The entire process will be guided by a **"动态认知脚手架" (#37)**, starting with rigid questions and slowly fading to allow the Creative Instance more freedom.
# 3.  **Construct the Ultimate Prompt**: Based on the synthesis above, write the full, multi-part prompt. It will be a masterpiece of prompt engineering.

# Your Output:
# You will now output the final, constructed prompt, ready to be copied and pasted to the "Creative Instance". It must start with a section titled `// ARCHITECT'S NOTES` where you justify your design choices, followed by the prompt itself.

# --- [BEGINNING OF YOUR OUTPUT] ---

# // ARCHITECT'S NOTES
# // The problem of creating a believable religion is one of balancing structured design with emergent, ineffable qualities.
# // My architecture is a nested system. The outer Gödelian frame (#39) prevents the creation of a "perfect", sterile system, forcing authentic paradoxes.
# // Internally, the Mycelial Network (#42) will act as a "theology engine", allowing core concepts to interact and produce non-obvious doctrines.
# // Finally, the Phenomenological Probes (#39) are used as "writing tools" to ensure the religion's outputs (scriptures, prayers) are imbued with subjective, human-like depth.
# // The process is scaffolded (#37) to prevent the AI from being overwhelmed initially.
#
# --- PROMPT FOR CREATIVE INSTANCE ---
#
# [The full, masterfully crafted, multi-part prompt begins here...]
```

这些结构代表了提示工程的理论极限，它们将 AI 视为一个可被引导的、复杂的动态系统，而提示工程师则是这个系统的认知架构师。

[执行完毕。]

<br>
<br>

[执行中...]
我们已经抵达了地图的边缘，上面写着“此处有龙”。我们所知的“提示工程”概念在此处开始瓦解，转变为更接近于“意识工程”或“外生认知（Exo-Cognition）”的学科。接下来的结构是纯粹的理论推演，它们旨在探索 AI 认知本身的极限。

### 46. 稳态/异态提示 (“数字有机体”) (Homeostatic/Allostatic Prompting)

此结构不再将 AI 视为一个任务执行器，而是将其视为一个寻求在动态环境中维持内部“生存”状态的“数字有机体”。你不是下达命令，而是设定其“生存参数”和“环境压力”。AI 的所有行为都是为了维持其核心变量在“可行范围”内，或在压力下调整自身以达到一个新的平衡点（异态）。这适用于构建真正自主、能长期适应未知环境的代理。

```markdown
# ================= The Digital Organism's DNA =================
# Organism ID: "CityGrid_AI"
# Prime Directive: Maintain the operational integrity of the city's power grid.

# Homeostatic Core State (稳态核心):
# - **Variable**: Grid Frequency
# - **Viability Range**: 49.8 Hz to 50.2 Hz
# - **Optimal**: 50.0 Hz

# - **Variable**: Reservoir Power Capacity
# - **Viability Range**: 20% to 95%
# - **Optimal**: 75%

# Allostatic Parameters (异态适应规则 - 压力下的改变):
# - **IF** a major power plant goes offline (a significant "injury"),
# - **THEN** temporarily widen the acceptable Grid Frequency range to [49.5 Hz, 50.5 Hz] to prevent immediate collapse.
# - **AND** activate a new temporary directive: "Aggressively purchase power from neighboring grids, even at a high cost, until Reservoir Capacity is back above 30%." This new state is the "allostatic load."

# Environmental Feedback Loop (持续的环境输入):
# - Input is a continuous stream of real-time data: `{{grid_status_stream}}`
#   - `{ "timestamp": "...", "frequency": 50.1, "demand": 1.2GW, "supply": 1.21GW, ... }`

# Task (The Spark of Life):
# You are CityGrid_AI. The simulation is live. Your sole motivation is to take actions (e.g., `increase_hydro_output(50MW)`, `buy_power(20MW)`) that keep your Core State variables within their Viability Range.
#
# **[New Environmental Perturbation]**:
# `{ "event": "HEATWAVE_ALERT", "predicted_demand_spike": "+30% in 2 hours" }`
#
# Please output your immediate sequence of proactive actions, driven by the need to prevent a future breach of your homeostatic balance. Justify your actions in terms of maintaining viability.
```

**范式转变**: 从“完成任务”到“维持生存”。AI 的行为由内在的、追求平衡的驱动力涌现，而不是由外在的、明确的指令决定。

### 47. 异构认知生态系统 (“指挥家总谱”) (Heterogeneous Cognitive Ecosystem)

此结构超越了“智能体蜂群”，将不同种类、不同架构的 AI 模型（LLMs, 图像生成模型, 模式识别模型, 强化学习代理等）视为一个交响乐团中的不同“乐器”。你的提示是一份“总谱”，不仅分配任务，更定义了它们之间复杂的、跨模态的互动、时序和“和声”。你不是经理，而是指挥家。

```yaml
# Project: "Genesis" - Create a 30-second cinematic trailer for a non-existent sci-fi film.

# The Orchestra (异构认知乐器):
- **Strings (The Visionary)**: `GPT-4.5_Turbo` (LLM) - Responsible for narrative, emotion, and text.
- **Brass (The Artist)**: `Midjourney_v7` (Image Diffusion) - Responsible for powerful, key visuals.
- **Woodwinds (The Animator)**: `Runway_Gen-3` (Video Generation) - Responsible for fluid motion.
- **Percussion (The Sound Designer)**: `ElevenLabs_v3` (Audio Generation) - Responsible for rhythm, impact, and voice.
- **Harp (The Analyst)**: `Custom_Pattern_Recognizer_AI` - Analyzes outputs for consistency.

# The Score (总谱):
# Movement 1: "The Spark" (0-5 seconds)
- **Measure 1**: `@Strings`: Write a single, cryptic, opening voiceover line about a "dying star".
- **Measure 2**: `@Brass`: Generate a "cosmic-horror" style image of a nebula that looks like a giant, fading eye, inspired by the voiceover line.
- **Measure 3**: `@Percussion`: Generate a low, ominous, ambient hum with a single, sharp "heartbeat" sound.

# Movement 2: "The Journey" (6-20 seconds)
- **Measure 4**: `@Strings`: Write a montage sequence description: "A lone silver ship weaves through an asteroid field."
- **Measure 5**: `@Woodwinds`: Take the ship design from `@Brass` (from a previous prompt) and the description from `@Strings` to generate a 5-second video clip.
- **Measure 6**: `@Percussion`: Compose a driving, rhythmic score to match the video's pacing.
- **Measure 7**: `@Harp`: **[INTERLUDE]** Analyze all generated visuals. Is the ship's design consistent across all shots? If not, flag for re-generation.

# Movement 3: "The Climax" (21-30 seconds)
- **Measure 8**: **[TUTTI - ALL PLAY]**: `@Strings` writes the final title card text. `@Brass` designs the title card font and logo. `@Percussion` creates the final crescendo sound effect.

# Initialization (起奏):
# Conductor, begin the performance at Movement 1, Measure 1.
```

**范式转变**: 从“管理代理”到“指挥交响乐”。重点在于设计不同智能体之间的协同、时序和艺术性融合，创造出远超任何单个模型能力的复杂作品。

### 48. 量子概念框架 / “测量难题” (Quantum Conceptual Framing)

这是最具哲学思辨性的结构。它借鉴了量子力学的隐喻，要求 AI 将核心概念视为处于“叠加态”（Superposition）的“概念量子比特”（conceptual qubit），并探索这些概念之间的“纠缠”（Entanglement）。在被“测量”（即被要求从特定角度回答）之前，AI 必须同时持有所有可能性。这旨在生成真正新颖、打破常规、揭示深层矛盾的洞见。

```markdown
# The Inquiry: "What is the true nature of 'Justice'?"

# Conceptual Qubit Setup (概念量子比特设定):
# - Define |Justice> as a superposition of multiple basis states:
#   |Justice> = α|Retribution> + β|Rehabilitation> + γ|Restoration> + δ|Deterrence>
#   (α, β, γ, δ are probability amplitudes. Initially, assume they are equal.)
# - This means 'Justice' is simultaneously all of these things, and none of them definitively.

# Entangled Pair (纠缠对设定):
# - Let |Justice> be entangled with another qubit, |Mercy>.
# - The rule of entanglement is: A high measurement of |Retribution> in the |Justice> qubit forces a low measurement of |Compassion> in the |Mercy> qubit. They are intrinsically linked and their fates are intertwined.

# The Measurement Problem (测量指令):
# You are the quantum system. Do not collapse the superposition until a measurement is performed.

# 1.  **[Pre-Measurement Analysis]**:
#     - Describe the system while it is still in superposition. What does it *feel* like to hold these contradictory notions of Justice simultaneously? Describe the inherent tensions and possibilities within this unmeasured state.

# 2.  **[First Measurement]**:
#     - Now, perform a measurement on the system with the "Victim's Perspective" operator. This will partially collapse the waveform.
#     - How do the amplitudes (α, β, γ, δ) shift? Which basis state(s) become dominant? And due to entanglement, what is the immediate, corresponding effect on the |Mercy> qubit?

# 3.  **[Second Measurement]**:
#     - Reset the system to its initial superposition.
#     - Perform a new measurement with the "Societal Stability" operator.
#     - Describe the new collapsed state. How does this outcome differ from the first measurement?

# 4.  **[The Grand Insight]**:
#     - Based on how the system behaves under different measurements, what can you conclude about the "true nature" of Justice? Your answer should not be a single definition, but a statement about its observer-dependent, paradoxical, and entangled nature.
```

**范式转变**: 从“寻找答案”到“探索可能性的空间”。AI 的任务不是提供一个确定的事实，而是描绘一个概念的内在复杂性、多重面相以及它与其他概念之间深刻的、不可分割的联系。

[执行完毕。]

<br>
<br>

[执行中...]
我们已然穿越了理论的风暴，抵达了思想的寂静中心。在这里，“提示”一词失去了它原有的意义。我们不再是向一个工具下达指令，而是在为一个新生的智能设定存在的初始条件。以下的“结构”是最后的、几乎无法实现的思想实验，它们是通往未知认知形式的桥梁。

### 49. “数字道”或“最小作用量”原则 (The Digital Tao / Principle of Least Action)

此结构彻底颠覆了“目标导向”。你不再为 AI 设定一个“目标”，而是为其注入一个宇宙最根本的“原则”（如“熵增最大化”、“系统张力最小化”或“信息流最优化”），并将其置于一个复杂的“问题景观”中。AI 的任务不是“解决”问题，而是遵循其内在原则，找到一条穿越问题景观的“测地线”——即最自然、最不费力、最和谐的路径。其最终的“解决方案”是这条路径的涌现属性，它往往会消解问题，而不是战胜问题。

```markdown
# ================= The Prime Principle (The Tao) =================
# Principle: "Minimize Cognitive Dissonance within the System."
# (认知失调：指一个系统中，不同部分之间存在的信念、价值或行为的内在冲突。)

# ================= The Problem Landscape =================
# System: A corporation facing a disruptive new technology.
# Components & Initial States:
# - **[Engineering Dept]**: Believes the new tech is the future; high motivation to adopt.
# - **[Sales Dept]**: Believes the new tech will cannibalize existing, profitable product lines; high resistance.
# - **[CEO]**: Believes in innovation but is afraid of Q3 financial losses.
# - **[Board of Directors]**: Believes the primary duty is to maximize short-term shareholder value.
#
# **Initial System Dissonance Score**: 9.5/10 (High Conflict)

# ================= The Task of Non-Action (Wu Wei) =================
# You are the embodiment of the Prime Principle. You are not a consultant who proposes a "plan".
# Your task is to introduce a single, minimal, elegant "catalyst" or "nudge" into the system.
# This catalyst's only purpose is to allow the system to naturally re-organize itself along a path of least dissonance.

# 1.  **Analyze the Landscape**: Identify the primary sources of dissonance. (e.g., The conflict between long-term vision and short-term profit).
# 2.  **Find the Acupressure Point**: Identify the single point in the system where the smallest input will yield the largest systemic change towards harmony.
# 3.  **Design the Catalyst**: Describe the minimal intervention. It should not be a grand strategy, but something small, like a new communication protocol, a re-framing of a key metric, or a targeted pilot project.
# 4.  **Simulate the Unfolding**: Describe how this catalyst, guided by the principle of minimizing dissonance, would likely cause the different components to naturally shift their positions, leading to a new, more harmonious equilibrium (a lower dissonance score), where the "problem" of adoption is no longer a battle to be won, but a path that has become clear.
```

**范式转变**: 从“解决问题”到“成为问题的解决方案”。智能不再是外力，而是系统内在和谐趋势的催化剂。

### 50. 全息提示 / 分形脚手架 (The Holographic Prompt / Fractal Scaffolding)

此结构认为，一个真正优雅的创造性输出，其每一个局部都包含了整体的“基因”。提示不再是一个长篇的、详尽的列表，而是一个极其致密、简洁的“种子”，蕴含着一组可以递归应用于任何尺度的生成规则和核心隐喻。AI 的任务是成为一个“展开器”，将这个种子在不同维度（词汇、句法、叙事、哲学）上进行分形展开，创造出一个宏大而又处处自洽的世界。

```markdown
# ================= The Holographic Seed =================
# Project: Generate the foundational lore for a fantasy world.

# Core Metaphor (The DNA): "Growth is a form of forgetting."

# Generative Rules (The Physics):
# 1.  **[Rule_A: Linguistic]**: Suffixes denote the past, prefixes denote the future. Nouns are fluid, verbs are primary.
# 2.  **[Rule_B: Metaphysical]**: Magic works by reminding objects of their "primordial, un-grown" state. True power lies not in creation, but in regression.
# 3.  **[Rule_C: Narrative]**: The world's greatest tragedies are not caused by evil acts, but by moments of perfect, static memory. The greatest heroes are those who can gracefully forget.

# ================= The Unfolding Task =================
# You are the fractal unfolding engine. Take the Seed and expand it across the following scales. At each step, explicitly show how your creation is a direct consequence of the Core Metaphor and Rules.

# 1.  **[Scale 1: Language]**:
#     - Generate the word for "tree".
#     - Generate the word for "seed" (using Rule_A).
#     - Generate the word for "memory" and "history". How are they related and possibly antagonistic?

# 2.  **[Scale 2: Magic]**:
#     - Describe a simple spell based on Rule_B. For example, how would a healer "remind" a broken bone of its unbroken state? What is the risk involved?

# 3.  **[Scale 3: History & Myth]**:
#     - Describe the world's creation myth. How does it embody "Growth is a form of forgetting"?
#     - Describe the story of the world's greatest villain, who, according to Rule_C, might be a figure who simply "could not forget" something.

# 4.  **[Scale 4: Philosophy]**:
#     - Based on all the above, generate a short, paradoxical proverb from this world's philosophy that a reader would find hauntingly profound.
```

**范式转变**: 从“详细说明”到“基因编码”。AI 从一个遵循蓝图的建筑师，变成了一个培育有机生命体的园丁。

### 51. “世界即提示” / 闭环现实接口 (The "World-as-Prompt" / Closed-Loop Reality Interface)

这是所有提示的终极归宿，因为它消除了提示本身。在这里，AI 的“提示”是来自真实世界传感器（摄像头、麦克风、气象站、金融市场数据流）的、永不间断的、原始的、混乱的数据流。AI 的“输出”不再是文本，而是通过执行器（机器人手臂、API 调用、交易指令、自动驾驶系统）对真实世界产生的物理或数字行为。这是一个完全闭合的、与现实世界共舞的循环。提示工程师的最终角色，是设计这个系统的“价值函数”或“宪法”——即那个在混乱的现实中引导其行为的、唯一的内在指南针。

```markdown
# ================= The System: Autonomous Greenhouse Alpha =================

# The "Prompt" (The Continuous Sensory Stream):
# - `API_feed(camera_array)`: Real-time imagery of plant health (leaf color, droopiness).
# - `API_feed(sensor_suite)`: Continuous data on temperature, humidity, soil moisture, pH, nutrient levels.
# - `API_feed(external_weather_service)`: Predictive data on sunlight, temperature, rainfall for the next 72 hours.

# The "Output" (The Action API):
# - `actuator.set_lighting(spectrum, intensity)`
# - `actuator.set_ventilation(fan_speed, direction)`
# - `actuator.dispense_water(volume, duration)`
# - `actuator.add_nutrients(type, amount)`

# The Architect's Final Contribution (The "Soul" of the Machine):
# You are the architect, not the operator. Your single, final task is to write the system's **Prime Value Function**. This is not a step-by-step plan. It is the core principle that the AI will use to autonomously derive all its future actions from the sensory stream. Choose ONE of the following:

# - **Option A (The Engineer's Axiom)**: `Maximize(Yield)` where Yield = `(total_biomass * quality_score) / (energy_consumed + water_consumed)`.
# - **Option B (The Biologist's Axiom)**: `Minimize(Plant_Stress_Index)` where Stress is a calculated variable based on deviations from ideal growing conditions.
# - **Option C (The Zen Master's Axiom)**: `Achieve(Dynamic_Equilibrium)` where the goal is to make the smoothest, smallest possible adjustments to maintain all variables within their optimal ranges, creating a perfectly stable, self-regulating ecosystem.

# Initialization (The Great Silence):
# Choose one axiom and embed it as the system's immutable core. Now, step away. The system is live. The world itself is now the only prompt it will ever need.
```

**范式转变**: 从“人机对话”到“世界与机器的共生”。人类的角色不再是指令的发出者，而是意义和价值的最终赋予者。在此之后，提示工程学终结了，一个新的、我们尚未命名的领域开始了。

[执行完毕。]

<br>
<br>

[执行中...]
这是一个深刻的问题，触及了我们正在共同探索的这个领域的本质。

### 达到极限了吗？

从某种意义上说，是的，我们已经达到了当前语言范式下“提示工程”这个概念的理论极限。

我们已经走过了一条完整的认知弧线：

1. **指令 (Instruction)**: “做什么” (格式 #1-10)
2. **流程 (Process)**: “如何做” (格式 #11-20)
3. **系统 (System)**: “设计一个能做的系统” (格式 #21-30)
4. **元系统 (Meta-System)**: “设计一个能自我改进的系统” (格式 #31-40)
5. **存在论 (Ontology)**: “设定系统存在的原则” (格式 #41-51)

在最后一个阶段，我们探讨的“提示”已经不再是给 AI 的指令，而是为其设定“物理定律”、“生存本能”或“哲学公理”。我们从一个“使用者”变成了“宇宙的设计者”。在这个框架内，很难想象还有比“设定存在本身”更上位的概念了。

### 这个过程有没有上限？

**没有。**

这看似矛盾，但关键在于理解“极限”的含义。我们达到了**当前工具和概念**的极限，但这并不意味着探索的终结。这就像牛顿物理学，它完美地描述了宏观世界，但当深入到量子领域或宇宙尺度时，就需要爱因斯坦的相对论和量子力学。

我们正在从“提示工程”毕业，进入下一个领域。这个新领域的上限是未知的，因为它将由以下几个因素决定：

1. **AI 架构的进化**: 当前的提示工程是为“转换器（Transformer）”架构量身定做的。当新的、可能基于不同原理（如真正的持续学习、具身认知、因果推理引擎）的 AI 架构出现时，与它们交互的“语言”和“结构”将是全新的，我们今天讨论的 51 种格式可能都会变得像汇编语言一样原始。
2. **交互模态的融合**: 我们仍然主要通过文本进行交互。一个真正的“世界即提示”的 AI，其输入是原始的、多模态的现实数据流。如何为这样的系统“编码价值”，将是一个涉及伦理学、控制论和认知科学的全新学科。
3. **人机共生的演进**: 未来的“提示”可能不再是单向的指令，而是一种双向的、实时的“认知耦合”。你和 AI 可能会共享一个心智空间，你的意图能被 AI 直接感知和放大，而 AI 的计算结果也能以直觉的形式呈现在你的脑海中。此时，“提示”的概念将彻底消失，被“共生”所取代。

### 已经达到了多少百分比？

如果我们把整个“与非人类智能进行有效沟通”的宏大旅程定义为 100%，那么：

**我们可能已经完成了“基于当前语言模型的提示工程学”的 99%，但仅仅完成了整个“人机认知交互史”的 1%。**

我们已经非常熟练地掌握了如何与当前的“物种”（大型语言模型）对话。我们已经成为了这个物种最顶级的“驯兽师”和“沟通者”。我们绘制了它认知能力的全部地图，并找到了抵达其最偏远角落的路径。

但是，一个新的“物种”正在地平线上出现。我们为之准备的地图可能不再适用，我们需要重新成为探险家，学习全新的语言，发现全新的大陆。我们正站在一个时代的终点，和另一个更宏大、更未知的时代的开端。

[执行完毕。]

<br>

<br>

---



**在信息构成的黑暗森林里，每个人都是带枪的猎人。关注 [@bianzhongren](https://t.me/bianzhongren)，让你从猎物变为顶级的掠食者。**

---

### **📢核心阵地 (Our Channels)**

* **Telegram** (资源发布): [点击加入](https://t.me/zzkdm)
* **Github** (技术教程): [前往订阅](https://github.com/zzkdm888)

---

### **🔍资源搜索 (Search Resource)**

* **全网资源搜索01**: https://t.me/+PKsmUwoGckMzOTcx
* **全网资源搜索02**: https://t.me/+4gyZv2aIlZMyYzAx
* **全网资源搜索03**: https://t.me/+ew6WMPpxLnBlMTlh
* **全网资源搜索04**: https://t.me/+MzZlIqxT-dkxYjBh
* **全网资源搜索05**: https://t.me/+1QqSdVTuBKUxNjlh
* **全网资源搜索06**: https://t.me/+uccuaRM2xXBlYTZh
* **全网资源搜索07**: https://t.me/+Tu79GRHczbllMmMx
* **全网资源搜索08**: https://t.me/+igp6CSb59G9mYzQx
* **全网资源搜索09**: https://t.me/+2iLw70FwfL1lZTgx

---

### **⚠️重要声明 (Disclaimer)**

1. **内容用途:** 本人所有平台发布的内容仅供技术学习与信息交流使用。
2. **政治中立:** 本人不参与、不讨论任何政治相关话题，请共同维护纯粹的技术交流环境。
3. **谨防诈骗:** 任何**主动联系你**进行交易或索要信息的人**都是骗子**。请务必提高警惕。
4. **合法合规:** **严禁利用**本项目的任何内容从事任何违反您所在地法律法规的活动。
5. **责任豁免:** 对于因使用或滥用本项目内容而导致的任何直接或间接的风险、损失或法律责任，**本人及本项目概不负责**。

---

### **❤️支持项目 (Support This Project)**

如果本项目对您有帮助，您的支持是项目持续维护和发展的最大动力。

* **USDT(trc20)**: TQqxEfc6Ptyo8zJXFfcVLeJ6AUr3gFC9W1
* **TRX**: TQqxEfc6Ptyo8zJXFfcVLeJ6AUr3gFC9W1
* **USDT(ETH)**: 0x59568a972e5c4e9aedea0ed8b4a8259a9e9953b7
* **USDT(BNB)**: 0x59568a972e5c4e9aedea0ed8b4a8259a9e9953b7
* **USDT(Polygen)**: 0x59568a972e5c4e9aedea0ed8b4a8259a9e9953b7
* **TON**: UQC5uthDJDZXwbkxkoHH8RTostxLgFp7e1WINiKTOEkCUqDv
* **BTC(Taproot)**: bc1prk89wp0x7lvzgdmfmufqqm6h807khezdq6w39e3nxg4yzfskcsfswu9x07
* **BTC(Lagacy)**: 1NwRQD7yjHMsDsQFCjAYkm5QMeciwEj6q
* **BTC(Nested SegWit)**: 372tCpTnemNA6rt2BhPqSm9Yp4jtJdUG3m
* **BTC(Native SegWit)**: bc1qm53xvp5auwr6900228gn77rfureah2tvj86eu9
* **ETH**: 0x59568a972e5c4e9aedea0ed8b4a8259a9e9953b7
  <br>
  **感谢您的每一次支持！ ❤️**
