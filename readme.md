# 使用 Node.js + Express 的短網址系統
簡單的 MVC 架構實作，並使用 ORM 套件 Sequelize 串接資料庫  

**MVC架構**  
- 大部分的路由邏輯都歸屬在 controller 中，例如 index.js 中包含首頁展示和縮網址的實際處理回傳，而 redirect.js 處理了短網址的查詢和轉址。  
- 與資料庫相關的設定和邏輯，則歸屬在 model 資料夾中，這裡主要處理了 Sequelize 資料物件以及與 MySQL 的串接的設定。
-  views 是 Express 預設的 HTML 模板引擎使用的資料夾，這裡選用的是 EJS。

**ORM套件 Sequelize**  
ORM技術將關聯式資料庫映射至物件導向資料，所以不需要直接撰寫 sql statement 來做 query，而是用類似操作 object 的方式操作關聯式資料庫。例如查詢資料的語法：
```
Url.findAll({
      where: { shorten_url: req.params.shortenUrl }
    })
    .then( result => {
      //do somthine when query success
    })
    .catch( err => {
      //do something when error occurs
    })
  }
```
Sequelize 支援 ES6 的 promise 語法，而 `Url` 是在 model 中預先定義好的資料物件。

**主機系統**  
- 主機：AWS EC2  
- 系統：ubuntu 16.04 / NodeJS 8.11 / Express 4  
- 使用 PM2 套件於伺服器端運行。  


