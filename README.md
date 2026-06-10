# ZhiPath · 个性化资源生成与学习多智能体系统

> 2026 中国软件杯 A3 赛题参赛作品

## 项目简介

ZhiPath 是一个基于大模型的多智能体个性化学习系统。用户通过自然语言对话，系统自动完成：

- **学习者画像构建** — 对话式采集 7 维度画像，随学随新
- **技能差距诊断** — 3 个 Agent 串联分析目标与现状的差距
- **学习路径规划** — 自动生成并动态调整个性化学习路径
- **多模态资源生成** — 讲义、测验、闪卡、思维导图、试卷、代码实操、音频等 7+ 种资源
- **闭环评估** — 测验 → 反馈 → 薄弱点回写画像 → 路径重规划，持续迭代

## 技术栈

- **前端**: Next.js 15 + React 19 + TypeScript + Tailwind CSS
- **后端**: Python 3.12+ + FastAPI + LangChain
- **数据库**: PostgreSQL + pgvector
- **LLM**: DeepSeek / 通义千问 / 智谱 GLM / Moonshot / 科大讯飞星火
- **通信**: WebSocket 流式传输

## 快速启动

### 1. 环境准备

- Python 3.12+
- Node.js 18+
- PostgreSQL 17 + pgvector

### 2. 启动数据库

创建数据库并启用 pgvector：

```sql
CREATE DATABASE learnflow;
\c learnflow
CREATE EXTENSION vector;
```

### 3. 启动后端

```bash
cd LearnFlow/backend
python -m venv .venv
# Windows:
.venv\Scripts\activate
# Linux/Mac:
source .venv/bin/activate

pip install -r requirements.txt
# 复制并编辑 .env 填入你的 API KEY
cp ../../.env.example ../../.env
python main.py
```

后端运行在 http://localhost:8000

### 4. 启动前端

```bash
cd LearnFlow/frontend
npm install
npm run dev
```

前端运行在 http://localhost:3000

打开 http://localhost:3000/chat 即可开始使用。

## 项目结构

```text
LearnFlow/
├── backend/          # 后端 (FastAPI)
│   ├── api/          #   路由层
│   ├── capabilities/ #   能力处理器
│   ├── modules/      #   智能体模块
│   ├── services/     #   数据服务
│   └── runtime/      #   编排器 + 注册表
├── frontend/         # 前端 (Next.js)
│   ├── app/          #   页面路由
│   ├── components/   #   组件库
│   └── lib/          #   工具库
└── docs/             #   文档
```
