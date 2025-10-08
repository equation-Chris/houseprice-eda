# Kaggle House Prices — EDA & Preprocessing

**分工**：我負責資料蒐集/EDA/特徵工程；隊友負責模型與可解釋性。  
**如何執行**：
1. 將 `train.csv`、`test.csv` 放在專案根目錄。
2. 開 `houseprice_eda_preprocess.ipynb` 由上到下執行。
3. 產出：`figs/`（圖）、`artifacts/`（train_clean.csv、test_clean.csv 等）。

**前處理策略摘要**：
- 設施缺值→`"None"`；面積/數量→`0`；一般類別→眾數。
- `LotFrontage`：以 `Neighborhood` 中位數補，兜底全域中位數。
- 衍生特徵：`TotalSF`、`TotalBath`、`AgeAtSale`、`RemodAge`。
- 建模目標：`SalePrice_log = log1p(SalePrice)`。
