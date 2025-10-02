# 開發日記 - Day 3

**日期**: 2025年10月2日  
**主要工作**: Node.js 開發環境優化 - 導入 nodemon 自動重啟功能

## 今天做了什麼

### 學習 nodemon 自動重啟功能
- 了解 nodemon 的作用：監控檔案變更自動重啟應用
- 學習兩種實現方式：
  1. 使用 nodemon 套件
  2. 使用 Node.js 18+ 內建的 --watch 功能

### 專案配置優化
- 修改 `/home/user/SideProjects/nodejs-practice/package.json`
- 新增 dev script：`"dev": "nodemon ./bin/www"`
- 新增 watch script：`"watch": "node --watch ./bin/www"`

### Docker 環境整合
- 修改 `/home/user/SideProjects/docker-web/nodejs/Dockerfile`
- 全域安裝 nodemon：`RUN npm install nodemon -g`
- 調整 docker-compose.yml 使用自定義 Dockerfile
- 成功在容器中安裝 nodemon 3.1.10 版本

### 實際測試
- 重新建構 Docker 容器
- 驗證 nodemon 在容器中正常運作
- 確認可以使用 `npm run dev` 啟動開發模式

## 踩到的坑

1. Docker 容器配置錯誤
   - 錯誤：ContainerConfig KeyError 導致容器無法啟動
   - 解決：先停止並移除現有容器，再重新建構

2. 工作目錄路徑問題
   - 錯誤：在 `/var/www` 執行 npm 找不到 package.json
   - 解決：需要切換到正確路徑 `/var/www/nodejs-practice`

## 明天想做什麼

1. 實際測試 nodemon 的檔案監控功能
2. 探索 nodemon 的進階配置選項
3. 研究如何在 Docker 環境中優化開發流程
4. 考慮整合其他開發工具提升效率

## 心得

今天學到了 nodemon 這個非常實用的開發工具，大大提升了開發效率。不用每次修改程式碼都手動重啟，這對開發體驗來說是質的提升。

在 Docker 環境中整合開發工具需要考慮更多細節，但一旦配置好就能享受到容器化帶來的一致性優勢。透過修改 Dockerfile 和 docker-compose.yml，成功將 nodemon 整合到現有的開發環境中。

這次的經驗讓我更深入理解了 Docker 的建構流程，以及如何在容器中安裝和配置開發工具。
