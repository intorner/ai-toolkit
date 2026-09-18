# ai-toolkit

## 專案識別
- 專案顯示名稱：`ai-toolkit`
- 專案代號：`ai-toolkit`
- GitHub repo：`intorner/ai-toolkit`
- Repository Current Truth / progress：依本 repo current state / durable work surface；local path 與 Obsidian 只作 projection。
- Shared AI engineering / ChatGPT Project bootstrap authority：`codex-sync`

## 定位

本 repo 是「Repository project bootstrap / initialization template」規格來源，負責：

- Repository 基本結構與 state files
- `CLAUDE.md` bootstrap/control entrypoint 規格
- 新專案 / 既有專案初始化 SOP
- 跨設備 local-path projection 規則
- 初始化驗證清單

ChatGPT Project Instructions 不由本 repo 產生或維護；其 shared canonical generation authority 是：

`codex-sync/docs/chatgpt-project-bootstrap-library.md`

shared capability / GB10 / Codex / Hermes / RDC routing 也不在本 repo 複製，消費者只保留 thin redirect 到 `codex-sync`。

## Authority model

初始化後的 consumer Project 應遵守：

1. `current-state.md`：目前仍有效的 Project Current Truth / resume surface。
2. `CLAUDE.md`：bootstrap / control entrypoint；說明 Project identity、authority pointers、startup 與 shared routing redirect。
3. Method / Spec / runbook / evidence：各自正式 authority。
4. Obsidian / local work note：可選 operational projection / fast-changing notes，不是必備 Source of Truth。
5. local working copy / host path / managed tool binding：projection only，可 stale / dirty。
6. chat memory / historical conversation：reference only。

`CLAUDE.md` 不再是「單一真相來源」，也不得把某個 host、Codex、Hermes、RDC、Obsidian MCP、model、endpoint 或 Vault drive 寫成永久 primary route。

## 對話開始時請先讀

初始化規則維護：
- `README-初始化規則.md`
- `專案初始化模板.md`
- `CLAUDE欄位規格.md`
- `初始化驗證清單.md`

建立 ChatGPT Project Instructions：
- 讀 `codex-sync/docs/chatgpt-project-bootstrap-library.md`

涉及 GB10/shared capability：
- 依 `codex-sync` canonical bootstrap / routing，不在本 repo 發明或複製 routing。

## 規則核心

- `current-state.md` 是 consumer Project 的 Current Truth surface；`CLAUDE.md` 是 bootstrap/control entrypoint。
- Project-specific authority 留在 consumer repo；shared AI engineering authority 外移到 `codex-sync`。
- shared routing 使用 thin redirect，不複製 mutable capability trigger、host、runner、model、fallback。
- Obsidian / work note 是 optional projection；沒有它也能完成初始化。
- 共享文件優先使用相對路徑 / semantic locator，不把單一設備絕對路徑當 authority。
- 新專案初始化與既有專案 retrofit 分流。
- Git init/add/commit/remote/push 都是 side effect；只有在 Human 明確授權對應 scope 後執行。
- 不因初始化建立空的 future-facing docs/scripts/tools 目錄；只有真實需要時建立。
- Durable Recording 只在長期、多階段、decision-rich project 啟用；checkpoint 不取代 Current Truth / Method / Spec。

## 重要文件

- 新專案表單：`新專案初始化表單.md`
- 初始化模板：`專案初始化模板.md`
- 欄位規格：`CLAUDE欄位規格.md`
- 驗證清單：`初始化驗證清單.md`
- 既有專案 SOP：`既有專案補初始化SOP.md`
- 跨設備路徑：`跨設備路徑規則.md`
- 範例：`examples/standard-project/`

## 安全邊界

- 不把 `.claude/`、`.codex/`、`.env`、credentials、private keys 納入版控。
- 不把 Human authorization 當 transport。
- 不因 initialization request 自動推定 Git write / remote write / deployment / service/runtime change authorization。
- 不建立第二份 shared routing authority。
