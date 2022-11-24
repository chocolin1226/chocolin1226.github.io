---
title: Ruby on Rails-1114
date: 2022-11-14 16:33:15
tags: 
description: Ruby on Rails
---

## Rack(架子)

### 規格：

回應call方法,回傳一個陣列，包含：
1. http狀態(200成功，301永久/302暫時 轉移位置，401 需要輸入帳密，403 需要授權，404使用者的瀏覽器找錯地方，500內部伺服器問題)
2. header頁面(hash)，告訴伺服器要用什麼方式渲染
3. body內文

```ruby=
{
    200,
    {"content-Type" => "text/html"},
    ["內文"]
}
```

## rackup

```ruby=
class Cat
  def call(env)
    [
      200,
      {"content-type" => "text/html"}, 
      ["hello world"]
    ]
  end
end

kitty= Cat.new

run kitty
```

## rails 網頁建置步驟

**快捷鍵control+p可快速找到需要檔案**


### routes.rb（路徑）

```ruby=
get "/about", to: "pages#about"
```

### $（終端機）

```ruby=
$ rails g controller pages
```

### pages_controller.rb（中控台）

```ruby=
    def about
    end
```

### about.html.erb（畫面）

```ruby=
<h1>關於我們</h1>
```

### 超連結寫法
```ruby=
<a href="/about">關於</a>

<%= link_to "關於", "/about" %>

<%= link_to "關於", about_path %> #相對路徑

<%= link_to "關於", about_url %> #絕對路徑
```

### 新增欄位

```
$ rails g migration add_online_to_wish_list
```

```
    add_column :wish_lists, :online, :boolean, default: false
```
**記得存檔**

```
$ rails db:migrate
```
