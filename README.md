
# AI-Assisted Automotive Procurement Optimization

## Overview

AI-Assisted Automotive Procurement Optimization is a data-driven procurement decision-support project designed to help companies make better supplier and purchasing decisions under real-world business constraints.

The system is designed to move beyond simple "lowest-price supplier" selection.

Instead, it aims to answer a more strategic question:

> How should procurement quantities be allocated across suppliers to achieve the best overall economic and operational outcome under cost, MOQ, lead-time, risk, capacity, and other business constraints?

The long-term vision is a risk-aware procurement decision-support system that can recommend:

- Which suppliers to use
- How much to purchase from each supplier
- Expected procurement cost
- Expected operational risk
- Constraint violations or limitations
- The reasoning behind the recommendation

---

## Project Roadmap

The project is being developed incrementally:

1. Excel Data Foundation
2. Python Data Processing & Cost Modeling
3. Mathematical Optimization
4. Risk-Aware Optimization
5. Machine Learning / AI Decision Support
6. API / MVP Development
7. ERP / SAP Integration

The project follows a practical principle:

Data → Validation → Cost Model → Optimization → Risk → ML/AI → Enterprise Integration

AI and machine learning will be introduced where they provide additional decision value beyond deterministic calculations and mathematical optimization.

---

# Phase 1 — Excel Data Foundation

The first phase established a structured procurement dataset containing supplier, pricing, logistics, MOQ, lead-time, risk, quality, and sourcing information.

The dataset includes supplier information such as:

- Supplier
- Supplier Country
- Manufacturer
- Part Number
- Product Description
- Unit Price
- Currency
- MOQ
- Order Quantity
- Lead Time
- Incoterms
- HS Code
- Shipping Cost
- Quality Certification
- Risk Information
- Supplier Score
- Source URL
- Data Date

The Excel model was used as the initial data foundation before moving the processing logic into Python.

---

# Phase 2 — Python Data Processing & Cost Modeling

## Objective

The objective of Phase 2 was to move beyond spreadsheet-based calculations and establish a structured Python data-processing layer for the future procurement decision-support system.

Python is used not only as a calculation engine, but also as a data validation and preparation layer before the data reaches the optimization engine.

---

## Implemented Capabilities

### 1. Excel Data Ingestion

Supplier data is loaded directly from the Excel workbook using Python and pandas.

The current implementation reads the procurement dataset from:

automotive_supplier_data.xlsx

---

### 2. Data Standardization

Column names are automatically standardized into a consistent internal format.

Examples:

- Unit Price Min → unit_price_min
- Shipping Cost Per Unit → shipping_cost_per_unit
- Lead Time Days → lead_time_days

The internal data model uses lowercase column names with underscores.

This creates a stable data structure for future calculations, optimization models, APIs, and ERP integration.

---

### 3. Data Inspection and Validation

The Python processing layer checks:

- Dataset dimensions
- Data types
- Missing values
- Procurement-related fields
- Calculation readiness

This provides an early validation layer before optimization.

---

### 4. Currency Normalization

Supplier prices can be provided in different currencies.

The current model normalizes unit prices into EUR using the corresponding exchange-rate data.

The resulting fields include:

- unit_price_min_eur
- unit_price_max_eur

This creates a common financial basis for supplier comparison and optimization.

---

### 5. Price Range Calculation

The system calculates the price range between minimum and maximum supplier prices.

This helps preserve pricing uncertainty instead of reducing the supplier's price immediately to a single value.

The resulting field is:

price_range

---

### 6. Shipping Cost per Unit

Total shipping cost is converted into a per-unit value based on the planned order quantity.

This allows logistics costs to be incorporated into the supplier cost model.

The resulting field is:

shipping_cost_per_unit

---

### 7. Landed Cost Modeling

The system calculates estimated landed procurement cost by combining:

- Normalized unit price
- Shipping cost per unit

The model currently produces:

- landed_cost_min
- landed_cost_max
- landed_cost_avg_eur

This creates a more realistic supplier comparison than using product price alone.

---

### 8. Automated MOQ Validation

MOQ is treated as a procurement constraint rather than simply another cost variable.

The system automatically validates whether the planned order quantity satisfies the supplier's minimum order quantity.

Logic:

order_quantity >= moq

Results are classified as:

- OK
- Below MOQ

This validation is performed programmatically rather than relying on manually entered spreadsheet indicators.

---

## Data Quality Principle

One of the key lessons from Phase 2 is that data quality is as important as the optimization algorithm itself.

A procurement dataset may contain valid raw numbers while still containing incorrect manually calculated indicators.

Therefore, the system uses Python to:

1. Load the data
2. Standardize the structure
3. Validate important fields
4. Recalculate derived values
5. Prepare reliable inputs for optimization

This reduces the risk of feeding inconsistent information into the optimization model.

---

# Current System Architecture

Supplier / Market Data
        ↓
Excel Data Foundation
        ↓
Python Data Processing
        ↓
Data Validation & Normalization
        ↓
Cost Modeling
        ↓
Optimization Engine
        ↓
Risk-Aware Procurement Decisions
        ↓
Future AI / ML Decision Support

The architecture is intentionally modular so that future components can be added without rebuilding the entire system.

---

# Phase 3 — Mathematical Optimization

The next development phase focuses on mathematical optimization.

Instead of selecting the supplier with the lowest individual price, the system will determine an optimal procurement allocation.

For example:

Supplier A → 55%
Supplier B → 30%
Supplier C → 15%

The exact allocation will depend on the input data and business constraints.

---

## Optimization Model

The first optimization model will define four main elements:

### Decision Variables

Decision variables represent how much should be purchased from each supplier.

For example:

x1 = quantity purchased from Supplier A
x2 = quantity purchased from Supplier B
x3 = quantity purchased from Supplier C

---

### Objective Function

The initial objective is to minimize total procurement cost.

A simplified representation is:

Minimize:

Total Procurement Cost
=
Product Cost
+
Shipping Cost
+
Other Applicable Procurement Costs

The model can later be extended to include risk and operational factors.

---

### Constraints

Potential constraints include:

- Total demand
- Supplier MOQ
- Supplier capacity
- Procurement budget
- Lead-time requirements
- Supplier diversification
- Risk limits
- Delivery requirements

This allows the optimization model to reflect real procurement decisions rather than a purely mathematical price comparison.

---

# Risk-Aware Optimization

A future version will incorporate supplier and market risk into the optimization process.

Potential risk factors include:

- Supplier reliability
- Delivery delays
- Country risk
- Supply disruption
- Quality performance
- Price volatility
- Capacity limitations
- Logistics uncertainty

The objective will eventually move from pure cost minimization toward a broader concept:

Minimize:

Expected Total Procurement Cost
+
Risk Penalty
+
Operational Penalty

The exact mathematical formulation will be developed after the initial optimization model is validated.

---

# Machine Learning / AI Roadmap

Machine learning and AI will be introduced after the deterministic optimization foundation is established.

Potential future capabilities include:

- Demand forecasting
- Lead-time prediction
- Supplier performance prediction
- Price trend prediction
- Risk prediction
- Disruption probability estimation
- Anomaly detection
- Dynamic supplier scoring
- Recommendation explanations

The purpose of AI is not to replace optimization unnecessarily.

Instead, AI should provide additional predictive information that improves the quality of procurement decisions.

---

# Decision-Support Vision

The long-term system is intended to become a procurement Decision Support System rather than a simple analytics notebook.

A future recommendation could look conceptually like:

Recommended Procurement Allocation

Supplier A: 55%
Supplier B: 30%
Supplier C: 15%

Expected Cost: €XXX

Risk Level: Medium

Key Reasons:

- Competitive landed cost
- Acceptable MOQ
- Better lead-time profile
- Supplier diversification
- Lower expected disruption exposure

The system should provide both the recommendation and the reasoning behind it.

---

# Business Objective

The business objective is to help procurement organizations make faster, more transparent, and more economically efficient sourcing decisions.

Potential benefits include:

- Lower total procurement cost
- Better supplier allocation
- Reduced supply disruption exposure
- Improved procurement transparency
- Better use of supplier capacity
- More consistent decision-making
- Reduced dependency on manual spreadsheet analysis
- Improved visibility into cost and risk trade-offs

---

# Competitive Differentiation

The project is not positioned as a generic supplier comparison tool.

The intended differentiation is the combination of:

- Procurement data processing
- Landed-cost modeling
- Mathematical optimization
- Supplier constraints
- Risk-aware decision-making
- Future predictive analytics
- Explainable recommendations
- Potential enterprise / ERP integration

The central concept is:

> Optimize the procurement decision, not simply the supplier price.

---

# Target Users

Potential target users include:

- Procurement departments
- Supply chain teams
- Manufacturing companies
- Automotive suppliers
- Electronics manufacturers
- Industrial companies
- Procurement consulting teams
- Companies managing multiple international suppliers

The architecture is intended to remain industry-flexible even though the current project uses automotive electronic components as its primary demonstration domain.

---

# Data Strategy

The project is designed to work with structured procurement and supplier data such as:

- Supplier prices
- Currency rates
- MOQ
- Order quantities
- Lead times
- Shipping costs
- Supplier performance
- Quality information
- Risk indicators
- Demand
- Capacity
- Historical purchasing data

Future versions may incorporate automatically refreshed external data sources and enterprise data.

---

# Technology Stack

Current and planned technologies include:

- Excel
- Python
- pandas
- Mathematical Optimization
- Machine Learning
- Artificial Intelligence
- APIs
- ERP / SAP Integration

The technology stack will evolve according to business requirements rather than technical complexity alone.

---

# Product Development Philosophy

The project follows a business-first development approach.

The objective is not to build a technically complex system simply because advanced technologies are available.

Instead, each technology should solve a specific business problem.

The development sequence therefore prioritizes:

Reliable Data
      ↓
Correct Calculations
      ↓
Optimization
      ↓
Risk Modeling
      ↓
Prediction
      ↓
AI-Assisted Decisions
      ↓
Enterprise Integration

This approach aims to create a system that can be evaluated based on measurable business value.

---

# Current Status

Completed:

- Excel Data Foundation
- Supplier Dataset Structure
- Data Standardization
- Python Data Ingestion
- Data Inspection
- Currency Normalization
- Price Range Calculation
- Shipping Cost per Unit
- Landed Cost Modeling
- Automated MOQ Validation

Next:

- Mathematical Optimization
- Procurement Allocation Model
- Constraint Modeling
- Optimization Validation

Future:

- Risk-Aware Optimization
- Machine Learning
- AI Decision Support
- API / MVP
- ERP / SAP Integration

---

# Long-Term Vision

The long-term vision is to develop an intelligent procurement decision-support platform capable of continuously evaluating supplier, cost, logistics, demand, and risk information and transforming that information into actionable procurement recommendations.

The system should ultimately answer three key questions:

Where should we buy?

How much should we buy?

Why is this the recommended decision?

The goal is to transform procurement from a largely manual supplier-selection process into a data-driven, constraint-aware, and explainable decision-making process.

---

# Project Status

The project is currently transitioning from the Python data-processing stage into the Mathematical Optimization stage.

The next milestone is to build and validate the first procurement allocation optimization model using the structured supplier dataset.

Excel Foundation          ✓
Python Processing         ✓
Cost Modeling             ✓
MOQ Validation            ✓
Mathematical Optimization →
Risk-Aware Optimization   →
ML / AI                   →
API / MVP                 →
ERP / SAP Integration     →
