# CLAUDE.md 欄位規格

> 版本：v0.2
> 更新日期：2026-05-03

這份文件補充 `CLAUDE.md` 在多專案工作模式中的必要欄位與用途。

---

## 必備欄位

建議每個專案的 `CLAUDE.md` 至少要能清楚表達：

| 欄位 | 用途 |
|------|------|
| 專案顯示名稱 | 給人讀的名稱 |
| 專案代號 | 路徑、資料夾、工具識別 |
| 工作根目錄 | 目前專案根目錄 |
| GitHub repo | 供 `startup` / `shutdown` 對照遠端 |
| Obsidian 工作筆記 | 供 `startup` / `shutdown` 找正確筆記 |
| Firebase 專案 | 資料來源對照，可空白 |

---

## 推薦寫法

```markdown
# <專案顯示名稱>

## 專案識別
- 專案代號：`<專案代號>`
- 工作根目錄：`<工作根目錄>`
- GitHub repo：`<GitHub帳號>/<GitHub repo slug>`
- Obsidian 工作筆記：`專案庫/<專案代號>/工作筆記.md`
- Firebase 專案：`<Firebase 專案名稱>`
```

---

## 固定欄位名稱

為了讓 `startup` / `shutdown` 能穩定解析，建議不要任意改名：

- `專案代號`
- `工作根目錄`
- `GitHub repo`
- `Obsidian 工作筆記`
- `Firebase 專案`

如果需要補充資訊，新增欄位即可，不要替換上述欄位名稱。

---

## 設計原則

1. `專案顯示名稱` 可以中文，但 `專案代號` 應穩定
2. `GitHub repo slug` 不假設等於顯示名稱
3. `Obsidian 工作筆記` 用相對於 vault 的路徑表示即可
4. `startup` / `shutdown` 應把這裡視為單一真相來源

---

## 不建議的寫法

- 只寫專案名稱，不寫 repo
- 只寫 repo，不寫工作筆記位置
- 把 Obsidian 路徑寫成模糊描述
- 依賴 skill 內硬編碼專案路徑
