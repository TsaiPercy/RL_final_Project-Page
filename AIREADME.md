# AIREADME — 專案內部設計文件

> 此文件僅供 Antigravity 閱讀，作為專案狀態的唯一可信來源。

## 專案概要

**專案名稱**: Designing Fun: LLM-based Game Level Generation via Agent Gameplay Feedback  
**類型**: 學術論文 Project Page（靜態網頁）  
**作者**: 謝侑哲、李佑軒、蔡承志  
**框架**: Bulma CSS + 原生 HTML/JS（基於 Academic Project Page Template）

## 目錄結構

```
Project-Page-Template/
├── index.html              # 主頁面
├── AIREADME.md             # 本文件
├── README.md               # 人類開發者說明
├── .nojekyll               # GitHub Pages 設定
└── static/
    ├── css/
    │   ├── index.css        # 自訂樣式（主要修改對象）
    │   ├── bulma.min.css    # Bulma CSS framework
    │   ├── bulma-carousel.min.css
    │   ├── bulma-slider.min.css
    │   └── fontawesome.all.min.css
    ├── js/
    │   ├── index.js         # 主要 JS 邏輯
    │   ├── bulma-carousel.min.js
    │   ├── bulma-slider.min.js
    │   └── fontawesome.all.min.js
    ├── images/              # 圖片資源
    ├── pdfs/                # PDF 文件
    └── videos/              # 影片資源
```

## 頁面 Section 架構（由上到下）

| 順序 | Section ID | 標題 | 背景色 | 說明 |
|------|-----------|------|--------|------|
| 1 | hero | 標題 + 作者 + 連結按鈕 | 白 | 保留原始模板 |
| 2 | teaser | Teaser | 白 | 四欄展示 `final_strong.gif` 到 `final_strong4.gif`（附帶各自 Goto 任務的標籤） |
| 3 | abstract | Abstract | 淺灰 `is-light` | 論文摘要 |
| 4 | problem-motivation | Problem + Motivation | 白 | 雙欄 `columns`（採 `is-max-widescreen` 寬版容器，左 Problem 右 Motivation） |
| 5 | methodology | Methodology | 淺灰 `is-light` | 子段落：How We Define Fun?（三卡片）+ SFT + Multi-Reward GRPO（method figure + 步驟 + reward cards） |
| 6 | results | Results | 白 | 主比較表格（5 metrics × 3 baselines）+ 縱向自適應視覺化圖表 + generated level samples comparison 畫廊 |
| 7 | ablation-study | Ablation Study | 淺灰 `is-light` → 白 | 消融表格（4 configs × 5 metrics，填入真實數據） |
| 8 | conclusion | Conclusion | 淺灰 `is-light` | 結論總結 + 雙欄卡片（Limitations + Future Work） |
| 9 | reference | References | 白 | 參考文獻列表 |

## 設計假設與技術債

- **Placeholder 圖片**: 大多數 `.placeholder-figure` 區塊已替換為實際圖片（包括 problem、motivation 及 results 視覺化圖表），僅剩 methodology 中個別預留位置。
- **Limitation 內容**: 限制和未來方向的條目需替換為實際內容
- **Meta 資訊**: `<head>` 中的 TODO 項目（OG tags、Twitter cards 等）仍使用模板預設值

## CSS 自訂樣式

在 `index.css` 尾部（`/* ===== Custom Section Styles ===== */` 之後）新增了以下自訂樣式：
- `.placeholder-figure` — 虛線框圖片佔位
- `.placeholder-figure.plain-figure` — 移除虛線框、背景與大內距的圖片佔位（保留排版且縮小垂直間距）
- `.problem-list` / `.motivation-point` — Problem & Motivation 佈局
- `.fun-dimension-card` — How We Define Fun 三張卡片
- `.method-step` / `.method-step-number` — Methodology 步驟 UI
- `.reward-card` — Reward Design 五張卡片（改用 Bulma columns 排版）
- `.result-table` — 表格樣式覆寫
- `.limitation-card` — Limitation/Future Work 卡片
- `.reference-list` — 參考文獻列表樣式

所有自訂樣式均有 mobile responsive 支援（`@media max-width: 768px`）。

## 更新記錄

- **2026-06-08**:
  - 填寫限制 (Limitations) 與未來工作 (Future Work) 卡片，分別填入 3 點正式的學術論述項目（包含無真人評估、受限於 MiniGrid 環境、Regret 依賴 Agent、結合真人玩測、擴充至 MiniHack/NetHack 與課程學習獎勵塑造）。
  - 填寫論文摘要 (Abstract)，替換原有的 Placeholder 內容。
  - 修復限制與未來工作卡片內因為兩端對齊（justify）產生的排版空格問題，在 CSS 的 `.limitation-card` 類別中強制套用 `text-align: left;`。
  - 填寫結論區塊 (Conclusion)，使用條列式列表列出論文的三大主要發現（架構提案、拆解「好玩」指標、實驗驗證）。
  - 調整主比較表格的資料列順序，使用遞進順序（`Vanilla LLM` -> `SFT LLM` -> `GRPO LLM (Ours)`）來呈現效能的逐步提升。
  - 將 `index.html` 中的「主比較表格 (Main Comparison)」進行轉置，將各生成方法 (Method) 調整為左側首欄，指標 (Metrics) 調整為上方首列，優化寬螢幕與行動裝置上的可讀性。
  - 清理 `AIREADME.md` 目錄結構中已刪除的 `index_B.html` 與 `index_C.html` 參照。
