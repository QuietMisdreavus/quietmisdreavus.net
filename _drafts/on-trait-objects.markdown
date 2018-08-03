---
layout: post
title: on trait objects, object safety, and all that
date: 2016-12-09 12:00 -0600
categories: code
---

The past few days on the Rust IRC chat have brought several questions about trait objects, how to
use them and when "object safety" comes into play. I actually learned a little bit myself about
this, and I'd like to share that.

## a crash course in what traits aren't

If you've been writing Rust for very long, you've probably come across traits. They're Rust's way of
aggregating separate implementations behind the same "interface" of sorts. (More on the scare quotes
in a moment.) They mesh very nicely with generics to allow for the same code to operate very
differently depending on how it's called. ([I've gushed a little about abusing traits and generics
before.][fromjson])

[fromjson]: /code/2016/10/22/dispatches-from-egg-mode/#custom-traits-for-custom-magic

For people new to Rust, traits can look an awful lot like [something they may have already
seen][interface]. If you're coming from something like C#, you might look at this and think "oh hey,
i know what this is, it's an interface!" And honestly, you're on the right track! But if you try to
use it the the same way as an interface, or an abstract base class from C++, then you're probably
going to run into some implementation details you didn't need to consider before.

[interface]: https://en.wikipedia.org/wiki/Protocol_(object-oriented_programming)
