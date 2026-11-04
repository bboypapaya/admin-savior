# 🛡️ 行政救星 Admin Savior

[![100% Offline](https://img.shields.io/badge/100%25_Offline-純本機離線運算-28a745?style=for-the-badge)](#)
[![CSP Zero Upload](https://img.shields.io/badge/CSP_connect--src_'none'-瀏覽器級零外傳鎖死-007bff?style=for-the-badge)](#)
[![Release](https://img.shields.io/badge/Release-v2.0.0-6f42c1?style=for-the-badge)](https://github.com/bboypapaya/admin-savior/releases/latest)
[![Visitors](https://visitor-badge.laobi.icu/badge?page_id=bboypapaya.admin-savior&style=for-the-badge)](#)

**[繁體中文](#-專案簡介) | [English](#-project-overview)**

---

## 📌 專案簡介

**《行政救星 Admin Savior》** 是一款專為行政人員、人資、公務機關與一般民眾打造的 **100% 純本機離線公文與雙證件影像處理工具**。

在日常申辦業務或處理公文時，我們常收到拍得歪斜、隔著透明卡套反光泛霧、帶有手機黑影，或是檔案太大無法上傳至政府/銀行系統的身分證與健保卡照片。傳統做法不是要開啟肥大的修圖與排版軟體耗時處理，就是得冒著敏感個資外洩的風險，將證件上傳至來路不明的免費線上工具。

本專案將所有影像矩陣運算、檔案大小精準壓縮與 PDF 生成技術封裝於**單一、100% 語意化開源的 `index.html` 檔案**中，透過瀏覽器內建的 `HTML5 Canvas` 在您自己的電腦或手機記憶體內完成處理，並於標頭寫入嚴格的 **`Content-Security-Policy (connect-src 'none')` 瀏覽器級資安鎖**——**無後端伺服器、無資料庫、無外部追蹤腳本，拔掉網路線或開啟飛航模式依然能 100% 正常運作**。

---

## 🚀 立即使用與離線下載

* 🌐 **線上立即開啟（電腦 / 手機皆可，支援建立手機桌面捷徑）**：
  👉 **[https://bboypapaya.github.io/admin-savior/](https://bboypapaya.github.io/admin-savior/)**
* 💻 **電腦版單一檔案離線下載（下載後無須網路，雙擊即可開啟）**：
  👉 **[點此直接下載最新版 `index.html` (v2.0.0)](https://github.com/bboypapaya/admin-savior/releases/latest/download/index.html)**（或前往 **[Releases 頁面](https://github.com/bboypapaya/admin-savior/releases/latest)** 查看完整更新日誌）

---

## 🎬 操作示範

![行政救星操作示範 Demo](https://raw.githubusercontent.com/bboypapaya/admin-savior/main/demo.gif)

---

## ✨ v2.0.0 核心功能與工程亮點一覽

| 功能模組 | 實務痛點解決與技術亮點 |
| :--- | :--- |
| **🗂️ 置頂 3 大頁籤 ＋ 底部匯出列**<br>*(v2.0.0 黃金動線配置)* | 頂部精簡為單行控制列（`選圖 / ↩ 上一步 / ↪ 下一步 / 🔄 重置 / 🌐 語系`）搭配 **3 大置頂修圖頁籤**，並將所有複製、下載與 PDF 匯出按鈕獨立於**畫布正下方**，最大化手機與筆電可視畫布空間，徹底終結上下來回滑動。 |
| **📐 智慧梯形校正與比例適配**<br>*(順逆時針自動修正 ＋ 即時微調)* | 點擊拍歪證件或公文的 4 個角落瞬間拉正（內建 **`normalizeQuad` 順逆時針自動方向正規化**，絕不產生鏡像圖）。預設自動拉正為各國法定證件尺寸 **`85.6×54mm`**（具備 **300DPI 列印清晰度保底** 與 **3×3 邊緣微銳化**）；校正後**免重選 4 角**，拉動 **「↔ 寬高自由微調」** 滑桿即可即時預覽調整。 |
| **👆 手機觸控偏心放大鏡** | 手機點選梯形頂點時，紅十字準星自動偏移於指尖上方並搭配青色引導線，左上/右上放大鏡（`88px`）具備頂角自動避讓機制，搭配統一 `Pointer Events` 系統，手指絕不擋住對位視線。 |
| **✨ 智慧去霧清晰化**<br>*(保留全彩・拯救泛霧與淡字)* | 針對隔著卡套翻拍、光線昏暗或反光泛霧的各類彩色證件、駕照、護照與銀行存摺，一鍵執行 **高動態範圍去霧 (Auto-Percentile HDR) ＋ 積分圖局部清晰度反差 (Clarity) ＋ Gamma 微增亮 ＋ 自然飽和度補償 (Vibrance) ＋ 邊緣銳化**，加深淡色字跡與存摺點陣字，同時保護大頭照膚色自然不失真。 |
| **📄 公文去陰影黑白強化**<br>*(智慧保留紅藍印章)* | 採用共用 `Uint32Array` 積分圖局部自適應演算法（記憶體消耗減半），一鍵消除手機翻拍公文時的桌面陰影並轉為高對比白底黑字；內建 **「保留彩色印章」** 色相偵測，自動保留紅色印泥與藍色公章。 |
| **🪪 雙證件正反面合併**<br>*(含 iOS 畫布安全上限護欄)* | 處理完證件正面後點擊「1️⃣ 暫存正面」，接著載入反面影像，即可一鍵完成 **「↕ 上下合併」** 或 **「↔ 左右合併」**，自動留白對齊並內建 `capCanvasBox` 長邊安全上限，防止突破行動裝置畫布限制。 |
| **🔏 滿版防盜浮水印 ＋ 📅 今日日期** | 支援自訂文字與 **「📅 插入今日日期」** 按鈕（自動帶入 `YYYY/MM/DD`），一鍵壓印滿版交錯斜向浮水印，提供 **半透明深灰、印泥紅、公文藍** 3 種專業配色，防範證件遭盜用且不遮蓋重要字跡。 |
| **⬛ 個資黑塊與不可逆馬賽克** | 提供常駐連續繪製的 **「⬛ 個資黑塊」** 與 **「局部馬賽克」**（動態採用短邊 `1/40` 且不小於 `28px` 之區塊真實平均 RGB，徹底抹除文字特徵），拖曳即可快速遮蔽敏感個資。 |
| **🖍️ 無紙化標註 ＋ 動態復原/重做** | 支援連續繪製 **「🟥 紅框標註」** 與 **「🖍️ 紅底線標註」**（接近水平自動拉直）；內建記憶體位元組預算制（`UNDO_BUDGET`）之 **上一步 (`Ctrl+Z`) / 下一步 (`Ctrl+Y`)** 與 `Escape` 快速退出模式。 |
| **💾 目標檔案大小壓縮下載**<br>*(PNG / JPG ≤ 2MB・1MB・500KB)* | 內建下載格式與大小選單（`PNG 無損`、`JPG 高畫質`、`JPG ≤ 2MB`、`JPG ≤ 1MB`、`JPG ≤ 500KB`），以二分搜尋法自動調配品質與尺寸，輕鬆通過政府與銀行網站的上傳大小限制。 |
| **📤 獨立紙張規格與 1:1 PDF 匯出** | 內建獨立之 **「📄 紙張：A4 / US Letter」** 選單（與介面語言解耦），直接於瀏覽器端生成 **「留 10mm 邊距縮放適應 PDF」** 或 **「證件 1:1 實際尺寸 (85.6×54mm) PDF」**（印出來即為真實身分證大小且保持比例不變形）。 |
| **📲 桌面捷徑與 9 國語系** | 內嵌動態繪製之「深藍盾牌」App 圖示，支援 iOS / Android **加入手機主畫面捷徑**（含 LINE / Threads 內建瀏覽器偵測引導）與 **繁中、英、日、德、韓、法、荷、西、瑞典** 9 國語系切換。 |

---

## 🛡️ 資安承諾與 5 大公開查驗方式

處理身分證、健保卡、存摺與內部公文時，**「資訊安全」是不可妥協的底線**。本工具不要求您相信口頭保證，您可隨時透過以下 5 種科學方式親自查驗：

1. **瀏覽器底層 `CSP` 強制鎖死**：本網頁於 `<head>` 設有 `Content-Security-Policy: default-src 'none'; connect-src 'none'`，由瀏覽器核心引擎直接封鎖任何對外連線能力（即便寫入連線指令亦會被瀏覽器強制攔截）。
2. **檢視 100% 語意化開源原始碼**：全專案僅一個 `index.html` 純文字檔，無任何壓縮混淆、無任何外部第三方套件（0 Dependencies）。您可以直接按 `Ctrl+F` 搜尋是否有任何網路傳輸語法（如 `fetch`、`XMLHttpRequest`、`WebSocket`、`sendBeacon`），結果為 **0 個**。
3. **交由 AI 進行逐行資安審計**：您可直接複製本專案的 `index.html` 原始碼，貼給 ChatGPT、Claude 或 Gemini，詢問：「*這段程式碼是否有留後門、植入木馬或將圖片上傳至外部伺服器？*」即可立即獲得客觀驗證。
4. **瀏覽器封包監控 (`F12` Network)**：在網頁按下 `F12` 開啟開發者工具並切換至 `Network（網路）` 分頁，載入照片、去霧清晰化、壓印浮水印或匯出 PDF，對外發送的網路封包全程為 **0 Bytes**。
5. **物理斷網執行**：將 `index.html` 下載至電腦並拔除網路線，或於手機開啟「飛航模式」後再載入證件處理，在物理層面上 100% 隔絕任何外傳可能。

---

## ☕ 贊助支持與免責聲明

本專案為免費開源工具，旨在提升第一線行政人員的工作效率並守護大眾的個資安全。如果這個小工具幫您省下了寶貴的時間、讓您能多喝一杯咖啡，歡迎隨緣贊助支持開發者持續維護：

* 💳 **台灣本地贊助（綠界科技 ECPay）**：[https://p.ecpay.com.tw/04052B1](https://p.ecpay.com.tw/04052B1)
* ☕ **海外與小額贊助（Ko-fi）**：[https://ko-fi.com/bboypapaya](https://ko-fi.com/bboypapaya)

> **⚖️ 服務條款與免責聲明**：
> 1. **純本機運算聲明**：本工具所有影像處理功能皆於使用者端瀏覽器沙盒記憶體內執行，開發者不蒐集、不傳輸、亦不留存任何使用者之圖片或個人資料。
> 2. **無對價贈與說明**：本工具所有功能皆為 100% 免費開放使用，無任何付費解鎖或會員分級機制。上述贊助連結純屬使用者基於認同本開源專案理念之**自願性無償贈與（打賞）**，無涉及任何商品買賣或對價勞務關係。
> 3. **聯絡資訊**：如有功能建議或專案合作事宜，歡迎透過 GitHub Issues 聯繫開發者（`bboypapaya`）。

---
---

## 📌 Project Overview

**Admin Savior** is a **100% offline, client-side document and ID card image processing web application** designed for administrative staff, HR professionals, civil servants, and everyday users who value privacy.

When handling ID cards, health insurance cards, bank passbooks, or official documents, we often deal with skewed photos, hazy glare through plastic sleeves, heavy phone shadows, or strict file-size upload limits (`1MB` / `500KB`) on government and banking portals. Uploading sensitive personal IDs to unknown third-party online tools poses severe privacy risks.

Admin Savior packs all matrix transformations, adaptive image enhancements, target file-size compression, and PDF generation into a **single, clean, semantic `index.html` file** powered by `HTML5 Canvas` and locked down with a strict **`Content-Security-Policy (connect-src 'none')`**. **There is no backend server, no database, and zero external uploads—it works 100% normally even with your internet disconnected or in Airplane Mode.**

---

## 🚀 Live Web App & Offline Download

* 🌐 **Live Web App (PC / Mobile, supports Home Screen App Shortcuts)**:
  👉 **[https://bboypapaya.github.io/admin-savior/](https://bboypapaya.github.io/admin-savior/)**
* 💻 **Offline Single-File Download (Double-click to run offline on any PC/Mac)**:
  👉 **[Download Latest `index.html` (v2.0.0) Directly](https://github.com/bboypapaya/admin-savior/releases/latest/download/index.html)** (or visit the **[Releases Page](https://github.com/bboypapaya/admin-savior/releases/latest)** for release notes)

---

## ✨ Key Features (v2.0.0)

| Feature | Description & Technical Highlights |
| :--- | :--- |
| **🗂️ 3 Sticky Tabs + Bottom Export Bar**<br>*(Mobile-First Ergonomics)* | Combines a compact **1-Line Top Bar** (`Choose File / Undo / Redo / Reset / Language`) with **3 Sticky Editing Tabs** above the canvas, while placing all copy, download, and PDF export controls in a dedicated **Bottom Export Bar** right below the canvas. |
| **📐 Smart Keystone & Auto-Orientation**<br>*(Mirror-Free Quad Sorting)* | Click 4 corners in clockwise or counter-clockwise order (`normalizeQuad` automatically prevents mirrored output). Normalizes to international standard ID card size (**`85.6×54mm`**) with a **300 DPI floor**, **3×3 edge micro-sharpening**, and a live **Fine-Tune Aspect Slider**. |
| **👆 Mobile Touch-Offset Magnifier** | On mobile devices, the red crosshair automatically offsets above your fingertip with a cyan tracking line, paired with an auto-dodging `88px` corner magnifier and unified `Pointer Events`. |
| **✨ Smart Dehaze & Clarity**<br>*(Full-Color Enhancement)* | Designed for hazy, dim, or glare-affected ID cards, driver's licenses, passports, and bank passbooks. Combines **Auto-Percentile HDR Dehazing, Integral-Image Local Contrast (Clarity), Gamma Brightening, Vibrance Boost, and Edge Sharpening** while preserving natural portrait skin tones. |
| **📄 Document B&W Enhancement**<br>*(Preserves Colored Stamps)* | Uses fast shared `Uint32Array` integral-image adaptive thresholding to remove phone shadows and convert documents into crisp black-and-white text, featuring a smart **"Keep Colored Stamps"** detector to preserve red and blue official seals. |
| **🪪 ID Card Front & Back Merger**<br>*(with iOS Canvas Safeguard)* | Temporarily store the processed front image in memory, load the back image, and merge them **Vertically** or **Horizontally** with one click, complete with automatic alignment, clean white padding, and `capCanvasBox` protection. |
| **🔏 Tiled Watermark + 📅 Date Stamp** | Apply custom angled full-page watermarks with a one-click **"📅 Insert Date"** button (`YYYY/MM/DD`) in **Translucent Dark Gray, Stamp Red, or Official Blue**. |
| **⬛ Blackout & Block-Averaged Mosaic** | Continuous drag-and-draw modes for **⬛ Blackout Redaction** and **Local Mosaic** (using dynamic `1/40` short-edge blocks `>= 28px` with true block-averaged RGB) to irreversibly mask sensitive numbers. |
| **🖍️ Highlighting + Byte-Budget Undo/Redo** | Continuous drawing modes for **Red Boxes** and **Red Underlines** (auto-straightens near horizontal), backed by dynamic byte-budget **Undo (`Ctrl+Z`) & Redo (`Ctrl+Y`)**. |
| **💾 Target File-Size Compression**<br>*(PNG / JPG ≤ 2MB・1MB・500KB)* | Built-in format and size selector (`PNG Lossless`, `JPG High Quality`, `JPG ≤ 2MB`, `JPG ≤ 1MB`, `JPG ≤ 500KB`) using binary-search JPEG encoding to easily pass strict portal upload limits. |
| **📤 Independent Paper Size & Local PDF** | Features a dedicated **Paper Size Selector (`A4` / `US Letter`)** decoupled from UI language. Generates **10mm-Margin Fit PDFs** or **1:1 Actual-Size ID Card PDFs (`85.6×54mm`)** directly in your browser. |
| **📲 Home Screen Shortcuts & 9 Languages** | Built-in dynamic high-res shield app icon generator, supporting iOS/Android Home Screen shortcuts and instant switching across **9 languages** (`zh-TW`, `en-US`, `ja`, `de`, `ko`, `fr`, `nl`, `es`, `sv`). |

---

## 🛡️ Privacy Guarantee & 5-Way Verification

We believe in **verifiable security** rather than verbal promises. You can verify Admin Savior's zero-upload architecture anytime:

1. **Browser-Enforced `CSP` Lock**: The page header enforces `Content-Security-Policy: default-src 'none'; connect-src 'none'`, blocking any outbound network connection at the browser engine level.
2. **Inspect the Clean Source Code**: The entire application lives in a single, human-readable `index.html` file with zero external dependencies. Search for any network API (`fetch`, `XMLHttpRequest`, `WebSocket`, `sendBeacon`)—there are **none**.
3. **Audit with AI**: Copy the `index.html` code and ask ChatGPT, Claude, or Gemini: *"Does this code contain any backdoors, trojans, or upload images to any server?"*
4. **Monitor Network Traffic (`F12`)**: Open your browser's Developer Tools (`F12` -> `Network` tab). Load images, apply enhancements, add watermarks, and export PDFs—outbound traffic remains **0 Bytes**.
5. **Run Completely Offline**: Turn on Airplane Mode or unplug your Ethernet cable before loading your ID photos.

---

## ☕ Support & Disclaimer

Admin Savior is 100% free and open-source. If this tool saves you time and boosts your daily efficiency, feel free to buy me a coffee:

* 💳 **ECPay (Taiwan Local Support)**: [https://p.ecpay.com.tw/04052B1](https://p.ecpay.com.tw/04052B1)
* ☕ **Ko-fi (International Support)**: [https://ko-fi.com/bboypapaya](https://ko-fi.com/bboypapaya)
