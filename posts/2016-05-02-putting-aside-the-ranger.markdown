---
date: 2016-05-02 23:42:18
title: Putting Aside the Ranger
tags: Haskell, Mad Coding
---

> Put aside the ranger. Become who you were born to be.
>
> &mdash;<cite>Elrond Half-elven</cite>

Nothing about my life, or this little story, is anywhere near as inspirational
as when Elrond gives Anduril, forged from the shards of Narsil, to Aragorn.

In fact, there's ample opportunity yet for crushing disappointment to steal the
day. It's my hope that writing this here, now, will put just enough pressure on
myself to stick with what I've committed to do.

I simply choose to believe that we can all find inspiration to make small
decisions to improve our lives, incrementally shedding the husks of older
versions of ourselves behind us.

## The podcast

Not long ago (the end of March, 2016), I listened to an episode of the
Changelog that had a profound effect on me. I'm not entirely sure what it was
that made [episode #198][1] different from other podcasts I've heard, featuring
guests who shone light on some (to me) heretofore unexplored topic.

The Changelog has aired many such episodes over the years. This one stood out
from the rest because, unlike previous installments, this particular show
hosted a pair of guests who are co-authoring a book about _Haskell_, the
functional programming language.

## The gateway drug

At work, one team took a different path from most, opting to do their work in
a more functional/reactive paradigm. Their stack is Node.js on the server,
which allowed lots of universal app code (that is, code meant to run on both
the client and the server) to be written in JavaScript.

Among other libraries, the team used [Ramda][2], a functional JavaScript
framework, to perform powerful data manipulation and flow control with
relatively few lines of code.

The lead engineer pointed me to [Professor Frisby's Mostly Adequate Guide to
Functional Programming][3], which ignited an interest in this new idea everyone
has been talking about lately&mdash;except there's really nothing new about it.
I got my first taste of point-free functions, Functors, and Hindley-Milner
notation, all within the familiar confines of JavaScript.

Later, when writing the build harness for my team's app, I used Ramda to wire
everything together. I'm sure I got a lot wrong, but my appetite for functional
programming had been whetted, and I wanted to learn more.

I wanted to learn _the_ reference functional programming language. I wanted to
learn Haskell.

I'll always love JavaScript, and I think I'll still be writing it many years
from now. However, I believe it is our duty as programmers to always strive to
broaden our horizons.

## The Haskell Book

When Chris Allen and Julie Moronuki were interviewed on the Changelog, what
caught my interest was their unique team dynamic as a writing duo.

Chris has over six years of Haskell experience under his belt, as well as
previous experience with other functional languages, like Clojure. His passion
is clearly teaching. Surely, the ideal candidate to author a programming book.

Julie is a linguist and stay-at-home mom, with no prior programming experience
other than Haskell. She's been working with the language for about a year.
Chris convinced Julie to let him teach her how to program, and along the way,
Julie became the co-author of the Haskell book: [Haskell Programming from First
Principles][4].

To me the book promised a pedagogical rigor, combined with what was sure to be
a fair amount of empathy for the beginner's mind. I'd tried to read about
Haskell before, but all I came away with was an esoteric vocabulary to describe
mountaintop ideas I couldn't comprehend.

> In interacting with other Haskell learners I often hear that other materials
> leave them feeling like Haskell is difficult and mysterious, a programming
> language best left to wizards. It doesn’t have to be that way.
>
> &mdash;<cite>Julie Moronuki</cite>

I found that point of view encouraging and refreshing. It was as if an
impenetrable veil was about to be lifted.

## An unexpected journey

I downloaded the free sample, and after completing it, I felt comfortable
buying the early access edition of the book. At the time I purchased it, the
book was complete but for three chapters remaining.

Today, I received the notification that the final chapters have been added. It
looks like the authors are now busying themselves with various preparations to
go to print with the hard copy.

As a challenge to myself, I've started reading the Haskell Book regularly. I've
found it both very clear and incredibly challenging to this point &ndash; I'm
just finishing up the sixth chapter: Typeclasses.

I'm being challenged to rethink much of what I know as a programmer, enough to
the point where I suspect that, if the command line and general tooling weren't
serious issues, it _would_ be easier for someone completely new to programming
to pick up Haskell.

If for no other reason than to reinforce them for myself, I am planning future
posts to discuss Haskell and functional programming concepts I'm learning as
I get further into the book. Stay tuned!

  [1]: https://changelog.com/198/
  [2]: http://ramdajs.com/
  [3]: https://drboolean.gitbooks.io/mostly-adequate-guide/content/
  [4]: http://haskellbook.com
