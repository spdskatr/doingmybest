+++
title = "Property-based testing"
date = "2022-01-25T23:37:12Z"
author = "spdskatr"
authorTwitter = "" #do not include @
cover = ""
tags = ["coding", "pbt"]
keywords = []
description = "My comments on the property-based testing talk I did."
showFullContent = false
readingTime = 10
+++

# Property-based testing

Hi! You're probably here because of some talk or lecture I did on property-based testing. A download link to the slides will also appear here after the talk

Slides: [Handout](https://spdskatr.github.io/misc/pbt_presentation_short.pdf)

## Extra points/disclaimers
- I know that Python's `hypothesis` library has a special component for model-based (or stateful) testing. Documentation can be found [here](https://hypothesis.readthedocs.io/en/latest/stateful.html).
  - I did not cover it because I would have to explain it and my talk already went for quite long.
  - Not all property-based testing libraries are guaranteed to have this (good libraries should, though) so using only the basic tools that `hypothesis` gives means that my examples are more transferrable to other libraries and languages.
- My classification of property-based testing design patterns is just a general overview. I have seen other talks where people group property-based testing patterns in different ways. As far as I know, there has been no definitive classification.
- In my explanation of what formal verification is, I was quite vague and my explanation can be interpreted as a program generating the proofs of correctness. Typically, all that proof assisitants do is *check* if your proof is correct, not generate proofs by themselves. However, automated proving *is* its own field!
- For those who were disappointed that my talk wasn't in Haskell, I do apologise. Can I offer you a nice [BubbleT](https://github.com/spdskatr/BubbleT/) in this trying time?

## Resources
Here are some resources I found quite useful when researching this topic.

### Papers
- Intro to QuickCheck: [Original QuickCheck Paper (2000)](https://dl.acm.org/doi/pdf/10.1145/351240.351266)
- For how to write properties: [How to Specify It! (2019)](https://research.chalmers.se/publication/517894/file/517894_Fulltext.pdf)
- Tony Hoare's original paper on writing proofs of correctness for data structures: [Proof of Correctness of Data Representations (1972)](https://link.springer.com/content/pdf/10.1007/BF00289507.pdf)
- Seems cool: [Do Judge a Test by its Cover: Combining Combinatorial and Property-Based Testing (2021)](https://link.springer.com/chapter/10.1007%2F978-3-030-72019-3_10)

### Blogs
- Series of blog posts on property-based testing in depth: [F# for Fun and Profit: Property Based Testing](https://fsharpforfunandprofit.com/series/property-based-testing/)
- Short Spotify blog on property-based testing in C++: [Generating test cases so you don’t have to](https://engineering.atspotify.com/2015/06/25/rapid-check/)

### Talks
- Short talk on the `hypothesis` library: [Matt Bachmann - Better Testing with Less Code (PyCon 2016)](https://youtu.be/jvwfDdgg93E)
- General introduction to property-based testing: [John Hughes - Don't Write Tests! (Curry On! Barcelona 2017)](https://www.youtube.com/watch?v=hXnS_Xjwk2Y)
- How to write good properties: [John Hughes - How to Specify it! (Code Mesh LDN 19)](https://www.youtube.com/watch?v=zvRAyq5wj38)
- How to test stateful and/or concurrent systems: [Eric Normand - Testing Stateful and Concurrent Systems Using test.check (Clojure/west 2017)](https://www.youtube.com/watch?v=r5i_OiZw6Sw)
- How people modelled and tested a NoSQL database: [Ulf Norell - Testing Eventual Consistency in Riak (Erlang User Conference 2012)](https://www.youtube.com/watch?v=x9mW54GJpG0)

### Just for fun
- John Hughes and co. made a company called [QuviQ](http://www.quviq.com) that provides property-based testing services!

### Acknowledgements

Special thanks to the University of New South Wales course COMP3141 "[Software System Design and Implementation](https://cgi.cse.unsw.edu.au/~cs3141/)" for initially introducing me to property-based testing.

Also thanks to [Churchill College, University of Cambridge](https://www.chu.cam.ac.uk/) for providing the venue to host my talk and my epic Director of Studies [Mr Matthew Ireland](https://www.chu.cam.ac.uk/people/view/matthew-ireland/) for his support and encouragement. You can find out more about the Churchill College CompSci Talks [here](https://kudos.chu.cam.ac.uk/talks/about).

Thanks for listening! ~💜
