---
name: New System Entry
about: Submit a new system to be added to the Potassco collection
title: "[New System] <name>"
labels: new-system
---

---
layout: system
title: <name>
summary: <one-line summary>
state: experimental
permalink: /labs/<name>/
---

<!--
INSTRUCTIONS
- Replace all <...> fields below with the actual content.
- state: use "stable" (maintained, documented), "experimental" (WIP), or "deprecated".
  If stable, change the permalink from /labs/<name>/ to /<name>/
- Remove this comment and any other comments before submitting.
-->

<Description: what the system does, its features, use cases. You can add examples and screenshots. We recommend keeping it concise and linking to the documentation for more details.>

## Documentation

<!-- Default URL assumes the Potassco project template. Change if docs are elsewhere. -->

- [Documentation webpage](https://potassco.org/<name>/docs)

## Resources

- Source code on [GitHub](https://github.com/potassco/<name>)

<!-- Add benchmarks, tutorials, demos, etc. here. Remove this section if none. -->

## Publications

<!--
To fill in publication links:
1. Find the publication at https://www.cs.uni-potsdam.de/wv/publications/
2. Copy the last part of its URL, e.g. corr/abs-2502-09222
3. Use it to replace <url-suffix> below. Remove this section if no publications.
-->
- <Authors>[<Title>]({{ site.publicationurl }}/#DBLP:journals/<url-suffix>), <Conference>, <Year>
