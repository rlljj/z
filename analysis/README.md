# CineMatch Deep Analysis Notebook

## Overview

This notebook contains a comprehensive deep analysis of the CineMatch recommendation system, including model evaluation, performance analysis, fairness testing, explainability, and production readiness assessment.

## Prerequisites

- **Python:** 3.9 or higher
- **RAM:** 8GB+ recommended
- **Storage:** 10GB+ free disk space
- **Execution Time:** 1-4 hours (depending on data mode and hardware)

## Setup Instructions

### 1. Install Dependencies

```bash
pip install -r ../requirements.txt
```

Or install packages individually:

```bash
pip install pandas numpy plotly scikit-learn optuna scipy matplotlib seaborn
```

**Note about scikit-surprise:** This package may fail to install on Python 3.11+ due to Cython compilation issues. The notebook will still run without it using alternative implementations.

Required packages:
- pandas
- numpy
- plotly
- scikit-learn
- optuna
- scipy
- matplotlib
- seaborn

Optional packages:
- scikit-surprise (may not work on Python 3.11+)

### 2. Verify Data Files Exist

Ensure the following files are in `data/ml-32m/`:
- `ratings.csv` (~2.3GB)
- `movies.csv` (~2MB)
- `tags.csv` (~20MB)
- `links.csv` (~2MB)

**Download:** [MovieLens 32M Dataset](https://grouplens.org/datasets/movielens/32m/)

### 3. Verify Output Directories

The following directories should exist (created automatically if missing):
```bash
analysis/outputs/
├── figures/
├── tables/
└── explanations/
```

## Running the Notebook

### ⚠️ CRITICAL: Execution Instructions

**This notebook MUST be run using the 'Run All' button.**

The notebook contains 150+ cells with sequential dependencies. Individual cell execution will fail with NameError.

### Method 1: VS Code (Recommended)

1. Open `CineMatch_Deep_Analysis.ipynb` in VS Code
2. Click **"Run All"** button in the toolbar
3. Wait for completion (1-4 hours)
4. Do NOT interrupt execution

### Method 2: Jupyter Notebook

```bash
cd analysis
jupyter notebook CineMatch_Deep_Analysis.ipynb
```

1. Click **"Run All"** in the Cell menu
2. Wait for completion
3. Monitor progress in cell outputs

### Method 3: Jupyter Lab

```bash
cd analysis
jupyter lab
```

1. Open `CineMatch_Deep_Analysis.ipynb`
2. Run → Run All Cells
3. Monitor execution progress

## Notebook Structure

The notebook is organized into the following phases:

1. **Phase 1:** Foundation & Setup - Data loading and environment configuration
2. **Phase 2:** EDA & Preprocessing - Exploratory data analysis
3. **Phase 3:** Model Training - SVD, KNN, Content-Based, and Hybrid models
4. **Phase 4:** Advanced Analysis - Cold-start, fairness, explainability, ablation studies
5. **Phase 5:** Finalization - QA, conclusions, and documentation

**Note:** The notebook file structure has results/QA cells first, then analysis cells. This is why you must run ALL cells - the analysis cells create the variables needed by the QA cells.

## Output Files

After successful execution, the following files will be generated:

### Visualizations (`outputs/figures/`)
- Interactive Plotly HTML charts
- Performance comparison plots
- Fairness distribution charts
- Explainability visualizations

### Tables (`outputs/tables/`)
- Model comparison results (CSV)
- Performance metrics summaries
- Statistical analysis tables

### Explanations (`outputs/explanations/`)
- Individual recommendation explanations (HTML)
- Feature importance reports

### Reports (`outputs/`)
- Final conclusions (Markdown)
- Bibliography and references
- Quality assurance reports

## Troubleshooting

### NameError: variable not defined

**Cause:** Cells run out of order or incompletely

**Solution:** Run ALL cells using "Run All" button

### Memory Error

**Cause:** Insufficient RAM

**Solutions:**
- Close other applications
- Use smaller data mode (if available)
- Increase system RAM to 8GB+

### Long Execution Time

**Status:** Normal behavior

**Details:**
- Full execution: 1-4 hours
- Model training: 30-120 minutes
- Optuna optimization: 20-60 minutes

Do not interrupt - progress indicators will show status.

### Import Errors

**Cause:** Missing Python packages

**Solution:**
```bash
pip install pandas numpy plotly scikit-learn optuna scipy matplotlib seaborn
```

**scikit-surprise installation issues:**
- Known problem with Python 3.11+ due to Cython compilation
- Error: "Invalid type" in co_clustering.pyx
- Solution: Skip this package - notebook will work without it
- Alternative: Use Python 3.9 or 3.10 if scikit-surprise is required

The notebook includes a dependency verification cell that will fail fast if critical packages are missing.

### File Not Found Errors

**Cause:** Missing data files or output directories

**Solutions:**
1. Download MovieLens 32M dataset
2. Extract to `data/ml-32m/`
3. Verify output directories exist

## Performance Optimization

### Execution Time Reduction

- Use SSD for data storage
- Close unnecessary applications
- Use smaller dataset for testing (not included by default)

### Memory Usage

- Expected: 4-8GB during execution
- Peak: Up to 12GB during model training
- Monitor with Task Manager / Activity Monitor

## Quality Assurance

The notebook includes comprehensive QA checks:

- ✅ Code quality validation
- ✅ Documentation completeness
- ✅ Visualization integrity
- ✅ Output validation
- ✅ Reproducibility verification
- ✅ Statistical significance testing

All QA cells must pass for production readiness.

## Expected Results

After successful execution, you should see:

- **Model Performance:** RMSE < 0.9, Precision@10 > 0.3
- **Hybrid Model:** Best overall performance
- **Fairness:** Gini coefficient < 0.6
- **Explainability:** Feature importance for all recommendations
- **Production Readiness:** All QA checks passed

## Citation

If you use this analysis in your research, please cite:

```bibtex
@misc{cinematch_analysis,
  title={CineMatch Deep Analysis: Comprehensive Evaluation of Hybrid Recommendation Systems},
  author={CineMatch Team},
  year={2025},
  note={Analysis of MovieLens 32M dataset}
}
```

## Support

For issues or questions:

1. Check this README's troubleshooting section
2. Review notebook execution instructions at top of notebook
3. Verify all prerequisites are met
4. Ensure "Run All" was used (not individual cells)

## License

This analysis notebook is part of the CineMatch project. Refer to the main project LICENSE file for details.

## Acknowledgments

- MovieLens dataset: GroupLens Research (University of Minnesota)
- Surprise library: Nicolas Hug
- Scikit-learn: Python ML community
- Optuna: Preferred Networks, Inc.

---

**Last Updated:** November 2025  
**Notebook Version:** 2.1  
**Status:** Production Ready ✅
