---
layout: post
title:      "What is Self... "
date:       2018-05-14 21:13:55 +0000
permalink:  what_is_self
---



It took me a bit of time to grasp the concept of `self`... who is `self`? why is `self` changing?

Whenever an object needs to refer to itself in the abstract, the keyword `self` is used. It's always changing and it's not explicitly shown in the code. Then how are you suppose to know what `self` really is?!


In an **instance method**, `self` will always refer to the instance itself – the individual.

In a **class method**, `self` will always refer to the class itself – the entire class. 

`self` can be thought of as the thing that will receive the method call.

```
class Dog

@@all = []

  def self.all
	  @@all
	end
		
  def initialize(name)
	  @name = name
		@@all << self 
	end
	
end
```

In the **CLASS METHOD**, `self` will refer to the class itself.

```
def self.all 
  @@all #Class variable
end
```

Explicit way to write the code with "Dog" class.
```
def Dog.all
  @@all
end
```

In the **INSTANCE METHOD**, `self` will refer to the instance of the class. 


```
def initialize(name)
	  @name = name
		@@all << self  #Instance of the class, it'll push itself into the class variable array 
	end

fido = Dog.new("FIDO")
#<Dog:0x00005639bc032ba8 @name="FIDO">

```


