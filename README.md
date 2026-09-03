# 最佳东方求职助手（veryeast-assistant）

一站式 AI 求职助手 Skill，依托[最佳东方](https://www.veryeast.cn)平台的海量酒店、餐饮、美业、康养、零售、电商等服务业招聘信息，帮求职者找工作、搜职位、投简历、编辑简历、分析匹配度。

## 能做什么

- **搜职位**：关键词 + 城市/行业/薪资/食宿/性质筛选，中文即可；0 条结果会自动换说法或放宽条件重试
- **看详情 & 投简历**：职位信息确认后一键投递，投后回执 + 会话内台账
- **简历管理**：完整度体检，基本信息/自我介绍/求职意向/工作经历/教育经历在线编辑，写后自动核验
- **智能推荐**：按简历画像分梯队推荐职位，8 维匹配度打分卡 + 最优方案
- **兜底引导**：暂不支持的操作指引到 App，不假装、不编造

## 目录结构

```
.
├── SKILL.md                        # Skill 入口（frontmatter + 能力总览）
├── references/
│   ├── agent-guide.md              # 完整执行指令（每会话必读）
│   ├── api.md                      # 工具参数 / 码表 / 易错字段
│   ├── scenarios.md                # 人群画像与高频表达应对
│   └── scoring.md                  # 匹配度打分维度
└── scripts/
    ├── veryeast-client.js          # MCP 客户端（调用平台接口）
    └── authorize.js                # 本地写入/清除 api_key
```

## 怎么开始

1. **登录授权**：首次使用会引导你授权，授权码只存本地设备（写入 `config.json`，已加入 `.gitignore`，不会被提交）
   ```bash
   node scripts/authorize.js '<api_key>'
   ```
2. **说需求**："帮我找工作""搜职位""投简历""改简历""推荐些职位"……即可开始

## 环境变量

| 变量 | 说明 |
|------|------|
| `VEAST_API_KEY` | 登录凭证（优先于 `config.json`） |
| `VEAST_MCP_URL` | MCP 端点（默认 `https://www.veryeast.cn/mcp`） |
| `VEAST_HOST_AGENT` | 宿主 agent 显式覆盖（可选，用于打点） |

## 安全说明

- 简历与登录凭证只存本地，`config.json` 权限 600，仅当前用户可读
- 投递为高风险写操作，带 `confirm:true` 前必须先取得用户明确同意
- 更多字段规范与码表见 [`references/api.md`](references/api.md)

## License

见仓库许可证（如有）。
