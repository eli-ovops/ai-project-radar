# AI Project Radar Daily

## 项目用途

这是一个面向本地 Codex 工作流的每日 AI 项目雷达任务包。它将公开可核验的 GitHub、YouTube、X/Twitter、Reddit 与开发者生态信号整理为一份中文 Markdown，并优先发现能形成真实客户案例、服务中小企业、提升网站或企业系统交付能力的项目。

本目录只包含任务说明、报告模板、评分规则和报告，不包含后台服务、定时器、账号凭证或依赖。

## 当前运行方式

安全边界禁止创建 cron、scheduler、Codex Automation 或 system service，因此“每天 09:00”是人工触发时间，不是已经部署的自动调度。

每天 09:00 在 Codex 中打开一个新任务，粘贴下面的“每日执行指令”，并把工作目录设为本目录。执行前确认允许访问公开互联网；不要授权登录任何平台。

```text
执行 AI Project Radar Daily。

工作目录：当前 ai-project-radar 目录。
先完整读取 README.md、templates/scoring-rule.md 和 templates/radar-template.md。
仅访问无需登录的公开网页和公开仓库元数据；不得读取 .env、API Key、Secret、Token、Cookie、SSH Key 或云凭证，不得复用浏览器登录态，不得访问私有仓库或真实账户。

采集 GitHub 高星与 Trending、YouTube AI 工具趋势，以及公开网页可核验的 X/Twitter、Reddit 讨论；同时覆盖 Agent Skills、MCP Servers、Claude Code Skills、Codex 工作流和 Vibe Coding 工具。围绕 README 中的关注方向筛选，并永久排除 BitLangLang、交易机器人、自动交易、实盘系统和金融套利。

严格按 scoring-rule.md 评分。每个入选项目必须核验最近更新、License、明显安全风险、密钥需求、公网部署需求和个人开发者适配性。缺失证据必须写“未核验”，不得猜测、补写或用搜索摘要冒充原始证据。社交来源不可访问时标记数据缺口，不得登录。

按 radar-template.md 生成 reports/YYYY-MM-DD-ai-radar.md。覆盖当天已有报告前必须先停下并请求我确认；不要改动本目录之外的任何文件。完成后只汇报报告路径、采集成功/失败来源、Top 3 名称和需要人工复核的风险。
```

## 关注方向

- 网站开发：Next.js、React、Vite、TypeScript、Tailwind、Astro、Payload CMS、Strapi、企业官网、SEO、GEO。
- 腾讯云与部署：腾讯云、CloudBase、EdgeOne、Docker、VPS、DNS、SSL、HTTPS、CDN、Caddy、Nginx。
- 企业系统：库存、ERP、CRM、B2B、客户管理、数据后台、Admin Dashboard。
- AI 提效：Agent、MCP、Skills、Plugins、Workflow、RAG、AI Automation、n8n、Dify、Langflow。
- Coding Agent：Codex、Claude Code、Hermes、OpenClaw、Cursor、Windsurf、Vibe Coding。
- 求职映射：AI Application Engineer、AI Solution Engineer、AI Project Manager、AI Automation Engineer、AI Agent Engineer。

## 输入来源

| 来源 | 允许的取数方式 | 主要证据 | 限制 |
| --- | --- | --- | --- |
| GitHub | 公开仓库页面、公开 Search/Repository/Release 元数据、Trending 页面 | Stars、更新时间、Release、License、Issues、安全公告 | Trending 没有稳定官方 API；未认证请求可能限流 |
| YouTube | 公开搜索结果、公开视频页面和公开元数据 | 发布时间、观看量、频道分散度、主题重复出现 | 不使用需要 Key 的 Data API；数据可能不完整 |
| X/Twitter | 无登录公开网页或公开搜索索引 | 帖子日期、互动、多个独立作者 | 不读 Cookie、不复用登录态；不可访问时必须记缺口 |
| Reddit | 无登录公开网页或公开搜索索引 | 帖子日期、分区、回复与讨论内容 | 不登录；不可访问时必须记缺口 |
| 官方项目资料 | 官方仓库、文档、Release、License、安全策略 | 能力、维护状态、部署与安全边界 | 项目自述不能单独证明市场需求 |

来源选择结论：优先直接使用官方仓库与官方文档；GitHub Trending 只作为热度线索；YouTube、X 和 Reddit 只作为社区信号，不能替代 License、安全或生产适用性核验。第三方榜单可以提供候选，但不能作为唯一证据。

## 输出格式

每次运行只创建一份 `reports/YYYY-MM-DD-ai-radar.md`，正文遵循 `templates/radar-template.md`。同一项目跨来源合并为一条；项目名后附官方链接；所有数量信号附采集日期。

状态只允许：

- `COMPLETE`：主要来源已采集，推荐项的六项风险检查完成。
- `PARTIAL`：部分来源不可用，但 Top 3 的核心证据完整。
- `DATA_COLLECTION_BLOCKED`：没有足够证据形成可信推荐。

## 风险边界

- 不读取或输出任何秘密、Token、Cookie、SSH Key、API Key 或云凭证。
- 不访问真实账户、私有仓库或需要登录的社交平台。
- 不启动长期服务，不创建任何定时任务，不修改系统配置，不安装依赖。
- 不发邮件、消息或通知，不自动部署，不向公网写入。
- 不执行候选项目代码，不运行未知安装脚本，不连接候选项目的云服务。
- 不修改本目录外的文件；不得自动覆盖已有日报。
- 永久排除 BitLangLang、交易机器人、自动交易、实盘系统和金融套利。

## 人工审核

发布或据此投入时间前，人工完成以下复核：

1. 打开 Top 3 的官方仓库、License、最近 Release 和安全页面，确认链接与日期。
2. 区分累计 Stars、当日 Trending 和真实近期增长，避免把历史热度当新趋势。
3. 检查是否要求真实密钥、公网部署、执行第三方代码或高权限配置。
4. 验证目标场景能否在低预算、隔离环境中做出 1 个真实客户案例。
5. 最终只选择一个下一步，不因榜单热度直接投入生产。

## 已知限制

- 当前没有定时调度；需要每天 09:00 人工启动 Codex 任务。
- X/Twitter 与 Reddit 在无登录模式下可能完全不可采集。
- GitHub 和 YouTube 的公开页面可能限流、反爬或改变结构。
- 本任务只做公开桌面研究，不证明留存、付费需求、生产安全或客户接受。
- 首次部署时 `agent-reach` 的 Exa 后端不可用，公开网页检索也未返回可用证据；详见当天报告。

