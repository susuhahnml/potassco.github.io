---
layout: page
title: Resources
menu: main
weight: 3
hide_title: true
permalink: /resources/
---

## Documentation

- A comprehensive documentation of our software can be found in the [Potassco PDF Guide](https://github.com/potassco/guide/releases/)
- For clingo v6 the interactive [Potassco Guide](/guide/) can be used to try clingo online and to get a quick introduction to the input language of clingo, modeling examples, and its usage.

## Teaching

We have a dedicated webpage with a lot of [teaching material](https://teaching.potassco.org) for Answer Set Programming.
This includes lecture slides, exercises, and solutions for courses on ASP and related topics.

* The [Potassco tutorials](/doc/tutorials/) collect tutorial talks.

* The [Potassco video clips](/doc/videos/) provide some rough, smallish tutorials on various aspects around our ASP tools.

* The videos can also be found on the [Potassco Youtube channel](https://www.youtube.com/channel/UCnvoHDf9RqBJxKPSGdToLzA/feed).


## Books

### Answer Set Solving in Practice

{% include callout.html
   tone="navy"
   icon='<i class="fa-solid fa-book"></i>'
   link="https://dx.doi.org/10.2200/S00457ED1V01Y201211AIM019"
   text='Martin Gebser,
Roland Kaminski,
Benjamin Kaufmann,
and
Torsten Schaub <br><a href="https://www.cs.uni-potsdam.de/wv/publications/#DBLP:series/synthesis/2012Gebser">Answer Set Solving in Practice</a>.
2012,
Published by
<a href="http://www.morganclaypool.com">Morgan and Claypool</a>' %}



<i>"This book presents a practical introduction to ASP, aiming at using ASP languages and systems for solving application problems.
Starting from the essential formal foundations,
it introduces ASP's solving technology, modeling language and methodology,
while illustrating the overall solving process by practical examples.''</i>

Available at: [Springer](https://dx.doi.org/10.2200/S00457ED1V01Y201211AIM019), [Amazon.com](https://www.amazon.com/Answer-Solving-Practice-Martin-Gebser/dp/1608459713), [Amazon.de](https://www.amazon.de/Answer-Solving-Practice-Martin-Gebser/dp/1608459713)
(Example programs: [zip](/files/listings.zip), [tgz](/files/listings.tgz))

### Answer Set Programming

{% include callout.html
   tone="navy"
   icon='<i class="fa-solid fa-book"></i>'
   link="https://dx.doi.org/10.2200/S00457ED1V01Y201211AIM019"
   text=' Vladimir Lifschitz <a href="https://www.amazon.com/-/he/Vladimir-Lifschitz/dp/3030246574">Answer Set Programming</a>.
2019' %}

<i>"The book introduces the reader to the theory and practice of ASP. It describes the input language of the answer set solver CLINGO, which was designed at the University of Potsdam in Germany and is used today by ASP programmers in many countries. It includes numerous examples of ASP programs and present the mathematical theory that ASP is based on. There are many exercises with complete solutions.''</i>

Available at: [Springer](https://link.springer.com/book/10.1007/978-3-030-24658-7), [Amazon.com](https://www.amazon.com/Answer-Solving-Practice-Martin-Gebser/dp/1608459713)


## Other prominent ASP systems

- [DVLP](https://dlv.demacs.unical.it/) a deductive database system, based on disjunctive logic programming, which offers front-ends to several advanced KR formalisms. It is developed by the University of Calabria and the Vienna University of Technology, Italy and Austria.

- [Wasp](http://alviano.github.io/wasp/) an ASP solver handling disjunctive logic programs under the stable model semantics. It combines techniques originally introduced for SAT solving with methods specifically designed for ASP computation. It is developed by the University of Calabria, Italy.


## Applications

In [ASP applications](/apps/) you can find a collection of projects involving our tools, we found interesting.
<!--
### BioASP

The BioASP software collection includes applications for analyzing metabolic, signaling and gene regulatory networks,
consistency checking, diagnosis, and repair of biological data and models. They allow for computing
predictions and generating hypotheses about required extensions of biological models, as well as designing
new experiments and finding intervention strategies to control the biological system at hand.

- [Encodings](http://bioasp.github.io/)

### Curriculum-Based Course Timetabling

The curriculum-based course timetabling (CB-CTT) problem has been
proposed in the third track of
[the second international timetabling competition](http://www.cs.qub.ac.uk/itc2007/).
This project comprises a set of ASP encodings for the CB-CTT problem.

- [Article]({{ site.publicationurl }}/#DBLP:journals/tplp/BanbaraSTIS13)
- [Encodings](http://kaminari.istc.kobe-u.ac.jp/resource/ctt/teaspoon-1.0.tgz)

### Metabolic Network Completion
This project comprises a set of encondings that calculate minimal completions for a metabolic draft network.

- [Article I]({{ site.publicationurl }}/#DBLP:conf/iclp/SchaubT09)
- [Article II]({{ site.publicationurl }}/#DBLP:conf/lpnmr/ColletEGPSST13)
- [Encodings](/files/meneco-encodings-2013-10-24.tar.gz)

### Minimal Intervention Strategies
This project comprises a set of encondings that calculate minimal intervention
strategies in logical signaling networks.  For further information see the
publication below.

- [Article]({{ site.publicationurl }}/#DBLP:journals/tplp/KaminskiSSV13)
- [Encodings](/files/intervention-encodings-2013-06-21.tar.bz2)

### Ricochet Robots

Alex Randolph's board game Ricochet Robots offers a rich and versatile benchmark for
ASP. As it stands, it represents a simple multi-agent planning problem in which each
agent, i.e., robot, has limited sensing capacities (that is, only bumps are detected).

The Ricochet Robots visualization tool robotviz allows for displaying the board with
barriers, robots, and targets as well as for animating robot moves in a stepwise fashion.

Note that the clingo examples (part of the [releases](https://github.com/potassco/clingo/releases)) also contain an encoding and a visualizer for the ricochet robot problems.

- [Article]({{ site.publicationurl }}/#DBLP:conf/lpnmr/GebserJKOSSS13)
- [Encodings](/files/ricochetrobots-encodings.tar.gz) -->
