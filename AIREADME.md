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
├── index.html              # 主頁面，所有 section 在此
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
| 2 | abstract | Abstract | 淺灰 `is-light` | 論文摘要 |
| 3 | problem-motivation | Problem + Motivation | 白 | 雙欄 `columns`，左 Problem 右 Motivation |
| 4 | methodology | Methodology | 淺灰 `is-light` | 子段落：How We Define Fun?（三卡片）+ SFT + Multi-Reward GRPO（method figure + 步驟 + reward cards） |
| 5 | results | Results | 白 | 主比較表格（7 metrics × 3 baselines）+ visualization |
| 6 | ablation-study | Ablation Study | 淺灰 `is-light` → 白 | 消融表格（6 configs × 4 metrics） |
| 7 | conclusion | Conclusion | 淺灰 `is-light` | 結論總結 + 雙欄卡片（Limitations + Future Work） |
| 8 | BibTeX | BibTeX | 白 | 引用資訊 + 複製按鈕 |

## 設計假設與技術債

- **Placeholder 圖片**: 所有 `.placeholder-figure` 區塊目前為虛線框 + 提示文字，需替換為實際圖片
- **表格數據**: Result 和 Ablation Study 表格中的 `—` 需替換為實際實驗數據
- **Limitation 內容**: 限制和未來方向的條目需替換為實際內容
- **Meta 資訊**: `<head>` 中的 TODO 項目（OG tags、Twitter cards 等）仍使用模板預設值
- **BibTeX**: 引用資訊需更新為正確內容

## CSS 自訂樣式

在 `index.css` 尾部（`/* ===== Custom Section Styles ===== */` 之後）新增了以下自訂樣式：
- `.placeholder-figure` — 虛線框圖片佔位
- `.problem-list` / `.motivation-point` — Problem & Motivation 佈局
- `.fun-dimension-card` — How We Define Fun 三張卡片
- `.method-step` / `.method-step-number` — Methodology 步驟 UI
- `.reward-card` — Reward Design 四張卡片
- `.result-table` — 表格樣式覆寫
- `.limitation-card` — Limitation/Future Work 卡片

所有自訂樣式均有 mobile responsive 支援（`@media max-width: 768px`）。
