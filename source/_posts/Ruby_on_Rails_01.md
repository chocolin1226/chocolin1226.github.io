---
title: 怎麼new一個rails專案？
date: 2022-11-26
tags: 
description: Ruby on Rails 之 CRUD 新手記憶弱區
---

## 最基本方式
```
$ rails new <專案名稱>
```

## 特定版本方式
```
$ rails _6.1.7_ new <專案名稱>
```

## 遇到的錯誤訊息
Invalid application name test. Please give a name which does not match one of the reserved rails words: application, destroy, plugin, runner, test

### 解：

不能用特殊字(application, destroy, plugin, runner, test)當專案名稱。