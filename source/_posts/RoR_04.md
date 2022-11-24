---
title: Ruby on Rails-1111
date: 2022-11-11 16:33:15
tags: 
description: Ruby on Rails
---

## Ruby 唯二不是物件?
method , block

## 類別繼承使用時機

因為類別多了繼承的能力，
如果彼此間是有關連的，
甚至是要有另一類別內的所有能力，
可以考慮使用類別繼承。

例如我們產生一個動物類別會動、能吃東西，
然後我們要產生一樣會動、能吃東西的魚類別、鳥類別、狗類別，
我們就可以讓這三個類別都繼承動物類別，
這樣這三個類別所有實體都會動、能吃東西。

## initialize(初始化)

* 只要一出生就會執行（new實體時一並執行）
* initialize 多練習打～有四個i，打錯就沒有了
* 初始化行為又稱建構或建構子
* ＪＳ也有類似行為：constructor

## superclass(超類別/父類別)

```ruby
clss Animal
end

p Animal.superclass  #Object

p Class.superclass   #Module
p Module.superclass  #Object
p Object.superclass  #BasicObject
p BasicObject.superclass  #nil
```

## 實體與實體變數

實體是一種實體(位置)、也是一種變數。
實體變數是一種實體變數、也是一種變數，只活在實體方法內。

## RB沒有屬性只有方法,可以使用以下方式

```ruby
attr_accessor :age #可讀可寫
attr_reader :age  #可讀
attr_writer :age  #可寫

```

## 單體（例）方法 => 類別方法 v.s 實體方法

```ruby
def kitty.hi #單體（例）方法
  p "hi"
end

class Cat
  def self.hi  #類別方法
    p "hi"
  end
  
  def haha     #實體方法
    p "haha"
  end
  
end

Cat.hi #類別方法

kitty = Cat.new  #類別方法
kitty.hi #單體（例）方法
kitty.haha  #實體方法

```
要使用實體方法時，new出實體再使用實體方法

## 類別變數使用方式

```ruby
class Cat
  @@count = 0
  
  def initialize
    @@count += 1
  end
  
  def self.total
    @@count
  end
end

```

## public(公用的)

系統預設定義是public,
是一種開放的、誰都可以存取的方式。
```ruby
class Cat
  def eat
    puts "eating..."
  end
end

kitty = Cat.new
kitty.eat  #eating...
```
像這樣，kitty可以直接提取eat這個方法。

## Protected(受保護的)

較public不自由，
不可以直接存取，
```ruby
class Cat
  protected
  def eat
    puts "eating..."
  end
end

kitty = Cat.new
kitty.eat  #錯誤訊息
```
但不限定有沒有明確的接收者，
所以用以下兩個方法都可以成功執行。
```ruby
class Cat
  def do_eat
    eat           #沒有接收者
    self.eat      #有接收者
  end
  
  protected
  def eat
    puts "eating..."
  end
end

kitty = Cat.new
kitty.do_eat 
```

##  Private(私人的)

相對於public，
不可以直接存取，
```ruby
class Cat
  private
  def eat
    puts "eating..."
  end
end

kitty = Cat.new
kitty.eat  #錯誤訊息
```
也不能有明確的接收者，
因此在呼叫方法時不能有.小數點
```ruby
class Cat
  def do_eat
    eat           #沒有接收者,但是在ruby3版本後可寫成self.eat
  end
  
  private
  def eat
    puts "eating..."
  end
end

kitty = Cat.new
kitty.do_eat 
```

不過在ruby的世界裡，
還可以用send方法來呼叫成功喔！
```ruby
class Cat
  private
  def eat
    puts "eating..."
  end
end

kitty = Cat.new
kitty.send(:eat) #動態執行
```

## 所有的.class都是Class


## namespace

```
kitty = A::B::Cat.new
```
代表
```
module(或class) A
  module(或class) B
    class Cat
    end
  end
end
```