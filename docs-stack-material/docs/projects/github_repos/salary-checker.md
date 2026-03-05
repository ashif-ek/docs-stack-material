# Salary Reality Checker – AI-Powered Salary Insights

> **An enterprise-grade, FAANG-style salary analytics platform offering automated market percentiles, predictive machine learning, and intelligent fuzzy matching for imperfect data.**

Built with state-of-the-art technologies including **FastAPI**, **PostgreSQL**, **scikit-learn**, and a dynamic **React** interface, this platform delivers precise, data-driven compensation intelligence.

[View Repository on GitHub](https://github.com/ashif-ek/salary-checker){ .md-button .md-button--primary }

---

## 🚀 Outstanding Features

### 🔹 Intelligent Percentile Engine
Dynamically calculates real-time market percentiles to provide a clear distribution overview:
- **P10 & P25**: Lower-bound market rates.
- **P50 (Median)**: Standard baseline compensation.
- **P75 & P90**: Top-tier and elite market ranges.

### 🔹 AI-Driven Fuzzy Matching
Implements advanced string-matching heuristics to auto-correct imperfect user input.
- Example: Transforms `py devloper` or `sofware eng` into perfectly matched professional titles, ensuring database integrity and accurate querying.

### 🔹 Machine Learning Salary Prediction
Utilizes robust ML models when exact database entries are absent.
- Automatically trains **Linear Regression models** on the fly.
- Forecasts salaries based on multi-variable experience trends.

### 🔹 Comprehensive Admin Tools
Enables seamless dataset operations:
- Direct CSV upload capabilities for thousands of records.
- Optimized bulk insertion routines straight into the PostgreSQL data warehouse.

### 🔹 Premium Modern UI
A responsive, high-performance interface built with React:
- **Interactive Visualizations**: Powered by Recharts for animated, dynamic data sets.
- **Polished Experience**: Features shimmer loading states, auto-suggest dropdowns, Framer Motion transitions, and native Dark/Light mode support.

---

## 🏗️ Technical Architecture

### Backend Infrastructure
- **FastAPI**: Blazing-fast routing and API endpoints.
- **SQLAlchemy & PostgreSQL**: Scalable ORM and robust relational database management.
- **scikit-learn & RapidFuzz**: Powering the core ML analytics and string-matching logic.

### Frontend Application
- **React (Vite)**: Optimized build and rapid Hot Module Replacement (HMR).
- **TailwindCSS**: Utility-first, consistently designed UI components.
- **Recharts & Framer Motion**: Declarative charts and fluid animations.

---

## 📡 Core API Integration

Exposes comprehensive RESTful endpoints for seamless integration:

- **Record Management:**
  - `POST /salary/add` - Append individual compensation data.
  - `POST /salary/bulk` - Execute high-speed bulk CSV ingestions.
- **Analytics & Predictions:**
  - `GET /salary/insights?job_role=&city=&experience=` - Retrieve percentile distributions.
  - `GET /salary/predict?job_role=&city=&experience=` - Fetch ML-driven predictions for custom queries.

---

## 🔧 Getting Started

### 1. Backend Setup
```bash
cd backend
pip install -r requirements.txt
uvicorn app.main:app --reload
```

### 2. Frontend Setup
```bash
cd frontend
npm install
npm run dev
```

Navigate to `http://localhost:5173` to experience the FAANG-grade UI and underlying analytics engine.
