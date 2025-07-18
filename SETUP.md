# MotionInsight Setup Guide

## Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/rosalinatorres888/human-activity-entropy.git
cd human-activity-entropy
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Analysis
```bash
# Main analysis notebook
jupyter notebook torres_rosalina_human_activity_analysis.ipynb

# Advanced visualizations
jupyter notebook plotly_advanced_visualizations.ipynb

# Portfolio visualizations
jupyter notebook portfolio_visualizations.ipynb
```

### 4. View Interactive Dashboard
Open `interactive_dashboard.html` in your web browser

## Project Structure
```
human-activity-entropy/
├── README.md                                    # Main project documentation
├── requirements.txt                             # Python dependencies
├── interactive_dashboard.html                   # Interactive Plotly dashboard
├── torres_rosalina_human_activity_analysis.ipynb # Main analysis
├── plotly_advanced_visualizations.ipynb        # Advanced visualizations
├── portfolio_visualizations.ipynb              # Portfolio-ready charts
├── data/                                       # Raw and processed data
├── docs/                                       # Detailed documentation
│   ├── methodology.md                          # Technical methodology
│   └── business_impact.md                      # Market analysis
├── images/                                     # Generated visualizations
├── results/                                    # Analysis outputs
└── src/                                        # Source code modules
```

## Key Results Summary

### Statistical Significance
- **Permutation Entropy**: p=0.022 (significant at α=0.05)
- **Complexity**: p<0.001 (highly significant)
- **Effect Sizes**: Complexity (η²=0.112), PE (η²=0.053)

### Optimal Parameters
- **Walking vs Running**: Dimension=5, Delay=2
- **Climbing Up vs Down**: Dimension=4, Delay=3

### Business Impact
- **Market Opportunity**: $187.9B total addressable market
- **Healthcare ROI**: 150-300% annual return
- **Accuracy Improvement**: 25-35% over existing methods

## Contact
- **Author**: Rosalina Torres
- **Email**: torres.ros@northeastern.edu
- **GitHub**: [@rosalinatorres888](https://github.com/rosalinatorres888)
