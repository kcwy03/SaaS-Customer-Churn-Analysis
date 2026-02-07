# SaaS-Customer-Churn-Analysis

我的資料分析作品集專案，分析 SaaS 公司的客戶流失問題。

## 專案背景

這是我用來練習資料分析的專案。資料來自 Kaggle 上的 SaaS 公司客戶資料（500 個客戶），想要了解為什麼客戶會流失，還有怎麼改善留存率。

**主要問題：**
- 為什麼客戶會流失？
- 哪些客戶比較容易流失？
- 怎麼提高留存率？

## 使用的工具

- Python（pandas, matplotlib, seaborn）
- Google Colab
- Excel (看資料用)

## 資料說明

資料包含 5 個表格：
- accounts: 客戶基本資料
- subscriptions: 訂閱紀錄
- churn_events: 流失事件
- feature_usage: 功能使用情況
- support_interactions: 客服紀錄

## 分析內容

### 1. 資料探索 (01_data_exploration.py)
先看看資料長什麼樣子，有沒有缺失值之類的。

**發現的問題：**
- 每個客戶有 10 個訂閱（有點奇怪但資料就是這樣）
- 流失率 22%，比業界標準高

### 2. KPI Dashboard (02_kpi_dashboard.py)
整理重要指標：
- MRR: $10.16M
- 流失率: 22%
- 客戶滿意度: 3.98/5

做了一些圖表看不同維度的表現。

### 3. Cohort Analysis (03_cohort_analysis_CORRECTED.py)
這部分我做了兩次，因為第一次發現留存率算出來超過 100%（明顯有問題）。

**遇到的問題：**
- 一開始用訂閱來算，但其實應該用帳號
- 修正後留存率從 100%+ 變成合理的 78%

**主要發現：**
- 前 6 個月流失最多（掉了 55%）
- 2023-02 的 cohort 留存最差（61%）
- 2024-12 的 cohort 留存最好（94%），但他們才剛註冊所以不太能比

### 4. Funnel Analysis (04_funnel_analysis_CORRECTED.py)
本來想分析 Trial → Paid 的轉換，但發現資料有點特別。

**問題：**
- 所有客戶都有付費訂閱（轉換率 100%）
- 這不太正常，可能資料只包含已經付費的客戶

**調整後：**
- 改成分析「付費後的留存」
- 比較先 Trial vs 直接付費的差異
- 發現兩種方式的留存率差不多（~78%）

## 主要發現

1. **流失率偏高 (22%)**
   - 業界標準是 5-10%
   - 我們是 22%，需要改善

2. **前 6 個月很關鍵**
   - 大部分流失發生在前半年
   - 需要加強 onboarding

3. **流失原因**
   - 功能不足 (19%)
   - 客服問題 (17%)
   - 預算 (17%)

4. **產業差異**
   - Cybersecurity 留存最好 (84%)
   - DevTools 留存最差 (69%)

5. **Trial 影響不大**
   - 先 Trial 和直接付費的留存率差不多
   - 產品本身比較重要

## 建議

根據分析結果，我覺得可以：

1. 改善前 3 個月的 onboarding
2. 開發客戶要的功能
3. 針對 DevTools 產業做專門的方案
4. 加強客服品質

## 專案反思

做這個專案學到蠻多的：

**技術面：**
- pandas 的 groupby 和 pivot 很好用
- 畫圖要選對圖表類型
- 資料清理很重要

**分析面：**
- 要檢查資料合不合理（我的留存率一開始超過 100% lol）
- 同一個問題可以從不同角度分析
- 要驗證結果（Cohort 和 Funnel 的留存率要一致）

**遇到的困難：**
1. Cohort 分析算錯（訂閱 vs 帳號搞混）
2. Funnel 資料不完整（只有付費客戶）
3. 圖表一開始不知道怎麼解讀

但我都有找出問題在哪，然後修正，覺得這個過程比結果更重要。

## 檔案說明

```
├── 01_data_exploration.py          # 資料探索
├── 02_kpi_dashboard.py             # KPI 分析
├── 03_cohort_analysis_CORRECTED.py # Cohort 分析（修正版）
├── 04_funnel_analysis_CORRECTED.py # Funnel 分析（修正版）
├── *.png                            # 圖表
└── *.md                             # 說明文件
```


## 資料來源

Kaggle - SaaS Customer Churn Dataset
（模擬資料，不是真實公司）

## 未來改進

如果有時間想做：
- 加上預測模型（預測誰會流失）
- 做 Tableau dashboard
- 分析客服對話內容
- 加入時間序列分析

---

**備註：**
這是練習專案，資料是模擬的。歡迎給建議！
2025
