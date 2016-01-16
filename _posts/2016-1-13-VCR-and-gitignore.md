---
layout: post
title: VCR & .gitignore
---

12:35 - The last iteration of the 'Rotten Potatoes' example application from BerkeleyX explores a little bit of external API integration through a 'Search TMDb' feature. This feature allows a user to search The Movie Database for movies in order to add them to the Rotten Potatoes database. There is even a third party gem to facilitate the calls to the API, and that's great, but where I've gotten stuck is in stubbing those calls in my Cucumber tests.

So enter VCR. This gem looks pretty great. Relatively simple to use, and it's buddy WebMock is also relevant. Those aren't the challenges: the challenge, for me, is where in the support structure of my Cucumber features to implement them.

Thus, today is a doc-reading day. Hope they don't suck.

13:39 - Docs.... kind of helpful. More helpful, as usual, were blog posts from others who have already tread this path.

So, what I learned:

The Support directory for Cucumber features is full of exactly that: support code. Thus, your VCR config file belongs here:

###### features/support/vcr.rb

```ruby
VCR.configure do |c|
	c.ignore_localhost = true
  c.cassette_library_dir = 'features/cassettes'
  c.hook_into :webmock
end

VCR.cucumber_tags do |t|
  t.tag '@vcr', use_scenario_name: true 
end
```

Line 2 allows your local HTTP requests to fly about unhindered. 
Line 3 sets the directory where your 'cassettes' will be saved.  These are generated and saved automatically the first time you run your tests, so while you will hit the API once, the results will be saved 'on cassette' and any further requests will be intercepted and instead return the content of those cassettes. 
Line 4 simply says we will be using WebMock to stub the internet.

The second block sets a VCR 'tag', or instance variable, which you then insert into your feature file. The option 'use_scenario_name' just tells VCR to save the results of the first HTTP response into a directory/file structure following the descriptions of the features and scenarios.

Inevitably every problem I find a solution to raises another question and today was no different: If I'm using a third-party API, and therefore require use of an API key, I don't want this key just floating in my GitHub for anyone to snap up. In the case of TMDb, obviously the consequences of such an oversight aren't dire, but, you know, bad habits are bad. This brought to my attention the importance of the .gitignore file, which up to this point has been provided as part of the boilerplate code for my projects but was conspicuously absent at the beginning of this project.

If, like I did, you run into this problem mid-project, git rm also becomes an important command: the command is identical to its Unix counterpart, except that it only removes the file/directory in question from git's scope, which is necessary at this stage because if you have already been tracking these files, just updating your .gitignore file isn't enough, you need to manually remove them from git's tracking system. This goes for testing/development environments, databases, and logs, as well as packages.

While I was already aware of these two lessons, sometimes it takes an experience like this to really cement theoretical knowledge into practical knowledge.