# LangGraph 智能旅行助手

基于 LangGraph 和 LangChain 构建的智能旅行行程规划系统，支持多 Agent 协作、流式响应、预算控制和地图可视化。

## 功能特性

### 核心功能

- **智能行程规划**: 根据目的地、日期、偏好自动生成详细行程
- **预算控制**: 支持设置预算范围，AI 会根据预算合理安排景点、餐饮和住宿
- **实时进度反馈**: SSE 流式响应，实时展示 Agent 执行进度
- **地图可视化**: 高德地图集成，展示景点位置和路线
- **多轮对话**: 支持自然语言交互，逐步完善行程需求
- **行程持久化**: 每次规划结果自动保存为 JSON 文件

### 技术亮点

- **多 LLM 支持**: DeepSeek、阿里云百炼，可灵活切换
- **高德地图 API**: POI 搜索、天气查询、酒店推荐、地理编码
- **类型安全**: 后端 Pydantic + 前端 TypeScript 全栈类型校验
- **响应式 UI**: Vue 3 + Element Plus，支持移动端

## 项目结构

```
langgraph-trip-planner/
├── backend/                    # 后端服务
│   ├── app/
│   │   ├── api/               # API 路由
│   │   │   ├── routes/
│   │   │   │   ├── trip.py    # 行程规划接口
│   │   │   │   ├── chat.py    # 多轮对话接口
│   │   │   │   └── map.py     # 地图服务接口
│   │   │   └── main.py        # FastAPI 入口
│   │   ├── core/              # 核心配置
│   │   │   ├── config.py      # 环境配置
│   │   │   └── llm.py         # LLM 工厂
│   │   ├── models/
│   │   │   └── schemas.py     # 数据模型
│   │   ├── services/
│   │   │   └── amap_service.py # 高德地图服务
│   │   └── saved_results/     # 行程结果存储
│   ├── requirements.txt
│   └── .env                   # 环境变量 (需配置)
│
└── frontend/                   # 前端应用
    ├── src/
    │   ├── views/
    │   │   ├── Home.vue       # 表单模式主页
    │   │   ├── Result.vue     # 结果展示页
    │   │   └── Chat.vue       # 对话模式页
    │   ├── stores/            # Pinia 状态管理
    │   ├── services/          # API 服务
    │   └── types/             # TypeScript 类型
    ├── package.json
    └── .env                   # 环境变量 (需配置)
```