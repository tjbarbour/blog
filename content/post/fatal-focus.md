+++
categories = ["UX"]
# date = "2015-07-02T01:43:44-07:00"
# date = "2015-05-24T18:53:17+02:00"
date = "2015-12-26T00:45:22-08:00"
description = "When your own focus is turned against you..."
draft = false
image = "/img/fatal-focus-bg.jpg"
tags = ["ux", "bad-dog", "rant", "yes-im-doing-tag-jokes"]
title = "fatal focus"

+++

> Summary: Never take the focus away from the current application, it could have disastrous results

# *Someone at Redmond owes me an hour...*

Ok, but really, sometimes our UX decisions can have unfortunate consequences.  There I was, working on an [important document](/resume/), typing away... ready to finish another line.. (period).. (ent...

*When suddenly* something like this popped up:
![Updates, one accidental keystroke away...](/img/updates_yey.png)

Now sure, I probably could've changed a setting somewhere to not propmt me for updates but in any case, this little dialog just snatched my [focus]( https://en.wikipedia.org/wiki/Focus_(computing) ) away, and that last keystroke I was about to hit? A simple [ENTER] and I went from productive to...

![...doomed, updates](/img/updates_doomed.png)

This may be an exaggeration, but it magnifies **how dangerous it can be to take focus away from your users!**  Imagine an application that just grabbed your mouse and pointed it to wherever they pleased?  That's essentially what you are doing when you take the focus away.

# The lesson? 
> (almost) Never steal focus, instead provide a meaningful notification or direction for the user to act on.

# Are there any exceptions?

In web apps it may be common to focus the input upon page load, typically the fisrt input of the web page such as the "username" input for a login page.
  
- This is acceptable because during page load the user can't interact with the page anyway, and the focus control is limited to that page, not like a naitive application that could take the user from one application where they are dropping careless keystrokes and switch the user to a context that requires a little more finesse...

**So, developers, don't distract your users, let them keep their focus.**