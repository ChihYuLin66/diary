# 開發日記 - Day 4

**日期**: 2025年10月03日  
**主要工作**: Express Todo 應用開發 + MongoDB 整合

## 今天做了什麼

### Express Todo CRUD 功能完成
- 實作了完整的 Todo 應用 CRUD 操作
- 使用 Express.js 建立 RESTful API
- 完成新增、讀取、更新、刪除功能

### 首次使用 MongoDB
- 學習 MongoDB 基本操作
- 實作資料庫連接和查詢
- 掌握 MongoDB 更新操作符（$set, $inc, $push 等）
- 理解 ObjectId 的使用方式

### 開發工具優化
- 發現並開始使用 MongoDB Compass
- 視覺化資料庫管理讓開發更順利
- 可以直接查看和編輯資料庫內容

## 踩到的坑

### MongoDB ObjectId 問題
- 一開始用字串 id 查詢，但 MongoDB 使用 ObjectId
- 解決方法：使用 `new ObjectId(req.params.id)` 轉換
- 查詢條件要用 `_id` 而不是 `id`

### 更新操作語法
- 忘記使用 `$set` 操作符
- MongoDB 需要明確指定更新操作類型
- 學會了各種更新操作符的用法

## 明天想做什麼

- 優化 Todo 應用的前端介面
- 加入資料驗證和錯誤處理
- 探索更多 MongoDB 進階功能

## 心得

今天是第一次真正接觸 NoSQL 資料庫，MongoDB 的文檔導向設計確實和關聯式資料庫很不同。MongoDB Compass 這個 GUI 工具真的很好用，讓我能夠直觀地看到資料結構和查詢結果，大大提升了開發效率。

雖然踩了一些坑，但透過實作學到了很多實用的知識，特別是 ObjectId 的概念和各種更新操作符的使用。感覺對 Node.js + MongoDB 的開發流程更熟悉了！ 🚀
