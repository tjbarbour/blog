+++
categories = ["DEVELOPMENT"]
date = "2015-07-02T01:43:44-07:00"
description = "Fluent:Interfaces :: Infix:Notations"
draft = true
image = "/img/photo-stefan-gessert-n-141.jpg"
tags = ["coding", "code-style", "lazy-coder"]
title = "Why Fluent Wins"
+++

> Fluent APIs better match our mental model of how data is processed == WIN 

# Cześć
Does this make sense to you?  

`+ 3 4 `

You may read this as It roughly reads like "Let's do an addition of 3 and four."  Sure, you may be familiar with "Polish Notation" or variants like "Reverse Polish Notation" or RPN, but it's not how most people naturally process these kind of operations.  This is especially true for these "binary" operations (have two parameters).    

Of course we usually think about it like this:

`3 + 4`

Here we envision this as "You have three, now add to it four" this seems natural.

And as we'll see, this is aggravated when you chain many operations.

#Functions make us think in reverse

#Fluent Methods walk us through step by step

#Example
string => base64 => decrypt => ascii blah blah...

#Compare it with reverse polish notation / polish notation

link to a blogpost about extension methods