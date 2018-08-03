---
layout: post
title: modules, and crates, and stuff
date: 2017-03-23 13:30 -0500
categories: code
---

Occasionally, I see some confusion from people learning how modules work in Rust.  There are three
different keywords that all seemingly do the same thing!  So something I'd like to do is try to give
some high-level overview of how a Rust project is laid out.

## mod squad

So when you have a pile of Rust files, you need some way for the Rust compiler to know which ones
are actually in the crate, and where. While some other languages rely on separate project files or
some other external indicator, Rust uses a keyword inside the language to pull a new file in. The
`mod` keyword is Rust's way of saying "look for a file with this name, and make it a submodule
here."

For example, if you have some files that look like this:

```text
src/
|-- lib.rs
|-- thing.rs
```

Then your crate is said to have its "crate root" at `lib.rs`, and the other file is pulled in like
this:

```rust
// in lib.rs:

mod thing;
```

So far so good? This works for any number of files in the same directory. Simply match the file name
with a corresponding `mod` statement and you're good to go.

"extern crate" is like "mod" but for non-local things

"use" is just sugar
