# AGENTS.md - 體能教練 × 運動營養師：健身與飲食科學知識庫

## 1. 專案目的 (Project Purpose)
本專案為一套結合「運動科學」與「精準營養學」的互動式網頁知識庫。旨在將艱澀的熱量赤字、BMR/TDEE 計算與重訓課表原理，轉化為結構清晰、可翻頁閱讀的視覺化講義，並作為未來多智能體 (Multi-Agent) 健身排程系統的知識底座。

## 2. 視覺與設計風格 (Design System & Aesthetics)
所有頁面必須嚴格遵守以下「運動科技卡片風 (Athletic Tech UI)」規範，確保全站視覺高度一致：
* **背景底色：** 冷冽運動藍灰點陣質感（`#F0F4F8` 底色搭配 `#CBD5E1` 圓點網格）。
* **主色調：** 深海藍（`#0F2942`）作為主要標題、邊框與按鈕文字色。
* **強調色：** 運動薄荷綠（`#A7F3D0`）用於重點螢光筆畫線與主要按鈕底色；金屬銀灰（`#CBD5E1`）與冰河藍（`#BAE6FD`）用於頂部「標籤貼 (Tag Strip)」裝飾。
* **卡片設計：** 圓角矩形（`border-radius: 16px`），搭配 `2px solid #0F2942` 實線邊框與柔和陰影。

## 3. 檔案架構與命名規則 (File Structure & Naming)
/
├── AGENTS.md           # 本專案核心規則與 AI 協作指南
├── index.html          # 網站首頁（講義總覽與卡片導覽入口）
└── lesson-01.html      # 單元一：能量代謝與 BMR/TDEE 核心算法（互動翻頁講義）

* **命名規範：** 新增任何知識單元時，必須統一命名為 `lesson-XX.html`（例如 `lesson-02.html`、`lesson-03.html`），禁止使用中文或大寫英文字母命名 HTML 檔案。

## 4. 新增頁面與內容的標準流程 (Rules for AI Extensions)
當 AI 收到「新增一個知識單元」的指令時，必須執行以下兩項動作：

### 動作 A：建立新講義頁面 (`lesson-XX.html`)
1. 複製 `lesson-01.html` 的 HTML 結構與 CSS 樣式表。
2. 頁面必須包含「單頁投影片視窗 (Slide Container)」與底部「進度圓點導覽列 (Pagination Dots)」。
3. 必須保留 JavaScript 鍵盤監聽事件，確保使用者可透過鍵盤 `ArrowLeft`（左鍵）與 `ArrowRight`（右鍵）流暢翻頁。
4. 每張投影片內容需精簡（不超過 120 字），善用 `<span class="highlight">` 螢光筆標記關鍵數據。

### 動作 B：同步更新首頁 (`index.html`)
1. 在 `index.html` 的 `.card-grid` 區塊內，新增一張對應的講義卡片。
2. 卡片結構必須包含：頂部標籤貼裝飾、分類標籤、單元標題、50 字內摘要、底部屬性膠囊，以及連結至 `lesson-XX.html` 的「開始 →」按鈕。

## 5. 程式碼品質與禁止事項 (Constraints)
* **純原生技術棧：** 僅使用原生 HTML5、CSS3 與 Vanilla JavaScript，禁止引入 React、Vue 或需要打包編譯的外部框架，確保可直接部署於 GitHub Pages。
* **響應式設計：** 卡片網格必須使用 CSS Grid（`grid-template-columns: repeat(auto-fit, minmax(300px, 1fr))`），確保在手機與電腦螢幕皆能正常瀏覽。