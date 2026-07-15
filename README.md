# 命輪少女：零界迴廊

二次元角色構築 × 可操作式 Slot × Roguelike 路線選擇的純前端網頁原型。

## 已實作

- 4 名規則完全不同的命輪使
- 5 軸 × 3 列 Slot；只有中央戰線結算
- 旋轉、鎖軸、重轉、結算的清楚回合流程
- 9 種符號與即時數值說明
- 結算前預覽傷害、防禦、回復、命運與自身損傷
- 公開的敵人意圖與戰鬥紀錄
- 一般戰、精英戰與 Boss 戰
- 8 件規則型遺物
- 休整、商店與公開結果的隨機事件
- 5 層完整 Roguelike 流程
- 響應式桌面與行動版介面
- GitHub Pages 自動部署設定

## 本機執行

此專案不需要建置工具。

```bash
python -m http.server 8080
```

開啟 `http://localhost:8080`。

## 一回合操作

1. 先閱讀敵人下一步行動。
2. 按下「旋轉轉輪」。
3. 點選最多兩個轉軸保留；刻璃可保留三個。
4. 使用「重轉未鎖定」整理中央戰線。
5. 查看固定顯示的結算預覽。
6. 按下「確認結算」。

只有中央一排生效。中央戰線出現 3 個相同符號時，該符號效果 ×1.5；4 個 ×2；5 個 ×3。

鍵盤：`Space` 旋轉，`Enter` 結算。

## UI / UX 原則

- 首頁先解釋一回合，再要求選角。
- 房間風險、內容與獎勵全部公開。
- 敵人意圖固定放在戰鬥主視覺內。
- 每個符號直接顯示名稱與效果，不要求玩家背圖示。
- 結算前顯示確切數值，避免隱藏公式。
- 移除霓虹儀表板、裝飾性英文與無功能面板，改為紙本戰術盤風格。

## Agent Sprite Forge / Image Generation 資產流程

`sprite-forge/` 內含角色、敵人、符號與背景的生成規格。流程依照 [0x0funky/agent-sprite-forge](https://github.com/0x0funky/agent-sprite-forge) 的 `generate2dsprite` 與 deterministic post-processing 思路設計。

目前版本使用幾何圖形與漢字識別作為可讀性優先的替代素材。生成完成後，依 `sprite-forge/ASSET_PIPELINE.md` 的命名規則放入 `assets/generated/`，再逐步替換角色立繪、敵人 Sprite、符號與特效。

## 專案結構

```text
index.html
styles.css
game.js
sprite-forge/
  ASSET_PIPELINE.md
  prompts/
.github/workflows/pages.yml
```

## 驗證

- JavaScript 語法檢查
- HTML 解析檢查
- DOM ID 參照檢查
- 轉輪合法性測試
- 三連、五連、角色被動與詛咒反噬規則測試

受執行環境政策限制，無頭瀏覽器無法存取本機 HTTP 或 `file://`，因此尚未完成自動化端對端瀏覽器測試。

## 設計原則

Slot 是玩家可以構築與操控的戰鬥系統，而不是被動發獎機制。角色、遺物、敵人與事件都直接改變轉輪規則、資源或風險。

## 授權

程式碼採 MIT License。原創角色與世界觀名稱保留作為本原型內容。
