# 開發日記 - Day 1

**日期**: 2024年9月18日  
**主要工作**: Docker 環境擴充 + Node.js 專案建立

## 今天做了什麼

### 🐳 Docker 環境大升級
今天主要在搞 Docker 環境，原本只有 PHP + MariaDB 的組合，覺得不夠用，所以決定大擴充一波！

新增了一堆服務：
- **Node.js** - 用 Node 20 完整版，不是 Alpine（因為要用 bash 和 zsh 比較方便）
- **MongoDB** - NoSQL 資料庫，配了管理員帳號 admin/secret
- **Redis** - 快取資料庫，也是用 secret 當密碼
- **Redis GUI** - 視覺化管理介面，跑在 8081 port
- **Elasticsearch** - 搜尋引擎，跑在 9200 port

整個 docker-compose.yml 變得超豐富，現在有 PHP 三個版本 + 各種資料庫 + 開發工具，感覺像個小型雲端環境了 😎

### 🔧 踩到的坑
最大的坑就是容器間的網路連接問題！Node.js 容器一直無法解析 `my-mongodb` 這個主機名，一直噴 `getaddrinfo EAI_AGAIN` 錯誤。

試了各種方法，最後發現只要 `docker-compose restart nodejs mongodb` 就解決了。原來是 Docker 的 DNS 解析有時候會卡住，重啟容器讓它重新建立網路連接就好了。

學到一課：遇到容器間連不通的問題，先試試重啟！

### 📝 Node.js 專案建立
建了一個新的練習專案 `nodejs-practice`，裡面包含：
- **MongoDB 連接範例** - 用官方 mongodb driver
- **Express 網頁伺服器** - 簡單的 CRUD 操作
- **基本的 .gitignore** - 把該忽略的檔案都加進去了

網頁可以正常訪問 http://localhost:3001，能顯示 MongoDB 裡的資料，也能新增資料。感覺還不錯！

### 📚 文件更新
把 README.md 都更新了，加了繁體中文說明，包含：
- 各服務的連接資訊
- 常用指令
- 目錄結構說明
- 開發建議

現在整個專案看起來專業多了！

## 明天想做什麼
- 試試看 Redis 的操作
- 玩玩 Elasticsearch 的搜尋功能
- 可能會寫個簡單的 API 來串接這些服務

## 心得
今天主要是在建基礎設施，雖然踩了一些坑，但最後都解決了。有了這個完整的 Docker 環境，以後開發各種專案都會方便很多！

Docker 真的是個好東西，一次設定好就能到處跑，而且各種服務都隔離得很乾淨。👍
