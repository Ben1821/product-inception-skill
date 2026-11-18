# Product Inception

把一個軟體產品構想，變成一份**能開工的「開工包」**的 Agent Skill。

用完之後，你手上會有一份文件，能回答四件事：

1. **要做什麼**：收斂後的題目、和現有做法的差異定位，以及原構想的核心保留了多少
2. **做到什麼算完成**：依你的終點（期末 Demo、比賽、首批試用…）寫成的完成定義
3. **明天先做什麼**：1–2 週內可完成、每項都有完成證據的第一輪工作
4. **不確定的事先怎麼處理**：每個未知都有預設做法、若錯要改什麼，以及你自己做得到的查證方式

適合個人、學生與小型團隊，可在 Claude（claude.ai、Claude Code）、Codex 等支援 Agent Skills（`SKILL.md` 格式）的工具中使用。

> *English: A skill that turns a software product idea into an actionable kickoff pack — scope, definition of done, first-iteration tasks, and defaults for open questions — via discovery, story mapping, MVP definition, architecture exploration, and development planning. Content is in Traditional Chinese.*

## 它怎麼帶你走

1. **先問專案情境**：終點與期限、人力與技術、能接觸到哪些使用者或資料。「做到什麼」由這些條件決定。
2. **主動找案例**：問完情境後，查現有解法、事件案例與跨領域類比，收斂成一句定位，作為選方向時的差異化依據。
3. **五個階段**：產品探索 → 使用者故事地圖 → MVP 定義 → 初步架構探索 → 開發規劃。
4. **重大方向由你決定**：要縮小題目時，它會給 2–3 個方向和取捨讓你選，不會自己替你改題目。
5. **正面處理最難的部分**：不用「模擬」或「AI 輔助」帶過關鍵難題。
6. **每輪顯示進度**：`目前階段｜已確認｜下一個要決定的事`
7. **最後交付開工包**：你說「整理一下」或「下一步」時就會產出（[模板](product-inception/assets/00-kickoff-pack.md)）。

## 安裝

Skill 本體是 [`product-inception/`](product-inception/) 這個資料夾。

**Claude Code**

```bash
git clone https://github.com/Ben1821/product-inception-skill.git
cp -R product-inception-skill/product-inception ~/.claude/skills/
```

只想在某個專案用的話，改放到該專案的 `.claude/skills/`。使用時輸入 `/product-inception`。

**Codex**

```bash
cp -R product-inception-skill/product-inception ~/.codex/skills/
```

只想在某個專案用的話，放到專案的 `.agents/skills/`。也可以在 Codex 裡用 `$skill-installer` 安裝這個 repo 的 `product-inception` 路徑。使用時輸入 `$product-inception`。

**claude.ai／Claude 桌面版**

從 [Releases](../../releases) 下載 `product-inception.zip`，或自行壓縮：

```bash
zip -r product-inception.zip product-inception -x '*.DS_Store'
```

到 **Customize › Skills**，按「+」→「Upload a skill」，上傳 zip。

## 使用範例

```
/product-inception 我想做一個校園二手書交易平台
```

```
/product-inception 這是一學期的課程專題，兩個人，會 Swift。直接給我開工包草案
```

```
/product-inception 只審查第 3 階段，文件在 docs/03-mvp-spec.md
```

## 檔案結構

```
product-inception/
├── SKILL.md          # 主要指示：目的、互動原則、品質關卡、五階段流程
├── references/       # 各階段方法（探索、故事地圖、MVP、架構、規劃、判斷規則）
├── assets/           # 文件模板（開工包、Brief、Story Map、MVP Spec、ADR、Backlog…）
├── examples/         # 五階段完整案例、好壞對照
└── evals/            # 行為評估案例，供維護與回歸測試
```

## 評估與貢獻

[`evals/cases.json`](product-inception/evals/cases.json) 收錄了一組人工評估案例：每案有輸入提示、應觀察的行為，以及會讓該案失敗的錯誤。做法見 [`evals/README.md`](product-inception/evals/README.md)。

歡迎開 Issue 或 PR。若用起來不符預期，附上對話紀錄最有幫助。

## 授權

MIT，見 [LICENSE](LICENSE)。
