# whoami — CLAUDE.md 角色設定產生器（Claude Code Skill）

一句話說「你是誰＋規則」，這個 skill 就用問答幫你釐清角色，產出一份**結構完整、可直接當專案／助理角色設定的 `CLAUDE.md`**，存進你目前的資料夾。

> A Claude Code skill that turns a one-line "who are you + rules" into a well-structured `CLAUDE.md` role/instructions file, saved into your current folder.

## 這是什麼

- **輸入**：你說「我誰」（或「幫我寫 CLAUDE.md」「設定一個角色」…）。
- **過程**：用 `AskUserQuestion` 一次問完關鍵變因（身分、目標、語言、語氣、輸出格式、禁止事項），不臆測。
- **輸出**：一份含「身分／核心職責／規則／語氣格式／限制／完成標準」的 `CLAUDE.md`。

## 安裝

把 `whoami` 資料夾放進 Claude Code 的 skills 目錄即可：

```bash
git clone https://github.com/chensoo8911/whoami-skill.git
mkdir -p ~/.claude/skills/whoami
cp whoami-skill/SKILL.md ~/.claude/skills/whoami/SKILL.md
```

或用 symlink（source of truth 留在 clone 下來的 repo，之後 `git pull` 就自動更新）：

```bash
git clone https://github.com/chensoo8911/whoami-skill.git ~/somewhere/whoami-skill
ln -s ~/somewhere/whoami-skill ~/.claude/skills/whoami
```

裝好後重開 Claude Code session，說「我誰」就會觸發。

## 觸發詞

「我誰」「幫我寫 CLAUDE.md」「產生 instructions」「設定一個角色／助理」「whoami」或語意相近時。

## 安全鐵則

- 只產生「專案／角色用」的 `CLAUDE.md`，**絕不覆寫全域 `~/.claude/CLAUDE.md`**。
- cwd 是家目錄或不像專案的位置時，會先問你要存哪裡。
- 目前資料夾已有 `CLAUDE.md` 時，會先問要覆寫、改名還是換資料夾。

## License

MIT
