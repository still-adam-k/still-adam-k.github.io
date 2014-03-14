---
layout: post
title: "The revelation of F# and DDD"
modified: 2014-03-14 13:44:52 +0000
category:
tags: [devnote]
image:
  feature: 
  credit: 
  creditlink: 
comments: 
share: 
---

Something for today: <a href="http://www.slideshare.net/ScottWlaschin/ddd-with-fsharptypesystemlondonndc2013">Scott Wlaschin on F# type system and DDD </a>

This was supposed to be a regular note from regular session, but it will be just one WOW for now. My brain exploded, and I'm still collecting missing pieces.

####The wow

Where should I start? Let's just look at the image:

![]({{ site.url }}/images/fsharp_walschen_slide.jpg)

This is almost complete ubiquitous language for a context of card game playing. Made with executable code. Fitting on one screen. Spelled so it's obvious what each line means. When I think about it, it would take a few files to present this in C#. Or a spaghetti of UML diagrams.

####The more wow

From what I've seen, creating a type in F# is a one liner, almost as simlpe as namig a variable in object code. And we are talking about complete, static typed, immutable, compared by value. If you need do to do something with Queen of Spades, you write type named QueenOfSpades - and every rules that applies to QoS, applies only to it - by definition. No type checking if our card would be Queen. No switch statements. No casting. No inheritance tree.

And you can do it to every thing. You don't have person types with two strings - you have person with Name and LastName. You don't have flags stating if your string-represented email with flags coding if it was verified or not. You have VerifiedEmailAddress and UnverifiedEmailAddress. Or BusinessEmailAddress and PrivateEmailAddress. Or even type of SendingShitloadOfSpamEmailAddress, if you wish. It's domain modeller's heaven. Something I always dreamed I could do, but was such a pain to maintain with C#.

####The wow to be continued

The session was very few on technical details, and I think for the best. I'm new to functional programming, and all the alien definitions just scare me. I jump whenever I hhear Monad, just thinking I have a bug on my shoulder.

I tried to write down my notes and more detailed thoughts about that session, but I would be forced to cite every slide. Instead, I'm going to watch it once again (and again ... and probably again as well) as soon as I get my hands on video. Then do some experiments and maybe have I will be able to produce some thoughts of my own. Hopefully.

P.S. I started my first F# kata. With bumps, but it's going surprisyngly well.

