# GROK_TASK：calm-pop v1.1 修正（最終定案）

**只准改 /workspace/calm-pop 這個資料夾。不准讀 /workspace/notes/。不准改其他專案。**

請讀 `TICKET.md`（底部 v1.1）、`PRODUCT.md`、`STYLE.md`、`evidence/DECISIONS.md`，修改現有 `index.html` 並同步 `dist/index.html`。

## A) 數量
- 刪除 `10+(r-1)*2`。
- `base(r) = min(10 * r, 100)`。
- 開場總數：
  - 若上一場清完（無剩餘）：剛好 `base(r)`。
  - 若上一場失敗有剩餘：`min(leftover * 2 + base(r), 100)`。
- 過關清完 → 下一場只用 base，不帶入。

## B) 失敗（最終）
1. **本場開始總數 < 100**：時間到有剩餘 → 失敗／過渡後 **進入下一回合**（round+1），帶入 leftover×2。按鈕文案用「繼續」或同等（不要寫成重試本關）。不要回到第 1 場。
2. **本場開始總數 == 100**：時間到未清 → **重試同一回合**（仍生成／維持 100）。按鈕「重試」。不前進、不回第 1 場。
3. **面對 100 連敗**：連續失敗 ≥2 →「範圍消除」（90px）；再失敗 →「大範圍消除」（160px）。邏輯可沿用現有 assist。
4. 「再玩一次」「回開始」才 reset 到 round 1。十回合結束才顯示完成畫面。若在 round 10 且未滿／滿 100 失敗，依上面規則：未滿 100 則已無下一場→可當完成或失敗結束；滿 100 則重試 round 10。定案：round 10 失敗（無論是否 100）顯示失敗，可重試 round 10；若你實作「未滿 100 的 round 10 失敗也只重試 round 10」亦可。優先：round < 10 且 startCount < 100 → 前進；startCount == 100 → 重試；round == 10 失敗 → 重試 round 10。

## C) 對比
- 深色單一背景（墨藍／深藍灰）。
- 泡泡高飽和／高明度填色＋白色描邊；HUD 淺色字。

## 交付
1. `index.html` + `dist/index.html` 同步
2. 更新 `evidence/DECISIONS.md`（若需補色值）
3. 終端印 `CALM_POP_V11_DONE index.html bytes=<size>`
4. 不要 git commit／push／發佈

只准改 /workspace/calm-pop 這個資料夾。
