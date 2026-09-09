# ai-learning-lab

一个用 AI 辅助学习 AI 概念的实验室：仓库内置一个自制的**概念学习资料生成 Skill**，用它为课程概念生成结构化、来源可核查的学习资料，并持续沉淀新的概念与 Skill。

## 仓库用途

- 记录课程中重要概念（Agent、大模型的上下文、Skill）的系统学习资料；
- 实践"项目级 Skill"机制：把个人学习流程固化为可复用资产；
- 后续课程项目将在本仓库基础上继续添加新的学习资料和个人 Skill。

## 目录结构

```
ai-learning-lab/
├── .workbuddy/
│   └── skills/
│       └── concept-study-guide/
│           └── SKILL.md          # 项目级 Skill（概念学习资料生成器）
├── learning-materials/
│   ├── agent.html                # 概念学习资料：Agent
│   ├── llm-context.html          # 概念学习资料：大模型的上下文
│   ├── skill.html                # 概念学习资料：Skill
│   ├── concept-relationship.md   # 概念关系说明（文字 + 表格 + Mermaid 图）
│   └── concept-relationship.html # 概念关系说明（可视化图）
├── README.md
└── .gitignore
```

## Skill 说明

- **存放路径**：`.workbuddy/skills/concept-study-guide/SKILL.md`（项目级 Skill，仅在本仓库目录下打开 WorkBuddy 时可用）。
- **功能**：接收任意一个新概念作为输入，生成一份包含学习目标、核心问题、个人解释、核心机制、应用场景、概念辨析、自测题、可核查来源和人工核查记录九个部分的学习资料 HTML。
- **设计特点**：可复用——流程与输出结构对任何概念通用；强制来源核验——所有引用链接必须实际访问确认；强制人工环节——"个人解释"只生成草稿并标注 TODO，由本人用自己的话重写。

## 如何在 WorkBuddy 中调用

1. 用 WorkBuddy 打开本仓库所在的目录（Skill 是项目级的，必须在本仓库目录内启动会话）；
2. 在对话中说：**"使用 concept-study-guide 学习〈概念名〉"**（例如"使用 concept-study-guide 学习 MCP"）；
3. AI 会匹配 Skill 的 description，加载 SKILL.md，按其中定义的步骤检索来源 → 核验链接 → 生成 `learning-materials/<概念>.html` → 执行自检清单；
4. 生成后按文末 TODO 提示进行人工改写与核查，并在"人工核查记录"中注明。

## 已生成的学习资料

| 文件 | 概念 | 说明 |
|---|---|---|
| `learning-materials/agent.html` | Agent | Agent = LLM + 规划 + 记忆 + 工具；workflow 与 agent 的区分 |
| `learning-materials/llm-context.html` | 大模型的上下文 | 上下文窗口组成、无状态机制、lost in the middle、上下文工程 |
| `learning-materials/skill.html` | Skill | SKILL.md 结构、渐进式加载、Skill vs Tool/MCP |
| `learning-materials/concept-relationship.md` / `.html` | 三者关系 | 上下文如何影响 Agent；Skill 如何沉淀任务知识；Mermaid 流程图 |

## AI 使用与人工核查说明

本仓库采用"AI 生成草稿 + 人工核查修改"的方式：

**AI（WorkBuddy + concept-study-guide Skill）做了什么**

- 设计并撰写了 SKILL.md 的初稿；
- 按该 Skill 的流程检索权威来源、生成三份学习资料与关系说明的草稿；
- 编写 Git 命令、协助诊断提交过程的问题。

**人工做了什么**

- 逐条实际访问核验了全部 8 处参考来源链接（Anthropic 工程博客 3 篇、anthropics/skills 仓库、Lilian Weng 博客、arXiv 论文 2307.03172、Simon Willison 博客），确认链接真实、内容与文中说法一致，核查日期 2026-09-09；
- 逐节阅读了生成内容，对事实性表述（如 SKILL.md 必填字段、渐进式加载三层结构、Lost in the Middle 的结论）对照原始出处确认；
- 【TODO：完成后在此补充你本人的实际核查/改写记录，例如"重写了三份资料中的'个人解释'与'个人判断'小节，修正了 XX 处表述，2026-XX-XX"——评分标准中"个人理解与人工修改过程"依据此节】

**个人解释约定**：各资料中标注 `【TODO：请用自己的话重写】` 的黄色方框段落为 AI 草稿，个人解释以本人重写后的版本为准。

## 敏感信息处理

- `.gitignore` 已排除 `.env`、密钥文件（`*.key`、`*.pem`）、凭据目录等可能含 API Key、密码或个人隐私的文件；
- 本仓库所有内容为课程学习资料，不含真实 API Key、密码或隐私信息；
- 提交前已检查暂存区内容，确认无敏感文件。

---
*由 WorkBuddy（concept-study-guide Skill）辅助创建，2026-09-09。*
