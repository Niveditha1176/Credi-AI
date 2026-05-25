# Credi AI - Quick Start Guide

## In 3 Simple Steps

### Step 1: Prepare Your Data
Create a spreadsheet with these columns:
- `id` - Customer ID
- `name` - Customer Name  
- `income` - Monthly Income
- `cibil` - Credit Score (300-900)
- `limit` - Total Credit Limit
- `outstanding` - Current Balance
- `dpd` - Days Past Due
- `unsecured` - Number of Unsecured Loans

Save as `.xlsx`, `.xls`, or `.csv`

### Step 2: Upload File
- Open `index.html` in your browser
- Drag & drop your file OR click to browse
- System validates and lists all profiles

### Step 3: Analyze
- Click a profile from the list (or type ID)
- Click "Analyze Risk Profile"
- View risk score, probability, and approved limit

## Understanding Your Results

### Risk Levels
| Risk Level | PD Range | Approved Limit | Color |
|------------|----------|----------------|-------|
| 🟢 LOW | < 25% | 4.5x Income | Green |
| 🟡 MEDIUM | 25-60% | 1.5x Income | Orange |
| 🔴 HIGH | > 60% | ₹0 | Red |

### Key Metrics
- **PD (Default Probability)**: Likelihood of default (0-100%)
- **CUR (Credit Util Rate)**: % of credit limit used
- **z (Linear Scale)**: Raw WoE score
- **Approved Limit**: Max credit recommendation

##  Model Explanation

Uses logistic regression with Weight of Evidence (WoE):

1. **Feature Scoring**: CIBIL, CUR, DPD, Unsecured count each get a WoE score
2. **Linear Combination**: z = -0.15 + (weighted sum of WoE scores)
3. **Sigmoid Transformation**: PD = 1/(1 + e^z)
4. **Risk Decision**: Based on PD threshold

##  Sample Data

Use provided `sample_data.csv` to test:
- 10 pre-loaded customer profiles
- Mix of LOW, MEDIUM, and HIGH risk examples
- Ready to analyze immediately

##  Deployment

### Local
- Just open HTML file in any browser
- No installation required

### Online (Free Options)
1. **GitHub Pages**: Push files to repo, enable Pages
2. **Netlify**: Drag & drop HTML files
3. **Vercel**: Connect GitHub repo

## ❓ FAQ

**Q: Where is my data stored?**
A: Nowhere! All processing happens in your browser. Zero data transmission.

**Q: Can I use this for production?**
A: Yes! It's designed for enterprise use. Deploy on your infrastructure.

**Q: What if file upload fails?**
A: Check that file has all required columns. Try .csv format first.

**Q: Can I customize the model?**
A: Yes! Edit the `calculateWoE()` and `sigmoid()` functions in the HTML.



---

**Credi AI** - Banking-Grade Credit Risk Analysis | 100% Client-Side | No Dependencies
