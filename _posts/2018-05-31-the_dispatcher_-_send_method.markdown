---
layout: post
title:      "The Dispatcher - SEND method"
date:       2018-05-31 18:18:45 -0400
permalink:  the_dispatcher_-_send_method
---


#SEND is a metaprogramming method, also referred to as the dispatcher. It invokes the method identified by symbol, passing it any arguments specified. The send method takes a value as an argument and interprets it as a method. 


### Taking a variable as an argument

```
string = "HELLO"
command =  :downcase
```

The local variable `command` is set to equal the built-in method `:downcase`. 
So what if we try to call `command` on the object `string` directly. 

```
string.command

NoMethodError: undefined method `command' for "HELLO":String
```

We get a `NoMethodError`! You cannot call `command` on the object string because `command` is not a method but a local variable. In order for this to work we will need to use the `send` method, that will interpret the variable as a method. 

```
string.send(command)
=> "hello"
```

So the `send` method takes in the local variable `command` as an argument and interprets it and extracts the correct method. It does it's magic and we get the correct method `:downcase` called on our object!



### Taking a symbol as an argument

```
string = "HELLO"

string.send(:reverse)
=> "OLLEH"

```

The send method invokes the method identified by symbol.
It's the same as:

```
string.reverse
=> "OLLEH"
```


### Taking a string as an argument

```
string = "HELLO"

string.send("length")
=> 5

```

Again, the `send` method interprets the string `"length"` and calls the actual method `.length`.

It's the same as:

```
string.length
=> 5
```

