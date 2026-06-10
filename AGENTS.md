# SoftwareCup-A3 项目

软件杯比赛项目，核心产品是 **LearnFlow** — 一个基于多智能体的个性化学习资源生成系统。

## 项目结构

```
SoftwareCup-A3/
├── LearnFlow/          # 主项目（开发中）
├── DeepTutor-main/     # 参考项目：Lumino/DeepTutor（LlamaIndex RAG + 多渠道 AI 导师）
├── edu-agent-master/   # 参考项目：EduAgent（Azure 全栈 + LangGraph）
└── gen-mentor-main/    # 参考项目：GenMentor（WWW 2025 论文，多智能体框架）
```

## LearnFlow 主项目

### 技术栈
- **前端**: Next.js 15 (App Router), React 19, TypeScript, Tailwind CSS
- **后端**: Python 3.12+, FastAPI, LangChain, DeepSeek LLM (deepseek-chat)
- **数据库**: PostgreSQL + pgvector (Docker), embedding: all-mpnet-base-v2
- **通信**: WebSocket 流式传输

### 核心架构
- Orchestrator 模式 + Capability Registry
- ChatOrchestrator 负责路由消息到对应模块
- StreamBus 处理流式事件
- 服务层: Memory, SessionStore, RAG Pipeline

### 5 个 Agent 模块
1. **Chat Tutor** (`modules/chat_tutor/`) — 通用 AI 辅导聊天（最完整，已接入）
2. **Skill Gap Analysis** (`modules/skill_gap/`) — 技能差距分析（3 个子 agent）
3. **Learner Profile** (`modules/learner_profile/`) — 自适应学习者画像
4. **Learning Path** (`modules/learning_path/`) — 学习路径规划
5. **Resource Generation** (`modules/resource_gen/`) — Quiz / Flashcard / Mindmap 生成

### 当前开发状态（截至 2026-05-08）
- 基础设施已搭建: orchestrator, registry, streaming bus, event system, LLM factory, RAG pipeline
- Chat Tutor 已可端到端运行（流式对话）
- 前端已有基础 Chat UI（ChatPanel, ChatInput, MessageBubble）+ WebSocket client
- 其余 4 个模块已 scaffold（prompt + schema），尚未接入 capability registry

### 启动方式
- 前端: `cd LearnFlow/frontend && npm run dev`（端口 3000）
- 后端: `cd LearnFlow/backend`，需要 Python 虚拟环境
- 数据库: Docker PostgreSQL + pgvector
