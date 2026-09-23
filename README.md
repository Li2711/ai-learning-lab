# ai-learning-lab

一个用 AI 辅助学习 AI 概念的实验室：仓库内置一个自制的**概念学习资料生成 Skill**，用它为课程概念生成结构化、来源可核查的学习资料，并持续沉淀新的概念与 Skill。

## 作业信息

- 课程作业：借助 AI 创建 GitHub 仓库 → 建立项目级 Skill → 生成概念学习资料 → 提交与推送
- 仓库链接：https://github.com/Li2711/ai-learning-lab （Public，可直接访问）
- 仓库内容：项目级 Skill、三份概念学习资料（Agent / 大模型的上下文 / Skill）、概念关系说明、README 与 .gitignore

## 如何在浏览器中查看学习资料

> **提示**：在 GitHub 网页上直接点击 `agent.html` 等文件时，GitHub 显示的是**网页源代码**（`<div>`、`<style>` 这类标签），这是 GitHub 对代码文件的正常展示方式，**不是文件乱码或损坏**——文件的编码是正确的 UTF-8，中文完全正常。

三种查看方式：

1. **在线浏览（推荐）**：开启 GitHub Pages 后直接访问 <https://li2711.github.io/ai-learning-lab/> ，即为渲染好的网页。
2. **本地查看**：`git clone https://github.com/Li2711/ai-learning-lab.git`（或点 Code → Download ZIP），双击 `learning-materials/index.html` 即可浏览。
3. **看文字版**：`learning-materials/concept-relationship.md` 在 GitHub 上可直接正常阅读（Markdown 会被渲染）。

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
│   ├── index.html                # 学习资料导航页（从浏览器打开这里）
│   ├── agent.html                # 概念学习资料：Agent
│   ├── llm-context.html          # 概念学习资料：大模型的上下文
│   ├── skill.html                # 概念学习资料：Skill
│   ├── concept-relationship.md   # 概念关系说明（文字 + 表格 + Mermaid 图）
│   └── concept-relationship.html # 概念关系说明（可视化图）
├── pypy/                         # Python 练习项目（个人学习用）
│   ├── script/01.ipynb           # Jupyter 练习笔记
│   ├── README.md
│   └── .gitignore                # 排除 .venv 虚拟环境
├── index.html                    # 仓库入口页（GitHub Pages 用）
├── README.md
└── .gitignore
```

## pypy 子目录说明

`pypy/` 是与课程作业无关的个人 Python 练习项目，作为子目录并入本仓库。

- 项目原本使用本地虚拟环境 `.venv`（约 109MB、9500+ 个文件），**已在 `pypy/.gitignore` 中排除**，不入库；
- 克隆后如需运行，请在 `pypy/` 下自行创建虚拟环境：`python -m venv .venv`，再按需 `pip install`；
- 目前 `pypy/script/01.ipynb` 为空笔记本，后续练习内容会持续提交到该目录。

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
| `learning-materials/index.html` | 导航页 | 四份资料的入口，浏览器打开即可浏览 |
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
- 将三份资料与关系说明中 AI 起草的"个人解释 / 个人判断"改写为自己的理解（2026-09-10），并在各资料的"人工核查记录"一节留档；
- 按作业要求把提交过程中的报错与解决方式记录在下方"常见问题与排错记录"，便于复盘。

## 常见问题与排错记录

记录本次从建仓到 push 过程中实际遇到的问题和最终解决方式：

| 现象 | 原因 | 解决方式 |
|---|---|---|
| `remote: Repository not found.` | GitHub 网页上的仓库还没创建（账号当时无任何公开仓库） | 先在 github.com/new 建好 Public 仓库 `ai-learning-lab`（不勾任何初始化选项），再执行 push |
| `fatal: unable to access ... CONNECT tunnel failed, response 502` | 本机代理软件（127.0.0.1:59735）连通，但无法连到 GitHub 上游，属代理节点掉线 | 重启 / 切换代理节点后重新 push 成功；排查手段：`curl -s -o /dev/null -w "%{http_code}" https://github.com` 对比走代理与直连的结果 |
| GitHub 网页匿名访问仓库返回 404 | 一度怀疑仓库是 Private | 用 `https://api.github.com/repos/Li2711/ai-learning-lab` 查询，返回 `"private": false`、`"visibility": "public"`，确认为公开仓库，404 系当时的网络/缓存原因 |
| `main...origin/main [gone]` | 本地与远程的跟踪引用不同步 | 网络恢复后重新 `git push -u origin main`，跟踪关系恢复正常 |

**经验**：push 失败时先分清是"认证问题、仓库不存在"还是"网络问题"——看报错关键词（`Repository not found` vs `CONNECT tunnel failed`）可以快速定位，避免在错误的目录里反复重试。

## 敏感信息处理

- `.gitignore` 已排除 `.env`、密钥文件（`*.key`、`*.pem`）、凭据目录等可能含 API Key、密码或个人隐私的文件；
- 本仓库所有内容为课程学习资料，不含真实 API Key、密码或隐私信息；
- 提交前已检查暂存区内容，确认无敏感文件。

---
*由 WorkBuddy（concept-study-guide Skill）辅助创建，2026-09-09 首次提交，2026-09-10 补充导航页、排错记录并改写个人理解部分。*
