# 既有專案補初始化 SOP

> 版本：v0.1
> 更新日期：2026-05-03

這份 SOP 用於把已存在的專案補上 `ai-toolkit` 的初始化規則。

---

## 適用情境

- 專案已經有檔案，但沒有 `CLAUDE.md`
- 專案已經有 git，但沒有完整 Obsidian 工作筆記
- 專案已有 GitHub repo，但 repo slug 和顯示名稱不同
- 專案從其他位置搬到正式工作目錄

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

---

## 8. 驗證

最後依 `初始化驗證清單.md` 檢查。

至少確認：

- `startup` 讀得到正確工作筆記
- `shutdown` 寫入正確工作筆記
- GitHub repo URL 正確
- `.gitignore` 沒有漏掉本機設定與敏感檔案
