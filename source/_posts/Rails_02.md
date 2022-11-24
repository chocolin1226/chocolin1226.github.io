---
title: 添加icon/多對多關聯
date: 2022-11-18 16:33:15
tags: 
description: Rails專案
---

## 添加icon
下載套件[fontawesome](https://fontawesome.com/docs/apis/javascript/get-started)
```
$ yarn add @fortawesome/fontawesome-svg-core
$ yarn add @fortawesome/free-solid-svg-icons
```

## 多對多 關聯

```
$ rails g model LikeWishList user:belongs_to wish_list:belongs_to
```
```ruby=
  has_many :like_wish_lists
  has_many :liked_wish_lists, through: :like_wish_lists, source: :wish_list
```

```ruby=
  has_many :like_wish_lists
  has_many :liked_users, through: :like_wish_lists, source: :user
```



![](https://railsbook.tw/images/chapter18/many-to-many-tables.png)
![](https://railsbook.tw/images/chapter18/many-to-many-model.png)


圖片取自[為你自己學Ruby](https://railsbook.tw/chapters/18-model-relationship)
