# ai-toolkit

## 專案識別
- 專案顯示名稱：`ai-toolkit`
- 專案代號：`ai-toolkit`
- 工作根目錄：`<AI_TOOLKIT_ROOT>`
- GitHub repo：`intorner/ai-toolkit`
- Obsidian 工作筆記：`專案庫/ai-toolkit/工作筆記.md`
- Firebase 專案：`my-teaching-tools`

## 這個專案的定位

這不是單一工具專案，而是「多專案初始化規則總控專案」。

它負責維護：
- 專案初始化模板
- `CLAUDE.md` 欄位規格
- 新專案初始化 SOP
- 既有專案補初始化 SOP
- 與 `startup` / `shutdown` 對接的規則

若其他專案要套用這套工作模式，應以本專案的模板與規格文件為準。

## 對話開始時請先讀

進度與最近更動都在 Obsidian：`專案庫/ai-toolkit/工作筆記.md`

若要初始化其他專案，優先閱讀：
- `新專案初始化表單.md`
- `新專案口令規則.md`
- `跨設備路徑規則.md`
- `專案初始化模板.md`
- `CLAUDE欄位規格.md`

## 工作模式

- **維護初始化規則**：修改 `專案初始化模板.md`、`CLAUDE欄位規格.md`、相關 SOP
- **開始新專案**：使用者說「開始新專案」、「我要開始新專案」、「我要初始化新專案」、「開一個新專案」時，先讀 `新專案初始化表單.md`，再依表單初始化
- **套用到其他專案**：依模板建立或補齊 `CLAUDE.md`、`.gitignore`、工作筆記與 git 設定
- **結束工作**：對 Codex 說「**收工**」→ 先依 `CLAUDE.md` 找到正確的工作筆記與 repo，再進行同步
- **接續工作**：對 Codex 說「讀工作筆記、告訴我上次做到哪」

## 規則核心

- `CLAUDE.md` 是每個專案的單一真相來源
- `startup` / `shutdown` 必須先讀 `CLAUDE.md`，不能寫死單一專案路徑
- 共享文件優先使用相對路徑與本機路徑變數，不綁定單一設備的絕對路徑
- Obsidian 工作筆記固定使用 `專案庫/<專案代號>/工作筆記.md`
- `專案顯示名稱`、`專案代號`、`GitHub repo slug` 必須分開管理
- 新專案初始化與既有專案補初始化必須分流處理

## 重要文件

- 新專案表單：`新專案初始化表單.md`
- 新專案口令：`新專案口令規則.md`
- 跨設備路徑規則：`跨設備路徑規則.md`
- 初始化索引：`README-初始化規則.md`
- 初始化模板：`專案初始化模板.md`
- 欄位規格：`CLAUDE欄位規格.md`
- 驗證清單：`初始化驗證清單.md`
- 既有專案 SOP：`既有專案補初始化SOP.md`
- 範例專案：`examples/standard-project/`
- 工作筆記：`專案庫/ai-toolkit/工作筆記.md`

## 工具清單

- `新專案初始化表單.md`
- `新專案口令規則.md`
- `跨設備路徑規則.md`
- `專案初始化模板.md`
- `CLAUDE欄位規格.md`
- `初始化驗證清單.md`
- `既有專案補初始化SOP.md`
- `examples/standard-project/`
- Codex `startup` / `shutdown` 多專案規則
- Stop 備份安全網（目前為本機 auto-commit 版）

## 工作注意事項

- 若模板、技能與實測結果衝突，以實測可穩定套用為優先，再回寫模板
- 若 `CLAUDE.md` 與工作筆記不一致，以 `CLAUDE.md` 為主，再修正工作筆記
- 不要把 `.claude/`、`.codex/`、`.env` 納入版控
- commit 訊息要寫清楚做了什麼 + 為什麼
- 收工前說「收工」讓 Codex 同步三方
