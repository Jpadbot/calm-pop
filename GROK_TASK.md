# GROK_TASK：calm-pop v1.2（範圍點擊模式＋暫停）

**只准改 /workspace/calm-pop 這個資料夾。不准讀 /workspace/notes/。不准改其他專案。**

請讀 `TICKET.md`（底部 v1.2）、`PRODUCT.md`、`STYLE.md`、`evidence/DECISIONS.md`，修改現有 `index.html` 並同步 `dist/index.html`。**保留 v1.1 的數量／失敗規則不變。**

## 1) 範圍消除改為點擊模式
- 未解鎖（`assist < 1`）：維持現狀——點一下消除一顆泡泡。
- 解鎖「範圍消除」（assist≥1）或「大範圍」（assist≥2）後：
  - **不要**再用底部按鈕單次清一塊就結束。
  - **每一次**在遊戲區（canvas）上的點擊，都以觸點為中心、依 `assistRadius`（約 90／160 CSS px）清除圓內所有泡泡，並顯示範圍環特效。
  - 底部按鈕改為不可點的提示標籤（例如「範圍消除中」／「大範圍消除中」），或隱藏按鈕、改在 HUD 顯示「範圍消除中」。
  - 解鎖條件維持 v1.1（面對 100 連敗）。

## 2) 暫停／返回目錄
- 對局中（play／celebrate 可選）顯示可點「暫停」——建議右上角小按鈕，或拇指易達但不蓋太多泡泡的位置。
- 暫停時：倒數／deadline 凍結（類似 visibility hidden 的 drift 處理）；顯示暫停面板，含：
  - 「繼續」→ 恢復對局並補償暫停時長到 deadline
  - 「返回目錄」→ 回主選單（等同 goStart／開始畫面）
- 介面繁體中文。暫停時不要繼續判失敗。

## 交付
1. 改好 `index.html`，複製到 `dist/index.html`
2. 更新 `evidence/DECISIONS.md` 寫明 v1.2：點擊範圍模式、暫停行為；註明底部單次清除已廢止
3. 終端印 `CALM_POP_V12_DONE index.html bytes=<size>`
4. 不要 git commit／push／發佈

只准改 /workspace/calm-pop 這個資料夾。
