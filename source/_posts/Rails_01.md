---
title: 路徑/加密/關聯
date: 2022-11-18 16:33:15
tags: 
description: Rails專案
---
## 當要建立前台路徑

```ruby=
resource :user, as: "users"
```

1. 可使用resource 會缺少id(不會看到別人的）, index（不會有所有列表）
2. resource單數 :user也是單數
3. 慣例上會去找users_path但我們是用單數去長，所以要再做給他`as: "users"`

## 為密碼加密

```ruby=
private
  def encrypt_password
    self.password =Digest::SHA256.digest(self.password)
  end
```

## cookie 與 session
1. server伺服器 拿的是session
2. client瀏覽器（使用者） 拿的是cookie
3. 類似點餐時會有取單號碼牌

## 快速製作使用者（包含登入登出）
下載套件
diveser 或 Sorcery

## 建立關聯性
WishList <-> User
1. 在User.rb => `has_many: wish_lists`
2. 在WishLst.rb => `belongs_to :user`

* 可以單獨存在，有查詢需求才需要添加。