---
author: Local Ghost
title: How to Display $\LaTeX$ in GitHub Pages using $\KaTeX$
tags: LaTeX GitHub-Pages
categories: LaTeX
---

## Step 1: Render $\KaTeX$

Include auto-render extension scripts in your header:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.15.3/dist/katex.min.css" integrity="sha384-KiWOvVjnN8qwAZbuQyWDIbfCLFhLXNETzBQjA/92pIowpC0d2O3nppDGQVgwd2nB" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.3/dist/katex.min.js" integrity="sha384-0fdwu/T/EQMsQlrHCCHoH10pkPLlKA1jL5dFyUOvB3lfeT2540/2g6YgSi2BL14p" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.3/dist/contrib/auto-render.min.js" integrity="sha384-+XBljXPPiv+OzfbB3cVmLHf4hdUFHlWNZN5spNQ7rmHTXpd7WvJum6fIACpNNfIR" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>
```

see [Auto-render Extension · KaTeX](https://katex.org/docs/autorender.html#usage).



For example, when using [mmistakes/minimal-mistakes](https://github.com/mmistakes/minimal-mistakes), include it in `_includes/head/custom.html`.

## Step 2: Configuration (optional)

Alternatively, you can call the `renderMathInElement` when (or after) the [`DOMContentLoaded` event](https://developer.mozilla.org/ko/docs/Web/Reference/Events/DOMContentLoaded) fires on the document or in another deferred script. This approach is useful for specifying or computing options, or if you don't want to use a `defer` or `onload` attribute. For example:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.15.3/dist/katex.min.css" integrity="sha384-KiWOvVjnN8qwAZbuQyWDIbfCLFhLXNETzBQjA/92pIowpC0d2O3nppDGQVgwd2nB" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.3/dist/katex.min.js" integrity="sha384-0fdwu/T/EQMsQlrHCCHoH10pkPLlKA1jL5dFyUOvB3lfeT2540/2g6YgSi2BL14p" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.3/dist/contrib/auto-render.min.js" integrity="sha384-+XBljXPPiv+OzfbB3cVmLHf4hdUFHlWNZN5spNQ7rmHTXpd7WvJum6fIACpNNfIR" crossorigin="anonymous"></script>
<script>
    document.addEventListener("DOMContentLoaded", function() {
        renderMathInElement(document.body, {
          // customised options
          // • auto-render specific keys, e.g.:
          delimiters: [
              {left: '$$', right: '$$', display: true},
              {left: '$', right: '$', display: false},
              {left: '\\(', right: '\\)', display: false},
              {left: '\\[', right: '\\]', display: true}
          ],
          // • rendering keys, e.g.:
          throwOnError : false
        });
    });
</script>
```

## Minimal Example

```tex
For $n \in \mathbb Z$, one has \[2n \in \mathbb Z\]
```

For $n \in \mathbb Z$, one has \\[2n \in \mathbb Z\\]

## Known Issues

- `$$` will convert into `\(` in `.html` file, making it inline.

```tex
One has $$2n \in \mathbb Z$$
```

One has $$2n \in \mathbb Z$$

- `\` in `\(\)` and `\[\]` will escape in `.html` file, type `\\` instead.