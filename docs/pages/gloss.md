---
layout: default
---

## Glossing in expex

Expex is, it seems, the most powerful and the most flexible tool for glossing out there. Glossing, isn't the only thing expex does, of course. However, first:

> Read the documentation [here](https://ctan.org/pkg/expex?lang=en).

The most basic use is to introduce a numbered example:

```TeX
\pex % Optional label
Some text.
\xe
```

Similar effect can be achieved in a simpler way:

```TeX
\ex % Optional label
Some text.
\xe
```

Examples that have multiple elements (or anything numbered, actually -- not only examples), can be formatted as:

```TeX
\pex % Optional label
\a Some text which will be labelled "a.".
\a Some text which will be labelled "b.".
\a Some text which will be labelled "c.".
\xe
```



[back](./)
