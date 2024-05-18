---
title: "Crossword: Behind The Scenes (re-written)"
date: 2024-05-18T11:30:00+01:00
description: "An editor's commentary on my first (semi)-cryptic crossword"
---

~~Welcome to my dissertation.~~

# Introduction

At an internship I went to, someone introduced me to cryptic crosswords. That evening, a group of fellow interns took an edition of the Evening Standard and we group-solved the cryptic that evening in a few hours.

This made me a bit curious how crossword builders assembled these word puzzles.

So I learned how to make a [crossword](/misc/crossword) and sent my finished product to a few of my friends. It was surprisingly fun watching them solve my puzzles. It's especially rewarding when you laugh along with them as they have their "aha" moments with each of the clues.

# Preparation

I begin work on planning out the crossword. Before I started assembling the crossword, I had already come up with a few ideas for clues that I wanted to add. Since the blank spaces in crossword grids should be rotationally symmetric, I had to pair up words with the same length from my word bank, to place them on opposite sides of the crossword.

It turns out, assembling a crossword itself is sort of like solving a puzzle:
1. Place the special words you have prepared in various corners of the board.
2. Make sure that the ends of the words touch black squares (or the edge of the board).
3. Fill in the rest of the squares strategically using either blanks or other words, making sure that you keep the grid rotationally symmetric.
4. Come up with clues for the other words.

Step 3 was really finnicky! Often I had to redo entire sections just because one word didn't fit, or I accidentally created a section with only two letters (which is not allowed). I often used the help of the [OneLook](https://onelook.com/) online crossword solver when I couldn't think of words.

I found that a spreadsheet was by far the best way to plan out my crossword.

## Checked and unchecked letters

In the context of crosswords, a *checked* letter is a letter which is both part of an across and a down clue. An *unchecked* letter is a letter which is only part of one clue.

In normal crosswords, unchecked letters are annoying because they are harder to know if you are correct. However, they are slightly more acceptable in cryptic crosswords, as the straight and cryptic parts of the clue complement each other, which can help you be far more confident in your answers.

{{< figure src="/posts/first-crossword/unchecked.webp" caption="Unchecked letters in my crossword. Colours inverted to be slightly easier on the eyes." >}}

There are a few best practices when it comes to checked letters in crossword clues. Specifically,
- **In American crosswords, unchecked letters aren't allowed.** Due to this rule, American crosswords have beautiful wide interlocking grids with few black squares. This was a bit hard for me to accomplish, since I was working with a large number of special words, so I decided to ignore this.
- **There should be no more than two unchecked letters in a row.** In fact, crosswords rarely even have two unchecked letters in a row. In my grid, there were a couple of sections with two adjacent unchecked letters. I managed to make sure there weren't more than two, though.

# Implementation

## Here be spoilers!

I will be giving spoilers for some of the cryptic clues. I have a lot to talk about!

If you haven't solved the [crossword](/misc/crossword) yet and would like to solve it, please do so before reading the rest of this post!

## 34 down

> reproduce red taco possibly without cat (4)

This clue doesn't even make sense when interpreted literally. I left this in here as a very obvious and easy cryptic clue, as long as you have a general understanding of how cryptic clues work.

Also, the clue is an obscure reference to an annoying game I used to play with friends over Discord, where we'd think up of as many anagrams of a word as possible. [AtCoder](http://atcoder.jp/), a Japanese competitive programming site, was one we found especially many anagrams for.

{{< figure src="/posts/first-crossword/atcoder.webp" caption="Yeah, I know, some of them don't make sense. It was three years ago..." >}}

We also found a lot for [Optiver](https://optiver.com/). Repivot, Overpit, Tip Over, To Viper, Vote Rip, Prove It, the list goes on...

## 26 across

> a fluffy thing can imbue endless fun-sized nanoseconds! (6)

The past version of this clue was:

> a fluffy thing to imbue endless joy in mere nanoseconds (6)

You are probably wondering what the word "joy" is doing there.

The answer is, nothing much, really. It's sort of a red herring that I couldn't get rid of at the time. Until I realised that you can put a phrase that means both abbreviation and fun. Luckily, I recall this message a friend sent me:

```
I am small because I am fun sized
O-|--< <--- normal person
O|< me
```

Anyway, why did I leave the word "joy" in there in the first place? Well, 26 across was meant to be a reference to Nim! She's a resident of the tea house and has had quite a few cameos in past blog posts (in both cloud form and human form). Nim's a beacon of joy, so that's why I put the word in there.

{{< figure src="/posts/first-crossword/nim-howtodraw.webp" caption="Another Nim cameo" >}}

The clues used to have a lot more of these sorts of obscure references, but I removed most of them when I was finalising the clues (because I actually want the clues to be solvable) and this was the only one I couldn't remove without changing the clue completely.

Why didn't I just change the clue? Well, I realised that the clue, when interpreted literally, is also a really good definition for Nim's personality. For lack of a better word, it's a cute clue!

This property of cryptic clues is sometimes called [&amp;lit.](https://en.wikipedia.org/wiki/Cryptic_crossword#.22.26lit..22), and they're like regular cryptic clues but wrapped up nicely with a double bow. These clues end in an exclamation mark to signal to the solver that there's something really cool going on.

## 18 down

> animal used by programmers of Rust (5)

This clue is supposed to be a cryptic clue disguised as a regular clue to mislead you. Indeed, animal, used by programmers of Rust, 5 letters, surely it's CRABS?

A friend actually originally suggested me this clue as a joke after my original clue, "Rust programmers rewrote this crossword", was thought to be a bad clue. He gave me the amazing alternative of:

{{< figure src="/posts/first-crossword/crabs.webp" caption="You can probably guess why I had to modify it." >}}

# Evaluation

I gave this crossword out to my friends. Let's see how they did!

## Solve times

Solve times varied. The fastest solve time was by one of my testers (who is pretty good with puzzles) who completed the crossword in under 30 minutes! The rest of the people who did my crossword took between two and four hours to fully solve it. I encouraged them (especially those who were new to cryptics) to use crossword solvers and the Internet. If they were stuck, they could also ask me (or other people who have solved it) for hints.

A solve time of two to four hours was just what I wanted, since this meant that the clues were hard, but never too hard that it took a long time to figure out. I created the crossword just for a bit of fun and not as some ridiculously hard challenge.

The last clues to be solved were usually 16 and 18 Down. I expected this - two out of five of the letters were unchecked and the clues were both quite difficult. The top left and bottom right corners were also quite hard and they also had five out of eight letters unchecked.

## General feedback from various people

People generally seemed to like my crossword! Some even shared the crossword to their friends. People also gave me feedback regarding the clues:

- very nice
- pls make more
- i like the cryptic clues, about half the cryptic clues i don't think i would have gotten by themselves so the xword format is nice
- 16 Down was the last word I got and I literally laughed when I got it
- [3 Down] I actually knew without googling -- really flexing my platformer chops

# Conclusions

Making the crossword was fun! I feel sort of bad for the unused words in my word bank, so here's a clue I left out:

> deliver from port the entitlements to the shark-lovers' slogan (5,6)

Can you guess what it is? Hint: "shark-lovers' slogan" is the straight part. "Straight" part? Okay, you know that's not what I mean.