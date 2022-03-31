---
title: SSH & HTTPS 
date: 2022-03-31 17:23:46
categories: 版本控制
tags: Git
---

兩種不同與Ｇit平台數據庫連接方式比較

:::info
SSH key 彈性高，必須要是專案管理員才能拉檔案
HTTPS 有網址的皆可以clone下來，需要輸入帳號密碼
:::

<!-- more -->

SSH
---
產出<font color='#f00'>**一對公鑰及私鑰**</font>，私鑰存在本地端，公鑰則上傳到Github或Gitlab些版本控制平台上供辨識，push不需要輸入帳號密碼

### 使用
1. 檢查電腦是不是已經有ssh key了，如果有了請跳過步驟二
`cd ~/.ssh`
`ls`
![](https://i.imgur.com/YLqjnq3.png)
取得公鑰
`cat id_rsa.pub `

2. 建立新的SSH key
`ssh-keygen -t rsa -C "你的email地址"`

3. 將SSH key 放到平台上，視不同平台加入
舉Gitlab為例子
![](https://i.imgur.com/bDsXnsW.png)


HTTPS
---
取得網址就可以clone，~~每次push時需要輸入帳號密碼(可以利用keychain去儲存帳號資料就可以不用每次都輸入)~~，現在改成需要<font color='#f00'>**Personal Access Token**</font> 來做推送

先用Github來做範例

1. 取得clone URL
![](https://i.imgur.com/M45tnjr.png)


2. 建立Personal Access Token
![](https://i.imgur.com/DyRhWab.png)


3. push

    加入遠端數據庫
    ```
    git remote add origin https://[token]@github.com/[username]/[repository]
    ```

    設定遠端設定
    ```
    git remote set-url origin https://[token]@github.com/[username]/[repository]
    ```
