# 專案初始化 skill 化評估

> 版本：v0.1
> 更新日期：2026-06-05

## 結論

專案初始化適合做成 Codex skill，但不應把完整規格硬寫死在 skill 內。

建議做成 `project-initializer` 或 `project-bootstrap` skill，職責是：

- 偵測使用者是否要建立新專案或補初始化既有專案
- 讀取 `ai-toolkit` 的表單、模板、欄位規格、跨設備路徑規則與驗證清單
- 引導使用者補齊缺少欄位
- 依規格建立或補齊專案文件
- 初始化或檢查 git
- 建立 Obsidian 工作筆記
- 最後依 `初始化驗證清單.md` 驗證

規格真相仍留在 `ai-toolkit` 文件內。skill 只做「入口、導引、套用、驗證」。

## 為什麼適合做 skill

目前「專案初始化」已經具備明確觸發語、固定 SOP、固定模板與驗證清單，符合 skill 的條件：

| 條件 | 判斷 |
|---|---|
| 有穩定觸發語 | 有，例如 `開始新專案`、`我要幫既有專案補初始化` |
| 有固定輸入表單 | 有，`新專案初始化表單.md` |
| 有固定輸出 | 有，`README.md`、`CLAUDE.md`、狀態檔、`.gitignore`、Obsidian 工作筆記 |
| 有可驗證完成條件 | 有，`初始化驗證清單.md` |
| 需要跨對話重複使用 | 有，Windows / Linux / NAS 都需要同一流程 |

## 不應放進 skill 的內容

以下內容不應硬寫在 skill 裡：

- 完整 `CLAUDE.md` 模板內容
- 完整 `.gitignore` 模板內容
- 完整狀態檔模板
- Windows / Linux 實際路徑清單
- 個別專案的 GitHub repo 或 Obsidian 路徑
- API key、token、機器專屬設定

這些應維持在 `ai-toolkit` 文件或每台本機設定中。

## 建議 skill 名稱

首選：`project-initializer`

理由：

- 語意直接，涵蓋新專案與既有專案補初始化
- 不和 `startup` / `shutdown` 混淆
- 比 `project-bootstrap` 更容易讓中文使用者理解

可接受別名：

- `project-bootstrap`
- `專案初始化`

## 建議觸發語

```text
開始新專案
我要開始新專案
我要初始化新專案
我要初始化一個新專案
開一個新專案
建立新專案
新專案初始化
我要幫既有專案補初始化
幫這個專案補 CLAUDE.md
補齊專案初始化規格
```

## skill SOP

### 1. 判斷任務類型

- 新專案：使用 `新專案初始化表單.md`
- 既有專案：使用 `既有專案補初始化SOP.md`

### 2. 讀取規格來源

依序讀：

1. `README-初始化規則.md`
2. `跨設備路徑規則.md`
3. `CLAUDE欄位規格.md`
4. `專案初始化模板.md`
5. `初始化驗證清單.md`

### 3. 補齊欄位

至少確認：

- 專案顯示名稱
- 專案代號
- 工作根目錄
- Linux 對應路徑
- GitHub repo slug
- Obsidian 工作筆記
- 平台支援
- 是否建立 GitHub remote
- 是否需要 Stop 備份白名單

### 4. 建立或補齊專案文件

最小輸出：

```text
README.md
CLAUDE.md
current-state.md
handoff.md
worklog.md
runbook.md
tasks.md
.gitignore
.gitattributes
docs/
scripts/
tools/
```

### 5. 建立 Obsidian 工作筆記

固定位置：

```text
<OBSIDIAN_VAULT_ROOT>/專案庫/<專案代號>/工作筆記.md
```

如果 Linux 端 Obsidian vault 尚未確認，skill 應標記待確認，不要猜測。

### 6. git 初始化或檢查

- 新專案：可初始化 git，但建立 GitHub repo 前需使用者確認
- 既有專案：只盤點 remote，不覆蓋 remote
- 無 remote 是合法狀態，但要明確回報

### 7. 驗證

依 `初始化驗證清單.md` 檢查，最後回報缺口。

## 和 startup / shutdown 的分工

| skill | 時機 | 主要動作 |
|---|---|---|
| `project-initializer` | 新專案或補初始化時 | 建立規格、文件、工作筆記、git 起點 |
| `startup` | 開工接續時 | 讀 `CLAUDE.md`、專案內狀態檔、Obsidian 工作筆記、git 狀態 |
| `shutdown` | 收工同步時 | 寫專案內狀態檔、Obsidian 工作筆記、commit / push |

## 安全邊界

skill 必須遵守：

- 不共用整個 `.codex` runtime / cache / auth / session
- 不把 `.env`、API key、token、憑證寫進共享文件
- 不把 `.project-session/` 進版控
- 不主動覆蓋既有 remote
- 不主動刪除既有檔案
- 建立 GitHub repo、push、寫 Obsidian vault、修改本機 Codex skills 前，都應依當前環境權限取得確認

## 目前實作狀態

截至 2026-06-05，Windows 本機已建立 `project-initializer` skill 草案：

```text
C:\Users\intor\.codex\skills\project-initializer\SKILL.md
C:\Users\intor\.codex\skills\project-initializer\agents\openai.yaml
```

目前草案已完成：

- 觸發語與 skill description
- `ai-toolkit` 規格來源讀取順序
- 新專案 / 既有專案補初始化分流
- 標準輸出檔案清單
- Obsidian 工作筆記建立規則
- git 初始化 / 既有 repo 檢查邊界
- 安全規則與 `startup` / `shutdown` 分工

驗證狀態：

- 已用 PowerShell 做等價基本驗證：`SKILL.md` frontmatter、skill name、description、`agents/openai.yaml` 與 `ai-toolkit` 規格引用均正常。
- 尚未執行 `skill-creator/scripts/quick_validate.py`，原因是目前 Windows Codex shell 找不到可用的 `python` 或 `py`。這不影響文字規則 skill 運作，但會影響 Python 驗證腳本與初始化腳本。

## 建議後續

1. 用 `_Codex-Sync` 或低風險教材專案試跑 Windows 本機 `project-initializer` 草案。
2. 補可用 Python 後，執行 `skill-creator/scripts/quick_validate.py` 驗證 skill。
3. 根據試跑結果修正 `project-initializer`。
4. 修改 Windows `startup` / `shutdown` skills，讓它們讀寫專案內狀態檔。
5. 驗證通過後，再讓 Windows 與 Altos GB10 F1 各自安裝同等 skill。
