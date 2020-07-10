```
├── Dockerfile   用來包裝該 web server 方便之後部署並維持相同環境
├── README.md 該 web server 專案的說明文件
├── app.js 該 web server 的相關設置
├── bin
│   └── www
├── config.js  會使用 nconf 來根據環境使用 settings 底下的不同環境設定檔
├── controller
│   └── query.js 放置相關邏輯操作
├── cron
│   └── sync.js  定期去 opendata server 拉回需要資料, 會設置在 linux 的 crontab 中定時執行
├── docs
│   └── swagger.yaml  該專案的 swagger 文件, 預計會由 express middleware 自動產生
├── lib
│   ├── mongo.js  maintain mongodb connection pool 連線的地方
│   └── openapi  將 open data 相關 api 抽象化成 method, 供該專案使用
│       └── index.js
├── model
│   ├── insert.js  對所有 DB 的操作都應該由 model layer 來實現
│   └── query.js
├── package-lock.json
├── package.json
├── public  該專案前端需要使用的 static file, 例如 .css or javascript
│   ├── images
│   ├── javascripts
│   └── stylesheets
│       └── style.css
├── routes  該專案 router 設置的地方, 決定該 request 要由哪個 controller 來執行
│   └── index.js
├── schema  每個 request 的 input, output 都要經由 schema 定義的 Joi validator, 來檢查 input, output 有沒有符合要求
│   └── query.js
├── settings  放置各環境執行需要的參數, 比如 DB 的連線資訊
│   ├── dev.js
│   └── prod.js
└── views  放置最後產生 html 的 jade 模板, jade engine 會在 render 的時候生成 html 格式的資料 response 回前端
    ├── error.jade
    ├── index.jade
    └── layout.jade
└── .github/workflows  放置 github actions 相關設定, 完成 CI/CD 相關操作
└── .eslintrc 訂定 code style, 確保多人開發時能維持相同的 code style, 並透過 husky 在 commit 之前檢查, 如果有錯誤就不能 commit
```