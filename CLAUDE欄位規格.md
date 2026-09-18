# CLAUDE.md 欄位規格

> 版本：v0.4
> 更新日期：2026-09-18

`CLAUDE.md` 是 Project bootstrap/control entrypoint，不是單一 Current Truth。

## Required content

每個長期 / repository-backed Project 的 `CLAUDE.md` 至少應表達：

| 欄位/區塊 | 用途 |
|---|---|
| Project identity | 顯示名稱、代號、repository |
| Project purpose / scope | 這個 Project 負責什麼、不負責什麼 |
| Current Truth pointer | 通常指向 `current-state.md` |
| Authority precedence | Project truth / shared authority / projections |
| Startup bootstrap | 先讀什麼、何時停止 document expansion |
| Shared capability redirect | 只指向 `codex-sync`，不複製 shared routing |
| Authorization boundary | write/deploy/runtime/security等需 Human 授權 |
| Do Not Reopen | 已 CLOSED/PASS/OPERATIONAL 不為 reassurance 重驗 |
| Optional projections | local path / work note / platform support，如有 |

## Authority rules

- `current-state.md` 保存目前有效 Current Truth。
- `CLAUDE.md` 保存固定 bootstrap / project governance / authority pointers。
- Method / Spec / runbook / evidence各自保留正式 authority。
- Obsidian/work note可作 fast-changing operational projection，但不是 mandatory authority。
- local working copy、drive letter、host path、model、MCP/tool binding、runner都是 current projection/binding，不得寫成跨設備永久 truth。
- chat memory / historical conversation不是 authority。

## Shared routing

如果 Project 會使用 shared AI engineering / GB10 capability，`CLAUDE.md` 應只保留 thin redirect：

```markdown
## Shared Capability Redirect
- Shared AI engineering authority: `codex-sync`.
- 涉及 shared capability 時，先做 existing-capability discovery並依 canonical routing選最窄 route。
- 不在本 Project 複製 capability trigger、host/runner/model、fallback 或 mutable runtime detail。
- 若涉及 GB10，讀 `codex-sync/docs/gb10-gpt-bootstrap.md` 與 canonical capability-routing index。
```

不得把某個 Codex/Hermes/RDC/host綁定寫成永久 primary route。

## Minimal template

```markdown
# <Project Name>

## Project identity
- Project code: `<code>`
- Repository authority: `<owner/repo 或 local-only>`
- Current Truth: `current-state.md`
- Shared AI engineering authority: `codex-sync`（若適用）

## Purpose / Scope
- <in scope>
- <out of scope>

## Authority
1. Project Current Truth / accepted Method/Spec
2. Human accepted decisions/evidence
3. shared `codex-sync` authority（若適用）
4. local/managed projections
5. chat/memory reference only

## Startup
1. Read `CLAUDE.md`.
2. Read `current-state.md`; judge sufficiency/freshness.
3. Read only directly relevant downstream docs.
4. For shared capability, follow canonical routing.
5. Do not reopen CLOSED/PASS/OPERATIONAL work for reassurance.

## Shared Capability Redirect
- Keep shared routing externalized to `codex-sync`.
- For GB10, use the canonical GB10 bootstrap/routing.
- Human uses natural language; agent resolves Skill/workflow/route.

## Authorization
Repository/Git write, remote write/push, deployment, runtime/service, model/backend, package install, destructive filesystem, network/security, credential/secret and privilege operations require explicit Human authorization.

## Optional local projections
- Work root: `<optional local path>`
- Work note: `<optional semantic locator>`
- Platform notes: `<optional>`
```

## Prohibited legacy patterns

不要生成：
- 「`CLAUDE.md` 是單一真相來源」
- 「若 CLAUDE 與 Current Truth 不同，以 CLAUDE 為主」
- 固定 Windows drive / Vault root 作跨設備 authority
- 固定 Codex / Hermes / RDC / Obsidian MCP 作 permanent executor
- 把初始化 request 當作 Git commit/push authorization
- 把所有 capability trigger複製進 consumer repo

## Relationship to ChatGPT Project Instructions

ChatGPT Project Instructions 不由本文件生成；其 canonical generator contract是：

`codex-sync/docs/chatgpt-project-bootstrap-library.md`

兩者必須一致，但 authority分工不同：
- ChatGPT Project Instructions：project-level conversational governance
- Repository `CLAUDE.md`：repository bootstrap/control entrypoint
