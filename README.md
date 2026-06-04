# GitHub Repo Curator

自动解析 GitHub 项目、生成中文摘要，并分类归档到 Markdown 知识库的助手技能。入库后自动同步到远端 GitHub 仓库，本地与云端始终保持一致。

## 功能

- **项目解析**：输入 GitHub 地址，自动拉取 README 和仓库信息，生成中文摘要
- **智能分类**：自动归类到硬件开发、一人公司、Agent 开发、好用工具等分类
- **一键入库**：说"入库"即可自动保存到本地知识库
- **自动同步**：入库后自动推送到远端，网络不佳时自动 fallback 到 GitHub API

## 分类体系

| 分类 | 目录 | 说明 |
|---|---|---|
| 硬件开发 | `hardware-dev` | ESP32、Arduino、IoT、PCB、机器人等 |
| 一人公司 | `solo-business` | SaaS、独立开发、副业变现、营销工具 |
| Agent 开发 | `agent-dev` | AI Agent、LLM、MCP、RAG、工作流自动化 |
| 好用工具 | `useful-tools` | CLI 工具、效率工具、开发者工具 |

> 支持按需创建新分类，目录名使用英文 kebab-case。

## 使用方法

1. 安装本技能到你的 AI 助手 skills 目录
2. 发送任意 GitHub 项目链接，助手会自动解析
3. 回复"入库"，项目摘要即自动保存并同步到远端

## 关联仓库

- 知识库仓库：`https://github.com/scsagentclub/knowledge-base`

## License

MIT
