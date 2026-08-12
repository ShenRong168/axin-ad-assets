# axin-ad-assets

阿信嚴選（1010.gold 廣告帳號代投）**廣告素材圖床**。

## 用途

Meta 的 `ads_creative_upload_image` 只接受**公開網址**——伺服器自己去下載圖片，
不吃本機路徑、不吃 base64、不吃 Google Drive／Dropbox 分享連結（會被登入頁擋掉）。
這個 repo 開了 GitHub Pages，把圖 push 上來就會變成可直連的公開網址，餵給 Meta 用。

## 怎麼用

```bash
cd /Volumes/fast/CODEX/axin-ad-assets && cp <你的圖> assets/ && git add assets/ && git commit -m "add: <素材說明>" && git push
```

push 完等 GitHub Pages build（約 30～60 秒），網址就是：

```
https://shenrong168.github.io/axin-ad-assets/assets/<檔名>
```

拿這個網址呼叫 `ads_creative_upload_image`，會回傳 image hash，再用 hash 建 creative。

## 注意事項

- **這個 repo 是公開的。** GitHub Pages 在免費方案只能從公開 repo 發布。
  只放要拿去投廣告的素材——那些本來就會公開曝光。**不要放**客戶的合約、報價、
  名單、後台截圖或任何不該被搜尋到的東西。
- 檔名用**英文小寫加連字號**，不要中文、不要空格（中文檔名會被 URL-encode，容易出錯）。
- 圖片格式限 JPEG / PNG / GIF，單檔上限 30 MB。
- 素材汰換不要直接覆蓋同檔名——已經在跑的廣告仍指向舊的 image hash，
  換圖請用新檔名（例如 `-v2`），舊檔留著當存檔。
- 如果是「加強推廣粉專既有貼文」，圖已經在 Facebook CDN 上了，
  creative 直接用該貼文的 `object_story_id` 即可，**不需要**經過這個圖床。

## 相關

- 專案背景與權限：見 Obsidian vault
- 榮心紳語自己的圖床是另一個 repo（`rongxin-shenyu`，網域 rongxinshenyu.com），兩邊不互相寫入
