---
layout: post
title: "DevNotes: Andy Hunt - Debugging Your Mind"
modified: 2014-03-10 12:15:30 +0000
category:
tags: [devnote]
image:
  feature: 
  credit: 
  creditlink: 
comments: 
share: 
---

Notes from session: <a href="http://vimeo.com/68378949">http://vimeo.com/68378949</a>

####Who

 Andy Hunt - I know his name was mentioned a couple of times somewhere. Finally got it, he's the author of Pragmatic Thinking and Learning. The book seems worth reading, and it's going on my must-read book pile.

####Spotting Fast vs Slow changes
 
 The example with <a href="http://www.youtube.com/watch?v=IGQmdoK_ZfY">counting how many times white players passed the ball</a>. I won't spoil the fun with anwers :) The bottom line is - we suck at spotting slow, constant changes. 

Interestingly enough we are exceptionally good at being aware of rapid movement. We were born to spot leaping sabre-tooth tiger in an instant, not to observe how the paint dries, and that may be the reason we miss obious signs of rotten code, until they bite us from behind.
		
My guess is this is why I find tracking global politics boring. Unless I play Civilization V.
	
####Processing Errors

Human brain does not function like a machine. Memory gets corrupted, we make illogical decisions, we do not "think" like we think we do. There are lot of examples, but Andy identified:

* Memory gets corrupted - we tend to remember things slightly different, the more the farther they were. Reminds me of my mother in law ("In my days, the young actually did care about <some generic problem> " ... Sheesh). Important thing to do is make notes, documents for further reference ("*Aaah, so that's why we chose this framework ...*")
* Fundamental attribution - eg. all java/.net/ruby/whatever developers do it wrong. If you write in ruby, you suck.
* Need for closure - people like fixed numbers, even when they now they can be false. Projects manager asking for estimations, anyone?
* Confirmation bias - when you see only arguments that back up your point of view. Observable in natural environment in most internet discussions
* Exposure tolerance - If bad things are not dealt with, we tend to live with them. If we do not die immiedietely, we tend to ignore the need to fix them. If we have failing tests, and we live with them for a few days, we will stop paying attention to other tests failing
* Symbolic reduction - Some see a hand just a five sticks - we are reducing objects to their very symbolic representations. This allows us to process more and more complex data, but at the loss of details. And apparently is responsible for me not being able to draw a hand (because something in my brain screams: These are sticks! Draw 5 sticks and youre done!)

####Cohorte

You have more in common with people born around your time, than with those born the same place. This is more of a social thing, people born in one generation tend to share similar beliefs, while the next generation does not see them as a value.
Interestingly, there are supposed to be only four "generation archetypes" - prophet nomad / hero / artist. The names are a little misleading, but more on them can be found <a href="http://www.lifecourse.com/about/method/generational-archetypes.html">here</a>

Even more interestingly, in IT there is a mix of generations: Older developers have totally diffrent values and approach than young ones. It poses some interesting challenges to managing team, in which by definition members do not share beliefs.

####How to cope with all of our biases 
Ask yourself a lot of questions (namely: why? just going deeper and deeper). If you you can't provide simple answers to simple and most basic questions, than you're not thinking clearly on this.

Even the sole act of asking questions is helpful - it allows you to stop and think.