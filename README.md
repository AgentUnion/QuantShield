# QuantShield

> AI 驱动的 A 股风险分析系统 — 帮散户识别潜在风险，远离价值陷阱

[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-In%20Development-orange.svg)]()

---

## 项目简介

QuantShield 是一个开源的 A 股风险分析框架，融合多源数据、大语言模型（LLM）与量化风控技术，从财务异常、市场情绪、政策信号等多个维度自动识别个股与市场的潜在风险。

**核心理念**：不预测涨跌，只量化风险。

本项目同时记录了完整的开发过程，以视频形式发布在抖音，展示如何用 AI 技术解决散户投资中的实际痛点。

---

## 散户的痛点

| 痛点 | 传统应对 | QuantShield 方案 |
|------|----------|----------------|
| 财务造假难识别 | 逐条看财报 | LLM + 异常指标自动检测 |
| 研报太多看不完 | 只看结论 | RAG 架构自动摘要与风险提取 |
| 黑天鹅无预警 | 靠运气 | 多维信号提前预警 |
| 舆情反转太快 | 盯股吧 | 实时情感分析 Pipeline |
| 政策影响判断难 | 凭感觉 | 政策文本 NLP 量化解读 |

---

## 功能模块

```
QuantShield/
├── data/               # 多源数据采集与存储
│   ├── raw/            # 原始数据（K线、财报、公告、股吧舆情）
│   ├── processed/      # 清洗后的结构化数据
│   └── cache/          # 缓存层
│
├── analysis/           # 核心分析引擎
│   ├── llm/            # LLM 研报解读、公告风险提取（RAG）
│   ├── quant/          # 量化风控指标（VaR、CVaR、波动率）
│   ├── sentiment/      # 舆情情感分析
│   └── backtest/       # 历史信号回测验证
│
├── agents/             # AI 智能体
│   ├── trading/        # TradingAgents 多智能体博弈分析
│   ├── risk/           # 风险评估 Agent
│   └── report/         # 报告生成 Agent
│
├── report/             # 自动化报告生成（Markdown / PDF）
│
├── video/              # 视频自动化流水线
│   ├── script/         # LLM 生成视频脚本
│   ├── voice/          # TTS 语音合成（Fish Audio / Edge-TTS）
│   ├── visual/         # Manim 数据可视化动画
│   ├── compose/        # FFmpeg 自动合成
│   └── output/         # 成品视频
│
├── dashboard/          # Web 可视化看板
│   ├── backend/        # FastAPI 后端
│   └── frontend/       # React / Next.js 前端
│
├── publish/            # 抖音自动发布脚本
├── config/             # 配置文件（见 config.example.yaml）
├── tests/              # 单元测试 & 集成测试
├── scripts/            # 工具脚本
└── docs/               # 技术文档
```

---

## 技术栈

| 层级 | 技术选型 |
|------|----------|
| 数据采集 | AkShare · Tushare · Scrapy · Playwright |
| 数据存储 | PostgreSQL · ClickHouse · Redis |
| AI / LLM | OpenAI / Claude API · LangChain · LlamaIndex |
| 量化分析 | pandas · numpy · backtrader · empyrical · TA-Lib |
| 后端服务 | FastAPI · Celery · Docker |
| 前端看板 | React · Next.js · Recharts / Plotly |
| 视频合成 | Manim · Fish Audio · FFmpeg · MoviePy |
| 发布自动化 | Python · GitHub Actions · schedule |

---

## 快速开始

### 环境要求

- Python 3.11+
- PostgreSQL 15+（可选 ClickHouse）
- Redis 7+

### 安装

```bash
git clone https://github.com/yourname/QuantShield.git
cd QuantShield

python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate

pip install -r requirements.txt
```

### 配置

```bash
cp config/config.example.yaml config/config.yaml
# 编辑 config/config.yaml，填入 API Key 等配置
```

### 运行数据采集

```bash
# 采集 A 股日 K 线（近 5 年）
python scripts/fetch_kline.py --market A --years 5

# 采集上市公司公告
python scripts/fetch_announcements.py

# 启动舆情实时爬取
python scripts/fetch_sentiment.py --source eastmoney
```

---

## 开发路线图

- [x] 项目初始化 & 架构设计
- [ ] **P1** 数据基础层 — K线、财报、舆情数据采集入库
- [ ] **P2** AI 分析引擎 — LLM 研报解读 + TradingAgents 框架
- [ ] **P3** 量化风控指标 — VaR/CVaR、财务异常预警、回测
- [ ] **P4** 可视化 & 报告 — Web Dashboard + 自动报告
- [ ] **P5** 视频流水线 — AI 全自动生成财经视频
- [ ] **P6** 开放 API + 社区版发布

---

## 抖音内容系列

本项目同步录制开发过程，以"一个开发者如何用 AI 帮散户防踩雷"为主线发布系列视频：

| 期数 | 主题 |
|------|------|
| 第 1 期 | 项目发布：我为什么要做这个工具 |
| 第 2-3 期 | 数据采集实战：爬取A股全量数据的那些坑 |
| 第 4-6 期 | 让大模型读完 500 份研报，它发现了什么 |
| 第 7-9 期 | 量化风控模型能预测暴雷吗？回测结果揭晓 |
| 第 10-11 期 | 给散户做了个实时风险雷达，免费开放 |
| 第 12+ 期 | AI 全自动生成财经视频，我的工作流 |

---

## 免责声明

**本项目仅用于技术研究与学习目的。**

所有分析结果均为模型输出，不构成任何投资建议。股市有风险，投资需谨慎。请勿将本系统的任何输出作为买卖决策依据。

---

## License

[MIT License](LICENSE) © 2026 QuantShield
