## 拿来源

- Catalog: Elite20 C5-AG2 sample repos（samples/submitted_repos.md）
- Base repo: CreatorCrew — https://github.com/shageenthsandrakumar/high-five
- Captain of base repo: Tali

## 借鉴片段

- agents/pipeline.py：整体 Agent 编排逻辑（保留前 6 个 Agent 的串联结构）
- utils/search.py：Tavily 网页搜索接口
- app.py：Streamlit UI 框架

## 我新增/修改的部分

- agents/pipeline.py：
  - 将 run_audience_agent（第 1 个 Agent）升级为 autogen.beta.Agent 新写法（第 2 步）
  - 新增 run_title_agent 函数，实现第 7 个 Agent：Viral Title Generator，读取 content_plan 和 script 后生成 3 条爆款标题（第 3 步）
- agents/config.py：改为从环境变量读取 OPENAI_API_KEY、OPENAI_MODEL、OPENAI_API_BASE
- app.py：在 AGENT_MAP 中新增 'title' 配置项（第 7 个 Agent）；Dashboard 底部增加"推荐爆款标题"显示区
- .env.example：新建，列出全部环境变量及申请链接
- README.md：新增 5-Minute Quick Start 章节

## 备注

原项目硬编码了 OpenRouter + Google Gemini，我将其改为通过环境变量配置，当前使用 DeepSeek（deepseek-chat），API 地址 https://api.deepseek.com。运行时曾遇到 Authentication Fails 错误，根因是缺少 .env 文件导致 load_dotenv() 无法加载环境变量，创建 .env 后彻底解决。