---
title: 兩個JS controller 溝通/隨機產生12位數亂碼
date: 2022-11-24 17:33:15
tags: 
description: Rails專案
---

## 金流處理方式
### 幕前
即時付款(信用卡)
### 幕後處理
非同步處理，沒有馬上付錢(匯款) 

## ngork 套件
可以產生「暫時的網址」
## dotenv 套件
處理環境變數 或 機要資訊（金鑰）

## 處理兩個JS controller 溝通
參考這裡[fullstackheroes](https://fullstackheroes.com/tutorials/stimulus/create-custom-events/)

```ruby=
const event = new CustomEvent("update-map");
window.dispatchEvent(event);
```
```ruby=
data-action="update-map@window->map#updateHotspotLocation"
```

## 隨機產生12位數亂碼

```ruby=
before_validation :generate_serial

private

  def generate_serial
    self.serial = SecureRandom.alphanumeric(12)
  end
```