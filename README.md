# @itwmw/markdown-it-plugin-katex

Add Math to your Markdown

[KaTeX](https://github.com/Khan/KaTeX) is a faster alternative to MathJax. This plugin makes it easy to support in your markdown.


## Usage
Install markdown-it

```
npm install markdown-it
```

Install the plugin

```
npm install @itwmw/markdown-it-plugin-katex
```

Use it in your javascript

```javascript
var md = require('markdown-it')(),
    mk = require('@itwmw/markdown-it-plugin-katex');

md.use(mk);

// double backslash is required for javascript strings, but not html input
var result = md.render('# Hello! \n  $\\sqrt{3x-1}+(1+x)^2$');
```

Include the KaTeX stylesheet in your html:
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.13.0/dist/katex.min.css">
```

If you're using the default markdown-it parser, I also recommend the [github stylesheet](https://github.com/sindresorhus/github-markdown-css):
```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/github-markdown-css/4.0.0/github-markdown.min.css"/>
```

`KaTeX` options can be supplied with the second argument to use.
```javascript
md.use(mk, {"throwOnError" : false, "errorColor" : " #cc0000"});
```

## Examples

### Inline
Surround your LaTeX with a single `$` on each side for inline rendering.
```
$\sqrt{3x-1}+(1+x)^2$
```

### Block
Use two (`$$`) for block rendering. This mode uses bigger symbols and centers
the result.

```
$$\begin{array}{c}

\nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} &
= \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\

\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\

\nabla \cdot \vec{\mathbf{B}} & = 0

\end{array}$$
```

## Syntax

Math parsing in markdown is designed to agree with the conventions set by pandoc:

    Anything between two $ characters will be treated as TeX math. The opening $ must
    have a non-space character immediately to its right, while the closing $ must
    have a non-space character immediately to its left, and must not be followed
    immediately by a digit. Thus, $20,000 and $30,000 won???t parse as math. If for some
    reason you need to enclose text in literal $ characters, backslash-escape them and
    they won???t be treated as math delimiters.

## Math Syntax Support

KaTeX is based on TeX and LaTeX. Support for both is growing. Here's a list of
currently supported functions:

[Function Support in KaTeX](https://github.com/Khan/KaTeX/wiki/Function-Support-in-KaTeX)
