# 🛒 Olist Smart Retail Data Warehouse & AI Query Layer

An end-to-end data engineering project with natural language query capability, based on the Brazilian Olist E-commerce public dataset (Kaggle).

## 🎯 Project Overview
A complete data pipeline: raw CSV ingestion → ETL cleaning → star-schema data warehouse → advanced SQL analytics → **AI-powered natural language querying**.

Users can ask questions in plain English/Chinese and get instant data-driven answers powered by LLM + Text-to-SQL.

## 🗂️ Dataset
- Source: [Olist Brazilian E-Commerce Dataset (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- 9 relational tables: Orders, Customers, Products, Sellers, Payments, Reviews, Geolocation
- ~100,000 real orders from 2016–2018

## 🏗️ Architecture
```
Raw CSV (9 tables, ~1.5M rows)
    ↓ Phase 1: ETL & Cleaning (Pandas)
Cleaned DataFrames
    ↓ Phase 2: Modeling & Ingestion (SQLAlchemy)
SQLite Data Warehouse (Star Schema, 550K+ rows)
    ↓ Phase 3: SQL Analytics (Window Functions)
Business Insights
    ↓ Phase 4: AI Query Layer (DeepSeek-V3 + Text-to-SQL)
Natural Language Interface
```

## 🔧 Tech Stack
- **Python** (Pandas, SQLAlchemy, OpenAI SDK)
- **SQL** (SQLite, Window Functions, Multi-table JOINs)
- **LLM** (DeepSeek-V3 via SiliconFlow API)
- **Git / GitHub**

## 📋 Project Phases

| Phase | Description | Status |
|-------|-------------|--------|
| Phase 1 | ETL & Data Cleaning (Pandas) | ✅ Complete |
| Phase 2 | Database Modeling & Ingestion (SQLite + SQLAlchemy) | ✅ Complete |
| Phase 3 | Advanced SQL Analytics (Window Functions, Views) | ✅ Complete |
| Phase 4 | AI Query Layer (Text-to-SQL + LLM) | ✅ Complete |

## 📊 Phase 1 — Data Cleaning Highlights
- Profiled 9 raw CSV tables (~1.5M total rows)
- Converted 7 datetime columns from string to datetime type
- Translated Portuguese product categories to English via lookup merge
- Removed 610 ghost products and 261,831 duplicate geolocation rows
- Manually patched 13 products missing from translation table

## 📐 Phase 2 — Star Schema Design
- 1 fact table (fact_order_items) + 7 dimension tables
- Automated ingestion via SQLAlchemy: 550,000+ rows loaded
- Verified row counts across all 8 tables post-ingestion

## 🔍 Phase 3 — SQL Business Analytics

| Analysis | Method | Key Finding |
|----------|--------|-------------|
| Platform Overview | Aggregation | 96K orders, R$13.2M revenue |
| Category Revenue Ranking | RANK() window function | health_beauty #1 at R$1.23M |
| Seller Performance Grading | CASE WHEN + multi-JOIN | 28 Star Sellers identified |
| Repurchase Cycle Analysis | LAG() window function | 52% repurchase within 30 days |

## 🤖 Phase 4 — AI Query Layer (Text-to-SQL)
Natural language querying powered by DeepSeek-V3. The system automatically:
1. Reads the full database schema
2. Translates user questions into SQL via LLM
3. Executes SQL against the SQLite warehouse
4. Returns results with business interpretation

**Example queries:**
> "哪个商品类别的销售额最高？" → health_beauty, R$1,233,131.72

> "评分最低的商品品类是什么？" → security_and_services, avg score 2.5/5

## 📁 Repository Structure
```
├── 01_data_cleaning.ipynb        # Phase 1: ETL & cleaning
├── 02_database_modeling.ipynb    # Phase 2: Star schema & ingestion
├── 03_sql_analysis.ipynb         # Phase 3: Business SQL analytics
├── 04_ai_query_layer.ipynb       # Phase 4: Text-to-SQL AI layer
├── .gitignore
└── README.md
```

## 🚀 Quick Start
```bash
pip install pandas sqlalchemy openai
# Set your SiliconFlow API key in 04_ai_query_layer.ipynb
# Run all cells and start querying in natural language
```
