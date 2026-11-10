# Cartier Watch Auctions on eBay: What Drives the Final Price?

I used the **CRISP-DM** process to study how auction settings affect the final selling price of Cartier watches on eBay.

## Project question

**Topic:** Optimising eBay auction strategies to maximise the final selling prices of Cartier watches.

**Research questions**
1. How does the **opening bid** affect the final selling price?
2. Do **longer auctions** achieve higher final prices than shorter ones?
3. Do auctions with **more unique bidders** achieve higher final prices?

## Key findings

I analysed **134 Cartier auctions** (1,953 bids), after removing 2 extreme outliers.

| Question | Result | Evidence |
|---|---|---|
| Opening bid | Small positive effect | Spearman ρ = 0.25 (p = 0.004); +10% opening bid ≈ +1.2% final price |
| Auction length | Positive once the other factors are held constant | Not significant alone (p = 0.24); ≈ +12.7% per extra day in the regression (p = 0.022) |
| Unique bidders | Positive effect | Spearman ρ = 0.17 (p = 0.044); ≈ +9.5% per extra bidder in the regression |

Opening bid and number of bidders are **negatively related** (ρ = −0.55): high opening bids scare bidders away. Looking at each factor on its own hides part of the effect, so I also used a multiple regression.

**Recommendations for sellers:** choose longer (7-day) auctions, attract as many bidders as possible, and use a very low opening bid (≤ $1) or a high one only for valuable watches.

**Limitations:** the sample is small, there are few 3- and 5-day auctions, and the data has no watch model or condition (R² ≈ 0.17). The results are associations, not causal effects.

## CRISP-DM steps in the notebook

1. **Business Understanding:** goal, research questions and the variables needed
2. **Data Understanding:** loading the data, checking structure and missing values, counting bids and auctions
3. **Data Preparation:** filling missing values, keeping only the Cartier rows, building one row per auction, removing outliers (z-score), log transform
4. **Modeling:** Spearman correlation, Kruskal–Wallis test and multiple linear regression (log price)
5. **Evaluation:** answers to the research questions and limitations
6. **Deployment:** recommendations for sellers

## Repository structure

```
├── cartier_crispdm_simple.ipynb   # Main notebook (analysis with notes)
├── requirements.txt               # Python libraries needed
├── README.md                      # This file
└── .gitignore                     # Files Git should ignore
```

## Data

The dataset is the eBay online auctions dataset from Jank & Shmueli (2010), available on Kaggle:
https://www.kaggle.com/datasets/onlineauctions/online-auctions-dataset

Download `auction.csv` and put it in the project's main folder (next to the notebook). It isn't included in this repository.

## How to run it

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/cartier-ebay-auctions.git
cd cartier-ebay-auctions

# 2. Create and activate a virtual environment
python3 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

# 3. Install the libraries
pip install -r requirements.txt

# 4. Add auction.csv to the folder, then start Jupyter
jupyter notebook
```

Open `cartier_crispdm_simple.ipynb` and choose **Run → Run All Cells**.

## Tools

Python · pandas · NumPy · seaborn · Matplotlib · SciPy · statsmodels · Jupyter

## Main references

- Chapman, P. et al. (2000). *CRISP-DM 1.0: Step-by-step data mining guide*. SPSS Inc.
- Jank, W., & Shmueli, G. (2010). *Modeling online auctions*. Wiley.
- Lucking-Reiley, D., Bryan, D., Prasad, N., & Reeves, D. (2007). Pennies from eBay: The determinants of price in online auctions. *Journal of Industrial Economics, 55*(2), 223–233.
- Bajari, P., & Hortaçsu, A. (2003). The winner's curse, reserve prices, and endogenous entry: Empirical insights from eBay auctions. *RAND Journal of Economics, 34*(2), 329–355.
- Ku, G., Galinsky, A. D., & Murnighan, J. K. (2006). Starting low but ending high: A reversal of the anchoring effect in auctions. *Journal of Personality and Social Psychology, 90*(6), 975–986.

The full reference list is at the end of the notebook.

## Author

**Laura Lukasevic**
