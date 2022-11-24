---
title: Ruby on Rails-1115
date: 2022-11-15 16:33:15
tags: 
description: Ruby on Rails
---
## JS暫存問題
### 早期
利用查詢字串的方式，每秒換新的數字，告訴瀏覽器這是不同的檔
### 後期
利用打包工具產生代碼，會去判斷，如果內容一樣，代碼不變，會有暫存效果，內容有改則換另一個代碼。

## 沒認證錯誤 Action Controller::InvalidAuthenticity Token

當表單寫入時會擋，為了防止有人亂傳的機制

解法：
```
<input type="hidden" name="authenticity_token">
```
或是推薦以下form_for寫法：
```ruby=
<%= form_for @wish_list, url: "/create_wish" do |f| %>
  <div>
    <%= f.label :title %>
    <%= f.text_field :title %>
  </div>
  <div>
    <%= f.label :description %>
    <%= f.text_area :description %>
  </div>
  <%= f.submit %>
<% end %>
```

## 沒清洗錯誤 Active Model::ForbiddenAttributesError

當整包資料寫入時會擋，為了防止有人亂傳的機制

解法，清洗動作：
```ruby=
clean_params = params.require(:wish_list).permit(:title, :description)  

@wish_list = WishList.new(clean_params)
```
