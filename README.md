# Credit Risk Analyzer - Fully Scalable Platform

A modern, production-ready credit risk analysis system that accepts user-provided data files and performs real-time logistic regression-based risk scoring with transparent model execution traces.

## Features

### File Import System
- **Drag & Drop Upload**: Simply drag your data file onto the upload area
- **Multiple Format Support**: Import from .xlsx, .xls, or .csv files
- **Quick Selection**: Click any profile to instantly load it for analysis

###  Advanced Credit Risk Analysis
- **Logistic Regression Model**: Industry-standard WoE (Weight of Evidence) scoring
- **Transparent Calculations**: Complete step-by-step model execution trace
- **Real-Time Processing**: Instant risk assessment for each profile
- **Multi-Factor Analysis**:
  - CIBIL Score assessment
  - Credit Utilization Rate (CUR) evaluation
  - Days Past Due (DPD) tracking
  - Unsecured loan count analysis

###  Visual Dashboard
- **Centered Sigmoid Graph**: Beautiful probability distribution visualization
- **Color-Coded Risk Levels**: 
  - 🟢 Low Risk (PD < 25%)
  - 🟡 Medium Risk (25% ≤ PD ≤ 60%)
  - 🔴 High Risk (PD > 60%)
- **Pipeline Flowchart**: Visual representation of model execution flow
- **Ledger Extract**: Detailed metrics and approved financing cap
- **Model Compilation Log**: Complete calculation breakdown

## Required Data Format

Your data file must contain the following columns:

| Column | Type | Description |
|--------|------|-------------|
| id | Integer | Unique customer identifier |
| name | String | Customer full name |
| income | Number | Monthly income (in currency units) |
| cibil | Integer | CIBIL/Credit score (300-900) |
| limit | Number | Total credit limit |
| outstanding | Number | Current outstanding balance |
| dpd | Integer | Days Past Due (0-180+) |
| unsecured | Integer | Number of unsecured loans |


##  How to Use

### 1. **Import Your Data**
   - Click the "Import Your Data" section or drag your file
   - Select your .csv, .xlsx, or .xls file
   - System validates and loads all profiles
   - View available profiles in the list

### 2. **Select a Profile**
   - Click on any profile from the loaded list, OR
   - Type the Profile ID in the input field
   - Profile ID will auto-complete using the datalist

### 3. **Run Analysis**
   - Click "Analyze Risk Profile" button
   - System computes:
     - WoE features for each factor
     - Linear scale sum (z-score)
     - Sigmoid probability (Default Probability)
     - Risk classification
     - Approved financing cap

### 4. **Review Results**
   - **Sigmoid Graph**: Shows PD on probability distribution curve
   - **Risk Status Badge**: Visual risk category indicator
   - **Ledger Extract**: Key metrics including:
     - Credit Utilization Rate (CUR)
     - Probability of Default (PD)
     - Linear Scale Sum (z)
     - Approved Financing Cap
   - **Model Log**: Complete step-by-step calculations

## Technical Details

### Risk Scoring Model
The system uses logistic regression with Weight of Evidence (WoE) encoding:

```
z = -0.15 + (1.25 * WoE_CIBIL) + (1.10 * WoE_CUR) + (1.45 * WoE_DPD) + (0.85 * WoE_UNSECURED)
PD = 1 / (1 + e^z)
```

### WoE Bins
- **CIBIL**: ≥750 (0.85), 650-749 (0.15), <650 (-0.95)
- **CUR**: ≤30% (0.75), 30-60% (0.10), >60% (-0.80)
- **DPD**: 0 days (0.90), 1 day (-0.20), 2+ days (-1.10)
- **Unsecured**: ≤1 loan (0.40), >1 loan (-0.65)

### Approved Limit Calculation
```
Approved Limit = Income × Risk Factor × (1 - PD)
```
- Low Risk: Factor = 4.5
- Medium Risk: Factor = 1.5
- High Risk: Factor = 0



##  Dependencies

- **SheetJS (XLSX)**: For Excel file parsing
- **Vanilla JavaScript**: No other frameworks required
- **Modern CSS**: For responsive design

##  Use Cases

1. **Banks & Financial Institutions**: Automated credit scoring
2. **Lending Platforms**: Quick risk assessment for loan applications
3. **Credit Analysis Tools**: Internal risk management systems
4. **Financial Training**: Educational demo for credit models
5. **Portfolio Management**: Batch analysis of customer portfolios



##  Data Privacy

- ✅ No data transmission to servers
- ✅ No cookies or tracking
- ✅ 100% client-side processing
- ✅ Safe for sensitive financial data



## Example Workflow

```
1. Export customer data from your CRM → CSV/Excel
2. Upload file to Credi AI
3. Select customer profiles
4. Get instant risk scores
5. Make informed lending decisions
```

---

**Built with FinTech Grade UI** | Modern Dashboard | Transparent Model Logic
