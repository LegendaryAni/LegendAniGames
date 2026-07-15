# Sprite Forge 資產管線

本目錄用於把目前的 CSS 向量替代圖，逐步替換成 image generation 產生的原創二次元遊戲素材。

## 依賴來源

參考 `0x0funky/agent-sprite-forge`：

- `$generate2dsprite`：角色、敵人、FX、符號、動畫 sheet
- deterministic scripts：洋紅去背、despill、切格、對齊、透明 PNG/GIF、metadata

來源專案採 MIT License。使用前仍應檢查自己的生成模型、平台與商業授權條款。

## 目標目錄

```text
assets/generated/
  characters/
    akane-portrait.webp
    chrono-portrait.webp
    noctis-portrait.webp
    luna-portrait.webp
  enemies/
    rift-hound-sheet.png
    mirror-sentinel-sheet.png
    light-moth-sheet.png
    faceless-assassin-sheet.png
    inverted-bishop-sheet.png
    fate-judge-sheet.png
  symbols/
    symbol-sheet.png
  fx/
    slash-sheet.png
    burn-sheet.png
    shield-sheet.png
    fate-burst-sheet.png
  backgrounds/
    route-map.webp
    battle-rift.webp
```

## 角色立繪規格

- 透明背景 WebP
- 直式半身像，建議 1024×1536
- 主體不得超出畫布
- 光源方向一致：左上主光、右下輪廓光
- 四名角色必須維持相同鏡頭、比例與渲染密度
- 不使用現有動漫 IP、角色服裝、標誌或高度近似臉部設計

## 戰鬥 Sprite 規格

- `4x2` sheet，共 8 幀
- 洋紅 `#FF00FF` 背景，後處理轉透明
- 每格相同尺寸，角色腳底基準線一致
- 動作在原地完成，不位移出格
- 保留至少 8% 透明安全邊界

## UI 符號規格

- `3x3` sheet，共 9 個符號
- 斬擊、護盾、熾炎、修復、晶幣、命印、侵蝕、萬用、空相
- 深色介面可讀，形狀輪廓優先，不依賴細小文字
- 每格單一物件、置中、留白一致

## 接線方式

1. 依 `prompts/` 生成原始 sheet。
2. 使用 Agent Sprite Forge 去背、切格與輸出。
3. 將結果放到 `assets/generated/`。
4. 在 `index.html` 增加 `<img>` 圖層，保留現有 CSS silhouette 作為載入失敗 fallback。
5. 在 `game.js` 的 `HEROES`、`ENEMIES`、`SYMBOLS` 資料中加入 `asset` 路徑。
6. 以 `object-fit: contain` 接入，不改變遊戲版面尺寸。

## 驗收條件

- 角色身份在不同素材中一致
- 動畫無切邊、無洋紅殘邊
- 256px 顯示尺寸仍可辨識角色與敵人
- 符號縮到 48px 仍能以輪廓區分
- 首屏總圖片體積低於 1.5MB
- WebP 靜態素材與 PNG 透明 sheet 分開管理
