---
layout: post
title: Rails Rails Rails again
---

19:30 - I'm rewriting the tests in [Michael Hartl's Rails Tutorial](https://railstutorial.org "Rails Tutorial") in RSpec, starting in Chapter 3, which focuses on the Static Pages controller.

First of all, installing Rails RSpec in an existing application was not quite as straight forward as using it right from the start. I mentioned in my last post that the available resources for learning RSpec 3 are a bit sparse, so I'd like to point to [Relish App's Project: RSpec Rails 3.4](http://www.relishapp.com/rspec/rspec-rails/v/3-4/docs "Relish App") as a great resource for sorting some of that out.

Second, once I got the static page tests written out it occurred to me that they all did the exact same thing: confirmed that the GET request was successful, and that the appropriate page view was rendered (by way of the title tag). So now I have the question: is it common practice to refactor such tests as shown below?

