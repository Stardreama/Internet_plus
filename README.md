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
  - 使用 MySQL 数据库存储和管理结构化数据
  - 支持数据的持久化、查询与分析

- **业务逻辑服务层**

  - **库存服务：** 分析库存数据、计算周转率、提供优化建议
  - **市场预测服务：** 基于历史数据和 AI 模型进行价格趋势与需求预测
  - **风险评估服务：** 整合财务、信用及政策数据进行风险计算和预警

- **辅助工具**
  - 通用数据处理、格式转换及其他工具函数

## 项目目标

### 库存监测与升级板块

升级：例如：用户输入：库存明细（仓库里不同型号的产品的规格、数量、位置）、原材料库存数据、生产计划表 → 判断周转率、库存积压成本
输出：给出库存优化方案、库存健康度、能否及时周转、安全问题排查
监测：安装实时监控，智能监测 → 给出库存产品进出变化水平线、直观展示哪些产品库存还多，还少 → 帮助指导公司生产规划

### 市场预测板块

用户输入：历史销售数据、客户分类及采购模式（定期/不定期）（稳定客户群体数量我还在要数据）、销售区域的市场特点（有没有开拓例如农村电缆建设，新能源建设电缆需求，是否稳定还是价格变化幅度大）、行业发展趋势
输出：价格趋势预测、产品如何调整结构，产品需求区域分析

### 风险评估板块

用户输入：财务数据（现金流，应付预付账款，负债等信息）、政策法规变化（政府资金鼓励拨款资料还在问）、客户信用数据......
输出：客户信用风险评估、财务风险预警...

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
│ ├── **init**.py // 初始化应用包
│ ├── main.py // FastAPI 应用入口，启动 API 服务
│ ├── api/
│ │ ├── **init**.py
│ │ ├── inventory.py // 库存管理相关 API 接口
│ │ ├── market.py // 市场预测相关 API 接口
│ │ └── risk.py // 风险评估相关 API 接口
│ ├── models/
│ │ ├── **init**.py
│ │ └── models.py // 数据库模型定义（ORM 映射库存、销售、财务等数据）
│ ├── services/
│ │ ├── **init**.py
│ │ ├── inventory_service.py // 库存监控与优化业务逻辑
│ │ ├── market_service.py // 市场预测业务逻辑（数据处理与 AI 模型）
│ │ └── risk_service.py // 风险评估业务逻辑（风险计算与预警）
│ └── utils/
│ ├── **init**.py
│ └── helper.py // 辅助工具和通用函数
├── requirements.txt // Python 依赖列表
└── README.md // 后端项目说明与部署指南
```

## 数据库设置 (MySQL)

本项目使用 MySQL 数据库来存储和管理库存、销售、财务等结构化数据。建议按照以下步骤进行数据库配置：

1. **安装 MySQL 数据库服务器：**

根据系统环境安装并启动 MySQL 服务。

2. **创建数据库：**

通过命令行或图形化工具创建一个数据库，例如：

```sql
CREATE DATABASE cable_ai;
```

3. **配置数据库连接：**

在后端项目中（例如在配置文件或环境变量中）设置数据库连接字符串。示例连接字符串：

```ini
DATABASE_URL = "mysql+pymysql://username:password@localhost/cable_ai"
```

请根据实际的用户名、密码和服务器地址进行调整。

4. **数据库模型与表结构：**

- 利用 ORM（如 SQLAlchemy）根据 `backend/app/models/models.py` 中定义的模型自动创建数据表，或使用 Alembic 等工具进行数据库迁移管理。

- 相关数据表包括库存记录、销售数据、财务数据等，以支持项目各业务模块的数据存储与查询。

确保 MySQL 服务正常运行并且连接配置正确，以便后端应用能够顺利进行数据交互和持久化存储。

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
