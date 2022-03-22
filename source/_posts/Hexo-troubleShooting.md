---
title: TroubleShooting
date: 2022-03-22 16:35:07
tags: Hexo
categories: 前端開發
---

### 執行hexo deploy時發現personal access token 過期了，導致無法上版
```shell=
remote: No anonymous write access.
fatal: Authentication failed for 'https://github.com/wayne201299/wayne201299.github.io/'
FATAL {
  err: Error: Spawn failed
      at ChildProcess.<anonymous> (/Users/ci-alan.zhuang/blogpsn/node_modules/hexo-util/lib/spawn.js:51:21)
      at ChildProcess.emit (node:events:390:28)
      at Process.ChildProcess._handle.onexit (node:internal/child_process:290:12) {
    code: 128
  }
} Something's wrong. Maybe you can find the solution here: %s https://hexo.io/docs/troubleshooting.html
```
* 更新config.yaml<font-color=#> 內的repo加上token
```yaml=
deploy:
  type: git
  repo: https://[personalAccessToken]@github.com/wayne201299/wayne201299.github.io.git
  branch: main
  token: [personalAccessToken]
```
### Hexo更新後，本地端的node如果沒更新，新語法會報錯
* 檢查node版本有沒有支援新語法
