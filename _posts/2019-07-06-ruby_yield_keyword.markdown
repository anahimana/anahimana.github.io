---
layout: post
title:      "Ruby Yield Keyword"
date:       2019-07-06 23:25:30 +0000
permalink:  ruby_yield_keyword
---


## Objectives
* What is a code block?
* What is the yield keyword?
* Common issue

### Code block

A code block is the code between ```do``` and ```end``` or ```{}```.

```ruby
[1, 2, 3].each do |number|
    puts number
end

[1, 2, 3].each {|number| puts number}

```
```#each``` method is being called with the code block (```{|number| puts number}```) on the literal numbers array ```[1, 2, 3]```.
A number is being passed to the code block on each iteration.

```
1
2
3
```
Both examples above produce the same results. The difference is the syntax of the block.

### Yield keyword

The ```yield``` keyword when used inside of a method allows you to call the method with code block.
It interrupts code execution inside of a method to execute the code in the block. Then it returns to the code in the method.

```ruby
def my_method
    puts "Hello! I am passing execution to 'yield'!"
    yield
end

```

```
my_method {puts "Hey, I was sent here by the code block!"}

```

```#my_method``` is being called with the code block ```{puts "Hey, I was sent here by the code block!"}```


```

Hello! I am passing execution to 'yield'
Hey, I was sent here by the code block!
 =nil
```
### Common issue

Whenever you define a method that uses ```yield``` keyword, you will encounter an error if you call it without a code block.
Let's try to call ```#my_method``` without the code block being passed to it.

```
Hello! I am passing execution to 'yield'
Traceback (most recent call last):
        7: from /Users/dev/.rvm/gems/ruby-2.6.1/bin/ruby_executable_hooks:24:in `<main>'
        6: from /Users/dev/.rvm/gems/ruby-2.6.1/bin/ruby_executable_hooks:24:in `eval'
        5: from /Users/dev/.rvm/rubies/ruby-2.6.1/bin/irb:23:in `<main>'
        4: from /Users/dev/.rvm/rubies/ruby-2.6.1/bin/irb:23:in `load'
        3: from /Users/dev/.rvm/rubies/ruby-2.6.1/lib/ruby/gems/2.6.0/gems/irb-1.0.0/exe/irb:11:in `<top (required)>'
        2: from (irb):23
        1: from (irb):13:in `my_method'
LocalJumpError (no block given (yield))

```

Notice the error "LocalJumpError (no block given (yield))". Ruby has a built-in ```#block_given?``` specifically for this reason.

Let's refactor #my_method

```ruby
def my_method
    puts "Hello! I am passing execution to 'yield'!"
    if block_given?
        puts "A code block was given!"
        yield
    else
        puts "No code block was given!"
    end
end

```

```#block_given?``` will evaluate to true if the method is called with a code block.


Calling #my_method without a code block

```
Hello! I am passing execution to 'yield'!
No code block was given!
```

Calling #my_method with a code block
```
Hello! I am passing execution to 'yield'!
A code block was given!
Hey, I was sent here by the code block!
```



