# CLAUDE.md 欄位規格

> 版本：v0.3
> 更新日期：2026-06-05

這份文件補充 `CLAUDE.md` 在多專案工作模式中的必要欄位與用途。

---

## 必備欄位

建議每個專案的 `CLAUDE.md` 至少要能清楚表達：

| 欄位 | 用途 |
|------|------|
| 專案顯示名稱 | 給人讀的名稱 |
| 專案代號 | 路徑、資料夾、工具識別 |
| 工作根目錄 | 目前設備上的專案根目錄 |
| Linux 對應路徑 | NAS 或 Linux 工作副本上的對應路徑，可空白 |
| GitHub repo | 供 `startup` / `shutdown` 對照遠端 |
| Obsidian 工作筆記 | 供 `startup` / `shutdown` 找正確筆記 |
| 平台支援 | 標記 Windows / Linux / NAS 是否可直接操作 |
| 專案內狀態檔 | `current-state.md`、`handoff.md`、`worklog.md`、`tasks.md`、`runbook.md` |
| Firebase 專案 | 資料來源對照，可空白 |

---

## 推薦寫法

```markdown
# <專案顯示名稱>

## 專案識別
- 專案代號：`<專案代號>`
- 工作根目錄：`<工作根目錄>`
- Linux 對應路徑：`<Linux 或 NAS 對應路徑，可空白>`
- GitHub repo：`<GitHub帳號>/<GitHub repo slug>`
- Obsidian 工作筆記：`專案庫/<專案代號>/工作筆記.md`
- 平台支援：`Windows: <可操作/只讀/不適用>; Linux: <可操作/只讀/不適用>; NAS: <共享/不共享>`
- 專案內狀態檔：`current-state.md; handoff.md; worklog.md; tasks.md; runbook.md`
- Active session：`.project-session/active-session.json`（本機提醒用，勿進版控）
- Firebase 專案：`<Firebase 專案名稱>`
```

---

## 固定欄位名稱

為了讓 `startup` / `shutdown` 能穩定解析，建議不要任意改名：

- `專案代號`
- `工作根目錄`
- `Linux 對應路徑`
- `GitHub repo`
- `Obsidian 工作筆記`
- `Firebase 專案`
- `平台支援`
- `專案內狀態檔`
- `Active session`

如果需要補充資訊，新增欄位即可，不要替換上述欄位名稱。

---

## 專案內狀態檔

跨 Windows / Linux / NAS 接續時，只靠 Obsidian 工作筆記不夠，因為 Linux 端不一定掛載同一個 vault，且 Codex 需要可直接在專案 repo 內讀取的交接狀態。

建議每個正式專案補齊：

| 檔案 | 用途 |
|---|---|
| `current-state.md` | 最短目前狀態，供 `startup` 快速讀取 |
| `handoff.md` | 給下一台電腦或新對話的可執行交接 |
| `worklog.md` | 可被 git 追蹤的工作紀錄 |
| `tasks.md` | 待辦、決策、阻塞 |
| `runbook.md` | 啟動、測試、部署與平台注意事項 |
| `.project-session/active-session.json` | active session 提醒，不進版控，不當可靠鎖 |

Obsidian `工作筆記.md` 仍保留作為人的駕駛艙與長期紀錄；專案內狀態檔則作為跨機器與 git 可追蹤的接續資料。

---

## 設計原則

1. `專案顯示名稱` 可以中文，但 `專案代號` 應穩定
2. `GitHub repo slug` 不假設等於顯示名稱
3. `Obsidian 工作筆記` 用相對於 vault 的路徑表示即可
4. 跨設備路徑用欄位與變數描述，不把單一 OS 絕對路徑當規則
5. 專案內狀態檔與 Obsidian 工作筆記要能互相對照
4. `startup` / `shutdown` 應把這裡視為單一真相來源

---

## 不建議的寫法

- 只寫專案名稱，不寫 repo
- 只寫 repo，不寫工作筆記位置
- 把 Obsidian 路徑寫成模糊描述
- 依賴 skill 內硬編碼專案路徑
