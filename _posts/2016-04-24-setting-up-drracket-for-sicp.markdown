---
title: Setting up DrRacket for SICP
layout: post
comments: true
permalink: setting-up-drracket-for-sicp
---

Download and install [DrRacket](https://racket-lang.org/).

Follow the instructions to set up [Scheme for SICP](http://docs.racket-lang.org/sicp-manual/index.html).

You should be good to go now but soon you will hit a limitation. While working through the exercises you'll find yourself wanting to create your own library of common functions. Doing this is slightly tricky to account for the modifications to DrRacket. Here's how to do it.

Lets say you have a file called ```lib.scm```:

```
#lang racket 
(define (sq x) (* x x))
(define (cube x) (* x x x))
(provide (all-defined-out))
```
Let's go over this, I have a file with some functions that I'd like to call elsewhere. The last line ```(provide (all-defined-out)``` is a method in Racket to make public all of the functions defined in the file. This method is only available in racket which is why we don't use ```#lang sicp``` here.

Now, to use the above program in another file, let's say ```test.scm``` just include the line ```(#%require <relative path to file>)```:

```
#lang sicp
(#%require "lib.scm")
(sq 5)
```  

#### Sources
<sup>[Scheme for SICP](http://docs.racket-lang.org/sicp-manual/index.html) , [StackOverflow](http://stackoverflow.com/questions/4809433/including-an-external-file-in-racket)<sup>


{% include twitter_plug.html %}