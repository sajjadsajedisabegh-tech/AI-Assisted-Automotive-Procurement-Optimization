# AI-Assisted-Automative-Procurement-Optimization
AI-Assisted Procurement decision-support model for automotive parts sourcing 
# AI-Assisted Automotive Procurement Optimization

AI-assisted procurement decision-support model for automotive parts sourcing.

## Project Overview

This project explores how data analysis, procurement rules, and optimization techniques can support better supplier selection and purchasing decisions in automotive parts procurement.

The project starts with an Excel-based procurement model and is planned to evolve into a Python-based optimization and AI-assisted decision-support system.

The current version focuses on building a structured procurement dataset and calculating key purchasing indicators such as:

- MOQ compliance
- EUR-normalized prices
- Price range
- Shipping cost per unit
- Landed cost
- Supplier/source risk

## Business Problem

Automotive procurement decisions often involve multiple suppliers, different currencies, minimum order quantities, shipping costs, lead times, and varying levels of supplier risk.

Looking only at unit price can lead to poor purchasing decisions.

For example, a supplier with a lower unit price may become more expensive after shipping costs, currency conversion, or other procurement constraints are considered.

This project aims to provide a more structured way to compare sourcing options.

## Current Model

The current Excel model contains procurement data including:

- Part Number
- Product Description
- Manufacturer
- Supplier
- Supplier Country
- Unit Price Range
- Currency
- MOQ
- Order Quantity
- Lead Time
- Incoterms
- HS Code
- Shipping Cost
- Quality Certification
- Source
- Risk Score
- EUR Exchange Rate

The model then derives:

- MOQ Check
- Minimum Price in EUR
- Maximum Price in EUR
- Price Range
- Shipping Cost per Unit
- Landed Cost Minimum
- Landed Cost Maximum
- Average Landed Cost

## Procurement Logic

The current model follows a simple procurement decision flow:

Order Quantity
→ MOQ Check
→ Price Normalization
→ Shipping Cost Allocation
→ Landed Cost Calculation
→ Risk Assessment

A supplier that does not meet the required MOQ is treated as infeasible for the selected order quantity.

Landed cost is calculated by combining the normalized product price with the allocated shipping cost per unit.

## Risk Assessment

The current model includes a source-based risk score.

The score is an initial procurement assumption rather than a statistically validated risk model.

Established distribution sources are treated as lower-risk sources, while marketplace-based sourcing is assigned a higher preliminary risk due to greater dependence on individual suppliers and verification.

This scoring methodology can be improved in future versions by incorporating additional supplier-level data such as:

- Supplier history
- Quality performance
- Delivery reliability
- Certification
- Country risk
- Payment terms
- Historical order performance

## Why Excel First?

Excel was selected as the first implementation environment because it is widely used in procurement and supply-chain operations.

The goal of the first stage is to validate the business logic before moving to a more automated analytical system.

The Excel model therefore serves as the first Minimum Viable Product (MVP) of the project.

## Planned Python Development

The next stage will move the analytical workflow into Python.

Planned components include:

- Data cleaning and validation
- Automated currency normalization
- Cost normalization
- Supplier scoring
- Supplier ranking
- Constraint handling
- Optimization
- Sensitivity analysis
- Scenario analysis
- Visualization

Python will also make it possible to test different procurement scenarios and compare alternative supplier combinations programmatically.

## AI-Assisted Decision Support

The long-term goal is to develop an AI-assisted procurement decision-support layer.

The system is not intended to replace procurement professionals.

Instead, it is designed to help procurement teams:

- Compare suppliers
- Identify cost drivers
- Detect procurement risks
- Evaluate sourcing scenarios
- Generate purchasing recommendations
- Explain the factors behind a recommendation

The AI layer will be developed after the underlying procurement and optimization logic has been validated.

## Current Limitations

The current version is an early-stage procurement model.

Important limitations include:

- Limited sample data
- Preliminary risk assumptions
- No historical supplier performance dataset
- No statistical validation of risk scores
- No automated supplier optimization yet
- No machine-learning model in the current Excel version

These limitations are intentionally documented so that future development can be measured against a clear baseline.

## Roadmap

### Phase 1 — Excel MVP
- [x] Procurement dataset
- [x] MOQ validation
- [x] Currency normalization
- [x] Price range calculation
- [x] Shipping cost per unit
- [x] Landed cost calculation
- [x] Preliminary source risk scoring

### Phase 2 — Python Analytics
- [ ] Data cleaning
- [ ] Automated normalization
- [ ] Supplier scoring
- [ ] Supplier ranking
- [ ] Scenario analysis
- [ ] Visualization

### Phase 3 — Optimization
- [ ] Procurement constraints
- [ ] Cost optimization
- [ ] Supplier allocation
- [ ] Sensitivity analysis
- [ ] What-if scenarios

### Phase 4 — AI-Assisted Procurement
- [ ] Recommendation engine
- [ ] Natural-language procurement analysis
- [ ] Explainable recommendations
- [ ] Automated procurement insights

## Technologies

Current:

- Microsoft Excel
- Procurement / International Trade concepts

Planned:

- Python
- Pandas
- NumPy
- Optimization libraries
- Data visualization
- Machine Learning / AI

## Project Status

**Current status: Excel MVP completed.**

The next development stage is the Python analytics and optimization layer.

## Author

Developed as a personal portfolio project focused on the intersection of:

- Procurement
- International Trade
- Data Analytics
- Optimization
- AI-assisted Decision Support
