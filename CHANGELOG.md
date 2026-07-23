# Changelog

本檔案記錄 claude-whoami 的變更歷史。格式參考 [Keep a Changelog](https://keepachangelog.com/zh-TW/1.1.0/)。

版本號採 [Semantic Versioning](https://semver.org/lang/zh-TW/)：MAJOR.MINOR.PATCH。

## [Unreleased]

## [1.1.1] — 2026-07-23

### Changed
- **觸發詞收斂**：SKILL.md 觸發詞由「我誰／幫我寫 CLAUDE.md／產生 instructions／設定一個角色／助理／whoami／語意相近時」精簡為只留「我誰」「幫我寫 CLAUDE.md」，與權威路由表一致（守住「不加別名」政策，避免 skill 自行擴張觸發語與正本漂移）。

## [1.1.0] — 2026-07-22

### Changed
- **產出改為「全域感知」**：生成專案 `CLAUDE.md` 前先讀使用者全域 `~/.claude/CLAUDE.md`；已被全域涵蓋的語氣／格式／資料紅線／通用規則**不再重複寫進產出**（同一規則兩處維護會失去單一正本），改用一句「依全域」帶過，主體只寫該專案特有的 delta。
- SOP 問答改為「**先讀全域、只問全域沒有又會改變產出方向的缺料**」；輸出範本的「語氣與格式」「限制」區塊改為「全域已涵蓋即省略」。

### Added
- **與全域衝突的確認機制**：若要寫進專案的規則和全域規範**矛盾／收緊／放寬**，先停下問使用者以哪個為準，不自行定奪、不靜默覆蓋全域；確認後才寫並註明「（經確認，本專案覆寫全域）」。

## [1.0.0] — 2026-07-15

### Added
- 首次正式發版：CLAUDE.md 角色設定產生器。使用者說「我誰」（或「幫我寫 CLAUDE.md」「設定一個角色」），用 `AskUserQuestion` 一次問完關鍵變因，產出結構完整的專案／角色用 `CLAUDE.md`。

### Changed
- Repo 更名 `whoami-skill` → `claude-whoami`，統一 `claude-*` 命名慣例；安裝說明改用 owner-中性寫法，方便任何人 fork 使用。
