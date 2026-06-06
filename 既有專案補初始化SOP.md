# 既有專案補初始化 SOP

> 版本：v0.2
> 更新日期：2026-06-06

這份 SOP 用於把已存在的專案補上 `ai-toolkit` 的初始化規則。

---

## 適用情境

- 專案已經有檔案，但沒有 `CLAUDE.md`
- 專案已經有 git，但沒有完整 Obsidian 工作筆記
- 專案已有 GitHub repo，但 repo slug 和顯示名稱不同
- 專案從其他位置搬到正式工作目錄
- 專案已有 `CLAUDE.md` 或 Obsidian 工作筆記，但缺少 `current-state.md`、`handoff.md`、`tasks.md`、`worklog.md`、`runbook.md` 等狀態檔

---

## 1. 盤點專案現況

先確認：

- 工作根目錄
- 專案顯示名稱
- 專案代號
- GitHub repo slug
- Obsidian vault 路徑
- Firebase 專案名稱是否需要

不要用專案顯示名稱直接推導 GitHub repo slug。

---

## 1.1 缺狀態檔的低風險初始化

若 `startup` 發現既有專案缺少專案內狀態檔，先走低風險初始化，不要直接進入功能修改。

適用條件：

- 專案已有 `CLAUDE.md`，或已有足以識別專案的 Obsidian 工作筆記
- 缺少一個以上標準狀態檔：`current-state.md`、`handoff.md`、`tasks.md`、`worklog.md`、`runbook.md`
- 本次目標只是補齊接續工作需要的文件，不修改功能程式

執行範圍：

- 先讀 `CLAUDE.md` 與 Obsidian 工作筆記
- 只建立缺少的狀態檔，已存在的狀態檔只做必要修正
- 可更新 Obsidian 工作筆記的 `上次做到哪` 與最近更動紀錄
- 不修改功能程式、腳本、設定檔、`.git`、`.env`、token、憑證或機器專屬設定

路徑分流：

- 若目前在 NAS shared state/document path，只寫共享狀態檔與 Obsidian 工作筆記，不執行 git
- 若需要 commit，先在每台電腦自己的 local git working copy 中同步這些狀態檔，再只提交狀態管理檔
- 若目前在 local git working copy，可直接提交，但 `git add` 範圍只限狀態管理檔

提交範圍：

```text
current-state.md
handoff.md
tasks.md
worklog.md
runbook.md
```

若同時補 `CLAUDE.md`、`.gitignore`、`.gitattributes` 或 Obsidian 工作筆記，要在回報中明確列出，避免混入功能修改。

---

## 2. 檢查 git

至少檢查：

```bash
git status --short
git branch --show-current
git remote -v
git branch -vv
```

若出現 `dubious ownership`，確認該目錄可信後再加入安全目錄：

```bash
git config --global --add safe.directory <工作根目錄>
```

---

## 3. 處理 remote

原則：

- 不直接覆蓋既有 `origin`
- 先看目前 remote 名稱與 URL
- 如果已有正確 remote，只修正 tracking
- 如果需要新增 remote，先確認名稱不衝突

常見情況：

- `origin` 已存在且正確
- `origin` 已存在但指向舊 repo
- 另有其他 remote，例如 `lazy-packs`
- 本機 branch 尚未追蹤遠端 branch

---

## 4. 補專案檔案

至少補：

- `CLAUDE.md`
- `.gitignore`
- `tools/`（若此專案會放工具）

`CLAUDE.md` 依 `CLAUDE欄位規格.md` 撰寫，尤其要確認：

- 專案代號
- 工作根目錄
- GitHub repo
- Obsidian 工作筆記

---

## 5. 補 Obsidian 工作筆記

固定位置：

```text
<Obsidian vault 路徑>\專案庫\<專案代號>\工作筆記.md
```

如果舊筆記已存在：

- 優先搬到固定位置
- 更新 repo 連結
- 更新 `上次做到哪`
- 保留有用的歷史紀錄

---

## 6. 專案搬移處理

若專案從舊位置搬到正式工作根目錄：

- 先確認新位置檔案完整
- 確認 `.git` 還在
- 確認 GitHub remote 正確
- 舊位置若刪不掉，列為後續清理項

不要因為舊空殼資料夾無法立即刪除而中斷初始化。

---

## 7. 做最小初始化 commit

只提交初始化相關檔案：

- `CLAUDE.md`
- `.gitignore`
- `tools/` 空資料夾若需要可用 `.gitkeep`
- 其他初始化文件

避免混入功能修改或大型重構。

若本次只是低風險狀態檔初始化，commit 範圍應縮小為狀態管理檔與必要工作筆記紀錄，不提交功能程式或環境設定。

---

## 8. 驗證

最後依 `初始化驗證清單.md` 檢查。

至少確認：

- `startup` 讀得到正確工作筆記
- `shutdown` 寫入正確工作筆記
- GitHub repo URL 正確
- `.gitignore` 沒有漏掉本機設定與敏感檔案
- 若本次為低風險狀態檔初始化，確認沒有功能程式、腳本、設定檔或敏感資料被修改
