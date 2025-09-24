# 開發日記 - Day 2

**日期**: 2024年1月17日  
**主要工作**: Express 專案配置、PM2 進程管理、Docker 環境優化

## 今天做了什麼

### Express 專案設定
- 使用 Express 建立基礎專案結構
- 配置基本路由和中間件
- 了解 bin/www 啟動腳本的作用

### PM2 進程管理
- 學習使用 PM2 管理 Node.js 應用
- 在 Docker 中配置 PM2
- 使用 pm2-runtime 確保容器中的應用正常運行
- 了解如何使用 ecosystem.config.js 管理多個應用

### Docker 環境優化
- 調整 docker-compose.yml 中的 nodejs 服務配置
- 解決 volumes 掛載的 ContainerConfig 錯誤
- 優化工作目錄和專案路徑設置
- 學習如何在一個容器中管理多個 Node.js 專案

## 踩到的坑

1. Docker volumes 配置問題
   - 錯誤：ContainerConfig KeyError
   - 解決：使用 type: bind 明確指定 volume 類型
   - 移除了可能導致問題的 volume 選項

2. PM2 在 Docker 中的使用
   - 問題：容器重啟後 PM2 進程消失
   - 解決：使用 pm2-runtime 而不是普通的 pm2 命令

## 明天想做什麼

1. 完善 Express 應用功能
2. 添加更多 API 路由
3. 研究 PM2 的進階功能（如負載均衡）
4. 優化開發環境的配置

## 心得

今天主要在處理專案的基礎架構，學到了很多關於 Node.js 應用部署的知識。PM2 是個強大的進程管理工具，特別是在 Docker 環境中的應用場景。Docker 的配置雖然遇到一些問題，但通過解決這些問題，更深入理解了 Docker 的運作機制。
