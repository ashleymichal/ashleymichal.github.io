---
layout: post
title: So. Stinkin. Close.
---

20:37 - In response to my question to me from the last post, the bit about Coercion vs. Questioning is in the [Event Manager Project](http://tutorials.jumpstartlab.com/projects/eventmanager.html#iteration-2:-cleaning-up-our-zip-codes).

Since I posted, I have finished Hangman (finally) and the Twitter SpamBot (which has more followers than my normal Twitter handle...)

Now I'm, no joke, ONE LINE OF CODE from finishing my simple_server/tiny_browser project. So. Stinkin'. Close.

I got through the issue of pulling in the POST request content (#gets takes an integer parameter 'limit' that you can set using the 'content-length' field of your request). I even figured out that the JSON module doesn't care about your Hash symbols (there is an argument, yes, but for now I'm bypassing for the sake of completion. Refactoring will come when the basic server works).

And the server *does* work. It takes in the json, it parses it, it fills in the erb template. But it still returns the error (now memorized) 757: unexpected token at [html]. But the error then includes the correctly generated html!

I am also lamenting that I still have to go through CS before I get to the (super light weight) RSPEC section of the Ruby chapter. I want the RSPEC skillz most of all so I can stop flailing around with manual tests.

I mean, it's not like I have instructors. What's the point of being self-taught if you can't skip around the content just a little bit?

21:35 - Document your troubleshooting, children. Because if you don't, you might end up running the same method twice. And if you're daft enough, you may wind up putting the output of the first method call in as an argument to the second method call. /facepalm/

So that project is complete... It could likely use some refactoring, but I'm going to leave that to Morning Ashley.