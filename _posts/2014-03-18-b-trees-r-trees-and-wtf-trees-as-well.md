---
layout: post
title: "B-Trees, R-Trees and WTF-Trees as well"
modified: 2014-03-18 18:35:40 +0000
category: 
tags: [devnotes]
image:
  feature: 
  credit: 
  creditlink: 
comments: 
share: 
---

My first live devnotes! I'm going to Skills Matter Big-O meetup. Apparently something to do with algorithms, big data and all of the nerdy stuff. I will try to make live notes, with remarks of my understandings of things, and publish them right after.

####

At least that was the plan. I came, sat down, took my laptop and 5 minutes later I had no idea what I am listening to. I don't know if that was due to the poor presentation skills, almost all-text slides that were little help in understanding, or just me being plainly stupid. I suspect the latter was most significant.

Either way, the notes turned horrible, and not much of a help to myself either. I had to make supposedly funny comments, just to make them bearable. But, from the beginning...

###### B-Tree
*Variable number of child nodes, All leaf nodes at same level (I understand this! Yay me!)
*Properties: best case for height log (mn), worst case log(m/2/) (I remember this from university, good enough)
*Efficient for point query, but not  for range and multi-dimensional data (wtf is multi-dim data?)

######Variants of B
*B+ is used in relational DB - finally something I heard about, though never had much interest in the internals of DB server.
*B* - balances more internal neighbours densely packed (I guess that speeds it up? Or not?)
*UB Tree - multi dimmensional data in B-Tree (since I don't know multi dimmensional data, It's double wtf for me)
*ST2B-tree - Self-Tunable Spatio-Temporal B+ tree Index for Moving Object - connects space/time efficiently ... just wow, It totally lands as a name for my space ship. And wtf^3

####I'll spare the rest of the details, and just present the general idea

R-Tree - Dynamic index structure for the spatial searching (wtf?)

... (a lot of mumbo jumbo I could not catch)

Some image of rectangles enclosing each other 

...

3D version of the above, lots of cubics

...

R* - increased reinsertion and implementation cost (wtf?)

...

Hilbert R-tree - indexing of line curve, 3D objects, feature based objects (wtf?)

...

X-tree - Nodes not split will grow and in extreme cases tree will linearise (wtf, but sounds like a bad thing)

...

You get the idea

#### WTF ovah 9000!

The things mentioned above surely are pretty basics. It just turns out I don't know the basics of Trees (apart from "green side goes up". You know, on the real ones).

Now, just knowing the range of my ignorance, I can sum up with the things to google:
*What are trees?
*How trees are searched, I have faint feeling this is mostly what this is about
*What *are* data, how the can be represented, and what would the dimmension mean
*Spatial and temporal - I think I know the general idea, just fail to grasp what they might mean here

This should be enough for today...

The meetup had second part, which was less technical, more accessible, and happened to go for 15 minutes when my laptop died. So this one I will have to watch once again or recreate from memory.

See you until next time!
