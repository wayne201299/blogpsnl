---
title: How browsers work?
date: 2022-04-07 14:53:06
categories: 前端開發
tags: [browser,web]
---

> 瀏覽器運作方式是所有Web工程師的都需要了解的，可以幫助我們了解網頁背後做了什麼事

本篇會先以主流的瀏覽器來做討論
* **Chrome**
* Firefox
* Internet Explorer
* Safari
<!-- more -->

## 輸入網址後發生了什麼事
1. 第一次輸入網站URL時，首先會向<font color='F000'>DNS(Domain Name Server)</font>發送lookup請求，找到相對應的<font color='F000'>IP位址</font>
2. 這時候IP會先被cache住，再次輸入網址時就不會重複再去lookup IP地址一次，但是地址中要是有不同的hostname就必需要多次呼叫(ex:image、font、script...)
3. 當IP位址確定了，會執行<font color='F000'>TCP三次握手協定</font>來確認雙方的連接狀況正常
4. 連接建立成功後，伺服器傳送資源，
5. 瀏覽器解析內容並渲染畫面

## 瀏覽器主要功能
運作方式大致是瀏覽器會主動向伺服器請求[資源]，再將接收的資源渲染到瀏覽器窗口。

這邊指的資源大部分是HTML檔案 || PDF || 圖片...等，資源的位置則是透過<font color='F000'>**URI**</font>來指定，HTML規格由W3C規範，但各瀏覽器在W3C規範下都有開發出自己的一套規則，所以帶來許多<font color='F000'>兼容性問題</font>

各瀏覽器介面共通點
* 輸入URI的地址欄
* 上一頁下一頁
* 重新整理
* 書籤
* 回到首頁

![](https://i.imgur.com/umsxUvo.png)

## 瀏覽器組成

1. Interface
使用者介面
2. The browser engine
負責UI及渲染引擎之間的互動
3. The rendering engine
負責渲染請求後的結果，例如將接收到的HTML、CSS解析出來再呈現在畫面上
4. Networking
處理網路請求(HTTP Request)，各平台間沒有差異
5. UI backend
介面的底層通用方法，各平台無差異性
6. JavaScript interpreter
解析JavaScript
7. Data storage
儲存資料，在硬碟上直接儲存，cookie、local storage、session、FileSystem...
    ![](https://i.imgur.com/PtfDSWa.png)
    *取材自[howbrowserswork](https://www.html5rocks.com/zh/tutorials/internals/howbrowserswork/)*


---

[howbrowserswork](https://www.html5rocks.com/zh/tutorials/internals/howbrowserswork/)
