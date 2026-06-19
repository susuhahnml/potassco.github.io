---
layout: system
title: metasp
summary: A framework to ease the creation of ASP extensions using meta-programming.
state: stable
permalink: "/metasp/"
---

The goal is to simplify the process of defining and running custom extensions by providing a structured way to specify syntax, semantics, and solver configurations. Modelers can focus on the ASP encodings that define the details of their extension, while metasp takes care of the rest.

- No need for any Python coding!
- Supports different solvers such as clingo, clingcon, and more.
- No need to worry about grounding simplifications metasp takes care of that for you.
- Custom operators can be nested and appear anywhere in the encoding.

#### Useful features

- Customization of output through Python scripts.
- Logging from the ASP encodings.
- Comment-based definition of tests for your extension as part of the ASP encodings.
- Built in [clinguin](/clinguin) interface for interactive use.
- Support for [clingoDL](/clingodl), [clingcon](/clingcon) and [flingo](/flingo) as solvers.

## Documentation

- [Documentation webpage](https://potassco.org/metasp/docs) for latest version.

## Resources

- [Benchmarks ICLP'26](https://github.com/potassco/metasp/blob/v1.0.2/benchmarks/README.md)
- Meta encodings within the [clingo project](/clingo/) in the [examples/reify/](https://github.com/potassco/clingo/tree/master/examples/reify/) folder

## Publications

- Martin Gebser, Roland Kaminski and Torsten Schaub,
  [Complex Optimization in Answer Set Programming: Extended Version]({{ site.publicationurl }}/#TEMP:journals/tplp/GebserKS11x),
  [[Experiments]({{ site.resourceurl }}/metasp/experiments.tar.xz)]
