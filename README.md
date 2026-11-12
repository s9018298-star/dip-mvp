# DIP · MVP Architecture

> **Data Innovation Platform · 架構總覽**
> 內外雙模切換 · Pitch / Onboarding 共用底圖
> 更新日期：2026-11-12

🔗 **線上預覽：** https://你的帳號.github.io/dip-architecture/

---

## 📖 這份文件是什麼

DIP (Data Innovation Platform) 的產品架構總覽單頁，服務於三種情境：

- **對客戶 Pitch**：講平台價值、客戶痛點、信任治理 → 切「對外模式」
- **新人 Onboarding**：了解 11 個產品、資料流、IAM 權限模型 → 切「內部模式」

單一 HTML 檔，無相依、無後端、離線可看。

---

## 🎯 內容章節（共 20 Sections · 繁體中文）

### Overview · 總覽（對內 7 / 對外 5）
- Hero · 平台概覽
- 客戶痛點（外部專屬）
- 四大資料流
- 11 大產品地圖（內部專屬）
- Topology · 5 層治理架構
- Trust & Governance · 治理 / 隔離 / 合規
- 11 Products 技術基礎（內部專屬）
- User Journey（內部專屬）

### IAM · 身分與權限（內部 5 / 對外 4）
- IAM Resource Hierarchy · 組織 → 專案 → 資料集
- SpiceDB + Ranger · 兩步驟分工（身分檢查 vs 行為授權）
- SpiceDB Playground · 階層授權模擬（內部專屬）
- 兩條授權路徑 · 人 vs 系統呼叫
- Multi-Project Isolation · 資料分倉

### CS · Compute Studio（內部 7）
- CS 1.0 vs DIP CS 比較
- BA 開發體驗 Before / After
- 4 種 Spark Job 類型
- Compute Credit / Tier 計價模型
- ADR 架構決策紀錄

### Delivery · 交付節奏（內部 1）
- 產品 Roadmap

---

## 🎨 設計風格

- **Morning Fog + Studio 風格**：淺色毛玻璃 + 靛藍 / 粉橘配色
- **字型**：Noto Serif TC（標題）· Fraunces italic（強調）· Plus Jakarta Sans（內文）· JetBrains Mono（技術代碼）
- **互動**：飄浮光暈、`cubic-bezier(.22, 1, .36, 1)` 統一緩動

---

## 🚀 怎麼用

### 本機開啟
直接雙擊 `index.html`，瀏覽器會打開。

### GitHub Pages 上線
```bash
# 1. clone / push
git clone https://github.com/你的帳號/dip-architecture.git
cd dip-architecture
cp 你的下載路徑/dip.html ./index.html
git add index.html README.md
git commit -m "init: DIP MVP Architecture v30"
git push

# 2. 到 Repo Settings → Pages
# 3. Source: main · /(root) → Save
# 4. 等 1~3 分鐘，網址會出現在 Pages 頁面
```

### 互動方式
- **右上角 Topic Tabs**：切換章節範圍（Overview / IAM / CS / Delivery / 全部）
- **右上角 Mode 切換**：內部版 vs 對外版（會自動隱藏技術細節）
- **⌘K / Ctrl+K**：開啟搜尋命令列，支援階層路徑
- **URL Hash 深連結**：
  - `#iam` · 跳到 IAM 區
  - `#iam/hierarchy` · 直接到 IAM Resource Hierarchy
  - `#cs/credit` · 直接到 CS Compute Credit 計價

---

## 📝 版本紀錄

| Version | Date | 主要變更 |
|---|---|---|
| **v30** | 2026-11-12 | IAM 區塊白話化（Resource Hierarchy / SpiceDB+Ranger / Multi-Project Isolation）· 改名為 DIP MVP Architecture |
| v29 | 2026-11-12 | 兩條授權路徑外部白話化（人 vs 系統呼叫） |
| v28 | 2026-11-12 | Phase A + B：Trust & Governance 移位、Section 7/9 設內部專屬、Hero 加對外開場、新增客戶痛點區塊 |
| v27 | 2026-11-11 | 升級 ⌘K 階層搜尋 · 修正 CMDK 與 Toast 深色底 |
| v26 | 2026-11-11 | Topology 改為 5 層結構（參照 lineage map） |
| v25 | 2026-11-10 | 加入 CS 詳細內容（5 新區塊） |
| v24 | 2026-11-10 | Topic Tabs Bar + URL Hash 支援 |

---

## ⚠️ 使用前請確認

### 對外分享前
- [ ] 右上角 Mode 預設切至「對外模式」
- [ ] 檢查 Section 11（IAM）所有技術 playground 已隱藏
- [ ] 確認 project id（如 `pxa-001`）的範例值在對外模式顯示為「獨立識別碼」

### 對外三原則
1. 不講具體客戶名與內部代號
2. 不暴露內部實作細節（Keycloak、APISIX、Kafka、SpiceDB 等）
3. 不透露交付時程與產品路線圖

### Repo 可見性建議
- **Public repo**：提交前先掃過內容；所有 commit history 也會公開
- **Private repo 用 Pages**：需要 GitHub Pro（$4/月）或 Team 以上方案

---

## 🛠 技術規格

- 單一 HTML 檔，約 5000+ 行
- 無相依套件、無 build step、無後端
- 瀏覽器支援：Chrome / Safari / Edge 近 2 年版本
- 檔案大小：~500 KB
- 離線可用（靜態資源 inline）
