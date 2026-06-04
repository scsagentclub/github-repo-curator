---
name: github-repo-curator
description: >
  解析 GitHub 项目地址并生成项目摘要，在用户要求"入库"时将项目分类保存到本地 Markdown 知识库。
  使用场景：(1) 用户发送 GitHub URL 请求分析项目，(2) 用户说"入库"/"保存到知识库"/"归档"要求保存已分析的项目，
  (3) 批量处理多个 GitHub 项目并归档。自动分类为：硬件开发、一人公司、agent 开发、好用工具，或按需创建新分类。
---

# GitHub 项目知识库整理

## 解析项目流程

当用户发送 GitHub 地址（如 `https://github.com/owner/repo`）时：

1. **提取信息**：从 URL 提取 owner 和 repo 名称。
2. **获取数据**：
   - 使用 FetchURL 获取仓库主页 `https://github.com/owner/repo`
   - 尝试获取 README：`https://raw.githubusercontent.com/owner/repo/main/README.md`
   - 如果 main 分支不存在，尝试 `master` 分支。
3. **生成摘要**：分析并输出以下信息：
   - **项目名称** 与 **一句话描述**
   - **主要功能**：项目解决什么问题、核心特性
   - **技术栈**：主要编程语言、框架
   - **适用场景**：谁会用、在什么情况下用
   - **推荐分类**：按下方规则给出最匹配的分类（可多个候选）
   - **标签建议**：3-5 个关键词标签

如果用户一次发送多个 URL，按顺序逐个解析，最后给出汇总列表。

## 入库流程

当用户说"入库"、"保存"、"归档"、"加入知识库"时：

1. **确认知识库路径**：
   - 如果当前会话未记录路径，询问用户知识库根目录（例如 `~/knowledge-base/`）。
   - 记录该路径供后续使用。
2. **确认分类**：
   - 向用户展示推荐分类，询问是否正确。
   - 用户可接受、更换为已有分类、或要求创建新分类。
3. **保存文件**：
   - 在知识库根目录下按分类创建子目录（如 `hardware-dev/`、`agent-dev/`）。
   - 子目录名使用英文 kebab-case，便于跨平台兼容。
   - 每个项目保存为独立 Markdown 文件：`knowledge-base/<category>/<repo-name>.md`
4. **确认结果**：告知用户文件保存的完整路径。

## 分类规则

| 中文名 | 目录名 | 判断标准 |
|---|---|---|
| 硬件开发 | `hardware-dev` | 嵌入式、IoT、PCB、3D打印、机器人、Arduino、ESP32、Raspberry Pi、固件、硬件设计、传感器、电机驱动 |
| 一人公司 | `solo-business` | 独立开发、SaaS、副业变现、营销工具、个人品牌、indie hacker、solopreneur、收费模板、landing page 生成器 |
| Agent 开发 | `agent-dev` | AI Agent、LLM、MCP、AutoGPT、LangChain、RAG、多智能体、工作流自动化、AI 基础设施、模型部署 |
| 好用工具 | `useful-tools` | CLI 工具、效率工具、开发者工具、脚本、开源软件、日常实用工具、文件处理、系统优化 |

**创建新分类**：如果项目明显不属于以上分类，询问用户是否创建新分类。新分类目录名使用英文 kebab-case（如 `game-dev`、`data-science`），并在 SKILL.md 的参考中记录。

## Markdown 文件模板

每个项目保存为以下格式的 Markdown 文件：

```markdown
---
name: <项目名称>
github_url: <原始 GitHub URL>
category: <分类中文名>
tags: [<标签1>, <标签2>, <标签3>]
added_date: <YYYY-MM-DD>
summary: <一句话描述>
---

## 项目简介

<2-3 句话描述项目核心功能>

## 主要特性

- <特性 1>
- <特性 2>
- <特性 3>

## 技术栈

<主要语言和框架>

## 适用场景

<谁应该使用这个项目，解决什么问题>

## 备注

<可选：安装方式、Star 数、许可证、个人评价>
```

## 注意事项

- 如果 FetchURL 获取 GitHub 主页失败，提示用户可能是私有仓库或网络问题，询问是否有其他信息来源。
- 如果 README 获取失败但主页成功，基于主页信息生成摘要，并在备注中注明"README 获取失败"。
- 同一项目重复入库时，询问用户是覆盖还是跳过。
- 知识库路径使用绝对路径或相对于 home 目录的路径，避免歧义。
