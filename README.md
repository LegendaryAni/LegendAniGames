# 命輪少女：零界迴廊

二次元角色構築 × 可操作式 Slot × Roguelike 路線選擇的純前端網頁原型。

## 已實作

- 4 名規則完全不同的命輪使
- 5 軸 × 3 列 Slot，包含 5 條 Payline
- 鎖軸、重轉、結算三階段決策
- 9 種符號與可視化權重
- 一般戰、精英戰、Boss 戰
- 敵人意圖、護盾、燃燒、污染與封印
- 12 件規則型遺物
- 休整、商店與隨機事件
- 6 層完整 Roguelike 流程
- 響應式桌面與行動版介面
- GitHub Pages 自動部署設定

## 本機執行

此專案不需要建置工具。

```bash
python -m http.server 8080
```

開啟 `http://localhost:8080`。

## 操作

1. 選擇角色並進入零界。
2. 在地圖選擇節點。
3. 戰鬥時先旋轉，再鎖定需要保留的轉軸。
4. 使用重轉調整結果，最後結算。
5. 取得遺物或調整符號權重，建立本局流派。

鍵盤：`Space` 旋轉，`Enter` 結算。

## Agent Sprite Forge / Image Generation 資產流程

`sprite-forge/` 內含角色、敵人、符號與背景的生成規格。流程依照 [0x0funky/agent-sprite-forge](https://github.com/0x0funky/agent-sprite-forge) 的 `generate2dsprite` 與 deterministic post-processing 思路設計。

目前版本使用 CSS 向量化替代圖，確保倉庫可直接運行。生成完成後，依 `sprite-forge/ASSET_PIPELINE.md` 的命名規則放入 `assets/generated/`，即可逐步替換角色立繪、敵人 Sprite、符號與特效。

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

## 設計原則

Slot 是玩家可以構築與操控的戰鬥系統，而不是被動發獎機制。角色、遺物、敵人與事件都直接改變轉輪規則、權重或風險。

## 授權

程式碼採 MIT License。原創角色與世界觀名稱保留作為本原型內容。
