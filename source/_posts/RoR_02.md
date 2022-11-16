---
title: Ruby on Rails-Ruby 複習
date: 2022-11-07 16:33:15
tags: 
description: Ruby on Rails
---

## 符號v.s.字串

符號：有名字的物件，是一種值

### 1. symbol的內容不能改變
  字串想要改其中一個字是可以的，但符號不行。
   ```
   "abcd"[0] = "z"    #字串變成"zbcd"
   :abcd[0] = "z"     #錯誤訊息
   ```
### 2. symbol指到同一個記憶體位置（編號）
  字串每次的記憶體位置是不固定的，而符號是同一個記憶體位置。
   ```
   5.times do
     puts "abcd".object_id
   end
   ```
   結果分別是：720 740 760 780 800
   ```
   5.times do
     puts :abcd.object_id
   end
   ```
   結果都是：1920348
   
   *每個人電腦的記憶體位置顯示都會有差異喔！
   我的例子是用Replit執行的結果。
   
   *補充：所有數字的位置都是奇數，其他放偶數。

### 3. symbol的效能比較好

   程式在比較符號是否相同時，
   是直接比對這物件的object_id是否相同，
   但在比較字串時，
   它是一個一個字母比對，
   因此比較的時間會隨著字母的數量而增加。
   
   *補充：但因為字串位置是暫存，長期來說，不會佔記憶體位置。
   
   
## hash v.s 陣列
1. 結構不同
2. 存取方式不同
3. 沒有順序

## 題目
```
a = [1, 2, 3, 1, 2, 1, 3, 1, 2, 3, 4, 5, 6]
#請計算在陣列 a 中，每個數字出現的次數。

p a.tally
```

## ruby的省略

為了更像人在講話

可「**適時**」省略（）{} return(最後一行的執行結果)

### 回傳值意義？

為了交回控制權

### ?與!
1. 放在物件後面
2. ?不成文默契：回傳true 或 false
3. !不成文默契：有你意想不到的結果，要注意


## Rakefile

```
desc "這是測試" #描述

task :hi do
    puts "hello world"
end

desc "hey123"
task :hey => :hi do #相依性
    puts "hey!!"
end

#初始
task :default => :hi 
```


## Block
不會主動執行的程式區塊，無法單獨存活。

## 題目

```
def my_map(arr)
  result = []
  arr.each { |x| result <<( yield x) }
  result
end

list = [1, 2, 3, 4, 5]
result = my_map(list) { |x| x * 2 }

p result # [2, 4, 6, 8, 10]
```

```
def my_filter(arr)
  result = []
  arr.each { |x| result << x if yield x }
  result
end

list = [1, 2, 3, 4, 5]
result = my_filter(list) { |x| x > 2 }

p result # [3, 4, 5]
```


## 有一些方法可以使block物件化：

### Proc

使用 Proc 類別把 Block 物件化
```
say_hello_to = Proc.new { |name| puts "hi #{name}"}  
```
呼叫Proc 方式
```
say_hello_to.call("小花")    # .call
say_hello_to.("小花")        # .小括號
say_hello_to["小花"]         # 中括號
say_hello_to === "小花"      # 三個等號
say_hello_to.yield "小花"    # .yield
```

### lambda

Proc 類別下，還有一個lambda可以把 Block 物件化，
但又有些許不同。

```
say_hello_to = lambda { |name| puts "hi #{name}"} 
```
或是
```
say_hello_to = ->(name) { puts "hi #{name}"} 
```
這兩種方式都可以把 Block 物件化，
呼叫方式和Proc 相同，
不過執行上會有些許不同


---



