# GROK_TASK：calm-pop v1.3（滿 100 第一次失敗即開小範圍）

**只准改 /workspace/calm-pop 這個資料夾。不准讀 /workspace/notes/。不准改其他專案。**

請讀 `TICKET.md`（底部 v1.3）、`PRODUCT.md`、`evidence/DECISIONS.md`，修改 `index.html` 並同步 `dist/index.html`。保留 v1.1 未滿 100 規則與 v1.2 點擊範圍模式／暫停。

## 必改
1. **滿 100 第一次失敗**即解鎖「小範圍消除」（assist=1）。不要等第二次失敗。
   - `reduceFail`：當 `roundStartCount >= 100` 時，streak 到 1 就 `assist = 1`；若已是 1 再失敗則升到 2（大範圍）。
   - `reduceUnlock`：改為 `failStreak >= 1` 即可解鎖（或與 reduceFail 對齊，避免重試開場時漏解鎖）。
2. **縮小小範圍半徑**：由 ~90 改為 **60 CSS px**（介於 55–65）。大範圍維持 ~160（或略縮亦可，建議仍 160）。
3. UI 文案：小範圍可用「小範圍消除中」或維持「範圍消除中」；大範圍「大範圍消除中」。仍是提示標籤，不是單次按鈕。
4. 未滿 100：失敗仍前進＋剩餘×2，不累計這條連敗／不解鎖。

## 交付
- 改 `index.html` → 複製 `dist/index.html`
- 更新 `evidence/DECISIONS.md`（寫明：第一次失敗解鎖；小半徑 = 60；大 = 160）
- 印 `CALM_POP_V13_DONE index.html bytes=<size>`
- 不要 git commit／push

只准改 /workspace/calm-pop 這個資料夾。
