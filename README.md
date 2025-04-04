# 电缆智联 AI: 市场感知与库存风险决策大脑

## 项目简介

**电缆智联 AI** 项目致力于为电缆行业提供智能化的库存管理、市场需求预测和供应链风险评估解决方案。通过数据采集、实时监控、AI 分析与决策支持，帮助电缆公司优化库存结构、提前预测市场需求以及有效应对供应链风险，从而提高运营效率并降低风险成本。

## 项目组成部分

项目分为前端和后端两大部分，各自负责不同的业务模块：

### 前端

- **库存监测与升级模块**

  - 显示库存实时监控数据
  - 展示库存产品进出变化趋势
  - 提供库存优化方案、库存健康度评估及周转效率反馈

- **市场预测模块**

  - 分析历史销售数据与客户采购模式
  - 预测价格趋势及市场需求
  - 提供产品结构优化建议及区域需求分析

- **风险评估模块**
  - 汇总客户信用、财务数据和政策变化信息
  - 评估供应链风险（包括交货准时性和产品质量）
  - 输出风险预警及应对策略

### 后端

- **API 接口层**

  - 基于 FastAPI 提供高性能 RESTful API
  - 分别为库存、市场预测和风险评估模块提供数据接口

- **数据模型与数据库交互**

  - 利用 ORM 定义库存、销售、财务等数据模型
  - 支持数据的存储、查询与分析

- **业务逻辑服务层**

  - **库存服务：** 分析库存数据、计算周转率、提供优化建议
  - **市场预测服务：** 基于历史数据和 AI 模型进行价格趋势与需求预测
  - **风险评估服务：** 整合财务、信用及政策数据进行风险计算和预警

- **辅助工具**
  - 通用数据处理、格式转换及其他工具函数

## 项目文件结构

### 前端

```markdown
frontend/
├── index.html // 主 HTML 入口文件
├── package.json // 项目依赖和脚本配置
├── vite.config.js // Vite 构建工具配置
└── src/
├── App.vue // 主应用组件
├── assets/
│ ├── base.css // 全局基础样式
│ ├── main.css // 主要样式文件
│ └── logo.svg // 应用 Logo
├── components/
│ ├── InventoryDashboard.vue // 库存监测与升级展示组件
│ ├── MarketForecast.vue // 市场预测展示组件
│ ├── RiskAssessment.vue // 风险评估展示组件
│ └── ... // 其他业务相关组件
└── main.js // 应用入口 JS 文件
```

### 后端

```markdown
backend/
├── app/
│ ├── __init__.py // 初始化应用包
│ ├── main.py // FastAPI 应用入口，启动 API 服务
│ ├── api/
│ │ ├── __init__.py
│ │ ├── inventory.py // 库存管理相关 API 接口
│ │ ├── market.py // 市场预测相关 API 接口
│ │ └── risk.py // 风险评估相关 API 接口
│ ├── models/
│ │ ├── __init__.py
│ │ └── models.py // 数据库模型定义
│ ├── services/
│ │ ├── __init__.py
│ │ ├── inventory_service.py // 库存监控与优化业务逻辑
│ │ ├── market_service.py // 市场预测业务逻辑（数据处理与 AI 模型）
│ │ └── risk_service.py // 风险评估业务逻辑（风险计算与预警）
│ └── utils/
│ ├── __init__.py
│ └── helper.py // 辅助工具和通用函数
├── requirements.txt // Python 依赖列表
└── README.md // 后端项目说明与部署指南
```

## 部署与运行

### 前端

#### 1.安装依赖：

```bash
cd frontend
npm install
```

#### 2.启动开发服务器：

```bash
npm run dev
```

### 后端

#### 1.创建虚拟环境并安装依赖:

```bash
cd backend
python -m venv venv
# Linux/MacOS
source venv/bin/activate
# Windows
venv\Scripts\activate
pip install -r requirements.txt
```

#### 2.启动 FastAPI 服务

```bash
uvicorn app.main:app --reload
```

## 功能说明

- 数据交互：
  前端通过 RESTful API 与后端进行数据交互，实时获取库存状态、市场数据和风险预警信息。

- 实时监控与数据展示：
  前端利用图表库（如 ECharts）直观展示库存动态、市场趋势和风险评估结果，辅助决策。

- AI 与数据分析：
  后端整合 AI 模型和数据处理算法，基于历史数据和实时数据进行市场预测及风险评估，为电缆公司提供数据驱动的决策支持。
