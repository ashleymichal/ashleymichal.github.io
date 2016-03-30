---
layout: post
title: Object#send
---

19:46 - I was reading Eloquent Ruby and came across the chapter about Object methods, i.e. the methods that come with every instance of any object you create (because all objects inherit from the Object class with few exceptions)and one of these methods is Object#send(:method_name) which has the same effect as calling Object.method 

_but_​ where it becomes useful is in testing when you’re looking to test a class that you’ve declared private and therefore cannot call from outside the class, you can instead call .send on that object, passing in the method name as a symbol, and it will then run the method. This was great because earlier this week I was refactoring a game I did, and wanted to make a method private, but it was also a method that needed tests, so I opted not to because how the hell can I test it if it’s private?! Oh wait, Object#send