# 🛒 Olist Smart Retail Data Warehouse & AI Ops Pipeline

A end-to-end data engineering project based on the Brazilian Olist E-commerce public dataset (Kaggle).

## 🎯 Project Overview
Simulating a real-world industrial data pipeline: from raw CSV ingestion → ETL cleaning → star-schema data warehouse → advanced SQL analytics → AI-powered business insights.

## 🗂️ Dataset
- Source: [Olist Brazilian E-Commerce Dataset (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- 9 relational tables: Orders, Customers, Products, Sellers, Payments, Reviews, Geolocation, etc.
- ~100,000 real orders from 2016–2018

## 🏗️ Project Phases

| Phase | Description | Status |
|-------|-------------|--------|
| Phase 1 | ETL & Data Cleaning (Pandas) | ✅ Complete |
| Phase 2 | Database Modeling & Ingestion (SQLite + SQLAlchemy) | ✅ Complete |
| Phase 3 | Advanced SQL Analytics (Window Functions, Views) | 🔄 In Progress |
| Phase 4 | AI Decision Layer (Dify / RAG) | 📅 Planned |

## 🔧 Tech Stack
- **Python** (Pandas, SQLAlchemy)
- **SQL** (SQLite, Window Functions)
- **Git / GitHub**
- **Dify** (AI Agent / RAG orchestration)

## 📊 Phase 1 Highlights — Data Cleaning
- Merged and profiled 9 raw CSV tables
- Converted 7 datetime columns from string to proper datetime type
- Translated Portuguese product category names to English via lookup merge
- Removed 610 "ghost products" (missing all attributes)
- Manually patched 13 products missing from translation table
- Removed 261,831 fully duplicate rows from geolocation table
- Final clean dataset: ~99K orders, 32K products, 3K sellers

## 📐 Phase 2 Highlights — Star Schema Design
```
fact_order_items (core fact table)
    ├── dim_orders
    ├── dim_customers
    ├── dim_products
    ├── dim_sellers
    ├── dim_payments
    ├── dim_reviews
    └── dim_geolocation
```
- Designed star schema with 1 fact table + 7 dimension tables
- Automated table creation and data ingestion via SQLAlchemy
- Total records loaded: ~550,000 rows across all tables

## 📁 Repository Structure
```
├── 01_data_cleaning.ipynb        # Phase 1: ETL & cleaning
├── 02_database_modeling.ipynb    # Phase 2: DB modeling & ingestion
├── .gitignore                    # Excludes raw data and DB files
└── README.md
```
