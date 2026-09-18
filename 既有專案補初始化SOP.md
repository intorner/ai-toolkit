# 既有專案補初始化 SOP

> 版本：v0.3
> 更新日期：2026-09-18

用途：把 legacy Project 收斂到 current repository bootstrap，而不重寫 domain truth或功能。

## 1. Read-only audit first

先確認：
- repository / branch / remote / dirty state
- `CLAUDE.md`
- `current-state.md`
- accepted Method/Spec/handoff（只有直接相關才讀）
- shared capability是否由 `codex-sync` 管理
- local path / Obsidian / host/tool bindings是否被錯當 authority

先分類：
- `NO_CHANGE`
- `THIN_REFRESH_REQUIRED`
- `LEGACY_MODERNIZATION_REQUIRED`

## 2. Authority modernization

必要時最小修正：
- `current-state.md` → Current Truth
- `CLAUDE.md` → bootstrap/control entrypoint
- shared routing → thin `codex-sync` redirect
- Obsidian/local path/tool binding → projection only
- legacy single-source statements → superseded，不刪除必要 history

不得把 shared GB10/RDC/Codex/Hermes規則全文複製到 consumer repo。

## 3. Missing state files

只建立真正缺少且 current workflow需要的：
- `current-state.md`
- `handoff.md`
- `worklog.md`
- `runbook.md`
- `tasks.md`

不要為形式預建空 history/checkpoint/docs/scripts/tools 目錄。

## 4. Preserve existing work

- 不 reset / checkout / delete user changes。
- 不修改功能程式、runtime設定、credential。
- local dirty/stale copy不是 canonical remote stale。
- 若 authoritative remote/current source可讀，read-only分析可直接以 current authority為準，不先破壞 local working copy。

## 5. Git / remote

Git mutation與初始化內容修改分離：
- status/branch/remote read可做 read-only inspection。
- `git init/add/commit`、remote create/change、push都需 Human明確授權。
- 不因「補初始化」自動推定 commit/push authorization。

## 6. Optional work-note

Obsidian/work-note若已有，可保留作 operational projection；若沒有，不因缺 work note阻斷 repository modernization。

## 7. Validate

依 `初始化驗證清單.md`確認：
- authority分層正確
- shared routing externalized
- side-effect boundaries未被擴張
- domain truth/functionality未被重寫
- legacy paths/bindings不再是 permanent authority
