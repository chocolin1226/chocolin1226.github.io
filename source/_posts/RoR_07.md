---
title: find/ find_by/ find_by！/ where
date: 2022-11-17 16:33:15
tags: 
description: Ruby on Rails
---
## .find/ find_by/ find_by！/ where

| .find(id) | find_by(key: value) | find_by！(key: value) | where(key: value) |
| --- | --------- | ------------------- | --------------------- |
| 找不到會噴訊息 (ActvieRecord::RecordNotFound) | 找不到噴nil   | 找不到會噴訊息 (ActvieRecord::RecordNotFound) | 找不到回傳空陣列[] |
| 只會撈一筆資料 回傳都是單一元素| 只會撈一筆資料 回傳都是單一元素 | 只會撈一筆資料 回傳都是單一元素  | 拿到的是陣列 一次找多筆資料 |

## 將顯示的內文自動換行

```ruby
 <%= simple_format(@wish_list.description) %>
```

## UJS = Unobtrusive JavaScript

非侵入式JS
目的是為了不要在html內放JS語法。

## form_with / form_for / form_tag

| form_with(Hash) | form_for(model)  | form_tag(url) |
| -------- | -------- | -------- |
| 會依據內容判斷是 form_for 或 form_tag ，但比form_for少了class和id屬性，可自行加| 不能是nil    | 網址     |

