# Kaggle House Prices — EDA & Preprocessing

**進度**：目前正在資料蒐集/EDA/特徵工程；將來選出模型與可解釋性。  
**如何執行**：
1. 將 `train.csv`、`test.csv` 放在專案根目錄。
2. 開 `houseprice_eda_preprocess.ipynb` 由上到下執行。
3. 產出：`figs/`（圖）、`artifacts/`（train_clean.csv、test_clean.csv 等）。

**前處理策略摘要**：
- 設施缺值→`"None"`；面積/數量→`0`；一般類別→眾數。
- `LotFrontage`：以 `Neighborhood` 中位數補，兜底全域中位數。
- 衍生特徵：`TotalSF`、`TotalBath`、`AgeAtSale`、`RemodAge`。


**未來目標**:
- 建模目標：用 SalePrice_log 當 y 就能直接訓練Linear/Ridge/Lasso/GBDT 並做可解釋性（PermImp/SHAP/PDP）(`SalePrice_log = log1p(SalePrice)`)。
