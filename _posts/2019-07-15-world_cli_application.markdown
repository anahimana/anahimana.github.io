---
layout: post
title:      "Ruby Parameters"
date:       2019-07-15 10:18:22 -0400
permalink:  world_cli_application
---


This article looks at how to work with parameters in ruby. Understanding how parameters is a essential to programming.

Consider a simple method that outputs a greeting when called.

```ruby
def greeting
	puts "Hello!"
end
greeting
#=> Outputs "Hello!"
```

All this code does is output "Hello!". That's a really boring method though.
Let's make it a little smarter.

```ruby
def greeting(name)
	puts "Hello #{name}!"
end
greeting("Samantha")
#=>  Outputs "Hello Samantha!"
```

Nice, now it outputs a greeting with the name passed to it. That's great!

But, wait a second here. We still want the method to output a greeting even without a name. Let's make the name field optional by defualting it to an empty value.

```ruby
def greeting(name="")
	puts "Hello #{name}!"
end
greeting
#=> Outputs "Hello !"
greeting("Samantha")
#=>  Outputs "Hello Samantha!"
```

If we did not make `name` optional, calling the method would have raised an error.
For a basic method, this is great. We can improve this a little more.

Let's rewrite the method, so that it does not just output "Hey", instead it output whatever we pass to it.

```ruby
def greeting(time_of_day, name="")
	puts "#{time_of_day} #{name}!"
end
greeting("Evening")
#=> Outputs "Evening !"
greeting("Night", "Samantha")
#=>  Outputs "Night Samantha!"
```

This is fantastic! Our method now accepts time_of_day and name as arguments.
However, you may have noticed that time_of_day is not optional, it is required.

```
greeting
ArgumentError (wrong number of arguments (given 0, expected 1..2))
```

Calling the method without the time_of_day argument raises an error.

To a beginner, the concept of parameters or arguments may difficult to grasp because the position of your arguments matters.
Whenever you define your method, you need to remember that order you place the arguments is important.

```ruby
def greeting(required, optional)
end
```

When you call your method, you just need to make sure that the first object you pass into method is required and the second can be empty.

