# 🏦 Zulo_Bank: Financial Data Warehouse Project

Zulo_Bank is a stack data engineering and analytics pipeline built for a fictional banking system. It transforms raw banking data into a fully normalized, analytics-ready **Data Warehouse**, structured around a clean **star schema**.

---

## 📌 Project Overview

This project delivers a complete banking data model and warehouse setup, including:

✅ Raw data normalization using 3NF principles  
✅ Star schema design with fact & dimension tables  
✅ PostgreSQL database integration  
✅ CSV-based transformation and staging  

---

## ⚙️ Technologies Used

 ⏺ Python (`pandas`, `psycopg2`) — ETL and automation  
 ⏺ PostgreSQL — relational database storage  
 ⏺ CSV — intermediate data staging  
 ⏺ SQL — schema definition and querying  

---

## 🔄 Full Workflow Breakdown

### 1. Normalize Raw Banking Tables (3NF)

- Created atomic versions of key entities:
  - `customer`.
  - `account` (linked with `OpeningDate_ID`).
  - `transaction` (linked with `TransactionDate_ID`).
  - `loan` (linked with `StartDate_ID` and `EndDate_ID`).

- Ensured data integrity by breaking composite fields and removing redundancies.

---

### 2. Generate a Central Date Dimension

- Created `date_dim` table with:
  - `date_id`.
  - `day`, `month`, `year`.

- Used it to replace raw date fields across other tables, enabling time-based slicing and aggregation.

---

### 3. Build Dimensions and Facts

**🧱 Dimension Tables:**
- `customer_dim` — atomic customer attributes.  
- `account_dim` — account type and metadata.  
- `transaction_dim` — transaction types and triggers.  
- `loan_dim` — loan product details.  
- `date_dim` — unified time dimension.

**📊 Fact Tables:**
- `transaction_fact_table` — records transactions with keys.  
- `loan_fact_table` — records loan events and balances.

Tables were designed to support aggregation, filtering, and joins across dimensions.

---

### 4. PostgreSQL Database Setup

- Built a reusable database connection function with `psycopg2`.  
- Created tables programmatically if they didn’t exist.  
- Used SQL `INSERT INTO` statements with placeholders (safe value passing).  
- Validated the integrity of references with foreign keys.  

---

## 📄 Results & Final Verification

✅ Normalized all tables to 3NF.  
✅ Populated dimensions and fact tables successfully.  
✅ Queried PostgreSQL with joins and filters across the star schema.  
✅ Database ready for live analytics or BI integration.  

---

## 📝 Notes

 ⏺ Used safe SQL statements with input substitution to prevent injection  
 ⏺ Dates were linked using generated `date_id` for clean time slicing  
 ⏺ Database schema supports scalable analytics and fast querying  
 ⏺ Designed with modular functions to support ongoing updates and migrations
 
