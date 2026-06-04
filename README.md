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

## 安装

### 方式一：自然语言（推荐）

直接告诉你的 AI 助手：

> "帮我安装 github-repo-curator 技能，仓库地址是 https://github.com/scsagentclub/github-repo-curator"

AI 助手会自动下载并加载该技能。

### 方式二：终端命令

将本技能克隆或复制到你的 AI 助手 skills 目录：

```bash
# 用户级安装（推荐）
git clone https://github.com/scsagentclub/github-repo-curator.git ~/.config/agents/skills/github-repo-curator

# 或项目级安装
git clone https://github.com/scsagentclub/github-repo-curator.git ./skills/github-repo-curator

# 或手动复制
mkdir -p ~/.config/agents/skills/github-repo-curator
cp SKILL.md ~/.config/agents/skills/github-repo-curator/SKILL.md
```

常见 skills 目录路径：
- `~/.config/agents/skills/`
- `~/.kimi/skills/`
- `~/.claude/skills/`
- `./skills/`（项目级）

## 使用方法

1. 安装并加载本技能
2. 发送任意 GitHub 项目链接，助手会自动解析
3. 回复"入库"，项目摘要即自动保存并同步到远端

## 关联仓库

- 知识库仓库：`https://github.com/scsagentclub/knowledge-base`

## License

MIT
