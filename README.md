# 🛒 Olist Smart Retail Data Warehouse & AI Ops Pipeline

An end-to-end data engineering project based on the Brazilian Olist E-commerce public dataset (Kaggle).

## 🎯 Project Overview
Simulating a real-world industrial data pipeline: raw CSV ingestion → ETL cleaning → star-schema data warehouse → advanced SQL analytics → AI-powered business insights.

## 🗂️ Dataset
- Source: [Olist Brazilian E-Commerce Dataset (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- 9 relational tables: Orders, Customers, Products, Sellers, Payments, Reviews, Geolocation
- ~100,000 real orders from 2016–2018

## 🏗️ Project Phases

| Phase | Description | Status |
|-------|-------------|--------|
| Phase 1 | ETL & Data Cleaning (Pandas) | ✅ Complete |
| Phase 2 | Database Modeling & Ingestion (SQLite + SQLAlchemy) | ✅ Complete |
| Phase 3 | Advanced SQL Analytics (Window Functions, Views) | ✅ Complete |
| Phase 4 | AI Decision Layer (Dify / RAG) | 📅 Planned |

## 🔧 Tech Stack
- **Python** (Pandas, SQLAlchemy)
- **SQL** (SQLite, Window Functions, Subqueries)
- **Git / GitHub**
- **Dify** (AI Agent / RAG — planned)

## 📊 Phase 1 — Data Cleaning Highlights
- Profiled 9 raw CSV tables (~1.5M total rows)
- Converted 7 datetime columns from string to datetime type
- Translated Portuguese product categories to English via lookup merge
- Removed 610 ghost products and 261,831 duplicate geolocation rows
- Manually patched 13 products missing from translation table

## 📐 Phase 2 — Star Schema Design
- 1 fact table (`fact_order_items`) + 7 dimension tables
- Automated ingestion via SQLAlchemy: 550,000+ rows loaded
- Verified row counts across all 8 tables post-ingestion

## 🔍 Phase 3 — SQL Business Analytics

**Analysis 1 — Platform Overview (delivered orders only)**
- 96,478 orders | 96,478 customers | 2,970 sellers
- Total revenue: R$13,221,498 | Avg item price: R$119.98
- Data spans: Sep 2016 – Aug 2018

**Analysis 2 — Category Revenue Ranking (RANK window function)**
- Top category: health_beauty (R$1.23M, 8,647 orders)
- Highest avg price: watches_gifts (R$199/item)
- Identified high-volume vs high-value category segments

**Analysis 3 — Seller Performance Grading (CASE WHEN + multi-table JOIN)**
- S: Star Seller — 28 sellers (avg 75 orders, score 4.6)
- A: Quality Seller — 521 sellers
- B: Average Seller — 2,230 sellers
- C: At-Risk Seller — 186 sellers (avg score 1.9, flagged for intervention)

**Analysis 4 — Repurchase Cycle Analysis (LAG window function)**
- 2,801 repeat customers identified
- 52% repurchased within 1 month (avg 5.4 days)
- Insight: 30-day post-purchase window is optimal for remarketing campaigns

## 📁 Repository Structure
```
├── 01_data_cleaning.ipynb        # Phase 1: ETL & cleaning
├── 02_database_modeling.ipynb    # Phase 2: Star schema & ingestion
├── 03_sql_analysis.ipynb         # Phase 3: Business SQL analytics
├── .gitignore
└── README.md
```
