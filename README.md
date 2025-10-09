# Kaggle House Prices — EDA & Preprocessing

**進度**：目前正在資料蒐集/EDA/特徵工程；將來選出模型與可解釋性。  
我整理了 Kaggle House Prices 的資料，Notebook 一鍵 Run All 就會把圖放在 figs/、乾淨資料放在 artifacts/。
價格分布右偏，對數化後較正常（figs/01,02）。缺值主要來自設施類（地下室、車庫、圍籬、泳池），我採 None/0/眾數 的一致補值策略（figs/03）。
與價格最相關的是 OverallQual 和面積類（GrLivArea/TotalBsmtSF/1stFlrSF/TotalSF，見 figs/30），分組圖也顯示品質、社區的明顯價差（figs/20,21）。
我做了 TotalSF、TotalBath、AgeAtSale、RemodAge 等衍生特徵，並輸出 artifacts/train_clean.csv（含 SalePrice_log 當目標）。建模同學請直接從這個檔出發做 Linear/Ridge/Lasso/GBDT，再用 Permutation/SHAP/PDP 做解釋即可。
離群值我先以 99.5 分位標記在 outliers_flags.csv，是否封頂或排除留待建模階段決策。

**如何執行**：
1. 將 `train.csv`、`test.csv` 放在專案根目錄。
2. 開 `houseprice_eda_preprocess.ipynb` 由上到下執行。
3. 產出：`figs/`（圖）、`artifacts/`（train_clean.csv、test_clean.csv 等）。
- 打開 figs/01、figs/02：說明右偏與 log1p。
- figs/03：三類缺值策略（None / 0 / 眾數）。
- figs/30 與 figs/31：相關 Top-20 與熱力圖。
- figs/20、figs/21：品質/社區差異。
- 打開 artifacts/train_clean.csv：指出 SalePrice_log 與衍生特徵欄位。
- artifacts/outliers_flags.csv：後續由模型端決定處理方式。

**前處理策略摘要**：
- 設施缺值→`"None"`；面積/數量→`0`；一般類別→眾數。
- `LotFrontage`：以 `Neighborhood` 中位數補，兜底全域中位數。
- 衍生特徵：`TotalSF`、`TotalBath`、`AgeAtSale`、`RemodAge`。


**未來目標**:
- 建模目標：用 SalePrice_log 當 y 就能直接訓練Linear/Ridge/Lasso/GBDT 並做可解釋性（PermImp/SHAP/PDP）(`SalePrice_log = log1p(SalePrice)`)。
