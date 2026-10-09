# GROK_TASK：calm-pop v1.1 修正

**只准改 /workspace/calm-pop 這個資料夾。不准讀 /workspace/notes/。不准改其他專案。**

請讀 `TICKET.md`（底部「v1.1 修正」）、`PRODUCT.md`、`STYLE.md`、`evidence/DECISIONS.md`，然後修改現有 `index.html`（並同步 `dist/index.html`）。

## 必須改的三項

### A) 數量公式（刪除舊公式）
- 刪除 `10 + (r-1)*2` 與跨回合「剩餘×2 帶入下一回合」。
- 第 r 回合開始時：清空畫面，生成剛好 `min(10 * r, 100)` 個泡泡。
  - r=1 → 10；r=2 → 20；r=3 → 30；…；r≥10 → 100。
- 過關（清完）→ 進入下一回合，重新依公式生成，不帶入上一場剩餘。

### B) 失敗重試
- 時間到仍有剩餘 → 失敗畫面。
- 「重試」：保持**同一回合號**與**同一目標數** `min(10*r,100)`，重新生成該場泡泡（簡單重置即可；不必在重試時×2）。
- 只有「再玩一次」或「回開始」才回到第 1 回合。
- 失敗畫面上的文案／按鈕保持繁中；確認不會誤把 round 設回 1。

### C) 對比（依 STYLE.md）
- 背景：單一深色（深藍灰／墨藍），勿接近泡泡填色。
- 泡泡：高飽和或高明度填色＋明顯白色／淺色描邊；半透明不可低到與背景糊成一片。
- HUD／按鈕文字在深背景上要可讀（必要時改淺色字）。

### 範圍消除（保留）
- 仍保留：面對 100 且連續失敗兩次 →「範圍消除」；再失敗 →「大範圍消除」。半徑 90／160 可維持。

## 交付
1. 改好 `/workspace/calm-pop/index.html`
2. 複製到 `/workspace/calm-pop/dist/index.html`
3. 更新 `/workspace/calm-pop/evidence/DECISIONS.md` 寫明新公式、已移除跨場×2、失敗重試行為、對比色值
4. 終端印：`CALM_POP_V11_DONE index.html bytes=<size>`
5. 不要 git commit、不要 push、不要發佈

開始修改。只准改 /workspace/calm-pop 這個資料夾。
