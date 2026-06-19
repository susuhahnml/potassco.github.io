---
layout: system
title: clingo-dl
summary: A solver extending clingo with difference constraint solving capabilities.
state: stable
date: "2017-06-19"
permalink: "/clingoDL/"
pinned: 1
order: 2
---

The clingo-dl system provides a seamless way to integrate a subset of the theory of linear constraints, namely difference logic, into ASP.
It deals with constraints of the form `x-y<=k`, where `x` and `y` are integer variables and `k` is an integer constant.
Despite its restriction, difference logic can be used to naturally encode timing related problems, e.g., scheduling or timetabling,
and provides the additional advantage of being solvable in polynomial time.
Syntactically, a difference constraint `x-y<=k` is represented by a difference constraint atom of the form `&diff {x-y} <= k`.

## Download

- Recent clingo-dl releases are on github: [https://github.com/potassco/clingo-dl/releases](https://github.com/potassco/clingo-dl/releases).
- The latest source is on github: [github.com/potassco/clingo-dl](https://github.com/potassco/clingo-dl).

## Resources

- [Potassco User Guide](https://github.com/potassco/guide)
- [Advanced Examples](https://github.com/potassco/clingo-dl/tree/master/examples)

## Publications

- Tomi Janhunen, Roland Kaminski, Max Ostrowski, Torsten Schaub, Sebastian Schellhorn and Philipp Wanko,
  [Clingo goes Linear Constraints over Reals and Integers]({{ site.publicationurl }}/#DBLP:journals/tplp/JanhunenKOSWS17), TPLP, 2017:
  [[Experiments]({{ site.resourceurl }}/clingo/experiments-clingoLC.tar.xz)]
