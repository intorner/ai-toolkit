# ai-toolkit Runbook

## 用途

本專案主要維護跨專案初始化規格、模板與 SOP 文件。

## 基本檢查

```bash
git status --short
git pull --ff-only
```

## 注意事項

- `startup` / `shutdown` 相關規則變更後，應回頭檢查 `專案初始化模板.md`、`既有專案補初始化SOP.md`、`初始化驗證清單.md` 是否一致。
- 若本次只是低風險狀態檔初始化，commit 範圍只限狀態管理檔。
