# 澳門停車場即時車位查詢（家人專用）

**單一檔案網頁 App**：手機瀏覽器直接調用澳門政府開放數據 API，無伺服器、無需電腦開機。

- 數據來源：澳門特區政府數據開放平台（交通事務局 DSAT）· APPCODE 為平台公開密鑰
- 技術形態：純靜態單頁（`index.html`）+ PWA，手機本地 60 秒快取減少 API 請求
- 家人密碼：`moka2026`（寫在前端，防君子不防小人；如需真保密需加後端）

## 部署到 GitHub Pages（免費、永不休眠）

1. 在 GitHub 新建一個倉庫（如 `macau-parking`，免費版需公開倉庫）
2. 把本目錄檔案推送上去：

```bash
git init
git add index.html icon.png manifest.webmanifest README.md
git commit -m "澳門停車場即時車位 v1"
git remote add origin https://github.com/你的帳號/倉庫名.git
git push -u origin main
```

3. 倉庫 Settings → Pages → Source 選 `main` 分支根目錄 → Save
4. 約 1 分鐘後訪問 `https://你的帳號.github.io/倉庫名/`

> 想倉庫不公開但免費部署：改用 Cloudflare Pages（支援私有倉庫，免費）。

## iPhone 上「變成 App」

1. Safari 打開網址 → 輸入密碼 `moka2026` 進入
2. 分享 → **加入主畫面**
3. 桌面出現「澳車位」圖示，點開即為全螢幕 App 形態

## 日常維護

- **改家人密碼**：編輯 `index.html` 中 `const ACCESS_CODE = 'moka2026'`，重新推送
- **政府新增停車場**：頁面會提示「未分類」；在 `index.html` 的 `REGIONS` 表按 ID 加一行 `"停車場ID":"macau|taipa|coloane"`，重新推送
- 區域歸類約定：路氹城歸氹仔、石排灣歸路環，可按認知自行調整

## 檔案說明

| 檔案 | 作用 |
|---|---|
| `index.html` | 全部：介面、樣式、邏輯（政府 API 直達調用） |
| `manifest.webmanifest` | PWA 配置（加入主畫面所需） |
| `icon.png` | App 圖示 |
