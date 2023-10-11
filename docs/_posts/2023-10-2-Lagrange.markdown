---
layout: post
title:  "Understanding Lagrange Interpolating Polynomials: Connecting the Dots
"
date:   2023-10-2 06:25:17 -0800
categories: jekyll update
---

## Introduction

In the vast realm of mathematics, interpolation plays a pivotal role. It allows us to fill in the gaps, connecting the dots, and making sense of data. One powerful tool for this purpose is the Lagrange Interpolating Polynomial. This polynomial, denoted as $$P(x)$$, is a remarkable mathematical construct that efficiently captures and approximates a function based on a limited number of data points. In this blog, we will explore the Lagrange Interpolating Polynomial, its formula, and its significance in various fields.

## Connecting the Dots

Imagine you have a set of data points $$(x_1, y_1)$$, $$(x_2, y_2)$$, ..., $$(x_n, y_n)$$, and you want to find a polynomial that passes through all of them. The Lagrange Interpolating Polynomial provides a solution to this problem. It is a polynomial of degree less than or equal to $$n-1$$ that seamlessly connects these points.
### **The Formula**

Lagrange Interpolating Polynomial, $$P(x)$$, is constructed using a combination of basis functions, one for each data point:

$$
P(x) = \sum_{j=1}^{n} [y_j \cdot L_j(x)]
$$

Here, $$L_j(x)$$ represents the Lagrange basis functions. Each $$L_j(x)$$ is defined as:

$$
L_j(x) = \prod_{k=1, k \neq j}^{n} \frac{(x - x_k)}{(x_j - x_k)}
$$

Explicitly, this can be written as:

$$
P(x) = \frac{(x - x_2)(x - x_3) \ldots (x - x_n)}{(x_1 - x_2)(x_1 - x_3) \ldots (x_1 - x_n)} \cdot y_1
         + \frac{(x - x_1)(x - x_3) \ldots (x - x_n)}{(x_2 - x_1)(x_2 - x_3) \ldots (x_2 - x_n)} \cdot y_2
         + \ldots
         + \frac{(x - x_1)(x - x_2) \ldots (x - x_{n-1})}{(x_n - x_1)(x_n - x_2) \ldots (x_n - x_{n-1})} \cdot y_n
$$

### **Breaking It Down**

The Lagrange Interpolating Polynomial may appear complex at first glance, but breaking it down into its components reveals its simplicity and elegance. Let's delve into some key elements:

1. **Basis Functions**: Each term, $$L_j(x)$$, represents a basis function for the $$j$$-th data point. These basis functions ensure that $$P(x)$$ passes through the corresponding data point $$(x_j, y_j)$$. They are designed in such a way that when $$x$$ equals $$x_j$$, $$L_j(x)$$ equals 1, and when $$x$$ equals any other data point $$x_k$$ ($$k \neq j$$), $$L_j(x)$$ equals 0, ensuring the polynomial's property.

2. **Weights**: The values $$y_j$$ are the weights associated with each data point. They determine the influence of each data point on the polynomial. The weight $$y_j$$ is multiplied by the corresponding basis function $$L_j(x)$$ for each data point.

3. **Normalization**: The denominator in each term normalizes the basis functions, ensuring that when evaluated at a data point $$x_j$$, the corresponding term equals $$y_j$$.


## Conclusion

The Lagrange Interpolating Polynomial is a versatile and powerful mathematical tool that connects the dots between data points, allowing us to approximate and interpolate functions with precision. Its formula, composed of basis functions and weights, ensures that the polynomial passes through the given data points. This concept finds applications in various fields, making it an essential tool for engineers, scientists, and mathematicians. So, the next time you need to connect the dots in your data, remember the Lagrange Interpolating Polynomial as your reliable mathematical friend.

## Python Notebook
<div id="html" markdown="0">
<html>
<head>



<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Nbconvert</title>


<script type="text/x-mathjax-config">
  MathJax.Hub.Config({tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}});
</script>
<script type="text/javascript"
  src="http://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

<script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>




<style type="text/css">
    pre { line-height: 125%; }
td.linenos .normal { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
span.linenos { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
td.linenos .special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
span.linenos.special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
.highlight .hll { background-color: var(--jp-cell-editor-active-background) }
.highlight { background: var(--jp-cell-editor-background); color: var(--jp-mirror-editor-variable-color) }
.highlight .c { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment */
.highlight .err { color: var(--jp-mirror-editor-error-color) } /* Error */
.highlight .k { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword */
.highlight .o { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator */
.highlight .p { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation */
.highlight .ch { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Multiline */
.highlight .cp { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Preproc */
.highlight .cpf { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Single */
.highlight .cs { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Special */
.highlight .kc { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Pseudo */
.highlight .kr { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Type */
.highlight .m { color: var(--jp-mirror-editor-number-color) } /* Literal.Number */
.highlight .s { color: var(--jp-mirror-editor-string-color) } /* Literal.String */
.highlight .ow { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator.Word */
.highlight .pm { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation.Marker */
.highlight .w { color: var(--jp-mirror-editor-variable-color) } /* Text.Whitespace */
.highlight .mb { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Bin */
.highlight .mf { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Float */
.highlight .mh { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Hex */
.highlight .mi { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer */
.highlight .mo { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Oct */
.highlight .sa { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Affix */
.highlight .sb { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Backtick */
.highlight .sc { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Char */
.highlight .dl { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Delimiter */
.highlight .sd { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Doc */
.highlight .s2 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Double */
.highlight .se { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Escape */
.highlight .sh { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Heredoc */
.highlight .si { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Interpol */
.highlight .sx { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Other */
.highlight .sr { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Regex */
.highlight .s1 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Single */
.highlight .ss { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Symbol */
.highlight .il { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer.Long */
  </style>



<style type="text/css">
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*
 * Mozilla scrollbar styling
 */

/* use standard opaque scrollbars for most nodes */
[data-jp-theme-scrollbars='true'] {
  scrollbar-color: rgb(var(--jp-scrollbar-thumb-color))
    var(--jp-scrollbar-background-color);
}

/* for code nodes, use a transparent style of scrollbar. These selectors
 * will match lower in the tree, and so will override the above */
[data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar,
[data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar {
  scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
}

/* tiny scrollbar */

.jp-scrollbar-tiny {
  scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
  scrollbar-width: thin;
}

/*
 * Webkit scrollbar styling
 */

/* use standard opaque scrollbars for most nodes */

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar,
[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-corner {
  background: var(--jp-scrollbar-background-color);
}

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-thumb {
  background: rgb(var(--jp-scrollbar-thumb-color));
  border: var(--jp-scrollbar-thumb-margin) solid transparent;
  background-clip: content-box;
  border-radius: var(--jp-scrollbar-thumb-radius);
}

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-track:horizontal {
  border-left: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
  border-right: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
}

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-track:vertical {
  border-top: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
  border-bottom: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
}

/* for code nodes, use a transparent style of scrollbar */

[data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar::-webkit-scrollbar,
[data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar::-webkit-scrollbar,
[data-jp-theme-scrollbars='true']
  .CodeMirror-hscrollbar::-webkit-scrollbar-corner,
[data-jp-theme-scrollbars='true']
  .CodeMirror-vscrollbar::-webkit-scrollbar-corner {
  background-color: transparent;
}

[data-jp-theme-scrollbars='true']
  .CodeMirror-hscrollbar::-webkit-scrollbar-thumb,
[data-jp-theme-scrollbars='true']
  .CodeMirror-vscrollbar::-webkit-scrollbar-thumb {
  background: rgba(var(--jp-scrollbar-thumb-color), 0.5);
  border: var(--jp-scrollbar-thumb-margin) solid transparent;
  background-clip: content-box;
  border-radius: var(--jp-scrollbar-thumb-radius);
}

[data-jp-theme-scrollbars='true']
  .CodeMirror-hscrollbar::-webkit-scrollbar-track:horizontal {
  border-left: var(--jp-scrollbar-endpad) solid transparent;
  border-right: var(--jp-scrollbar-endpad) solid transparent;
}

[data-jp-theme-scrollbars='true']
  .CodeMirror-vscrollbar::-webkit-scrollbar-track:vertical {
  border-top: var(--jp-scrollbar-endpad) solid transparent;
  border-bottom: var(--jp-scrollbar-endpad) solid transparent;
}

/* tiny scrollbar */

.jp-scrollbar-tiny::-webkit-scrollbar,
.jp-scrollbar-tiny::-webkit-scrollbar-corner {
  background-color: transparent;
  height: 4px;
  width: 4px;
}

.jp-scrollbar-tiny::-webkit-scrollbar-thumb {
  background: rgba(var(--jp-scrollbar-thumb-color), 0.5);
}

.jp-scrollbar-tiny::-webkit-scrollbar-track:horizontal {
  border-left: 0px solid transparent;
  border-right: 0px solid transparent;
}

.jp-scrollbar-tiny::-webkit-scrollbar-track:vertical {
  border-top: 0px solid transparent;
  border-bottom: 0px solid transparent;
}

/*
 * Phosphor
 */

.lm-ScrollBar[data-orientation='horizontal'] {
  min-height: 16px;
  max-height: 16px;
  min-width: 45px;
  border-top: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='vertical'] {
  min-width: 16px;
  max-width: 16px;
  min-height: 45px;
  border-left: 1px solid #a0a0a0;
}

.lm-ScrollBar-button {
  background-color: #f0f0f0;
  background-position: center center;
  min-height: 15px;
  max-height: 15px;
  min-width: 15px;
  max-width: 15px;
}

.lm-ScrollBar-button:hover {
  background-color: #dadada;
}

.lm-ScrollBar-button.lm-mod-active {
  background-color: #cdcdcd;
}

.lm-ScrollBar-track {
  background: #f0f0f0;
}

.lm-ScrollBar-thumb {
  background: #cdcdcd;
}

.lm-ScrollBar-thumb:hover {
  background: #bababa;
}

.lm-ScrollBar-thumb.lm-mod-active {
  background: #a0a0a0;
}

.lm-ScrollBar[data-orientation='horizontal'] .lm-ScrollBar-thumb {
  height: 100%;
  min-width: 15px;
  border-left: 1px solid #a0a0a0;
  border-right: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='vertical'] .lm-ScrollBar-thumb {
  width: 100%;
  min-height: 15px;
  border-top: 1px solid #a0a0a0;
  border-bottom: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='horizontal']
  .lm-ScrollBar-button[data-action='decrement'] {
  background-image: var(--jp-icon-caret-left);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='horizontal']
  .lm-ScrollBar-button[data-action='increment'] {
  background-image: var(--jp-icon-caret-right);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='vertical']
  .lm-ScrollBar-button[data-action='decrement'] {
  background-image: var(--jp-icon-caret-up);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='vertical']
  .lm-ScrollBar-button[data-action='increment'] {
  background-image: var(--jp-icon-caret-down);
  background-size: 17px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-Widget, /* </DEPRECATED> */
.lm-Widget {
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
  cursor: default;
}


/* <DEPRECATED> */ .p-Widget.p-mod-hidden, /* </DEPRECATED> */
.lm-Widget.lm-mod-hidden {
  display: none !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-CommandPalette, /* </DEPRECATED> */
.lm-CommandPalette {
  display: flex;
  flex-direction: column;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-CommandPalette-search, /* </DEPRECATED> */
.lm-CommandPalette-search {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-CommandPalette-content, /* </DEPRECATED> */
.lm-CommandPalette-content {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  min-height: 0;
  overflow: auto;
  list-style-type: none;
}


/* <DEPRECATED> */ .p-CommandPalette-header, /* </DEPRECATED> */
.lm-CommandPalette-header {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}


/* <DEPRECATED> */ .p-CommandPalette-item, /* </DEPRECATED> */
.lm-CommandPalette-item {
  display: flex;
  flex-direction: row;
}


/* <DEPRECATED> */ .p-CommandPalette-itemIcon, /* </DEPRECATED> */
.lm-CommandPalette-itemIcon {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-CommandPalette-itemContent, /* </DEPRECATED> */
.lm-CommandPalette-itemContent {
  flex: 1 1 auto;
  overflow: hidden;
}


/* <DEPRECATED> */ .p-CommandPalette-itemShortcut, /* </DEPRECATED> */
.lm-CommandPalette-itemShortcut {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-CommandPalette-itemLabel, /* </DEPRECATED> */
.lm-CommandPalette-itemLabel {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.lm-close-icon {
	border:1px solid transparent;
  background-color: transparent;
  position: absolute;
	z-index:1;
	right:3%;
	top: 0;
	bottom: 0;
	margin: auto;
	padding: 7px 0;
	display: none;
	vertical-align: middle;
  outline: 0;
  cursor: pointer;
}
.lm-close-icon:after {
	content: "X";
	display: block;
	width: 15px;
	height: 15px;
	text-align: center;
	color:#000;
	font-weight: normal;
	font-size: 12px;
	cursor: pointer;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-DockPanel, /* </DEPRECATED> */
.lm-DockPanel {
  z-index: 0;
}


/* <DEPRECATED> */ .p-DockPanel-widget, /* </DEPRECATED> */
.lm-DockPanel-widget {
  z-index: 0;
}


/* <DEPRECATED> */ .p-DockPanel-tabBar, /* </DEPRECATED> */
.lm-DockPanel-tabBar {
  z-index: 1;
}


/* <DEPRECATED> */ .p-DockPanel-handle, /* </DEPRECATED> */
.lm-DockPanel-handle {
  z-index: 2;
}


/* <DEPRECATED> */ .p-DockPanel-handle.p-mod-hidden, /* </DEPRECATED> */
.lm-DockPanel-handle.lm-mod-hidden {
  display: none !important;
}


/* <DEPRECATED> */ .p-DockPanel-handle:after, /* </DEPRECATED> */
.lm-DockPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='horizontal'],
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='horizontal'] {
  cursor: ew-resize;
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='vertical'],
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='vertical'] {
  cursor: ns-resize;
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='horizontal']:after,
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='horizontal']:after {
  left: 50%;
  min-width: 8px;
  transform: translateX(-50%);
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='vertical']:after,
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='vertical']:after {
  top: 50%;
  min-height: 8px;
  transform: translateY(-50%);
}


/* <DEPRECATED> */ .p-DockPanel-overlay, /* </DEPRECATED> */
.lm-DockPanel-overlay {
  z-index: 3;
  box-sizing: border-box;
  pointer-events: none;
}


/* <DEPRECATED> */ .p-DockPanel-overlay.p-mod-hidden, /* </DEPRECATED> */
.lm-DockPanel-overlay.lm-mod-hidden {
  display: none !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-Menu, /* </DEPRECATED> */
.lm-Menu {
  z-index: 10000;
  position: absolute;
  white-space: nowrap;
  overflow-x: hidden;
  overflow-y: auto;
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-Menu-content, /* </DEPRECATED> */
.lm-Menu-content {
  margin: 0;
  padding: 0;
  display: table;
  list-style-type: none;
}


/* <DEPRECATED> */ .p-Menu-item, /* </DEPRECATED> */
.lm-Menu-item {
  display: table-row;
}


/* <DEPRECATED> */
.p-Menu-item.p-mod-hidden,
.p-Menu-item.p-mod-collapsed,
/* </DEPRECATED> */
.lm-Menu-item.lm-mod-hidden,
.lm-Menu-item.lm-mod-collapsed {
  display: none !important;
}


/* <DEPRECATED> */
.p-Menu-itemIcon,
.p-Menu-itemSubmenuIcon,
/* </DEPRECATED> */
.lm-Menu-itemIcon,
.lm-Menu-itemSubmenuIcon {
  display: table-cell;
  text-align: center;
}


/* <DEPRECATED> */ .p-Menu-itemLabel, /* </DEPRECATED> */
.lm-Menu-itemLabel {
  display: table-cell;
  text-align: left;
}


/* <DEPRECATED> */ .p-Menu-itemShortcut, /* </DEPRECATED> */
.lm-Menu-itemShortcut {
  display: table-cell;
  text-align: right;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-MenuBar, /* </DEPRECATED> */
.lm-MenuBar {
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-MenuBar-content, /* </DEPRECATED> */
.lm-MenuBar-content {
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: row;
  list-style-type: none;
}


/* <DEPRECATED> */ .p--MenuBar-item, /* </DEPRECATED> */
.lm-MenuBar-item {
  box-sizing: border-box;
}


/* <DEPRECATED> */
.p-MenuBar-itemIcon,
.p-MenuBar-itemLabel,
/* </DEPRECATED> */
.lm-MenuBar-itemIcon,
.lm-MenuBar-itemLabel {
  display: inline-block;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-ScrollBar, /* </DEPRECATED> */
.lm-ScrollBar {
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */
.p-ScrollBar[data-orientation='horizontal'],
/* </DEPRECATED> */
.lm-ScrollBar[data-orientation='horizontal'] {
  flex-direction: row;
}


/* <DEPRECATED> */
.p-ScrollBar[data-orientation='vertical'],
/* </DEPRECATED> */
.lm-ScrollBar[data-orientation='vertical'] {
  flex-direction: column;
}


/* <DEPRECATED> */ .p-ScrollBar-button, /* </DEPRECATED> */
.lm-ScrollBar-button {
  box-sizing: border-box;
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-ScrollBar-track, /* </DEPRECATED> */
.lm-ScrollBar-track {
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
  flex: 1 1 auto;
}


/* <DEPRECATED> */ .p-ScrollBar-thumb, /* </DEPRECATED> */
.lm-ScrollBar-thumb {
  box-sizing: border-box;
  position: absolute;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-SplitPanel-child, /* </DEPRECATED> */
.lm-SplitPanel-child {
  z-index: 0;
}


/* <DEPRECATED> */ .p-SplitPanel-handle, /* </DEPRECATED> */
.lm-SplitPanel-handle {
  z-index: 1;
}


/* <DEPRECATED> */ .p-SplitPanel-handle.p-mod-hidden, /* </DEPRECATED> */
.lm-SplitPanel-handle.lm-mod-hidden {
  display: none !important;
}


/* <DEPRECATED> */ .p-SplitPanel-handle:after, /* </DEPRECATED> */
.lm-SplitPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='horizontal'] > .p-SplitPanel-handle,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle {
  cursor: ew-resize;
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='vertical'] > .p-SplitPanel-handle,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle {
  cursor: ns-resize;
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='horizontal'] > .p-SplitPanel-handle:after,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle:after {
  left: 50%;
  min-width: 8px;
  transform: translateX(-50%);
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='vertical'] > .p-SplitPanel-handle:after,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle:after {
  top: 50%;
  min-height: 8px;
  transform: translateY(-50%);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-TabBar, /* </DEPRECATED> */
.lm-TabBar {
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-TabBar[data-orientation='horizontal'], /* </DEPRECATED> */
.lm-TabBar[data-orientation='horizontal'] {
  flex-direction: row;
  align-items: flex-end;
}


/* <DEPRECATED> */ .p-TabBar[data-orientation='vertical'], /* </DEPRECATED> */
.lm-TabBar[data-orientation='vertical'] {
  flex-direction: column;
  align-items: flex-end;
}


/* <DEPRECATED> */ .p-TabBar-content, /* </DEPRECATED> */
.lm-TabBar-content {
  margin: 0;
  padding: 0;
  display: flex;
  flex: 1 1 auto;
  list-style-type: none;
}


/* <DEPRECATED> */
.p-TabBar[data-orientation='horizontal'] > .p-TabBar-content,
/* </DEPRECATED> */
.lm-TabBar[data-orientation='horizontal'] > .lm-TabBar-content {
  flex-direction: row;
}


/* <DEPRECATED> */
.p-TabBar[data-orientation='vertical'] > .p-TabBar-content,
/* </DEPRECATED> */
.lm-TabBar[data-orientation='vertical'] > .lm-TabBar-content {
  flex-direction: column;
}


/* <DEPRECATED> */ .p-TabBar-tab, /* </DEPRECATED> */
.lm-TabBar-tab {
  display: flex;
  flex-direction: row;
  box-sizing: border-box;
  overflow: hidden;
}


/* <DEPRECATED> */
.p-TabBar-tabIcon,
.p-TabBar-tabCloseIcon,
/* </DEPRECATED> */
.lm-TabBar-tabIcon,
.lm-TabBar-tabCloseIcon {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-TabBar-tabLabel, /* </DEPRECATED> */
.lm-TabBar-tabLabel {
  flex: 1 1 auto;
  overflow: hidden;
  white-space: nowrap;
}


.lm-TabBar-tabInput {
  user-select: all;
  width: 100%;
  box-sizing : border-box;
}


/* <DEPRECATED> */ .p-TabBar-tab.p-mod-hidden, /* </DEPRECATED> */
.lm-TabBar-tab.lm-mod-hidden {
  display: none !important;
}


.lm-TabBar-addButton.lm-mod-hidden {
  display: none !important;
}


/* <DEPRECATED> */ .p-TabBar.p-mod-dragging .p-TabBar-tab, /* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging .lm-TabBar-tab {
  position: relative;
}


/* <DEPRECATED> */
.p-TabBar.p-mod-dragging[data-orientation='horizontal'] .p-TabBar-tab,
/* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging[data-orientation='horizontal'] .lm-TabBar-tab {
  left: 0;
  transition: left 150ms ease;
}


/* <DEPRECATED> */
.p-TabBar.p-mod-dragging[data-orientation='vertical'] .p-TabBar-tab,
/* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging[data-orientation='vertical'] .lm-TabBar-tab {
  top: 0;
  transition: top 150ms ease;
}


/* <DEPRECATED> */
.p-TabBar.p-mod-dragging .p-TabBar-tab.p-mod-dragging,
/* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging .lm-TabBar-tab.lm-mod-dragging {
  transition: none;
}

.lm-TabBar-tabLabel .lm-TabBar-tabInput {
  user-select: all;
  width: 100%;
  box-sizing : border-box;
  background: inherit;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-TabPanel-tabBar, /* </DEPRECATED> */
.lm-TabPanel-tabBar {
  z-index: 1;
}


/* <DEPRECATED> */ .p-TabPanel-stackedPanel, /* </DEPRECATED> */
.lm-TabPanel-stackedPanel {
  z-index: 0;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

@charset "UTF-8";
html{
  -webkit-box-sizing:border-box;
          box-sizing:border-box; }

*,
*::before,
*::after{
  -webkit-box-sizing:inherit;
          box-sizing:inherit; }

body{
  font-size:14px;
  font-weight:400;
  letter-spacing:0;
  line-height:1.28581;
  text-transform:none;
  color:#182026;
  font-family:-apple-system, "BlinkMacSystemFont", "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Open Sans", "Helvetica Neue", "Icons16", sans-serif; }

p{
  margin-bottom:10px;
  margin-top:0; }

small{
  font-size:12px; }

strong{
  font-weight:600; }

::-moz-selection{
  background:rgba(125, 188, 255, 0.6); }

::selection{
  background:rgba(125, 188, 255, 0.6); }
.bp3-heading{
  color:#182026;
  font-weight:600;
  margin:0 0 10px;
  padding:0; }
  .bp3-dark .bp3-heading{
    color:#f5f8fa; }

h1.bp3-heading, .bp3-running-text h1{
  font-size:36px;
  line-height:40px; }

h2.bp3-heading, .bp3-running-text h2{
  font-size:28px;
  line-height:32px; }

h3.bp3-heading, .bp3-running-text h3{
  font-size:22px;
  line-height:25px; }

h4.bp3-heading, .bp3-running-text h4{
  font-size:18px;
  line-height:21px; }

h5.bp3-heading, .bp3-running-text h5{
  font-size:16px;
  line-height:19px; }

h6.bp3-heading, .bp3-running-text h6{
  font-size:14px;
  line-height:16px; }
.bp3-ui-text{
  font-size:14px;
  font-weight:400;
  letter-spacing:0;
  line-height:1.28581;
  text-transform:none; }

.bp3-monospace-text{
  font-family:monospace;
  text-transform:none; }

.bp3-text-muted{
  color:#5c7080; }
  .bp3-dark .bp3-text-muted{
    color:#a7b6c2; }

.bp3-text-disabled{
  color:rgba(92, 112, 128, 0.6); }
  .bp3-dark .bp3-text-disabled{
    color:rgba(167, 182, 194, 0.6); }

.bp3-text-overflow-ellipsis{
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal; }
.bp3-running-text{
  font-size:14px;
  line-height:1.5; }
  .bp3-running-text h1{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h1{
      color:#f5f8fa; }
  .bp3-running-text h2{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h2{
      color:#f5f8fa; }
  .bp3-running-text h3{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h3{
      color:#f5f8fa; }
  .bp3-running-text h4{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h4{
      color:#f5f8fa; }
  .bp3-running-text h5{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h5{
      color:#f5f8fa; }
  .bp3-running-text h6{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h6{
      color:#f5f8fa; }
  .bp3-running-text hr{
    border:none;
    border-bottom:1px solid rgba(16, 22, 26, 0.15);
    margin:20px 0; }
    .bp3-dark .bp3-running-text hr{
      border-color:rgba(255, 255, 255, 0.15); }
  .bp3-running-text p{
    margin:0 0 10px;
    padding:0; }

.bp3-text-large{
  font-size:16px; }

.bp3-text-small{
  font-size:12px; }
a{
  color:#106ba3;
  text-decoration:none; }
  a:hover{
    color:#106ba3;
    cursor:pointer;
    text-decoration:underline; }
  a .bp3-icon, a .bp3-icon-standard, a .bp3-icon-large{
    color:inherit; }
  a code,
  .bp3-dark a code{
    color:inherit; }
  .bp3-dark a,
  .bp3-dark a:hover{
    color:#48aff0; }
    .bp3-dark a .bp3-icon, .bp3-dark a .bp3-icon-standard, .bp3-dark a .bp3-icon-large,
    .bp3-dark a:hover .bp3-icon,
    .bp3-dark a:hover .bp3-icon-standard,
    .bp3-dark a:hover .bp3-icon-large{
      color:inherit; }
.bp3-running-text code, .bp3-code{
  font-family:monospace;
  text-transform:none;
  background:rgba(255, 255, 255, 0.7);
  border-radius:3px;
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2);
  color:#5c7080;
  font-size:smaller;
  padding:2px 5px; }
  .bp3-dark .bp3-running-text code, .bp3-running-text .bp3-dark code, .bp3-dark .bp3-code{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#a7b6c2; }
  .bp3-running-text a > code, a > .bp3-code{
    color:#137cbd; }
    .bp3-dark .bp3-running-text a > code, .bp3-running-text .bp3-dark a > code, .bp3-dark a > .bp3-code{
      color:inherit; }

.bp3-running-text pre, .bp3-code-block{
  font-family:monospace;
  text-transform:none;
  background:rgba(255, 255, 255, 0.7);
  border-radius:3px;
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
  color:#182026;
  display:block;
  font-size:13px;
  line-height:1.4;
  margin:10px 0;
  padding:13px 15px 12px;
  word-break:break-all;
  word-wrap:break-word; }
  .bp3-dark .bp3-running-text pre, .bp3-running-text .bp3-dark pre, .bp3-dark .bp3-code-block{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
  .bp3-running-text pre > code, .bp3-code-block > code{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:inherit;
    font-size:inherit;
    padding:0; }

.bp3-running-text kbd, .bp3-key{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background:#ffffff;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
  color:#5c7080;
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  font-family:inherit;
  font-size:12px;
  height:24px;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  line-height:24px;
  min-width:24px;
  padding:3px 6px;
  vertical-align:middle; }
  .bp3-running-text kbd .bp3-icon, .bp3-key .bp3-icon, .bp3-running-text kbd .bp3-icon-standard, .bp3-key .bp3-icon-standard, .bp3-running-text kbd .bp3-icon-large, .bp3-key .bp3-icon-large{
    margin-right:5px; }
  .bp3-dark .bp3-running-text kbd, .bp3-running-text .bp3-dark kbd, .bp3-dark .bp3-key{
    background:#394b59;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
    color:#a7b6c2; }
.bp3-running-text blockquote, .bp3-blockquote{
  border-left:solid 4px rgba(167, 182, 194, 0.5);
  margin:0 0 10px;
  padding:0 20px; }
  .bp3-dark .bp3-running-text blockquote, .bp3-running-text .bp3-dark blockquote, .bp3-dark .bp3-blockquote{
    border-color:rgba(115, 134, 148, 0.5); }
.bp3-running-text ul,
.bp3-running-text ol, .bp3-list{
  margin:10px 0;
  padding-left:30px; }
  .bp3-running-text ul li:not(:last-child), .bp3-running-text ol li:not(:last-child), .bp3-list li:not(:last-child){
    margin-bottom:5px; }
  .bp3-running-text ul ol, .bp3-running-text ol ol, .bp3-list ol,
  .bp3-running-text ul ul,
  .bp3-running-text ol ul,
  .bp3-list ul{
    margin-top:5px; }

.bp3-list-unstyled{
  list-style:none;
  margin:0;
  padding:0; }
  .bp3-list-unstyled li{
    padding:0; }
.bp3-rtl{
  text-align:right; }

.bp3-dark{
  color:#f5f8fa; }

:focus{
  outline:rgba(19, 124, 189, 0.6) auto 2px;
  outline-offset:2px;
  -moz-outline-radius:6px; }

.bp3-focus-disabled :focus{
  outline:none !important; }
  .bp3-focus-disabled :focus ~ .bp3-control-indicator{
    outline:none !important; }

.bp3-alert{
  max-width:400px;
  padding:20px; }

.bp3-alert-body{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex; }
  .bp3-alert-body .bp3-icon{
    font-size:40px;
    margin-right:20px;
    margin-top:0; }

.bp3-alert-contents{
  word-break:break-word; }

.bp3-alert-footer{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:reverse;
      -ms-flex-direction:row-reverse;
          flex-direction:row-reverse;
  margin-top:10px; }
  .bp3-alert-footer .bp3-button{
    margin-left:10px; }
.bp3-breadcrumbs{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  cursor:default;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-wrap:wrap;
      flex-wrap:wrap;
  height:30px;
  list-style:none;
  margin:0;
  padding:0; }
  .bp3-breadcrumbs > li{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex; }
    .bp3-breadcrumbs > li::after{
      background:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M10.71 7.29l-4-4a1.003 1.003 0 00-1.42 1.42L8.59 8 5.3 11.29c-.19.18-.3.43-.3.71a1.003 1.003 0 001.71.71l4-4c.18-.18.29-.43.29-.71 0-.28-.11-.53-.29-.71z' fill='%235C7080'/%3e%3c/svg%3e");
      content:"";
      display:block;
      height:16px;
      margin:0 5px;
      width:16px; }
    .bp3-breadcrumbs > li:last-of-type::after{
      display:none; }

.bp3-breadcrumb,
.bp3-breadcrumb-current,
.bp3-breadcrumbs-collapsed{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  font-size:16px; }

.bp3-breadcrumb,
.bp3-breadcrumbs-collapsed{
  color:#5c7080; }

.bp3-breadcrumb:hover{
  text-decoration:none; }

.bp3-breadcrumb.bp3-disabled{
  color:rgba(92, 112, 128, 0.6);
  cursor:not-allowed; }

.bp3-breadcrumb .bp3-icon{
  margin-right:5px; }

.bp3-breadcrumb-current{
  color:inherit;
  font-weight:600; }
  .bp3-breadcrumb-current .bp3-input{
    font-size:inherit;
    font-weight:inherit;
    vertical-align:baseline; }

.bp3-breadcrumbs-collapsed{
  background:#ced9e0;
  border:none;
  border-radius:3px;
  cursor:pointer;
  margin-right:2px;
  padding:1px 5px;
  vertical-align:text-bottom; }
  .bp3-breadcrumbs-collapsed::before{
    background:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cg fill='%235C7080'%3e%3ccircle cx='2' cy='8.03' r='2'/%3e%3ccircle cx='14' cy='8.03' r='2'/%3e%3ccircle cx='8' cy='8.03' r='2'/%3e%3c/g%3e%3c/svg%3e") center no-repeat;
    content:"";
    display:block;
    height:16px;
    width:16px; }
  .bp3-breadcrumbs-collapsed:hover{
    background:#bfccd6;
    color:#182026;
    text-decoration:none; }

.bp3-dark .bp3-breadcrumb,
.bp3-dark .bp3-breadcrumbs-collapsed{
  color:#a7b6c2; }

.bp3-dark .bp3-breadcrumbs > li::after{
  color:#a7b6c2; }

.bp3-dark .bp3-breadcrumb.bp3-disabled{
  color:rgba(167, 182, 194, 0.6); }

.bp3-dark .bp3-breadcrumb-current{
  color:#f5f8fa; }

.bp3-dark .bp3-breadcrumbs-collapsed{
  background:rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-breadcrumbs-collapsed:hover{
    background:rgba(16, 22, 26, 0.6);
    color:#f5f8fa; }
.bp3-button{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  border:none;
  border-radius:3px;
  cursor:pointer;
  font-size:14px;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  padding:5px 10px;
  text-align:left;
  vertical-align:middle;
  min-height:30px;
  min-width:30px; }
  .bp3-button > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-button > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-button::before,
  .bp3-button > *{
    margin-right:7px; }
  .bp3-button:empty::before,
  .bp3-button > :last-child{
    margin-right:0; }
  .bp3-button:empty{
    padding:0 !important; }
  .bp3-button:disabled, .bp3-button.bp3-disabled{
    cursor:not-allowed; }
  .bp3-button.bp3-fill{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    width:100%; }
  .bp3-button.bp3-align-right,
  .bp3-align-right .bp3-button{
    text-align:right; }
  .bp3-button.bp3-align-left,
  .bp3-align-left .bp3-button{
    text-align:left; }
  .bp3-button:not([class*="bp3-intent-"]){
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    color:#182026; }
    .bp3-button:not([class*="bp3-intent-"]):hover{
      background-clip:padding-box;
      background-color:#ebf1f5;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
    .bp3-button:not([class*="bp3-intent-"]):active, .bp3-button:not([class*="bp3-intent-"]).bp3-active{
      background-color:#d8e1e8;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button:not([class*="bp3-intent-"]):disabled, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled{
      background-color:rgba(206, 217, 224, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      outline:none; }
      .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active, .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active:hover, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active:hover{
        background:rgba(206, 217, 224, 0.7); }
  .bp3-button.bp3-intent-primary{
    background-color:#137cbd;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
    .bp3-button.bp3-intent-primary:hover, .bp3-button.bp3-intent-primary:active, .bp3-button.bp3-intent-primary.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-primary:hover{
      background-color:#106ba3;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-primary:active, .bp3-button.bp3-intent-primary.bp3-active{
      background-color:#0e5a8a;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-primary:disabled, .bp3-button.bp3-intent-primary.bp3-disabled{
      background-color:rgba(19, 124, 189, 0.5);
      background-image:none;
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button.bp3-intent-success{
    background-color:#0f9960;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
    .bp3-button.bp3-intent-success:hover, .bp3-button.bp3-intent-success:active, .bp3-button.bp3-intent-success.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-success:hover{
      background-color:#0d8050;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-success:active, .bp3-button.bp3-intent-success.bp3-active{
      background-color:#0a6640;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-success:disabled, .bp3-button.bp3-intent-success.bp3-disabled{
      background-color:rgba(15, 153, 96, 0.5);
      background-image:none;
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button.bp3-intent-warning{
    background-color:#d9822b;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
    .bp3-button.bp3-intent-warning:hover, .bp3-button.bp3-intent-warning:active, .bp3-button.bp3-intent-warning.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-warning:hover{
      background-color:#bf7326;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-warning:active, .bp3-button.bp3-intent-warning.bp3-active{
      background-color:#a66321;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-warning:disabled, .bp3-button.bp3-intent-warning.bp3-disabled{
      background-color:rgba(217, 130, 43, 0.5);
      background-image:none;
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button.bp3-intent-danger{
    background-color:#db3737;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
    .bp3-button.bp3-intent-danger:hover, .bp3-button.bp3-intent-danger:active, .bp3-button.bp3-intent-danger.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-danger:hover{
      background-color:#c23030;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-danger:active, .bp3-button.bp3-intent-danger.bp3-active{
      background-color:#a82a2a;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-danger:disabled, .bp3-button.bp3-intent-danger.bp3-disabled{
      background-color:rgba(219, 55, 55, 0.5);
      background-image:none;
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button[class*="bp3-intent-"] .bp3-button-spinner .bp3-spinner-head{
    stroke:#ffffff; }
  .bp3-button.bp3-large,
  .bp3-large .bp3-button{
    min-height:40px;
    min-width:40px;
    font-size:16px;
    padding:5px 15px; }
    .bp3-button.bp3-large::before,
    .bp3-button.bp3-large > *,
    .bp3-large .bp3-button::before,
    .bp3-large .bp3-button > *{
      margin-right:10px; }
    .bp3-button.bp3-large:empty::before,
    .bp3-button.bp3-large > :last-child,
    .bp3-large .bp3-button:empty::before,
    .bp3-large .bp3-button > :last-child{
      margin-right:0; }
  .bp3-button.bp3-small,
  .bp3-small .bp3-button{
    min-height:24px;
    min-width:24px;
    padding:0 7px; }
  .bp3-button.bp3-loading{
    position:relative; }
    .bp3-button.bp3-loading[class*="bp3-icon-"]::before{
      visibility:hidden; }
    .bp3-button.bp3-loading .bp3-button-spinner{
      margin:0;
      position:absolute; }
    .bp3-button.bp3-loading > :not(.bp3-button-spinner){
      visibility:hidden; }
  .bp3-button[class*="bp3-icon-"]::before{
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-style:normal;
    font-weight:400;
    line-height:1;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    color:#5c7080; }
  .bp3-button .bp3-icon, .bp3-button .bp3-icon-standard, .bp3-button .bp3-icon-large{
    color:#5c7080; }
    .bp3-button .bp3-icon.bp3-align-right, .bp3-button .bp3-icon-standard.bp3-align-right, .bp3-button .bp3-icon-large.bp3-align-right{
      margin-left:7px; }
  .bp3-button .bp3-icon:first-child:last-child,
  .bp3-button .bp3-spinner + .bp3-icon:last-child{
    margin:0 -7px; }
  .bp3-dark .bp3-button:not([class*="bp3-intent-"]){
    background-color:#394b59;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):hover, .bp3-dark .bp3-button:not([class*="bp3-intent-"]):active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-active{
      color:#f5f8fa; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):hover{
      background-color:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-active{
      background-color:#202b33;
      background-image:none;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):disabled, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-disabled{
      background-color:rgba(57, 75, 89, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active{
        background:rgba(57, 75, 89, 0.7); }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-button-spinner .bp3-spinner-head{
      background:rgba(16, 22, 26, 0.5);
      stroke:#8a9ba8; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"])[class*="bp3-icon-"]::before{
      color:#a7b6c2; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon, .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon-standard, .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon-large{
      color:#a7b6c2; }
  .bp3-dark .bp3-button[class*="bp3-intent-"]{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-button[class*="bp3-intent-"]:hover{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-button[class*="bp3-intent-"]:active, .bp3-dark .bp3-button[class*="bp3-intent-"].bp3-active{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-button[class*="bp3-intent-"]:disabled, .bp3-dark .bp3-button[class*="bp3-intent-"].bp3-disabled{
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.3); }
    .bp3-dark .bp3-button[class*="bp3-intent-"] .bp3-button-spinner .bp3-spinner-head{
      stroke:#8a9ba8; }
  .bp3-button:disabled::before,
  .bp3-button:disabled .bp3-icon, .bp3-button:disabled .bp3-icon-standard, .bp3-button:disabled .bp3-icon-large, .bp3-button.bp3-disabled::before,
  .bp3-button.bp3-disabled .bp3-icon, .bp3-button.bp3-disabled .bp3-icon-standard, .bp3-button.bp3-disabled .bp3-icon-large, .bp3-button[class*="bp3-intent-"]::before,
  .bp3-button[class*="bp3-intent-"] .bp3-icon, .bp3-button[class*="bp3-intent-"] .bp3-icon-standard, .bp3-button[class*="bp3-intent-"] .bp3-icon-large{
    color:inherit !important; }
  .bp3-button.bp3-minimal{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none; }
    .bp3-button.bp3-minimal:hover{
      background:rgba(167, 182, 194, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026;
      text-decoration:none; }
    .bp3-button.bp3-minimal:active, .bp3-button.bp3-minimal.bp3-active{
      background:rgba(115, 134, 148, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026; }
    .bp3-button.bp3-minimal:disabled, .bp3-button.bp3-minimal:disabled:hover, .bp3-button.bp3-minimal.bp3-disabled, .bp3-button.bp3-minimal.bp3-disabled:hover{
      background:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
      .bp3-button.bp3-minimal:disabled.bp3-active, .bp3-button.bp3-minimal:disabled:hover.bp3-active, .bp3-button.bp3-minimal.bp3-disabled.bp3-active, .bp3-button.bp3-minimal.bp3-disabled:hover.bp3-active{
        background:rgba(115, 134, 148, 0.3); }
    .bp3-dark .bp3-button.bp3-minimal{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:inherit; }
      .bp3-dark .bp3-button.bp3-minimal:hover, .bp3-dark .bp3-button.bp3-minimal:active, .bp3-dark .bp3-button.bp3-minimal.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-button.bp3-minimal:hover{
        background:rgba(138, 155, 168, 0.15); }
      .bp3-dark .bp3-button.bp3-minimal:active, .bp3-dark .bp3-button.bp3-minimal.bp3-active{
        background:rgba(138, 155, 168, 0.3);
        color:#f5f8fa; }
      .bp3-dark .bp3-button.bp3-minimal:disabled, .bp3-dark .bp3-button.bp3-minimal:disabled:hover, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled:hover{
        background:none;
        color:rgba(167, 182, 194, 0.6);
        cursor:not-allowed; }
        .bp3-dark .bp3-button.bp3-minimal:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal:disabled:hover.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled:hover.bp3-active{
          background:rgba(138, 155, 168, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-primary{
      color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:hover, .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.15);
        color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:disabled, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(16, 107, 163, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-primary:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
        stroke:#106ba3; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary{
        color:#48aff0; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.2);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(72, 175, 240, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-success{
      color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:hover, .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.15);
        color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:disabled, .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(13, 128, 80, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-success:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
        stroke:#0d8050; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success{
        color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.2);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(61, 204, 145, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-warning{
      color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:hover, .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.15);
        color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:disabled, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(191, 115, 38, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-warning:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
        stroke:#bf7326; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning{
        color:#ffb366; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.2);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(255, 179, 102, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-danger{
      color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:hover, .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.15);
        color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:disabled, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(194, 48, 48, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-danger:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
        stroke:#c23030; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger{
        color:#ff7373; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.2);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(255, 115, 115, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
  .bp3-button.bp3-outlined{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    border:1px solid rgba(24, 32, 38, 0.2);
    -webkit-box-sizing:border-box;
            box-sizing:border-box; }
    .bp3-button.bp3-outlined:hover{
      background:rgba(167, 182, 194, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026;
      text-decoration:none; }
    .bp3-button.bp3-outlined:active, .bp3-button.bp3-outlined.bp3-active{
      background:rgba(115, 134, 148, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026; }
    .bp3-button.bp3-outlined:disabled, .bp3-button.bp3-outlined:disabled:hover, .bp3-button.bp3-outlined.bp3-disabled, .bp3-button.bp3-outlined.bp3-disabled:hover{
      background:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
      .bp3-button.bp3-outlined:disabled.bp3-active, .bp3-button.bp3-outlined:disabled:hover.bp3-active, .bp3-button.bp3-outlined.bp3-disabled.bp3-active, .bp3-button.bp3-outlined.bp3-disabled:hover.bp3-active{
        background:rgba(115, 134, 148, 0.3); }
    .bp3-dark .bp3-button.bp3-outlined{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:inherit; }
      .bp3-dark .bp3-button.bp3-outlined:hover, .bp3-dark .bp3-button.bp3-outlined:active, .bp3-dark .bp3-button.bp3-outlined.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-button.bp3-outlined:hover{
        background:rgba(138, 155, 168, 0.15); }
      .bp3-dark .bp3-button.bp3-outlined:active, .bp3-dark .bp3-button.bp3-outlined.bp3-active{
        background:rgba(138, 155, 168, 0.3);
        color:#f5f8fa; }
      .bp3-dark .bp3-button.bp3-outlined:disabled, .bp3-dark .bp3-button.bp3-outlined:disabled:hover, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled:hover{
        background:none;
        color:rgba(167, 182, 194, 0.6);
        cursor:not-allowed; }
        .bp3-dark .bp3-button.bp3-outlined:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined:disabled:hover.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled:hover.bp3-active{
          background:rgba(138, 155, 168, 0.3); }
    .bp3-button.bp3-outlined.bp3-intent-primary{
      color:#106ba3; }
      .bp3-button.bp3-outlined.bp3-intent-primary:hover, .bp3-button.bp3-outlined.bp3-intent-primary:active, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#106ba3; }
      .bp3-button.bp3-outlined.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.15);
        color:#106ba3; }
      .bp3-button.bp3-outlined.bp3-intent-primary:active, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#106ba3; }
      .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(16, 107, 163, 0.5); }
        .bp3-button.bp3-outlined.bp3-intent-primary:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
        stroke:#106ba3; }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary{
        color:#48aff0; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.2);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(72, 175, 240, 0.5); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
    .bp3-button.bp3-outlined.bp3-intent-success{
      color:#0d8050; }
      .bp3-button.bp3-outlined.bp3-intent-success:hover, .bp3-button.bp3-outlined.bp3-intent-success:active, .bp3-button.bp3-outlined.bp3-intent-success.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#0d8050; }
      .bp3-button.bp3-outlined.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.15);
        color:#0d8050; }
      .bp3-button.bp3-outlined.bp3-intent-success:active, .bp3-button.bp3-outlined.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#0d8050; }
      .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(13, 128, 80, 0.5); }
        .bp3-button.bp3-outlined.bp3-intent-success:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
        stroke:#0d8050; }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success{
        color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.2);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(61, 204, 145, 0.5); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
    .bp3-button.bp3-outlined.bp3-intent-warning{
      color:#bf7326; }
      .bp3-button.bp3-outlined.bp3-intent-warning:hover, .bp3-button.bp3-outlined.bp3-intent-warning:active, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#bf7326; }
      .bp3-button.bp3-outlined.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.15);
        color:#bf7326; }
      .bp3-button.bp3-outlined.bp3-intent-warning:active, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#bf7326; }
      .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(191, 115, 38, 0.5); }
        .bp3-button.bp3-outlined.bp3-intent-warning:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
        stroke:#bf7326; }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning{
        color:#ffb366; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.2);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(255, 179, 102, 0.5); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
    .bp3-button.bp3-outlined.bp3-intent-danger{
      color:#c23030; }
      .bp3-button.bp3-outlined.bp3-intent-danger:hover, .bp3-button.bp3-outlined.bp3-intent-danger:active, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#c23030; }
      .bp3-button.bp3-outlined.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.15);
        color:#c23030; }
      .bp3-button.bp3-outlined.bp3-intent-danger:active, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#c23030; }
      .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(194, 48, 48, 0.5); }
        .bp3-button.bp3-outlined.bp3-intent-danger:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
        stroke:#c23030; }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger{
        color:#ff7373; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.2);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(255, 115, 115, 0.5); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
    .bp3-button.bp3-outlined:disabled, .bp3-button.bp3-outlined.bp3-disabled, .bp3-button.bp3-outlined:disabled:hover, .bp3-button.bp3-outlined.bp3-disabled:hover{
      border-color:rgba(92, 112, 128, 0.1); }
    .bp3-dark .bp3-button.bp3-outlined{
      border-color:rgba(255, 255, 255, 0.4); }
      .bp3-dark .bp3-button.bp3-outlined:disabled, .bp3-dark .bp3-button.bp3-outlined:disabled:hover, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled:hover{
        border-color:rgba(255, 255, 255, 0.2); }
    .bp3-button.bp3-outlined.bp3-intent-primary{
      border-color:rgba(16, 107, 163, 0.6); }
      .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
        border-color:rgba(16, 107, 163, 0.2); }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary{
        border-color:rgba(72, 175, 240, 0.6); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
          border-color:rgba(72, 175, 240, 0.2); }
    .bp3-button.bp3-outlined.bp3-intent-success{
      border-color:rgba(13, 128, 80, 0.6); }
      .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
        border-color:rgba(13, 128, 80, 0.2); }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success{
        border-color:rgba(61, 204, 145, 0.6); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
          border-color:rgba(61, 204, 145, 0.2); }
    .bp3-button.bp3-outlined.bp3-intent-warning{
      border-color:rgba(191, 115, 38, 0.6); }
      .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
        border-color:rgba(191, 115, 38, 0.2); }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning{
        border-color:rgba(255, 179, 102, 0.6); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
          border-color:rgba(255, 179, 102, 0.2); }
    .bp3-button.bp3-outlined.bp3-intent-danger{
      border-color:rgba(194, 48, 48, 0.6); }
      .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
        border-color:rgba(194, 48, 48, 0.2); }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger{
        border-color:rgba(255, 115, 115, 0.6); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
          border-color:rgba(255, 115, 115, 0.2); }

a.bp3-button{
  text-align:center;
  text-decoration:none;
  -webkit-transition:none;
  transition:none; }
  a.bp3-button, a.bp3-button:hover, a.bp3-button:active{
    color:#182026; }
  a.bp3-button.bp3-disabled{
    color:rgba(92, 112, 128, 0.6); }

.bp3-button-text{
  -webkit-box-flex:0;
      -ms-flex:0 1 auto;
          flex:0 1 auto; }

.bp3-button.bp3-align-left .bp3-button-text, .bp3-button.bp3-align-right .bp3-button-text,
.bp3-button-group.bp3-align-left .bp3-button-text,
.bp3-button-group.bp3-align-right .bp3-button-text{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto; }
.bp3-button-group{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex; }
  .bp3-button-group .bp3-button{
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    position:relative;
    z-index:4; }
    .bp3-button-group .bp3-button:focus{
      z-index:5; }
    .bp3-button-group .bp3-button:hover{
      z-index:6; }
    .bp3-button-group .bp3-button:active, .bp3-button-group .bp3-button.bp3-active{
      z-index:7; }
    .bp3-button-group .bp3-button:disabled, .bp3-button-group .bp3-button.bp3-disabled{
      z-index:3; }
    .bp3-button-group .bp3-button[class*="bp3-intent-"]{
      z-index:9; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:focus{
        z-index:10; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:hover{
        z-index:11; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:active, .bp3-button-group .bp3-button[class*="bp3-intent-"].bp3-active{
        z-index:12; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:disabled, .bp3-button-group .bp3-button[class*="bp3-intent-"].bp3-disabled{
        z-index:8; }
  .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:first-child) .bp3-button,
  .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:first-child){
    border-bottom-left-radius:0;
    border-top-left-radius:0; }
  .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
  .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:last-child){
    border-bottom-right-radius:0;
    border-top-right-radius:0;
    margin-right:-1px; }
  .bp3-button-group.bp3-minimal .bp3-button{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none; }
    .bp3-button-group.bp3-minimal .bp3-button:hover{
      background:rgba(167, 182, 194, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026;
      text-decoration:none; }
    .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
      background:rgba(115, 134, 148, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026; }
    .bp3-button-group.bp3-minimal .bp3-button:disabled, .bp3-button-group.bp3-minimal .bp3-button:disabled:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover{
      background:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
      .bp3-button-group.bp3-minimal .bp3-button:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button:disabled:hover.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover.bp3-active{
        background:rgba(115, 134, 148, 0.3); }
    .bp3-dark .bp3-button-group.bp3-minimal .bp3-button{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:inherit; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:hover, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:hover{
        background:rgba(138, 155, 168, 0.15); }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
        background:rgba(138, 155, 168, 0.3);
        color:#f5f8fa; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled:hover, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover{
        background:none;
        color:rgba(167, 182, 194, 0.6);
        cursor:not-allowed; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled:hover.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover.bp3-active{
          background:rgba(138, 155, 168, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary{
      color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.15);
        color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(16, 107, 163, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
        stroke:#106ba3; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary{
        color:#48aff0; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.2);
          color:#48aff0; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#48aff0; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(72, 175, 240, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success{
      color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.15);
        color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(13, 128, 80, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
        stroke:#0d8050; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success{
        color:#3dcc91; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.2);
          color:#3dcc91; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#3dcc91; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(61, 204, 145, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning{
      color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.15);
        color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(191, 115, 38, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
        stroke:#bf7326; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning{
        color:#ffb366; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.2);
          color:#ffb366; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#ffb366; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(255, 179, 102, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger{
      color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.15);
        color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(194, 48, 48, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
        stroke:#c23030; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger{
        color:#ff7373; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.2);
          color:#ff7373; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#ff7373; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(255, 115, 115, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
  .bp3-button-group .bp3-popover-wrapper,
  .bp3-button-group .bp3-popover-target{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-button-group.bp3-fill{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    width:100%; }
  .bp3-button-group .bp3-button.bp3-fill,
  .bp3-button-group.bp3-fill .bp3-button:not(.bp3-fixed){
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-button-group.bp3-vertical{
    -webkit-box-align:stretch;
        -ms-flex-align:stretch;
            align-items:stretch;
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column;
    vertical-align:top; }
    .bp3-button-group.bp3-vertical.bp3-fill{
      height:100%;
      width:unset; }
    .bp3-button-group.bp3-vertical .bp3-button{
      margin-right:0 !important;
      width:100%; }
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:first-child .bp3-button,
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:first-child{
      border-radius:3px 3px 0 0; }
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:last-child .bp3-button,
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:last-child{
      border-radius:0 0 3px 3px; }
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:not(:last-child){
      margin-bottom:-1px; }
  .bp3-button-group.bp3-align-left .bp3-button{
    text-align:left; }
  .bp3-dark .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
  .bp3-dark .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:last-child){
    margin-right:1px; }
  .bp3-dark .bp3-button-group.bp3-vertical > .bp3-popover-wrapper:not(:last-child) .bp3-button,
  .bp3-dark .bp3-button-group.bp3-vertical > .bp3-button:not(:last-child){
    margin-bottom:1px; }
.bp3-callout{
  font-size:14px;
  line-height:1.5;
  background-color:rgba(138, 155, 168, 0.15);
  border-radius:3px;
  padding:10px 12px 9px;
  position:relative;
  width:100%; }
  .bp3-callout[class*="bp3-icon-"]{
    padding-left:40px; }
    .bp3-callout[class*="bp3-icon-"]::before{
      font-family:"Icons20", sans-serif;
      font-size:20px;
      font-style:normal;
      font-weight:400;
      line-height:1;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased;
      color:#5c7080;
      left:10px;
      position:absolute;
      top:10px; }
  .bp3-callout.bp3-callout-icon{
    padding-left:40px; }
    .bp3-callout.bp3-callout-icon > .bp3-icon:first-child{
      color:#5c7080;
      left:10px;
      position:absolute;
      top:10px; }
  .bp3-callout .bp3-heading{
    line-height:20px;
    margin-bottom:5px;
    margin-top:0; }
    .bp3-callout .bp3-heading:last-child{
      margin-bottom:0; }
  .bp3-dark .bp3-callout{
    background-color:rgba(138, 155, 168, 0.2); }
    .bp3-dark .bp3-callout[class*="bp3-icon-"]::before{
      color:#a7b6c2; }
  .bp3-callout.bp3-intent-primary{
    background-color:rgba(19, 124, 189, 0.15); }
    .bp3-callout.bp3-intent-primary[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-primary > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-primary .bp3-heading{
      color:#106ba3; }
    .bp3-dark .bp3-callout.bp3-intent-primary{
      background-color:rgba(19, 124, 189, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-primary[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-primary > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-primary .bp3-heading{
        color:#48aff0; }
  .bp3-callout.bp3-intent-success{
    background-color:rgba(15, 153, 96, 0.15); }
    .bp3-callout.bp3-intent-success[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-success > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-success .bp3-heading{
      color:#0d8050; }
    .bp3-dark .bp3-callout.bp3-intent-success{
      background-color:rgba(15, 153, 96, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-success[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-success > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-success .bp3-heading{
        color:#3dcc91; }
  .bp3-callout.bp3-intent-warning{
    background-color:rgba(217, 130, 43, 0.15); }
    .bp3-callout.bp3-intent-warning[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-warning > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-warning .bp3-heading{
      color:#bf7326; }
    .bp3-dark .bp3-callout.bp3-intent-warning{
      background-color:rgba(217, 130, 43, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-warning[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-warning > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-warning .bp3-heading{
        color:#ffb366; }
  .bp3-callout.bp3-intent-danger{
    background-color:rgba(219, 55, 55, 0.15); }
    .bp3-callout.bp3-intent-danger[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-danger > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-danger .bp3-heading{
      color:#c23030; }
    .bp3-dark .bp3-callout.bp3-intent-danger{
      background-color:rgba(219, 55, 55, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-danger[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-danger > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-danger .bp3-heading{
        color:#ff7373; }
  .bp3-running-text .bp3-callout{
    margin:20px 0; }
.bp3-card{
  background-color:#ffffff;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
  padding:20px;
  -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-card.bp3-dark,
  .bp3-dark .bp3-card{
    background-color:#30404d;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }

.bp3-elevation-0{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }
  .bp3-elevation-0.bp3-dark,
  .bp3-dark .bp3-elevation-0{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }

.bp3-elevation-1{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-1.bp3-dark,
  .bp3-dark .bp3-elevation-1{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-elevation-2{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 1px 1px rgba(16, 22, 26, 0.2), 0 2px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 1px 1px rgba(16, 22, 26, 0.2), 0 2px 6px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-2.bp3-dark,
  .bp3-dark .bp3-elevation-2{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.4), 0 2px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.4), 0 2px 6px rgba(16, 22, 26, 0.4); }

.bp3-elevation-3{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-3.bp3-dark,
  .bp3-dark .bp3-elevation-3{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }

.bp3-elevation-4{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-4.bp3-dark,
  .bp3-dark .bp3-elevation-4{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4); }

.bp3-card.bp3-interactive:hover{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  cursor:pointer; }
  .bp3-card.bp3-interactive:hover.bp3-dark,
  .bp3-dark .bp3-card.bp3-interactive:hover{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }

.bp3-card.bp3-interactive:active{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
  opacity:0.9;
  -webkit-transition-duration:0;
          transition-duration:0; }
  .bp3-card.bp3-interactive:active.bp3-dark,
  .bp3-dark .bp3-card.bp3-interactive:active{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-collapse{
  height:0;
  overflow-y:hidden;
  -webkit-transition:height 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:height 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-collapse .bp3-collapse-body{
    -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-collapse .bp3-collapse-body[aria-hidden="true"]{
      display:none; }

.bp3-context-menu .bp3-popover-target{
  display:block; }

.bp3-context-menu-popover-target{
  position:fixed; }

.bp3-divider{
  border-bottom:1px solid rgba(16, 22, 26, 0.15);
  border-right:1px solid rgba(16, 22, 26, 0.15);
  margin:5px; }
  .bp3-dark .bp3-divider{
    border-color:rgba(16, 22, 26, 0.4); }
.bp3-dialog-container{
  opacity:1;
  -webkit-transform:scale(1);
          transform:scale(1);
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  min-height:100%;
  pointer-events:none;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none;
  width:100%; }
  .bp3-dialog-container.bp3-overlay-enter > .bp3-dialog, .bp3-dialog-container.bp3-overlay-appear > .bp3-dialog{
    opacity:0;
    -webkit-transform:scale(0.5);
            transform:scale(0.5); }
  .bp3-dialog-container.bp3-overlay-enter-active > .bp3-dialog, .bp3-dialog-container.bp3-overlay-appear-active > .bp3-dialog{
    opacity:1;
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:opacity, -webkit-transform;
    transition-property:opacity, -webkit-transform;
    transition-property:opacity, transform;
    transition-property:opacity, transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-dialog-container.bp3-overlay-exit > .bp3-dialog{
    opacity:1;
    -webkit-transform:scale(1);
            transform:scale(1); }
  .bp3-dialog-container.bp3-overlay-exit-active > .bp3-dialog{
    opacity:0;
    -webkit-transform:scale(0.5);
            transform:scale(0.5);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:opacity, -webkit-transform;
    transition-property:opacity, -webkit-transform;
    transition-property:opacity, transform;
    transition-property:opacity, transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }

.bp3-dialog{
  background:#ebf1f5;
  border-radius:6px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin:30px 0;
  padding-bottom:20px;
  pointer-events:all;
  -webkit-user-select:text;
     -moz-user-select:text;
      -ms-user-select:text;
          user-select:text;
  width:500px; }
  .bp3-dialog:focus{
    outline:0; }
  .bp3-dialog.bp3-dark,
  .bp3-dark .bp3-dialog{
    background:#293742;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }

.bp3-dialog-header{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background:#ffffff;
  border-radius:6px 6px 0 0;
  -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
          box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  min-height:40px;
  padding-left:20px;
  padding-right:5px;
  z-index:30; }
  .bp3-dialog-header .bp3-icon-large,
  .bp3-dialog-header .bp3-icon{
    color:#5c7080;
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    margin-right:10px; }
  .bp3-dialog-header .bp3-heading{
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    line-height:inherit;
    margin:0; }
    .bp3-dialog-header .bp3-heading:last-child{
      margin-right:20px; }
  .bp3-dark .bp3-dialog-header{
    background:#30404d;
    -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.4);
            box-shadow:0 1px 0 rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-dialog-header .bp3-icon-large,
    .bp3-dark .bp3-dialog-header .bp3-icon{
      color:#a7b6c2; }

.bp3-dialog-body{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  line-height:18px;
  margin:20px; }

.bp3-dialog-footer{
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  margin:0 20px; }

.bp3-dialog-footer-actions{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:end;
      -ms-flex-pack:end;
          justify-content:flex-end; }
  .bp3-dialog-footer-actions .bp3-button{
    margin-left:10px; }
.bp3-multistep-dialog-panels{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex; }

.bp3-multistep-dialog-left-panel{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:1;
      -ms-flex:1;
          flex:1;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column; }
  .bp3-dark .bp3-multistep-dialog-left-panel{
    background:#202b33; }

.bp3-multistep-dialog-right-panel{
  background-color:#f5f8fa;
  border-left:1px solid rgba(16, 22, 26, 0.15);
  border-radius:0 0 6px 0;
  -webkit-box-flex:3;
      -ms-flex:3;
          flex:3;
  min-width:0; }
  .bp3-dark .bp3-multistep-dialog-right-panel{
    background-color:#293742;
    border-left:1px solid rgba(16, 22, 26, 0.4); }

.bp3-multistep-dialog-footer{
  background-color:#ffffff;
  border-radius:0 0 6px 0;
  border-top:1px solid rgba(16, 22, 26, 0.15);
  padding:10px; }
  .bp3-dark .bp3-multistep-dialog-footer{
    background:#30404d;
    border-top:1px solid rgba(16, 22, 26, 0.4); }

.bp3-dialog-step-container{
  background-color:#f5f8fa;
  border-bottom:1px solid rgba(16, 22, 26, 0.15); }
  .bp3-dark .bp3-dialog-step-container{
    background:#293742;
    border-bottom:1px solid rgba(16, 22, 26, 0.4); }
  .bp3-dialog-step-container.bp3-dialog-step-viewed{
    background-color:#ffffff; }
    .bp3-dark .bp3-dialog-step-container.bp3-dialog-step-viewed{
      background:#30404d; }

.bp3-dialog-step{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background-color:#f5f8fa;
  border-radius:6px;
  cursor:not-allowed;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  margin:4px;
  padding:6px 14px; }
  .bp3-dark .bp3-dialog-step{
    background:#293742; }
  .bp3-dialog-step-viewed .bp3-dialog-step{
    background-color:#ffffff;
    cursor:pointer; }
    .bp3-dark .bp3-dialog-step-viewed .bp3-dialog-step{
      background:#30404d; }
  .bp3-dialog-step:hover{
    background-color:#f5f8fa; }
    .bp3-dark .bp3-dialog-step:hover{
      background:#293742; }

.bp3-dialog-step-icon{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background-color:rgba(92, 112, 128, 0.6);
  border-radius:50%;
  color:#ffffff;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  height:25px;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  width:25px; }
  .bp3-dark .bp3-dialog-step-icon{
    background-color:rgba(167, 182, 194, 0.6); }
  .bp3-active.bp3-dialog-step-viewed .bp3-dialog-step-icon{
    background-color:#2b95d6; }
  .bp3-dialog-step-viewed .bp3-dialog-step-icon{
    background-color:#8a9ba8; }

.bp3-dialog-step-title{
  color:rgba(92, 112, 128, 0.6);
  -webkit-box-flex:1;
      -ms-flex:1;
          flex:1;
  padding-left:10px; }
  .bp3-dark .bp3-dialog-step-title{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-active.bp3-dialog-step-viewed .bp3-dialog-step-title{
    color:#2b95d6; }
  .bp3-dialog-step-viewed:not(.bp3-active) .bp3-dialog-step-title{
    color:#182026; }
    .bp3-dark .bp3-dialog-step-viewed:not(.bp3-active) .bp3-dialog-step-title{
      color:#f5f8fa; }
.bp3-drawer{
  background:#ffffff;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin:0;
  padding:0; }
  .bp3-drawer:focus{
    outline:0; }
  .bp3-drawer.bp3-position-top{
    height:50%;
    left:0;
    right:0;
    top:0; }
    .bp3-drawer.bp3-position-top.bp3-overlay-enter, .bp3-drawer.bp3-position-top.bp3-overlay-appear{
      -webkit-transform:translateY(-100%);
              transform:translateY(-100%); }
    .bp3-drawer.bp3-position-top.bp3-overlay-enter-active, .bp3-drawer.bp3-position-top.bp3-overlay-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-top.bp3-overlay-exit{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-drawer.bp3-position-top.bp3-overlay-exit-active{
      -webkit-transform:translateY(-100%);
              transform:translateY(-100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer.bp3-position-bottom{
    bottom:0;
    height:50%;
    left:0;
    right:0; }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-enter, .bp3-drawer.bp3-position-bottom.bp3-overlay-appear{
      -webkit-transform:translateY(100%);
              transform:translateY(100%); }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-enter-active, .bp3-drawer.bp3-position-bottom.bp3-overlay-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-exit{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-exit-active{
      -webkit-transform:translateY(100%);
              transform:translateY(100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer.bp3-position-left{
    bottom:0;
    left:0;
    top:0;
    width:50%; }
    .bp3-drawer.bp3-position-left.bp3-overlay-enter, .bp3-drawer.bp3-position-left.bp3-overlay-appear{
      -webkit-transform:translateX(-100%);
              transform:translateX(-100%); }
    .bp3-drawer.bp3-position-left.bp3-overlay-enter-active, .bp3-drawer.bp3-position-left.bp3-overlay-appear-active{
      -webkit-transform:translateX(0);
              transform:translateX(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-left.bp3-overlay-exit{
      -webkit-transform:translateX(0);
              transform:translateX(0); }
    .bp3-drawer.bp3-position-left.bp3-overlay-exit-active{
      -webkit-transform:translateX(-100%);
              transform:translateX(-100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer.bp3-position-right{
    bottom:0;
    right:0;
    top:0;
    width:50%; }
    .bp3-drawer.bp3-position-right.bp3-overlay-enter, .bp3-drawer.bp3-position-right.bp3-overlay-appear{
      -webkit-transform:translateX(100%);
              transform:translateX(100%); }
    .bp3-drawer.bp3-position-right.bp3-overlay-enter-active, .bp3-drawer.bp3-position-right.bp3-overlay-appear-active{
      -webkit-transform:translateX(0);
              transform:translateX(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-right.bp3-overlay-exit{
      -webkit-transform:translateX(0);
              transform:translateX(0); }
    .bp3-drawer.bp3-position-right.bp3-overlay-exit-active{
      -webkit-transform:translateX(100%);
              transform:translateX(100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
  .bp3-position-right):not(.bp3-vertical){
    bottom:0;
    right:0;
    top:0;
    width:50%; }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-enter, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-appear{
      -webkit-transform:translateX(100%);
              transform:translateX(100%); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-enter-active, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-appear-active{
      -webkit-transform:translateX(0);
              transform:translateX(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-exit{
      -webkit-transform:translateX(0);
              transform:translateX(0); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-exit-active{
      -webkit-transform:translateX(100%);
              transform:translateX(100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
  .bp3-position-right).bp3-vertical{
    bottom:0;
    height:50%;
    left:0;
    right:0; }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-enter, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-appear{
      -webkit-transform:translateY(100%);
              transform:translateY(100%); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-enter-active, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-exit{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-exit-active{
      -webkit-transform:translateY(100%);
              transform:translateY(100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer.bp3-dark,
  .bp3-dark .bp3-drawer{
    background:#30404d;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }

.bp3-drawer-header{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  border-radius:0;
  -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
          box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  min-height:40px;
  padding:5px;
  padding-left:20px;
  position:relative; }
  .bp3-drawer-header .bp3-icon-large,
  .bp3-drawer-header .bp3-icon{
    color:#5c7080;
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    margin-right:10px; }
  .bp3-drawer-header .bp3-heading{
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    line-height:inherit;
    margin:0; }
    .bp3-drawer-header .bp3-heading:last-child{
      margin-right:20px; }
  .bp3-dark .bp3-drawer-header{
    -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.4);
            box-shadow:0 1px 0 rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-drawer-header .bp3-icon-large,
    .bp3-dark .bp3-drawer-header .bp3-icon{
      color:#a7b6c2; }

.bp3-drawer-body{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  line-height:18px;
  overflow:auto; }

.bp3-drawer-footer{
  -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
          box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  padding:10px 20px;
  position:relative; }
  .bp3-dark .bp3-drawer-footer{
    -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.4); }
.bp3-editable-text{
  cursor:text;
  display:inline-block;
  max-width:100%;
  position:relative;
  vertical-align:top;
  white-space:nowrap; }
  .bp3-editable-text::before{
    bottom:-3px;
    left:-3px;
    position:absolute;
    right:-3px;
    top:-3px;
    border-radius:3px;
    content:"";
    -webkit-transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-editable-text:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
  .bp3-editable-text.bp3-editable-text-editing::before{
    background-color:#ffffff;
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-disabled::before{
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-editable-text.bp3-intent-primary .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-primary .bp3-editable-text-content{
    color:#137cbd; }
  .bp3-editable-text.bp3-intent-primary:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(19, 124, 189, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(19, 124, 189, 0.4); }
  .bp3-editable-text.bp3-intent-primary.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-intent-success .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-success .bp3-editable-text-content{
    color:#0f9960; }
  .bp3-editable-text.bp3-intent-success:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px rgba(15, 153, 96, 0.4);
            box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px rgba(15, 153, 96, 0.4); }
  .bp3-editable-text.bp3-intent-success.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-intent-warning .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-warning .bp3-editable-text-content{
    color:#d9822b; }
  .bp3-editable-text.bp3-intent-warning:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px rgba(217, 130, 43, 0.4);
            box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px rgba(217, 130, 43, 0.4); }
  .bp3-editable-text.bp3-intent-warning.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-intent-danger .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-danger .bp3-editable-text-content{
    color:#db3737; }
  .bp3-editable-text.bp3-intent-danger:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px rgba(219, 55, 55, 0.4);
            box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px rgba(219, 55, 55, 0.4); }
  .bp3-editable-text.bp3-intent-danger.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-editable-text:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(255, 255, 255, 0.15);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(255, 255, 255, 0.15); }
  .bp3-dark .bp3-editable-text.bp3-editable-text-editing::before{
    background-color:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-disabled::before{
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-dark .bp3-editable-text.bp3-intent-primary .bp3-editable-text-content{
    color:#48aff0; }
  .bp3-dark .bp3-editable-text.bp3-intent-primary:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(72, 175, 240, 0), 0 0 0 0 rgba(72, 175, 240, 0), inset 0 0 0 1px rgba(72, 175, 240, 0.4);
            box-shadow:0 0 0 0 rgba(72, 175, 240, 0), 0 0 0 0 rgba(72, 175, 240, 0), inset 0 0 0 1px rgba(72, 175, 240, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-primary.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #48aff0, 0 0 0 3px rgba(72, 175, 240, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #48aff0, 0 0 0 3px rgba(72, 175, 240, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-success .bp3-editable-text-content{
    color:#3dcc91; }
  .bp3-dark .bp3-editable-text.bp3-intent-success:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(61, 204, 145, 0), 0 0 0 0 rgba(61, 204, 145, 0), inset 0 0 0 1px rgba(61, 204, 145, 0.4);
            box-shadow:0 0 0 0 rgba(61, 204, 145, 0), 0 0 0 0 rgba(61, 204, 145, 0), inset 0 0 0 1px rgba(61, 204, 145, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-success.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #3dcc91, 0 0 0 3px rgba(61, 204, 145, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #3dcc91, 0 0 0 3px rgba(61, 204, 145, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-warning .bp3-editable-text-content{
    color:#ffb366; }
  .bp3-dark .bp3-editable-text.bp3-intent-warning:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(255, 179, 102, 0), 0 0 0 0 rgba(255, 179, 102, 0), inset 0 0 0 1px rgba(255, 179, 102, 0.4);
            box-shadow:0 0 0 0 rgba(255, 179, 102, 0), 0 0 0 0 rgba(255, 179, 102, 0), inset 0 0 0 1px rgba(255, 179, 102, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-warning.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #ffb366, 0 0 0 3px rgba(255, 179, 102, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #ffb366, 0 0 0 3px rgba(255, 179, 102, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-danger .bp3-editable-text-content{
    color:#ff7373; }
  .bp3-dark .bp3-editable-text.bp3-intent-danger:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(255, 115, 115, 0), 0 0 0 0 rgba(255, 115, 115, 0), inset 0 0 0 1px rgba(255, 115, 115, 0.4);
            box-shadow:0 0 0 0 rgba(255, 115, 115, 0), 0 0 0 0 rgba(255, 115, 115, 0), inset 0 0 0 1px rgba(255, 115, 115, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-danger.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #ff7373, 0 0 0 3px rgba(255, 115, 115, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #ff7373, 0 0 0 3px rgba(255, 115, 115, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-editable-text-input,
.bp3-editable-text-content{
  color:inherit;
  display:inherit;
  font:inherit;
  letter-spacing:inherit;
  max-width:inherit;
  min-width:inherit;
  position:relative;
  resize:none;
  text-transform:inherit;
  vertical-align:top; }

.bp3-editable-text-input{
  background:none;
  border:none;
  -webkit-box-shadow:none;
          box-shadow:none;
  padding:0;
  white-space:pre-wrap;
  width:100%; }
  .bp3-editable-text-input::-webkit-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input::-moz-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input:-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input::-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input::placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input:focus{
    outline:none; }
  .bp3-editable-text-input::-ms-clear{
    display:none; }

.bp3-editable-text-content{
  overflow:hidden;
  padding-right:2px;
  text-overflow:ellipsis;
  white-space:pre; }
  .bp3-editable-text-editing > .bp3-editable-text-content{
    left:0;
    position:absolute;
    visibility:hidden; }
  .bp3-editable-text-placeholder > .bp3-editable-text-content{
    color:rgba(92, 112, 128, 0.6); }
    .bp3-dark .bp3-editable-text-placeholder > .bp3-editable-text-content{
      color:rgba(167, 182, 194, 0.6); }

.bp3-editable-text.bp3-multiline{
  display:block; }
  .bp3-editable-text.bp3-multiline .bp3-editable-text-content{
    overflow:auto;
    white-space:pre-wrap;
    word-wrap:break-word; }
.bp3-divider{
  border-bottom:1px solid rgba(16, 22, 26, 0.15);
  border-right:1px solid rgba(16, 22, 26, 0.15);
  margin:5px; }
  .bp3-dark .bp3-divider{
    border-color:rgba(16, 22, 26, 0.4); }
.bp3-control-group{
  -webkit-transform:translateZ(0);
          transform:translateZ(0);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:stretch;
      -ms-flex-align:stretch;
          align-items:stretch; }
  .bp3-control-group > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-control-group > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-control-group .bp3-button,
  .bp3-control-group .bp3-html-select,
  .bp3-control-group .bp3-input,
  .bp3-control-group .bp3-select{
    position:relative; }
  .bp3-control-group .bp3-input{
    border-radius:inherit;
    z-index:2; }
    .bp3-control-group .bp3-input:focus{
      border-radius:3px;
      z-index:14; }
    .bp3-control-group .bp3-input[class*="bp3-intent"]{
      z-index:13; }
      .bp3-control-group .bp3-input[class*="bp3-intent"]:focus{
        z-index:15; }
    .bp3-control-group .bp3-input[readonly], .bp3-control-group .bp3-input:disabled, .bp3-control-group .bp3-input.bp3-disabled{
      z-index:1; }
  .bp3-control-group .bp3-input-group[class*="bp3-intent"] .bp3-input{
    z-index:13; }
    .bp3-control-group .bp3-input-group[class*="bp3-intent"] .bp3-input:focus{
      z-index:15; }
  .bp3-control-group .bp3-button,
  .bp3-control-group .bp3-html-select select,
  .bp3-control-group .bp3-select select{
    -webkit-transform:translateZ(0);
            transform:translateZ(0);
    border-radius:inherit;
    z-index:4; }
    .bp3-control-group .bp3-button:focus,
    .bp3-control-group .bp3-html-select select:focus,
    .bp3-control-group .bp3-select select:focus{
      z-index:5; }
    .bp3-control-group .bp3-button:hover,
    .bp3-control-group .bp3-html-select select:hover,
    .bp3-control-group .bp3-select select:hover{
      z-index:6; }
    .bp3-control-group .bp3-button:active,
    .bp3-control-group .bp3-html-select select:active,
    .bp3-control-group .bp3-select select:active{
      z-index:7; }
    .bp3-control-group .bp3-button[readonly], .bp3-control-group .bp3-button:disabled, .bp3-control-group .bp3-button.bp3-disabled,
    .bp3-control-group .bp3-html-select select[readonly],
    .bp3-control-group .bp3-html-select select:disabled,
    .bp3-control-group .bp3-html-select select.bp3-disabled,
    .bp3-control-group .bp3-select select[readonly],
    .bp3-control-group .bp3-select select:disabled,
    .bp3-control-group .bp3-select select.bp3-disabled{
      z-index:3; }
    .bp3-control-group .bp3-button[class*="bp3-intent"],
    .bp3-control-group .bp3-html-select select[class*="bp3-intent"],
    .bp3-control-group .bp3-select select[class*="bp3-intent"]{
      z-index:9; }
      .bp3-control-group .bp3-button[class*="bp3-intent"]:focus,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:focus,
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:focus{
        z-index:10; }
      .bp3-control-group .bp3-button[class*="bp3-intent"]:hover,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:hover,
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:hover{
        z-index:11; }
      .bp3-control-group .bp3-button[class*="bp3-intent"]:active,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:active,
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:active{
        z-index:12; }
      .bp3-control-group .bp3-button[class*="bp3-intent"][readonly], .bp3-control-group .bp3-button[class*="bp3-intent"]:disabled, .bp3-control-group .bp3-button[class*="bp3-intent"].bp3-disabled,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"][readonly],
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:disabled,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"].bp3-disabled,
      .bp3-control-group .bp3-select select[class*="bp3-intent"][readonly],
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:disabled,
      .bp3-control-group .bp3-select select[class*="bp3-intent"].bp3-disabled{
        z-index:8; }
  .bp3-control-group .bp3-input-group > .bp3-icon,
  .bp3-control-group .bp3-input-group > .bp3-button,
  .bp3-control-group .bp3-input-group > .bp3-input-left-container,
  .bp3-control-group .bp3-input-group > .bp3-input-action{
    z-index:16; }
  .bp3-control-group .bp3-select::after,
  .bp3-control-group .bp3-html-select::after,
  .bp3-control-group .bp3-select > .bp3-icon,
  .bp3-control-group .bp3-html-select > .bp3-icon{
    z-index:17; }
  .bp3-control-group .bp3-select:focus-within{
    z-index:5; }
  .bp3-control-group:not(.bp3-vertical) > *:not(.bp3-divider){
    margin-right:-1px; }
  .bp3-control-group:not(.bp3-vertical) > .bp3-divider:not(:first-child){
    margin-left:6px; }
  .bp3-dark .bp3-control-group:not(.bp3-vertical) > *:not(.bp3-divider){
    margin-right:0; }
  .bp3-dark .bp3-control-group:not(.bp3-vertical) > .bp3-button + .bp3-button{
    margin-left:1px; }
  .bp3-control-group .bp3-popover-wrapper,
  .bp3-control-group .bp3-popover-target{
    border-radius:inherit; }
  .bp3-control-group > :first-child{
    border-radius:3px 0 0 3px; }
  .bp3-control-group > :last-child{
    border-radius:0 3px 3px 0;
    margin-right:0; }
  .bp3-control-group > :only-child{
    border-radius:3px;
    margin-right:0; }
  .bp3-control-group .bp3-input-group .bp3-button{
    border-radius:3px; }
  .bp3-control-group .bp3-numeric-input:not(:first-child) .bp3-input-group{
    border-bottom-left-radius:0;
    border-top-left-radius:0; }
  .bp3-control-group.bp3-fill{
    width:100%; }
  .bp3-control-group > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-control-group.bp3-fill > *:not(.bp3-fixed){
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-control-group.bp3-vertical{
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column; }
    .bp3-control-group.bp3-vertical > *{
      margin-top:-1px; }
    .bp3-control-group.bp3-vertical > :first-child{
      border-radius:3px 3px 0 0;
      margin-top:0; }
    .bp3-control-group.bp3-vertical > :last-child{
      border-radius:0 0 3px 3px; }
.bp3-control{
  cursor:pointer;
  display:block;
  margin-bottom:10px;
  position:relative;
  text-transform:none; }
  .bp3-control input:checked ~ .bp3-control-indicator{
    background-color:#137cbd;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
  .bp3-control:hover input:checked ~ .bp3-control-indicator{
    background-color:#106ba3;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
  .bp3-control input:not(:disabled):active:checked ~ .bp3-control-indicator{
    background:#0e5a8a;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-control input:disabled:checked ~ .bp3-control-indicator{
    background:rgba(19, 124, 189, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-dark .bp3-control input:checked ~ .bp3-control-indicator{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control:hover input:checked ~ .bp3-control-indicator{
    background-color:#106ba3;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control input:not(:disabled):active:checked ~ .bp3-control-indicator{
    background-color:#0e5a8a;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-control input:disabled:checked ~ .bp3-control-indicator{
    background:rgba(14, 90, 138, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-control:not(.bp3-align-right){
    padding-left:26px; }
    .bp3-control:not(.bp3-align-right) .bp3-control-indicator{
      margin-left:-26px; }
  .bp3-control.bp3-align-right{
    padding-right:26px; }
    .bp3-control.bp3-align-right .bp3-control-indicator{
      margin-right:-26px; }
  .bp3-control.bp3-disabled{
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }
  .bp3-control.bp3-inline{
    display:inline-block;
    margin-right:20px; }
  .bp3-control input{
    left:0;
    opacity:0;
    position:absolute;
    top:0;
    z-index:-1; }
  .bp3-control .bp3-control-indicator{
    background-clip:padding-box;
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    border:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    cursor:pointer;
    display:inline-block;
    font-size:16px;
    height:1em;
    margin-right:10px;
    margin-top:-3px;
    position:relative;
    -webkit-user-select:none;
       -moz-user-select:none;
        -ms-user-select:none;
            user-select:none;
    vertical-align:middle;
    width:1em; }
    .bp3-control .bp3-control-indicator::before{
      content:"";
      display:block;
      height:1em;
      width:1em; }
  .bp3-control:hover .bp3-control-indicator{
    background-color:#ebf1f5; }
  .bp3-control input:not(:disabled):active ~ .bp3-control-indicator{
    background:#d8e1e8;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-control input:disabled ~ .bp3-control-indicator{
    background:rgba(206, 217, 224, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none;
    cursor:not-allowed; }
  .bp3-control input:focus ~ .bp3-control-indicator{
    outline:rgba(19, 124, 189, 0.6) auto 2px;
    outline-offset:2px;
    -moz-outline-radius:6px; }
  .bp3-control.bp3-align-right .bp3-control-indicator{
    float:right;
    margin-left:10px;
    margin-top:1px; }
  .bp3-control.bp3-large{
    font-size:16px; }
    .bp3-control.bp3-large:not(.bp3-align-right){
      padding-left:30px; }
      .bp3-control.bp3-large:not(.bp3-align-right) .bp3-control-indicator{
        margin-left:-30px; }
    .bp3-control.bp3-large.bp3-align-right{
      padding-right:30px; }
      .bp3-control.bp3-large.bp3-align-right .bp3-control-indicator{
        margin-right:-30px; }
    .bp3-control.bp3-large .bp3-control-indicator{
      font-size:20px; }
    .bp3-control.bp3-large.bp3-align-right .bp3-control-indicator{
      margin-top:0; }
  .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator{
    background-color:#137cbd;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
  .bp3-control.bp3-checkbox:hover input:indeterminate ~ .bp3-control-indicator{
    background-color:#106ba3;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
  .bp3-control.bp3-checkbox input:not(:disabled):active:indeterminate ~ .bp3-control-indicator{
    background:#0e5a8a;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
    background:rgba(19, 124, 189, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-dark .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-checkbox:hover input:indeterminate ~ .bp3-control-indicator{
    background-color:#106ba3;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-checkbox input:not(:disabled):active:indeterminate ~ .bp3-control-indicator{
    background-color:#0e5a8a;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
    background:rgba(14, 90, 138, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-control.bp3-checkbox .bp3-control-indicator{
    border-radius:3px; }
  .bp3-control.bp3-checkbox input:checked ~ .bp3-control-indicator::before{
    background-image:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M12 5c-.28 0-.53.11-.71.29L7 9.59l-2.29-2.3a1.003 1.003 0 00-1.42 1.42l3 3c.18.18.43.29.71.29s.53-.11.71-.29l5-5A1.003 1.003 0 0012 5z' fill='white'/%3e%3c/svg%3e"); }
  .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator::before{
    background-image:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M11 7H5c-.55 0-1 .45-1 1s.45 1 1 1h6c.55 0 1-.45 1-1s-.45-1-1-1z' fill='white'/%3e%3c/svg%3e"); }
  .bp3-control.bp3-radio .bp3-control-indicator{
    border-radius:50%; }
  .bp3-control.bp3-radio input:checked ~ .bp3-control-indicator::before{
    background-image:radial-gradient(#ffffff, #ffffff 28%, transparent 32%); }
  .bp3-control.bp3-radio input:checked:disabled ~ .bp3-control-indicator::before{
    opacity:0.5; }
  .bp3-control.bp3-radio input:focus ~ .bp3-control-indicator{
    -moz-outline-radius:16px; }
  .bp3-control.bp3-switch input ~ .bp3-control-indicator{
    background:rgba(167, 182, 194, 0.5); }
  .bp3-control.bp3-switch:hover input ~ .bp3-control-indicator{
    background:rgba(115, 134, 148, 0.5); }
  .bp3-control.bp3-switch input:not(:disabled):active ~ .bp3-control-indicator{
    background:rgba(92, 112, 128, 0.5); }
  .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator{
    background:rgba(206, 217, 224, 0.5); }
    .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator::before{
      background:rgba(255, 255, 255, 0.8); }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator{
    background:#137cbd; }
  .bp3-control.bp3-switch:hover input:checked ~ .bp3-control-indicator{
    background:#106ba3; }
  .bp3-control.bp3-switch input:checked:not(:disabled):active ~ .bp3-control-indicator{
    background:#0e5a8a; }
  .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator{
    background:rgba(19, 124, 189, 0.5); }
    .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator::before{
      background:rgba(255, 255, 255, 0.8); }
  .bp3-control.bp3-switch:not(.bp3-align-right){
    padding-left:38px; }
    .bp3-control.bp3-switch:not(.bp3-align-right) .bp3-control-indicator{
      margin-left:-38px; }
  .bp3-control.bp3-switch.bp3-align-right{
    padding-right:38px; }
    .bp3-control.bp3-switch.bp3-align-right .bp3-control-indicator{
      margin-right:-38px; }
  .bp3-control.bp3-switch .bp3-control-indicator{
    border:none;
    border-radius:1.75em;
    -webkit-box-shadow:none !important;
            box-shadow:none !important;
    min-width:1.75em;
    -webkit-transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    width:auto; }
    .bp3-control.bp3-switch .bp3-control-indicator::before{
      background:#ffffff;
      border-radius:50%;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
      height:calc(1em - 4px);
      left:0;
      margin:2px;
      position:absolute;
      -webkit-transition:left 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:left 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
      width:calc(1em - 4px); }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator::before{
    left:calc(100% - 1em); }
  .bp3-control.bp3-switch.bp3-large:not(.bp3-align-right){
    padding-left:45px; }
    .bp3-control.bp3-switch.bp3-large:not(.bp3-align-right) .bp3-control-indicator{
      margin-left:-45px; }
  .bp3-control.bp3-switch.bp3-large.bp3-align-right{
    padding-right:45px; }
    .bp3-control.bp3-switch.bp3-large.bp3-align-right .bp3-control-indicator{
      margin-right:-45px; }
  .bp3-dark .bp3-control.bp3-switch input ~ .bp3-control-indicator{
    background:rgba(16, 22, 26, 0.5); }
  .bp3-dark .bp3-control.bp3-switch:hover input ~ .bp3-control-indicator{
    background:rgba(16, 22, 26, 0.7); }
  .bp3-dark .bp3-control.bp3-switch input:not(:disabled):active ~ .bp3-control-indicator{
    background:rgba(16, 22, 26, 0.9); }
  .bp3-dark .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator{
    background:rgba(57, 75, 89, 0.5); }
    .bp3-dark .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator::before{
      background:rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator{
    background:#137cbd; }
  .bp3-dark .bp3-control.bp3-switch:hover input:checked ~ .bp3-control-indicator{
    background:#106ba3; }
  .bp3-dark .bp3-control.bp3-switch input:checked:not(:disabled):active ~ .bp3-control-indicator{
    background:#0e5a8a; }
  .bp3-dark .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator{
    background:rgba(14, 90, 138, 0.5); }
    .bp3-dark .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator::before{
      background:rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-switch .bp3-control-indicator::before{
    background:#394b59;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator::before{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-control.bp3-switch .bp3-switch-inner-text{
    font-size:0.7em;
    text-align:center; }
  .bp3-control.bp3-switch .bp3-control-indicator-child:first-child{
    line-height:0;
    margin-left:0.5em;
    margin-right:1.2em;
    visibility:hidden; }
  .bp3-control.bp3-switch .bp3-control-indicator-child:last-child{
    line-height:1em;
    margin-left:1.2em;
    margin-right:0.5em;
    visibility:visible; }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator .bp3-control-indicator-child:first-child{
    line-height:1em;
    visibility:visible; }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator .bp3-control-indicator-child:last-child{
    line-height:0;
    visibility:hidden; }
  .bp3-dark .bp3-control{
    color:#f5f8fa; }
    .bp3-dark .bp3-control.bp3-disabled{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-control .bp3-control-indicator{
      background-color:#394b59;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-control:hover .bp3-control-indicator{
      background-color:#30404d; }
    .bp3-dark .bp3-control input:not(:disabled):active ~ .bp3-control-indicator{
      background:#202b33;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-control input:disabled ~ .bp3-control-indicator{
      background:rgba(57, 75, 89, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      cursor:not-allowed; }
    .bp3-dark .bp3-control.bp3-checkbox input:disabled:checked ~ .bp3-control-indicator, .bp3-dark .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
      color:rgba(167, 182, 194, 0.6); }
.bp3-file-input{
  cursor:pointer;
  display:inline-block;
  height:30px;
  position:relative; }
  .bp3-file-input input{
    margin:0;
    min-width:200px;
    opacity:0; }
    .bp3-file-input input:disabled + .bp3-file-upload-input,
    .bp3-file-input input.bp3-disabled + .bp3-file-upload-input{
      background:rgba(206, 217, 224, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      resize:none; }
      .bp3-file-input input:disabled + .bp3-file-upload-input::after,
      .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after{
        background-color:rgba(206, 217, 224, 0.5);
        background-image:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(92, 112, 128, 0.6);
        cursor:not-allowed;
        outline:none; }
        .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active, .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active:hover,
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active,
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active:hover{
          background:rgba(206, 217, 224, 0.7); }
      .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input, .bp3-dark
      .bp3-file-input input.bp3-disabled + .bp3-file-upload-input{
        background:rgba(57, 75, 89, 0.5);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(167, 182, 194, 0.6); }
        .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input::after, .bp3-dark
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after{
          background-color:rgba(57, 75, 89, 0.5);
          background-image:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:rgba(167, 182, 194, 0.6); }
          .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active, .bp3-dark
          .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active{
            background:rgba(57, 75, 89, 0.7); }
  .bp3-file-input.bp3-file-input-has-selection .bp3-file-upload-input{
    color:#182026; }
  .bp3-dark .bp3-file-input.bp3-file-input-has-selection .bp3-file-upload-input{
    color:#f5f8fa; }
  .bp3-file-input.bp3-fill{
    width:100%; }
  .bp3-file-input.bp3-large,
  .bp3-large .bp3-file-input{
    height:40px; }
  .bp3-file-input .bp3-file-upload-input-custom-text::after{
    content:attr(bp3-button-text); }

.bp3-file-upload-input{
  -webkit-appearance:none;
     -moz-appearance:none;
          appearance:none;
  background:#ffffff;
  border:none;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
  color:#182026;
  font-size:14px;
  font-weight:400;
  height:30px;
  line-height:30px;
  outline:none;
  padding:0 10px;
  -webkit-transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  vertical-align:middle;
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal;
  color:rgba(92, 112, 128, 0.6);
  left:0;
  padding-right:80px;
  position:absolute;
  right:0;
  top:0;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-file-upload-input::-webkit-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input::-moz-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input:-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input::-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input::placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input:focus, .bp3-file-upload-input.bp3-active{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-file-upload-input[type="search"], .bp3-file-upload-input.bp3-round{
    border-radius:30px;
    -webkit-box-sizing:border-box;
            box-sizing:border-box;
    padding-left:10px; }
  .bp3-file-upload-input[readonly]{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
  .bp3-file-upload-input:disabled, .bp3-file-upload-input.bp3-disabled{
    background:rgba(206, 217, 224, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed;
    resize:none; }
  .bp3-file-upload-input::after{
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    color:#182026;
    min-height:24px;
    min-width:24px;
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    border-radius:3px;
    content:"Browse";
    line-height:24px;
    margin:3px;
    position:absolute;
    right:0;
    text-align:center;
    top:0;
    width:70px; }
    .bp3-file-upload-input::after:hover{
      background-clip:padding-box;
      background-color:#ebf1f5;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
    .bp3-file-upload-input::after:active, .bp3-file-upload-input::after.bp3-active{
      background-color:#d8e1e8;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-file-upload-input::after:disabled, .bp3-file-upload-input::after.bp3-disabled{
      background-color:rgba(206, 217, 224, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      outline:none; }
      .bp3-file-upload-input::after:disabled.bp3-active, .bp3-file-upload-input::after:disabled.bp3-active:hover, .bp3-file-upload-input::after.bp3-disabled.bp3-active, .bp3-file-upload-input::after.bp3-disabled.bp3-active:hover{
        background:rgba(206, 217, 224, 0.7); }
  .bp3-file-upload-input:hover::after{
    background-clip:padding-box;
    background-color:#ebf1f5;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
  .bp3-file-upload-input:active::after{
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-large .bp3-file-upload-input{
    font-size:16px;
    height:40px;
    line-height:40px;
    padding-right:95px; }
    .bp3-large .bp3-file-upload-input[type="search"], .bp3-large .bp3-file-upload-input.bp3-round{
      padding:0 15px; }
    .bp3-large .bp3-file-upload-input::after{
      min-height:30px;
      min-width:30px;
      line-height:30px;
      margin:5px;
      width:85px; }
  .bp3-dark .bp3-file-upload-input{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa;
    color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-file-upload-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-file-upload-input:disabled, .bp3-dark .bp3-file-upload-input.bp3-disabled{
      background:rgba(57, 75, 89, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::after{
      background-color:#394b59;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
      color:#f5f8fa; }
      .bp3-dark .bp3-file-upload-input::after:hover, .bp3-dark .bp3-file-upload-input::after:active, .bp3-dark .bp3-file-upload-input::after.bp3-active{
        color:#f5f8fa; }
      .bp3-dark .bp3-file-upload-input::after:hover{
        background-color:#30404d;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-file-upload-input::after:active, .bp3-dark .bp3-file-upload-input::after.bp3-active{
        background-color:#202b33;
        background-image:none;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-dark .bp3-file-upload-input::after:disabled, .bp3-dark .bp3-file-upload-input::after.bp3-disabled{
        background-color:rgba(57, 75, 89, 0.5);
        background-image:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(167, 182, 194, 0.6); }
        .bp3-dark .bp3-file-upload-input::after:disabled.bp3-active, .bp3-dark .bp3-file-upload-input::after.bp3-disabled.bp3-active{
          background:rgba(57, 75, 89, 0.7); }
      .bp3-dark .bp3-file-upload-input::after .bp3-button-spinner .bp3-spinner-head{
        background:rgba(16, 22, 26, 0.5);
        stroke:#8a9ba8; }
    .bp3-dark .bp3-file-upload-input:hover::after{
      background-color:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-file-upload-input:active::after{
      background-color:#202b33;
      background-image:none;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
.bp3-file-upload-input::after{
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
.bp3-form-group{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin:0 0 15px; }
  .bp3-form-group label.bp3-label{
    margin-bottom:5px; }
  .bp3-form-group .bp3-control{
    margin-top:7px; }
  .bp3-form-group .bp3-form-helper-text{
    color:#5c7080;
    font-size:12px;
    margin-top:5px; }
  .bp3-form-group.bp3-intent-primary .bp3-form-helper-text{
    color:#106ba3; }
  .bp3-form-group.bp3-intent-success .bp3-form-helper-text{
    color:#0d8050; }
  .bp3-form-group.bp3-intent-warning .bp3-form-helper-text{
    color:#bf7326; }
  .bp3-form-group.bp3-intent-danger .bp3-form-helper-text{
    color:#c23030; }
  .bp3-form-group.bp3-inline{
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row; }
    .bp3-form-group.bp3-inline.bp3-large label.bp3-label{
      line-height:40px;
      margin:0 10px 0 0; }
    .bp3-form-group.bp3-inline label.bp3-label{
      line-height:30px;
      margin:0 10px 0 0; }
  .bp3-form-group.bp3-disabled .bp3-label,
  .bp3-form-group.bp3-disabled .bp3-text-muted,
  .bp3-form-group.bp3-disabled .bp3-form-helper-text{
    color:rgba(92, 112, 128, 0.6) !important; }
  .bp3-dark .bp3-form-group.bp3-intent-primary .bp3-form-helper-text{
    color:#48aff0; }
  .bp3-dark .bp3-form-group.bp3-intent-success .bp3-form-helper-text{
    color:#3dcc91; }
  .bp3-dark .bp3-form-group.bp3-intent-warning .bp3-form-helper-text{
    color:#ffb366; }
  .bp3-dark .bp3-form-group.bp3-intent-danger .bp3-form-helper-text{
    color:#ff7373; }
  .bp3-dark .bp3-form-group .bp3-form-helper-text{
    color:#a7b6c2; }
  .bp3-dark .bp3-form-group.bp3-disabled .bp3-label,
  .bp3-dark .bp3-form-group.bp3-disabled .bp3-text-muted,
  .bp3-dark .bp3-form-group.bp3-disabled .bp3-form-helper-text{
    color:rgba(167, 182, 194, 0.6) !important; }
.bp3-input-group{
  display:block;
  position:relative; }
  .bp3-input-group .bp3-input{
    position:relative;
    width:100%; }
    .bp3-input-group .bp3-input:not(:first-child){
      padding-left:30px; }
    .bp3-input-group .bp3-input:not(:last-child){
      padding-right:30px; }
  .bp3-input-group .bp3-input-action,
  .bp3-input-group > .bp3-input-left-container,
  .bp3-input-group > .bp3-button,
  .bp3-input-group > .bp3-icon{
    position:absolute;
    top:0; }
    .bp3-input-group .bp3-input-action:first-child,
    .bp3-input-group > .bp3-input-left-container:first-child,
    .bp3-input-group > .bp3-button:first-child,
    .bp3-input-group > .bp3-icon:first-child{
      left:0; }
    .bp3-input-group .bp3-input-action:last-child,
    .bp3-input-group > .bp3-input-left-container:last-child,
    .bp3-input-group > .bp3-button:last-child,
    .bp3-input-group > .bp3-icon:last-child{
      right:0; }
  .bp3-input-group .bp3-button{
    min-height:24px;
    min-width:24px;
    margin:3px;
    padding:0 7px; }
    .bp3-input-group .bp3-button:empty{
      padding:0; }
  .bp3-input-group > .bp3-input-left-container,
  .bp3-input-group > .bp3-icon{
    z-index:1; }
  .bp3-input-group > .bp3-input-left-container > .bp3-icon,
  .bp3-input-group > .bp3-icon{
    color:#5c7080; }
    .bp3-input-group > .bp3-input-left-container > .bp3-icon:empty,
    .bp3-input-group > .bp3-icon:empty{
      font-family:"Icons16", sans-serif;
      font-size:16px;
      font-style:normal;
      font-weight:400;
      line-height:1;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased; }
  .bp3-input-group > .bp3-input-left-container > .bp3-icon,
  .bp3-input-group > .bp3-icon,
  .bp3-input-group .bp3-input-action > .bp3-spinner{
    margin:7px; }
  .bp3-input-group .bp3-tag{
    margin:5px; }
  .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus),
  .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus){
    color:#5c7080; }
    .bp3-dark .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus), .bp3-dark
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus){
      color:#a7b6c2; }
    .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-standard, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-large,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-standard,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-large{
      color:#5c7080; }
  .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled,
  .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled{
    color:rgba(92, 112, 128, 0.6) !important; }
    .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon-standard, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon-large,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon-standard,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon-large{
      color:rgba(92, 112, 128, 0.6) !important; }
  .bp3-input-group.bp3-disabled{
    cursor:not-allowed; }
    .bp3-input-group.bp3-disabled .bp3-icon{
      color:rgba(92, 112, 128, 0.6); }
  .bp3-input-group.bp3-large .bp3-button{
    min-height:30px;
    min-width:30px;
    margin:5px; }
  .bp3-input-group.bp3-large > .bp3-input-left-container > .bp3-icon,
  .bp3-input-group.bp3-large > .bp3-icon,
  .bp3-input-group.bp3-large .bp3-input-action > .bp3-spinner{
    margin:12px; }
  .bp3-input-group.bp3-large .bp3-input{
    font-size:16px;
    height:40px;
    line-height:40px; }
    .bp3-input-group.bp3-large .bp3-input[type="search"], .bp3-input-group.bp3-large .bp3-input.bp3-round{
      padding:0 15px; }
    .bp3-input-group.bp3-large .bp3-input:not(:first-child){
      padding-left:40px; }
    .bp3-input-group.bp3-large .bp3-input:not(:last-child){
      padding-right:40px; }
  .bp3-input-group.bp3-small .bp3-button{
    min-height:20px;
    min-width:20px;
    margin:2px; }
  .bp3-input-group.bp3-small .bp3-tag{
    min-height:20px;
    min-width:20px;
    margin:2px; }
  .bp3-input-group.bp3-small > .bp3-input-left-container > .bp3-icon,
  .bp3-input-group.bp3-small > .bp3-icon,
  .bp3-input-group.bp3-small .bp3-input-action > .bp3-spinner{
    margin:4px; }
  .bp3-input-group.bp3-small .bp3-input{
    font-size:12px;
    height:24px;
    line-height:24px;
    padding-left:8px;
    padding-right:8px; }
    .bp3-input-group.bp3-small .bp3-input[type="search"], .bp3-input-group.bp3-small .bp3-input.bp3-round{
      padding:0 12px; }
    .bp3-input-group.bp3-small .bp3-input:not(:first-child){
      padding-left:24px; }
    .bp3-input-group.bp3-small .bp3-input:not(:last-child){
      padding-right:24px; }
  .bp3-input-group.bp3-fill{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    width:100%; }
  .bp3-input-group.bp3-round .bp3-button,
  .bp3-input-group.bp3-round .bp3-input,
  .bp3-input-group.bp3-round .bp3-tag{
    border-radius:30px; }
  .bp3-dark .bp3-input-group .bp3-icon{
    color:#a7b6c2; }
  .bp3-dark .bp3-input-group.bp3-disabled .bp3-icon{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-input-group.bp3-intent-primary .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-primary .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-primary .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #137cbd;
              box-shadow:inset 0 0 0 1px #137cbd; }
    .bp3-input-group.bp3-intent-primary .bp3-input:disabled, .bp3-input-group.bp3-intent-primary .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-primary > .bp3-icon{
    color:#106ba3; }
    .bp3-dark .bp3-input-group.bp3-intent-primary > .bp3-icon{
      color:#48aff0; }
  .bp3-input-group.bp3-intent-success .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-success .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-success .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #0f9960;
              box-shadow:inset 0 0 0 1px #0f9960; }
    .bp3-input-group.bp3-intent-success .bp3-input:disabled, .bp3-input-group.bp3-intent-success .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-success > .bp3-icon{
    color:#0d8050; }
    .bp3-dark .bp3-input-group.bp3-intent-success > .bp3-icon{
      color:#3dcc91; }
  .bp3-input-group.bp3-intent-warning .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-warning .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-warning .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #d9822b;
              box-shadow:inset 0 0 0 1px #d9822b; }
    .bp3-input-group.bp3-intent-warning .bp3-input:disabled, .bp3-input-group.bp3-intent-warning .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-warning > .bp3-icon{
    color:#bf7326; }
    .bp3-dark .bp3-input-group.bp3-intent-warning > .bp3-icon{
      color:#ffb366; }
  .bp3-input-group.bp3-intent-danger .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-danger .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-danger .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #db3737;
              box-shadow:inset 0 0 0 1px #db3737; }
    .bp3-input-group.bp3-intent-danger .bp3-input:disabled, .bp3-input-group.bp3-intent-danger .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-danger > .bp3-icon{
    color:#c23030; }
    .bp3-dark .bp3-input-group.bp3-intent-danger > .bp3-icon{
      color:#ff7373; }
.bp3-input{
  -webkit-appearance:none;
     -moz-appearance:none;
          appearance:none;
  background:#ffffff;
  border:none;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
  color:#182026;
  font-size:14px;
  font-weight:400;
  height:30px;
  line-height:30px;
  outline:none;
  padding:0 10px;
  -webkit-transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  vertical-align:middle; }
  .bp3-input::-webkit-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input::-moz-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input:-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input::-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input::placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input:focus, .bp3-input.bp3-active{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-input[type="search"], .bp3-input.bp3-round{
    border-radius:30px;
    -webkit-box-sizing:border-box;
            box-sizing:border-box;
    padding-left:10px; }
  .bp3-input[readonly]{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
  .bp3-input:disabled, .bp3-input.bp3-disabled{
    background:rgba(206, 217, 224, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed;
    resize:none; }
  .bp3-input.bp3-large{
    font-size:16px;
    height:40px;
    line-height:40px; }
    .bp3-input.bp3-large[type="search"], .bp3-input.bp3-large.bp3-round{
      padding:0 15px; }
  .bp3-input.bp3-small{
    font-size:12px;
    height:24px;
    line-height:24px;
    padding-left:8px;
    padding-right:8px; }
    .bp3-input.bp3-small[type="search"], .bp3-input.bp3-small.bp3-round{
      padding:0 12px; }
  .bp3-input.bp3-fill{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    width:100%; }
  .bp3-dark .bp3-input{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark .bp3-input::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input::placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-input:disabled, .bp3-dark .bp3-input.bp3-disabled{
      background:rgba(57, 75, 89, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
  .bp3-input.bp3-intent-primary{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-primary:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-primary[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #137cbd;
              box-shadow:inset 0 0 0 1px #137cbd; }
    .bp3-input.bp3-intent-primary:disabled, .bp3-input.bp3-intent-primary.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-primary:focus{
        -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-primary[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #137cbd;
                box-shadow:inset 0 0 0 1px #137cbd; }
      .bp3-dark .bp3-input.bp3-intent-primary:disabled, .bp3-dark .bp3-input.bp3-intent-primary.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input.bp3-intent-success{
    -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-success:focus{
      -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-success[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #0f9960;
              box-shadow:inset 0 0 0 1px #0f9960; }
    .bp3-input.bp3-intent-success:disabled, .bp3-input.bp3-intent-success.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-success{
      -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-success:focus{
        -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #0f9960, 0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-success[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #0f9960;
                box-shadow:inset 0 0 0 1px #0f9960; }
      .bp3-dark .bp3-input.bp3-intent-success:disabled, .bp3-dark .bp3-input.bp3-intent-success.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input.bp3-intent-warning{
    -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-warning:focus{
      -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-warning[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #d9822b;
              box-shadow:inset 0 0 0 1px #d9822b; }
    .bp3-input.bp3-intent-warning:disabled, .bp3-input.bp3-intent-warning.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-warning:focus{
        -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #d9822b, 0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-warning[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #d9822b;
                box-shadow:inset 0 0 0 1px #d9822b; }
      .bp3-dark .bp3-input.bp3-intent-warning:disabled, .bp3-dark .bp3-input.bp3-intent-warning.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input.bp3-intent-danger{
    -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-danger:focus{
      -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-danger[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #db3737;
              box-shadow:inset 0 0 0 1px #db3737; }
    .bp3-input.bp3-intent-danger:disabled, .bp3-input.bp3-intent-danger.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-danger:focus{
        -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #db3737, 0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-danger[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #db3737;
                box-shadow:inset 0 0 0 1px #db3737; }
      .bp3-dark .bp3-input.bp3-intent-danger:disabled, .bp3-dark .bp3-input.bp3-intent-danger.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input::-ms-clear{
    display:none; }
textarea.bp3-input{
  max-width:100%;
  padding:10px; }
  textarea.bp3-input, textarea.bp3-input.bp3-large, textarea.bp3-input.bp3-small{
    height:auto;
    line-height:inherit; }
  textarea.bp3-input.bp3-small{
    padding:8px; }
  .bp3-dark textarea.bp3-input{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark textarea.bp3-input::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input::placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark textarea.bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark textarea.bp3-input:disabled, .bp3-dark textarea.bp3-input.bp3-disabled{
      background:rgba(57, 75, 89, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
label.bp3-label{
  display:block;
  margin-bottom:15px;
  margin-top:0; }
  label.bp3-label .bp3-html-select,
  label.bp3-label .bp3-input,
  label.bp3-label .bp3-select,
  label.bp3-label .bp3-slider,
  label.bp3-label .bp3-popover-wrapper{
    display:block;
    margin-top:5px;
    text-transform:none; }
  label.bp3-label .bp3-button-group{
    margin-top:5px; }
  label.bp3-label .bp3-select select,
  label.bp3-label .bp3-html-select select{
    font-weight:400;
    vertical-align:top;
    width:100%; }
  label.bp3-label.bp3-disabled,
  label.bp3-label.bp3-disabled .bp3-text-muted{
    color:rgba(92, 112, 128, 0.6); }
  label.bp3-label.bp3-inline{
    line-height:30px; }
    label.bp3-label.bp3-inline .bp3-html-select,
    label.bp3-label.bp3-inline .bp3-input,
    label.bp3-label.bp3-inline .bp3-input-group,
    label.bp3-label.bp3-inline .bp3-select,
    label.bp3-label.bp3-inline .bp3-popover-wrapper{
      display:inline-block;
      margin:0 0 0 5px;
      vertical-align:top; }
    label.bp3-label.bp3-inline .bp3-button-group{
      margin:0 0 0 5px; }
    label.bp3-label.bp3-inline .bp3-input-group .bp3-input{
      margin-left:0; }
    label.bp3-label.bp3-inline.bp3-large{
      line-height:40px; }
  label.bp3-label:not(.bp3-inline) .bp3-popover-target{
    display:block; }
  .bp3-dark label.bp3-label{
    color:#f5f8fa; }
    .bp3-dark label.bp3-label.bp3-disabled,
    .bp3-dark label.bp3-label.bp3-disabled .bp3-text-muted{
      color:rgba(167, 182, 194, 0.6); }
.bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button{
  -webkit-box-flex:1;
      -ms-flex:1 1 14px;
          flex:1 1 14px;
  min-height:0;
  padding:0;
  width:30px; }
  .bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button:first-child{
    border-radius:0 3px 0 0; }
  .bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button:last-child{
    border-radius:0 0 3px 0; }

.bp3-numeric-input .bp3-button-group.bp3-vertical:first-child > .bp3-button:first-child{
  border-radius:3px 0 0 0; }

.bp3-numeric-input .bp3-button-group.bp3-vertical:first-child > .bp3-button:last-child{
  border-radius:0 0 0 3px; }

.bp3-numeric-input.bp3-large .bp3-button-group.bp3-vertical > .bp3-button{
  width:40px; }

form{
  display:block; }
.bp3-html-select select,
.bp3-select select{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  border:none;
  border-radius:3px;
  cursor:pointer;
  font-size:14px;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  padding:5px 10px;
  text-align:left;
  vertical-align:middle;
  background-color:#f5f8fa;
  background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
  background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
  color:#182026;
  -moz-appearance:none;
  -webkit-appearance:none;
  border-radius:3px;
  height:30px;
  padding:0 25px 0 10px;
  width:100%; }
  .bp3-html-select select > *, .bp3-select select > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-html-select select > .bp3-fill, .bp3-select select > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-html-select select::before,
  .bp3-select select::before, .bp3-html-select select > *, .bp3-select select > *{
    margin-right:7px; }
  .bp3-html-select select:empty::before,
  .bp3-select select:empty::before,
  .bp3-html-select select > :last-child,
  .bp3-select select > :last-child{
    margin-right:0; }
  .bp3-html-select select:hover,
  .bp3-select select:hover{
    background-clip:padding-box;
    background-color:#ebf1f5;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
  .bp3-html-select select:active,
  .bp3-select select:active, .bp3-html-select select.bp3-active,
  .bp3-select select.bp3-active{
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-html-select select:disabled,
  .bp3-select select:disabled, .bp3-html-select select.bp3-disabled,
  .bp3-select select.bp3-disabled{
    background-color:rgba(206, 217, 224, 0.5);
    background-image:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed;
    outline:none; }
    .bp3-html-select select:disabled.bp3-active,
    .bp3-select select:disabled.bp3-active, .bp3-html-select select:disabled.bp3-active:hover,
    .bp3-select select:disabled.bp3-active:hover, .bp3-html-select select.bp3-disabled.bp3-active,
    .bp3-select select.bp3-disabled.bp3-active, .bp3-html-select select.bp3-disabled.bp3-active:hover,
    .bp3-select select.bp3-disabled.bp3-active:hover{
      background:rgba(206, 217, 224, 0.7); }

.bp3-html-select.bp3-minimal select,
.bp3-select.bp3-minimal select{
  background:none;
  -webkit-box-shadow:none;
          box-shadow:none; }
  .bp3-html-select.bp3-minimal select:hover,
  .bp3-select.bp3-minimal select:hover{
    background:rgba(167, 182, 194, 0.3);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:#182026;
    text-decoration:none; }
  .bp3-html-select.bp3-minimal select:active,
  .bp3-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal select.bp3-active,
  .bp3-select.bp3-minimal select.bp3-active{
    background:rgba(115, 134, 148, 0.3);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:#182026; }
  .bp3-html-select.bp3-minimal select:disabled,
  .bp3-select.bp3-minimal select:disabled, .bp3-html-select.bp3-minimal select:disabled:hover,
  .bp3-select.bp3-minimal select:disabled:hover, .bp3-html-select.bp3-minimal select.bp3-disabled,
  .bp3-select.bp3-minimal select.bp3-disabled, .bp3-html-select.bp3-minimal select.bp3-disabled:hover,
  .bp3-select.bp3-minimal select.bp3-disabled:hover{
    background:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }
    .bp3-html-select.bp3-minimal select:disabled.bp3-active,
    .bp3-select.bp3-minimal select:disabled.bp3-active, .bp3-html-select.bp3-minimal select:disabled:hover.bp3-active,
    .bp3-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-html-select.bp3-minimal select.bp3-disabled.bp3-active,
    .bp3-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-disabled:hover.bp3-active,
    .bp3-select.bp3-minimal select.bp3-disabled:hover.bp3-active{
      background:rgba(115, 134, 148, 0.3); }
  .bp3-dark .bp3-html-select.bp3-minimal select, .bp3-html-select.bp3-minimal .bp3-dark select,
  .bp3-dark .bp3-select.bp3-minimal select, .bp3-select.bp3-minimal .bp3-dark select{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:inherit; }
    .bp3-dark .bp3-html-select.bp3-minimal select:hover, .bp3-html-select.bp3-minimal .bp3-dark select:hover,
    .bp3-dark .bp3-select.bp3-minimal select:hover, .bp3-select.bp3-minimal .bp3-dark select:hover, .bp3-dark .bp3-html-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal .bp3-dark select:active,
    .bp3-dark .bp3-select.bp3-minimal select:active, .bp3-select.bp3-minimal .bp3-dark select:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-active,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-html-select.bp3-minimal select:hover, .bp3-html-select.bp3-minimal .bp3-dark select:hover,
    .bp3-dark .bp3-select.bp3-minimal select:hover, .bp3-select.bp3-minimal .bp3-dark select:hover{
      background:rgba(138, 155, 168, 0.15); }
    .bp3-dark .bp3-html-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal .bp3-dark select:active,
    .bp3-dark .bp3-select.bp3-minimal select:active, .bp3-select.bp3-minimal .bp3-dark select:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-active,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-active{
      background:rgba(138, 155, 168, 0.3);
      color:#f5f8fa; }
    .bp3-dark .bp3-html-select.bp3-minimal select:disabled, .bp3-html-select.bp3-minimal .bp3-dark select:disabled,
    .bp3-dark .bp3-select.bp3-minimal select:disabled, .bp3-select.bp3-minimal .bp3-dark select:disabled, .bp3-dark .bp3-html-select.bp3-minimal select:disabled:hover, .bp3-html-select.bp3-minimal .bp3-dark select:disabled:hover,
    .bp3-dark .bp3-select.bp3-minimal select:disabled:hover, .bp3-select.bp3-minimal .bp3-dark select:disabled:hover, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled:hover,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled:hover{
      background:none;
      color:rgba(167, 182, 194, 0.6);
      cursor:not-allowed; }
      .bp3-dark .bp3-html-select.bp3-minimal select:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select:disabled.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select:disabled:hover.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-select.bp3-minimal .bp3-dark select:disabled:hover.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled:hover.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled:hover.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled:hover.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled:hover.bp3-active{
        background:rgba(138, 155, 168, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-primary,
  .bp3-select.bp3-minimal select.bp3-intent-primary{
    color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover,
    .bp3-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-html-select.bp3-minimal select.bp3-intent-primary:active,
    .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover,
    .bp3-select.bp3-minimal select.bp3-intent-primary:hover{
      background:rgba(19, 124, 189, 0.15);
      color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:active,
    .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active{
      background:rgba(19, 124, 189, 0.3);
      color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled{
      background:none;
      color:rgba(16, 107, 163, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active{
        background:rgba(19, 124, 189, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
      stroke:#106ba3; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary{
      color:#48aff0; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.2);
        color:#48aff0; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#48aff0; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(72, 175, 240, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-success,
  .bp3-select.bp3-minimal select.bp3-intent-success{
    color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:hover,
    .bp3-select.bp3-minimal select.bp3-intent-success:hover, .bp3-html-select.bp3-minimal select.bp3-intent-success:active,
    .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:hover,
    .bp3-select.bp3-minimal select.bp3-intent-success:hover{
      background:rgba(15, 153, 96, 0.15);
      color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:active,
    .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active{
      background:rgba(15, 153, 96, 0.3);
      color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled{
      background:none;
      color:rgba(13, 128, 80, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active{
        background:rgba(15, 153, 96, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-success .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
      stroke:#0d8050; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success{
      color:#3dcc91; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.2);
        color:#3dcc91; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#3dcc91; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(61, 204, 145, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-warning,
  .bp3-select.bp3-minimal select.bp3-intent-warning{
    color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover,
    .bp3-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-html-select.bp3-minimal select.bp3-intent-warning:active,
    .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover,
    .bp3-select.bp3-minimal select.bp3-intent-warning:hover{
      background:rgba(217, 130, 43, 0.15);
      color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:active,
    .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active{
      background:rgba(217, 130, 43, 0.3);
      color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled{
      background:none;
      color:rgba(191, 115, 38, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active{
        background:rgba(217, 130, 43, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
      stroke:#bf7326; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning{
      color:#ffb366; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.2);
        color:#ffb366; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#ffb366; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(255, 179, 102, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-danger,
  .bp3-select.bp3-minimal select.bp3-intent-danger{
    color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover,
    .bp3-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-html-select.bp3-minimal select.bp3-intent-danger:active,
    .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover,
    .bp3-select.bp3-minimal select.bp3-intent-danger:hover{
      background:rgba(219, 55, 55, 0.15);
      color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:active,
    .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active{
      background:rgba(219, 55, 55, 0.3);
      color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled{
      background:none;
      color:rgba(194, 48, 48, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active{
        background:rgba(219, 55, 55, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
      stroke:#c23030; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger{
      color:#ff7373; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.2);
        color:#ff7373; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#ff7373; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(255, 115, 115, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }

.bp3-html-select.bp3-large select,
.bp3-select.bp3-large select{
  font-size:16px;
  height:40px;
  padding-right:35px; }

.bp3-dark .bp3-html-select select, .bp3-dark .bp3-select select{
  background-color:#394b59;
  background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
  background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
  color:#f5f8fa; }
  .bp3-dark .bp3-html-select select:hover, .bp3-dark .bp3-select select:hover, .bp3-dark .bp3-html-select select:active, .bp3-dark .bp3-select select:active, .bp3-dark .bp3-html-select select.bp3-active, .bp3-dark .bp3-select select.bp3-active{
    color:#f5f8fa; }
  .bp3-dark .bp3-html-select select:hover, .bp3-dark .bp3-select select:hover{
    background-color:#30404d;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-html-select select:active, .bp3-dark .bp3-select select:active, .bp3-dark .bp3-html-select select.bp3-active, .bp3-dark .bp3-select select.bp3-active{
    background-color:#202b33;
    background-image:none;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-html-select select:disabled, .bp3-dark .bp3-select select:disabled, .bp3-dark .bp3-html-select select.bp3-disabled, .bp3-dark .bp3-select select.bp3-disabled{
    background-color:rgba(57, 75, 89, 0.5);
    background-image:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-html-select select:disabled.bp3-active, .bp3-dark .bp3-select select:disabled.bp3-active, .bp3-dark .bp3-html-select select.bp3-disabled.bp3-active, .bp3-dark .bp3-select select.bp3-disabled.bp3-active{
      background:rgba(57, 75, 89, 0.7); }
  .bp3-dark .bp3-html-select select .bp3-button-spinner .bp3-spinner-head, .bp3-dark .bp3-select select .bp3-button-spinner .bp3-spinner-head{
    background:rgba(16, 22, 26, 0.5);
    stroke:#8a9ba8; }

.bp3-html-select select:disabled,
.bp3-select select:disabled{
  background-color:rgba(206, 217, 224, 0.5);
  -webkit-box-shadow:none;
          box-shadow:none;
  color:rgba(92, 112, 128, 0.6);
  cursor:not-allowed; }

.bp3-html-select .bp3-icon,
.bp3-select .bp3-icon, .bp3-select::after{
  color:#5c7080;
  pointer-events:none;
  position:absolute;
  right:7px;
  top:7px; }
  .bp3-html-select .bp3-disabled.bp3-icon,
  .bp3-select .bp3-disabled.bp3-icon, .bp3-disabled.bp3-select::after{
    color:rgba(92, 112, 128, 0.6); }
.bp3-html-select,
.bp3-select{
  display:inline-block;
  letter-spacing:normal;
  position:relative;
  vertical-align:middle; }
  .bp3-html-select select::-ms-expand,
  .bp3-select select::-ms-expand{
    display:none; }
  .bp3-html-select .bp3-icon,
  .bp3-select .bp3-icon{
    color:#5c7080; }
    .bp3-html-select .bp3-icon:hover,
    .bp3-select .bp3-icon:hover{
      color:#182026; }
    .bp3-dark .bp3-html-select .bp3-icon, .bp3-dark
    .bp3-select .bp3-icon{
      color:#a7b6c2; }
      .bp3-dark .bp3-html-select .bp3-icon:hover, .bp3-dark
      .bp3-select .bp3-icon:hover{
        color:#f5f8fa; }
  .bp3-html-select.bp3-large::after,
  .bp3-html-select.bp3-large .bp3-icon,
  .bp3-select.bp3-large::after,
  .bp3-select.bp3-large .bp3-icon{
    right:12px;
    top:12px; }
  .bp3-html-select.bp3-fill,
  .bp3-html-select.bp3-fill select,
  .bp3-select.bp3-fill,
  .bp3-select.bp3-fill select{
    width:100%; }
  .bp3-dark .bp3-html-select option, .bp3-dark
  .bp3-select option{
    background-color:#30404d;
    color:#f5f8fa; }
  .bp3-dark .bp3-html-select option:disabled, .bp3-dark
  .bp3-select option:disabled{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-dark .bp3-html-select::after, .bp3-dark
  .bp3-select::after{
    color:#a7b6c2; }

.bp3-select::after{
  font-family:"Icons16", sans-serif;
  font-size:16px;
  font-style:normal;
  font-weight:400;
  line-height:1;
  -moz-osx-font-smoothing:grayscale;
  -webkit-font-smoothing:antialiased;
  content:""; }
.bp3-running-text table, table.bp3-html-table{
  border-spacing:0;
  font-size:14px; }
  .bp3-running-text table th, table.bp3-html-table th,
  .bp3-running-text table td,
  table.bp3-html-table td{
    padding:11px;
    text-align:left;
    vertical-align:top; }
  .bp3-running-text table th, table.bp3-html-table th{
    color:#182026;
    font-weight:600; }
  
  .bp3-running-text table td,
  table.bp3-html-table td{
    color:#182026; }
  .bp3-running-text table tbody tr:first-child th, table.bp3-html-table tbody tr:first-child th,
  .bp3-running-text table tbody tr:first-child td,
  table.bp3-html-table tbody tr:first-child td,
  .bp3-running-text table tfoot tr:first-child th,
  table.bp3-html-table tfoot tr:first-child th,
  .bp3-running-text table tfoot tr:first-child td,
  table.bp3-html-table tfoot tr:first-child td{
    -webkit-box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15); }
  .bp3-dark .bp3-running-text table th, .bp3-running-text .bp3-dark table th, .bp3-dark table.bp3-html-table th{
    color:#f5f8fa; }
  .bp3-dark .bp3-running-text table td, .bp3-running-text .bp3-dark table td, .bp3-dark table.bp3-html-table td{
    color:#f5f8fa; }
  .bp3-dark .bp3-running-text table tbody tr:first-child th, .bp3-running-text .bp3-dark table tbody tr:first-child th, .bp3-dark table.bp3-html-table tbody tr:first-child th,
  .bp3-dark .bp3-running-text table tbody tr:first-child td,
  .bp3-running-text .bp3-dark table tbody tr:first-child td,
  .bp3-dark table.bp3-html-table tbody tr:first-child td,
  .bp3-dark .bp3-running-text table tfoot tr:first-child th,
  .bp3-running-text .bp3-dark table tfoot tr:first-child th,
  .bp3-dark table.bp3-html-table tfoot tr:first-child th,
  .bp3-dark .bp3-running-text table tfoot tr:first-child td,
  .bp3-running-text .bp3-dark table tfoot tr:first-child td,
  .bp3-dark table.bp3-html-table tfoot tr:first-child td{
    -webkit-box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15); }

table.bp3-html-table.bp3-html-table-condensed th,
table.bp3-html-table.bp3-html-table-condensed td, table.bp3-html-table.bp3-small th,
table.bp3-html-table.bp3-small td{
  padding-bottom:6px;
  padding-top:6px; }

table.bp3-html-table.bp3-html-table-striped tbody tr:nth-child(odd) td{
  background:rgba(191, 204, 214, 0.15); }

table.bp3-html-table.bp3-html-table-bordered th:not(:first-child){
  -webkit-box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15);
          box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15); }

table.bp3-html-table.bp3-html-table-bordered tbody tr td,
table.bp3-html-table.bp3-html-table-bordered tfoot tr td{
  -webkit-box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15);
          box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15); }
  table.bp3-html-table.bp3-html-table-bordered tbody tr td:not(:first-child),
  table.bp3-html-table.bp3-html-table-bordered tfoot tr td:not(:first-child){
    -webkit-box-shadow:inset 1px 1px 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 1px 1px 0 0 rgba(16, 22, 26, 0.15); }

table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td{
  -webkit-box-shadow:none;
          box-shadow:none; }
  table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td:not(:first-child){
    -webkit-box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15); }

table.bp3-html-table.bp3-interactive tbody tr:hover td{
  background-color:rgba(191, 204, 214, 0.3);
  cursor:pointer; }

table.bp3-html-table.bp3-interactive tbody tr:active td{
  background-color:rgba(191, 204, 214, 0.4); }

.bp3-dark table.bp3-html-table{ }
  .bp3-dark table.bp3-html-table.bp3-html-table-striped tbody tr:nth-child(odd) td{
    background:rgba(92, 112, 128, 0.15); }
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered th:not(:first-child){
    -webkit-box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15); }
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered tbody tr td,
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered tfoot tr td{
    -webkit-box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15); }
    .bp3-dark table.bp3-html-table.bp3-html-table-bordered tbody tr td:not(:first-child),
    .bp3-dark table.bp3-html-table.bp3-html-table-bordered tfoot tr td:not(:first-child){
      -webkit-box-shadow:inset 1px 1px 0 0 rgba(255, 255, 255, 0.15);
              box-shadow:inset 1px 1px 0 0 rgba(255, 255, 255, 0.15); }
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td{
    -webkit-box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15); }
    .bp3-dark table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td:first-child{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-dark table.bp3-html-table.bp3-interactive tbody tr:hover td{
    background-color:rgba(92, 112, 128, 0.3);
    cursor:pointer; }
  .bp3-dark table.bp3-html-table.bp3-interactive tbody tr:active td{
    background-color:rgba(92, 112, 128, 0.4); }

.bp3-key-combo{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center; }
  .bp3-key-combo > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-key-combo > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-key-combo::before,
  .bp3-key-combo > *{
    margin-right:5px; }
  .bp3-key-combo:empty::before,
  .bp3-key-combo > :last-child{
    margin-right:0; }

.bp3-hotkey-dialog{
  padding-bottom:0;
  top:40px; }
  .bp3-hotkey-dialog .bp3-dialog-body{
    margin:0;
    padding:0; }
  .bp3-hotkey-dialog .bp3-hotkey-label{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1; }

.bp3-hotkey-column{
  margin:auto;
  max-height:80vh;
  overflow-y:auto;
  padding:30px; }
  .bp3-hotkey-column .bp3-heading{
    margin-bottom:20px; }
    .bp3-hotkey-column .bp3-heading:not(:first-child){
      margin-top:40px; }

.bp3-hotkey{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:justify;
      -ms-flex-pack:justify;
          justify-content:space-between;
  margin-left:0;
  margin-right:0; }
  .bp3-hotkey:not(:last-child){
    margin-bottom:10px; }
.bp3-icon{
  display:inline-block;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  vertical-align:text-bottom; }
  .bp3-icon:not(:empty)::before{
    content:"" !important;
    content:unset !important; }
  .bp3-icon > svg{
    display:block; }
    .bp3-icon > svg:not([fill]){
      fill:currentColor; }

.bp3-icon.bp3-intent-primary, .bp3-icon-standard.bp3-intent-primary, .bp3-icon-large.bp3-intent-primary{
  color:#106ba3; }
  .bp3-dark .bp3-icon.bp3-intent-primary, .bp3-dark .bp3-icon-standard.bp3-intent-primary, .bp3-dark .bp3-icon-large.bp3-intent-primary{
    color:#48aff0; }

.bp3-icon.bp3-intent-success, .bp3-icon-standard.bp3-intent-success, .bp3-icon-large.bp3-intent-success{
  color:#0d8050; }
  .bp3-dark .bp3-icon.bp3-intent-success, .bp3-dark .bp3-icon-standard.bp3-intent-success, .bp3-dark .bp3-icon-large.bp3-intent-success{
    color:#3dcc91; }

.bp3-icon.bp3-intent-warning, .bp3-icon-standard.bp3-intent-warning, .bp3-icon-large.bp3-intent-warning{
  color:#bf7326; }
  .bp3-dark .bp3-icon.bp3-intent-warning, .bp3-dark .bp3-icon-standard.bp3-intent-warning, .bp3-dark .bp3-icon-large.bp3-intent-warning{
    color:#ffb366; }

.bp3-icon.bp3-intent-danger, .bp3-icon-standard.bp3-intent-danger, .bp3-icon-large.bp3-intent-danger{
  color:#c23030; }
  .bp3-dark .bp3-icon.bp3-intent-danger, .bp3-dark .bp3-icon-standard.bp3-intent-danger, .bp3-dark .bp3-icon-large.bp3-intent-danger{
    color:#ff7373; }

span.bp3-icon-standard{
  font-family:"Icons16", sans-serif;
  font-size:16px;
  font-style:normal;
  font-weight:400;
  line-height:1;
  -moz-osx-font-smoothing:grayscale;
  -webkit-font-smoothing:antialiased;
  display:inline-block; }

span.bp3-icon-large{
  font-family:"Icons20", sans-serif;
  font-size:20px;
  font-style:normal;
  font-weight:400;
  line-height:1;
  -moz-osx-font-smoothing:grayscale;
  -webkit-font-smoothing:antialiased;
  display:inline-block; }

span.bp3-icon:empty{
  font-family:"Icons20";
  font-size:inherit;
  font-style:normal;
  font-weight:400;
  line-height:1; }
  span.bp3-icon:empty::before{
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased; }

.bp3-icon-add::before{
  content:""; }

.bp3-icon-add-column-left::before{
  content:""; }

.bp3-icon-add-column-right::before{
  content:""; }

.bp3-icon-add-row-bottom::before{
  content:""; }

.bp3-icon-add-row-top::before{
  content:""; }

.bp3-icon-add-to-artifact::before{
  content:""; }

.bp3-icon-add-to-folder::before{
  content:""; }

.bp3-icon-airplane::before{
  content:""; }

.bp3-icon-align-center::before{
  content:""; }

.bp3-icon-align-justify::before{
  content:""; }

.bp3-icon-align-left::before{
  content:""; }

.bp3-icon-align-right::before{
  content:""; }

.bp3-icon-alignment-bottom::before{
  content:""; }

.bp3-icon-alignment-horizontal-center::before{
  content:""; }

.bp3-icon-alignment-left::before{
  content:""; }

.bp3-icon-alignment-right::before{
  content:""; }

.bp3-icon-alignment-top::before{
  content:""; }

.bp3-icon-alignment-vertical-center::before{
  content:""; }

.bp3-icon-annotation::before{
  content:""; }

.bp3-icon-application::before{
  content:""; }

.bp3-icon-applications::before{
  content:""; }

.bp3-icon-archive::before{
  content:""; }

.bp3-icon-arrow-bottom-left::before{
  content:"↙"; }

.bp3-icon-arrow-bottom-right::before{
  content:"↘"; }

.bp3-icon-arrow-down::before{
  content:"↓"; }

.bp3-icon-arrow-left::before{
  content:"←"; }

.bp3-icon-arrow-right::before{
  content:"→"; }

.bp3-icon-arrow-top-left::before{
  content:"↖"; }

.bp3-icon-arrow-top-right::before{
  content:"↗"; }

.bp3-icon-arrow-up::before{
  content:"↑"; }

.bp3-icon-arrows-horizontal::before{
  content:"↔"; }

.bp3-icon-arrows-vertical::before{
  content:"↕"; }

.bp3-icon-asterisk::before{
  content:"*"; }

.bp3-icon-automatic-updates::before{
  content:""; }

.bp3-icon-badge::before{
  content:""; }

.bp3-icon-ban-circle::before{
  content:""; }

.bp3-icon-bank-account::before{
  content:""; }

.bp3-icon-barcode::before{
  content:""; }

.bp3-icon-blank::before{
  content:""; }

.bp3-icon-blocked-person::before{
  content:""; }

.bp3-icon-bold::before{
  content:""; }

.bp3-icon-book::before{
  content:""; }

.bp3-icon-bookmark::before{
  content:""; }

.bp3-icon-box::before{
  content:""; }

.bp3-icon-briefcase::before{
  content:""; }

.bp3-icon-bring-data::before{
  content:""; }

.bp3-icon-build::before{
  content:""; }

.bp3-icon-calculator::before{
  content:""; }

.bp3-icon-calendar::before{
  content:""; }

.bp3-icon-camera::before{
  content:""; }

.bp3-icon-caret-down::before{
  content:"⌄"; }

.bp3-icon-caret-left::before{
  content:"〈"; }

.bp3-icon-caret-right::before{
  content:"〉"; }

.bp3-icon-caret-up::before{
  content:"⌃"; }

.bp3-icon-cell-tower::before{
  content:""; }

.bp3-icon-changes::before{
  content:""; }

.bp3-icon-chart::before{
  content:""; }

.bp3-icon-chat::before{
  content:""; }

.bp3-icon-chevron-backward::before{
  content:""; }

.bp3-icon-chevron-down::before{
  content:""; }

.bp3-icon-chevron-forward::before{
  content:""; }

.bp3-icon-chevron-left::before{
  content:""; }

.bp3-icon-chevron-right::before{
  content:""; }

.bp3-icon-chevron-up::before{
  content:""; }

.bp3-icon-circle::before{
  content:""; }

.bp3-icon-circle-arrow-down::before{
  content:""; }

.bp3-icon-circle-arrow-left::before{
  content:""; }

.bp3-icon-circle-arrow-right::before{
  content:""; }

.bp3-icon-circle-arrow-up::before{
  content:""; }

.bp3-icon-citation::before{
  content:""; }

.bp3-icon-clean::before{
  content:""; }

.bp3-icon-clipboard::before{
  content:""; }

.bp3-icon-cloud::before{
  content:"☁"; }

.bp3-icon-cloud-download::before{
  content:""; }

.bp3-icon-cloud-upload::before{
  content:""; }

.bp3-icon-code::before{
  content:""; }

.bp3-icon-code-block::before{
  content:""; }

.bp3-icon-cog::before{
  content:""; }

.bp3-icon-collapse-all::before{
  content:""; }

.bp3-icon-column-layout::before{
  content:""; }

.bp3-icon-comment::before{
  content:""; }

.bp3-icon-comparison::before{
  content:""; }

.bp3-icon-compass::before{
  content:""; }

.bp3-icon-compressed::before{
  content:""; }

.bp3-icon-confirm::before{
  content:""; }

.bp3-icon-console::before{
  content:""; }

.bp3-icon-contrast::before{
  content:""; }

.bp3-icon-control::before{
  content:""; }

.bp3-icon-credit-card::before{
  content:""; }

.bp3-icon-cross::before{
  content:"✗"; }

.bp3-icon-crown::before{
  content:""; }

.bp3-icon-cube::before{
  content:""; }

.bp3-icon-cube-add::before{
  content:""; }

.bp3-icon-cube-remove::before{
  content:""; }

.bp3-icon-curved-range-chart::before{
  content:""; }

.bp3-icon-cut::before{
  content:""; }

.bp3-icon-dashboard::before{
  content:""; }

.bp3-icon-data-lineage::before{
  content:""; }

.bp3-icon-database::before{
  content:""; }

.bp3-icon-delete::before{
  content:""; }

.bp3-icon-delta::before{
  content:"Δ"; }

.bp3-icon-derive-column::before{
  content:""; }

.bp3-icon-desktop::before{
  content:""; }

.bp3-icon-diagnosis::before{
  content:""; }

.bp3-icon-diagram-tree::before{
  content:""; }

.bp3-icon-direction-left::before{
  content:""; }

.bp3-icon-direction-right::before{
  content:""; }

.bp3-icon-disable::before{
  content:""; }

.bp3-icon-document::before{
  content:""; }

.bp3-icon-document-open::before{
  content:""; }

.bp3-icon-document-share::before{
  content:""; }

.bp3-icon-dollar::before{
  content:"$"; }

.bp3-icon-dot::before{
  content:"•"; }

.bp3-icon-double-caret-horizontal::before{
  content:""; }

.bp3-icon-double-caret-vertical::before{
  content:""; }

.bp3-icon-double-chevron-down::before{
  content:""; }

.bp3-icon-double-chevron-left::before{
  content:""; }

.bp3-icon-double-chevron-right::before{
  content:""; }

.bp3-icon-double-chevron-up::before{
  content:""; }

.bp3-icon-doughnut-chart::before{
  content:""; }

.bp3-icon-download::before{
  content:""; }

.bp3-icon-drag-handle-horizontal::before{
  content:""; }

.bp3-icon-drag-handle-vertical::before{
  content:""; }

.bp3-icon-draw::before{
  content:""; }

.bp3-icon-drive-time::before{
  content:""; }

.bp3-icon-duplicate::before{
  content:""; }

.bp3-icon-edit::before{
  content:"✎"; }

.bp3-icon-eject::before{
  content:"⏏"; }

.bp3-icon-endorsed::before{
  content:""; }

.bp3-icon-envelope::before{
  content:"✉"; }

.bp3-icon-equals::before{
  content:""; }

.bp3-icon-eraser::before{
  content:""; }

.bp3-icon-error::before{
  content:""; }

.bp3-icon-euro::before{
  content:"€"; }

.bp3-icon-exchange::before{
  content:""; }

.bp3-icon-exclude-row::before{
  content:""; }

.bp3-icon-expand-all::before{
  content:""; }

.bp3-icon-export::before{
  content:""; }

.bp3-icon-eye-off::before{
  content:""; }

.bp3-icon-eye-on::before{
  content:""; }

.bp3-icon-eye-open::before{
  content:""; }

.bp3-icon-fast-backward::before{
  content:""; }

.bp3-icon-fast-forward::before{
  content:""; }

.bp3-icon-feed::before{
  content:""; }

.bp3-icon-feed-subscribed::before{
  content:""; }

.bp3-icon-film::before{
  content:""; }

.bp3-icon-filter::before{
  content:""; }

.bp3-icon-filter-keep::before{
  content:""; }

.bp3-icon-filter-list::before{
  content:""; }

.bp3-icon-filter-open::before{
  content:""; }

.bp3-icon-filter-remove::before{
  content:""; }

.bp3-icon-flag::before{
  content:"⚑"; }

.bp3-icon-flame::before{
  content:""; }

.bp3-icon-flash::before{
  content:""; }

.bp3-icon-floppy-disk::before{
  content:""; }

.bp3-icon-flow-branch::before{
  content:""; }

.bp3-icon-flow-end::before{
  content:""; }

.bp3-icon-flow-linear::before{
  content:""; }

.bp3-icon-flow-review::before{
  content:""; }

.bp3-icon-flow-review-branch::before{
  content:""; }

.bp3-icon-flows::before{
  content:""; }

.bp3-icon-folder-close::before{
  content:""; }

.bp3-icon-folder-new::before{
  content:""; }

.bp3-icon-folder-open::before{
  content:""; }

.bp3-icon-folder-shared::before{
  content:""; }

.bp3-icon-folder-shared-open::before{
  content:""; }

.bp3-icon-follower::before{
  content:""; }

.bp3-icon-following::before{
  content:""; }

.bp3-icon-font::before{
  content:""; }

.bp3-icon-fork::before{
  content:""; }

.bp3-icon-form::before{
  content:""; }

.bp3-icon-full-circle::before{
  content:""; }

.bp3-icon-full-stacked-chart::before{
  content:""; }

.bp3-icon-fullscreen::before{
  content:""; }

.bp3-icon-function::before{
  content:""; }

.bp3-icon-gantt-chart::before{
  content:""; }

.bp3-icon-geolocation::before{
  content:""; }

.bp3-icon-geosearch::before{
  content:""; }

.bp3-icon-git-branch::before{
  content:""; }

.bp3-icon-git-commit::before{
  content:""; }

.bp3-icon-git-merge::before{
  content:""; }

.bp3-icon-git-new-branch::before{
  content:""; }

.bp3-icon-git-pull::before{
  content:""; }

.bp3-icon-git-push::before{
  content:""; }

.bp3-icon-git-repo::before{
  content:""; }

.bp3-icon-glass::before{
  content:""; }

.bp3-icon-globe::before{
  content:""; }

.bp3-icon-globe-network::before{
  content:""; }

.bp3-icon-graph::before{
  content:""; }

.bp3-icon-graph-remove::before{
  content:""; }

.bp3-icon-greater-than::before{
  content:""; }

.bp3-icon-greater-than-or-equal-to::before{
  content:""; }

.bp3-icon-grid::before{
  content:""; }

.bp3-icon-grid-view::before{
  content:""; }

.bp3-icon-group-objects::before{
  content:""; }

.bp3-icon-grouped-bar-chart::before{
  content:""; }

.bp3-icon-hand::before{
  content:""; }

.bp3-icon-hand-down::before{
  content:""; }

.bp3-icon-hand-left::before{
  content:""; }

.bp3-icon-hand-right::before{
  content:""; }

.bp3-icon-hand-up::before{
  content:""; }

.bp3-icon-header::before{
  content:""; }

.bp3-icon-header-one::before{
  content:""; }

.bp3-icon-header-two::before{
  content:""; }

.bp3-icon-headset::before{
  content:""; }

.bp3-icon-heart::before{
  content:"♥"; }

.bp3-icon-heart-broken::before{
  content:""; }

.bp3-icon-heat-grid::before{
  content:""; }

.bp3-icon-heatmap::before{
  content:""; }

.bp3-icon-help::before{
  content:"?"; }

.bp3-icon-helper-management::before{
  content:""; }

.bp3-icon-highlight::before{
  content:""; }

.bp3-icon-history::before{
  content:""; }

.bp3-icon-home::before{
  content:"⌂"; }

.bp3-icon-horizontal-bar-chart::before{
  content:""; }

.bp3-icon-horizontal-bar-chart-asc::before{
  content:""; }

.bp3-icon-horizontal-bar-chart-desc::before{
  content:""; }

.bp3-icon-horizontal-distribution::before{
  content:""; }

.bp3-icon-id-number::before{
  content:""; }

.bp3-icon-image-rotate-left::before{
  content:""; }

.bp3-icon-image-rotate-right::before{
  content:""; }

.bp3-icon-import::before{
  content:""; }

.bp3-icon-inbox::before{
  content:""; }

.bp3-icon-inbox-filtered::before{
  content:""; }

.bp3-icon-inbox-geo::before{
  content:""; }

.bp3-icon-inbox-search::before{
  content:""; }

.bp3-icon-inbox-update::before{
  content:""; }

.bp3-icon-info-sign::before{
  content:"ℹ"; }

.bp3-icon-inheritance::before{
  content:""; }

.bp3-icon-inner-join::before{
  content:""; }

.bp3-icon-insert::before{
  content:""; }

.bp3-icon-intersection::before{
  content:""; }

.bp3-icon-ip-address::before{
  content:""; }

.bp3-icon-issue::before{
  content:""; }

.bp3-icon-issue-closed::before{
  content:""; }

.bp3-icon-issue-new::before{
  content:""; }

.bp3-icon-italic::before{
  content:""; }

.bp3-icon-join-table::before{
  content:""; }

.bp3-icon-key::before{
  content:""; }

.bp3-icon-key-backspace::before{
  content:""; }

.bp3-icon-key-command::before{
  content:""; }

.bp3-icon-key-control::before{
  content:""; }

.bp3-icon-key-delete::before{
  content:""; }

.bp3-icon-key-enter::before{
  content:""; }

.bp3-icon-key-escape::before{
  content:""; }

.bp3-icon-key-option::before{
  content:""; }

.bp3-icon-key-shift::before{
  content:""; }

.bp3-icon-key-tab::before{
  content:""; }

.bp3-icon-known-vehicle::before{
  content:""; }

.bp3-icon-lab-test::before{
  content:""; }

.bp3-icon-label::before{
  content:""; }

.bp3-icon-layer::before{
  content:""; }

.bp3-icon-layers::before{
  content:""; }

.bp3-icon-layout::before{
  content:""; }

.bp3-icon-layout-auto::before{
  content:""; }

.bp3-icon-layout-balloon::before{
  content:""; }

.bp3-icon-layout-circle::before{
  content:""; }

.bp3-icon-layout-grid::before{
  content:""; }

.bp3-icon-layout-group-by::before{
  content:""; }

.bp3-icon-layout-hierarchy::before{
  content:""; }

.bp3-icon-layout-linear::before{
  content:""; }

.bp3-icon-layout-skew-grid::before{
  content:""; }

.bp3-icon-layout-sorted-clusters::before{
  content:""; }

.bp3-icon-learning::before{
  content:""; }

.bp3-icon-left-join::before{
  content:""; }

.bp3-icon-less-than::before{
  content:""; }

.bp3-icon-less-than-or-equal-to::before{
  content:""; }

.bp3-icon-lifesaver::before{
  content:""; }

.bp3-icon-lightbulb::before{
  content:""; }

.bp3-icon-link::before{
  content:""; }

.bp3-icon-list::before{
  content:"☰"; }

.bp3-icon-list-columns::before{
  content:""; }

.bp3-icon-list-detail-view::before{
  content:""; }

.bp3-icon-locate::before{
  content:""; }

.bp3-icon-lock::before{
  content:""; }

.bp3-icon-log-in::before{
  content:""; }

.bp3-icon-log-out::before{
  content:""; }

.bp3-icon-manual::before{
  content:""; }

.bp3-icon-manually-entered-data::before{
  content:""; }

.bp3-icon-map::before{
  content:""; }

.bp3-icon-map-create::before{
  content:""; }

.bp3-icon-map-marker::before{
  content:""; }

.bp3-icon-maximize::before{
  content:""; }

.bp3-icon-media::before{
  content:""; }

.bp3-icon-menu::before{
  content:""; }

.bp3-icon-menu-closed::before{
  content:""; }

.bp3-icon-menu-open::before{
  content:""; }

.bp3-icon-merge-columns::before{
  content:""; }

.bp3-icon-merge-links::before{
  content:""; }

.bp3-icon-minimize::before{
  content:""; }

.bp3-icon-minus::before{
  content:"−"; }

.bp3-icon-mobile-phone::before{
  content:""; }

.bp3-icon-mobile-video::before{
  content:""; }

.bp3-icon-moon::before{
  content:""; }

.bp3-icon-more::before{
  content:""; }

.bp3-icon-mountain::before{
  content:""; }

.bp3-icon-move::before{
  content:""; }

.bp3-icon-mugshot::before{
  content:""; }

.bp3-icon-multi-select::before{
  content:""; }

.bp3-icon-music::before{
  content:""; }

.bp3-icon-new-drawing::before{
  content:""; }

.bp3-icon-new-grid-item::before{
  content:""; }

.bp3-icon-new-layer::before{
  content:""; }

.bp3-icon-new-layers::before{
  content:""; }

.bp3-icon-new-link::before{
  content:""; }

.bp3-icon-new-object::before{
  content:""; }

.bp3-icon-new-person::before{
  content:""; }

.bp3-icon-new-prescription::before{
  content:""; }

.bp3-icon-new-text-box::before{
  content:""; }

.bp3-icon-ninja::before{
  content:""; }

.bp3-icon-not-equal-to::before{
  content:""; }

.bp3-icon-notifications::before{
  content:""; }

.bp3-icon-notifications-updated::before{
  content:""; }

.bp3-icon-numbered-list::before{
  content:""; }

.bp3-icon-numerical::before{
  content:""; }

.bp3-icon-office::before{
  content:""; }

.bp3-icon-offline::before{
  content:""; }

.bp3-icon-oil-field::before{
  content:""; }

.bp3-icon-one-column::before{
  content:""; }

.bp3-icon-outdated::before{
  content:""; }

.bp3-icon-page-layout::before{
  content:""; }

.bp3-icon-panel-stats::before{
  content:""; }

.bp3-icon-panel-table::before{
  content:""; }

.bp3-icon-paperclip::before{
  content:""; }

.bp3-icon-paragraph::before{
  content:""; }

.bp3-icon-path::before{
  content:""; }

.bp3-icon-path-search::before{
  content:""; }

.bp3-icon-pause::before{
  content:""; }

.bp3-icon-people::before{
  content:""; }

.bp3-icon-percentage::before{
  content:""; }

.bp3-icon-person::before{
  content:""; }

.bp3-icon-phone::before{
  content:"☎"; }

.bp3-icon-pie-chart::before{
  content:""; }

.bp3-icon-pin::before{
  content:""; }

.bp3-icon-pivot::before{
  content:""; }

.bp3-icon-pivot-table::before{
  content:""; }

.bp3-icon-play::before{
  content:""; }

.bp3-icon-plus::before{
  content:"+"; }

.bp3-icon-polygon-filter::before{
  content:""; }

.bp3-icon-power::before{
  content:""; }

.bp3-icon-predictive-analysis::before{
  content:""; }

.bp3-icon-prescription::before{
  content:""; }

.bp3-icon-presentation::before{
  content:""; }

.bp3-icon-print::before{
  content:"⎙"; }

.bp3-icon-projects::before{
  content:""; }

.bp3-icon-properties::before{
  content:""; }

.bp3-icon-property::before{
  content:""; }

.bp3-icon-publish-function::before{
  content:""; }

.bp3-icon-pulse::before{
  content:""; }

.bp3-icon-random::before{
  content:""; }

.bp3-icon-record::before{
  content:""; }

.bp3-icon-redo::before{
  content:""; }

.bp3-icon-refresh::before{
  content:""; }

.bp3-icon-regression-chart::before{
  content:""; }

.bp3-icon-remove::before{
  content:""; }

.bp3-icon-remove-column::before{
  content:""; }

.bp3-icon-remove-column-left::before{
  content:""; }

.bp3-icon-remove-column-right::before{
  content:""; }

.bp3-icon-remove-row-bottom::before{
  content:""; }

.bp3-icon-remove-row-top::before{
  content:""; }

.bp3-icon-repeat::before{
  content:""; }

.bp3-icon-reset::before{
  content:""; }

.bp3-icon-resolve::before{
  content:""; }

.bp3-icon-rig::before{
  content:""; }

.bp3-icon-right-join::before{
  content:""; }

.bp3-icon-ring::before{
  content:""; }

.bp3-icon-rotate-document::before{
  content:""; }

.bp3-icon-rotate-page::before{
  content:""; }

.bp3-icon-satellite::before{
  content:""; }

.bp3-icon-saved::before{
  content:""; }

.bp3-icon-scatter-plot::before{
  content:""; }

.bp3-icon-search::before{
  content:""; }

.bp3-icon-search-around::before{
  content:""; }

.bp3-icon-search-template::before{
  content:""; }

.bp3-icon-search-text::before{
  content:""; }

.bp3-icon-segmented-control::before{
  content:""; }

.bp3-icon-select::before{
  content:""; }

.bp3-icon-selection::before{
  content:"⦿"; }

.bp3-icon-send-to::before{
  content:""; }

.bp3-icon-send-to-graph::before{
  content:""; }

.bp3-icon-send-to-map::before{
  content:""; }

.bp3-icon-series-add::before{
  content:""; }

.bp3-icon-series-configuration::before{
  content:""; }

.bp3-icon-series-derived::before{
  content:""; }

.bp3-icon-series-filtered::before{
  content:""; }

.bp3-icon-series-search::before{
  content:""; }

.bp3-icon-settings::before{
  content:""; }

.bp3-icon-share::before{
  content:""; }

.bp3-icon-shield::before{
  content:""; }

.bp3-icon-shop::before{
  content:""; }

.bp3-icon-shopping-cart::before{
  content:""; }

.bp3-icon-signal-search::before{
  content:""; }

.bp3-icon-sim-card::before{
  content:""; }

.bp3-icon-slash::before{
  content:""; }

.bp3-icon-small-cross::before{
  content:""; }

.bp3-icon-small-minus::before{
  content:""; }

.bp3-icon-small-plus::before{
  content:""; }

.bp3-icon-small-tick::before{
  content:""; }

.bp3-icon-snowflake::before{
  content:""; }

.bp3-icon-social-media::before{
  content:""; }

.bp3-icon-sort::before{
  content:""; }

.bp3-icon-sort-alphabetical::before{
  content:""; }

.bp3-icon-sort-alphabetical-desc::before{
  content:""; }

.bp3-icon-sort-asc::before{
  content:""; }

.bp3-icon-sort-desc::before{
  content:""; }

.bp3-icon-sort-numerical::before{
  content:""; }

.bp3-icon-sort-numerical-desc::before{
  content:""; }

.bp3-icon-split-columns::before{
  content:""; }

.bp3-icon-square::before{
  content:""; }

.bp3-icon-stacked-chart::before{
  content:""; }

.bp3-icon-star::before{
  content:"★"; }

.bp3-icon-star-empty::before{
  content:"☆"; }

.bp3-icon-step-backward::before{
  content:""; }

.bp3-icon-step-chart::before{
  content:""; }

.bp3-icon-step-forward::before{
  content:""; }

.bp3-icon-stop::before{
  content:""; }

.bp3-icon-stopwatch::before{
  content:""; }

.bp3-icon-strikethrough::before{
  content:""; }

.bp3-icon-style::before{
  content:""; }

.bp3-icon-swap-horizontal::before{
  content:""; }

.bp3-icon-swap-vertical::before{
  content:""; }

.bp3-icon-symbol-circle::before{
  content:""; }

.bp3-icon-symbol-cross::before{
  content:""; }

.bp3-icon-symbol-diamond::before{
  content:""; }

.bp3-icon-symbol-square::before{
  content:""; }

.bp3-icon-symbol-triangle-down::before{
  content:""; }

.bp3-icon-symbol-triangle-up::before{
  content:""; }

.bp3-icon-tag::before{
  content:""; }

.bp3-icon-take-action::before{
  content:""; }

.bp3-icon-taxi::before{
  content:""; }

.bp3-icon-text-highlight::before{
  content:""; }

.bp3-icon-th::before{
  content:""; }

.bp3-icon-th-derived::before{
  content:""; }

.bp3-icon-th-disconnect::before{
  content:""; }

.bp3-icon-th-filtered::before{
  content:""; }

.bp3-icon-th-list::before{
  content:""; }

.bp3-icon-thumbs-down::before{
  content:""; }

.bp3-icon-thumbs-up::before{
  content:""; }

.bp3-icon-tick::before{
  content:"✓"; }

.bp3-icon-tick-circle::before{
  content:""; }

.bp3-icon-time::before{
  content:"⏲"; }

.bp3-icon-timeline-area-chart::before{
  content:""; }

.bp3-icon-timeline-bar-chart::before{
  content:""; }

.bp3-icon-timeline-events::before{
  content:""; }

.bp3-icon-timeline-line-chart::before{
  content:""; }

.bp3-icon-tint::before{
  content:""; }

.bp3-icon-torch::before{
  content:""; }

.bp3-icon-tractor::before{
  content:""; }

.bp3-icon-train::before{
  content:""; }

.bp3-icon-translate::before{
  content:""; }

.bp3-icon-trash::before{
  content:""; }

.bp3-icon-tree::before{
  content:""; }

.bp3-icon-trending-down::before{
  content:""; }

.bp3-icon-trending-up::before{
  content:""; }

.bp3-icon-truck::before{
  content:""; }

.bp3-icon-two-columns::before{
  content:""; }

.bp3-icon-unarchive::before{
  content:""; }

.bp3-icon-underline::before{
  content:"⎁"; }

.bp3-icon-undo::before{
  content:"⎌"; }

.bp3-icon-ungroup-objects::before{
  content:""; }

.bp3-icon-unknown-vehicle::before{
  content:""; }

.bp3-icon-unlock::before{
  content:""; }

.bp3-icon-unpin::before{
  content:""; }

.bp3-icon-unresolve::before{
  content:""; }

.bp3-icon-updated::before{
  content:""; }

.bp3-icon-upload::before{
  content:""; }

.bp3-icon-user::before{
  content:""; }

.bp3-icon-variable::before{
  content:""; }

.bp3-icon-vertical-bar-chart-asc::before{
  content:""; }

.bp3-icon-vertical-bar-chart-desc::before{
  content:""; }

.bp3-icon-vertical-distribution::before{
  content:""; }

.bp3-icon-video::before{
  content:""; }

.bp3-icon-volume-down::before{
  content:""; }

.bp3-icon-volume-off::before{
  content:""; }

.bp3-icon-volume-up::before{
  content:""; }

.bp3-icon-walk::before{
  content:""; }

.bp3-icon-warning-sign::before{
  content:""; }

.bp3-icon-waterfall-chart::before{
  content:""; }

.bp3-icon-widget::before{
  content:""; }

.bp3-icon-widget-button::before{
  content:""; }

.bp3-icon-widget-footer::before{
  content:""; }

.bp3-icon-widget-header::before{
  content:""; }

.bp3-icon-wrench::before{
  content:""; }

.bp3-icon-zoom-in::before{
  content:""; }

.bp3-icon-zoom-out::before{
  content:""; }

.bp3-icon-zoom-to-fit::before{
  content:""; }
.bp3-submenu > .bp3-popover-wrapper{
  display:block; }

.bp3-submenu .bp3-popover-target{
  display:block; }
  .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{ }

.bp3-submenu.bp3-popover{
  -webkit-box-shadow:none;
          box-shadow:none;
  padding:0 5px; }
  .bp3-submenu.bp3-popover > .bp3-popover-content{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-submenu.bp3-popover, .bp3-submenu.bp3-popover.bp3-dark{
    -webkit-box-shadow:none;
            box-shadow:none; }
    .bp3-dark .bp3-submenu.bp3-popover > .bp3-popover-content, .bp3-submenu.bp3-popover.bp3-dark > .bp3-popover-content{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
.bp3-menu{
  background:#ffffff;
  border-radius:3px;
  color:#182026;
  list-style:none;
  margin:0;
  min-width:180px;
  padding:5px;
  text-align:left; }

.bp3-menu-divider{
  border-top:1px solid rgba(16, 22, 26, 0.15);
  display:block;
  margin:5px; }
  .bp3-dark .bp3-menu-divider{
    border-top-color:rgba(255, 255, 255, 0.15); }

.bp3-menu-item{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:start;
      -ms-flex-align:start;
          align-items:flex-start;
  border-radius:2px;
  color:inherit;
  line-height:20px;
  padding:5px 7px;
  text-decoration:none;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-menu-item > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-menu-item > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-menu-item::before,
  .bp3-menu-item > *{
    margin-right:7px; }
  .bp3-menu-item:empty::before,
  .bp3-menu-item > :last-child{
    margin-right:0; }
  .bp3-menu-item > .bp3-fill{
    word-break:break-word; }
  .bp3-menu-item:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
    background-color:rgba(167, 182, 194, 0.3);
    cursor:pointer;
    text-decoration:none; }
  .bp3-menu-item.bp3-disabled{
    background-color:inherit;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }
  .bp3-dark .bp3-menu-item{
    color:inherit; }
    .bp3-dark .bp3-menu-item:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
      background-color:rgba(138, 155, 168, 0.15);
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-disabled{
      background-color:inherit;
      color:rgba(167, 182, 194, 0.6); }
  .bp3-menu-item.bp3-intent-primary{
    color:#106ba3; }
    .bp3-menu-item.bp3-intent-primary .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-primary::before, .bp3-menu-item.bp3-intent-primary::after,
    .bp3-menu-item.bp3-intent-primary .bp3-menu-item-label{
      color:#106ba3; }
    .bp3-menu-item.bp3-intent-primary:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-menu-item.bp3-intent-primary.bp3-active{
      background-color:#137cbd; }
    .bp3-menu-item.bp3-intent-primary:active{
      background-color:#106ba3; }
    .bp3-menu-item.bp3-intent-primary:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-menu-item.bp3-intent-primary:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-menu-item.bp3-intent-primary:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-primary:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-primary:active, .bp3-menu-item.bp3-intent-primary:active::before, .bp3-menu-item.bp3-intent-primary:active::after,
    .bp3-menu-item.bp3-intent-primary:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-primary.bp3-active, .bp3-menu-item.bp3-intent-primary.bp3-active::before, .bp3-menu-item.bp3-intent-primary.bp3-active::after,
    .bp3-menu-item.bp3-intent-primary.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item.bp3-intent-success{
    color:#0d8050; }
    .bp3-menu-item.bp3-intent-success .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-success::before, .bp3-menu-item.bp3-intent-success::after,
    .bp3-menu-item.bp3-intent-success .bp3-menu-item-label{
      color:#0d8050; }
    .bp3-menu-item.bp3-intent-success:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-menu-item.bp3-intent-success.bp3-active{
      background-color:#0f9960; }
    .bp3-menu-item.bp3-intent-success:active{
      background-color:#0d8050; }
    .bp3-menu-item.bp3-intent-success:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-menu-item.bp3-intent-success:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-menu-item.bp3-intent-success:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-success:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-success:active, .bp3-menu-item.bp3-intent-success:active::before, .bp3-menu-item.bp3-intent-success:active::after,
    .bp3-menu-item.bp3-intent-success:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-success.bp3-active, .bp3-menu-item.bp3-intent-success.bp3-active::before, .bp3-menu-item.bp3-intent-success.bp3-active::after,
    .bp3-menu-item.bp3-intent-success.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item.bp3-intent-warning{
    color:#bf7326; }
    .bp3-menu-item.bp3-intent-warning .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-warning::before, .bp3-menu-item.bp3-intent-warning::after,
    .bp3-menu-item.bp3-intent-warning .bp3-menu-item-label{
      color:#bf7326; }
    .bp3-menu-item.bp3-intent-warning:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-menu-item.bp3-intent-warning.bp3-active{
      background-color:#d9822b; }
    .bp3-menu-item.bp3-intent-warning:active{
      background-color:#bf7326; }
    .bp3-menu-item.bp3-intent-warning:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-menu-item.bp3-intent-warning:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-menu-item.bp3-intent-warning:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-warning:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-warning:active, .bp3-menu-item.bp3-intent-warning:active::before, .bp3-menu-item.bp3-intent-warning:active::after,
    .bp3-menu-item.bp3-intent-warning:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-warning.bp3-active, .bp3-menu-item.bp3-intent-warning.bp3-active::before, .bp3-menu-item.bp3-intent-warning.bp3-active::after,
    .bp3-menu-item.bp3-intent-warning.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item.bp3-intent-danger{
    color:#c23030; }
    .bp3-menu-item.bp3-intent-danger .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-danger::before, .bp3-menu-item.bp3-intent-danger::after,
    .bp3-menu-item.bp3-intent-danger .bp3-menu-item-label{
      color:#c23030; }
    .bp3-menu-item.bp3-intent-danger:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-menu-item.bp3-intent-danger.bp3-active{
      background-color:#db3737; }
    .bp3-menu-item.bp3-intent-danger:active{
      background-color:#c23030; }
    .bp3-menu-item.bp3-intent-danger:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-menu-item.bp3-intent-danger:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-menu-item.bp3-intent-danger:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-danger:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-danger:active, .bp3-menu-item.bp3-intent-danger:active::before, .bp3-menu-item.bp3-intent-danger:active::after,
    .bp3-menu-item.bp3-intent-danger:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-danger.bp3-active, .bp3-menu-item.bp3-intent-danger.bp3-active::before, .bp3-menu-item.bp3-intent-danger.bp3-active::after,
    .bp3-menu-item.bp3-intent-danger.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item::before{
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-style:normal;
    font-weight:400;
    line-height:1;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    margin-right:7px; }
  .bp3-menu-item::before,
  .bp3-menu-item > .bp3-icon{
    color:#5c7080;
    margin-top:2px; }
  .bp3-menu-item .bp3-menu-item-label{
    color:#5c7080; }
  .bp3-menu-item:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
    color:inherit; }
  .bp3-menu-item.bp3-active, .bp3-menu-item:active{
    background-color:rgba(115, 134, 148, 0.3); }
  .bp3-menu-item.bp3-disabled{
    background-color:inherit !important;
    color:rgba(92, 112, 128, 0.6) !important;
    cursor:not-allowed !important;
    outline:none !important; }
    .bp3-menu-item.bp3-disabled::before,
    .bp3-menu-item.bp3-disabled > .bp3-icon,
    .bp3-menu-item.bp3-disabled .bp3-menu-item-label{
      color:rgba(92, 112, 128, 0.6) !important; }
  .bp3-large .bp3-menu-item{
    font-size:16px;
    line-height:22px;
    padding:9px 7px; }
    .bp3-large .bp3-menu-item .bp3-icon{
      margin-top:3px; }
    .bp3-large .bp3-menu-item::before{
      font-family:"Icons20", sans-serif;
      font-size:20px;
      font-style:normal;
      font-weight:400;
      line-height:1;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased;
      margin-right:10px;
      margin-top:1px; }

button.bp3-menu-item{
  background:none;
  border:none;
  text-align:left;
  width:100%; }
.bp3-menu-header{
  border-top:1px solid rgba(16, 22, 26, 0.15);
  display:block;
  margin:5px;
  cursor:default;
  padding-left:2px; }
  .bp3-dark .bp3-menu-header{
    border-top-color:rgba(255, 255, 255, 0.15); }
  .bp3-menu-header:first-of-type{
    border-top:none; }
  .bp3-menu-header > h6{
    color:#182026;
    font-weight:600;
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    line-height:17px;
    margin:0;
    padding:10px 7px 0 1px; }
    .bp3-dark .bp3-menu-header > h6{
      color:#f5f8fa; }
  .bp3-menu-header:first-of-type > h6{
    padding-top:0; }
  .bp3-large .bp3-menu-header > h6{
    font-size:18px;
    padding-bottom:5px;
    padding-top:15px; }
  .bp3-large .bp3-menu-header:first-of-type > h6{
    padding-top:0; }

.bp3-dark .bp3-menu{
  background:#30404d;
  color:#f5f8fa; }

.bp3-dark .bp3-menu-item{ }
  .bp3-dark .bp3-menu-item.bp3-intent-primary{
    color:#48aff0; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary .bp3-icon{
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary::before, .bp3-dark .bp3-menu-item.bp3-intent-primary::after,
    .bp3-dark .bp3-menu-item.bp3-intent-primary .bp3-menu-item-label{
      color:#48aff0; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active{
      background-color:#137cbd; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary:active{
      background-color:#106ba3; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-primary:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-primary:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after,
    .bp3-dark .bp3-menu-item.bp3-intent-primary:hover .bp3-menu-item-label,
    .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label,
    .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-primary:active, .bp3-dark .bp3-menu-item.bp3-intent-primary:active::before, .bp3-dark .bp3-menu-item.bp3-intent-primary:active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-primary:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-dark .bp3-menu-item.bp3-intent-success{
    color:#3dcc91; }
    .bp3-dark .bp3-menu-item.bp3-intent-success .bp3-icon{
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-intent-success::before, .bp3-dark .bp3-menu-item.bp3-intent-success::after,
    .bp3-dark .bp3-menu-item.bp3-intent-success .bp3-menu-item-label{
      color:#3dcc91; }
    .bp3-dark .bp3-menu-item.bp3-intent-success:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active{
      background-color:#0f9960; }
    .bp3-dark .bp3-menu-item.bp3-intent-success:active{
      background-color:#0d8050; }
    .bp3-dark .bp3-menu-item.bp3-intent-success:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-success:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-success:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after,
    .bp3-dark .bp3-menu-item.bp3-intent-success:hover .bp3-menu-item-label,
    .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label,
    .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-success:active, .bp3-dark .bp3-menu-item.bp3-intent-success:active::before, .bp3-dark .bp3-menu-item.bp3-intent-success:active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-success:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-dark .bp3-menu-item.bp3-intent-warning{
    color:#ffb366; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning .bp3-icon{
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning::before, .bp3-dark .bp3-menu-item.bp3-intent-warning::after,
    .bp3-dark .bp3-menu-item.bp3-intent-warning .bp3-menu-item-label{
      color:#ffb366; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active{
      background-color:#d9822b; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning:active{
      background-color:#bf7326; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-warning:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-warning:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after,
    .bp3-dark .bp3-menu-item.bp3-intent-warning:hover .bp3-menu-item-label,
    .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label,
    .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-warning:active, .bp3-dark .bp3-menu-item.bp3-intent-warning:active::before, .bp3-dark .bp3-menu-item.bp3-intent-warning:active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-warning:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-dark .bp3-menu-item.bp3-intent-danger{
    color:#ff7373; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger .bp3-icon{
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger::before, .bp3-dark .bp3-menu-item.bp3-intent-danger::after,
    .bp3-dark .bp3-menu-item.bp3-intent-danger .bp3-menu-item-label{
      color:#ff7373; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active{
      background-color:#db3737; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger:active{
      background-color:#c23030; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-danger:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-danger:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after,
    .bp3-dark .bp3-menu-item.bp3-intent-danger:hover .bp3-menu-item-label,
    .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label,
    .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-danger:active, .bp3-dark .bp3-menu-item.bp3-intent-danger:active::before, .bp3-dark .bp3-menu-item.bp3-intent-danger:active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-danger:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-dark .bp3-menu-item::before,
  .bp3-dark .bp3-menu-item > .bp3-icon{
    color:#a7b6c2; }
  .bp3-dark .bp3-menu-item .bp3-menu-item-label{
    color:#a7b6c2; }
  .bp3-dark .bp3-menu-item.bp3-active, .bp3-dark .bp3-menu-item:active{
    background-color:rgba(138, 155, 168, 0.3); }
  .bp3-dark .bp3-menu-item.bp3-disabled{
    color:rgba(167, 182, 194, 0.6) !important; }
    .bp3-dark .bp3-menu-item.bp3-disabled::before,
    .bp3-dark .bp3-menu-item.bp3-disabled > .bp3-icon,
    .bp3-dark .bp3-menu-item.bp3-disabled .bp3-menu-item-label{
      color:rgba(167, 182, 194, 0.6) !important; }

.bp3-dark .bp3-menu-divider,
.bp3-dark .bp3-menu-header{
  border-color:rgba(255, 255, 255, 0.15); }

.bp3-dark .bp3-menu-header > h6{
  color:#f5f8fa; }

.bp3-label .bp3-menu{
  margin-top:5px; }
.bp3-navbar{
  background-color:#ffffff;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
  height:50px;
  padding:0 15px;
  position:relative;
  width:100%;
  z-index:10; }
  .bp3-navbar.bp3-dark,
  .bp3-dark .bp3-navbar{
    background-color:#394b59; }
  .bp3-navbar.bp3-dark{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-navbar{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-navbar.bp3-fixed-top{
    left:0;
    position:fixed;
    right:0;
    top:0; }

.bp3-navbar-heading{
  font-size:16px;
  margin-right:15px; }

.bp3-navbar-group{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  height:50px; }
  .bp3-navbar-group.bp3-align-left{
    float:left; }
  .bp3-navbar-group.bp3-align-right{
    float:right; }

.bp3-navbar-divider{
  border-left:1px solid rgba(16, 22, 26, 0.15);
  height:20px;
  margin:0 10px; }
  .bp3-dark .bp3-navbar-divider{
    border-left-color:rgba(255, 255, 255, 0.15); }
.bp3-non-ideal-state{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  height:100%;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  text-align:center;
  width:100%; }
  .bp3-non-ideal-state > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-non-ideal-state > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-non-ideal-state::before,
  .bp3-non-ideal-state > *{
    margin-bottom:20px; }
  .bp3-non-ideal-state:empty::before,
  .bp3-non-ideal-state > :last-child{
    margin-bottom:0; }
  .bp3-non-ideal-state > *{
    max-width:400px; }

.bp3-non-ideal-state-visual{
  color:rgba(92, 112, 128, 0.6);
  font-size:60px; }
  .bp3-dark .bp3-non-ideal-state-visual{
    color:rgba(167, 182, 194, 0.6); }

.bp3-overflow-list{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-wrap:nowrap;
      flex-wrap:nowrap;
  min-width:0; }

.bp3-overflow-list-spacer{
  -ms-flex-negative:1;
      flex-shrink:1;
  width:1px; }

body.bp3-overlay-open{
  overflow:hidden; }

.bp3-overlay{
  bottom:0;
  left:0;
  position:static;
  right:0;
  top:0;
  z-index:20; }
  .bp3-overlay:not(.bp3-overlay-open){
    pointer-events:none; }
  .bp3-overlay.bp3-overlay-container{
    overflow:hidden;
    position:fixed; }
    .bp3-overlay.bp3-overlay-container.bp3-overlay-inline{
      position:absolute; }
  .bp3-overlay.bp3-overlay-scroll-container{
    overflow:auto;
    position:fixed; }
    .bp3-overlay.bp3-overlay-scroll-container.bp3-overlay-inline{
      position:absolute; }
  .bp3-overlay.bp3-overlay-inline{
    display:inline;
    overflow:visible; }

.bp3-overlay-content{
  position:fixed;
  z-index:20; }
  .bp3-overlay-inline .bp3-overlay-content,
  .bp3-overlay-scroll-container .bp3-overlay-content{
    position:absolute; }

.bp3-overlay-backdrop{
  bottom:0;
  left:0;
  position:fixed;
  right:0;
  top:0;
  opacity:1;
  background-color:rgba(16, 22, 26, 0.7);
  overflow:auto;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none;
  z-index:20; }
  .bp3-overlay-backdrop.bp3-overlay-enter, .bp3-overlay-backdrop.bp3-overlay-appear{
    opacity:0; }
  .bp3-overlay-backdrop.bp3-overlay-enter-active, .bp3-overlay-backdrop.bp3-overlay-appear-active{
    opacity:1;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-overlay-backdrop.bp3-overlay-exit{
    opacity:1; }
  .bp3-overlay-backdrop.bp3-overlay-exit-active{
    opacity:0;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-overlay-backdrop:focus{
    outline:none; }
  .bp3-overlay-inline .bp3-overlay-backdrop{
    position:absolute; }
.bp3-panel-stack{
  overflow:hidden;
  position:relative; }

.bp3-panel-stack-header{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-shadow:0 1px rgba(16, 22, 26, 0.15);
          box-shadow:0 1px rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-negative:0;
      flex-shrink:0;
  height:30px;
  z-index:1; }
  .bp3-dark .bp3-panel-stack-header{
    -webkit-box-shadow:0 1px rgba(255, 255, 255, 0.15);
            box-shadow:0 1px rgba(255, 255, 255, 0.15); }
  .bp3-panel-stack-header > span{
    -webkit-box-align:stretch;
        -ms-flex-align:stretch;
            align-items:stretch;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:1;
        -ms-flex:1;
            flex:1; }
  .bp3-panel-stack-header .bp3-heading{
    margin:0 5px; }

.bp3-button.bp3-panel-stack-header-back{
  margin-left:5px;
  padding-left:0;
  white-space:nowrap; }
  .bp3-button.bp3-panel-stack-header-back .bp3-icon{
    margin:0 2px; }

.bp3-panel-stack-view{
  bottom:0;
  left:0;
  position:absolute;
  right:0;
  top:0;
  background-color:#ffffff;
  border-right:1px solid rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin-right:-1px;
  overflow-y:auto;
  z-index:1; }
  .bp3-dark .bp3-panel-stack-view{
    background-color:#30404d; }
  .bp3-panel-stack-view:nth-last-child(n + 4){
    display:none; }

.bp3-panel-stack-push .bp3-panel-stack-enter, .bp3-panel-stack-push .bp3-panel-stack-appear{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0; }

.bp3-panel-stack-push .bp3-panel-stack-enter-active, .bp3-panel-stack-push .bp3-panel-stack-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack-push .bp3-panel-stack-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack-push .bp3-panel-stack-exit-active{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack-pop .bp3-panel-stack-enter, .bp3-panel-stack-pop .bp3-panel-stack-appear{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0; }

.bp3-panel-stack-pop .bp3-panel-stack-enter-active, .bp3-panel-stack-pop .bp3-panel-stack-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack-pop .bp3-panel-stack-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack-pop .bp3-panel-stack-exit-active{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }
.bp3-panel-stack2{
  overflow:hidden;
  position:relative; }

.bp3-panel-stack2-header{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-shadow:0 1px rgba(16, 22, 26, 0.15);
          box-shadow:0 1px rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-negative:0;
      flex-shrink:0;
  height:30px;
  z-index:1; }
  .bp3-dark .bp3-panel-stack2-header{
    -webkit-box-shadow:0 1px rgba(255, 255, 255, 0.15);
            box-shadow:0 1px rgba(255, 255, 255, 0.15); }
  .bp3-panel-stack2-header > span{
    -webkit-box-align:stretch;
        -ms-flex-align:stretch;
            align-items:stretch;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:1;
        -ms-flex:1;
            flex:1; }
  .bp3-panel-stack2-header .bp3-heading{
    margin:0 5px; }

.bp3-button.bp3-panel-stack2-header-back{
  margin-left:5px;
  padding-left:0;
  white-space:nowrap; }
  .bp3-button.bp3-panel-stack2-header-back .bp3-icon{
    margin:0 2px; }

.bp3-panel-stack2-view{
  bottom:0;
  left:0;
  position:absolute;
  right:0;
  top:0;
  background-color:#ffffff;
  border-right:1px solid rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin-right:-1px;
  overflow-y:auto;
  z-index:1; }
  .bp3-dark .bp3-panel-stack2-view{
    background-color:#30404d; }
  .bp3-panel-stack2-view:nth-last-child(n + 4){
    display:none; }

.bp3-panel-stack2-push .bp3-panel-stack2-enter, .bp3-panel-stack2-push .bp3-panel-stack2-appear{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0; }

.bp3-panel-stack2-push .bp3-panel-stack2-enter-active, .bp3-panel-stack2-push .bp3-panel-stack2-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack2-push .bp3-panel-stack2-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack2-push .bp3-panel-stack2-exit-active{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack2-pop .bp3-panel-stack2-enter, .bp3-panel-stack2-pop .bp3-panel-stack2-appear{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0; }

.bp3-panel-stack2-pop .bp3-panel-stack2-enter-active, .bp3-panel-stack2-pop .bp3-panel-stack2-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack2-pop .bp3-panel-stack2-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack2-pop .bp3-panel-stack2-exit-active{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }
.bp3-popover{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  -webkit-transform:scale(1);
          transform:scale(1);
  border-radius:3px;
  display:inline-block;
  z-index:20; }
  .bp3-popover .bp3-popover-arrow{
    height:30px;
    position:absolute;
    width:30px; }
    .bp3-popover .bp3-popover-arrow::before{
      height:20px;
      margin:5px;
      width:20px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover{
    margin-bottom:17px;
    margin-top:-17px; }
    .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow{
      bottom:-11px; }
      .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(-90deg);
                transform:rotate(-90deg); }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover{
    margin-left:17px; }
    .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow{
      left:-11px; }
      .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(0);
                transform:rotate(0); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover{
    margin-top:17px; }
    .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow{
      top:-11px; }
      .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(90deg);
                transform:rotate(90deg); }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover{
    margin-left:-17px;
    margin-right:17px; }
    .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow{
      right:-11px; }
      .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(180deg);
                transform:rotate(180deg); }
  .bp3-tether-element-attached-middle > .bp3-popover > .bp3-popover-arrow{
    top:50%;
    -webkit-transform:translateY(-50%);
            transform:translateY(-50%); }
  .bp3-tether-element-attached-center > .bp3-popover > .bp3-popover-arrow{
    right:50%;
    -webkit-transform:translateX(50%);
            transform:translateX(50%); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow{
    top:-0.3934px; }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow{
    right:-0.3934px; }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow{
    left:-0.3934px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow{
    bottom:-0.3934px; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-left > .bp3-popover{
    -webkit-transform-origin:top left;
            transform-origin:top left; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-center > .bp3-popover{
    -webkit-transform-origin:top center;
            transform-origin:top center; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-right > .bp3-popover{
    -webkit-transform-origin:top right;
            transform-origin:top right; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-left > .bp3-popover{
    -webkit-transform-origin:center left;
            transform-origin:center left; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-center > .bp3-popover{
    -webkit-transform-origin:center center;
            transform-origin:center center; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-right > .bp3-popover{
    -webkit-transform-origin:center right;
            transform-origin:center right; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-left > .bp3-popover{
    -webkit-transform-origin:bottom left;
            transform-origin:bottom left; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-center > .bp3-popover{
    -webkit-transform-origin:bottom center;
            transform-origin:bottom center; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-right > .bp3-popover{
    -webkit-transform-origin:bottom right;
            transform-origin:bottom right; }
  .bp3-popover .bp3-popover-content{
    background:#ffffff;
    color:inherit; }
  .bp3-popover .bp3-popover-arrow::before{
    -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2);
            box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2); }
  .bp3-popover .bp3-popover-arrow-border{
    fill:#10161a;
    fill-opacity:0.1; }
  .bp3-popover .bp3-popover-arrow-fill{
    fill:#ffffff; }
  .bp3-popover-enter > .bp3-popover, .bp3-popover-appear > .bp3-popover{
    -webkit-transform:scale(0.3);
            transform:scale(0.3); }
  .bp3-popover-enter-active > .bp3-popover, .bp3-popover-appear-active > .bp3-popover{
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-popover-exit > .bp3-popover{
    -webkit-transform:scale(1);
            transform:scale(1); }
  .bp3-popover-exit-active > .bp3-popover{
    -webkit-transform:scale(0.3);
            transform:scale(0.3);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-popover .bp3-popover-content{
    border-radius:3px;
    position:relative; }
  .bp3-popover.bp3-popover-content-sizing .bp3-popover-content{
    max-width:350px;
    padding:20px; }
  .bp3-popover-target + .bp3-overlay .bp3-popover.bp3-popover-content-sizing{
    width:350px; }
  .bp3-popover.bp3-minimal{
    margin:0 !important; }
    .bp3-popover.bp3-minimal .bp3-popover-arrow{
      display:none; }
    .bp3-popover.bp3-minimal.bp3-popover{
      -webkit-transform:scale(1);
              transform:scale(1); }
      .bp3-popover-enter > .bp3-popover.bp3-minimal.bp3-popover, .bp3-popover-appear > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1); }
      .bp3-popover-enter-active > .bp3-popover.bp3-minimal.bp3-popover, .bp3-popover-appear-active > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
      .bp3-popover-exit > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1); }
      .bp3-popover-exit-active > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-popover.bp3-dark,
  .bp3-dark .bp3-popover{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
    .bp3-popover.bp3-dark .bp3-popover-content,
    .bp3-dark .bp3-popover .bp3-popover-content{
      background:#30404d;
      color:inherit; }
    .bp3-popover.bp3-dark .bp3-popover-arrow::before,
    .bp3-dark .bp3-popover .bp3-popover-arrow::before{
      -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4);
              box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4); }
    .bp3-popover.bp3-dark .bp3-popover-arrow-border,
    .bp3-dark .bp3-popover .bp3-popover-arrow-border{
      fill:#10161a;
      fill-opacity:0.2; }
    .bp3-popover.bp3-dark .bp3-popover-arrow-fill,
    .bp3-dark .bp3-popover .bp3-popover-arrow-fill{
      fill:#30404d; }

.bp3-popover-arrow::before{
  border-radius:2px;
  content:"";
  display:block;
  position:absolute;
  -webkit-transform:rotate(45deg);
          transform:rotate(45deg); }

.bp3-tether-pinned .bp3-popover-arrow{
  display:none; }

.bp3-popover-backdrop{
  background:rgba(255, 255, 255, 0); }

.bp3-transition-container{
  opacity:1;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  z-index:20; }
  .bp3-transition-container.bp3-popover-enter, .bp3-transition-container.bp3-popover-appear{
    opacity:0; }
  .bp3-transition-container.bp3-popover-enter-active, .bp3-transition-container.bp3-popover-appear-active{
    opacity:1;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-transition-container.bp3-popover-exit{
    opacity:1; }
  .bp3-transition-container.bp3-popover-exit-active{
    opacity:0;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-transition-container:focus{
    outline:none; }
  .bp3-transition-container.bp3-popover-leave .bp3-popover-content{
    pointer-events:none; }
  .bp3-transition-container[data-x-out-of-boundaries]{
    display:none; }

span.bp3-popover-target{
  display:inline-block; }

.bp3-popover-wrapper.bp3-fill{
  width:100%; }

.bp3-portal{
  left:0;
  position:absolute;
  right:0;
  top:0; }
@-webkit-keyframes linear-progress-bar-stripes{
  from{
    background-position:0 0; }
  to{
    background-position:30px 0; } }
@keyframes linear-progress-bar-stripes{
  from{
    background-position:0 0; }
  to{
    background-position:30px 0; } }

.bp3-progress-bar{
  background:rgba(92, 112, 128, 0.2);
  border-radius:40px;
  display:block;
  height:8px;
  overflow:hidden;
  position:relative;
  width:100%; }
  .bp3-progress-bar .bp3-progress-meter{
    background:linear-gradient(-45deg, rgba(255, 255, 255, 0.2) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.2) 50%, rgba(255, 255, 255, 0.2) 75%, transparent 75%);
    background-color:rgba(92, 112, 128, 0.8);
    background-size:30px 30px;
    border-radius:40px;
    height:100%;
    position:absolute;
    -webkit-transition:width 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:width 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    width:100%; }
  .bp3-progress-bar:not(.bp3-no-animation):not(.bp3-no-stripes) .bp3-progress-meter{
    animation:linear-progress-bar-stripes 300ms linear infinite reverse; }
  .bp3-progress-bar.bp3-no-stripes .bp3-progress-meter{
    background-image:none; }

.bp3-dark .bp3-progress-bar{
  background:rgba(16, 22, 26, 0.5); }
  .bp3-dark .bp3-progress-bar .bp3-progress-meter{
    background-color:#8a9ba8; }

.bp3-progress-bar.bp3-intent-primary .bp3-progress-meter{
  background-color:#137cbd; }

.bp3-progress-bar.bp3-intent-success .bp3-progress-meter{
  background-color:#0f9960; }

.bp3-progress-bar.bp3-intent-warning .bp3-progress-meter{
  background-color:#d9822b; }

.bp3-progress-bar.bp3-intent-danger .bp3-progress-meter{
  background-color:#db3737; }
@-webkit-keyframes skeleton-glow{
  from{
    background:rgba(206, 217, 224, 0.2);
    border-color:rgba(206, 217, 224, 0.2); }
  to{
    background:rgba(92, 112, 128, 0.2);
    border-color:rgba(92, 112, 128, 0.2); } }
@keyframes skeleton-glow{
  from{
    background:rgba(206, 217, 224, 0.2);
    border-color:rgba(206, 217, 224, 0.2); }
  to{
    background:rgba(92, 112, 128, 0.2);
    border-color:rgba(92, 112, 128, 0.2); } }
.bp3-skeleton{
  -webkit-animation:1000ms linear infinite alternate skeleton-glow;
          animation:1000ms linear infinite alternate skeleton-glow;
  background:rgba(206, 217, 224, 0.2);
  background-clip:padding-box !important;
  border-color:rgba(206, 217, 224, 0.2) !important;
  border-radius:2px;
  -webkit-box-shadow:none !important;
          box-shadow:none !important;
  color:transparent !important;
  cursor:default;
  pointer-events:none;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-skeleton::before, .bp3-skeleton::after,
  .bp3-skeleton *{
    visibility:hidden !important; }
.bp3-slider{
  height:40px;
  min-width:150px;
  width:100%;
  cursor:default;
  outline:none;
  position:relative;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-slider:hover{
    cursor:pointer; }
  .bp3-slider:active{
    cursor:-webkit-grabbing;
    cursor:grabbing; }
  .bp3-slider.bp3-disabled{
    cursor:not-allowed;
    opacity:0.5; }
  .bp3-slider.bp3-slider-unlabeled{
    height:16px; }

.bp3-slider-track,
.bp3-slider-progress{
  height:6px;
  left:0;
  right:0;
  top:5px;
  position:absolute; }

.bp3-slider-track{
  border-radius:3px;
  overflow:hidden; }

.bp3-slider-progress{
  background:rgba(92, 112, 128, 0.2); }
  .bp3-dark .bp3-slider-progress{
    background:rgba(16, 22, 26, 0.5); }
  .bp3-slider-progress.bp3-intent-primary{
    background-color:#137cbd; }
  .bp3-slider-progress.bp3-intent-success{
    background-color:#0f9960; }
  .bp3-slider-progress.bp3-intent-warning{
    background-color:#d9822b; }
  .bp3-slider-progress.bp3-intent-danger{
    background-color:#db3737; }

.bp3-slider-handle{
  background-color:#f5f8fa;
  background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
  background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
  color:#182026;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
  cursor:pointer;
  height:16px;
  left:0;
  position:absolute;
  top:0;
  width:16px; }
  .bp3-slider-handle:hover{
    background-clip:padding-box;
    background-color:#ebf1f5;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
  .bp3-slider-handle:active, .bp3-slider-handle.bp3-active{
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-slider-handle:disabled, .bp3-slider-handle.bp3-disabled{
    background-color:rgba(206, 217, 224, 0.5);
    background-image:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed;
    outline:none; }
    .bp3-slider-handle:disabled.bp3-active, .bp3-slider-handle:disabled.bp3-active:hover, .bp3-slider-handle.bp3-disabled.bp3-active, .bp3-slider-handle.bp3-disabled.bp3-active:hover{
      background:rgba(206, 217, 224, 0.7); }
  .bp3-slider-handle:focus{
    z-index:1; }
  .bp3-slider-handle:hover{
    background-clip:padding-box;
    background-color:#ebf1f5;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
    cursor:-webkit-grab;
    cursor:grab;
    z-index:2; }
  .bp3-slider-handle.bp3-active{
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 1px rgba(16, 22, 26, 0.1);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 1px rgba(16, 22, 26, 0.1);
    cursor:-webkit-grabbing;
    cursor:grabbing; }
  .bp3-disabled .bp3-slider-handle{
    background:#bfccd6;
    -webkit-box-shadow:none;
            box-shadow:none;
    pointer-events:none; }
  .bp3-dark .bp3-slider-handle{
    background-color:#394b59;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark .bp3-slider-handle:hover, .bp3-dark .bp3-slider-handle:active, .bp3-dark .bp3-slider-handle.bp3-active{
      color:#f5f8fa; }
    .bp3-dark .bp3-slider-handle:hover{
      background-color:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-slider-handle:active, .bp3-dark .bp3-slider-handle.bp3-active{
      background-color:#202b33;
      background-image:none;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-slider-handle:disabled, .bp3-dark .bp3-slider-handle.bp3-disabled{
      background-color:rgba(57, 75, 89, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-slider-handle:disabled.bp3-active, .bp3-dark .bp3-slider-handle.bp3-disabled.bp3-active{
        background:rgba(57, 75, 89, 0.7); }
    .bp3-dark .bp3-slider-handle .bp3-button-spinner .bp3-spinner-head{
      background:rgba(16, 22, 26, 0.5);
      stroke:#8a9ba8; }
    .bp3-dark .bp3-slider-handle, .bp3-dark .bp3-slider-handle:hover{
      background-color:#394b59; }
    .bp3-dark .bp3-slider-handle.bp3-active{
      background-color:#293742; }
  .bp3-dark .bp3-disabled .bp3-slider-handle{
    background:#5c7080;
    border-color:#5c7080;
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-slider-handle .bp3-slider-label{
    background:#394b59;
    border-radius:3px;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
    color:#f5f8fa;
    margin-left:8px; }
    .bp3-dark .bp3-slider-handle .bp3-slider-label{
      background:#e1e8ed;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
      color:#394b59; }
    .bp3-disabled .bp3-slider-handle .bp3-slider-label{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-slider-handle.bp3-start, .bp3-slider-handle.bp3-end{
    width:8px; }
  .bp3-slider-handle.bp3-start{
    border-bottom-right-radius:0;
    border-top-right-radius:0; }
  .bp3-slider-handle.bp3-end{
    border-bottom-left-radius:0;
    border-top-left-radius:0;
    margin-left:8px; }
    .bp3-slider-handle.bp3-end .bp3-slider-label{
      margin-left:0; }

.bp3-slider-label{
  -webkit-transform:translate(-50%, 20px);
          transform:translate(-50%, 20px);
  display:inline-block;
  font-size:12px;
  line-height:1;
  padding:2px 5px;
  position:absolute;
  vertical-align:top; }

.bp3-slider.bp3-vertical{
  height:150px;
  min-width:40px;
  width:40px; }
  .bp3-slider.bp3-vertical .bp3-slider-track,
  .bp3-slider.bp3-vertical .bp3-slider-progress{
    bottom:0;
    height:auto;
    left:5px;
    top:0;
    width:6px; }
  .bp3-slider.bp3-vertical .bp3-slider-progress{
    top:auto; }
  .bp3-slider.bp3-vertical .bp3-slider-label{
    -webkit-transform:translate(20px, 50%);
            transform:translate(20px, 50%); }
  .bp3-slider.bp3-vertical .bp3-slider-handle{
    top:auto; }
    .bp3-slider.bp3-vertical .bp3-slider-handle .bp3-slider-label{
      margin-left:0;
      margin-top:-8px; }
    .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-end, .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start{
      height:8px;
      margin-left:0;
      width:16px; }
    .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start{
      border-bottom-right-radius:3px;
      border-top-left-radius:0; }
      .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start .bp3-slider-label{
        -webkit-transform:translate(20px);
                transform:translate(20px); }
    .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-end{
      border-bottom-left-radius:0;
      border-bottom-right-radius:0;
      border-top-left-radius:3px;
      margin-bottom:8px; }

@-webkit-keyframes pt-spinner-animation{
  from{
    -webkit-transform:rotate(0deg);
            transform:rotate(0deg); }
  to{
    -webkit-transform:rotate(360deg);
            transform:rotate(360deg); } }

@keyframes pt-spinner-animation{
  from{
    -webkit-transform:rotate(0deg);
            transform:rotate(0deg); }
  to{
    -webkit-transform:rotate(360deg);
            transform:rotate(360deg); } }

.bp3-spinner{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  overflow:visible;
  vertical-align:middle; }
  .bp3-spinner svg{
    display:block; }
  .bp3-spinner path{
    fill-opacity:0; }
  .bp3-spinner .bp3-spinner-head{
    stroke:rgba(92, 112, 128, 0.8);
    stroke-linecap:round;
    -webkit-transform-origin:center;
            transform-origin:center;
    -webkit-transition:stroke-dashoffset 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:stroke-dashoffset 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-spinner .bp3-spinner-track{
    stroke:rgba(92, 112, 128, 0.2); }

.bp3-spinner-animation{
  -webkit-animation:pt-spinner-animation 500ms linear infinite;
          animation:pt-spinner-animation 500ms linear infinite; }
  .bp3-no-spin > .bp3-spinner-animation{
    -webkit-animation:none;
            animation:none; }

.bp3-dark .bp3-spinner .bp3-spinner-head{
  stroke:#8a9ba8; }

.bp3-dark .bp3-spinner .bp3-spinner-track{
  stroke:rgba(16, 22, 26, 0.5); }

.bp3-spinner.bp3-intent-primary .bp3-spinner-head{
  stroke:#137cbd; }

.bp3-spinner.bp3-intent-success .bp3-spinner-head{
  stroke:#0f9960; }

.bp3-spinner.bp3-intent-warning .bp3-spinner-head{
  stroke:#d9822b; }

.bp3-spinner.bp3-intent-danger .bp3-spinner-head{
  stroke:#db3737; }
.bp3-tabs.bp3-vertical{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex; }
  .bp3-tabs.bp3-vertical > .bp3-tab-list{
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start;
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column; }
    .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab{
      border-radius:3px;
      padding:0 10px;
      width:100%; }
      .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab[aria-selected="true"]{
        background-color:rgba(19, 124, 189, 0.2);
        -webkit-box-shadow:none;
                box-shadow:none; }
    .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab-indicator-wrapper .bp3-tab-indicator{
      background-color:rgba(19, 124, 189, 0.2);
      border-radius:3px;
      bottom:0;
      height:auto;
      left:0;
      right:0;
      top:0; }
  .bp3-tabs.bp3-vertical > .bp3-tab-panel{
    margin-top:0;
    padding-left:20px; }

.bp3-tab-list{
  -webkit-box-align:end;
      -ms-flex-align:end;
          align-items:flex-end;
  border:none;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  list-style:none;
  margin:0;
  padding:0;
  position:relative; }
  .bp3-tab-list > *:not(:last-child){
    margin-right:20px; }

.bp3-tab{
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal;
  color:#182026;
  cursor:pointer;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  font-size:14px;
  line-height:30px;
  max-width:100%;
  position:relative;
  vertical-align:top; }
  .bp3-tab a{
    color:inherit;
    display:block;
    text-decoration:none; }
  .bp3-tab-indicator-wrapper ~ .bp3-tab{
    background-color:transparent !important;
    -webkit-box-shadow:none !important;
            box-shadow:none !important; }
  .bp3-tab[aria-disabled="true"]{
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }
  .bp3-tab[aria-selected="true"]{
    border-radius:0;
    -webkit-box-shadow:inset 0 -3px 0 #106ba3;
            box-shadow:inset 0 -3px 0 #106ba3; }
  .bp3-tab[aria-selected="true"], .bp3-tab:not([aria-disabled="true"]):hover{
    color:#106ba3; }
  .bp3-tab:focus{
    -moz-outline-radius:0; }
  .bp3-large > .bp3-tab{
    font-size:16px;
    line-height:40px; }

.bp3-tab-panel{
  margin-top:20px; }
  .bp3-tab-panel[aria-hidden="true"]{
    display:none; }

.bp3-tab-indicator-wrapper{
  left:0;
  pointer-events:none;
  position:absolute;
  top:0;
  -webkit-transform:translateX(0), translateY(0);
          transform:translateX(0), translateY(0);
  -webkit-transition:height, width, -webkit-transform;
  transition:height, width, -webkit-transform;
  transition:height, transform, width;
  transition:height, transform, width, -webkit-transform;
  -webkit-transition-duration:200ms;
          transition-duration:200ms;
  -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
          transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-tab-indicator-wrapper .bp3-tab-indicator{
    background-color:#106ba3;
    bottom:0;
    height:3px;
    left:0;
    position:absolute;
    right:0; }
  .bp3-tab-indicator-wrapper.bp3-no-animation{
    -webkit-transition:none;
    transition:none; }

.bp3-dark .bp3-tab{
  color:#f5f8fa; }
  .bp3-dark .bp3-tab[aria-disabled="true"]{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-dark .bp3-tab[aria-selected="true"]{
    -webkit-box-shadow:inset 0 -3px 0 #48aff0;
            box-shadow:inset 0 -3px 0 #48aff0; }
  .bp3-dark .bp3-tab[aria-selected="true"], .bp3-dark .bp3-tab:not([aria-disabled="true"]):hover{
    color:#48aff0; }

.bp3-dark .bp3-tab-indicator{
  background-color:#48aff0; }

.bp3-flex-expander{
  -webkit-box-flex:1;
      -ms-flex:1 1;
          flex:1 1; }
.bp3-tag{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background-color:#5c7080;
  border:none;
  border-radius:3px;
  -webkit-box-shadow:none;
          box-shadow:none;
  color:#f5f8fa;
  font-size:12px;
  line-height:16px;
  max-width:100%;
  min-height:20px;
  min-width:20px;
  padding:2px 6px;
  position:relative; }
  .bp3-tag.bp3-interactive{
    cursor:pointer; }
    .bp3-tag.bp3-interactive:hover{
      background-color:rgba(92, 112, 128, 0.85); }
    .bp3-tag.bp3-interactive.bp3-active, .bp3-tag.bp3-interactive:active{
      background-color:rgba(92, 112, 128, 0.7); }
  .bp3-tag > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-tag > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-tag::before,
  .bp3-tag > *{
    margin-right:4px; }
  .bp3-tag:empty::before,
  .bp3-tag > :last-child{
    margin-right:0; }
  .bp3-tag:focus{
    outline:rgba(19, 124, 189, 0.6) auto 2px;
    outline-offset:0;
    -moz-outline-radius:6px; }
  .bp3-tag.bp3-round{
    border-radius:30px;
    padding-left:8px;
    padding-right:8px; }
  .bp3-dark .bp3-tag{
    background-color:#bfccd6;
    color:#182026; }
    .bp3-dark .bp3-tag.bp3-interactive{
      cursor:pointer; }
      .bp3-dark .bp3-tag.bp3-interactive:hover{
        background-color:rgba(191, 204, 214, 0.85); }
      .bp3-dark .bp3-tag.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-interactive:active{
        background-color:rgba(191, 204, 214, 0.7); }
    .bp3-dark .bp3-tag > .bp3-icon, .bp3-dark .bp3-tag .bp3-icon-standard, .bp3-dark .bp3-tag .bp3-icon-large{
      fill:currentColor; }
  .bp3-tag > .bp3-icon, .bp3-tag .bp3-icon-standard, .bp3-tag .bp3-icon-large{
    fill:#ffffff; }
  .bp3-tag.bp3-large,
  .bp3-large .bp3-tag{
    font-size:14px;
    line-height:20px;
    min-height:30px;
    min-width:30px;
    padding:5px 10px; }
    .bp3-tag.bp3-large::before,
    .bp3-tag.bp3-large > *,
    .bp3-large .bp3-tag::before,
    .bp3-large .bp3-tag > *{
      margin-right:7px; }
    .bp3-tag.bp3-large:empty::before,
    .bp3-tag.bp3-large > :last-child,
    .bp3-large .bp3-tag:empty::before,
    .bp3-large .bp3-tag > :last-child{
      margin-right:0; }
    .bp3-tag.bp3-large.bp3-round,
    .bp3-large .bp3-tag.bp3-round{
      padding-left:12px;
      padding-right:12px; }
  .bp3-tag.bp3-intent-primary{
    background:#137cbd;
    color:#ffffff; }
    .bp3-tag.bp3-intent-primary.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-primary.bp3-interactive:hover{
        background-color:rgba(19, 124, 189, 0.85); }
      .bp3-tag.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-primary.bp3-interactive:active{
        background-color:rgba(19, 124, 189, 0.7); }
  .bp3-tag.bp3-intent-success{
    background:#0f9960;
    color:#ffffff; }
    .bp3-tag.bp3-intent-success.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-success.bp3-interactive:hover{
        background-color:rgba(15, 153, 96, 0.85); }
      .bp3-tag.bp3-intent-success.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-success.bp3-interactive:active{
        background-color:rgba(15, 153, 96, 0.7); }
  .bp3-tag.bp3-intent-warning{
    background:#d9822b;
    color:#ffffff; }
    .bp3-tag.bp3-intent-warning.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-warning.bp3-interactive:hover{
        background-color:rgba(217, 130, 43, 0.85); }
      .bp3-tag.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-warning.bp3-interactive:active{
        background-color:rgba(217, 130, 43, 0.7); }
  .bp3-tag.bp3-intent-danger{
    background:#db3737;
    color:#ffffff; }
    .bp3-tag.bp3-intent-danger.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-danger.bp3-interactive:hover{
        background-color:rgba(219, 55, 55, 0.85); }
      .bp3-tag.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-danger.bp3-interactive:active{
        background-color:rgba(219, 55, 55, 0.7); }
  .bp3-tag.bp3-fill{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    width:100%; }
  .bp3-tag.bp3-minimal > .bp3-icon, .bp3-tag.bp3-minimal .bp3-icon-standard, .bp3-tag.bp3-minimal .bp3-icon-large{
    fill:#5c7080; }
  .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]){
    background-color:rgba(138, 155, 168, 0.2);
    color:#182026; }
    .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:hover{
        background-color:rgba(92, 112, 128, 0.3); }
      .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive.bp3-active, .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:active{
        background-color:rgba(92, 112, 128, 0.4); }
    .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]){
      color:#f5f8fa; }
      .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:hover{
          background-color:rgba(191, 204, 214, 0.3); }
        .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:active{
          background-color:rgba(191, 204, 214, 0.4); }
      .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) > .bp3-icon, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) .bp3-icon-standard, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) .bp3-icon-large{
        fill:#a7b6c2; }
  .bp3-tag.bp3-minimal.bp3-intent-primary{
    background-color:rgba(19, 124, 189, 0.15);
    color:#106ba3; }
    .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:hover{
        background-color:rgba(19, 124, 189, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:active{
        background-color:rgba(19, 124, 189, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-primary > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-primary .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-primary .bp3-icon-large{
      fill:#137cbd; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary{
      background-color:rgba(19, 124, 189, 0.25);
      color:#48aff0; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:hover{
          background-color:rgba(19, 124, 189, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:active{
          background-color:rgba(19, 124, 189, 0.45); }
  .bp3-tag.bp3-minimal.bp3-intent-success{
    background-color:rgba(15, 153, 96, 0.15);
    color:#0d8050; }
    .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:hover{
        background-color:rgba(15, 153, 96, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:active{
        background-color:rgba(15, 153, 96, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-success > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-success .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-success .bp3-icon-large{
      fill:#0f9960; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success{
      background-color:rgba(15, 153, 96, 0.25);
      color:#3dcc91; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:hover{
          background-color:rgba(15, 153, 96, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:active{
          background-color:rgba(15, 153, 96, 0.45); }
  .bp3-tag.bp3-minimal.bp3-intent-warning{
    background-color:rgba(217, 130, 43, 0.15);
    color:#bf7326; }
    .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:hover{
        background-color:rgba(217, 130, 43, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:active{
        background-color:rgba(217, 130, 43, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-warning > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-warning .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-warning .bp3-icon-large{
      fill:#d9822b; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning{
      background-color:rgba(217, 130, 43, 0.25);
      color:#ffb366; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:hover{
          background-color:rgba(217, 130, 43, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:active{
          background-color:rgba(217, 130, 43, 0.45); }
  .bp3-tag.bp3-minimal.bp3-intent-danger{
    background-color:rgba(219, 55, 55, 0.15);
    color:#c23030; }
    .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:hover{
        background-color:rgba(219, 55, 55, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:active{
        background-color:rgba(219, 55, 55, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-danger > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-danger .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-danger .bp3-icon-large{
      fill:#db3737; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger{
      background-color:rgba(219, 55, 55, 0.25);
      color:#ff7373; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:hover{
          background-color:rgba(219, 55, 55, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:active{
          background-color:rgba(219, 55, 55, 0.45); }

.bp3-tag-remove{
  background:none;
  border:none;
  color:inherit;
  cursor:pointer;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  margin-bottom:-2px;
  margin-right:-6px !important;
  margin-top:-2px;
  opacity:0.5;
  padding:2px;
  padding-left:0; }
  .bp3-tag-remove:hover{
    background:none;
    opacity:0.8;
    text-decoration:none; }
  .bp3-tag-remove:active{
    opacity:1; }
  .bp3-tag-remove:empty::before{
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-style:normal;
    font-weight:400;
    line-height:1;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    content:""; }
  .bp3-large .bp3-tag-remove{
    margin-right:-10px !important;
    padding:0 5px 0 0; }
    .bp3-large .bp3-tag-remove:empty::before{
      font-family:"Icons20", sans-serif;
      font-size:20px;
      font-style:normal;
      font-weight:400;
      line-height:1; }
.bp3-tag-input{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:start;
      -ms-flex-align:start;
          align-items:flex-start;
  cursor:text;
  height:auto;
  line-height:inherit;
  min-height:30px;
  padding-left:5px;
  padding-right:0; }
  .bp3-tag-input > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-tag-input > .bp3-tag-input-values{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-tag-input .bp3-tag-input-icon{
    color:#5c7080;
    margin-left:2px;
    margin-right:7px;
    margin-top:7px; }
  .bp3-tag-input .bp3-tag-input-values{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row;
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    -ms-flex-item-align:stretch;
        align-self:stretch;
    -ms-flex-wrap:wrap;
        flex-wrap:wrap;
    margin-right:7px;
    margin-top:5px;
    min-width:0; }
    .bp3-tag-input .bp3-tag-input-values > *{
      -webkit-box-flex:0;
          -ms-flex-positive:0;
              flex-grow:0;
      -ms-flex-negative:0;
          flex-shrink:0; }
    .bp3-tag-input .bp3-tag-input-values > .bp3-fill{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1;
      -ms-flex-negative:1;
          flex-shrink:1; }
    .bp3-tag-input .bp3-tag-input-values::before,
    .bp3-tag-input .bp3-tag-input-values > *{
      margin-right:5px; }
    .bp3-tag-input .bp3-tag-input-values:empty::before,
    .bp3-tag-input .bp3-tag-input-values > :last-child{
      margin-right:0; }
    .bp3-tag-input .bp3-tag-input-values:first-child .bp3-input-ghost:first-child{
      padding-left:5px; }
    .bp3-tag-input .bp3-tag-input-values > *{
      margin-bottom:5px; }
  .bp3-tag-input .bp3-tag{
    overflow-wrap:break-word; }
    .bp3-tag-input .bp3-tag.bp3-active{
      outline:rgba(19, 124, 189, 0.6) auto 2px;
      outline-offset:0;
      -moz-outline-radius:6px; }
  .bp3-tag-input .bp3-input-ghost{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    line-height:20px;
    width:80px; }
    .bp3-tag-input .bp3-input-ghost:disabled, .bp3-tag-input .bp3-input-ghost.bp3-disabled{
      cursor:not-allowed; }
  .bp3-tag-input .bp3-button,
  .bp3-tag-input .bp3-spinner{
    margin:3px;
    margin-left:0; }
  .bp3-tag-input .bp3-button{
    min-height:24px;
    min-width:24px;
    padding:0 7px; }
  .bp3-tag-input.bp3-large{
    height:auto;
    min-height:40px; }
    .bp3-tag-input.bp3-large::before,
    .bp3-tag-input.bp3-large > *{
      margin-right:10px; }
    .bp3-tag-input.bp3-large:empty::before,
    .bp3-tag-input.bp3-large > :last-child{
      margin-right:0; }
    .bp3-tag-input.bp3-large .bp3-tag-input-icon{
      margin-left:5px;
      margin-top:10px; }
    .bp3-tag-input.bp3-large .bp3-input-ghost{
      line-height:30px; }
    .bp3-tag-input.bp3-large .bp3-button{
      min-height:30px;
      min-width:30px;
      padding:5px 10px;
      margin:5px;
      margin-left:0; }
    .bp3-tag-input.bp3-large .bp3-spinner{
      margin:8px;
      margin-left:0; }
  .bp3-tag-input.bp3-active{
    background-color:#ffffff;
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-success{
      -webkit-box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-tag-input .bp3-tag-input-icon, .bp3-tag-input.bp3-dark .bp3-tag-input-icon{
    color:#a7b6c2; }
  .bp3-dark .bp3-tag-input .bp3-input-ghost, .bp3-tag-input.bp3-dark .bp3-input-ghost{
    color:#f5f8fa; }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::-webkit-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::-moz-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost:-ms-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::-ms-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::placeholder{
      color:rgba(167, 182, 194, 0.6); }
  .bp3-dark .bp3-tag-input.bp3-active, .bp3-tag-input.bp3-dark.bp3-active{
    background-color:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-primary, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-success, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-success{
      -webkit-box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-warning, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-danger, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-input-ghost{
  background:none;
  border:none;
  -webkit-box-shadow:none;
          box-shadow:none;
  padding:0; }
  .bp3-input-ghost::-webkit-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost::-moz-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost:-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost::-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost::placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost:focus{
    outline:none !important; }
.bp3-toast{
  -webkit-box-align:start;
      -ms-flex-align:start;
          align-items:flex-start;
  background-color:#ffffff;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  margin:20px 0 0;
  max-width:500px;
  min-width:300px;
  pointer-events:all;
  position:relative !important; }
  .bp3-toast.bp3-toast-enter, .bp3-toast.bp3-toast-appear{
    -webkit-transform:translateY(-40px);
            transform:translateY(-40px); }
  .bp3-toast.bp3-toast-enter-active, .bp3-toast.bp3-toast-appear-active{
    -webkit-transform:translateY(0);
            transform:translateY(0);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-toast.bp3-toast-enter ~ .bp3-toast, .bp3-toast.bp3-toast-appear ~ .bp3-toast{
    -webkit-transform:translateY(-40px);
            transform:translateY(-40px); }
  .bp3-toast.bp3-toast-enter-active ~ .bp3-toast, .bp3-toast.bp3-toast-appear-active ~ .bp3-toast{
    -webkit-transform:translateY(0);
            transform:translateY(0);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-toast.bp3-toast-exit{
    opacity:1;
    -webkit-filter:blur(0);
            filter:blur(0); }
  .bp3-toast.bp3-toast-exit-active{
    opacity:0;
    -webkit-filter:blur(10px);
            filter:blur(10px);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:opacity, -webkit-filter;
    transition-property:opacity, -webkit-filter;
    transition-property:opacity, filter;
    transition-property:opacity, filter, -webkit-filter;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-toast.bp3-toast-exit ~ .bp3-toast{
    -webkit-transform:translateY(0);
            transform:translateY(0); }
  .bp3-toast.bp3-toast-exit-active ~ .bp3-toast{
    -webkit-transform:translateY(-40px);
            transform:translateY(-40px);
    -webkit-transition-delay:50ms;
            transition-delay:50ms;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-toast .bp3-button-group{
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    padding:5px;
    padding-left:0; }
  .bp3-toast > .bp3-icon{
    color:#5c7080;
    margin:12px;
    margin-right:0; }
  .bp3-toast.bp3-dark,
  .bp3-dark .bp3-toast{
    background-color:#394b59;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
    .bp3-toast.bp3-dark > .bp3-icon,
    .bp3-dark .bp3-toast > .bp3-icon{
      color:#a7b6c2; }
  .bp3-toast[class*="bp3-intent-"] a{
    color:rgba(255, 255, 255, 0.7); }
    .bp3-toast[class*="bp3-intent-"] a:hover{
      color:#ffffff; }
  .bp3-toast[class*="bp3-intent-"] > .bp3-icon{
    color:#ffffff; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button, .bp3-toast[class*="bp3-intent-"] .bp3-button::before,
  .bp3-toast[class*="bp3-intent-"] .bp3-button .bp3-icon, .bp3-toast[class*="bp3-intent-"] .bp3-button:active{
    color:rgba(255, 255, 255, 0.7) !important; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button:focus{
    outline-color:rgba(255, 255, 255, 0.5); }
  .bp3-toast[class*="bp3-intent-"] .bp3-button:hover{
    background-color:rgba(255, 255, 255, 0.15) !important;
    color:#ffffff !important; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button:active{
    background-color:rgba(255, 255, 255, 0.3) !important;
    color:#ffffff !important; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button::after{
    background:rgba(255, 255, 255, 0.3) !important; }
  .bp3-toast.bp3-intent-primary{
    background-color:#137cbd;
    color:#ffffff; }
  .bp3-toast.bp3-intent-success{
    background-color:#0f9960;
    color:#ffffff; }
  .bp3-toast.bp3-intent-warning{
    background-color:#d9822b;
    color:#ffffff; }
  .bp3-toast.bp3-intent-danger{
    background-color:#db3737;
    color:#ffffff; }

.bp3-toast-message{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  padding:11px;
  word-break:break-word; }

.bp3-toast-container{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box !important;
  display:-ms-flexbox !important;
  display:flex !important;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  left:0;
  overflow:hidden;
  padding:0 20px 20px;
  pointer-events:none;
  right:0;
  z-index:40; }
  .bp3-toast-container.bp3-toast-container-in-portal{
    position:fixed; }
  .bp3-toast-container.bp3-toast-container-inline{
    position:absolute; }
  .bp3-toast-container.bp3-toast-container-top{
    top:0; }
  .bp3-toast-container.bp3-toast-container-bottom{
    bottom:0;
    -webkit-box-orient:vertical;
    -webkit-box-direction:reverse;
        -ms-flex-direction:column-reverse;
            flex-direction:column-reverse;
    top:auto; }
  .bp3-toast-container.bp3-toast-container-left{
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start; }
  .bp3-toast-container.bp3-toast-container-right{
    -webkit-box-align:end;
        -ms-flex-align:end;
            align-items:flex-end; }

.bp3-toast-container-bottom .bp3-toast.bp3-toast-enter:not(.bp3-toast-enter-active),
.bp3-toast-container-bottom .bp3-toast.bp3-toast-enter:not(.bp3-toast-enter-active) ~ .bp3-toast, .bp3-toast-container-bottom .bp3-toast.bp3-toast-appear:not(.bp3-toast-appear-active),
.bp3-toast-container-bottom .bp3-toast.bp3-toast-appear:not(.bp3-toast-appear-active) ~ .bp3-toast,
.bp3-toast-container-bottom .bp3-toast.bp3-toast-exit-active ~ .bp3-toast,
.bp3-toast-container-bottom .bp3-toast.bp3-toast-leave-active ~ .bp3-toast{
  -webkit-transform:translateY(60px);
          transform:translateY(60px); }
.bp3-tooltip{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  -webkit-transform:scale(1);
          transform:scale(1); }
  .bp3-tooltip .bp3-popover-arrow{
    height:22px;
    position:absolute;
    width:22px; }
    .bp3-tooltip .bp3-popover-arrow::before{
      height:14px;
      margin:4px;
      width:14px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip{
    margin-bottom:11px;
    margin-top:-11px; }
    .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow{
      bottom:-8px; }
      .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(-90deg);
                transform:rotate(-90deg); }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip{
    margin-left:11px; }
    .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow{
      left:-8px; }
      .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(0);
                transform:rotate(0); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip{
    margin-top:11px; }
    .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow{
      top:-8px; }
      .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(90deg);
                transform:rotate(90deg); }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip{
    margin-left:-11px;
    margin-right:11px; }
    .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow{
      right:-8px; }
      .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(180deg);
                transform:rotate(180deg); }
  .bp3-tether-element-attached-middle > .bp3-tooltip > .bp3-popover-arrow{
    top:50%;
    -webkit-transform:translateY(-50%);
            transform:translateY(-50%); }
  .bp3-tether-element-attached-center > .bp3-tooltip > .bp3-popover-arrow{
    right:50%;
    -webkit-transform:translateX(50%);
            transform:translateX(50%); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow{
    top:-0.22183px; }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow{
    right:-0.22183px; }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow{
    left:-0.22183px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow{
    bottom:-0.22183px; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-left > .bp3-tooltip{
    -webkit-transform-origin:top left;
            transform-origin:top left; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-center > .bp3-tooltip{
    -webkit-transform-origin:top center;
            transform-origin:top center; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-right > .bp3-tooltip{
    -webkit-transform-origin:top right;
            transform-origin:top right; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-left > .bp3-tooltip{
    -webkit-transform-origin:center left;
            transform-origin:center left; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-center > .bp3-tooltip{
    -webkit-transform-origin:center center;
            transform-origin:center center; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-right > .bp3-tooltip{
    -webkit-transform-origin:center right;
            transform-origin:center right; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-left > .bp3-tooltip{
    -webkit-transform-origin:bottom left;
            transform-origin:bottom left; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-center > .bp3-tooltip{
    -webkit-transform-origin:bottom center;
            transform-origin:bottom center; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-right > .bp3-tooltip{
    -webkit-transform-origin:bottom right;
            transform-origin:bottom right; }
  .bp3-tooltip .bp3-popover-content{
    background:#394b59;
    color:#f5f8fa; }
  .bp3-tooltip .bp3-popover-arrow::before{
    -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2);
            box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2); }
  .bp3-tooltip .bp3-popover-arrow-border{
    fill:#10161a;
    fill-opacity:0.1; }
  .bp3-tooltip .bp3-popover-arrow-fill{
    fill:#394b59; }
  .bp3-popover-enter > .bp3-tooltip, .bp3-popover-appear > .bp3-tooltip{
    -webkit-transform:scale(0.8);
            transform:scale(0.8); }
  .bp3-popover-enter-active > .bp3-tooltip, .bp3-popover-appear-active > .bp3-tooltip{
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-popover-exit > .bp3-tooltip{
    -webkit-transform:scale(1);
            transform:scale(1); }
  .bp3-popover-exit-active > .bp3-tooltip{
    -webkit-transform:scale(0.8);
            transform:scale(0.8);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-tooltip .bp3-popover-content{
    padding:10px 12px; }
  .bp3-tooltip.bp3-dark,
  .bp3-dark .bp3-tooltip{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
    .bp3-tooltip.bp3-dark .bp3-popover-content,
    .bp3-dark .bp3-tooltip .bp3-popover-content{
      background:#e1e8ed;
      color:#394b59; }
    .bp3-tooltip.bp3-dark .bp3-popover-arrow::before,
    .bp3-dark .bp3-tooltip .bp3-popover-arrow::before{
      -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4);
              box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4); }
    .bp3-tooltip.bp3-dark .bp3-popover-arrow-border,
    .bp3-dark .bp3-tooltip .bp3-popover-arrow-border{
      fill:#10161a;
      fill-opacity:0.2; }
    .bp3-tooltip.bp3-dark .bp3-popover-arrow-fill,
    .bp3-dark .bp3-tooltip .bp3-popover-arrow-fill{
      fill:#e1e8ed; }
  .bp3-tooltip.bp3-intent-primary .bp3-popover-content{
    background:#137cbd;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-primary .bp3-popover-arrow-fill{
    fill:#137cbd; }
  .bp3-tooltip.bp3-intent-success .bp3-popover-content{
    background:#0f9960;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-success .bp3-popover-arrow-fill{
    fill:#0f9960; }
  .bp3-tooltip.bp3-intent-warning .bp3-popover-content{
    background:#d9822b;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-warning .bp3-popover-arrow-fill{
    fill:#d9822b; }
  .bp3-tooltip.bp3-intent-danger .bp3-popover-content{
    background:#db3737;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-danger .bp3-popover-arrow-fill{
    fill:#db3737; }

.bp3-tooltip-indicator{
  border-bottom:dotted 1px;
  cursor:help; }
.bp3-tree .bp3-icon, .bp3-tree .bp3-icon-standard, .bp3-tree .bp3-icon-large{
  color:#5c7080; }
  .bp3-tree .bp3-icon.bp3-intent-primary, .bp3-tree .bp3-icon-standard.bp3-intent-primary, .bp3-tree .bp3-icon-large.bp3-intent-primary{
    color:#137cbd; }
  .bp3-tree .bp3-icon.bp3-intent-success, .bp3-tree .bp3-icon-standard.bp3-intent-success, .bp3-tree .bp3-icon-large.bp3-intent-success{
    color:#0f9960; }
  .bp3-tree .bp3-icon.bp3-intent-warning, .bp3-tree .bp3-icon-standard.bp3-intent-warning, .bp3-tree .bp3-icon-large.bp3-intent-warning{
    color:#d9822b; }
  .bp3-tree .bp3-icon.bp3-intent-danger, .bp3-tree .bp3-icon-standard.bp3-intent-danger, .bp3-tree .bp3-icon-large.bp3-intent-danger{
    color:#db3737; }

.bp3-tree-node-list{
  list-style:none;
  margin:0;
  padding-left:0; }

.bp3-tree-root{
  background-color:transparent;
  cursor:default;
  padding-left:0;
  position:relative; }

.bp3-tree-node-content-0{
  padding-left:0px; }

.bp3-tree-node-content-1{
  padding-left:23px; }

.bp3-tree-node-content-2{
  padding-left:46px; }

.bp3-tree-node-content-3{
  padding-left:69px; }

.bp3-tree-node-content-4{
  padding-left:92px; }

.bp3-tree-node-content-5{
  padding-left:115px; }

.bp3-tree-node-content-6{
  padding-left:138px; }

.bp3-tree-node-content-7{
  padding-left:161px; }

.bp3-tree-node-content-8{
  padding-left:184px; }

.bp3-tree-node-content-9{
  padding-left:207px; }

.bp3-tree-node-content-10{
  padding-left:230px; }

.bp3-tree-node-content-11{
  padding-left:253px; }

.bp3-tree-node-content-12{
  padding-left:276px; }

.bp3-tree-node-content-13{
  padding-left:299px; }

.bp3-tree-node-content-14{
  padding-left:322px; }

.bp3-tree-node-content-15{
  padding-left:345px; }

.bp3-tree-node-content-16{
  padding-left:368px; }

.bp3-tree-node-content-17{
  padding-left:391px; }

.bp3-tree-node-content-18{
  padding-left:414px; }

.bp3-tree-node-content-19{
  padding-left:437px; }

.bp3-tree-node-content-20{
  padding-left:460px; }

.bp3-tree-node-content{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  height:30px;
  padding-right:5px;
  width:100%; }
  .bp3-tree-node-content:hover{
    background-color:rgba(191, 204, 214, 0.4); }

.bp3-tree-node-caret,
.bp3-tree-node-caret-none{
  min-width:30px; }

.bp3-tree-node-caret{
  color:#5c7080;
  cursor:pointer;
  padding:7px;
  -webkit-transform:rotate(0deg);
          transform:rotate(0deg);
  -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-tree-node-caret:hover{
    color:#182026; }
  .bp3-dark .bp3-tree-node-caret{
    color:#a7b6c2; }
    .bp3-dark .bp3-tree-node-caret:hover{
      color:#f5f8fa; }
  .bp3-tree-node-caret.bp3-tree-node-caret-open{
    -webkit-transform:rotate(90deg);
            transform:rotate(90deg); }
  .bp3-tree-node-caret.bp3-icon-standard::before{
    content:""; }

.bp3-tree-node-icon{
  margin-right:7px;
  position:relative; }

.bp3-tree-node-label{
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal;
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  position:relative;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-tree-node-label span{
    display:inline; }

.bp3-tree-node-secondary-label{
  padding:0 5px;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-tree-node-secondary-label .bp3-popover-wrapper,
  .bp3-tree-node-secondary-label .bp3-popover-target{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex; }

.bp3-tree-node.bp3-disabled .bp3-tree-node-content{
  background-color:inherit;
  color:rgba(92, 112, 128, 0.6);
  cursor:not-allowed; }

.bp3-tree-node.bp3-disabled .bp3-tree-node-caret,
.bp3-tree-node.bp3-disabled .bp3-tree-node-icon{
  color:rgba(92, 112, 128, 0.6);
  cursor:not-allowed; }

.bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content{
  background-color:#137cbd; }
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content,
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon, .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon-standard, .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon-large{
    color:#ffffff; }
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-tree-node-caret::before{
    color:rgba(255, 255, 255, 0.7); }
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-tree-node-caret:hover::before{
    color:#ffffff; }

.bp3-dark .bp3-tree-node-content:hover{
  background-color:rgba(92, 112, 128, 0.3); }

.bp3-dark .bp3-tree .bp3-icon, .bp3-dark .bp3-tree .bp3-icon-standard, .bp3-dark .bp3-tree .bp3-icon-large{
  color:#a7b6c2; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-primary, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-primary, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-primary{
    color:#137cbd; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-success, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-success, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-success{
    color:#0f9960; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-warning, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-warning, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-warning{
    color:#d9822b; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-danger, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-danger, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-danger{
    color:#db3737; }

.bp3-dark .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content{
  background-color:#137cbd; }
.bp3-omnibar{
  -webkit-filter:blur(0);
          filter:blur(0);
  opacity:1;
  background-color:#ffffff;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
  left:calc(50% - 250px);
  top:20vh;
  width:500px;
  z-index:21; }
  .bp3-omnibar.bp3-overlay-enter, .bp3-omnibar.bp3-overlay-appear{
    -webkit-filter:blur(20px);
            filter:blur(20px);
    opacity:0.2; }
  .bp3-omnibar.bp3-overlay-enter-active, .bp3-omnibar.bp3-overlay-appear-active{
    -webkit-filter:blur(0);
            filter:blur(0);
    opacity:1;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-property:opacity, -webkit-filter;
    transition-property:opacity, -webkit-filter;
    transition-property:filter, opacity;
    transition-property:filter, opacity, -webkit-filter;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-omnibar.bp3-overlay-exit{
    -webkit-filter:blur(0);
            filter:blur(0);
    opacity:1; }
  .bp3-omnibar.bp3-overlay-exit-active{
    -webkit-filter:blur(20px);
            filter:blur(20px);
    opacity:0.2;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-property:opacity, -webkit-filter;
    transition-property:opacity, -webkit-filter;
    transition-property:filter, opacity;
    transition-property:filter, opacity, -webkit-filter;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-omnibar .bp3-input{
    background-color:transparent;
    border-radius:0; }
    .bp3-omnibar .bp3-input, .bp3-omnibar .bp3-input:focus{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-omnibar .bp3-menu{
    background-color:transparent;
    border-radius:0;
    -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
    max-height:calc(60vh - 40px);
    overflow:auto; }
    .bp3-omnibar .bp3-menu:empty{
      display:none; }
  .bp3-dark .bp3-omnibar, .bp3-omnibar.bp3-dark{
    background-color:#30404d;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4); }

.bp3-omnibar-overlay .bp3-overlay-backdrop{
  background-color:rgba(16, 22, 26, 0.2); }

.bp3-select-popover .bp3-popover-content{
  padding:5px; }

.bp3-select-popover .bp3-input-group{
  margin-bottom:0; }

.bp3-select-popover .bp3-menu{
  max-height:300px;
  max-width:400px;
  overflow:auto;
  padding:0; }
  .bp3-select-popover .bp3-menu:not(:first-child){
    padding-top:5px; }

.bp3-multi-select{
  min-width:150px; }

.bp3-multi-select-popover .bp3-menu{
  max-height:300px;
  max-width:400px;
  overflow:auto; }

.bp3-select-popover .bp3-popover-content{
  padding:5px; }

.bp3-select-popover .bp3-input-group{
  margin-bottom:0; }

.bp3-select-popover .bp3-menu{
  max-height:300px;
  max-width:400px;
  overflow:auto;
  padding:0; }
  .bp3-select-popover .bp3-menu:not(:first-child){
    padding-top:5px; }
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensureUiComponents() in @jupyterlab/buildutils */

/**
 * (DEPRECATED) Support for consuming icons as CSS background images
 */

/* Icons urls */

:root {
  --jp-icon-add: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDEzaC02djZoLTJ2LTZINXYtMmg2VjVoMnY2aDZ2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-bug: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0yMCA4aC0yLjgxYy0uNDUtLjc4LTEuMDctMS40NS0xLjgyLTEuOTZMMTcgNC40MSAxNS41OSAzbC0yLjE3IDIuMTdDMTIuOTYgNS4wNiAxMi40OSA1IDEyIDVjLS40OSAwLS45Ni4wNi0xLjQxLjE3TDguNDEgMyA3IDQuNDFsMS42MiAxLjYzQzcuODggNi41NSA3LjI2IDcuMjIgNi44MSA4SDR2MmgyLjA5Yy0uMDUuMzMtLjA5LjY2LS4wOSAxdjFINHYyaDJ2MWMwIC4zNC4wNC42Ny4wOSAxSDR2MmgyLjgxYzEuMDQgMS43OSAyLjk3IDMgNS4xOSAzczQuMTUtMS4yMSA1LjE5LTNIMjB2LTJoLTIuMDljLjA1LS4zMy4wOS0uNjYuMDktMXYtMWgydi0yaC0ydi0xYzAtLjM0LS4wNC0uNjctLjA5LTFIMjBWOHptLTYgOGgtNHYtMmg0djJ6bTAtNGgtNHYtMmg0djJ6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-build: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE0LjkgMTcuNDVDMTYuMjUgMTcuNDUgMTcuMzUgMTYuMzUgMTcuMzUgMTVDMTcuMzUgMTMuNjUgMTYuMjUgMTIuNTUgMTQuOSAxMi41NUMxMy41NCAxMi41NSAxMi40NSAxMy42NSAxMi40NSAxNUMxMi40NSAxNi4zNSAxMy41NCAxNy40NSAxNC45IDE3LjQ1Wk0yMC4xIDE1LjY4TDIxLjU4IDE2Ljg0QzIxLjcxIDE2Ljk1IDIxLjc1IDE3LjEzIDIxLjY2IDE3LjI5TDIwLjI2IDE5LjcxQzIwLjE3IDE5Ljg2IDIwIDE5LjkyIDE5LjgzIDE5Ljg2TDE4LjA5IDE5LjE2QzE3LjczIDE5LjQ0IDE3LjMzIDE5LjY3IDE2LjkxIDE5Ljg1TDE2LjY0IDIxLjdDMTYuNjIgMjEuODcgMTYuNDcgMjIgMTYuMyAyMkgxMy41QzEzLjMyIDIyIDEzLjE4IDIxLjg3IDEzLjE1IDIxLjdMMTIuODkgMTkuODVDMTIuNDYgMTkuNjcgMTIuMDcgMTkuNDQgMTEuNzEgMTkuMTZMOS45NjAwMiAxOS44NkM5LjgxMDAyIDE5LjkyIDkuNjIwMDIgMTkuODYgOS41NDAwMiAxOS43MUw4LjE0MDAyIDE3LjI5QzguMDUwMDIgMTcuMTMgOC4wOTAwMiAxNi45NSA4LjIyMDAyIDE2Ljg0TDkuNzAwMDIgMTUuNjhMOS42NTAwMSAxNUw5LjcwMDAyIDE0LjMxTDguMjIwMDIgMTMuMTZDOC4wOTAwMiAxMy4wNSA4LjA1MDAyIDEyLjg2IDguMTQwMDIgMTIuNzFMOS41NDAwMiAxMC4yOUM5LjYyMDAyIDEwLjEzIDkuODEwMDIgMTAuMDcgOS45NjAwMiAxMC4xM0wxMS43MSAxMC44NEMxMi4wNyAxMC41NiAxMi40NiAxMC4zMiAxMi44OSAxMC4xNUwxMy4xNSA4LjI4OTk4QzEzLjE4IDguMTI5OTggMTMuMzIgNy45OTk5OCAxMy41IDcuOTk5OThIMTYuM0MxNi40NyA3Ljk5OTk4IDE2LjYyIDguMTI5OTggMTYuNjQgOC4yODk5OEwxNi45MSAxMC4xNUMxNy4zMyAxMC4zMiAxNy43MyAxMC41NiAxOC4wOSAxMC44NEwxOS44MyAxMC4xM0MyMCAxMC4wNyAyMC4xNyAxMC4xMyAyMC4yNiAxMC4yOUwyMS42NiAxMi43MUMyMS43NSAxMi44NiAyMS43MSAxMy4wNSAyMS41OCAxMy4xNkwyMC4xIDE0LjMxTDIwLjE1IDE1TDIwLjEgMTUuNjhaIi8+CiAgICA8cGF0aCBkPSJNNy4zMjk2NiA3LjQ0NDU0QzguMDgzMSA3LjAwOTU0IDguMzM5MzIgNi4wNTMzMiA3LjkwNDMyIDUuMjk5ODhDNy40NjkzMiA0LjU0NjQzIDYuNTA4MSA0LjI4MTU2IDUuNzU0NjYgNC43MTY1NkM1LjM5MTc2IDQuOTI2MDggNS4xMjY5NSA1LjI3MTE4IDUuMDE4NDkgNS42NzU5NEM0LjkxMDA0IDYuMDgwNzEgNC45NjY4MiA2LjUxMTk4IDUuMTc2MzQgNi44NzQ4OEM1LjYxMTM0IDcuNjI4MzIgNi41NzYyMiA3Ljg3OTU0IDcuMzI5NjYgNy40NDQ1NFpNOS42NTcxOCA0Ljc5NTkzTDEwLjg2NzIgNC45NTE3OUMxMC45NjI4IDQuOTc3NDEgMTEuMDQwMiA1LjA3MTMzIDExLjAzODIgNS4xODc5M0wxMS4wMzg4IDYuOTg4OTNDMTEuMDQ1NSA3LjEwMDU0IDEwLjk2MTYgNy4xOTUxOCAxMC44NTUgNy4yMTA1NEw5LjY2MDAxIDcuMzgwODNMOS4yMzkxNSA4LjEzMTg4TDkuNjY5NjEgOS4yNTc0NUM5LjcwNzI5IDkuMzYyNzEgOS42NjkzNCA5LjQ3Njk5IDkuNTc0MDggOS41MzE5OUw4LjAxNTIzIDEwLjQzMkM3LjkxMTMxIDEwLjQ5MiA3Ljc5MzM3IDEwLjQ2NzcgNy43MjEwNSAxMC4zODI0TDYuOTg3NDggOS40MzE4OEw2LjEwOTMxIDkuNDMwODNMNS4zNDcwNCAxMC4zOTA1QzUuMjg5MDkgMTAuNDcwMiA1LjE3MzgzIDEwLjQ5MDUgNS4wNzE4NyAxMC40MzM5TDMuNTEyNDUgOS41MzI5M0MzLjQxMDQ5IDkuNDc2MzMgMy4zNzY0NyA5LjM1NzQxIDMuNDEwNzUgOS4yNTY3OUwzLjg2MzQ3IDguMTQwOTNMMy42MTc0OSA3Ljc3NDg4TDMuNDIzNDcgNy4zNzg4M0wyLjIzMDc1IDcuMjEyOTdDMi4xMjY0NyA3LjE5MjM1IDIuMDQwNDkgNy4xMDM0MiAyLjA0MjQ1IDYuOTg2ODJMMi4wNDE4NyA1LjE4NTgyQzIuMDQzODMgNS4wNjkyMiAyLjExOTA5IDQuOTc5NTggMi4yMTcwNCA0Ljk2OTIyTDMuNDIwNjUgNC43OTM5M0wzLjg2NzQ5IDQuMDI3ODhMMy40MTEwNSAyLjkxNzMxQzMuMzczMzcgMi44MTIwNCAzLjQxMTMxIDIuNjk3NzYgMy41MTUyMyAyLjYzNzc2TDUuMDc0MDggMS43Mzc3NkM1LjE2OTM0IDEuNjgyNzYgNS4yODcyOSAxLjcwNzA0IDUuMzU5NjEgMS43OTIzMUw2LjExOTE1IDIuNzI3ODhMNi45ODAwMSAyLjczODkzTDcuNzI0OTYgMS43ODkyMkM3Ljc5MTU2IDEuNzA0NTggNy45MTU0OCAxLjY3OTIyIDguMDA4NzkgMS43NDA4Mkw5LjU2ODIxIDIuNjQxODJDOS42NzAxNyAyLjY5ODQyIDkuNzEyODUgMi44MTIzNCA5LjY4NzIzIDIuOTA3OTdMOS4yMTcxOCA0LjAzMzgzTDkuNDYzMTYgNC4zOTk4OEw5LjY1NzE4IDQuNzk1OTNaIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iOS45LDEzLjYgMy42LDcuNCA0LjQsNi42IDkuOSwxMi4yIDE1LjQsNi43IDE2LjEsNy40ICIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNS45TDksOS43bDMuOC0zLjhsMS4yLDEuMmwtNC45LDVsLTQuOS01TDUuMiw1Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNy41TDksMTEuMmwzLjgtMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-caret-left: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik0xMC44LDEyLjhMNy4xLDlsMy44LTMuOGwwLDcuNkgxMC44eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-caret-right: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik03LjIsNS4yTDEwLjksOWwtMy44LDMuOFY1LjJINy4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-caret-up-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iMTUuNCwxMy4zIDkuOSw3LjcgNC40LDEzLjIgMy42LDEyLjUgOS45LDYuMyAxNi4xLDEyLjYgIi8+Cgk8L2c+Cjwvc3ZnPgo=);
  --jp-icon-caret-up: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik01LjIsMTAuNUw5LDYuOGwzLjgsMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-case-sensitive: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgogIDxnIGNsYXNzPSJqcC1pY29uLWFjY2VudDIiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTcuNiw4aDAuOWwzLjUsOGgtMS4xTDEwLDE0SDZsLTAuOSwySDRMNy42LDh6IE04LDkuMUw2LjQsMTNoMy4yTDgsOS4xeiIvPgogICAgPHBhdGggZD0iTTE2LjYsOS44Yy0wLjIsMC4xLTAuNCwwLjEtMC43LDAuMWMtMC4yLDAtMC40LTAuMS0wLjYtMC4yYy0wLjEtMC4xLTAuMi0wLjQtMC4yLTAuNyBjLTAuMywwLjMtMC42LDAuNS0wLjksMC43Yy0wLjMsMC4xLTAuNywwLjItMS4xLDAuMmMtMC4zLDAtMC41LDAtMC43LTAuMWMtMC4yLTAuMS0wLjQtMC4yLTAuNi0wLjNjLTAuMi0wLjEtMC4zLTAuMy0wLjQtMC41IGMtMC4xLTAuMi0wLjEtMC40LTAuMS0wLjdjMC0wLjMsMC4xLTAuNiwwLjItMC44YzAuMS0wLjIsMC4zLTAuNCwwLjQtMC41QzEyLDcsMTIuMiw2LjksMTIuNSw2LjhjMC4yLTAuMSwwLjUtMC4xLDAuNy0wLjIgYzAuMy0wLjEsMC41LTAuMSwwLjctMC4xYzAuMiwwLDAuNC0wLjEsMC42LTAuMWMwLjIsMCwwLjMtMC4xLDAuNC0wLjJjMC4xLTAuMSwwLjItMC4yLDAuMi0wLjRjMC0xLTEuMS0xLTEuMy0xIGMtMC40LDAtMS40LDAtMS40LDEuMmgtMC45YzAtMC40LDAuMS0wLjcsMC4yLTFjMC4xLTAuMiwwLjMtMC40LDAuNS0wLjZjMC4yLTAuMiwwLjUtMC4zLDAuOC0wLjNDMTMuMyw0LDEzLjYsNCwxMy45LDQgYzAuMywwLDAuNSwwLDAuOCwwLjFjMC4zLDAsMC41LDAuMSwwLjcsMC4yYzAuMiwwLjEsMC40LDAuMywwLjUsMC41QzE2LDUsMTYsNS4yLDE2LDUuNnYyLjljMCwwLjIsMCwwLjQsMCwwLjUgYzAsMC4xLDAuMSwwLjIsMC4zLDAuMmMwLjEsMCwwLjIsMCwwLjMsMFY5Ljh6IE0xNS4yLDYuOWMtMS4yLDAuNi0zLjEsMC4yLTMuMSwxLjRjMCwxLjQsMy4xLDEsMy4xLTAuNVY2Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-check: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik05IDE2LjE3TDQuODMgMTJsLTEuNDIgMS40MUw5IDE5IDIxIDdsLTEuNDEtMS40MXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-circle-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDJDNi40NyAyIDIgNi40NyAyIDEyczQuNDcgMTAgMTAgMTAgMTAtNC40NyAxMC0xMFMxNy41MyAyIDEyIDJ6bTAgMThjLTQuNDEgMC04LTMuNTktOC04czMuNTktOCA4LTggOCAzLjU5IDggOC0zLjU5IDgtOCA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-circle: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iOSIgY3k9IjkiIHI9IjgiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-clear: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8bWFzayBpZD0iZG9udXRIb2xlIj4KICAgIDxyZWN0IHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgZmlsbD0id2hpdGUiIC8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSI4IiBmaWxsPSJibGFjayIvPgogIDwvbWFzaz4KCiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxyZWN0IGhlaWdodD0iMTgiIHdpZHRoPSIyIiB4PSIxMSIgeT0iMyIgdHJhbnNmb3JtPSJyb3RhdGUoMzE1LCAxMiwgMTIpIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIxMCIgbWFzaz0idXJsKCNkb251dEhvbGUpIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-close: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1ub25lIGpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIGpwLWljb24zLWhvdmVyIiBmaWxsPSJub25lIj4KICAgIDxjaXJjbGUgY3g9IjEyIiBjeT0iMTIiIHI9IjExIi8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIGpwLWljb24tYWNjZW50Mi1ob3ZlciIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMTkgNi40MUwxNy41OSA1IDEyIDEwLjU5IDYuNDEgNSA1IDYuNDEgMTAuNTkgMTIgNSAxNy41OSA2LjQxIDE5IDEyIDEzLjQxIDE3LjU5IDE5IDE5IDE3LjU5IDEzLjQxIDEyeiIvPgogIDwvZz4KCiAgPGcgY2xhc3M9ImpwLWljb24tbm9uZSBqcC1pY29uLWJ1c3kiIGZpbGw9Im5vbmUiPgogICAgPGNpcmNsZSBjeD0iMTIiIGN5PSIxMiIgcj0iNyIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-code: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTExLjQgMTguNkw2LjggMTRMMTEuNCA5LjRMMTAgOEw0IDE0TDEwIDIwTDExLjQgMTguNlpNMTYuNiAxOC42TDIxLjIgMTRMMTYuNiA5LjRMMTggOEwyNCAxNEwxOCAyMEwxNi42IDE4LjZWMTguNloiLz4KCTwvZz4KPC9zdmc+Cg==);
  --jp-icon-console: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwMCAyMDAiPgogIDxnIGNsYXNzPSJqcC1pY29uLWJyYW5kMSBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMjg4RDEiPgogICAgPHBhdGggZD0iTTIwIDE5LjhoMTYwdjE1OS45SDIweiIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNmZmYiPgogICAgPHBhdGggZD0iTTEwNSAxMjcuM2g0MHYxMi44aC00MHpNNTEuMSA3N0w3NCA5OS45bC0yMy4zIDIzLjMgMTAuNSAxMC41IDIzLjMtMjMuM0w5NSA5OS45IDg0LjUgODkuNCA2MS42IDY2LjV6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-copy: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTExLjksMUgzLjJDMi40LDEsMS43LDEuNywxLjcsMi41djEwLjJoMS41VjIuNWg4LjdWMXogTTE0LjEsMy45aC04Yy0wLjgsMC0xLjUsMC43LTEuNSwxLjV2MTAuMmMwLDAuOCwwLjcsMS41LDEuNSwxLjVoOCBjMC44LDAsMS41LTAuNywxLjUtMS41VjUuNEMxNS41LDQuNiwxNC45LDMuOSwxNC4xLDMuOXogTTE0LjEsMTUuNWgtOFY1LjRoOFYxNS41eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-copyright: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGVuYWJsZS1iYWNrZ3JvdW5kPSJuZXcgMCAwIDI0IDI0IiBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCI+CiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0xMS44OCw5LjE0YzEuMjgsMC4wNiwxLjYxLDEuMTUsMS42MywxLjY2aDEuNzljLTAuMDgtMS45OC0xLjQ5LTMuMTktMy40NS0zLjE5QzkuNjQsNy42MSw4LDksOCwxMi4xNCBjMCwxLjk0LDAuOTMsNC4yNCwzLjg0LDQuMjRjMi4yMiwwLDMuNDEtMS42NSwzLjQ0LTIuOTVoLTEuNzljLTAuMDMsMC41OS0wLjQ1LDEuMzgtMS42MywxLjQ0QzEwLjU1LDE0LjgzLDEwLDEzLjgxLDEwLDEyLjE0IEMxMCw5LjI1LDExLjI4LDkuMTYsMTEuODgsOS4xNHogTTEyLDJDNi40OCwyLDIsNi40OCwyLDEyczQuNDgsMTAsMTAsMTBzMTAtNC40OCwxMC0xMFMxNy41MiwyLDEyLDJ6IE0xMiwyMGMtNC40MSwwLTgtMy41OS04LTggczMuNTktOCw4LThzOCwzLjU5LDgsOFMxNi40MSwyMCwxMiwyMHoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-cut: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkuNjQgNy42NGMuMjMtLjUuMzYtMS4wNS4zNi0xLjY0IDAtMi4yMS0xLjc5LTQtNC00UzIgMy43OSAyIDZzMS43OSA0IDQgNGMuNTkgMCAxLjE0LS4xMyAxLjY0LS4zNkwxMCAxMmwtMi4zNiAyLjM2QzcuMTQgMTQuMTMgNi41OSAxNCA2IDE0Yy0yLjIxIDAtNCAxLjc5LTQgNHMxLjc5IDQgNCA0IDQtMS43OSA0LTRjMC0uNTktLjEzLTEuMTQtLjM2LTEuNjRMMTIgMTRsNyA3aDN2LTFMOS42NCA3LjY0ek02IDhjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTAgMTJjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTYtNy41Yy0uMjggMC0uNS0uMjItLjUtLjVzLjIyLS41LjUtLjUuNS4yMi41LjUtLjIyLjUtLjUuNXpNMTkgM2wtNiA2IDIgMiA3LTdWM3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-download: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDloLTRWM0g5djZINWw3IDcgNy03ek01IDE4djJoMTR2LTJINXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-edit: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMgMTcuMjVWMjFoMy43NUwxNy44MSA5Ljk0bC0zLjc1LTMuNzVMMyAxNy4yNXpNMjAuNzEgNy4wNGMuMzktLjM5LjM5LTEuMDIgMC0xLjQxbC0yLjM0LTIuMzRjLS4zOS0uMzktMS4wMi0uMzktMS40MSAwbC0xLjgzIDEuODMgMy43NSAzLjc1IDEuODMtMS44M3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-ellipses: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iNSIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxOSIgY3k9IjEyIiByPSIyIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-extension: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwLjUgMTFIMTlWN2MwLTEuMS0uOS0yLTItMmgtNFYzLjVDMTMgMi4xMiAxMS44OCAxIDEwLjUgMVM4IDIuMTIgOCAzLjVWNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAydjMuOEgzLjVjMS40OSAwIDIuNyAxLjIxIDIuNyAyLjdzLTEuMjEgMi43LTIuNyAyLjdIMlYyMGMwIDEuMS45IDIgMiAyaDMuOHYtMS41YzAtMS40OSAxLjIxLTIuNyAyLjctMi43IDEuNDkgMCAyLjcgMS4yMSAyLjcgMi43VjIySDE3YzEuMSAwIDItLjkgMi0ydi00aDEuNWMxLjM4IDAgMi41LTEuMTIgMi41LTIuNVMyMS44OCAxMSAyMC41IDExeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-fast-forward: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTQgMThsOC41LTZMNCA2djEyem05LTEydjEybDguNS02TDEzIDZ6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-file-upload: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkgMTZoNnYtNmg0bC03LTctNyA3aDR6bS00IDJoMTR2Mkg1eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-file: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuMyA4LjJsLTUuNS01LjVjLS4zLS4zLS43LS41LTEuMi0uNUgzLjljLS44LjEtMS42LjktMS42IDEuOHYxNC4xYzAgLjkuNyAxLjYgMS42IDEuNmgxNC4yYy45IDAgMS42LS43IDEuNi0xLjZWOS40Yy4xLS41LS4xLS45LS40LTEuMnptLTUuOC0zLjNsMy40IDMuNmgtMy40VjQuOXptMy45IDEyLjdINC43Yy0uMSAwLS4yIDAtLjItLjJWNC43YzAtLjIuMS0uMy4yLS4zaDcuMnY0LjRzMCAuOC4zIDEuMWMuMy4zIDEuMS4zIDEuMS4zaDQuM3Y3LjJzLS4xLjItLjIuMnoiLz4KPC9zdmc+Cg==);
  --jp-icon-filter-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEwIDE4aDR2LTJoLTR2MnpNMyA2djJoMThWNkgzem0zIDdoMTJ2LTJINnYyeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY4YzAtMS4xLS45LTItMi0yaC04bC0yLTJ6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-html5: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMDAiIGQ9Ik0xMDguNCAwaDIzdjIyLjhoMjEuMlYwaDIzdjY5aC0yM1Y0NmgtMjF2MjNoLTIzLjJNMjA2IDIzaC0yMC4zVjBoNjMuN3YyM0gyMjl2NDZoLTIzbTUzLjUtNjloMjQuMWwxNC44IDI0LjNMMzEzLjIgMGgyNC4xdjY5aC0yM1YzNC44bC0xNi4xIDI0LjgtMTYuMS0yNC44VjY5aC0yMi42bTg5LjItNjloMjN2NDYuMmgzMi42VjY5aC01NS42Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI2U0NGQyNiIgZD0iTTEwNy42IDQ3MWwtMzMtMzcwLjRoMzYyLjhsLTMzIDM3MC4yTDI1NS43IDUxMiIvPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNmMTY1MjkiIGQ9Ik0yNTYgNDgwLjVWMTMxaDE0OC4zTDM3NiA0NDciLz4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNlYmViZWIiIGQ9Ik0xNDIgMTc2LjNoMTE0djQ1LjRoLTY0LjJsNC4yIDQ2LjVoNjB2NDUuM0gxNTQuNG0yIDIyLjhIMjAybDMuMiAzNi4zIDUwLjggMTMuNnY0Ny40bC05My4yLTI2Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIiBmaWxsPSIjZmZmIiBkPSJNMzY5LjYgMTc2LjNIMjU1Ljh2NDUuNGgxMDkuNm0tNC4xIDQ2LjVIMjU1Ljh2NDUuNGg1NmwtNS4zIDU5LTUwLjcgMTMuNnY0Ny4ybDkzLTI1LjgiLz4KPC9zdmc+Cg==);
  --jp-icon-image: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1icmFuZDQganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNGRkYiIGQ9Ik0yLjIgMi4yaDE3LjV2MTcuNUgyLjJ6Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzNGNTFCNSIgZD0iTTIuMiAyLjJ2MTcuNWgxNy41bC4xLTE3LjVIMi4yem0xMi4xIDIuMmMxLjIgMCAyLjIgMSAyLjIgMi4ycy0xIDIuMi0yLjIgMi4yLTIuMi0xLTIuMi0yLjIgMS0yLjIgMi4yLTIuMnpNNC40IDE3LjZsMy4zLTguOCAzLjMgNi42IDIuMi0zLjIgNC40IDUuNEg0LjR6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-inspector: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY2YzAtMS4xLS45LTItMi0yem0tNSAxNEg0di00aDExdjR6bTAtNUg0VjloMTF2NHptNSA1aC00VjloNHY5eiIvPgo8L3N2Zz4K);
  --jp-icon-json: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMSBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNGOUE4MjUiPgogICAgPHBhdGggZD0iTTIwLjIgMTEuOGMtMS42IDAtMS43LjUtMS43IDEgMCAuNC4xLjkuMSAxLjMuMS41LjEuOS4xIDEuMyAwIDEuNy0xLjQgMi4zLTMuNSAyLjNoLS45di0xLjloLjVjMS4xIDAgMS40IDAgMS40LS44IDAtLjMgMC0uNi0uMS0xIDAtLjQtLjEtLjgtLjEtMS4yIDAtMS4zIDAtMS44IDEuMy0yLTEuMy0uMi0xLjMtLjctMS4zLTIgMC0uNC4xLS44LjEtMS4yLjEtLjQuMS0uNy4xLTEgMC0uOC0uNC0uNy0xLjQtLjhoLS41VjQuMWguOWMyLjIgMCAzLjUuNyAzLjUgMi4zIDAgLjQtLjEuOS0uMSAxLjMtLjEuNS0uMS45LS4xIDEuMyAwIC41LjIgMSAxLjcgMXYxLjh6TTEuOCAxMC4xYzEuNiAwIDEuNy0uNSAxLjctMSAwLS40LS4xLS45LS4xLTEuMy0uMS0uNS0uMS0uOS0uMS0xLjMgMC0xLjYgMS40LTIuMyAzLjUtMi4zaC45djEuOWgtLjVjLTEgMC0xLjQgMC0xLjQuOCAwIC4zIDAgLjYuMSAxIDAgLjIuMS42LjEgMSAwIDEuMyAwIDEuOC0xLjMgMkM2IDExLjIgNiAxMS43IDYgMTNjMCAuNC0uMS44LS4xIDEuMi0uMS4zLS4xLjctLjEgMSAwIC44LjMuOCAxLjQuOGguNXYxLjloLS45Yy0yLjEgMC0zLjUtLjYtMy41LTIuMyAwLS40LjEtLjkuMS0xLjMuMS0uNS4xLS45LjEtMS4zIDAtLjUtLjItMS0xLjctMXYtMS45eiIvPgogICAgPGNpcmNsZSBjeD0iMTEiIGN5PSIxMy44IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY3g9IjExIiBjeT0iOC4yIiByPSIyLjEiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-julia: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDMyNSAzMDAiPgogIDxnIGNsYXNzPSJqcC1icmFuZDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjY2IzYzMzIj4KICAgIDxwYXRoIGQ9Ik0gMTUwLjg5ODQzOCAyMjUgQyAxNTAuODk4NDM4IDI2Ni40MjE4NzUgMTE3LjMyMDMxMiAzMDAgNzUuODk4NDM4IDMwMCBDIDM0LjQ3NjU2MiAzMDAgMC44OTg0MzggMjY2LjQyMTg3NSAwLjg5ODQzOCAyMjUgQyAwLjg5ODQzOCAxODMuNTc4MTI1IDM0LjQ3NjU2MiAxNTAgNzUuODk4NDM4IDE1MCBDIDExNy4zMjAzMTIgMTUwIDE1MC44OTg0MzggMTgzLjU3ODEyNSAxNTAuODk4NDM4IDIyNSIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzM4OTgyNiI+CiAgICA8cGF0aCBkPSJNIDIzNy41IDc1IEMgMjM3LjUgMTE2LjQyMTg3NSAyMDMuOTIxODc1IDE1MCAxNjIuNSAxNTAgQyAxMjEuMDc4MTI1IDE1MCA4Ny41IDExNi40MjE4NzUgODcuNSA3NSBDIDg3LjUgMzMuNTc4MTI1IDEyMS4wNzgxMjUgMCAxNjIuNSAwIEMgMjAzLjkyMTg3NSAwIDIzNy41IDMzLjU3ODEyNSAyMzcuNSA3NSIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzk1NThiMiI+CiAgICA8cGF0aCBkPSJNIDMyNC4xMDE1NjIgMjI1IEMgMzI0LjEwMTU2MiAyNjYuNDIxODc1IDI5MC41MjM0MzggMzAwIDI0OS4xMDE1NjIgMzAwIEMgMjA3LjY3OTY4OCAzMDAgMTc0LjEwMTU2MiAyNjYuNDIxODc1IDE3NC4xMDE1NjIgMjI1IEMgMTc0LjEwMTU2MiAxODMuNTc4MTI1IDIwNy42Nzk2ODggMTUwIDI0OS4xMDE1NjIgMTUwIEMgMjkwLjUyMzQzOCAxNTAgMzI0LjEwMTU2MiAxODMuNTc4MTI1IDMyNC4xMDE1NjIgMjI1Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-jupyter-favicon: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTUyIiBoZWlnaHQ9IjE2NSIgdmlld0JveD0iMCAwIDE1MiAxNjUiIHZlcnNpb249IjEuMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA3ODk0NywgMTEwLjU4MjkyNykiIGQ9Ik03NS45NDIyODQyLDI5LjU4MDQ1NjEgQzQzLjMwMjM5NDcsMjkuNTgwNDU2MSAxNC43OTY3ODMyLDE3LjY1MzQ2MzQgMCwwIEM1LjUxMDgzMjExLDE1Ljg0MDY4MjkgMTUuNzgxNTM4OSwyOS41NjY3NzMyIDI5LjM5MDQ5NDcsMzkuMjc4NDE3MSBDNDIuOTk5Nyw0OC45ODk4NTM3IDU5LjI3MzcsNTQuMjA2NzgwNSA3NS45NjA1Nzg5LDU0LjIwNjc4MDUgQzkyLjY0NzQ1NzksNTQuMjA2NzgwNSAxMDguOTIxNDU4LDQ4Ljk4OTg1MzcgMTIyLjUzMDY2MywzOS4yNzg0MTcxIEMxMzYuMTM5NDUzLDI5LjU2Njc3MzIgMTQ2LjQxMDI4NCwxNS44NDA2ODI5IDE1MS45MjExNTgsMCBDMTM3LjA4Nzg2OCwxNy42NTM0NjM0IDEwOC41ODI1ODksMjkuNTgwNDU2MSA3NS45NDIyODQyLDI5LjU4MDQ1NjEgTDc1Ljk0MjI4NDIsMjkuNTgwNDU2MSBaIiAvPgogICAgPHBhdGggdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMzczNjgsIDAuNzA0ODc4KSIgZD0iTTc1Ljk3ODQ1NzksMjQuNjI2NDA3MyBDMTA4LjYxODc2MywyNC42MjY0MDczIDEzNy4xMjQ0NTgsMzYuNTUzNDQxNSAxNTEuOTIxMTU4LDU0LjIwNjc4MDUgQzE0Ni40MTAyODQsMzguMzY2MjIyIDEzNi4xMzk0NTMsMjQuNjQwMTMxNyAxMjIuNTMwNjYzLDE0LjkyODQ4NzggQzEwOC45MjE0NTgsNS4yMTY4NDM5IDkyLjY0NzQ1NzksMCA3NS45NjA1Nzg5LDAgQzU5LjI3MzcsMCA0Mi45OTk3LDUuMjE2ODQzOSAyOS4zOTA0OTQ3LDE0LjkyODQ4NzggQzE1Ljc4MTUzODksMjQuNjQwMTMxNyA1LjUxMDgzMjExLDM4LjM2NjIyMiAwLDU0LjIwNjc4MDUgQzE0LjgzMzA4MTYsMzYuNTg5OTI5MyA0My4zMzg1Njg0LDI0LjYyNjQwNzMgNzUuOTc4NDU3OSwyNC42MjY0MDczIEw3NS45Nzg0NTc5LDI0LjYyNjQwNzMgWiIgLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-jupyter: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMzkiIGhlaWdodD0iNTEiIHZpZXdCb3g9IjAgMCAzOSA1MSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgtMTYzOCAtMjI4MSkiPgogICAgPGcgY2xhc3M9ImpwLWljb24td2FybjAiIGZpbGw9IiNGMzc3MjYiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5Ljc0IDIzMTEuOTgpIiBkPSJNIDE4LjI2NDYgNy4xMzQxMUMgMTAuNDE0NSA3LjEzNDExIDMuNTU4NzIgNC4yNTc2IDAgMEMgMS4zMjUzOSAzLjgyMDQgMy43OTU1NiA3LjEzMDgxIDcuMDY4NiA5LjQ3MzAzQyAxMC4zNDE3IDExLjgxNTIgMTQuMjU1NyAxMy4wNzM0IDE4LjI2OSAxMy4wNzM0QyAyMi4yODIzIDEzLjA3MzQgMjYuMTk2MyAxMS44MTUyIDI5LjQ2OTQgOS40NzMwM0MgMzIuNzQyNCA3LjEzMDgxIDM1LjIxMjYgMy44MjA0IDM2LjUzOCAwQyAzMi45NzA1IDQuMjU3NiAyNi4xMTQ4IDcuMTM0MTEgMTguMjY0NiA3LjEzNDExWiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5LjczIDIyODUuNDgpIiBkPSJNIDE4LjI3MzMgNS45MzkzMUMgMjYuMTIzNSA1LjkzOTMxIDMyLjk3OTMgOC44MTU4MyAzNi41MzggMTMuMDczNEMgMzUuMjEyNiA5LjI1MzAzIDMyLjc0MjQgNS45NDI2MiAyOS40Njk0IDMuNjAwNEMgMjYuMTk2MyAxLjI1ODE4IDIyLjI4MjMgMCAxOC4yNjkgMEMgMTQuMjU1NyAwIDEwLjM0MTcgMS4yNTgxOCA3LjA2ODYgMy42MDA0QyAzLjc5NTU2IDUuOTQyNjIgMS4zMjUzOSA5LjI1MzAzIDAgMTMuMDczNEMgMy41Njc0NSA4LjgyNDYzIDEwLjQyMzIgNS45MzkzMSAxOC4yNzMzIDUuOTM5MzFaIi8+CiAgICA8L2c+CiAgICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjY5LjMgMjI4MS4zMSkiIGQ9Ik0gNS44OTM1MyAyLjg0NEMgNS45MTg4OSAzLjQzMTY1IDUuNzcwODUgNC4wMTM2NyA1LjQ2ODE1IDQuNTE2NDVDIDUuMTY1NDUgNS4wMTkyMiA0LjcyMTY4IDUuNDIwMTUgNC4xOTI5OSA1LjY2ODUxQyAzLjY2NDMgNS45MTY4OCAzLjA3NDQ0IDYuMDAxNTEgMi40OTgwNSA1LjkxMTcxQyAxLjkyMTY2IDUuODIxOSAxLjM4NDYzIDUuNTYxNyAwLjk1NDg5OCA1LjE2NDAxQyAwLjUyNTE3IDQuNzY2MzMgMC4yMjIwNTYgNC4yNDkwMyAwLjA4MzkwMzcgMy42Nzc1N0MgLTAuMDU0MjQ4MyAzLjEwNjExIC0wLjAyMTIzIDIuNTA2MTcgMC4xNzg3ODEgMS45NTM2NEMgMC4zNzg3OTMgMS40MDExIDAuNzM2ODA5IDAuOTIwODE3IDEuMjA3NTQgMC41NzM1MzhDIDEuNjc4MjYgMC4yMjYyNTkgMi4yNDA1NSAwLjAyNzU5MTkgMi44MjMyNiAwLjAwMjY3MjI5QyAzLjYwMzg5IC0wLjAzMDcxMTUgNC4zNjU3MyAwLjI0OTc4OSA0Ljk0MTQyIDAuNzgyNTUxQyA1LjUxNzExIDEuMzE1MzEgNS44NTk1NiAyLjA1Njc2IDUuODkzNTMgMi44NDRaIi8+CiAgICAgIDxwYXRoIHRyYW5zZm9ybT0idHJhbnNsYXRlKDE2MzkuOCAyMzIzLjgxKSIgZD0iTSA3LjQyNzg5IDMuNTgzMzhDIDcuNDYwMDggNC4zMjQzIDcuMjczNTUgNS4wNTgxOSA2Ljg5MTkzIDUuNjkyMTNDIDYuNTEwMzEgNi4zMjYwNyA1Ljk1MDc1IDYuODMxNTYgNS4yODQxMSA3LjE0NDZDIDQuNjE3NDcgNy40NTc2MyAzLjg3MzcxIDcuNTY0MTQgMy4xNDcwMiA3LjQ1MDYzQyAyLjQyMDMyIDcuMzM3MTIgMS43NDMzNiA3LjAwODcgMS4yMDE4NCA2LjUwNjk1QyAwLjY2MDMyOCA2LjAwNTIgMC4yNzg2MSA1LjM1MjY4IDAuMTA1MDE3IDQuNjMyMDJDIC0wLjA2ODU3NTcgMy45MTEzNSAtMC4wMjYyMzYxIDMuMTU0OTQgMC4yMjY2NzUgMi40NTg1NkMgMC40Nzk1ODcgMS43NjIxNyAwLjkzMTY5NyAxLjE1NzEzIDEuNTI1NzYgMC43MjAwMzNDIDIuMTE5ODMgMC4yODI5MzUgMi44MjkxNCAwLjAzMzQzOTUgMy41NjM4OSAwLjAwMzEzMzQ0QyA0LjU0NjY3IC0wLjAzNzQwMzMgNS41MDUyOSAwLjMxNjcwNiA2LjIyOTYxIDAuOTg3ODM1QyA2Ljk1MzkzIDEuNjU4OTYgNy4zODQ4NCAyLjU5MjM1IDcuNDI3ODkgMy41ODMzOEwgNy40Mjc4OSAzLjU4MzM4WiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM4LjM2IDIyODYuMDYpIiBkPSJNIDIuMjc0NzEgNC4zOTYyOUMgMS44NDM2MyA0LjQxNTA4IDEuNDE2NzEgNC4zMDQ0NSAxLjA0Nzk5IDQuMDc4NDNDIDAuNjc5MjY4IDMuODUyNCAwLjM4NTMyOCAzLjUyMTE0IDAuMjAzMzcxIDMuMTI2NTZDIDAuMDIxNDEzNiAyLjczMTk4IC0wLjA0MDM3OTggMi4yOTE4MyAwLjAyNTgxMTYgMS44NjE4MUMgMC4wOTIwMDMxIDEuNDMxOCAwLjI4MzIwNCAxLjAzMTI2IDAuNTc1MjEzIDAuNzEwODgzQyAwLjg2NzIyMiAwLjM5MDUxIDEuMjQ2OTEgMC4xNjQ3MDggMS42NjYyMiAwLjA2MjA1OTJDIDIuMDg1NTMgLTAuMDQwNTg5NyAyLjUyNTYxIC0wLjAxNTQ3MTQgMi45MzA3NiAwLjEzNDIzNUMgMy4zMzU5MSAwLjI4Mzk0MSAzLjY4NzkyIDAuNTUxNTA1IDMuOTQyMjIgMC45MDMwNkMgNC4xOTY1MiAxLjI1NDYyIDQuMzQxNjkgMS42NzQzNiA0LjM1OTM1IDIuMTA5MTZDIDQuMzgyOTkgMi42OTEwNyA0LjE3Njc4IDMuMjU4NjkgMy43ODU5NyAzLjY4NzQ2QyAzLjM5NTE2IDQuMTE2MjQgMi44NTE2NiA0LjM3MTE2IDIuMjc0NzEgNC4zOTYyOUwgMi4yNzQ3MSA0LjM5NjI5WiIvPgogICAgPC9nPgogIDwvZz4+Cjwvc3ZnPgo=);
  --jp-icon-jupyterlab-wordmark: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyMDAiIHZpZXdCb3g9IjAgMCAxODYwLjggNDc1Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0RTRFNEUiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDQ4MC4xMzY0MDEsIDY0LjI3MTQ5MykiPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMDAwMDAsIDU4Ljg3NTU2NikiPgogICAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA4NzYwMywgMC4xNDAyOTQpIj4KICAgICAgICA8cGF0aCBkPSJNLTQyNi45LDE2OS44YzAsNDguNy0zLjcsNjQuNy0xMy42LDc2LjRjLTEwLjgsMTAtMjUsMTUuNS0zOS43LDE1LjVsMy43LDI5IGMyMi44LDAuMyw0NC44LTcuOSw2MS45LTIzLjFjMTcuOC0xOC41LDI0LTQ0LjEsMjQtODMuM1YwSC00Mjd2MTcwLjFMLTQyNi45LDE2OS44TC00MjYuOSwxNjkuOHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTU1LjA0NTI5NiwgNTYuODM3MTA0KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuNTYyNDUzLCAxLjc5OTg0MikiPgogICAgICAgIDxwYXRoIGQ9Ik0tMzEyLDE0OGMwLDIxLDAsMzkuNSwxLjcsNTUuNGgtMzEuOGwtMi4xLTMzLjNoLTAuOGMtNi43LDExLjYtMTYuNCwyMS4zLTI4LDI3LjkgYy0xMS42LDYuNi0yNC44LDEwLTM4LjIsOS44Yy0zMS40LDAtNjktMTcuNy02OS04OVYwaDM2LjR2MTEyLjdjMCwzOC43LDExLjYsNjQuNyw0NC42LDY0LjdjMTAuMy0wLjIsMjAuNC0zLjUsMjguOS05LjQgYzguNS01LjksMTUuMS0xNC4zLDE4LjktMjMuOWMyLjItNi4xLDMuMy0xMi41LDMuMy0xOC45VjAuMmgzNi40VjE0OEgtMzEyTC0zMTIsMTQ4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzOTAuMDEzMzIyLCA1My40Nzk2MzgpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS43MDY0NTgsIDAuMjMxNDI1KSI+CiAgICAgICAgPHBhdGggZD0iTS00NzguNiw3MS40YzAtMjYtMC44LTQ3LTEuNy02Ni43aDMyLjdsMS43LDM0LjhoMC44YzcuMS0xMi41LDE3LjUtMjIuOCwzMC4xLTI5LjcgYzEyLjUtNywyNi43LTEwLjMsNDEtOS44YzQ4LjMsMCw4NC43LDQxLjcsODQuNywxMDMuM2MwLDczLjEtNDMuNywxMDkuMi05MSwxMDkuMmMtMTIuMSwwLjUtMjQuMi0yLjItMzUtNy44IGMtMTAuOC01LjYtMTkuOS0xMy45LTI2LjYtMjQuMmgtMC44VjI5MWgtMzZ2LTIyMEwtNDc4LjYsNzEuNEwtNDc4LjYsNzEuNHogTS00NDIuNiwxMjUuNmMwLjEsNS4xLDAuNiwxMC4xLDEuNywxNS4xIGMzLDEyLjMsOS45LDIzLjMsMTkuOCwzMS4xYzkuOSw3LjgsMjIuMSwxMi4xLDM0LjcsMTIuMWMzOC41LDAsNjAuNy0zMS45LDYwLjctNzguNWMwLTQwLjctMjEuMS03NS42LTU5LjUtNzUuNiBjLTEyLjksMC40LTI1LjMsNS4xLTM1LjMsMTMuNGMtOS45LDguMy0xNi45LDE5LjctMTkuNiwzMi40Yy0xLjUsNC45LTIuMywxMC0yLjUsMTUuMVYxMjUuNkwtNDQyLjYsMTI1LjZMLTQ0Mi42LDEyNS42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSg2MDYuNzQwNzI2LCA1Ni44MzcxMDQpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC43NTEyMjYsIDEuOTg5Mjk5KSI+CiAgICAgICAgPHBhdGggZD0iTS00NDAuOCwwbDQzLjcsMTIwLjFjNC41LDEzLjQsOS41LDI5LjQsMTIuOCw0MS43aDAuOGMzLjctMTIuMiw3LjktMjcuNywxMi44LTQyLjQgbDM5LjctMTE5LjJoMzguNUwtMzQ2LjksMTQ1Yy0yNiw2OS43LTQzLjcsMTA1LjQtNjguNiwxMjcuMmMtMTIuNSwxMS43LTI3LjksMjAtNDQuNiwyMy45bC05LjEtMzEuMSBjMTEuNy0zLjksMjIuNS0xMC4xLDMxLjgtMTguMWMxMy4yLTExLjEsMjMuNy0yNS4yLDMwLjYtNDEuMmMxLjUtMi44LDIuNS01LjcsMi45LTguOGMtMC4zLTMuMy0xLjItNi42LTIuNS05LjdMLTQ4MC4yLDAuMSBoMzkuN0wtNDQwLjgsMEwtNDQwLjgsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoODIyLjc0ODEwNCwgMC4wMDAwMDApIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS40NjQwNTAsIDAuMzc4OTE0KSI+CiAgICAgICAgPHBhdGggZD0iTS00MTMuNywwdjU4LjNoNTJ2MjguMmgtNTJWMTk2YzAsMjUsNywzOS41LDI3LjMsMzkuNWM3LjEsMC4xLDE0LjItMC43LDIxLjEtMi41IGwxLjcsMjcuN2MtMTAuMywzLjctMjEuMyw1LjQtMzIuMiw1Yy03LjMsMC40LTE0LjYtMC43LTIxLjMtMy40Yy02LjgtMi43LTEyLjktNi44LTE3LjktMTIuMWMtMTAuMy0xMC45LTE0LjEtMjktMTQuMS01Mi45IFY4Ni41aC0zMVY1OC4zaDMxVjkuNkwtNDEzLjcsMEwtNDEzLjcsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOTc0LjQzMzI4NiwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuOTkwMDM0LCAwLjYxMDMzOSkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDQ1LjgsMTEzYzAuOCw1MCwzMi4yLDcwLjYsNjguNiw3MC42YzE5LDAuNiwzNy45LTMsNTUuMy0xMC41bDYuMiwyNi40IGMtMjAuOSw4LjktNDMuNSwxMy4xLTY2LjIsMTIuNmMtNjEuNSwwLTk4LjMtNDEuMi05OC4zLTEwMi41Qy00ODAuMiw0OC4yLTQ0NC43LDAtMzg2LjUsMGM2NS4yLDAsODIuNyw1OC4zLDgyLjcsOTUuNyBjLTAuMSw1LjgtMC41LDExLjUtMS4yLDE3LjJoLTE0MC42SC00NDUuOEwtNDQ1LjgsMTEzeiBNLTMzOS4yLDg2LjZjMC40LTIzLjUtOS41LTYwLjEtNTAuNC02MC4xIGMtMzYuOCwwLTUyLjgsMzQuNC01NS43LDYwLjFILTMzOS4yTC0zMzkuMiw4Ni42TC0zMzkuMiw4Ni42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxMjAxLjk2MTA1OCwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuMTc5NjQwLCAwLjcwNTA2OCkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDc4LjYsNjhjMC0yMy45LTAuNC00NC41LTEuNy02My40aDMxLjhsMS4yLDM5LjloMS43YzkuMS0yNy4zLDMxLTQ0LjUsNTUuMy00NC41IGMzLjUtMC4xLDcsMC40LDEwLjMsMS4ydjM0LjhjLTQuMS0wLjktOC4yLTEuMy0xMi40LTEuMmMtMjUuNiwwLTQzLjcsMTkuNy00OC43LDQ3LjRjLTEsNS43LTEuNiwxMS41LTEuNywxNy4ydjEwOC4zaC0zNlY2OCBMLTQ3OC42LDY4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCBkPSJNMTM1Mi4zLDMyNi4yaDM3VjI4aC0zN1YzMjYuMnogTTE2MDQuOCwzMjYuMmMtMi41LTEzLjktMy40LTMxLjEtMy40LTQ4Ljd2LTc2IGMwLTQwLjctMTUuMS04My4xLTc3LjMtODMuMWMtMjUuNiwwLTUwLDcuMS02Ni44LDE4LjFsOC40LDI0LjRjMTQuMy05LjIsMzQtMTUuMSw1My0xNS4xYzQxLjYsMCw0Ni4yLDMwLjIsNDYuMiw0N3Y0LjIgYy03OC42LTAuNC0xMjIuMywyNi41LTEyMi4zLDc1LjZjMCwyOS40LDIxLDU4LjQsNjIuMiw1OC40YzI5LDAsNTAuOS0xNC4zLDYyLjItMzAuMmgxLjNsMi45LDI1LjZIMTYwNC44eiBNMTU2NS43LDI1Ny43IGMwLDMuOC0wLjgsOC0yLjEsMTEuOGMtNS45LDE3LjItMjIuNywzNC00OS4yLDM0Yy0xOC45LDAtMzQuOS0xMS4zLTM0LjktMzUuM2MwLTM5LjUsNDUuOC00Ni42LDg2LjItNDUuOFYyNTcuN3ogTTE2OTguNSwzMjYuMiBsMS43LTMzLjZoMS4zYzE1LjEsMjYuOSwzOC43LDM4LjIsNjguMSwzOC4yYzQ1LjQsMCw5MS4yLTM2LjEsOTEuMi0xMDguOGMwLjQtNjEuNy0zNS4zLTEwMy43LTg1LjctMTAzLjcgYy0zMi44LDAtNTYuMywxNC43LTY5LjMsMzcuNGgtMC44VjI4aC0zNi42djI0NS43YzAsMTguMS0wLjgsMzguNi0xLjcsNTIuNUgxNjk4LjV6IE0xNzA0LjgsMjA4LjJjMC01LjksMS4zLTEwLjksMi4xLTE1LjEgYzcuNi0yOC4xLDMxLjEtNDUuNCw1Ni4zLTQ1LjRjMzkuNSwwLDYwLjUsMzQuOSw2MC41LDc1LjZjMCw0Ni42LTIzLjEsNzguMS02MS44LDc4LjFjLTI2LjksMC00OC4zLTE3LjYtNTUuNS00My4zIGMtMC44LTQuMi0xLjctOC44LTEuNy0xMy40VjIwOC4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgZmlsbD0iIzYxNjE2MSIgZD0iTTE1IDlIOXY2aDZWOXptLTIgNGgtMnYtMmgydjJ6bTgtMlY5aC0yVjdjMC0xLjEtLjktMi0yLTJoLTJWM2gtMnYyaC0yVjNIOXYySDdjLTEuMSAwLTIgLjktMiAydjJIM3YyaDJ2MkgzdjJoMnYyYzAgMS4xLjkgMiAyIDJoMnYyaDJ2LTJoMnYyaDJ2LTJoMmMxLjEgMCAyLS45IDItMnYtMmgydi0yaC0ydi0yaDJ6bS00IDZIN1Y3aDEwdjEweiIvPgo8L3N2Zz4K);
  --jp-icon-keyboard: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMTdjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY3YzAtMS4xLS45LTItMi0yem0tOSAzaDJ2MmgtMlY4em0wIDNoMnYyaC0ydi0yek04IDhoMnYySDhWOHptMCAzaDJ2Mkg4di0yem0tMSAySDV2LTJoMnYyem0wLTNINVY4aDJ2MnptOSA3SDh2LTJoOHYyem0wLTRoLTJ2LTJoMnYyem0wLTNoLTJWOGgydjJ6bTMgM2gtMnYtMmgydjJ6bTAtM2gtMlY4aDJ2MnoiLz4KPC9zdmc+Cg==);
  --jp-icon-launcher: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkgMTlINVY1aDdWM0g1YTIgMiAwIDAwLTIgMnYxNGEyIDIgMCAwMDIgMmgxNGMxLjEgMCAyLS45IDItMnYtN2gtMnY3ek0xNCAzdjJoMy41OWwtOS44MyA5LjgzIDEuNDEgMS40MUwxOSA2LjQxVjEwaDJWM2gtN3oiLz4KPC9zdmc+Cg==);
  --jp-icon-line-form: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGZpbGw9IndoaXRlIiBkPSJNNS44OCA0LjEyTDEzLjc2IDEybC03Ljg4IDcuODhMOCAyMmwxMC0xMEw4IDJ6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-link: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMuOSAxMmMwLTEuNzEgMS4zOS0zLjEgMy4xLTMuMWg0VjdIN2MtMi43NiAwLTUgMi4yNC01IDVzMi4yNCA1IDUgNWg0di0xLjlIN2MtMS43MSAwLTMuMS0xLjM5LTMuMS0zLjF6TTggMTNoOHYtMkg4djJ6bTktNmgtNHYxLjloNGMxLjcxIDAgMy4xIDEuMzkgMy4xIDMuMXMtMS4zOSAzLjEtMy4xIDMuMWgtNFYxN2g0YzIuNzYgMCA1LTIuMjQgNS01cy0yLjI0LTUtNS01eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xOSA1djE0SDVWNWgxNG0xLjEtMkgzLjljLS41IDAtLjkuNC0uOS45djE2LjJjMCAuNC40LjkuOS45aDE2LjJjLjQgMCAuOS0uNS45LS45VjMuOWMwLS41LS41LS45LS45LS45ek0xMSA3aDZ2MmgtNlY3em0wIDRoNnYyaC02di0yem0wIDRoNnYyaC02ek03IDdoMnYySDd6bTAgNGgydjJIN3ptMCA0aDJ2Mkg3eiIvPgo8L3N2Zz4=);
  --jp-icon-listings-info: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA1MC45NzggNTAuOTc4IiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCA1MC45NzggNTAuOTc4OyIgeG1sOnNwYWNlPSJwcmVzZXJ2ZSI+Cgk8Zz4KCQk8cGF0aCBzdHlsZT0iZmlsbDojMDEwMDAyOyIgZD0iTTQzLjUyLDcuNDU4QzM4LjcxMSwyLjY0OCwzMi4zMDcsMCwyNS40ODksMEMxOC42NywwLDEyLjI2NiwyLjY0OCw3LjQ1OCw3LjQ1OAoJCQljLTkuOTQzLDkuOTQxLTkuOTQzLDI2LjExOSwwLDM2LjA2MmM0LjgwOSw0LjgwOSwxMS4yMTIsNy40NTYsMTguMDMxLDcuNDU4YzAsMCwwLjAwMSwwLDAuMDAyLDAKCQkJYzYuODE2LDAsMTMuMjIxLTIuNjQ4LDE4LjAyOS03LjQ1OGM0LjgwOS00LjgwOSw3LjQ1Ny0xMS4yMTIsNy40NTctMTguMDNDNTAuOTc3LDE4LjY3LDQ4LjMyOCwxMi4yNjYsNDMuNTIsNy40NTh6CgkJCSBNNDIuMTA2LDQyLjEwNWMtNC40MzIsNC40MzEtMTAuMzMyLDYuODcyLTE2LjYxNSw2Ljg3MmgtMC4wMDJjLTYuMjg1LTAuMDAxLTEyLjE4Ny0yLjQ0MS0xNi42MTctNi44NzIKCQkJYy05LjE2Mi05LjE2My05LjE2Mi0yNC4wNzEsMC0zMy4yMzNDMTMuMzAzLDQuNDQsMTkuMjA0LDIsMjUuNDg5LDJjNi4yODQsMCwxMi4xODYsMi40NCwxNi42MTcsNi44NzIKCQkJYzQuNDMxLDQuNDMxLDYuODcxLDEwLjMzMiw2Ljg3MSwxNi42MTdDNDguOTc3LDMxLjc3Miw0Ni41MzYsMzcuNjc1LDQyLjEwNiw0Mi4xMDV6Ii8+CgkJPHBhdGggc3R5bGU9ImZpbGw6IzAxMDAwMjsiIGQ9Ik0yMy41NzgsMzIuMjE4Yy0wLjAyMy0xLjczNCwwLjE0My0zLjA1OSwwLjQ5Ni0zLjk3MmMwLjM1My0wLjkxMywxLjExLTEuOTk3LDIuMjcyLTMuMjUzCgkJCWMwLjQ2OC0wLjUzNiwwLjkyMy0xLjA2MiwxLjM2Ny0xLjU3NWMwLjYyNi0wLjc1MywxLjEwNC0xLjQ3OCwxLjQzNi0yLjE3NWMwLjMzMS0wLjcwNywwLjQ5NS0xLjU0MSwwLjQ5NS0yLjUKCQkJYzAtMS4wOTYtMC4yNi0yLjA4OC0wLjc3OS0yLjk3OWMtMC41NjUtMC44NzktMS41MDEtMS4zMzYtMi44MDYtMS4zNjljLTEuODAyLDAuMDU3LTIuOTg1LDAuNjY3LTMuNTUsMS44MzIKCQkJYy0wLjMwMSwwLjUzNS0wLjUwMywxLjE0MS0wLjYwNywxLjgxNGMtMC4xMzksMC43MDctMC4yMDcsMS40MzItMC4yMDcsMi4xNzRoLTIuOTM3Yy0wLjA5MS0yLjIwOCwwLjQwNy00LjExNCwxLjQ5My01LjcxOQoJCQljMS4wNjItMS42NCwyLjg1NS0yLjQ4MSw1LjM3OC0yLjUyN2MyLjE2LDAuMDIzLDMuODc0LDAuNjA4LDUuMTQxLDEuNzU4YzEuMjc4LDEuMTYsMS45MjksMi43NjQsMS45NSw0LjgxMQoJCQljMCwxLjE0Mi0wLjEzNywyLjExMS0wLjQxLDIuOTExYy0wLjMwOSwwLjg0NS0wLjczMSwxLjU5My0xLjI2OCwyLjI0M2MtMC40OTIsMC42NS0xLjA2OCwxLjMxOC0xLjczLDIuMDAyCgkJCWMtMC42NSwwLjY5Ny0xLjMxMywxLjQ3OS0xLjk4NywyLjM0NmMtMC4yMzksMC4zNzctMC40MjksMC43NzctMC41NjUsMS4xOTljLTAuMTYsMC45NTktMC4yMTcsMS45NTEtMC4xNzEsMi45NzkKCQkJQzI2LjU4OSwzMi4yMTgsMjMuNTc4LDMyLjIxOCwyMy41NzgsMzIuMjE4eiBNMjMuNTc4LDM4LjIydi0zLjQ4NGgzLjA3NnYzLjQ4NEgyMy41Nzh6Ii8+Cgk8L2c+Cjwvc3ZnPgo=);
  --jp-icon-markdown: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjN0IxRkEyIiBkPSJNNSAxNC45aDEybC02LjEgNnptOS40LTYuOGMwLTEuMy0uMS0yLjktLjEtNC41LS40IDEuNC0uOSAyLjktMS4zIDQuM2wtMS4zIDQuM2gtMkw4LjUgNy45Yy0uNC0xLjMtLjctMi45LTEtNC4zLS4xIDEuNi0uMSAzLjItLjIgNC42TDcgMTIuNEg0LjhsLjctMTFoMy4zTDEwIDVjLjQgMS4yLjcgMi43IDEgMy45LjMtMS4yLjctMi42IDEtMy45bDEuMi0zLjdoMy4zbC42IDExaC0yLjRsLS4zLTQuMnoiLz4KPC9zdmc+Cg==);
  --jp-icon-new-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwIDZoLThsLTItMkg0Yy0xLjExIDAtMS45OS44OS0xLjk5IDJMMiAxOGMwIDEuMTEuODkgMiAyIDJoMTZjMS4xMSAwIDItLjg5IDItMlY4YzAtMS4xMS0uODktMi0yLTJ6bS0xIDhoLTN2M2gtMnYtM2gtM3YtMmgzVjloMnYzaDN2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-not-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI1IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDMgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMTkgMTcuMTg0NCAyLjk2OTY4IDE0LjMwMzIgMS44NjA5NCAxMS40NDA5WiIvPgogICAgPHBhdGggY2xhc3M9ImpwLWljb24yIiBzdHJva2U9IiMzMzMzMzMiIHN0cm9rZS13aWR0aD0iMiIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOS4zMTU5MiA5LjMyMDMxKSIgZD0iTTcuMzY4NDIgMEwwIDcuMzY0NzkiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDkuMzE1OTIgMTYuNjgzNikgc2NhbGUoMSAtMSkiIGQ9Ik03LjM2ODQyIDBMMCA3LjM2NDc5Ii8+Cjwvc3ZnPgo=);
  --jp-icon-notebook: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNFRjZDMDAiPgogICAgPHBhdGggZD0iTTE4LjcgMy4zdjE1LjRIMy4zVjMuM2gxNS40bTEuNS0xLjVIMS44djE4LjNoMTguM2wuMS0xOC4zeiIvPgogICAgPHBhdGggZD0iTTE2LjUgMTYuNWwtNS40LTQuMy01LjYgNC4zdi0xMWgxMXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-numbering: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTQgMTlINlYxOS41SDVWMjAuNUg2VjIxSDRWMjJIN1YxOEg0VjE5Wk01IDEwSDZWNkg0VjdINVYxMFpNNCAxM0g1LjhMNCAxNS4xVjE2SDdWMTVINS4yTDcgMTIuOVYxMkg0VjEzWk05IDdWOUgyM1Y3SDlaTTkgMjFIMjNWMTlIOVYyMVpNOSAxNUgyM1YxM0g5VjE1WiIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-offline-bolt: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDIuMDJjLTUuNTEgMC05Ljk4IDQuNDctOS45OCA5Ljk4czQuNDcgOS45OCA5Ljk4IDkuOTggOS45OC00LjQ3IDkuOTgtOS45OFMxNy41MSAyLjAyIDEyIDIuMDJ6TTExLjQ4IDIwdi02LjI2SDhMMTMgNHY2LjI2aDMuMzVMMTEuNDggMjB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-palette: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE4IDEzVjIwSDRWNkg5LjAyQzkuMDcgNS4yOSA5LjI0IDQuNjIgOS41IDRINEMyLjkgNCAyIDQuOSAyIDZWMjBDMiAyMS4xIDIuOSAyMiA0IDIySDE4QzE5LjEgMjIgMjAgMjEuMSAyMCAyMFYxNUwxOCAxM1pNMTkuMyA4Ljg5QzE5Ljc0IDguMTkgMjAgNy4zOCAyMCA2LjVDMjAgNC4wMSAxNy45OSAyIDE1LjUgMkMxMy4wMSAyIDExIDQuMDEgMTEgNi41QzExIDguOTkgMTMuMDEgMTEgMTUuNDkgMTFDMTYuMzcgMTEgMTcuMTkgMTAuNzQgMTcuODggMTAuM0wyMSAxMy40MkwyMi40MiAxMkwxOS4zIDguODlaTTE1LjUgOUMxNC4xMiA5IDEzIDcuODggMTMgNi41QzEzIDUuMTIgMTQuMTIgNCAxNS41IDRDMTYuODggNCAxOCA1LjEyIDE4IDYuNUMxOCA3Ljg4IDE2Ljg4IDkgMTUuNSA5WiIvPgogICAgPHBhdGggZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIGQ9Ik00IDZIOS4wMTg5NEM5LjAwNjM5IDYuMTY1MDIgOSA2LjMzMTc2IDkgNi41QzkgOC44MTU3NyAxMC4yMTEgMTAuODQ4NyAxMi4wMzQzIDEySDlWMTRIMTZWMTIuOTgxMUMxNi41NzAzIDEyLjkzNzcgMTcuMTIgMTIuODIwNyAxNy42Mzk2IDEyLjYzOTZMMTggMTNWMjBINFY2Wk04IDhINlYxMEg4VjhaTTYgMTJIOFYxNEg2VjEyWk04IDE2SDZWMThIOFYxNlpNOSAxNkgxNlYxOEg5VjE2WiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-paste: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE5IDJoLTQuMThDMTQuNC44NCAxMy4zIDAgMTIgMGMtMS4zIDAtMi40Ljg0LTIuODIgMkg1Yy0xLjEgMC0yIC45LTIgMnYxNmMwIDEuMS45IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjRjMC0xLjEtLjktMi0yLTJ6bS03IDBjLjU1IDAgMSAuNDUgMSAxcy0uNDUgMS0xIDEtMS0uNDUtMS0xIC40NS0xIDEtMXptNyAxOEg1VjRoMnYzaDEwVjRoMnYxNnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-pdf: url(data:image/svg+xml;base64,PHN2ZwogICB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyMiAyMiIgd2lkdGg9IjE2Ij4KICAgIDxwYXRoIHRyYW5zZm9ybT0icm90YXRlKDQ1KSIgY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI0ZGMkEyQSIKICAgICAgIGQ9Im0gMjIuMzQ0MzY5LC0zLjAxNjM2NDIgaCA1LjYzODYwNCB2IDEuNTc5MjQzMyBoIC0zLjU0OTIyNyB2IDEuNTA4NjkyOTkgaCAzLjMzNzU3NiBWIDEuNjUwODE1NCBoIC0zLjMzNzU3NiB2IDMuNDM1MjYxMyBoIC0yLjA4OTM3NyB6IG0gLTcuMTM2NDQ0LDEuNTc5MjQzMyB2IDQuOTQzOTU0MyBoIDAuNzQ4OTIgcSAxLjI4MDc2MSwwIDEuOTUzNzAzLC0wLjYzNDk1MzUgMC42NzgzNjksLTAuNjM0OTUzNSAwLjY3ODM2OSwtMS44NDUxNjQxIDAsLTEuMjA0NzgzNTUgLTAuNjcyOTQyLC0xLjgzNDMxMDExIC0wLjY3Mjk0MiwtMC42Mjk1MjY1OSAtMS45NTkxMywtMC42Mjk1MjY1OSB6IG0gLTIuMDg5Mzc3LC0xLjU3OTI0MzMgaCAyLjIwMzM0MyBxIDEuODQ1MTY0LDAgMi43NDYwMzksMC4yNjU5MjA3IDAuOTA2MzAxLDAuMjYwNDkzNyAxLjU1MjEwOCwwLjg5MDAyMDMgMC41Njk4MywwLjU0ODEyMjMgMC44NDY2MDUsMS4yNjQ0ODAwNiAwLjI3Njc3NCwwLjcxNjM1NzgxIDAuMjc2Nzc0LDEuNjIyNjU4OTQgMCwwLjkxNzE1NTEgLTAuMjc2Nzc0LDEuNjM4OTM5OSAtMC4yNzY3NzUsMC43MTYzNTc4IC0wLjg0NjYwNSwxLjI2NDQ4IC0wLjY1MTIzNCwwLjYyOTUyNjYgLTEuNTYyOTYyLDAuODk1NDQ3MyAtMC45MTE3MjgsMC4yNjA0OTM3IC0yLjczNTE4NSwwLjI2MDQ5MzcgaCAtMi4yMDMzNDMgeiBtIC04LjE0NTg1NjUsMCBoIDMuNDY3ODIzIHEgMS41NDY2ODE2LDAgMi4zNzE1Nzg1LDAuNjg5MjIzIDAuODMwMzI0LDAuNjgzNzk2MSAwLjgzMDMyNCwxLjk1MzcwMzE0IDAsMS4yNzUzMzM5NyAtMC44MzAzMjQsMS45NjQ1NTcwNiBRIDkuOTg3MTk2MSwyLjI3NDkxNSA4LjQ0MDUxNDUsMi4yNzQ5MTUgSCA3LjA2MjA2ODQgViA1LjA4NjA3NjcgSCA0Ljk3MjY5MTUgWiBtIDIuMDg5Mzc2OSwxLjUxNDExOTkgdiAyLjI2MzAzOTQzIGggMS4xNTU5NDEgcSAwLjYwNzgxODgsMCAwLjkzODg2MjksLTAuMjkzMDU1NDcgMC4zMzEwNDQxLC0wLjI5ODQ4MjQxIDAuMzMxMDQ0MSwtMC44NDExNzc3MiAwLC0wLjU0MjY5NTMxIC0wLjMzMTA0NDEsLTAuODM1NzUwNzQgLTAuMzMxMDQ0MSwtMC4yOTMwNTU1IC0wLjkzODg2MjksLTAuMjkzMDU1NSB6IgovPgo8L3N2Zz4K);
  --jp-icon-python: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1icmFuZDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMEQ0N0ExIj4KICAgIDxwYXRoIGQ9Ik0xMS4xIDYuOVY1LjhINi45YzAtLjUgMC0xLjMuMi0xLjYuNC0uNy44LTEuMSAxLjctMS40IDEuNy0uMyAyLjUtLjMgMy45LS4xIDEgLjEgMS45LjkgMS45IDEuOXY0LjJjMCAuNS0uOSAxLjYtMiAxLjZIOC44Yy0xLjUgMC0yLjQgMS40LTIuNCAyLjh2Mi4ySDQuN0MzLjUgMTUuMSAzIDE0IDMgMTMuMVY5Yy0uMS0xIC42LTIgMS44LTIgMS41LS4xIDYuMy0uMSA2LjMtLjF6Ii8+CiAgICA8cGF0aCBkPSJNMTAuOSAxNS4xdjEuMWg0LjJjMCAuNSAwIDEuMy0uMiAxLjYtLjQuNy0uOCAxLjEtMS43IDEuNC0xLjcuMy0yLjUuMy0zLjkuMS0xLS4xLTEuOS0uOS0xLjktMS45di00LjJjMC0uNS45LTEuNiAyLTEuNmgzLjhjMS41IDAgMi40LTEuNCAyLjQtMi44VjYuNmgxLjdDMTguNSA2LjkgMTkgOCAxOSA4LjlWMTNjMCAxLS43IDIuMS0xLjkgMi4xaC02LjJ6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-r-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjE5NkYzIiBkPSJNNC40IDIuNWMxLjItLjEgMi45LS4zIDQuOS0uMyAyLjUgMCA0LjEuNCA1LjIgMS4zIDEgLjcgMS41IDEuOSAxLjUgMy41IDAgMi0xLjQgMy41LTIuOSA0LjEgMS4yLjQgMS43IDEuNiAyLjIgMyAuNiAxLjkgMSAzLjkgMS4zIDQuNmgtMy44Yy0uMy0uNC0uOC0xLjctMS4yLTMuN3MtMS4yLTIuNi0yLjYtMi42aC0uOXY2LjRINC40VjIuNXptMy43IDYuOWgxLjRjMS45IDAgMi45LS45IDIuOS0yLjNzLTEtMi4zLTIuOC0yLjNjLS43IDAtMS4zIDAtMS42LjJ2NC41aC4xdi0uMXoiLz4KPC9zdmc+Cg==);
  --jp-icon-react: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMTUwIDE1MCA1NDEuOSAyOTUuMyI+CiAgPGcgY2xhc3M9ImpwLWljb24tYnJhbmQyIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzYxREFGQiI+CiAgICA8cGF0aCBkPSJNNjY2LjMgMjk2LjVjMC0zMi41LTQwLjctNjMuMy0xMDMuMS04Mi40IDE0LjQtNjMuNiA4LTExNC4yLTIwLjItMTMwLjQtNi41LTMuOC0xNC4xLTUuNi0yMi40LTUuNnYyMi4zYzQuNiAwIDguMy45IDExLjQgMi42IDEzLjYgNy44IDE5LjUgMzcuNSAxNC45IDc1LjctMS4xIDkuNC0yLjkgMTkuMy01LjEgMjkuNC0xOS42LTQuOC00MS04LjUtNjMuNS0xMC45LTEzLjUtMTguNS0yNy41LTM1LjMtNDEuNi01MCAzMi42LTMwLjMgNjMuMi00Ni45IDg0LTQ2LjlWNzhjLTI3LjUgMC02My41IDE5LjYtOTkuOSA1My42LTM2LjQtMzMuOC03Mi40LTUzLjItOTkuOS01My4ydjIyLjNjMjAuNyAwIDUxLjQgMTYuNSA4NCA0Ni42LTE0IDE0LjctMjggMzEuNC00MS4zIDQ5LjktMjIuNiAyLjQtNDQgNi4xLTYzLjYgMTEtMi4zLTEwLTQtMTkuNy01LjItMjktNC43LTM4LjIgMS4xLTY3LjkgMTQuNi03NS44IDMtMS44IDYuOS0yLjYgMTEuNS0yLjZWNzguNWMtOC40IDAtMTYgMS44LTIyLjYgNS42LTI4LjEgMTYuMi0zNC40IDY2LjctMTkuOSAxMzAuMS02Mi4yIDE5LjItMTAyLjcgNDkuOS0xMDIuNyA4Mi4zIDAgMzIuNSA0MC43IDYzLjMgMTAzLjEgODIuNC0xNC40IDYzLjYtOCAxMTQuMiAyMC4yIDEzMC40IDYuNSAzLjggMTQuMSA1LjYgMjIuNSA1LjYgMjcuNSAwIDYzLjUtMTkuNiA5OS45LTUzLjYgMzYuNCAzMy44IDcyLjQgNTMuMiA5OS45IDUzLjIgOC40IDAgMTYtMS44IDIyLjYtNS42IDI4LjEtMTYuMiAzNC40LTY2LjcgMTkuOS0xMzAuMSA2Mi0xOS4xIDEwMi41LTQ5LjkgMTAyLjUtODIuM3ptLTEzMC4yLTY2LjdjLTMuNyAxMi45LTguMyAyNi4yLTEzLjUgMzkuNS00LjEtOC04LjQtMTYtMTMuMS0yNC00LjYtOC05LjUtMTUuOC0xNC40LTIzLjQgMTQuMiAyLjEgMjcuOSA0LjcgNDEgNy45em0tNDUuOCAxMDYuNWMtNy44IDEzLjUtMTUuOCAyNi4zLTI0LjEgMzguMi0xNC45IDEuMy0zMCAyLTQ1LjIgMi0xNS4xIDAtMzAuMi0uNy00NS0xLjktOC4zLTExLjktMTYuNC0yNC42LTI0LjItMzgtNy42LTEzLjEtMTQuNS0yNi40LTIwLjgtMzkuOCA2LjItMTMuNCAxMy4yLTI2LjggMjAuNy0zOS45IDcuOC0xMy41IDE1LjgtMjYuMyAyNC4xLTM4LjIgMTQuOS0xLjMgMzAtMiA0NS4yLTIgMTUuMSAwIDMwLjIuNyA0NSAxLjkgOC4zIDExLjkgMTYuNCAyNC42IDI0LjIgMzggNy42IDEzLjEgMTQuNSAyNi40IDIwLjggMzkuOC02LjMgMTMuNC0xMy4yIDI2LjgtMjAuNyAzOS45em0zMi4zLTEzYzUuNCAxMy40IDEwIDI2LjggMTMuOCAzOS44LTEzLjEgMy4yLTI2LjkgNS45LTQxLjIgOCA0LjktNy43IDkuOC0xNS42IDE0LjQtMjMuNyA0LjYtOCA4LjktMTYuMSAxMy0yNC4xek00MjEuMiA0MzBjLTkuMy05LjYtMTguNi0yMC4zLTI3LjgtMzIgOSAuNCAxOC4yLjcgMjcuNS43IDkuNCAwIDE4LjctLjIgMjcuOC0uNy05IDExLjctMTguMyAyMi40LTI3LjUgMzJ6bS03NC40LTU4LjljLTE0LjItMi4xLTI3LjktNC43LTQxLTcuOSAzLjctMTIuOSA4LjMtMjYuMiAxMy41LTM5LjUgNC4xIDggOC40IDE2IDEzLjEgMjQgNC43IDggOS41IDE1LjggMTQuNCAyMy40ek00MjAuNyAxNjNjOS4zIDkuNiAxOC42IDIwLjMgMjcuOCAzMi05LS40LTE4LjItLjctMjcuNS0uNy05LjQgMC0xOC43LjItMjcuOC43IDktMTEuNyAxOC4zLTIyLjQgMjcuNS0zMnptLTc0IDU4LjljLTQuOSA3LjctOS44IDE1LjYtMTQuNCAyMy43LTQuNiA4LTguOSAxNi0xMyAyNC01LjQtMTMuNC0xMC0yNi44LTEzLjgtMzkuOCAxMy4xLTMuMSAyNi45LTUuOCA0MS4yLTcuOXptLTkwLjUgMTI1LjJjLTM1LjQtMTUuMS01OC4zLTM0LjktNTguMy01MC42IDAtMTUuNyAyMi45LTM1LjYgNTguMy01MC42IDguNi0zLjcgMTgtNyAyNy43LTEwLjEgNS43IDE5LjYgMTMuMiA0MCAyMi41IDYwLjktOS4yIDIwLjgtMTYuNiA0MS4xLTIyLjIgNjAuNi05LjktMy4xLTE5LjMtNi41LTI4LTEwLjJ6TTMxMCA0OTBjLTEzLjYtNy44LTE5LjUtMzcuNS0xNC45LTc1LjcgMS4xLTkuNCAyLjktMTkuMyA1LjEtMjkuNCAxOS42IDQuOCA0MSA4LjUgNjMuNSAxMC45IDEzLjUgMTguNSAyNy41IDM1LjMgNDEuNiA1MC0zMi42IDMwLjMtNjMuMiA0Ni45LTg0IDQ2LjktNC41LS4xLTguMy0xLTExLjMtMi43em0yMzcuMi03Ni4yYzQuNyAzOC4yLTEuMSA2Ny45LTE0LjYgNzUuOC0zIDEuOC02LjkgMi42LTExLjUgMi42LTIwLjcgMC01MS40LTE2LjUtODQtNDYuNiAxNC0xNC43IDI4LTMxLjQgNDEuMy00OS45IDIyLjYtMi40IDQ0LTYuMSA2My42LTExIDIuMyAxMC4xIDQuMSAxOS44IDUuMiAyOS4xem0zOC41LTY2LjdjLTguNiAzLjctMTggNy0yNy43IDEwLjEtNS43LTE5LjYtMTMuMi00MC0yMi41LTYwLjkgOS4yLTIwLjggMTYuNi00MS4xIDIyLjItNjAuNiA5LjkgMy4xIDE5LjMgNi41IDI4LjEgMTAuMiAzNS40IDE1LjEgNTguMyAzNC45IDU4LjMgNTAuNi0uMSAxNS43LTIzIDM1LjYtNTguNCA1MC42ek0zMjAuOCA3OC40eiIvPgogICAgPGNpcmNsZSBjeD0iNDIwLjkiIGN5PSIyOTYuNSIgcj0iNDUuNyIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-redo: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCBkPSJNMCAwaDI0djI0SDB6IiBmaWxsPSJub25lIi8+PHBhdGggZD0iTTE4LjQgMTAuNkMxNi41NSA4Ljk5IDE0LjE1IDggMTEuNSA4Yy00LjY1IDAtOC41OCAzLjAzLTkuOTYgNy4yMkwzLjkgMTZjMS4wNS0zLjE5IDQuMDUtNS41IDcuNi01LjUgMS45NSAwIDMuNzMuNzIgNS4xMiAxLjg4TDEzIDE2aDlWN2wtMy42IDMuNnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-refresh: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTkgMTMuNWMtMi40OSAwLTQuNS0yLjAxLTQuNS00LjVTNi41MSA0LjUgOSA0LjVjMS4yNCAwIDIuMzYuNTIgMy4xNyAxLjMzTDEwIDhoNVYzbC0xLjc2IDEuNzZDMTIuMTUgMy42OCAxMC42NiAzIDkgMyA1LjY5IDMgMy4wMSA1LjY5IDMuMDEgOVM1LjY5IDE1IDkgMTVjMi45NyAwIDUuNDMtMi4xNiA1LjktNWgtMS41MmMtLjQ2IDItMi4yNCAzLjUtNC4zOCAzLjV6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-regex: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi1hY2NlbnQyIiBmaWxsPSIjRkZGIj4KICAgIDxjaXJjbGUgY2xhc3M9InN0MiIgY3g9IjUuNSIgY3k9IjE0LjUiIHI9IjEuNSIvPgogICAgPHJlY3QgeD0iMTIiIHk9IjQiIGNsYXNzPSJzdDIiIHdpZHRoPSIxIiBoZWlnaHQ9IjgiLz4KICAgIDxyZWN0IHg9IjguNSIgeT0iNy41IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjg2NiAtMC41IDAuNSAwLjg2NiAtMi4zMjU1IDcuMzIxOSkiIGNsYXNzPSJzdDIiIHdpZHRoPSI4IiBoZWlnaHQ9IjEiLz4KICAgIDxyZWN0IHg9IjEyIiB5PSI0IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjUgLTAuODY2IDAuODY2IDAuNSAtMC42Nzc5IDE0LjgyNTIpIiBjbGFzcz0ic3QyIiB3aWR0aD0iMSIgaGVpZ2h0PSI4Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-run: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTggNXYxNGwxMS03eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-running: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMjU2IDhDMTE5IDggOCAxMTkgOCAyNTZzMTExIDI0OCAyNDggMjQ4IDI0OC0xMTEgMjQ4LTI0OFMzOTMgOCAyNTYgOHptOTYgMzI4YzAgOC44LTcuMiAxNi0xNiAxNkgxNzZjLTguOCAwLTE2LTcuMi0xNi0xNlYxNzZjMC04LjggNy4yLTE2IDE2LTE2aDE2MGM4LjggMCAxNiA3LjIgMTYgMTZ2MTYweiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-save: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE3IDNINWMtMS4xMSAwLTIgLjktMiAydjE0YzAgMS4xLjg5IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjdsLTQtNHptLTUgMTZjLTEuNjYgMC0zLTEuMzQtMy0zczEuMzQtMyAzLTMgMyAxLjM0IDMgMy0xLjM0IDMtMyAzem0zLTEwSDVWNWgxMHY0eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-search: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjEsMTAuOWgtMC43bC0wLjItMC4yYzAuOC0wLjksMS4zLTIuMiwxLjMtMy41YzAtMy0yLjQtNS40LTUuNC01LjRTMS44LDQuMiwxLjgsNy4xczIuNCw1LjQsNS40LDUuNCBjMS4zLDAsMi41LTAuNSwzLjUtMS4zbDAuMiwwLjJ2MC43bDQuMSw0LjFsMS4yLTEuMkwxMi4xLDEwLjl6IE03LjEsMTAuOWMtMi4xLDAtMy43LTEuNy0zLjctMy43czEuNy0zLjcsMy43LTMuN3MzLjcsMS43LDMuNywzLjcgUzkuMiwxMC45LDcuMSwxMC45eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-settings: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuNDMgMTIuOThjLjA0LS4zMi4wNy0uNjQuMDctLjk4cy0uMDMtLjY2LS4wNy0uOThsMi4xMS0xLjY1Yy4xOS0uMTUuMjQtLjQyLjEyLS42NGwtMi0zLjQ2Yy0uMTItLjIyLS4zOS0uMy0uNjEtLjIybC0yLjQ5IDFjLS41Mi0uNC0xLjA4LS43My0xLjY5LS45OGwtLjM4LTIuNjVBLjQ4OC40ODggMCAwMDE0IDJoLTRjLS4yNSAwLS40Ni4xOC0uNDkuNDJsLS4zOCAyLjY1Yy0uNjEuMjUtMS4xNy41OS0xLjY5Ljk4bC0yLjQ5LTFjLS4yMy0uMDktLjQ5IDAtLjYxLjIybC0yIDMuNDZjLS4xMy4yMi0uMDcuNDkuMTIuNjRsMi4xMSAxLjY1Yy0uMDQuMzItLjA3LjY1LS4wNy45OHMuMDMuNjYuMDcuOThsLTIuMTEgMS42NWMtLjE5LjE1LS4yNC40Mi0uMTIuNjRsMiAzLjQ2Yy4xMi4yMi4zOS4zLjYxLjIybDIuNDktMWMuNTIuNCAxLjA4LjczIDEuNjkuOThsLjM4IDIuNjVjLjAzLjI0LjI0LjQyLjQ5LjQyaDRjLjI1IDAgLjQ2LS4xOC40OS0uNDJsLjM4LTIuNjVjLjYxLS4yNSAxLjE3LS41OSAxLjY5LS45OGwyLjQ5IDFjLjIzLjA5LjQ5IDAgLjYxLS4yMmwyLTMuNDZjLjEyLS4yMi4wNy0uNDktLjEyLS42NGwtMi4xMS0xLjY1ek0xMiAxNS41Yy0xLjkzIDAtMy41LTEuNTctMy41LTMuNXMxLjU3LTMuNSAzLjUtMy41IDMuNSAxLjU3IDMuNSAzLjUtMS41NyAzLjUtMy41IDMuNXoiLz4KPC9zdmc+Cg==);
  --jp-icon-spreadsheet: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNENBRjUwIiBkPSJNMi4yIDIuMnYxNy42aDE3LjZWMi4ySDIuMnptMTUuNCA3LjdoLTUuNVY0LjRoNS41djUuNXpNOS45IDQuNHY1LjVINC40VjQuNGg1LjV6bS01LjUgNy43aDUuNXY1LjVINC40di01LjV6bTcuNyA1LjV2LTUuNWg1LjV2NS41aC01LjV6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-stop: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik02IDZoMTJ2MTJINnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-tab: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIxIDNIM2MtMS4xIDAtMiAuOS0yIDJ2MTRjMCAxLjEuOSAyIDIgMmgxOGMxLjEgMCAyLS45IDItMlY1YzAtMS4xLS45LTItMi0yem0wIDE2SDNWNWgxMHY0aDh2MTB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-table-rows: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMSw4SDNWNGgxOFY4eiBNMjEsMTBIM3Y0aDE4VjEweiBNMjEsMTZIM3Y0aDE4VjE2eiIvPgogICAgPC9nPgo8L3N2Zz4=);
  --jp-icon-tag: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjgiIGhlaWdodD0iMjgiIHZpZXdCb3g9IjAgMCA0MyAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTI4LjgzMzIgMTIuMzM0TDMyLjk5OTggMTYuNTAwN0wzNy4xNjY1IDEyLjMzNEgyOC44MzMyWiIvPgoJCTxwYXRoIGQ9Ik0xNi4yMDk1IDIxLjYxMDRDMTUuNjg3MyAyMi4xMjk5IDE0Ljg0NDMgMjIuMTI5OSAxNC4zMjQ4IDIxLjYxMDRMNi45ODI5IDE0LjcyNDVDNi41NzI0IDE0LjMzOTQgNi4wODMxMyAxMy42MDk4IDYuMDQ3ODYgMTMuMDQ4MkM1Ljk1MzQ3IDExLjUyODggNi4wMjAwMiA4LjYxOTQ0IDYuMDY2MjEgNy4wNzY5NUM2LjA4MjgxIDYuNTE0NzcgNi41NTU0OCA2LjA0MzQ3IDcuMTE4MDQgNi4wMzA1NUM5LjA4ODYzIDUuOTg0NzMgMTMuMjYzOCA1LjkzNTc5IDEzLjY1MTggNi4zMjQyNUwyMS43MzY5IDEzLjYzOUMyMi4yNTYgMTQuMTU4NSAyMS43ODUxIDE1LjQ3MjQgMjEuMjYyIDE1Ljk5NDZMMTYuMjA5NSAyMS42MTA0Wk05Ljc3NTg1IDguMjY1QzkuMzM1NTEgNy44MjU2NiA4LjYyMzUxIDcuODI1NjYgOC4xODI4IDguMjY1QzcuNzQzNDYgOC43MDU3MSA3Ljc0MzQ2IDkuNDE3MzMgOC4xODI4IDkuODU2NjdDOC42MjM4MiAxMC4yOTY0IDkuMzM1ODIgMTAuMjk2NCA5Ljc3NTg1IDkuODU2NjdDMTAuMjE1NiA5LjQxNzMzIDEwLjIxNTYgOC43MDUzMyA5Ljc3NTg1IDguMjY1WiIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-terminal: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0IiA+CiAgICA8cmVjdCBjbGFzcz0ianAtaWNvbjIganAtaWNvbi1zZWxlY3RhYmxlIiB3aWR0aD0iMjAiIGhlaWdodD0iMjAiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMikiIGZpbGw9IiMzMzMzMzMiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uLWFjY2VudDIganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGQ9Ik01LjA1NjY0IDguNzYxNzJDNS4wNTY2NCA4LjU5NzY2IDUuMDMxMjUgOC40NTMxMiA0Ljk4MDQ3IDguMzI4MTJDNC45MzM1OSA4LjE5OTIyIDQuODU1NDcgOC4wODIwMyA0Ljc0NjA5IDcuOTc2NTZDNC42NDA2MiA3Ljg3MTA5IDQuNSA3Ljc3NTM5IDQuMzI0MjIgNy42ODk0NUM0LjE1MjM0IDcuNTk5NjEgMy45NDMzNiA3LjUxMTcyIDMuNjk3MjcgNy40MjU3OEMzLjMwMjczIDcuMjg1MTYgMi45NDMzNiA3LjEzNjcyIDIuNjE5MTQgNi45ODA0N0MyLjI5NDkyIDYuODI0MjIgMi4wMTc1OCA2LjY0MjU4IDEuNzg3MTEgNi40MzU1NUMxLjU2MDU1IDYuMjI4NTIgMS4zODQ3NyA1Ljk4ODI4IDEuMjU5NzcgNS43MTQ4NEMxLjEzNDc3IDUuNDM3NSAxLjA3MjI3IDUuMTA5MzggMS4wNzIyNyA0LjczMDQ3QzEuMDcyMjcgNC4zOTg0NCAxLjEyODkxIDQuMDk1NyAxLjI0MjE5IDMuODIyMjdDMS4zNTU0NyAzLjU0NDkyIDEuNTE1NjIgMy4zMDQ2OSAxLjcyMjY2IDMuMTAxNTZDMS45Mjk2OSAyLjg5ODQ0IDIuMTc5NjkgMi43MzQzNyAyLjQ3MjY2IDIuNjA5MzhDMi43NjU2MiAyLjQ4NDM4IDMuMDkxOCAyLjQwNDMgMy40NTExNyAyLjM2OTE0VjEuMTA5MzhINC4zODg2N1YyLjM4MDg2QzQuNzQwMjMgMi40Mjc3MyA1LjA1NjY0IDIuNTIzNDQgNS4zMzc4OSAyLjY2Nzk3QzUuNjE5MTQgMi44MTI1IDUuODU3NDIgMy4wMDE5NSA2LjA1MjczIDMuMjM2MzNDNi4yNTE5NSAzLjQ2NjggNi40MDQzIDMuNzQwMjMgNi41MDk3NyA0LjA1NjY0QzYuNjE5MTQgNC4zNjkxNCA2LjY3MzgzIDQuNzIwNyA2LjY3MzgzIDUuMTExMzNINS4wNDQ5MkM1LjA0NDkyIDQuNjM4NjcgNC45Mzc1IDQuMjgxMjUgNC43MjI2NiA0LjAzOTA2QzQuNTA3ODEgMy43OTI5NyA0LjIxNjggMy42Njk5MiAzLjg0OTYxIDMuNjY5OTJDMy42NTAzOSAzLjY2OTkyIDMuNDc2NTYgMy42OTcyNyAzLjMyODEyIDMuNzUxOTVDMy4xODM1OSAzLjgwMjczIDMuMDY0NDUgMy44NzY5NSAyLjk3MDcgMy45NzQ2MUMyLjg3Njk1IDQuMDY4MzYgMi44MDY2NCA0LjE3OTY5IDIuNzU5NzcgNC4zMDg1OUMyLjcxNjggNC40Mzc1IDIuNjk1MzEgNC41NzgxMiAyLjY5NTMxIDQuNzMwNDdDMi42OTUzMSA0Ljg4MjgxIDIuNzE2OCA1LjAxOTUzIDIuNzU5NzcgNS4xNDA2MkMyLjgwNjY0IDUuMjU3ODEgMi44ODI4MSA1LjM2NzE5IDIuOTg4MjggNS40Njg3NUMzLjA5NzY2IDUuNTcwMzEgMy4yNDAyMyA1LjY2Nzk3IDMuNDE2MDIgNS43NjE3MkMzLjU5MTggNS44NTE1NiAzLjgxMDU1IDUuOTQzMzYgNC4wNzIyNyA2LjAzNzExQzQuNDY2OCA2LjE4NTU1IDQuODI0MjIgNi4zMzk4NCA1LjE0NDUzIDYuNUM1LjQ2NDg0IDYuNjU2MjUgNS43MzgyOCA2LjgzOTg0IDUuOTY0ODQgNy4wNTA3OEM2LjE5NTMxIDcuMjU3ODEgNi4zNzEwOSA3LjUgNi40OTIxOSA3Ljc3NzM0QzYuNjE3MTkgOC4wNTA3OCA2LjY3OTY5IDguMzc1IDYuNjc5NjkgOC43NUM2LjY3OTY5IDkuMDkzNzUgNi42MjMwNSA5LjQwNDMgNi41MDk3NyA5LjY4MTY0QzYuMzk2NDggOS45NTUwOCA2LjIzNDM4IDEwLjE5MTQgNi4wMjM0NCAxMC4zOTA2QzUuODEyNSAxMC41ODk4IDUuNTU4NTkgMTAuNzUgNS4yNjE3MiAxMC44NzExQzQuOTY0ODQgMTAuOTg4MyA0LjYzMjgxIDExLjA2NDUgNC4yNjU2MiAxMS4wOTk2VjEyLjI0OEgzLjMzMzk4VjExLjA5OTZDMy4wMDE5NSAxMS4wNjg0IDIuNjc5NjkgMTAuOTk2MSAyLjM2NzE5IDEwLjg4MjhDMi4wNTQ2OSAxMC43NjU2IDEuNzc3MzQgMTAuNTk3NyAxLjUzNTE2IDEwLjM3ODlDMS4yOTY4OCAxMC4xNjAyIDEuMTA1NDcgOS44ODQ3NyAwLjk2MDkzOCA5LjU1MjczQzAuODE2NDA2IDkuMjE2OCAwLjc0NDE0MSA4LjgxNDQ1IDAuNzQ0MTQxIDguMzQ1N0gyLjM3ODkxQzIuMzc4OTEgOC42MjY5NSAyLjQxOTkyIDguODYzMjggMi41MDE5NSA5LjA1NDY5QzIuNTgzOTggOS4yNDIxOSAyLjY4OTQ1IDkuMzkyNTggMi44MTgzNiA5LjUwNTg2QzIuOTUxMTcgOS42MTUyMyAzLjEwMTU2IDkuNjkzMzYgMy4yNjk1MyA5Ljc0MDIzQzMuNDM3NSA5Ljc4NzExIDMuNjA5MzggOS44MTA1NSAzLjc4NTE2IDkuODEwNTVDNC4yMDMxMiA5LjgxMDU1IDQuNTE5NTMgOS43MTI4OSA0LjczNDM4IDkuNTE3NThDNC45NDkyMiA5LjMyMjI3IDUuMDU2NjQgOS4wNzAzMSA1LjA1NjY0IDguNzYxNzJaTTEzLjQxOCAxMi4yNzE1SDguMDc0MjJWMTFIMTMuNDE4VjEyLjI3MTVaIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzLjk1MjY0IDYpIiBmaWxsPSJ3aGl0ZSIvPgo8L3N2Zz4K);
  --jp-icon-text-editor: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTUgMTVIM3YyaDEydi0yem0wLThIM3YyaDEyVjd6TTMgMTNoMTh2LTJIM3Yyem0wIDhoMTh2LTJIM3Yyek0zIDN2MmgxOFYzSDN6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-toc: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik03LDVIMjFWN0g3VjVNNywxM1YxMUgyMVYxM0g3TTQsNC41QTEuNSwxLjUgMCAwLDEgNS41LDZBMS41LDEuNSAwIDAsMSA0LDcuNUExLjUsMS41IDAgMCwxIDIuNSw2QTEuNSwxLjUgMCAwLDEgNCw0LjVNNCwxMC41QTEuNSwxLjUgMCAwLDEgNS41LDEyQTEuNSwxLjUgMCAwLDEgNCwxMy41QTEuNSwxLjUgMCAwLDEgMi41LDEyQTEuNSwxLjUgMCAwLDEgNCwxMC41TTcsMTlWMTdIMjFWMTlIN000LDE2LjVBMS41LDEuNSAwIDAsMSA1LjUsMThBMS41LDEuNSAwIDAsMSA0LDE5LjVBMS41LDEuNSAwIDAsMSAyLjUsMThBMS41LDEuNSAwIDAsMSA0LDE2LjVaIiAvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-tree-view: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMiAxMVYzaC03djNIOVYzSDJ2OGg3VjhoMnYxMGg0djNoN3YtOGgtN3YzaC0yVjhoMnYzeiIvPgogICAgPC9nPgo8L3N2Zz4=);
  --jp-icon-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMiAxNy4xODQ0IDIuOTY5NjggMTQuMzAzMiAxLjg2MDk0IDExLjQ0MDlaIi8+CiAgICA8cGF0aCBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiMzMzMzMzMiIHN0cm9rZT0iIzMzMzMzMyIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOCA5Ljg2NzE5KSIgZD0iTTIuODYwMTUgNC44NjUzNUwwLjcyNjU0OSAyLjk5OTU5TDAgMy42MzA0NUwyLjg2MDE1IDYuMTMxNTdMOCAwLjYzMDg3Mkw3LjI3ODU3IDBMMi44NjAxNSA0Ljg2NTM1WiIvPgo8L3N2Zz4K);
  --jp-icon-undo: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjUgOGMtMi42NSAwLTUuMDUuOTktNi45IDIuNkwyIDd2OWg5bC0zLjYyLTMuNjJjMS4zOS0xLjE2IDMuMTYtMS44OCA1LjEyLTEuODggMy41NCAwIDYuNTUgMi4zMSA3LjYgNS41bDIuMzctLjc4QzIxLjA4IDExLjAzIDE3LjE1IDggMTIuNSA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-vega: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbjEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjEyMTIxIj4KICAgIDxwYXRoIGQ9Ik0xMC42IDUuNGwyLjItMy4ySDIuMnY3LjNsNC02LjZ6Ii8+CiAgICA8cGF0aCBkPSJNMTUuOCAyLjJsLTQuNCA2LjZMNyA2LjNsLTQuOCA4djUuNWgxNy42VjIuMmgtNHptLTcgMTUuNEg1LjV2LTQuNGgzLjN2NC40em00LjQgMEg5LjhWOS44aDMuNHY3Ljh6bTQuNCAwaC0zLjRWNi41aDMuNHYxMS4xeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-yaml: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1jb250cmFzdDIganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjRDgxQjYwIj4KICAgIDxwYXRoIGQ9Ik03LjIgMTguNnYtNS40TDMgNS42aDMuM2wxLjQgMy4xYy4zLjkuNiAxLjYgMSAyLjUuMy0uOC42LTEuNiAxLTIuNWwxLjQtMy4xaDMuNGwtNC40IDcuNnY1LjVsLTIuOS0uMXoiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxNi41IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxMSIgcj0iMi4xIi8+CiAgPC9nPgo8L3N2Zz4K);
}

/* Icon CSS class declarations */

.jp-AddIcon {
  background-image: var(--jp-icon-add);
}
.jp-BugIcon {
  background-image: var(--jp-icon-bug);
}
.jp-BuildIcon {
  background-image: var(--jp-icon-build);
}
.jp-CaretDownEmptyIcon {
  background-image: var(--jp-icon-caret-down-empty);
}
.jp-CaretDownEmptyThinIcon {
  background-image: var(--jp-icon-caret-down-empty-thin);
}
.jp-CaretDownIcon {
  background-image: var(--jp-icon-caret-down);
}
.jp-CaretLeftIcon {
  background-image: var(--jp-icon-caret-left);
}
.jp-CaretRightIcon {
  background-image: var(--jp-icon-caret-right);
}
.jp-CaretUpEmptyThinIcon {
  background-image: var(--jp-icon-caret-up-empty-thin);
}
.jp-CaretUpIcon {
  background-image: var(--jp-icon-caret-up);
}
.jp-CaseSensitiveIcon {
  background-image: var(--jp-icon-case-sensitive);
}
.jp-CheckIcon {
  background-image: var(--jp-icon-check);
}
.jp-CircleEmptyIcon {
  background-image: var(--jp-icon-circle-empty);
}
.jp-CircleIcon {
  background-image: var(--jp-icon-circle);
}
.jp-ClearIcon {
  background-image: var(--jp-icon-clear);
}
.jp-CloseIcon {
  background-image: var(--jp-icon-close);
}
.jp-CodeIcon {
  background-image: var(--jp-icon-code);
}
.jp-ConsoleIcon {
  background-image: var(--jp-icon-console);
}
.jp-CopyIcon {
  background-image: var(--jp-icon-copy);
}
.jp-CopyrightIcon {
  background-image: var(--jp-icon-copyright);
}
.jp-CutIcon {
  background-image: var(--jp-icon-cut);
}
.jp-DownloadIcon {
  background-image: var(--jp-icon-download);
}
.jp-EditIcon {
  background-image: var(--jp-icon-edit);
}
.jp-EllipsesIcon {
  background-image: var(--jp-icon-ellipses);
}
.jp-ExtensionIcon {
  background-image: var(--jp-icon-extension);
}
.jp-FastForwardIcon {
  background-image: var(--jp-icon-fast-forward);
}
.jp-FileIcon {
  background-image: var(--jp-icon-file);
}
.jp-FileUploadIcon {
  background-image: var(--jp-icon-file-upload);
}
.jp-FilterListIcon {
  background-image: var(--jp-icon-filter-list);
}
.jp-FolderIcon {
  background-image: var(--jp-icon-folder);
}
.jp-Html5Icon {
  background-image: var(--jp-icon-html5);
}
.jp-ImageIcon {
  background-image: var(--jp-icon-image);
}
.jp-InspectorIcon {
  background-image: var(--jp-icon-inspector);
}
.jp-JsonIcon {
  background-image: var(--jp-icon-json);
}
.jp-JuliaIcon {
  background-image: var(--jp-icon-julia);
}
.jp-JupyterFaviconIcon {
  background-image: var(--jp-icon-jupyter-favicon);
}
.jp-JupyterIcon {
  background-image: var(--jp-icon-jupyter);
}
.jp-JupyterlabWordmarkIcon {
  background-image: var(--jp-icon-jupyterlab-wordmark);
}
.jp-KernelIcon {
  background-image: var(--jp-icon-kernel);
}
.jp-KeyboardIcon {
  background-image: var(--jp-icon-keyboard);
}
.jp-LauncherIcon {
  background-image: var(--jp-icon-launcher);
}
.jp-LineFormIcon {
  background-image: var(--jp-icon-line-form);
}
.jp-LinkIcon {
  background-image: var(--jp-icon-link);
}
.jp-ListIcon {
  background-image: var(--jp-icon-list);
}
.jp-ListingsInfoIcon {
  background-image: var(--jp-icon-listings-info);
}
.jp-MarkdownIcon {
  background-image: var(--jp-icon-markdown);
}
.jp-NewFolderIcon {
  background-image: var(--jp-icon-new-folder);
}
.jp-NotTrustedIcon {
  background-image: var(--jp-icon-not-trusted);
}
.jp-NotebookIcon {
  background-image: var(--jp-icon-notebook);
}
.jp-NumberingIcon {
  background-image: var(--jp-icon-numbering);
}
.jp-OfflineBoltIcon {
  background-image: var(--jp-icon-offline-bolt);
}
.jp-PaletteIcon {
  background-image: var(--jp-icon-palette);
}
.jp-PasteIcon {
  background-image: var(--jp-icon-paste);
}
.jp-PdfIcon {
  background-image: var(--jp-icon-pdf);
}
.jp-PythonIcon {
  background-image: var(--jp-icon-python);
}
.jp-RKernelIcon {
  background-image: var(--jp-icon-r-kernel);
}
.jp-ReactIcon {
  background-image: var(--jp-icon-react);
}
.jp-RedoIcon {
  background-image: var(--jp-icon-redo);
}
.jp-RefreshIcon {
  background-image: var(--jp-icon-refresh);
}
.jp-RegexIcon {
  background-image: var(--jp-icon-regex);
}
.jp-RunIcon {
  background-image: var(--jp-icon-run);
}
.jp-RunningIcon {
  background-image: var(--jp-icon-running);
}
.jp-SaveIcon {
  background-image: var(--jp-icon-save);
}
.jp-SearchIcon {
  background-image: var(--jp-icon-search);
}
.jp-SettingsIcon {
  background-image: var(--jp-icon-settings);
}
.jp-SpreadsheetIcon {
  background-image: var(--jp-icon-spreadsheet);
}
.jp-StopIcon {
  background-image: var(--jp-icon-stop);
}
.jp-TabIcon {
  background-image: var(--jp-icon-tab);
}
.jp-TableRowsIcon {
  background-image: var(--jp-icon-table-rows);
}
.jp-TagIcon {
  background-image: var(--jp-icon-tag);
}
.jp-TerminalIcon {
  background-image: var(--jp-icon-terminal);
}
.jp-TextEditorIcon {
  background-image: var(--jp-icon-text-editor);
}
.jp-TocIcon {
  background-image: var(--jp-icon-toc);
}
.jp-TreeViewIcon {
  background-image: var(--jp-icon-tree-view);
}
.jp-TrustedIcon {
  background-image: var(--jp-icon-trusted);
}
.jp-UndoIcon {
  background-image: var(--jp-icon-undo);
}
.jp-VegaIcon {
  background-image: var(--jp-icon-vega);
}
.jp-YamlIcon {
  background-image: var(--jp-icon-yaml);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * (DEPRECATED) Support for consuming icons as CSS background images
 */

.jp-Icon,
.jp-MaterialIcon {
  background-position: center;
  background-repeat: no-repeat;
  background-size: 16px;
  min-width: 16px;
  min-height: 16px;
}

.jp-Icon-cover {
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

/**
 * (DEPRECATED) Support for specific CSS icon sizes
 */

.jp-Icon-16 {
  background-size: 16px;
  min-width: 16px;
  min-height: 16px;
}

.jp-Icon-18 {
  background-size: 18px;
  min-width: 18px;
  min-height: 18px;
}

.jp-Icon-20 {
  background-size: 20px;
  min-width: 20px;
  min-height: 20px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * Support for icons as inline SVG HTMLElements
 */

/* recolor the primary elements of an icon */
.jp-icon0[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon1[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon2[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon3[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon4[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon0[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon1[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon2[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon3[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon4[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}
/* recolor the accent elements of an icon */
.jp-icon-accent0[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-accent1[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-accent2[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-accent3[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-accent4[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-accent0[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-accent1[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-accent2[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-accent3[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-accent4[stroke] {
  stroke: var(--jp-layout-color4);
}
/* set the color of an icon to transparent */
.jp-icon-none[fill] {
  fill: none;
}

.jp-icon-none[stroke] {
  stroke: none;
}
/* brand icon colors. Same for light and dark */
.jp-icon-brand0[fill] {
  fill: var(--jp-brand-color0);
}
.jp-icon-brand1[fill] {
  fill: var(--jp-brand-color1);
}
.jp-icon-brand2[fill] {
  fill: var(--jp-brand-color2);
}
.jp-icon-brand3[fill] {
  fill: var(--jp-brand-color3);
}
.jp-icon-brand4[fill] {
  fill: var(--jp-brand-color4);
}

.jp-icon-brand0[stroke] {
  stroke: var(--jp-brand-color0);
}
.jp-icon-brand1[stroke] {
  stroke: var(--jp-brand-color1);
}
.jp-icon-brand2[stroke] {
  stroke: var(--jp-brand-color2);
}
.jp-icon-brand3[stroke] {
  stroke: var(--jp-brand-color3);
}
.jp-icon-brand4[stroke] {
  stroke: var(--jp-brand-color4);
}
/* warn icon colors. Same for light and dark */
.jp-icon-warn0[fill] {
  fill: var(--jp-warn-color0);
}
.jp-icon-warn1[fill] {
  fill: var(--jp-warn-color1);
}
.jp-icon-warn2[fill] {
  fill: var(--jp-warn-color2);
}
.jp-icon-warn3[fill] {
  fill: var(--jp-warn-color3);
}

.jp-icon-warn0[stroke] {
  stroke: var(--jp-warn-color0);
}
.jp-icon-warn1[stroke] {
  stroke: var(--jp-warn-color1);
}
.jp-icon-warn2[stroke] {
  stroke: var(--jp-warn-color2);
}
.jp-icon-warn3[stroke] {
  stroke: var(--jp-warn-color3);
}
/* icon colors that contrast well with each other and most backgrounds */
.jp-icon-contrast0[fill] {
  fill: var(--jp-icon-contrast-color0);
}
.jp-icon-contrast1[fill] {
  fill: var(--jp-icon-contrast-color1);
}
.jp-icon-contrast2[fill] {
  fill: var(--jp-icon-contrast-color2);
}
.jp-icon-contrast3[fill] {
  fill: var(--jp-icon-contrast-color3);
}

.jp-icon-contrast0[stroke] {
  stroke: var(--jp-icon-contrast-color0);
}
.jp-icon-contrast1[stroke] {
  stroke: var(--jp-icon-contrast-color1);
}
.jp-icon-contrast2[stroke] {
  stroke: var(--jp-icon-contrast-color2);
}
.jp-icon-contrast3[stroke] {
  stroke: var(--jp-icon-contrast-color3);
}

/* CSS for icons in selected items in the settings editor */
#setting-editor .jp-PluginList .jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}
#setting-editor
  .jp-PluginList
  .jp-mod-selected
  .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}

/* CSS for icons in selected filebrowser listing items */
.jp-DirListing-item.jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}
.jp-DirListing-item.jp-mod-selected .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}

/* CSS for icons in selected tabs in the sidebar tab manager */
#tab-manager .lm-TabBar-tab.jp-mod-active .jp-icon-selectable[fill] {
  fill: #fff;
}

#tab-manager .lm-TabBar-tab.jp-mod-active .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}
#tab-manager
  .lm-TabBar-tab.jp-mod-active
  .jp-icon-hover
  :hover
  .jp-icon-selectable[fill] {
  fill: var(--jp-brand-color1);
}

#tab-manager
  .lm-TabBar-tab.jp-mod-active
  .jp-icon-hover
  :hover
  .jp-icon-selectable-inverse[fill] {
  fill: #fff;
}

/**
 * TODO: come up with non css-hack solution for showing the busy icon on top
 *  of the close icon
 * CSS for complex behavior of close icon of tabs in the sidebar tab manager
 */
#tab-manager
  .lm-TabBar-tab.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon3[fill] {
  fill: none;
}
#tab-manager
  .lm-TabBar-tab.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: var(--jp-inverse-layout-color3);
}

#tab-manager
  .lm-TabBar-tab.jp-mod-dirty.jp-mod-active
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: #fff;
}

/**
* TODO: come up with non css-hack solution for showing the busy icon on top
*  of the close icon
* CSS for complex behavior of close icon of tabs in the main area tabbar
*/
.lm-DockPanel-tabBar
  .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon3[fill] {
  fill: none;
}
.lm-DockPanel-tabBar
  .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: var(--jp-inverse-layout-color3);
}

/* CSS for icons in status bar */
#jp-main-statusbar .jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}

#jp-main-statusbar .jp-mod-selected .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}
/* special handling for splash icon CSS. While the theme CSS reloads during
   splash, the splash icon can loose theming. To prevent that, we set a
   default for its color variable */
:root {
  --jp-warn-color0: var(--md-orange-700);
}

/* not sure what to do with this one, used in filebrowser listing */
.jp-DragIcon {
  margin-right: 4px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * Support for alt colors for icons as inline SVG HTMLElements
 */

/* alt recolor the primary elements of an icon */
.jp-icon-alt .jp-icon0[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-alt .jp-icon1[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-alt .jp-icon2[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-alt .jp-icon3[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-alt .jp-icon4[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-alt .jp-icon0[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-alt .jp-icon1[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-alt .jp-icon2[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-alt .jp-icon3[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-alt .jp-icon4[stroke] {
  stroke: var(--jp-layout-color4);
}

/* alt recolor the accent elements of an icon */
.jp-icon-alt .jp-icon-accent0[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon-alt .jp-icon-accent1[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon-alt .jp-icon-accent2[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon-alt .jp-icon-accent3[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon-alt .jp-icon-accent4[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-alt .jp-icon-accent0[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon-alt .jp-icon-accent1[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon-alt .jp-icon-accent2[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon-alt .jp-icon-accent3[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon-alt .jp-icon-accent4[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-icon-hoverShow:not(:hover) svg {
  display: none !important;
}

/**
 * Support for hover colors for icons as inline SVG HTMLElements
 */

/**
 * regular colors
 */

/* recolor the primary elements of an icon */
.jp-icon-hover :hover .jp-icon0-hover[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon-hover :hover .jp-icon1-hover[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon-hover :hover .jp-icon2-hover[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon-hover :hover .jp-icon3-hover[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon-hover :hover .jp-icon4-hover[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-hover :hover .jp-icon0-hover[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon-hover :hover .jp-icon1-hover[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon-hover :hover .jp-icon2-hover[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon-hover :hover .jp-icon3-hover[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon-hover :hover .jp-icon4-hover[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/* recolor the accent elements of an icon */
.jp-icon-hover :hover .jp-icon-accent0-hover[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-hover :hover .jp-icon-accent1-hover[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-hover :hover .jp-icon-accent2-hover[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-hover :hover .jp-icon-accent3-hover[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-hover :hover .jp-icon-accent4-hover[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-hover :hover .jp-icon-accent0-hover[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-hover :hover .jp-icon-accent1-hover[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-hover :hover .jp-icon-accent2-hover[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-hover :hover .jp-icon-accent3-hover[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-hover :hover .jp-icon-accent4-hover[stroke] {
  stroke: var(--jp-layout-color4);
}

/* set the color of an icon to transparent */
.jp-icon-hover :hover .jp-icon-none-hover[fill] {
  fill: none;
}

.jp-icon-hover :hover .jp-icon-none-hover[stroke] {
  stroke: none;
}

/**
 * inverse colors
 */

/* inverse recolor the primary elements of an icon */
.jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[stroke] {
  stroke: var(--jp-layout-color4);
}

/* inverse recolor the accent elements of an icon */
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-switch {
  display: flex;
  align-items: center;
  padding-left: 4px;
  padding-right: 4px;
  font-size: var(--jp-ui-font-size1);
  background-color: transparent;
  color: var(--jp-ui-font-color1);
  border: none;
  height: 20px;
}

.jp-switch:hover {
  background-color: var(--jp-layout-color2);
}

.jp-switch-label {
  margin-right: 5px;
}

.jp-switch-track {
  cursor: pointer;
  background-color: var(--jp-border-color1);
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 34px;
  height: 16px;
  width: 35px;
  position: relative;
}

.jp-switch-track::before {
  content: '';
  position: absolute;
  height: 10px;
  width: 10px;
  margin: 3px;
  left: 0px;
  background-color: var(--jp-ui-inverse-font-color1);
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 50%;
}

.jp-switch[aria-checked='true'] .jp-switch-track {
  background-color: var(--jp-warn-color0);
}

.jp-switch[aria-checked='true'] .jp-switch-track::before {
  /* track width (35) - margins (3 + 3) - thumb width (10) */
  left: 19px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* Sibling imports */

/* Override Blueprint's _reset.scss styles */
html {
  box-sizing: unset;
}

*,
*::before,
*::after {
  box-sizing: unset;
}

body {
  color: unset;
  font-family: var(--jp-ui-font-family);
}

p {
  margin-top: unset;
  margin-bottom: unset;
}

small {
  font-size: unset;
}

strong {
  font-weight: unset;
}

/* Override Blueprint's _typography.scss styles */
a {
  text-decoration: unset;
  color: unset;
}
a:hover {
  text-decoration: unset;
  color: unset;
}

/* Override Blueprint's _accessibility.scss styles */
:focus {
  outline: unset;
  outline-offset: unset;
  -moz-outline-radius: unset;
}

/* Styles for ui-components */
.jp-Button {
  border-radius: var(--jp-border-radius);
  padding: 0px 12px;
  font-size: var(--jp-ui-font-size1);
}

/* Use our own theme for hover styles */
button.jp-Button.bp3-button.bp3-minimal:hover {
  background-color: var(--jp-layout-color2);
}
.jp-Button.minimal {
  color: unset !important;
}

.jp-Button.jp-ToolbarButtonComponent {
  text-transform: none;
}

.jp-InputGroup input {
  box-sizing: border-box;
  border-radius: 0;
  background-color: transparent;
  color: var(--jp-ui-font-color0);
  box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
}

.jp-InputGroup input:focus {
  box-shadow: inset 0 0 0 var(--jp-border-width)
      var(--jp-input-active-box-shadow-color),
    inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
}

.jp-InputGroup input::placeholder,
input::placeholder {
  color: var(--jp-ui-font-color3);
}

.jp-BPIcon {
  display: inline-block;
  vertical-align: middle;
  margin: auto;
}

/* Stop blueprint futzing with our icon fills */
.bp3-icon.jp-BPIcon > svg:not([fill]) {
  fill: var(--jp-inverse-layout-color3);
}

.jp-InputGroupAction {
  padding: 6px;
}

.jp-HTMLSelect.jp-DefaultStyle select {
  background-color: initial;
  border: none;
  border-radius: 0;
  box-shadow: none;
  color: var(--jp-ui-font-color0);
  display: block;
  font-size: var(--jp-ui-font-size1);
  height: 24px;
  line-height: 14px;
  padding: 0 25px 0 10px;
  text-align: left;
  -moz-appearance: none;
  -webkit-appearance: none;
}

/* Use our own theme for hover and option styles */
.jp-HTMLSelect.jp-DefaultStyle select:hover,
.jp-HTMLSelect.jp-DefaultStyle select > option {
  background-color: var(--jp-layout-color2);
  color: var(--jp-ui-font-color0);
}
select {
  box-sizing: border-box;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Collapse {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-top: 1px solid var(--jp-border-color2);
  border-bottom: 1px solid var(--jp-border-color2);
}

.jp-Collapse-header {
  padding: 1px 12px;
  color: var(--jp-ui-font-color1);
  background-color: var(--jp-layout-color1);
  font-size: var(--jp-ui-font-size2);
}

.jp-Collapse-header:hover {
  background-color: var(--jp-layout-color2);
}

.jp-Collapse-contents {
  padding: 0px 12px 0px 12px;
  background-color: var(--jp-layout-color1);
  color: var(--jp-ui-font-color1);
  overflow: auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-commandpalette-search-height: 28px;
}

/*-----------------------------------------------------------------------------
| Overall styles
|----------------------------------------------------------------------------*/

.lm-CommandPalette {
  padding-bottom: 0px;
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
}

/*-----------------------------------------------------------------------------
| Modal variant
|----------------------------------------------------------------------------*/

.jp-ModalCommandPalette {
  position: absolute;
  z-index: 10000;
  top: 38px;
  left: 30%;
  margin: 0;
  padding: 4px;
  width: 40%;
  box-shadow: var(--jp-elevation-z4);
  border-radius: 4px;
  background: var(--jp-layout-color0);
}

.jp-ModalCommandPalette .lm-CommandPalette {
  max-height: 40vh;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-close-icon::after {
  display: none;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-header {
  display: none;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-item {
  margin-left: 4px;
  margin-right: 4px;
}

.jp-ModalCommandPalette
  .lm-CommandPalette
  .lm-CommandPalette-item.lm-mod-disabled {
  display: none;
}

/*-----------------------------------------------------------------------------
| Search
|----------------------------------------------------------------------------*/

.lm-CommandPalette-search {
  padding: 4px;
  background-color: var(--jp-layout-color1);
  z-index: 2;
}

.lm-CommandPalette-wrapper {
  overflow: overlay;
  padding: 0px 9px;
  background-color: var(--jp-input-active-background);
  height: 30px;
  box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
}

.lm-CommandPalette.lm-mod-focused .lm-CommandPalette-wrapper {
  box-shadow: inset 0 0 0 1px var(--jp-input-active-box-shadow-color),
    inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
}

.jp-SearchIconGroup {
  color: white;
  background-color: var(--jp-brand-color1);
  position: absolute;
  top: 4px;
  right: 4px;
  padding: 5px 5px 1px 5px;
}

.jp-SearchIconGroup svg {
  height: 20px;
  width: 20px;
}

.jp-SearchIconGroup .jp-icon3[fill] {
  fill: var(--jp-layout-color0);
}

.lm-CommandPalette-input {
  background: transparent;
  width: calc(100% - 18px);
  float: left;
  border: none;
  outline: none;
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  line-height: var(--jp-private-commandpalette-search-height);
}

.lm-CommandPalette-input::-webkit-input-placeholder,
.lm-CommandPalette-input::-moz-placeholder,
.lm-CommandPalette-input:-ms-input-placeholder {
  color: var(--jp-ui-font-color2);
  font-size: var(--jp-ui-font-size1);
}

/*-----------------------------------------------------------------------------
| Results
|----------------------------------------------------------------------------*/

.lm-CommandPalette-header:first-child {
  margin-top: 0px;
}

.lm-CommandPalette-header {
  border-bottom: solid var(--jp-border-width) var(--jp-border-color2);
  color: var(--jp-ui-font-color1);
  cursor: pointer;
  display: flex;
  font-size: var(--jp-ui-font-size0);
  font-weight: 600;
  letter-spacing: 1px;
  margin-top: 8px;
  padding: 8px 0 8px 12px;
  text-transform: uppercase;
}

.lm-CommandPalette-header.lm-mod-active {
  background: var(--jp-layout-color2);
}

.lm-CommandPalette-header > mark {
  background-color: transparent;
  font-weight: bold;
  color: var(--jp-ui-font-color1);
}

.lm-CommandPalette-item {
  padding: 4px 12px 4px 4px;
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
  font-weight: 400;
  display: flex;
}

.lm-CommandPalette-item.lm-mod-disabled {
  color: var(--jp-ui-font-color2);
}

.lm-CommandPalette-item.lm-mod-active {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.lm-CommandPalette-item.lm-mod-active .lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-inverse-font-color0);
}

.lm-CommandPalette-item.lm-mod-active .jp-icon-selectable[fill] {
  fill: var(--jp-layout-color0);
}

.lm-CommandPalette-item.lm-mod-active .lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-inverse-font-color0);
}

.lm-CommandPalette-item.lm-mod-active:hover:not(.lm-mod-disabled) {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.lm-CommandPalette-item:hover:not(.lm-mod-active):not(.lm-mod-disabled) {
  background: var(--jp-layout-color2);
}

.lm-CommandPalette-itemContent {
  overflow: hidden;
}

.lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-font-color0);
  background-color: transparent;
  font-weight: bold;
}

.lm-CommandPalette-item.lm-mod-disabled mark {
  color: var(--jp-ui-font-color2);
}

.lm-CommandPalette-item .lm-CommandPalette-itemIcon {
  margin: 0 4px 0 0;
  position: relative;
  width: 16px;
  top: 2px;
  flex: 0 0 auto;
}

.lm-CommandPalette-item.lm-mod-disabled .lm-CommandPalette-itemIcon {
  opacity: 0.6;
}

.lm-CommandPalette-item .lm-CommandPalette-itemShortcut {
  flex: 0 0 auto;
}

.lm-CommandPalette-itemCaption {
  display: none;
}

.lm-CommandPalette-content {
  background-color: var(--jp-layout-color1);
}

.lm-CommandPalette-content:empty:after {
  content: 'No results';
  margin: auto;
  margin-top: 20px;
  width: 100px;
  display: block;
  font-size: var(--jp-ui-font-size2);
  font-family: var(--jp-ui-font-family);
  font-weight: lighter;
}

.lm-CommandPalette-emptyMessage {
  text-align: center;
  margin-top: 24px;
  line-height: 1.32;
  padding: 0px 8px;
  color: var(--jp-content-font-color3);
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Dialog {
  position: absolute;
  z-index: 10000;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  top: 0px;
  left: 0px;
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background: var(--jp-dialog-background);
}

.jp-Dialog-content {
  display: flex;
  flex-direction: column;
  margin-left: auto;
  margin-right: auto;
  background: var(--jp-layout-color1);
  padding: 24px;
  padding-bottom: 12px;
  min-width: 300px;
  min-height: 150px;
  max-width: 1000px;
  max-height: 500px;
  box-sizing: border-box;
  box-shadow: var(--jp-elevation-z20);
  word-wrap: break-word;
  border-radius: var(--jp-border-radius);
  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color1);
  resize: both;
}

.jp-Dialog-button {
  overflow: visible;
}

button.jp-Dialog-button:focus {
  outline: 1px solid var(--jp-brand-color1);
  outline-offset: 4px;
  -moz-outline-radius: 0px;
}

button.jp-Dialog-button:focus::-moz-focus-inner {
  border: 0;
}

button.jp-Dialog-close-button {
  padding: 0;
  height: 100%;
  min-width: unset;
  min-height: unset;
}

.jp-Dialog-header {
  display: flex;
  justify-content: space-between;
  flex: 0 0 auto;
  padding-bottom: 12px;
  font-size: var(--jp-ui-font-size3);
  font-weight: 400;
  color: var(--jp-ui-font-color0);
}

.jp-Dialog-body {
  display: flex;
  flex-direction: column;
  flex: 1 1 auto;
  font-size: var(--jp-ui-font-size1);
  background: var(--jp-layout-color1);
  overflow: auto;
}

.jp-Dialog-footer {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  flex: 0 0 auto;
  margin-left: -12px;
  margin-right: -12px;
  padding: 12px;
}

.jp-Dialog-title {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.jp-Dialog-body > .jp-select-wrapper {
  width: 100%;
}

.jp-Dialog-body > button {
  padding: 0px 16px;
}

.jp-Dialog-body > label {
  line-height: 1.4;
  color: var(--jp-ui-font-color0);
}

.jp-Dialog-button.jp-mod-styled:not(:last-child) {
  margin-right: 12px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-HoverBox {
  position: fixed;
}

.jp-HoverBox.jp-mod-outofview {
  display: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-IFrame {
  width: 100%;
  height: 100%;
}

.jp-IFrame > iframe {
  border: none;
}

/*
When drag events occur, `p-mod-override-cursor` is added to the body.
Because iframes steal all cursor events, the following two rules are necessary
to suppress pointer events while resize drags are occurring. There may be a
better solution to this problem.
*/
body.lm-mod-override-cursor .jp-IFrame {
  position: relative;
}

body.lm-mod-override-cursor .jp-IFrame:before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
}

.jp-Input-Boolean-Dialog {
  flex-direction: row-reverse;
  align-items: end;
  width: 100%;
}

.jp-Input-Boolean-Dialog > label {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-MainAreaWidget > :focus {
  outline: none;
}

/**
 * google-material-color v1.2.6
 * https://github.com/danlevan/google-material-color
 */
:root {
  --md-red-50: #ffebee;
  --md-red-100: #ffcdd2;
  --md-red-200: #ef9a9a;
  --md-red-300: #e57373;
  --md-red-400: #ef5350;
  --md-red-500: #f44336;
  --md-red-600: #e53935;
  --md-red-700: #d32f2f;
  --md-red-800: #c62828;
  --md-red-900: #b71c1c;
  --md-red-A100: #ff8a80;
  --md-red-A200: #ff5252;
  --md-red-A400: #ff1744;
  --md-red-A700: #d50000;

  --md-pink-50: #fce4ec;
  --md-pink-100: #f8bbd0;
  --md-pink-200: #f48fb1;
  --md-pink-300: #f06292;
  --md-pink-400: #ec407a;
  --md-pink-500: #e91e63;
  --md-pink-600: #d81b60;
  --md-pink-700: #c2185b;
  --md-pink-800: #ad1457;
  --md-pink-900: #880e4f;
  --md-pink-A100: #ff80ab;
  --md-pink-A200: #ff4081;
  --md-pink-A400: #f50057;
  --md-pink-A700: #c51162;

  --md-purple-50: #f3e5f5;
  --md-purple-100: #e1bee7;
  --md-purple-200: #ce93d8;
  --md-purple-300: #ba68c8;
  --md-purple-400: #ab47bc;
  --md-purple-500: #9c27b0;
  --md-purple-600: #8e24aa;
  --md-purple-700: #7b1fa2;
  --md-purple-800: #6a1b9a;
  --md-purple-900: #4a148c;
  --md-purple-A100: #ea80fc;
  --md-purple-A200: #e040fb;
  --md-purple-A400: #d500f9;
  --md-purple-A700: #aa00ff;

  --md-deep-purple-50: #ede7f6;
  --md-deep-purple-100: #d1c4e9;
  --md-deep-purple-200: #b39ddb;
  --md-deep-purple-300: #9575cd;
  --md-deep-purple-400: #7e57c2;
  --md-deep-purple-500: #673ab7;
  --md-deep-purple-600: #5e35b1;
  --md-deep-purple-700: #512da8;
  --md-deep-purple-800: #4527a0;
  --md-deep-purple-900: #311b92;
  --md-deep-purple-A100: #b388ff;
  --md-deep-purple-A200: #7c4dff;
  --md-deep-purple-A400: #651fff;
  --md-deep-purple-A700: #6200ea;

  --md-indigo-50: #e8eaf6;
  --md-indigo-100: #c5cae9;
  --md-indigo-200: #9fa8da;
  --md-indigo-300: #7986cb;
  --md-indigo-400: #5c6bc0;
  --md-indigo-500: #3f51b5;
  --md-indigo-600: #3949ab;
  --md-indigo-700: #303f9f;
  --md-indigo-800: #283593;
  --md-indigo-900: #1a237e;
  --md-indigo-A100: #8c9eff;
  --md-indigo-A200: #536dfe;
  --md-indigo-A400: #3d5afe;
  --md-indigo-A700: #304ffe;

  --md-blue-50: #e3f2fd;
  --md-blue-100: #bbdefb;
  --md-blue-200: #90caf9;
  --md-blue-300: #64b5f6;
  --md-blue-400: #42a5f5;
  --md-blue-500: #2196f3;
  --md-blue-600: #1e88e5;
  --md-blue-700: #1976d2;
  --md-blue-800: #1565c0;
  --md-blue-900: #0d47a1;
  --md-blue-A100: #82b1ff;
  --md-blue-A200: #448aff;
  --md-blue-A400: #2979ff;
  --md-blue-A700: #2962ff;

  --md-light-blue-50: #e1f5fe;
  --md-light-blue-100: #b3e5fc;
  --md-light-blue-200: #81d4fa;
  --md-light-blue-300: #4fc3f7;
  --md-light-blue-400: #29b6f6;
  --md-light-blue-500: #03a9f4;
  --md-light-blue-600: #039be5;
  --md-light-blue-700: #0288d1;
  --md-light-blue-800: #0277bd;
  --md-light-blue-900: #01579b;
  --md-light-blue-A100: #80d8ff;
  --md-light-blue-A200: #40c4ff;
  --md-light-blue-A400: #00b0ff;
  --md-light-blue-A700: #0091ea;

  --md-cyan-50: #e0f7fa;
  --md-cyan-100: #b2ebf2;
  --md-cyan-200: #80deea;
  --md-cyan-300: #4dd0e1;
  --md-cyan-400: #26c6da;
  --md-cyan-500: #00bcd4;
  --md-cyan-600: #00acc1;
  --md-cyan-700: #0097a7;
  --md-cyan-800: #00838f;
  --md-cyan-900: #006064;
  --md-cyan-A100: #84ffff;
  --md-cyan-A200: #18ffff;
  --md-cyan-A400: #00e5ff;
  --md-cyan-A700: #00b8d4;

  --md-teal-50: #e0f2f1;
  --md-teal-100: #b2dfdb;
  --md-teal-200: #80cbc4;
  --md-teal-300: #4db6ac;
  --md-teal-400: #26a69a;
  --md-teal-500: #009688;
  --md-teal-600: #00897b;
  --md-teal-700: #00796b;
  --md-teal-800: #00695c;
  --md-teal-900: #004d40;
  --md-teal-A100: #a7ffeb;
  --md-teal-A200: #64ffda;
  --md-teal-A400: #1de9b6;
  --md-teal-A700: #00bfa5;

  --md-green-50: #e8f5e9;
  --md-green-100: #c8e6c9;
  --md-green-200: #a5d6a7;
  --md-green-300: #81c784;
  --md-green-400: #66bb6a;
  --md-green-500: #4caf50;
  --md-green-600: #43a047;
  --md-green-700: #388e3c;
  --md-green-800: #2e7d32;
  --md-green-900: #1b5e20;
  --md-green-A100: #b9f6ca;
  --md-green-A200: #69f0ae;
  --md-green-A400: #00e676;
  --md-green-A700: #00c853;

  --md-light-green-50: #f1f8e9;
  --md-light-green-100: #dcedc8;
  --md-light-green-200: #c5e1a5;
  --md-light-green-300: #aed581;
  --md-light-green-400: #9ccc65;
  --md-light-green-500: #8bc34a;
  --md-light-green-600: #7cb342;
  --md-light-green-700: #689f38;
  --md-light-green-800: #558b2f;
  --md-light-green-900: #33691e;
  --md-light-green-A100: #ccff90;
  --md-light-green-A200: #b2ff59;
  --md-light-green-A400: #76ff03;
  --md-light-green-A700: #64dd17;

  --md-lime-50: #f9fbe7;
  --md-lime-100: #f0f4c3;
  --md-lime-200: #e6ee9c;
  --md-lime-300: #dce775;
  --md-lime-400: #d4e157;
  --md-lime-500: #cddc39;
  --md-lime-600: #c0ca33;
  --md-lime-700: #afb42b;
  --md-lime-800: #9e9d24;
  --md-lime-900: #827717;
  --md-lime-A100: #f4ff81;
  --md-lime-A200: #eeff41;
  --md-lime-A400: #c6ff00;
  --md-lime-A700: #aeea00;

  --md-yellow-50: #fffde7;
  --md-yellow-100: #fff9c4;
  --md-yellow-200: #fff59d;
  --md-yellow-300: #fff176;
  --md-yellow-400: #ffee58;
  --md-yellow-500: #ffeb3b;
  --md-yellow-600: #fdd835;
  --md-yellow-700: #fbc02d;
  --md-yellow-800: #f9a825;
  --md-yellow-900: #f57f17;
  --md-yellow-A100: #ffff8d;
  --md-yellow-A200: #ffff00;
  --md-yellow-A400: #ffea00;
  --md-yellow-A700: #ffd600;

  --md-amber-50: #fff8e1;
  --md-amber-100: #ffecb3;
  --md-amber-200: #ffe082;
  --md-amber-300: #ffd54f;
  --md-amber-400: #ffca28;
  --md-amber-500: #ffc107;
  --md-amber-600: #ffb300;
  --md-amber-700: #ffa000;
  --md-amber-800: #ff8f00;
  --md-amber-900: #ff6f00;
  --md-amber-A100: #ffe57f;
  --md-amber-A200: #ffd740;
  --md-amber-A400: #ffc400;
  --md-amber-A700: #ffab00;

  --md-orange-50: #fff3e0;
  --md-orange-100: #ffe0b2;
  --md-orange-200: #ffcc80;
  --md-orange-300: #ffb74d;
  --md-orange-400: #ffa726;
  --md-orange-500: #ff9800;
  --md-orange-600: #fb8c00;
  --md-orange-700: #f57c00;
  --md-orange-800: #ef6c00;
  --md-orange-900: #e65100;
  --md-orange-A100: #ffd180;
  --md-orange-A200: #ffab40;
  --md-orange-A400: #ff9100;
  --md-orange-A700: #ff6d00;

  --md-deep-orange-50: #fbe9e7;
  --md-deep-orange-100: #ffccbc;
  --md-deep-orange-200: #ffab91;
  --md-deep-orange-300: #ff8a65;
  --md-deep-orange-400: #ff7043;
  --md-deep-orange-500: #ff5722;
  --md-deep-orange-600: #f4511e;
  --md-deep-orange-700: #e64a19;
  --md-deep-orange-800: #d84315;
  --md-deep-orange-900: #bf360c;
  --md-deep-orange-A100: #ff9e80;
  --md-deep-orange-A200: #ff6e40;
  --md-deep-orange-A400: #ff3d00;
  --md-deep-orange-A700: #dd2c00;

  --md-brown-50: #efebe9;
  --md-brown-100: #d7ccc8;
  --md-brown-200: #bcaaa4;
  --md-brown-300: #a1887f;
  --md-brown-400: #8d6e63;
  --md-brown-500: #795548;
  --md-brown-600: #6d4c41;
  --md-brown-700: #5d4037;
  --md-brown-800: #4e342e;
  --md-brown-900: #3e2723;

  --md-grey-50: #fafafa;
  --md-grey-100: #f5f5f5;
  --md-grey-200: #eeeeee;
  --md-grey-300: #e0e0e0;
  --md-grey-400: #bdbdbd;
  --md-grey-500: #9e9e9e;
  --md-grey-600: #757575;
  --md-grey-700: #616161;
  --md-grey-800: #424242;
  --md-grey-900: #212121;

  --md-blue-grey-50: #eceff1;
  --md-blue-grey-100: #cfd8dc;
  --md-blue-grey-200: #b0bec5;
  --md-blue-grey-300: #90a4ae;
  --md-blue-grey-400: #78909c;
  --md-blue-grey-500: #607d8b;
  --md-blue-grey-600: #546e7a;
  --md-blue-grey-700: #455a64;
  --md-blue-grey-800: #37474f;
  --md-blue-grey-900: #263238;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Spinner {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 10;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: var(--jp-layout-color0);
  outline: none;
}

.jp-SpinnerContent {
  font-size: 10px;
  margin: 50px auto;
  text-indent: -9999em;
  width: 3em;
  height: 3em;
  border-radius: 50%;
  background: var(--jp-brand-color3);
  background: linear-gradient(
    to right,
    #f37626 10%,
    rgba(255, 255, 255, 0) 42%
  );
  position: relative;
  animation: load3 1s infinite linear, fadeIn 1s;
}

.jp-SpinnerContent:before {
  width: 50%;
  height: 50%;
  background: #f37626;
  border-radius: 100% 0 0 0;
  position: absolute;
  top: 0;
  left: 0;
  content: '';
}

.jp-SpinnerContent:after {
  background: var(--jp-layout-color0);
  width: 75%;
  height: 75%;
  border-radius: 50%;
  content: '';
  margin: auto;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes load3 {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

button.jp-mod-styled {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  border: none;
  box-sizing: border-box;
  text-align: center;
  line-height: 32px;
  height: 32px;
  padding: 0px 12px;
  letter-spacing: 0.8px;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

input.jp-mod-styled {
  background: var(--jp-input-background);
  height: 28px;
  box-sizing: border-box;
  border: var(--jp-border-width) solid var(--jp-border-color1);
  padding-left: 7px;
  padding-right: 7px;
  font-size: var(--jp-ui-font-size2);
  color: var(--jp-ui-font-color0);
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

input[type='checkbox'].jp-mod-styled {
  appearance: checkbox;
  -webkit-appearance: checkbox;
  -moz-appearance: checkbox;
  height: auto;
}

input.jp-mod-styled:focus {
  border: var(--jp-border-width) solid var(--md-blue-500);
  box-shadow: inset 0 0 4px var(--md-blue-300);
}

.jp-FileDialog-Checkbox {
  margin-top: 35px;
  display: flex;
  flex-direction: row;
  align-items: end;
  width: 100%;
}

.jp-FileDialog-Checkbox > label {
  flex: 1 1 auto;
}

.jp-select-wrapper {
  display: flex;
  position: relative;
  flex-direction: column;
  padding: 1px;
  background-color: var(--jp-layout-color1);
  height: 28px;
  box-sizing: border-box;
  margin-bottom: 12px;
}

.jp-select-wrapper.jp-mod-focused select.jp-mod-styled {
  border: var(--jp-border-width) solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
  background-color: var(--jp-input-active-background);
}

select.jp-mod-styled:hover {
  background-color: var(--jp-layout-color1);
  cursor: pointer;
  color: var(--jp-ui-font-color0);
  background-color: var(--jp-input-hover-background);
  box-shadow: inset 0 0px 1px rgba(0, 0, 0, 0.5);
}

select.jp-mod-styled {
  flex: 1 1 auto;
  height: 32px;
  width: 100%;
  font-size: var(--jp-ui-font-size2);
  background: var(--jp-input-background);
  color: var(--jp-ui-font-color0);
  padding: 0 25px 0 8px;
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  border-radius: 0px;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

:root {
  --jp-private-toolbar-height: calc(
    28px + var(--jp-border-width)
  ); /* leave 28px for content */
}

.jp-Toolbar {
  color: var(--jp-ui-font-color1);
  flex: 0 0 auto;
  display: flex;
  flex-direction: row;
  border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  box-shadow: var(--jp-toolbar-box-shadow);
  background: var(--jp-toolbar-background);
  min-height: var(--jp-toolbar-micro-height);
  padding: 2px;
  z-index: 1;
  overflow-x: auto;
}

/* Toolbar items */

.jp-Toolbar > .jp-Toolbar-item.jp-Toolbar-spacer {
  flex-grow: 1;
  flex-shrink: 1;
}

.jp-Toolbar-item.jp-Toolbar-kernelStatus {
  display: inline-block;
  width: 32px;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 16px;
}

.jp-Toolbar > .jp-Toolbar-item {
  flex: 0 0 auto;
  display: flex;
  padding-left: 1px;
  padding-right: 1px;
  font-size: var(--jp-ui-font-size1);
  line-height: var(--jp-private-toolbar-height);
  height: 100%;
}

/* Toolbar buttons */

/* This is the div we use to wrap the react component into a Widget */
div.jp-ToolbarButton {
  color: transparent;
  border: none;
  box-sizing: border-box;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 0px;
  margin: 0px;
}

button.jp-ToolbarButtonComponent {
  background: var(--jp-layout-color1);
  border: none;
  box-sizing: border-box;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 0px 6px;
  margin: 0px;
  height: 24px;
  border-radius: var(--jp-border-radius);
  display: flex;
  align-items: center;
  text-align: center;
  font-size: 14px;
  min-width: unset;
  min-height: unset;
}

button.jp-ToolbarButtonComponent:disabled {
  opacity: 0.4;
}

button.jp-ToolbarButtonComponent span {
  padding: 0px;
  flex: 0 0 auto;
}

button.jp-ToolbarButtonComponent .jp-ToolbarButtonComponent-label {
  font-size: var(--jp-ui-font-size1);
  line-height: 100%;
  padding-left: 2px;
  color: var(--jp-ui-font-color1);
}

#jp-main-dock-panel[data-mode='single-document']
  .jp-MainAreaWidget
  > .jp-Toolbar.jp-Toolbar-micro {
  padding: 0;
  min-height: 0;
}

#jp-main-dock-panel[data-mode='single-document']
  .jp-MainAreaWidget
  > .jp-Toolbar {
  border: none;
  box-shadow: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ body.p-mod-override-cursor *, /* </DEPRECATED> */
body.lm-mod-override-cursor * {
  cursor: inherit !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-JSONEditor {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.jp-JSONEditor-host {
  flex: 1 1 auto;
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  border-radius: 0px;
  background: var(--jp-layout-color0);
  min-height: 50px;
  padding: 1px;
}

.jp-JSONEditor.jp-mod-error .jp-JSONEditor-host {
  border-color: red;
  outline-color: red;
}

.jp-JSONEditor-header {
  display: flex;
  flex: 1 0 auto;
  padding: 0 0 0 12px;
}

.jp-JSONEditor-header label {
  flex: 0 0 auto;
}

.jp-JSONEditor-commitButton {
  height: 16px;
  width: 16px;
  background-size: 18px;
  background-repeat: no-repeat;
  background-position: center;
}

.jp-JSONEditor-host.jp-mod-focused {
  background-color: var(--jp-input-active-background);
  border: 1px solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
}

.jp-Editor.jp-mod-dropTarget {
  border: var(--jp-border-width) solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
}

/* BASICS */

.CodeMirror {
  /* Set height, width, borders, and global font properties here */
  font-family: monospace;
  height: 300px;
  color: black;
  direction: ltr;
}

/* PADDING */

.CodeMirror-lines {
  padding: 4px 0; /* Vertical padding around content */
}
.CodeMirror pre.CodeMirror-line,
.CodeMirror pre.CodeMirror-line-like {
  padding: 0 4px; /* Horizontal padding of content */
}

.CodeMirror-scrollbar-filler, .CodeMirror-gutter-filler {
  background-color: white; /* The little square between H and V scrollbars */
}

/* GUTTER */

.CodeMirror-gutters {
  border-right: 1px solid #ddd;
  background-color: #f7f7f7;
  white-space: nowrap;
}
.CodeMirror-linenumbers {}
.CodeMirror-linenumber {
  padding: 0 3px 0 5px;
  min-width: 20px;
  text-align: right;
  color: #999;
  white-space: nowrap;
}

.CodeMirror-guttermarker { color: black; }
.CodeMirror-guttermarker-subtle { color: #999; }

/* CURSOR */

.CodeMirror-cursor {
  border-left: 1px solid black;
  border-right: none;
  width: 0;
}
/* Shown when moving in bi-directional text */
.CodeMirror div.CodeMirror-secondarycursor {
  border-left: 1px solid silver;
}
.cm-fat-cursor .CodeMirror-cursor {
  width: auto;
  border: 0 !important;
  background: #7e7;
}
.cm-fat-cursor div.CodeMirror-cursors {
  z-index: 1;
}
.cm-fat-cursor-mark {
  background-color: rgba(20, 255, 20, 0.5);
  -webkit-animation: blink 1.06s steps(1) infinite;
  -moz-animation: blink 1.06s steps(1) infinite;
  animation: blink 1.06s steps(1) infinite;
}
.cm-animate-fat-cursor {
  width: auto;
  border: 0;
  -webkit-animation: blink 1.06s steps(1) infinite;
  -moz-animation: blink 1.06s steps(1) infinite;
  animation: blink 1.06s steps(1) infinite;
  background-color: #7e7;
}
@-moz-keyframes blink {
  0% {}
  50% { background-color: transparent; }
  100% {}
}
@-webkit-keyframes blink {
  0% {}
  50% { background-color: transparent; }
  100% {}
}
@keyframes blink {
  0% {}
  50% { background-color: transparent; }
  100% {}
}

/* Can style cursor different in overwrite (non-insert) mode */
.CodeMirror-overwrite .CodeMirror-cursor {}

.cm-tab { display: inline-block; text-decoration: inherit; }

.CodeMirror-rulers {
  position: absolute;
  left: 0; right: 0; top: -50px; bottom: 0;
  overflow: hidden;
}
.CodeMirror-ruler {
  border-left: 1px solid #ccc;
  top: 0; bottom: 0;
  position: absolute;
}

/* DEFAULT THEME */

.cm-s-default .cm-header {color: blue;}
.cm-s-default .cm-quote {color: #090;}
.cm-negative {color: #d44;}
.cm-positive {color: #292;}
.cm-header, .cm-strong {font-weight: bold;}
.cm-em {font-style: italic;}
.cm-link {text-decoration: underline;}
.cm-strikethrough {text-decoration: line-through;}

.cm-s-default .cm-keyword {color: #708;}
.cm-s-default .cm-atom {color: #219;}
.cm-s-default .cm-number {color: #164;}
.cm-s-default .cm-def {color: #00f;}
.cm-s-default .cm-variable,
.cm-s-default .cm-punctuation,
.cm-s-default .cm-property,
.cm-s-default .cm-operator {}
.cm-s-default .cm-variable-2 {color: #05a;}
.cm-s-default .cm-variable-3, .cm-s-default .cm-type {color: #085;}
.cm-s-default .cm-comment {color: #a50;}
.cm-s-default .cm-string {color: #a11;}
.cm-s-default .cm-string-2 {color: #f50;}
.cm-s-default .cm-meta {color: #555;}
.cm-s-default .cm-qualifier {color: #555;}
.cm-s-default .cm-builtin {color: #30a;}
.cm-s-default .cm-bracket {color: #997;}
.cm-s-default .cm-tag {color: #170;}
.cm-s-default .cm-attribute {color: #00c;}
.cm-s-default .cm-hr {color: #999;}
.cm-s-default .cm-link {color: #00c;}

.cm-s-default .cm-error {color: #f00;}
.cm-invalidchar {color: #f00;}

.CodeMirror-composing { border-bottom: 2px solid; }

/* Default styles for common addons */

div.CodeMirror span.CodeMirror-matchingbracket {color: #0b0;}
div.CodeMirror span.CodeMirror-nonmatchingbracket {color: #a22;}
.CodeMirror-matchingtag { background: rgba(255, 150, 0, .3); }
.CodeMirror-activeline-background {background: #e8f2ff;}

/* STOP */

/* The rest of this file contains styles related to the mechanics of
   the editor. You probably shouldn't touch them. */

.CodeMirror {
  position: relative;
  overflow: hidden;
  background: white;
}

.CodeMirror-scroll {
  overflow: scroll !important; /* Things will break if this is overridden */
  /* 50px is the magic margin used to hide the element's real scrollbars */
  /* See overflow: hidden in .CodeMirror */
  margin-bottom: -50px; margin-right: -50px;
  padding-bottom: 50px;
  height: 100%;
  outline: none; /* Prevent dragging from highlighting the element */
  position: relative;
}
.CodeMirror-sizer {
  position: relative;
  border-right: 50px solid transparent;
}

/* The fake, visible scrollbars. Used to force redraw during scrolling
   before actual scrolling happens, thus preventing shaking and
   flickering artifacts. */
.CodeMirror-vscrollbar, .CodeMirror-hscrollbar, .CodeMirror-scrollbar-filler, .CodeMirror-gutter-filler {
  position: absolute;
  z-index: 6;
  display: none;
  outline: none;
}
.CodeMirror-vscrollbar {
  right: 0; top: 0;
  overflow-x: hidden;
  overflow-y: scroll;
}
.CodeMirror-hscrollbar {
  bottom: 0; left: 0;
  overflow-y: hidden;
  overflow-x: scroll;
}
.CodeMirror-scrollbar-filler {
  right: 0; bottom: 0;
}
.CodeMirror-gutter-filler {
  left: 0; bottom: 0;
}

.CodeMirror-gutters {
  position: absolute; left: 0; top: 0;
  min-height: 100%;
  z-index: 3;
}
.CodeMirror-gutter {
  white-space: normal;
  height: 100%;
  display: inline-block;
  vertical-align: top;
  margin-bottom: -50px;
}
.CodeMirror-gutter-wrapper {
  position: absolute;
  z-index: 4;
  background: none !important;
  border: none !important;
}
.CodeMirror-gutter-background {
  position: absolute;
  top: 0; bottom: 0;
  z-index: 4;
}
.CodeMirror-gutter-elt {
  position: absolute;
  cursor: default;
  z-index: 4;
}
.CodeMirror-gutter-wrapper ::selection { background-color: transparent }
.CodeMirror-gutter-wrapper ::-moz-selection { background-color: transparent }

.CodeMirror-lines {
  cursor: text;
  min-height: 1px; /* prevents collapsing before first draw */
}
.CodeMirror pre.CodeMirror-line,
.CodeMirror pre.CodeMirror-line-like {
  /* Reset some styles that the rest of the page might have set */
  -moz-border-radius: 0; -webkit-border-radius: 0; border-radius: 0;
  border-width: 0;
  background: transparent;
  font-family: inherit;
  font-size: inherit;
  margin: 0;
  white-space: pre;
  word-wrap: normal;
  line-height: inherit;
  color: inherit;
  z-index: 2;
  position: relative;
  overflow: visible;
  -webkit-tap-highlight-color: transparent;
  -webkit-font-variant-ligatures: contextual;
  font-variant-ligatures: contextual;
}
.CodeMirror-wrap pre.CodeMirror-line,
.CodeMirror-wrap pre.CodeMirror-line-like {
  word-wrap: break-word;
  white-space: pre-wrap;
  word-break: normal;
}

.CodeMirror-linebackground {
  position: absolute;
  left: 0; right: 0; top: 0; bottom: 0;
  z-index: 0;
}

.CodeMirror-linewidget {
  position: relative;
  z-index: 2;
  padding: 0.1px; /* Force widget margins to stay inside of the container */
}

.CodeMirror-widget {}

.CodeMirror-rtl pre { direction: rtl; }

.CodeMirror-code {
  outline: none;
}

/* Force content-box sizing for the elements where we expect it */
.CodeMirror-scroll,
.CodeMirror-sizer,
.CodeMirror-gutter,
.CodeMirror-gutters,
.CodeMirror-linenumber {
  -moz-box-sizing: content-box;
  box-sizing: content-box;
}

.CodeMirror-measure {
  position: absolute;
  width: 100%;
  height: 0;
  overflow: hidden;
  visibility: hidden;
}

.CodeMirror-cursor {
  position: absolute;
  pointer-events: none;
}
.CodeMirror-measure pre { position: static; }

div.CodeMirror-cursors {
  visibility: hidden;
  position: relative;
  z-index: 3;
}
div.CodeMirror-dragcursors {
  visibility: visible;
}

.CodeMirror-focused div.CodeMirror-cursors {
  visibility: visible;
}

.CodeMirror-selected { background: #d9d9d9; }
.CodeMirror-focused .CodeMirror-selected { background: #d7d4f0; }
.CodeMirror-crosshair { cursor: crosshair; }
.CodeMirror-line::selection, .CodeMirror-line > span::selection, .CodeMirror-line > span > span::selection { background: #d7d4f0; }
.CodeMirror-line::-moz-selection, .CodeMirror-line > span::-moz-selection, .CodeMirror-line > span > span::-moz-selection { background: #d7d4f0; }

.cm-searching {
  background-color: #ffa;
  background-color: rgba(255, 255, 0, .4);
}

/* Used to force a border model for a node */
.cm-force-border { padding-right: .1px; }

@media print {
  /* Hide the cursor when printing */
  .CodeMirror div.CodeMirror-cursors {
    visibility: hidden;
  }
}

/* See issue #2901 */
.cm-tab-wrap-hack:after { content: ''; }

/* Help users use markselection to safely style text background */
span.CodeMirror-selectedtext { background: none; }

.CodeMirror-dialog {
  position: absolute;
  left: 0; right: 0;
  background: inherit;
  z-index: 15;
  padding: .1em .8em;
  overflow: hidden;
  color: inherit;
}

.CodeMirror-dialog-top {
  border-bottom: 1px solid #eee;
  top: 0;
}

.CodeMirror-dialog-bottom {
  border-top: 1px solid #eee;
  bottom: 0;
}

.CodeMirror-dialog input {
  border: none;
  outline: none;
  background: transparent;
  width: 20em;
  color: inherit;
  font-family: monospace;
}

.CodeMirror-dialog button {
  font-size: 70%;
}

.CodeMirror-foldmarker {
  color: blue;
  text-shadow: #b9f 1px 1px 2px, #b9f -1px -1px 2px, #b9f 1px -1px 2px, #b9f -1px 1px 2px;
  font-family: arial;
  line-height: .3;
  cursor: pointer;
}
.CodeMirror-foldgutter {
  width: .7em;
}
.CodeMirror-foldgutter-open,
.CodeMirror-foldgutter-folded {
  cursor: pointer;
}
.CodeMirror-foldgutter-open:after {
  content: "\25BE";
}
.CodeMirror-foldgutter-folded:after {
  content: "\25B8";
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.CodeMirror {
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  font-family: var(--jp-code-font-family);
  border: 0;
  border-radius: 0;
  height: auto;
  /* Changed to auto to autogrow */
}

.CodeMirror pre {
  padding: 0 var(--jp-code-padding);
}

.jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-dialog {
  background-color: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
}

/* This causes https://github.com/jupyter/jupyterlab/issues/522 */
/* May not cause it not because we changed it! */
.CodeMirror-lines {
  padding: var(--jp-code-padding) 0;
}

.CodeMirror-linenumber {
  padding: 0 8px;
}

.jp-CodeMirrorEditor {
  cursor: text;
}

.jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
  border-left: var(--jp-code-cursor-width0) solid var(--jp-editor-cursor-color);
}

/* When zoomed out 67% and 33% on a screen of 1440 width x 900 height */
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
    border-left: var(--jp-code-cursor-width1) solid
      var(--jp-editor-cursor-color);
  }
}

/* When zoomed out less than 33% */
@media screen and (min-width: 4320px) {
  .jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
    border-left: var(--jp-code-cursor-width2) solid
      var(--jp-editor-cursor-color);
  }
}

.CodeMirror.jp-mod-readOnly .CodeMirror-cursor {
  display: none;
}

.CodeMirror-gutters {
  border-right: 1px solid var(--jp-border-color2);
  background-color: var(--jp-layout-color0);
}

.jp-CollaboratorCursor {
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: none;
  border-bottom: 3px solid;
  background-clip: content-box;
  margin-left: -5px;
  margin-right: -5px;
}

.CodeMirror-selectedtext.cm-searching {
  background-color: var(--jp-search-selected-match-background-color) !important;
  color: var(--jp-search-selected-match-color) !important;
}

.cm-searching {
  background-color: var(
    --jp-search-unselected-match-background-color
  ) !important;
  color: var(--jp-search-unselected-match-color) !important;
}

.CodeMirror-focused .CodeMirror-selected {
  background-color: var(--jp-editor-selected-focused-background);
}

.CodeMirror-selected {
  background-color: var(--jp-editor-selected-background);
}

.jp-CollaboratorCursor-hover {
  position: absolute;
  z-index: 1;
  transform: translateX(-50%);
  color: white;
  border-radius: 3px;
  padding-left: 4px;
  padding-right: 4px;
  padding-top: 1px;
  padding-bottom: 1px;
  text-align: center;
  font-size: var(--jp-ui-font-size1);
  white-space: nowrap;
}

.jp-CodeMirror-ruler {
  border-left: 1px dashed var(--jp-border-color2);
}

/**
 * Here is our jupyter theme for CodeMirror syntax highlighting
 * This is used in our marked.js syntax highlighting and CodeMirror itself
 * The string "jupyter" is set in ../codemirror/widget.DEFAULT_CODEMIRROR_THEME
 * This came from the classic notebook, which came form highlight.js/GitHub
 */

/**
 * CodeMirror themes are handling the background/color in this way. This works
 * fine for CodeMirror editors outside the notebook, but the notebook styles
 * these things differently.
 */
.CodeMirror.cm-s-jupyter {
  background: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
}

/* In the notebook, we want this styling to be handled by its container */
.jp-CodeConsole .CodeMirror.cm-s-jupyter,
.jp-Notebook .CodeMirror.cm-s-jupyter {
  background: transparent;
}

.cm-s-jupyter .CodeMirror-cursor {
  border-left: var(--jp-code-cursor-width0) solid var(--jp-editor-cursor-color);
}
.cm-s-jupyter span.cm-keyword {
  color: var(--jp-mirror-editor-keyword-color);
  font-weight: bold;
}
.cm-s-jupyter span.cm-atom {
  color: var(--jp-mirror-editor-atom-color);
}
.cm-s-jupyter span.cm-number {
  color: var(--jp-mirror-editor-number-color);
}
.cm-s-jupyter span.cm-def {
  color: var(--jp-mirror-editor-def-color);
}
.cm-s-jupyter span.cm-variable {
  color: var(--jp-mirror-editor-variable-color);
}
.cm-s-jupyter span.cm-variable-2 {
  color: var(--jp-mirror-editor-variable-2-color);
}
.cm-s-jupyter span.cm-variable-3 {
  color: var(--jp-mirror-editor-variable-3-color);
}
.cm-s-jupyter span.cm-punctuation {
  color: var(--jp-mirror-editor-punctuation-color);
}
.cm-s-jupyter span.cm-property {
  color: var(--jp-mirror-editor-property-color);
}
.cm-s-jupyter span.cm-operator {
  color: var(--jp-mirror-editor-operator-color);
  font-weight: bold;
}
.cm-s-jupyter span.cm-comment {
  color: var(--jp-mirror-editor-comment-color);
  font-style: italic;
}
.cm-s-jupyter span.cm-string {
  color: var(--jp-mirror-editor-string-color);
}
.cm-s-jupyter span.cm-string-2 {
  color: var(--jp-mirror-editor-string-2-color);
}
.cm-s-jupyter span.cm-meta {
  color: var(--jp-mirror-editor-meta-color);
}
.cm-s-jupyter span.cm-qualifier {
  color: var(--jp-mirror-editor-qualifier-color);
}
.cm-s-jupyter span.cm-builtin {
  color: var(--jp-mirror-editor-builtin-color);
}
.cm-s-jupyter span.cm-bracket {
  color: var(--jp-mirror-editor-bracket-color);
}
.cm-s-jupyter span.cm-tag {
  color: var(--jp-mirror-editor-tag-color);
}
.cm-s-jupyter span.cm-attribute {
  color: var(--jp-mirror-editor-attribute-color);
}
.cm-s-jupyter span.cm-header {
  color: var(--jp-mirror-editor-header-color);
}
.cm-s-jupyter span.cm-quote {
  color: var(--jp-mirror-editor-quote-color);
}
.cm-s-jupyter span.cm-link {
  color: var(--jp-mirror-editor-link-color);
}
.cm-s-jupyter span.cm-error {
  color: var(--jp-mirror-editor-error-color);
}
.cm-s-jupyter span.cm-hr {
  color: #999;
}

.cm-s-jupyter span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}

.cm-s-jupyter .CodeMirror-activeline-background,
.cm-s-jupyter .CodeMirror-gutter {
  background-color: var(--jp-layout-color2);
}

/* Styles for shared cursors (remote cursor locations and selected ranges) */
.jp-CodeMirrorEditor .remote-caret {
  position: relative;
  border-left: 2px solid black;
  margin-left: -1px;
  margin-right: -1px;
  box-sizing: border-box;
}

.jp-CodeMirrorEditor .remote-caret > div {
  white-space: nowrap;
  position: absolute;
  top: -1.15em;
  padding-bottom: 0.05em;
  left: -2px;
  font-size: 0.95em;
  background-color: rgb(250, 129, 0);
  font-family: var(--jp-ui-font-family);
  font-weight: bold;
  line-height: normal;
  user-select: none;
  color: white;
  padding-left: 2px;
  padding-right: 2px;
  z-index: 3;
  transition: opacity 0.3s ease-in-out;
}

.jp-CodeMirrorEditor .remote-caret.hide-name > div {
  transition-delay: 0.7s;
  opacity: 0;
}

.jp-CodeMirrorEditor .remote-caret:hover > div {
  opacity: 1;
  transition-delay: 0s;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| RenderedText
|----------------------------------------------------------------------------*/

:root {
  /* This is the padding value to fill the gaps between lines containing spans with background color. */
  --jp-private-code-span-padding: calc(
    (var(--jp-code-line-height) - 1) * var(--jp-code-font-size) / 2
  );
}

.jp-RenderedText {
  text-align: left;
  padding-left: var(--jp-code-padding);
  line-height: var(--jp-code-line-height);
  font-family: var(--jp-code-font-family);
}

.jp-RenderedText pre,
.jp-RenderedJavaScript pre,
.jp-RenderedHTMLCommon pre {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-code-font-size);
  border: none;
  margin: 0px;
  padding: 0px;
}

.jp-RenderedText pre a:link {
  text-decoration: none;
  color: var(--jp-content-link-color);
}
.jp-RenderedText pre a:hover {
  text-decoration: underline;
  color: var(--jp-content-link-color);
}
.jp-RenderedText pre a:visited {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

/* console foregrounds and backgrounds */
.jp-RenderedText pre .ansi-black-fg {
  color: #3e424d;
}
.jp-RenderedText pre .ansi-red-fg {
  color: #e75c58;
}
.jp-RenderedText pre .ansi-green-fg {
  color: #00a250;
}
.jp-RenderedText pre .ansi-yellow-fg {
  color: #ddb62b;
}
.jp-RenderedText pre .ansi-blue-fg {
  color: #208ffb;
}
.jp-RenderedText pre .ansi-magenta-fg {
  color: #d160c4;
}
.jp-RenderedText pre .ansi-cyan-fg {
  color: #60c6c8;
}
.jp-RenderedText pre .ansi-white-fg {
  color: #c5c1b4;
}

.jp-RenderedText pre .ansi-black-bg {
  background-color: #3e424d;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-red-bg {
  background-color: #e75c58;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-green-bg {
  background-color: #00a250;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-yellow-bg {
  background-color: #ddb62b;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-blue-bg {
  background-color: #208ffb;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-magenta-bg {
  background-color: #d160c4;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-cyan-bg {
  background-color: #60c6c8;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-white-bg {
  background-color: #c5c1b4;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-black-intense-fg {
  color: #282c36;
}
.jp-RenderedText pre .ansi-red-intense-fg {
  color: #b22b31;
}
.jp-RenderedText pre .ansi-green-intense-fg {
  color: #007427;
}
.jp-RenderedText pre .ansi-yellow-intense-fg {
  color: #b27d12;
}
.jp-RenderedText pre .ansi-blue-intense-fg {
  color: #0065ca;
}
.jp-RenderedText pre .ansi-magenta-intense-fg {
  color: #a03196;
}
.jp-RenderedText pre .ansi-cyan-intense-fg {
  color: #258f8f;
}
.jp-RenderedText pre .ansi-white-intense-fg {
  color: #a1a6b2;
}

.jp-RenderedText pre .ansi-black-intense-bg {
  background-color: #282c36;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-red-intense-bg {
  background-color: #b22b31;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-green-intense-bg {
  background-color: #007427;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-yellow-intense-bg {
  background-color: #b27d12;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-blue-intense-bg {
  background-color: #0065ca;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-magenta-intense-bg {
  background-color: #a03196;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-cyan-intense-bg {
  background-color: #258f8f;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-white-intense-bg {
  background-color: #a1a6b2;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-default-inverse-fg {
  color: var(--jp-ui-inverse-font-color0);
}
.jp-RenderedText pre .ansi-default-inverse-bg {
  background-color: var(--jp-inverse-layout-color0);
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-bold {
  font-weight: bold;
}
.jp-RenderedText pre .ansi-underline {
  text-decoration: underline;
}

.jp-RenderedText[data-mime-type='application/vnd.jupyter.stderr'] {
  background: var(--jp-rendermime-error-background);
  padding-top: var(--jp-code-padding);
}

/*-----------------------------------------------------------------------------
| RenderedLatex
|----------------------------------------------------------------------------*/

.jp-RenderedLatex {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-content-font-size1);
  line-height: var(--jp-content-line-height);
}

/* Left-justify outputs.*/
.jp-OutputArea-output.jp-RenderedLatex {
  padding: var(--jp-code-padding);
  text-align: left;
}

/*-----------------------------------------------------------------------------
| RenderedHTML
|----------------------------------------------------------------------------*/

.jp-RenderedHTMLCommon {
  color: var(--jp-content-font-color1);
  font-family: var(--jp-content-font-family);
  font-size: var(--jp-content-font-size1);
  line-height: var(--jp-content-line-height);
  /* Give a bit more R padding on Markdown text to keep line lengths reasonable */
  padding-right: 20px;
}

.jp-RenderedHTMLCommon em {
  font-style: italic;
}

.jp-RenderedHTMLCommon strong {
  font-weight: bold;
}

.jp-RenderedHTMLCommon u {
  text-decoration: underline;
}

.jp-RenderedHTMLCommon a:link {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

.jp-RenderedHTMLCommon a:hover {
  text-decoration: underline;
  color: var(--jp-content-link-color);
}

.jp-RenderedHTMLCommon a:visited {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

/* Headings */

.jp-RenderedHTMLCommon h1,
.jp-RenderedHTMLCommon h2,
.jp-RenderedHTMLCommon h3,
.jp-RenderedHTMLCommon h4,
.jp-RenderedHTMLCommon h5,
.jp-RenderedHTMLCommon h6 {
  line-height: var(--jp-content-heading-line-height);
  font-weight: var(--jp-content-heading-font-weight);
  font-style: normal;
  margin: var(--jp-content-heading-margin-top) 0
    var(--jp-content-heading-margin-bottom) 0;
}

.jp-RenderedHTMLCommon h1:first-child,
.jp-RenderedHTMLCommon h2:first-child,
.jp-RenderedHTMLCommon h3:first-child,
.jp-RenderedHTMLCommon h4:first-child,
.jp-RenderedHTMLCommon h5:first-child,
.jp-RenderedHTMLCommon h6:first-child {
  margin-top: calc(0.5 * var(--jp-content-heading-margin-top));
}

.jp-RenderedHTMLCommon h1:last-child,
.jp-RenderedHTMLCommon h2:last-child,
.jp-RenderedHTMLCommon h3:last-child,
.jp-RenderedHTMLCommon h4:last-child,
.jp-RenderedHTMLCommon h5:last-child,
.jp-RenderedHTMLCommon h6:last-child {
  margin-bottom: calc(0.5 * var(--jp-content-heading-margin-bottom));
}

.jp-RenderedHTMLCommon h1 {
  font-size: var(--jp-content-font-size5);
}

.jp-RenderedHTMLCommon h2 {
  font-size: var(--jp-content-font-size4);
}

.jp-RenderedHTMLCommon h3 {
  font-size: var(--jp-content-font-size3);
}

.jp-RenderedHTMLCommon h4 {
  font-size: var(--jp-content-font-size2);
}

.jp-RenderedHTMLCommon h5 {
  font-size: var(--jp-content-font-size1);
}

.jp-RenderedHTMLCommon h6 {
  font-size: var(--jp-content-font-size0);
}

/* Lists */

.jp-RenderedHTMLCommon ul:not(.list-inline),
.jp-RenderedHTMLCommon ol:not(.list-inline) {
  padding-left: 2em;
}

.jp-RenderedHTMLCommon ul {
  list-style: disc;
}

.jp-RenderedHTMLCommon ul ul {
  list-style: square;
}

.jp-RenderedHTMLCommon ul ul ul {
  list-style: circle;
}

.jp-RenderedHTMLCommon ol {
  list-style: decimal;
}

.jp-RenderedHTMLCommon ol ol {
  list-style: upper-alpha;
}

.jp-RenderedHTMLCommon ol ol ol {
  list-style: lower-alpha;
}

.jp-RenderedHTMLCommon ol ol ol ol {
  list-style: lower-roman;
}

.jp-RenderedHTMLCommon ol ol ol ol ol {
  list-style: decimal;
}

.jp-RenderedHTMLCommon ol,
.jp-RenderedHTMLCommon ul {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon ul ul,
.jp-RenderedHTMLCommon ul ol,
.jp-RenderedHTMLCommon ol ul,
.jp-RenderedHTMLCommon ol ol {
  margin-bottom: 0em;
}

.jp-RenderedHTMLCommon hr {
  color: var(--jp-border-color2);
  background-color: var(--jp-border-color1);
  margin-top: 1em;
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon > pre {
  margin: 1.5em 2em;
}

.jp-RenderedHTMLCommon pre,
.jp-RenderedHTMLCommon code {
  border: 0;
  background-color: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
  font-family: var(--jp-code-font-family);
  font-size: inherit;
  line-height: var(--jp-code-line-height);
  padding: 0;
  white-space: pre-wrap;
}

.jp-RenderedHTMLCommon :not(pre) > code {
  background-color: var(--jp-layout-color2);
  padding: 1px 5px;
}

/* Tables */

.jp-RenderedHTMLCommon table {
  border-collapse: collapse;
  border-spacing: 0;
  border: none;
  color: var(--jp-ui-font-color1);
  font-size: 12px;
  table-layout: fixed;
  margin-left: auto;
  margin-right: auto;
}

.jp-RenderedHTMLCommon thead {
  border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
  vertical-align: bottom;
}

.jp-RenderedHTMLCommon td,
.jp-RenderedHTMLCommon th,
.jp-RenderedHTMLCommon tr {
  vertical-align: middle;
  padding: 0.5em 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}

.jp-RenderedMarkdown.jp-RenderedHTMLCommon td,
.jp-RenderedMarkdown.jp-RenderedHTMLCommon th {
  max-width: none;
}

:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon td,
:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon th,
:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon tr {
  text-align: right;
}

.jp-RenderedHTMLCommon th {
  font-weight: bold;
}

.jp-RenderedHTMLCommon tbody tr:nth-child(odd) {
  background: var(--jp-layout-color0);
}

.jp-RenderedHTMLCommon tbody tr:nth-child(even) {
  background: var(--jp-rendermime-table-row-background);
}

.jp-RenderedHTMLCommon tbody tr:hover {
  background: var(--jp-rendermime-table-row-hover-background);
}

.jp-RenderedHTMLCommon table {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon p {
  text-align: left;
  margin: 0px;
}

.jp-RenderedHTMLCommon p {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon img {
  -moz-force-broken-image-icon: 1;
}

/* Restrict to direct children as other images could be nested in other content. */
.jp-RenderedHTMLCommon > img {
  display: block;
  margin-left: 0;
  margin-right: 0;
  margin-bottom: 1em;
}

/* Change color behind transparent images if they need it... */
[data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-light-background {
  background-color: var(--jp-inverse-layout-color1);
}
[data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-dark-background {
  background-color: var(--jp-inverse-layout-color1);
}
/* ...or leave it untouched if they don't */
[data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-dark-background {
}
[data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-light-background {
}

.jp-RenderedHTMLCommon img,
.jp-RenderedImage img,
.jp-RenderedHTMLCommon svg,
.jp-RenderedSVG svg {
  max-width: 100%;
  height: auto;
}

.jp-RenderedHTMLCommon img.jp-mod-unconfined,
.jp-RenderedImage img.jp-mod-unconfined,
.jp-RenderedHTMLCommon svg.jp-mod-unconfined,
.jp-RenderedSVG svg.jp-mod-unconfined {
  max-width: none;
}

.jp-RenderedHTMLCommon .alert {
  padding: var(--jp-notebook-padding);
  border: var(--jp-border-width) solid transparent;
  border-radius: var(--jp-border-radius);
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon .alert-info {
  color: var(--jp-info-color0);
  background-color: var(--jp-info-color3);
  border-color: var(--jp-info-color2);
}
.jp-RenderedHTMLCommon .alert-info hr {
  border-color: var(--jp-info-color3);
}
.jp-RenderedHTMLCommon .alert-info > p:last-child,
.jp-RenderedHTMLCommon .alert-info > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-warning {
  color: var(--jp-warn-color0);
  background-color: var(--jp-warn-color3);
  border-color: var(--jp-warn-color2);
}
.jp-RenderedHTMLCommon .alert-warning hr {
  border-color: var(--jp-warn-color3);
}
.jp-RenderedHTMLCommon .alert-warning > p:last-child,
.jp-RenderedHTMLCommon .alert-warning > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-success {
  color: var(--jp-success-color0);
  background-color: var(--jp-success-color3);
  border-color: var(--jp-success-color2);
}
.jp-RenderedHTMLCommon .alert-success hr {
  border-color: var(--jp-success-color3);
}
.jp-RenderedHTMLCommon .alert-success > p:last-child,
.jp-RenderedHTMLCommon .alert-success > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-danger {
  color: var(--jp-error-color0);
  background-color: var(--jp-error-color3);
  border-color: var(--jp-error-color2);
}
.jp-RenderedHTMLCommon .alert-danger hr {
  border-color: var(--jp-error-color3);
}
.jp-RenderedHTMLCommon .alert-danger > p:last-child,
.jp-RenderedHTMLCommon .alert-danger > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon blockquote {
  margin: 1em 2em;
  padding: 0 1em;
  border-left: 5px solid var(--jp-border-color2);
}

a.jp-InternalAnchorLink {
  visibility: hidden;
  margin-left: 8px;
  color: var(--md-blue-800);
}

h1:hover .jp-InternalAnchorLink,
h2:hover .jp-InternalAnchorLink,
h3:hover .jp-InternalAnchorLink,
h4:hover .jp-InternalAnchorLink,
h5:hover .jp-InternalAnchorLink,
h6:hover .jp-InternalAnchorLink {
  visibility: visible;
}

.jp-RenderedHTMLCommon kbd {
  background-color: var(--jp-rendermime-table-row-background);
  border: 1px solid var(--jp-border-color0);
  border-bottom-color: var(--jp-border-color2);
  border-radius: 3px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
  display: inline-block;
  font-size: 0.8em;
  line-height: 1em;
  padding: 0.2em 0.5em;
}

/* Most direct children of .jp-RenderedHTMLCommon have a margin-bottom of 1.0.
 * At the bottom of cells this is a bit too much as there is also spacing
 * between cells. Going all the way to 0 gets too tight between markdown and
 * code cells.
 */
.jp-RenderedHTMLCommon > *:last-child {
  margin-bottom: 0.5em;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-MimeDocument {
  outline: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-filebrowser-button-height: 28px;
  --jp-private-filebrowser-button-width: 48px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-FileBrowser {
  display: flex;
  flex-direction: column;
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
}

.jp-FileBrowser-toolbar.jp-Toolbar {
  border-bottom: none;
  height: auto;
  margin: var(--jp-toolbar-header-margin);
  box-shadow: none;
}

.jp-BreadCrumbs {
  flex: 0 0 auto;
  margin: 8px 12px 8px 12px;
}

.jp-BreadCrumbs-item {
  margin: 0px 2px;
  padding: 0px 2px;
  border-radius: var(--jp-border-radius);
  cursor: pointer;
}

.jp-BreadCrumbs-item:hover {
  background-color: var(--jp-layout-color2);
}

.jp-BreadCrumbs-item:first-child {
  margin-left: 0px;
}

.jp-BreadCrumbs-item.jp-mod-dropTarget {
  background-color: var(--jp-brand-color2);
  opacity: 0.7;
}

/*-----------------------------------------------------------------------------
| Buttons
|----------------------------------------------------------------------------*/

.jp-FileBrowser-toolbar.jp-Toolbar {
  padding: 0px;
  margin: 8px 12px 0px 12px;
}

.jp-FileBrowser-toolbar.jp-Toolbar {
  justify-content: flex-start;
}

.jp-FileBrowser-toolbar.jp-Toolbar .jp-Toolbar-item {
  flex: 0 0 auto;
  padding-left: 0px;
  padding-right: 2px;
}

.jp-FileBrowser-toolbar.jp-Toolbar .jp-ToolbarButtonComponent {
  width: 40px;
}

.jp-FileBrowser-toolbar.jp-Toolbar
  .jp-Toolbar-item:first-child
  .jp-ToolbarButtonComponent {
  width: 72px;
  background: var(--jp-brand-color1);
}

.jp-FileBrowser-toolbar.jp-Toolbar
  .jp-Toolbar-item:first-child
  .jp-ToolbarButtonComponent:focus-visible {
  background-color: var(--jp-brand-color0);
}

.jp-FileBrowser-toolbar.jp-Toolbar
  .jp-Toolbar-item:first-child
  .jp-ToolbarButtonComponent
  .jp-icon3 {
  fill: white;
}

/*-----------------------------------------------------------------------------
| Other styles
|----------------------------------------------------------------------------*/

.jp-FileDialog.jp-mod-conflict input {
  color: var(--jp-error-color1);
}

.jp-FileDialog .jp-new-name-title {
  margin-top: 12px;
}

.jp-LastModified-hidden {
  display: none;
}

.jp-FileBrowser-filterBox {
  padding: 0px;
  flex: 0 0 auto;
  margin: 8px 12px 0px 12px;
}

/*-----------------------------------------------------------------------------
| DirListing
|----------------------------------------------------------------------------*/

.jp-DirListing {
  flex: 1 1 auto;
  display: flex;
  flex-direction: column;
  outline: 0;
}

.jp-DirListing:focus-visible {
  border: 1px solid var(--jp-brand-color1);
}

.jp-DirListing-header {
  flex: 0 0 auto;
  display: flex;
  flex-direction: row;
  overflow: hidden;
  border-top: var(--jp-border-width) solid var(--jp-border-color2);
  border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
  box-shadow: var(--jp-toolbar-box-shadow);
  z-index: 2;
}

.jp-DirListing-headerItem {
  padding: 4px 12px 2px 12px;
  font-weight: 500;
}

.jp-DirListing-headerItem:hover {
  background: var(--jp-layout-color2);
}

.jp-DirListing-headerItem.jp-id-name {
  flex: 1 0 84px;
}

.jp-DirListing-headerItem.jp-id-modified {
  flex: 0 0 112px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
}

.jp-id-narrow {
  display: none;
  flex: 0 0 5px;
  padding: 4px 4px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
  color: var(--jp-border-color2);
}

.jp-DirListing-narrow .jp-id-narrow {
  display: block;
}

.jp-DirListing-narrow .jp-id-modified,
.jp-DirListing-narrow .jp-DirListing-itemModified {
  display: none;
}

.jp-DirListing-headerItem.jp-mod-selected {
  font-weight: 600;
}

/* increase specificity to override bundled default */
.jp-DirListing-content {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  list-style-type: none;
  overflow: auto;
  background-color: var(--jp-layout-color1);
}

.jp-DirListing-content mark {
  color: var(--jp-ui-font-color0);
  background-color: transparent;
  font-weight: bold;
}

.jp-DirListing-content .jp-DirListing-item.jp-mod-selected mark {
  color: var(--jp-ui-inverse-font-color0);
}

/* Style the directory listing content when a user drops a file to upload */
.jp-DirListing.jp-mod-native-drop .jp-DirListing-content {
  outline: 5px dashed rgba(128, 128, 128, 0.5);
  outline-offset: -10px;
  cursor: copy;
}

.jp-DirListing-item {
  display: flex;
  flex-direction: row;
  padding: 4px 12px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.jp-DirListing-item[data-is-dot] {
  opacity: 75%;
}

.jp-DirListing-item.jp-mod-selected {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.jp-DirListing-item.jp-mod-dropTarget {
  background: var(--jp-brand-color3);
}

.jp-DirListing-item:hover:not(.jp-mod-selected) {
  background: var(--jp-layout-color2);
}

.jp-DirListing-itemIcon {
  flex: 0 0 20px;
  margin-right: 4px;
}

.jp-DirListing-itemText {
  flex: 1 0 64px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  user-select: none;
}

.jp-DirListing-itemModified {
  flex: 0 0 125px;
  text-align: right;
}

.jp-DirListing-editor {
  flex: 1 0 64px;
  outline: none;
  border: none;
}

.jp-DirListing-item.jp-mod-running .jp-DirListing-itemIcon:before {
  color: var(--jp-success-color1);
  content: '\25CF';
  font-size: 8px;
  position: absolute;
  left: -8px;
}

.jp-DirListing-item.jp-mod-running.jp-mod-selected
  .jp-DirListing-itemIcon:before {
  color: var(--jp-ui-inverse-font-color1);
}

.jp-DirListing-item.lm-mod-drag-image,
.jp-DirListing-item.jp-mod-selected.lm-mod-drag-image {
  font-size: var(--jp-ui-font-size1);
  padding-left: 4px;
  margin-left: 4px;
  width: 160px;
  background-color: var(--jp-ui-inverse-font-color2);
  box-shadow: var(--jp-elevation-z2);
  border-radius: 0px;
  color: var(--jp-ui-font-color1);
  transform: translateX(-40%) translateY(-58%);
}

.jp-DirListing-deadSpace {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  list-style-type: none;
  overflow: auto;
  background-color: var(--jp-layout-color1);
}

.jp-Document {
  min-width: 120px;
  min-height: 120px;
  outline: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
}

/*-----------------------------------------------------------------------------
| Main OutputArea
| OutputArea has a list of Outputs
|----------------------------------------------------------------------------*/

.jp-OutputArea {
  overflow-y: auto;
}

.jp-OutputArea-child {
  display: flex;
  flex-direction: row;
}

body[data-format='mobile'] .jp-OutputArea-child {
  flex-direction: column;
}

.jp-OutputPrompt {
  flex: 0 0 var(--jp-cell-prompt-width);
  color: var(--jp-cell-outprompt-font-color);
  font-family: var(--jp-cell-prompt-font-family);
  padding: var(--jp-code-padding);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
  opacity: var(--jp-cell-prompt-opacity);
  /* Right align prompt text, don't wrap to handle large prompt numbers */
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  /* Disable text selection */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

body[data-format='mobile'] .jp-OutputPrompt {
  flex: 0 0 auto;
  text-align: left;
}

.jp-OutputArea-output {
  height: auto;
  overflow: auto;
  user-select: text;
  -moz-user-select: text;
  -webkit-user-select: text;
  -ms-user-select: text;
}

.jp-OutputArea-child .jp-OutputArea-output {
  flex-grow: 1;
  flex-shrink: 1;
}

body[data-format='mobile'] .jp-OutputArea-child .jp-OutputArea-output {
  margin-left: var(--jp-notebook-padding);
}

/**
 * Isolated output.
 */
.jp-OutputArea-output.jp-mod-isolated {
  width: 100%;
  display: block;
}

/*
When drag events occur, `p-mod-override-cursor` is added to the body.
Because iframes steal all cursor events, the following two rules are necessary
to suppress pointer events while resize drags are occurring. There may be a
better solution to this problem.
*/
body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated {
  position: relative;
}

body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated:before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
}

/* pre */

.jp-OutputArea-output pre {
  border: none;
  margin: 0px;
  padding: 0px;
  overflow-x: auto;
  overflow-y: auto;
  word-break: break-all;
  word-wrap: break-word;
  white-space: pre-wrap;
}

/* tables */

.jp-OutputArea-output.jp-RenderedHTMLCommon table {
  margin-left: 0;
  margin-right: 0;
}

/* description lists */

.jp-OutputArea-output dl,
.jp-OutputArea-output dt,
.jp-OutputArea-output dd {
  display: block;
}

.jp-OutputArea-output dl {
  width: 100%;
  overflow: hidden;
  padding: 0;
  margin: 0;
}

.jp-OutputArea-output dt {
  font-weight: bold;
  float: left;
  width: 20%;
  padding: 0;
  margin: 0;
}

.jp-OutputArea-output dd {
  float: left;
  width: 80%;
  padding: 0;
  margin: 0;
}

/* Hide the gutter in case of
 *  - nested output areas (e.g. in the case of output widgets)
 *  - mirrored output areas
 */
.jp-OutputArea .jp-OutputArea .jp-OutputArea-prompt {
  display: none;
}

/*-----------------------------------------------------------------------------
| executeResult is added to any Output-result for the display of the object
| returned by a cell
|----------------------------------------------------------------------------*/

.jp-OutputArea-output.jp-OutputArea-executeResult {
  margin-left: 0px;
  flex: 1 1 auto;
}

/* Text output with the Out[] prompt needs a top padding to match the
 * alignment of the Out[] prompt itself.
 */
.jp-OutputArea-executeResult .jp-RenderedText.jp-OutputArea-output {
  padding-top: var(--jp-code-padding);
  border-top: var(--jp-border-width) solid transparent;
}

/*-----------------------------------------------------------------------------
| The Stdin output
|----------------------------------------------------------------------------*/

.jp-OutputArea-stdin {
  line-height: var(--jp-code-line-height);
  padding-top: var(--jp-code-padding);
  display: flex;
}

.jp-Stdin-prompt {
  color: var(--jp-content-font-color0);
  padding-right: var(--jp-code-padding);
  vertical-align: baseline;
  flex: 0 0 auto;
}

.jp-Stdin-input {
  font-family: var(--jp-code-font-family);
  font-size: inherit;
  color: inherit;
  background-color: inherit;
  width: 42%;
  min-width: 200px;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
  flex: 0 0 70%;
}

.jp-Stdin-input:focus {
  box-shadow: none;
}

/*-----------------------------------------------------------------------------
| Output Area View
|----------------------------------------------------------------------------*/

.jp-LinkedOutputView .jp-OutputArea {
  height: 100%;
  display: block;
}

.jp-LinkedOutputView .jp-OutputArea-output:only-child {
  height: 100%;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Collapser {
  flex: 0 0 var(--jp-cell-collapser-width);
  padding: 0px;
  margin: 0px;
  border: none;
  outline: none;
  background: transparent;
  border-radius: var(--jp-border-radius);
  opacity: 1;
}

.jp-Collapser-child {
  display: block;
  width: 100%;
  box-sizing: border-box;
  /* height: 100% doesn't work because the height of its parent is computed from content */
  position: absolute;
  top: 0px;
  bottom: 0px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Header/Footer
|----------------------------------------------------------------------------*/

/* Hidden by zero height by default */
.jp-CellHeader,
.jp-CellFooter {
  height: 0px;
  width: 100%;
  padding: 0px;
  margin: 0px;
  border: none;
  outline: none;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Input
|----------------------------------------------------------------------------*/

/* All input areas */
.jp-InputArea {
  display: flex;
  flex-direction: row;
  overflow: hidden;
}

body[data-format='mobile'] .jp-InputArea {
  flex-direction: column;
}

.jp-InputArea-editor {
  flex: 1 1 auto;
  overflow: hidden;
}

.jp-InputArea-editor {
  /* This is the non-active, default styling */
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  border-radius: 0px;
  background: var(--jp-cell-editor-background);
}

body[data-format='mobile'] .jp-InputArea-editor {
  margin-left: var(--jp-notebook-padding);
}

.jp-InputPrompt {
  flex: 0 0 var(--jp-cell-prompt-width);
  color: var(--jp-cell-inprompt-font-color);
  font-family: var(--jp-cell-prompt-font-family);
  padding: var(--jp-code-padding);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  opacity: var(--jp-cell-prompt-opacity);
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
  opacity: var(--jp-cell-prompt-opacity);
  /* Right align prompt text, don't wrap to handle large prompt numbers */
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  /* Disable text selection */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

body[data-format='mobile'] .jp-InputPrompt {
  flex: 0 0 auto;
  text-align: left;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Placeholder
|----------------------------------------------------------------------------*/

.jp-Placeholder {
  display: flex;
  flex-direction: row;
  flex: 1 1 auto;
}

.jp-Placeholder-prompt {
  box-sizing: border-box;
}

.jp-Placeholder-content {
  flex: 1 1 auto;
  border: none;
  background: transparent;
  height: 20px;
  box-sizing: border-box;
}

.jp-Placeholder-content .jp-MoreHorizIcon {
  width: 32px;
  height: 16px;
  border: 1px solid transparent;
  border-radius: var(--jp-border-radius);
}

.jp-Placeholder-content .jp-MoreHorizIcon:hover {
  border: 1px solid var(--jp-border-color1);
  box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
  background-color: var(--jp-layout-color0);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-cell-scrolling-output-offset: 5px;
}

/*-----------------------------------------------------------------------------
| Cell
|----------------------------------------------------------------------------*/

.jp-Cell {
  padding: var(--jp-cell-padding);
  margin: 0px;
  border: none;
  outline: none;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Common input/output
|----------------------------------------------------------------------------*/

.jp-Cell-inputWrapper,
.jp-Cell-outputWrapper {
  display: flex;
  flex-direction: row;
  padding: 0px;
  margin: 0px;
  /* Added to reveal the box-shadow on the input and output collapsers. */
  overflow: visible;
}

/* Only input/output areas inside cells */
.jp-Cell-inputArea,
.jp-Cell-outputArea {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Collapser
|----------------------------------------------------------------------------*/

/* Make the output collapser disappear when there is not output, but do so
 * in a manner that leaves it in the layout and preserves its width.
 */
.jp-Cell.jp-mod-noOutputs .jp-Cell-outputCollapser {
  border: none !important;
  background: transparent !important;
}

.jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputCollapser {
  min-height: var(--jp-cell-collapser-min-height);
}

/*-----------------------------------------------------------------------------
| Output
|----------------------------------------------------------------------------*/

/* Put a space between input and output when there IS output */
.jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputWrapper {
  margin-top: 5px;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea {
  overflow-y: auto;
  max-height: 200px;
  box-shadow: inset 0 0 6px 2px rgba(0, 0, 0, 0.3);
  margin-left: var(--jp-private-cell-scrolling-output-offset);
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-prompt {
  flex: 0 0
    calc(
      var(--jp-cell-prompt-width) -
        var(--jp-private-cell-scrolling-output-offset)
    );
}

/*-----------------------------------------------------------------------------
| CodeCell
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| MarkdownCell
|----------------------------------------------------------------------------*/

.jp-MarkdownOutput {
  flex: 1 1 auto;
  margin-top: 0;
  margin-bottom: 0;
  padding-left: var(--jp-code-padding);
}

.jp-MarkdownOutput.jp-RenderedHTMLCommon {
  overflow: auto;
}

.jp-showHiddenCellsButton {
  margin-left: calc(var(--jp-cell-prompt-width) + 2 * var(--jp-code-padding));
  margin-top: var(--jp-code-padding);
  border: 1px solid var(--jp-border-color2);
  background-color: var(--jp-border-color3) !important;
  color: var(--jp-content-font-color0) !important;
}

.jp-showHiddenCellsButton:hover {
  background-color: var(--jp-border-color2) !important;
}

.jp-collapseHeadingButton {
  display: none;
}

.jp-MarkdownCell:hover .jp-collapseHeadingButton {
  display: flex;
  min-height: var(--jp-cell-collapser-min-height);
  position: absolute;
  right: 0;
  top: 0;
  bottom: 0;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------

/*-----------------------------------------------------------------------------
| Styles
|----------------------------------------------------------------------------*/

.jp-NotebookPanel-toolbar {
  padding: 2px;
}

.jp-Toolbar-item.jp-Notebook-toolbarCellType .jp-select-wrapper.jp-mod-focused {
  border: none;
  box-shadow: none;
}

.jp-Notebook-toolbarCellTypeDropdown select {
  height: 24px;
  font-size: var(--jp-ui-font-size1);
  line-height: 14px;
  border-radius: 0;
  display: block;
}

.jp-Notebook-toolbarCellTypeDropdown span {
  top: 5px !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-notebook-dragImage-width: 304px;
  --jp-private-notebook-dragImage-height: 36px;
  --jp-private-notebook-selected-color: var(--md-blue-400);
  --jp-private-notebook-active-color: var(--md-green-400);
}

/*-----------------------------------------------------------------------------
| Imports
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Notebook
|----------------------------------------------------------------------------*/

.jp-NotebookPanel {
  display: block;
  height: 100%;
}

.jp-NotebookPanel.jp-Document {
  min-width: 240px;
  min-height: 120px;
}

.jp-Notebook {
  padding: var(--jp-notebook-padding);
  outline: none;
  overflow: auto;
  background: var(--jp-layout-color0);
}

.jp-Notebook.jp-mod-scrollPastEnd::after {
  display: block;
  content: '';
  min-height: var(--jp-notebook-scroll-padding);
}

.jp-MainAreaWidget-ContainStrict .jp-Notebook * {
  contain: strict;
}

.jp-Notebook-render * {
  contain: none !important;
}

.jp-Notebook .jp-Cell {
  overflow: visible;
}

.jp-Notebook .jp-Cell .jp-InputPrompt {
  cursor: move;
  float: left;
}

/*-----------------------------------------------------------------------------
| Notebook state related styling
|
| The notebook and cells each have states, here are the possibilities:
|
| - Notebook
|   - Command
|   - Edit
| - Cell
|   - None
|   - Active (only one can be active)
|   - Selected (the cells actions are applied to)
|   - Multiselected (when multiple selected, the cursor)
|   - No outputs
|----------------------------------------------------------------------------*/

/* Command or edit modes */

.jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-InputPrompt {
  opacity: var(--jp-cell-prompt-not-active-opacity);
  color: var(--jp-cell-prompt-not-active-font-color);
}

.jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-OutputPrompt {
  opacity: var(--jp-cell-prompt-not-active-opacity);
  color: var(--jp-cell-prompt-not-active-font-color);
}

/* cell is active */
.jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser {
  background: var(--jp-brand-color1);
}

/* cell is dirty */
.jp-Notebook .jp-Cell.jp-mod-dirty .jp-InputPrompt {
  color: var(--jp-warn-color1);
}
.jp-Notebook .jp-Cell.jp-mod-dirty .jp-InputPrompt:before {
  color: var(--jp-warn-color1);
  content: '•';
}

.jp-Notebook .jp-Cell.jp-mod-active.jp-mod-dirty .jp-Collapser {
  background: var(--jp-warn-color1);
}

/* collapser is hovered */
.jp-Notebook .jp-Cell .jp-Collapser:hover {
  box-shadow: var(--jp-elevation-z2);
  background: var(--jp-brand-color1);
  opacity: var(--jp-cell-collapser-not-active-hover-opacity);
}

/* cell is active and collapser is hovered */
.jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser:hover {
  background: var(--jp-brand-color0);
  opacity: 1;
}

/* Command mode */

.jp-Notebook.jp-mod-commandMode .jp-Cell.jp-mod-selected {
  background: var(--jp-notebook-multiselected-color);
}

.jp-Notebook.jp-mod-commandMode
  .jp-Cell.jp-mod-active.jp-mod-selected:not(.jp-mod-multiSelected) {
  background: transparent;
}

/* Edit mode */

.jp-Notebook.jp-mod-editMode .jp-Cell.jp-mod-active .jp-InputArea-editor {
  border: var(--jp-border-width) solid var(--jp-cell-editor-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
  background-color: var(--jp-cell-editor-active-background);
}

/*-----------------------------------------------------------------------------
| Notebook drag and drop
|----------------------------------------------------------------------------*/

.jp-Notebook-cell.jp-mod-dropSource {
  opacity: 0.5;
}

.jp-Notebook-cell.jp-mod-dropTarget,
.jp-Notebook.jp-mod-commandMode
  .jp-Notebook-cell.jp-mod-active.jp-mod-selected.jp-mod-dropTarget {
  border-top-color: var(--jp-private-notebook-selected-color);
  border-top-style: solid;
  border-top-width: 2px;
}

.jp-dragImage {
  display: block;
  flex-direction: row;
  width: var(--jp-private-notebook-dragImage-width);
  height: var(--jp-private-notebook-dragImage-height);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background);
  overflow: visible;
}

.jp-dragImage-singlePrompt {
  box-shadow: 2px 2px 4px 0px rgba(0, 0, 0, 0.12);
}

.jp-dragImage .jp-dragImage-content {
  flex: 1 1 auto;
  z-index: 2;
  font-size: var(--jp-code-font-size);
  font-family: var(--jp-code-font-family);
  line-height: var(--jp-code-line-height);
  padding: var(--jp-code-padding);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background-color);
  color: var(--jp-content-font-color3);
  text-align: left;
  margin: 4px 4px 4px 0px;
}

.jp-dragImage .jp-dragImage-prompt {
  flex: 0 0 auto;
  min-width: 36px;
  color: var(--jp-cell-inprompt-font-color);
  padding: var(--jp-code-padding);
  padding-left: 12px;
  font-family: var(--jp-cell-prompt-font-family);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  line-height: 1.9;
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
}

.jp-dragImage-multipleBack {
  z-index: -1;
  position: absolute;
  height: 32px;
  width: 300px;
  top: 8px;
  left: 8px;
  background: var(--jp-layout-color2);
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  box-shadow: 2px 2px 4px 0px rgba(0, 0, 0, 0.12);
}

/*-----------------------------------------------------------------------------
| Cell toolbar
|----------------------------------------------------------------------------*/

.jp-NotebookTools {
  display: block;
  min-width: var(--jp-sidebar-min-width);
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  /* This is needed so that all font sizing of children done in ems is
    * relative to this base size */
  font-size: var(--jp-ui-font-size1);
  overflow: auto;
}

.jp-NotebookTools-tool {
  padding: 0px 12px 0 12px;
}

.jp-ActiveCellTool {
  padding: 12px;
  background-color: var(--jp-layout-color1);
  border-top: none !important;
}

.jp-ActiveCellTool .jp-InputArea-prompt {
  flex: 0 0 auto;
  padding-left: 0px;
}

.jp-ActiveCellTool .jp-InputArea-editor {
  flex: 1 1 auto;
  background: var(--jp-cell-editor-background);
  border-color: var(--jp-cell-editor-border-color);
}

.jp-ActiveCellTool .jp-InputArea-editor .CodeMirror {
  background: transparent;
}

.jp-MetadataEditorTool {
  flex-direction: column;
  padding: 12px 0px 12px 0px;
}

.jp-RankedPanel > :not(:first-child) {
  margin-top: 12px;
}

.jp-KeySelector select.jp-mod-styled {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  border: var(--jp-border-width) solid var(--jp-border-color1);
}

.jp-KeySelector label,
.jp-MetadataEditorTool label {
  line-height: 1.4;
}

.jp-NotebookTools .jp-select-wrapper {
  margin-top: 4px;
  margin-bottom: 0px;
}

.jp-NotebookTools .jp-Collapse {
  margin-top: 16px;
}

/*-----------------------------------------------------------------------------
| Presentation Mode (.jp-mod-presentationMode)
|----------------------------------------------------------------------------*/

.jp-mod-presentationMode .jp-Notebook {
  --jp-content-font-size1: var(--jp-content-presentation-font-size1);
  --jp-code-font-size: var(--jp-code-presentation-font-size);
}

.jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-InputPrompt,
.jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-OutputPrompt {
  flex: 0 0 110px;
}

/*-----------------------------------------------------------------------------
| Placeholder
|----------------------------------------------------------------------------*/

.jp-Cell-Placeholder {
  padding-left: 55px;
}

.jp-Cell-Placeholder-wrapper {
  background: #fff;
  border: 1px solid;
  border-color: #e5e6e9 #dfe0e4 #d0d1d5;
  border-radius: 4px;
  -webkit-border-radius: 4px;
  margin: 10px 15px;
}

.jp-Cell-Placeholder-wrapper-inner {
  padding: 15px;
  position: relative;
}

.jp-Cell-Placeholder-wrapper-body {
  background-repeat: repeat;
  background-size: 50% auto;
}

.jp-Cell-Placeholder-wrapper-body div {
  background: #f6f7f8;
  background-image: -webkit-linear-gradient(
    left,
    #f6f7f8 0%,
    #edeef1 20%,
    #f6f7f8 40%,
    #f6f7f8 100%
  );
  background-repeat: no-repeat;
  background-size: 800px 104px;
  height: 104px;
  position: relative;
}

.jp-Cell-Placeholder-wrapper-body div {
  position: absolute;
  right: 15px;
  left: 15px;
  top: 15px;
}

div.jp-Cell-Placeholder-h1 {
  top: 20px;
  height: 20px;
  left: 15px;
  width: 150px;
}

div.jp-Cell-Placeholder-h2 {
  left: 15px;
  top: 50px;
  height: 10px;
  width: 100px;
}

div.jp-Cell-Placeholder-content-1,
div.jp-Cell-Placeholder-content-2,
div.jp-Cell-Placeholder-content-3 {
  left: 15px;
  right: 15px;
  height: 10px;
}

div.jp-Cell-Placeholder-content-1 {
  top: 100px;
}

div.jp-Cell-Placeholder-content-2 {
  top: 120px;
}

div.jp-Cell-Placeholder-content-3 {
  top: 140px;
}

</style>

    <style type="text/css">
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*
The following CSS variables define the main, public API for styling JupyterLab.
These variables should be used by all plugins wherever possible. In other
words, plugins should not define custom colors, sizes, etc unless absolutely
necessary. This enables users to change the visual theme of JupyterLab
by changing these variables.

Many variables appear in an ordered sequence (0,1,2,3). These sequences
are designed to work well together, so for example, `--jp-border-color1` should
be used with `--jp-layout-color1`. The numbers have the following meanings:

* 0: super-primary, reserved for special emphasis
* 1: primary, most important under normal situations
* 2: secondary, next most important under normal situations
* 3: tertiary, next most important under normal situations

Throughout JupyterLab, we are mostly following principles from Google's
Material Design when selecting colors. We are not, however, following
all of MD as it is not optimized for dense, information rich UIs.
*/

:root {
  /* Elevation
   *
   * We style box-shadows using Material Design's idea of elevation. These particular numbers are taken from here:
   *
   * https://github.com/material-components/material-components-web
   * https://material-components-web.appspot.com/elevation.html
   */

  --jp-shadow-base-lightness: 0;
  --jp-shadow-umbra-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.2
  );
  --jp-shadow-penumbra-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.14
  );
  --jp-shadow-ambient-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.12
  );
  --jp-elevation-z0: none;
  --jp-elevation-z1: 0px 2px 1px -1px var(--jp-shadow-umbra-color),
    0px 1px 1px 0px var(--jp-shadow-penumbra-color),
    0px 1px 3px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z2: 0px 3px 1px -2px var(--jp-shadow-umbra-color),
    0px 2px 2px 0px var(--jp-shadow-penumbra-color),
    0px 1px 5px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z4: 0px 2px 4px -1px var(--jp-shadow-umbra-color),
    0px 4px 5px 0px var(--jp-shadow-penumbra-color),
    0px 1px 10px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z6: 0px 3px 5px -1px var(--jp-shadow-umbra-color),
    0px 6px 10px 0px var(--jp-shadow-penumbra-color),
    0px 1px 18px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z8: 0px 5px 5px -3px var(--jp-shadow-umbra-color),
    0px 8px 10px 1px var(--jp-shadow-penumbra-color),
    0px 3px 14px 2px var(--jp-shadow-ambient-color);
  --jp-elevation-z12: 0px 7px 8px -4px var(--jp-shadow-umbra-color),
    0px 12px 17px 2px var(--jp-shadow-penumbra-color),
    0px 5px 22px 4px var(--jp-shadow-ambient-color);
  --jp-elevation-z16: 0px 8px 10px -5px var(--jp-shadow-umbra-color),
    0px 16px 24px 2px var(--jp-shadow-penumbra-color),
    0px 6px 30px 5px var(--jp-shadow-ambient-color);
  --jp-elevation-z20: 0px 10px 13px -6px var(--jp-shadow-umbra-color),
    0px 20px 31px 3px var(--jp-shadow-penumbra-color),
    0px 8px 38px 7px var(--jp-shadow-ambient-color);
  --jp-elevation-z24: 0px 11px 15px -7px var(--jp-shadow-umbra-color),
    0px 24px 38px 3px var(--jp-shadow-penumbra-color),
    0px 9px 46px 8px var(--jp-shadow-ambient-color);

  /* Borders
   *
   * The following variables, specify the visual styling of borders in JupyterLab.
   */

  --jp-border-width: 1px;
  --jp-border-color0: var(--md-grey-400);
  --jp-border-color1: var(--md-grey-400);
  --jp-border-color2: var(--md-grey-300);
  --jp-border-color3: var(--md-grey-200);
  --jp-border-radius: 2px;

  /* UI Fonts
   *
   * The UI font CSS variables are used for the typography all of the JupyterLab
   * user interface elements that are not directly user generated content.
   *
   * The font sizing here is done assuming that the body font size of --jp-ui-font-size1
   * is applied to a parent element. When children elements, such as headings, are sized
   * in em all things will be computed relative to that body size.
   */

  --jp-ui-font-scale-factor: 1.2;
  --jp-ui-font-size0: 0.83333em;
  --jp-ui-font-size1: 13px; /* Base font size */
  --jp-ui-font-size2: 1.2em;
  --jp-ui-font-size3: 1.44em;

  --jp-ui-font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica,
    Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';

  /*
   * Use these font colors against the corresponding main layout colors.
   * In a light theme, these go from dark to light.
   */

  /* Defaults use Material Design specification */
  --jp-ui-font-color0: rgba(0, 0, 0, 1);
  --jp-ui-font-color1: rgba(0, 0, 0, 0.87);
  --jp-ui-font-color2: rgba(0, 0, 0, 0.54);
  --jp-ui-font-color3: rgba(0, 0, 0, 0.38);

  /*
   * Use these against the brand/accent/warn/error colors.
   * These will typically go from light to darker, in both a dark and light theme.
   */

  --jp-ui-inverse-font-color0: rgba(255, 255, 255, 1);
  --jp-ui-inverse-font-color1: rgba(255, 255, 255, 1);
  --jp-ui-inverse-font-color2: rgba(255, 255, 255, 0.7);
  --jp-ui-inverse-font-color3: rgba(255, 255, 255, 0.5);

  /* Content Fonts
   *
   * Content font variables are used for typography of user generated content.
   *
   * The font sizing here is done assuming that the body font size of --jp-content-font-size1
   * is applied to a parent element. When children elements, such as headings, are sized
   * in em all things will be computed relative to that body size.
   */

  --jp-content-line-height: 1.6;
  --jp-content-font-scale-factor: 1.2;
  --jp-content-font-size0: 0.83333em;
  --jp-content-font-size1: 14px; /* Base font size */
  --jp-content-font-size2: 1.2em;
  --jp-content-font-size3: 1.44em;
  --jp-content-font-size4: 1.728em;
  --jp-content-font-size5: 2.0736em;

  /* This gives a magnification of about 125% in presentation mode over normal. */
  --jp-content-presentation-font-size1: 17px;

  --jp-content-heading-line-height: 1;
  --jp-content-heading-margin-top: 1.2em;
  --jp-content-heading-margin-bottom: 0.8em;
  --jp-content-heading-font-weight: 500;

  /* Defaults use Material Design specification */
  --jp-content-font-color0: rgba(0, 0, 0, 1);
  --jp-content-font-color1: rgba(0, 0, 0, 0.87);
  --jp-content-font-color2: rgba(0, 0, 0, 0.54);
  --jp-content-font-color3: rgba(0, 0, 0, 0.38);

  --jp-content-link-color: var(--md-blue-700);

  --jp-content-font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
    'Segoe UI Symbol';

  /*
   * Code Fonts
   *
   * Code font variables are used for typography of code and other monospaces content.
   */

  --jp-code-font-size: 13px;
  --jp-code-line-height: 1.3077; /* 17px for 13px base */
  --jp-code-padding: 5px; /* 5px for 13px base, codemirror highlighting needs integer px value */
  --jp-code-font-family-default: Menlo, Consolas, 'DejaVu Sans Mono', monospace;
  --jp-code-font-family: var(--jp-code-font-family-default);

  /* This gives a magnification of about 125% in presentation mode over normal. */
  --jp-code-presentation-font-size: 16px;

  /* may need to tweak cursor width if you change font size */
  --jp-code-cursor-width0: 1.4px;
  --jp-code-cursor-width1: 2px;
  --jp-code-cursor-width2: 4px;

  /* Layout
   *
   * The following are the main layout colors use in JupyterLab. In a light
   * theme these would go from light to dark.
   */

  --jp-layout-color0: white;
  --jp-layout-color1: white;
  --jp-layout-color2: var(--md-grey-200);
  --jp-layout-color3: var(--md-grey-400);
  --jp-layout-color4: var(--md-grey-600);

  /* Inverse Layout
   *
   * The following are the inverse layout colors use in JupyterLab. In a light
   * theme these would go from dark to light.
   */

  --jp-inverse-layout-color0: #111111;
  --jp-inverse-layout-color1: var(--md-grey-900);
  --jp-inverse-layout-color2: var(--md-grey-800);
  --jp-inverse-layout-color3: var(--md-grey-700);
  --jp-inverse-layout-color4: var(--md-grey-600);

  /* Brand/accent */

  --jp-brand-color0: var(--md-blue-900);
  --jp-brand-color1: var(--md-blue-700);
  --jp-brand-color2: var(--md-blue-300);
  --jp-brand-color3: var(--md-blue-100);
  --jp-brand-color4: var(--md-blue-50);

  --jp-accent-color0: var(--md-green-900);
  --jp-accent-color1: var(--md-green-700);
  --jp-accent-color2: var(--md-green-300);
  --jp-accent-color3: var(--md-green-100);

  /* State colors (warn, error, success, info) */

  --jp-warn-color0: var(--md-orange-900);
  --jp-warn-color1: var(--md-orange-700);
  --jp-warn-color2: var(--md-orange-300);
  --jp-warn-color3: var(--md-orange-100);

  --jp-error-color0: var(--md-red-900);
  --jp-error-color1: var(--md-red-700);
  --jp-error-color2: var(--md-red-300);
  --jp-error-color3: var(--md-red-100);

  --jp-success-color0: var(--md-green-900);
  --jp-success-color1: var(--md-green-700);
  --jp-success-color2: var(--md-green-300);
  --jp-success-color3: var(--md-green-100);

  --jp-info-color0: var(--md-cyan-900);
  --jp-info-color1: var(--md-cyan-700);
  --jp-info-color2: var(--md-cyan-300);
  --jp-info-color3: var(--md-cyan-100);

  /* Cell specific styles */

  --jp-cell-padding: 5px;

  --jp-cell-collapser-width: 8px;
  --jp-cell-collapser-min-height: 20px;
  --jp-cell-collapser-not-active-hover-opacity: 0.6;

  --jp-cell-editor-background: var(--md-grey-100);
  --jp-cell-editor-border-color: var(--md-grey-300);
  --jp-cell-editor-box-shadow: inset 0 0 2px var(--md-blue-300);
  --jp-cell-editor-active-background: var(--jp-layout-color0);
  --jp-cell-editor-active-border-color: var(--jp-brand-color1);

  --jp-cell-prompt-width: 64px;
  --jp-cell-prompt-font-family: var(--jp-code-font-family-default);
  --jp-cell-prompt-letter-spacing: 0px;
  --jp-cell-prompt-opacity: 1;
  --jp-cell-prompt-not-active-opacity: 0.5;
  --jp-cell-prompt-not-active-font-color: var(--md-grey-700);
  /* A custom blend of MD grey and blue 600
   * See https://meyerweb.com/eric/tools/color-blend/#546E7A:1E88E5:5:hex */
  --jp-cell-inprompt-font-color: #307fc1;
  /* A custom blend of MD grey and orange 600
   * https://meyerweb.com/eric/tools/color-blend/#546E7A:F4511E:5:hex */
  --jp-cell-outprompt-font-color: #bf5b3d;

  /* Notebook specific styles */

  --jp-notebook-padding: 10px;
  --jp-notebook-select-background: var(--jp-layout-color1);
  --jp-notebook-multiselected-color: var(--md-blue-50);

  /* The scroll padding is calculated to fill enough space at the bottom of the
  notebook to show one single-line cell (with appropriate padding) at the top
  when the notebook is scrolled all the way to the bottom. We also subtract one
  pixel so that no scrollbar appears if we have just one single-line cell in the
  notebook. This padding is to enable a 'scroll past end' feature in a notebook.
  */
  --jp-notebook-scroll-padding: calc(
    100% - var(--jp-code-font-size) * var(--jp-code-line-height) -
      var(--jp-code-padding) - var(--jp-cell-padding) - 1px
  );

  /* Rendermime styles */

  --jp-rendermime-error-background: #fdd;
  --jp-rendermime-table-row-background: var(--md-grey-100);
  --jp-rendermime-table-row-hover-background: var(--md-light-blue-50);

  /* Dialog specific styles */

  --jp-dialog-background: rgba(0, 0, 0, 0.25);

  /* Console specific styles */

  --jp-console-padding: 10px;

  /* Toolbar specific styles */

  --jp-toolbar-border-color: var(--jp-border-color1);
  --jp-toolbar-micro-height: 8px;
  --jp-toolbar-background: var(--jp-layout-color1);
  --jp-toolbar-box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.24);
  --jp-toolbar-header-margin: 4px 4px 0px 4px;
  --jp-toolbar-active-background: var(--md-grey-300);

  /* Statusbar specific styles */

  --jp-statusbar-height: 24px;

  /* Input field styles */

  --jp-input-box-shadow: inset 0 0 2px var(--md-blue-300);
  --jp-input-active-background: var(--jp-layout-color1);
  --jp-input-hover-background: var(--jp-layout-color1);
  --jp-input-background: var(--md-grey-100);
  --jp-input-border-color: var(--jp-border-color1);
  --jp-input-active-border-color: var(--jp-brand-color1);
  --jp-input-active-box-shadow-color: rgba(19, 124, 189, 0.3);

  /* General editor styles */

  --jp-editor-selected-background: #d9d9d9;
  --jp-editor-selected-focused-background: #d7d4f0;
  --jp-editor-cursor-color: var(--jp-ui-font-color0);

  /* Code mirror specific styles */

  --jp-mirror-editor-keyword-color: #008000;
  --jp-mirror-editor-atom-color: #88f;
  --jp-mirror-editor-number-color: #080;
  --jp-mirror-editor-def-color: #00f;
  --jp-mirror-editor-variable-color: var(--md-grey-900);
  --jp-mirror-editor-variable-2-color: #05a;
  --jp-mirror-editor-variable-3-color: #085;
  --jp-mirror-editor-punctuation-color: #05a;
  --jp-mirror-editor-property-color: #05a;
  --jp-mirror-editor-operator-color: #aa22ff;
  --jp-mirror-editor-comment-color: #408080;
  --jp-mirror-editor-string-color: #ba2121;
  --jp-mirror-editor-string-2-color: #708;
  --jp-mirror-editor-meta-color: #aa22ff;
  --jp-mirror-editor-qualifier-color: #555;
  --jp-mirror-editor-builtin-color: #008000;
  --jp-mirror-editor-bracket-color: #997;
  --jp-mirror-editor-tag-color: #170;
  --jp-mirror-editor-attribute-color: #00c;
  --jp-mirror-editor-header-color: blue;
  --jp-mirror-editor-quote-color: #090;
  --jp-mirror-editor-link-color: #00c;
  --jp-mirror-editor-error-color: #f00;
  --jp-mirror-editor-hr-color: #999;

  /* Vega extension styles */

  --jp-vega-background: white;

  /* Sidebar-related styles */

  --jp-sidebar-min-width: 250px;

  /* Search-related styles */

  --jp-search-toggle-off-opacity: 0.5;
  --jp-search-toggle-hover-opacity: 0.8;
  --jp-search-toggle-on-opacity: 1;
  --jp-search-selected-match-background-color: rgb(245, 200, 0);
  --jp-search-selected-match-color: black;
  --jp-search-unselected-match-background-color: var(
    --jp-inverse-layout-color0
  );
  --jp-search-unselected-match-color: var(--jp-ui-inverse-font-color0);

  /* Icon colors that work well with light or dark backgrounds */
  --jp-icon-contrast-color0: var(--md-purple-600);
  --jp-icon-contrast-color1: var(--md-green-600);
  --jp-icon-contrast-color2: var(--md-pink-600);
  --jp-icon-contrast-color3: var(--md-blue-600);
}
</style>

<style type="text/css">
/* Force rendering true colors when outputing to pdf */
* {
  -webkit-print-color-adjust: exact;
}

/* Misc */
a.anchor-link {
  display: none;
}

.highlight  {
  margin: 0.4em;
}

/* Input area styling */
.jp-InputArea {
  overflow: hidden;
}

.jp-InputArea-editor {
  overflow: hidden;
}

.CodeMirror pre {
  margin: 0;
  padding: 0;
}

/* Using table instead of flexbox so that we can use break-inside property */
/* CSS rules under this comment should not be required anymore after we move to the JupyterLab 4.0 CSS */


.jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-prompt {
  min-width: calc(
    var(--jp-cell-prompt-width) - var(--jp-private-cell-scrolling-output-offset)
  );
}

.jp-OutputArea-child {
  display: table;
  width: 100%;
}

.jp-OutputPrompt {
  display: table-cell;
  vertical-align: top;
  min-width: var(--jp-cell-prompt-width);
}

body[data-format='mobile'] .jp-OutputPrompt {
  display: table-row;
}

.jp-OutputArea-output {
  display: table-cell;
  width: 100%;
}

body[data-format='mobile'] .jp-OutputArea-child .jp-OutputArea-output {
  display: table-row;
}

.jp-OutputArea-output.jp-OutputArea-executeResult {
  width: 100%;
}

/* Hiding the collapser by default */
.jp-Collapser {
  display: none;
}

@media print {
  .jp-Cell-inputWrapper,
  .jp-Cell-outputWrapper {
    display: block;
  }

  .jp-OutputArea-child {
    break-inside: avoid-page;
  }
}
</style>

<!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/latest.js?config=TeX-AMS_CHTML-full,Safe"> </script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    init_mathjax = function() {
        if (window.MathJax) {
        // MathJax loaded
            MathJax.Hub.Config({
                TeX: {
                    equationNumbers: {
                    autoNumber: "AMS",
                    useLabelIds: true
                    }
                },
                tex2jax: {
                    inlineMath: [ ['$','$'], ["\\(","\\)"] ],
                    displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
                    processEscapes: true,
                    processEnvironments: true
                },
                displayAlign: 'center',
                CommonHTML: {
                    linebreaks: {
                    automatic: true
                    }
                }
            });

            MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
        }
    }
    init_mathjax();
    </script>
    <!-- End of mathjax configuration --></head>
<body class="jp-Notebook" data-jp-theme-light="true" data-jp-theme-name="JupyterLab Light">
<div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[1]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-python"><pre><span></span><span class="kn">import</span> <span class="nn">sympy</span> <span class="k">as</span> <span class="nn">sp</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">from</span> <span class="nn">IPython.display</span> <span class="kn">import</span> <span class="n">Latex</span>

<span class="k">def</span> <span class="nf">interpolate_lagrange</span><span class="p">(</span><span class="n">x_values</span><span class="p">,</span> <span class="n">y_values</span><span class="p">):</span>
    <span class="c1"># Define the symbolic variable</span>
    <span class="n">x</span> <span class="o">=</span> <span class="n">sp</span><span class="o">.</span><span class="n">symbols</span><span class="p">(</span><span class="s1">'x'</span><span class="p">)</span>

    <span class="c1"># Initialize the Lagrange polynomial</span>
    <span class="n">lagrange_poly</span> <span class="o">=</span> <span class="mi">0</span>

    <span class="c1"># Calculate the Lagrange basis polynomials</span>
    <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">x_values</span><span class="p">)):</span>
        <span class="n">basis_poly</span> <span class="o">=</span> <span class="mi">1</span>
        <span class="k">for</span> <span class="n">j</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">x_values</span><span class="p">)):</span>
            <span class="k">if</span> <span class="n">i</span> <span class="o">!=</span> <span class="n">j</span><span class="p">:</span>
                <span class="n">basis_poly</span> <span class="o">*=</span> <span class="p">(</span><span class="n">x</span> <span class="o">-</span> <span class="n">x_values</span><span class="p">[</span><span class="n">j</span><span class="p">])</span> <span class="o">/</span> <span class="p">(</span><span class="n">x_values</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">-</span> <span class="n">x_values</span><span class="p">[</span><span class="n">j</span><span class="p">])</span>
        <span class="n">lagrange_poly</span> <span class="o">+=</span> <span class="n">y_values</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">*</span> <span class="n">basis_poly</span>

    <span class="c1"># Simplify the Lagrange polynomial</span>
    <span class="n">lagrange_poly</span>

    <span class="k">return</span> <span class="n">lagrange_poly</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[2]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-python"><pre><span></span><span class="k">def</span> <span class="nf">interpolate_and_plot</span><span class="p">(</span><span class="n">function_str</span><span class="p">,</span> <span class="n">x_values</span><span class="p">):</span>
    <span class="c1"># Create a lambda function from the string</span>
    <span class="k">if</span> <span class="nb">isinstance</span><span class="p">(</span><span class="n">function_str</span><span class="p">,</span> <span class="nb">str</span><span class="p">):</span>
      <span class="n">f</span> <span class="o">=</span> <span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="nb">eval</span><span class="p">(</span><span class="n">function_str</span><span class="p">)</span>


      <span class="c1"># Define the interpolation points and function values</span>
      <span class="n">y_values</span> <span class="o">=</span> <span class="p">[</span><span class="n">f</span><span class="p">(</span><span class="n">x</span><span class="p">)</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">x_values</span><span class="p">]</span>
    <span class="k">else</span><span class="p">:</span>
      <span class="n">y_values</span> <span class="o">=</span> <span class="n">function_str</span>

    <span class="c1"># Perform Lagrange interpolation</span>
    <span class="n">lagrange_poly</span> <span class="o">=</span> <span class="n">interpolate_lagrange</span><span class="p">(</span><span class="n">x_values</span><span class="p">,</span> <span class="n">y_values</span><span class="p">)</span>

    <span class="c1"># Create a range of x values for plotting</span>
    <span class="n">x_range</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">linspace</span><span class="p">(</span><span class="nb">min</span><span class="p">(</span><span class="n">x_values</span><span class="p">),</span> <span class="nb">max</span><span class="p">(</span><span class="n">x_values</span><span class="p">),</span> <span class="mi">400</span><span class="p">)</span>  <span class="c1"># Adjust the range as needed</span>

    <span class="c1"># Evaluate the interpolating polynomial at the x_range</span>
    <span class="n">y_interpolated</span> <span class="o">=</span> <span class="p">[</span><span class="n">lagrange_poly</span><span class="o">.</span><span class="n">subs</span><span class="p">(</span><span class="s1">'x'</span><span class="p">,</span> <span class="n">xi</span><span class="p">)</span><span class="o">.</span><span class="n">evalf</span><span class="p">()</span> <span class="k">for</span> <span class="n">xi</span> <span class="ow">in</span> <span class="n">x_range</span><span class="p">]</span>

    <span class="c1"># Convert the Lagrange polynomial to LaTeX format</span>
    <span class="n">latex_formula</span> <span class="o">=</span> <span class="n">sp</span><span class="o">.</span><span class="n">latex</span><span class="p">(</span><span class="n">lagrange_poly</span><span class="p">)</span>


    <span class="c1"># Create a plot of the original function</span>
    <span class="k">if</span> <span class="nb">isinstance</span><span class="p">(</span><span class="n">function_str</span><span class="p">,</span> <span class="nb">str</span><span class="p">):</span>
      <span class="n">label</span> <span class="o">=</span> <span class="sa">f</span><span class="s1">'f(x) = </span><span class="si">{</span><span class="n">function_str</span><span class="si">}</span><span class="s1">'</span>
      <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">x_range</span><span class="p">,</span> <span class="n">f</span><span class="p">(</span><span class="n">x_range</span><span class="p">),</span> <span class="n">label</span><span class="o">=</span><span class="n">label</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">'blue'</span><span class="p">,</span> <span class="n">linewidth</span><span class="o">=</span><span class="mi">3</span><span class="p">)</span>

    <span class="c1"># Create a scatter plot of the interpolation points</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">x_values</span><span class="p">,</span> <span class="n">y_values</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s1">'Interpolation Points'</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">'red'</span><span class="p">)</span>

    <span class="c1"># Create a plot of the interpolating polynomial</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">x_range</span><span class="p">,</span> <span class="n">y_interpolated</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s1">'Interpolating Polynomial'</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">'orange'</span><span class="p">,</span> <span class="n">linestyle</span><span class="o">=</span><span class="s1">'--'</span><span class="p">,</span> <span class="n">linewidth</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>

    <span class="n">title_text</span> <span class="o">=</span> <span class="sa">f</span><span class="s1">'Lagrange Polynomial:</span><span class="se">\n</span><span class="s1">$</span><span class="si">{</span><span class="n">latex_formula</span><span class="si">}</span><span class="s1">$'</span>

    <span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">'x'</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">'y'</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">()</span>

    <span class="c1"># Show the plot</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">grid</span><span class="p">(</span><span class="kc">True</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">"Lagrange Polynomial:"</span><span class="p">)</span>

    <span class="n">display</span><span class="p">(</span><span class="n">Latex</span><span class="p">(</span><span class="n">latex_formula</span><span class="p">))</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">"Polynomial:"</span><span class="p">)</span>
    <span class="n">display</span><span class="p">(</span><span class="n">Latex</span><span class="p">(</span><span class="n">sp</span><span class="o">.</span><span class="n">latex</span><span class="p">(</span><span class="n">sp</span><span class="o">.</span><span class="n">simplify</span><span class="p">(</span><span class="n">lagrange_poly</span><span class="p">))))</span>
    <span class="k">return</span> <span class="n">lagrange_poly</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[3]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-python"><pre><span></span><span class="n">function</span> <span class="o">=</span> <span class="s2">"np.sqrt(1 + x**2)"</span>
<span class="n">x_values</span> <span class="o">=</span> <span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">1</span><span class="o">/</span><span class="mi">3</span><span class="p">,</span> <span class="mi">1</span><span class="o">/</span><span class="mi">2</span><span class="p">,</span> <span class="mi">1</span><span class="p">]</span>
<span class="n">interpolate_and_plot</span><span class="p">(</span><span class="n">function</span><span class="p">,</span> <span class="n">x_values</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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
"
class="
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>Lagrange Polynomial:
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedLatex jp-OutputArea-output " data-mime-type="text/latex">
$$3.16227766016838 x \left(1.5 - 1.5 x\right) \left(3.0 - 6.0 x\right) + 2.23606797749979 x \left(2.0 - 2.0 x\right) \left(6.0 x - 2.0\right) + 1.4142135623731 x \left(1.5 x - 0.5\right) \left(2.0 x - 1.0\right) + 1.0 \cdot \left(1.0 - 3.0 x\right) \left(1.0 - 2.0 x\right) \left(1 - x\right)$$
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>Polynomial:
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedLatex jp-OutputArea-output " data-mime-type="text/latex">
$$- 0.129676101362787 x^{3} + 0.55080532179079 x^{2} - 0.00691565805490768 x + 1.0$$
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[3]:</div>




<div class="jp-RenderedLatex jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/latex">
$$\displaystyle 3.16227766016838 x \left(1.5 - 1.5 x\right) \left(3.0 - 6.0 x\right) + 2.23606797749979 x \left(2.0 - 2.0 x\right) \left(6.0 x - 2.0\right) + 1.4142135623731 x \left(1.5 x - 0.5\right) \left(2.0 x - 1.0\right) + 1.0 \cdot \left(1.0 - 3.0 x\right) \left(1.0 - 2.0 x\right) \left(1 - x\right)$$
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[4]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-python"><pre><span></span><span class="n">function</span> <span class="o">=</span> <span class="p">[</span><span class="mi">6</span><span class="p">,</span><span class="mi">5</span><span class="p">,</span><span class="mi">12</span><span class="p">]</span>
<span class="n">x_values</span> <span class="o">=</span> <span class="p">[</span><span class="mi">9</span><span class="p">,</span><span class="mi">3</span><span class="p">,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">lagrange_poly</span><span class="o">=</span><span class="n">interpolate_and_plot</span><span class="p">(</span><span class="n">function</span><span class="p">,</span> <span class="n">x_values</span><span class="p">)</span>
<span class="n">x_value</span> <span class="o">=</span> <span class="mi">10</span>
<span class="n">y_value</span> <span class="o">=</span> <span class="n">lagrange_poly</span><span class="o">.</span><span class="n">subs</span><span class="p">(</span><span class="s1">'x'</span><span class="p">,</span> <span class="n">x_value</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s1">'f(</span><span class="si">{</span><span class="n">x_value</span><span class="si">}</span><span class="s1">) = </span><span class="si">{</span><span class="n">y_value</span><span class="si">}</span><span class="s1">'</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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1Vfney48PDynffIv55Kya9cuLr/8cu6++26ee+45KlWqxJIlS7j99tvJysoqciFTnM+jMB5++GFuueUWypUrR/Xq1fMUHUXVpk0bWrVqxXvvvUevXr3YsGEDX331VZ51vDWOk7fjcDiKtN20tDT69OlDt27dmDZtGtWrV2f37t307t2brKysImcpLhUyIiKF1eRB61EcXT4/+zo2CAkJwe1251nWtm1bNm/eTP369Yu1zZ9//pnatWsDkJyczJYtW2jSpAkATZo0YenSpfnWb9iw4Wn3xqxevRqPx8OLL75IUJB1WudHH32UZ53Q0NB8YyiORo0a8fXXX+dZdvIJsmdSpUqV035ejRs3ZsqUKaSlpeXsQVm6dClBQUE0atSowO3961//YtKkSSQlJdGjRw/i40+zl68A5513HqGhoSxdupSEhATAOpdl5cqVRZoD5mx+//13/v77b55++mmaNm1KUFAQq1at8tr2C0sn+5amv1eCO8PuFCIiOerUqcOCBQvYv38/ycnJADz11FO89957jBo1ig0bNrBp0yZmzpzJE088UahtPvPMMyxYsID169dzyy23UKVKlZz5bR566CEWLFjA6NGj2bJlC1OnTuXtt9/mwQdPXyDWr18fl8vFyy+/zI4dO5g2bRqvv553fq46depw9OhRFixYwMGDB/NcZVMUd955J7///jvDhw9ny5YtfPTRRzknIRd3D8ugQYMIDw/nlltuYf369fzwww/cd9993HTTTac9rHTCwIED2bNnD2+99Vaek3wLIyoqirvvvpuHH36Yb7/9lo0bN/Lvf/+b9PR0br/99mKN43Rq165NaGgob775Jjt27ODzzz+3ZY4ZFTKl4cCP8N1F8N2F8MdHZ19fRKSUvPjii8ybN4/4+HjatGkDQO/evfnyyy+ZO3cu7dq1o3379kycODHnr/uzGTduHEOHDuX8889n//79fPHFF4SGWjfQbdu2LR999BEzZ86kefPmjBw5khEjRhR4pUurVq2YMGEC48ePp3nz5kyfPp2xY8fmWadjx47cddddXH/99VStWpXnn3++WJ9F3bp1+eSTT5g1axYtW7Zk8uTJOVcthYWFFWubkZGRfPLJJyQnJ9OuXTuuvfZaunfvftZLzsuXL88111xDuXLlijXr77hx47jmmmu46aabaNu2Ldu2beO7776jYsWKxRrH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5ZVX8uuvv9KsWTO743nVypUreeONN2jZsqXdUbyuWbNmzJ8/P6cfHBw4P86Sk5Pp1KkT3bp145tvvqFq1aps3bqVihUr2h3NK1auXInb7c7pr1+/np49e3LdddfZmMq7xo8fz+TJk5k6dSrNmjVj1apV3HrrrZQvX57777/f7nhe8a9//Yv169czbdo0atasyfvvv0+PHj3YuHEjtWrVKr0gRs4JYGbPnm13jBJz4MABA5hFixbZHaVEVaxY0bz99tt2x/CqI0eOmAYNGph58+aZLl26mKFDh9odyWuefvpp06pVK7tjlJjhw4ebzp072x2j1AwdOtScd955xuPx2B3Fa/r27Wtuu+22PMuuvvpqM2jQIJsSeVd6erpxOp3myy+/zLO8bdu25vHHHy/VLDq0JGeUkpICQKVKlWxOUjLcbjczZ84kLS2NDh062B3Hq4YMGULfvn3p0aOH3VFKxNatW6lZsyb16tVj0KBB7N692+5IXvP5559zwQUXcN1111GtWjXatGnDW2+9ZXesEpGVlcX777/Pbbfd5tUb+9qtY8eOLFiwgC1btgCwdu1alixZQp8+fWxO5h3Z2dm43W7Cw8PzLI+IiGDJkiWlmiVw9sWK13k8HoYNG0anTp1o3ry53XG8at26dXTo0IGMjAzKlSvH7Nmzadq0qd2xvGbmzJn88ssvthyvLg0XXXQRU6ZMoVGjRuzbt49Ro0Zx8cUXs379eqKjo+2Od8527NjB5MmTefDBB3nsscdYuXIl999/P6GhoQwePNjueF41Z84cDh8+zC233GJ3FK969NFHSU1NpXHjxjidTtxuN8899xyDBg2yO5pXREdH06FDB0aPHk2TJk2oXr06H3zwAT/99BP169cv3TCluv8nABHAh5buuusuk5CQYBITE+2O4nWZmZlm69atZtWqVebRRx81VapUMRs2bLA7llfs3r3bVKtWzaxduzZnWaAdWjpVcnKyiYmJCZjDgyEhIaZDhw55lt13332mffv2NiUqOb169TKXX3653TG87oMPPjBxcXHmgw8+ML/99pt57733TKVKlcyUKVPsjuY127ZtM5dccokBjNPpNO3atTODBg0yjRs3LtUcKmTOUaAWMkOGDDFxcXFmx44ddkcpFd27dzd33HGH3TG8Yvbs2Tk/WE48AONwOIzT6TTZ2dl2RywRF1xwgXn00UftjuEVtWvXNrfffnueZa+99pqpWbOmTYlKxq5du0xQUJCZM2eO3VG8Li4uzrzyyit5lo0ePdo0atTIpkQl5+jRo2bv3r3GGGMGDBhgLrvsslJ9f50jI3kYY7j33nuZPXs233//PXXr1rU7UqnweDxkZmbaHcMrunfvzrp161izZk3O44ILLmDQoEGsWbMGp9Npd0SvO3r0KNu3byc2NtbuKF7RqVOnfNMebNmyhYSEBJsSlYx3332XatWq0bdvX7ujeF16ejpBQXl/xTqdTjwej02JSk5UVBSxsbEkJyfz3XffceWVV5bq++scmWI4evQo27Zty+nv3LmTNWvWUKlSJWrXrm1jsnM3ZMgQZsyYwWeffUZ0dDT79+8HoHz58kRERNiczjtGjBhBnz59qF27NkeOHGHGjBksXLiQ7777zu5oXhEdHZ3vnKaoqCgqV64cMOc6/ec//6Ffv34kJCSwd+9enn76aZxOJzfeeKPd0bzigQceoGPHjowZM4YBAwawYsUK3nzzTd588027o3mNx+Ph3XffZfDgwQF16fwJ/fr147nnnqN27do0a9aMX3/9lQkTJnDbbbfZHc1rvvvuO4wxNGrUiG3btvHwww/TuHFjbr311tINUqr7fwLEDz/8YIB8j8GDB9sd7ZydblyAeffdd+2O5jW33XabSUhIMKGhoaZq1aqme/fuZu7cuXbHKlGBdo7M9ddfb2JjY01oaKipVauWuf766822bdvsjuVVX3zxhWnevLkJCwszjRs3Nm+++abdkbzqu+++M4DZvHmz3VFKRGpqqhk6dKipXbu2CQ8PN/Xq1TOPP/64yczMtDua13z44YemXr16JjQ01NSoUcMMGTLEHD58uNRzOIwJoGkGRUREpEzROTIiIiLit1TIiIiIiN9SISMiIiJ+S4WMiIiI+C0VMiIiIuK3VMiIiIiI31IhIyIiIn5LhYyIiIj4LRUyIiIi4rdUyIiIiIjfUiEjIiIifkuFjIj4lb/++osaNWowZsyYnGXLli0jNDSUBQsW2JhMROygm0aKiN/5+uuv6d+/P8uWLaNRo0a0bt2aK6+8kgkTJtgdTURKmQoZEfFLQ4YMYf78+VxwwQWsW7eOlStXEhYWZncsESllKmRExC8dO3aM5s2bk5iYyOrVq2nRooXdkUTEBjpHRkT80vbt29m7dy8ej4ddu3bZHUdEbKI9MiLid7Kysrjwwgtp3bo1jRo1YtKkSaxbt45q1arZHU1ESpkKGRHxOw8//DCffPIJa9eupVy5cnTp0oXy5cvz5Zdf2h1NREqZDi2JiF9ZuHAhkyZNYtq0acTExBAUFMS0adP48ccfmTx5st3xRKSUaY+MiIiI+C3tkRERERG/pUJGRERE/JYKGREREfFbKmRERETEb6mQEREREb+lQkZERET8lgoZERER8VsqZERERMRvqZARERERv6VCRkRERPyWChkRERHxW/8Pi9x/mY6VwjIAAAAASUVORK5CYII=
"
class="
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>Lagrange Polynomial:
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedLatex jp-OutputArea-output " data-mime-type="text/latex">
$$12 \cdot \left(\frac{9}{8} - \frac{x}{8}\right) \left(\frac{3}{2} - \frac{x}{2}\right) + 5 \cdot \left(\frac{3}{2} - \frac{x}{6}\right) \left(\frac{x}{2} - \frac{1}{2}\right) + 6 \left(\frac{x}{8} - \frac{1}{8}\right) \left(\frac{x}{6} - \frac{1}{2}\right)$$
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>Polynomial:
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedLatex jp-OutputArea-output " data-mime-type="text/latex">
$$\frac{11 x^{2}}{24} - \frac{16 x}{3} + \frac{135}{8}$$
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>f(10) = 75/8
</pre>
</div>
</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[5]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-python"><pre><span></span><span class="n">function</span> <span class="o">=</span> <span class="p">[</span><span class="mi">10</span><span class="p">,</span><span class="mi">4</span><span class="p">,</span><span class="mi">4</span><span class="p">,</span><span class="mi">7</span><span class="p">]</span>
<span class="n">x_values</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span><span class="mi">2</span><span class="p">,</span><span class="mi">3</span><span class="p">,</span><span class="mi">5</span><span class="p">]</span>
<span class="n">lagrange_poly</span><span class="o">=</span><span class="n">interpolate_and_plot</span><span class="p">(</span><span class="n">function</span><span class="p">,</span> <span class="n">x_values</span><span class="p">)</span>
<span class="n">x_value</span> <span class="o">=</span> <span class="mi">7</span>
<span class="n">y_value</span> <span class="o">=</span> <span class="n">lagrange_poly</span><span class="o">.</span><span class="n">subs</span><span class="p">(</span><span class="s1">'x'</span><span class="p">,</span> <span class="n">x_value</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s1">'f(</span><span class="si">{</span><span class="n">x_value</span><span class="si">}</span><span class="s1">) = </span><span class="si">{</span><span class="n">y_value</span><span class="si">}</span><span class="s1">'</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAjIAAAGwCAYAAACzXI8XAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjcuMSwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy/bCgiHAAAACXBIWXMAAA9hAAAPYQGoP6dpAABakElEQVR4nO3dd3wUdf7H8ddms2kkoQRIgdAh9CaIFCnSROTArnCKXTkLqD8sp6eACugp4KlnOe8AORFRERXwJCBFQBARkN57EYGQEEKSTXZ+fwwkhCSQPjub9/Px2Aczs7Ozn89OyH4y3+98vw7DMAxEREREbMjP6gBEREREikqFjIiIiNiWChkRERGxLRUyIiIiYlsqZERERMS2VMiIiIiIbamQEREREdvytzqA0ubxeDh8+DBhYWE4HA6rwxEREZECMAyD06dPExMTg59f/tddfL6QOXz4MLGxsVaHISIiIkVw4MABatasme/zPl/IhIWFAeYHER4eXmLHdbvdzJ8/nz59+uByuUrsuN7E13P09fzA93NUfvbn6zkqv6JLSkoiNjY263s8Pz5fyJxvTgoPDy/xQiYkJITw8HCf/OEE38/R1/MD389R+dmfr+eo/Irvct1C1NlXREREbEuFjIiIiNiWChkRERGxLZ/vIyMiUlQej4f09HTL3t/tduPv709qaiqZmZmWxVGafD1H5Zc/l8uF0+ksdgwqZERE8pCens6ePXvweDyWxWAYBlFRURw4cMBnx8Hy9RyV36VVqlSJqKioYn02KmRERC5iGAZHjhzB6XQSGxt7ycG4SpPH4yE5OZnQ0FDLYihtvp6j8subYRikpKRw7NgxAKKjo4scgwoZEZGLZGRkkJKSQkxMDCEhIZbFcb5pKygoyCe/BMH3c1R++QsODgbg2LFjVK9evcjNTL73qYqIFNP5tv6AgACLIxHxbef/UHC73UU+hgoZEZF8+GKfBhFvUhL/x1TIFEVmJixbZi4vW2aui4iISJmztJBZunQpAwYMICYmBofDwezZs3M8bxgGL774ItHR0QQHB9OrVy927NhhTbDnzZoFdepA//7mev/+5vqsWVZGJSIiUi5ZWsicOXOGVq1a8e677+b5/Ouvv84//vEP3n//fVatWkWFChXo27cvqampZRzpObNmwc03w8GDObcfOmRuVzEjIlJsderUYdKkSV5znNKW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cd9995Genl7oQqYon0dBjBw5krvvvpvQ0FAiIyNzFB2F1aZNG1q1asXHH39Mnz592LRpE3Pnzs2xT0nlceFxHA5HoY575swZ+vXrR48ePZg2bRqRkZHs37+fvn37kp6eXuhYikqFTEmqd7fVEYhIaWrypPkoim7fXH4fC7hcLjIzM3Nsa9u2Ldu2baNBgwZFOubKlSupVasWAAkJCWzfvp0mTZoA0KRJE5YvX55r/0aNGuV5NWbNmjV4PB7efPNN/PzMbp0zZ87MsU9AQECuHIoiLi6OefPm5dh2YQfZS6latWqen1fjxo2ZMmUKZ86cybqCsnz5cvz8/IiLi8v3ePfffz+TJk3i0KFD9OrVi9jYPK7y5aN+/foEBASwfPlyateuDZh9WVavXl2oMWAuZ+vWrZw4cYKXXnqJpk2b4ufnxy+//FJixy8odfYVESnH6tSpw8KFCzl69CgJCQkAvPjii3z88ceMHj2aTZs2sWXLFmbMmMELL7xQoGOOGTOGhQsXsnHjRu6++26qVq2aNb7NU089xcKFC3n55ZfZvn07U6dO5aOPPuLJJ/MuEBs0aIDb7ebtt99m9+7dTJs2jffffz9XDsnJySxcuJDjx4/nuMumMB566CG2bt3KM888w/bt25k5c2ZWJ+SiXmEZMmQIQUFB3H333WzcuJFFixbx2GOPceedd+bZrHTe4MGDOXjwIP/6179ydPItiAoVKjBs2DBGjhzJ//73PzZv3swDDzxASkoK9913X5HyyEutWrUICAjgww8/ZPfu3XzzzTeWjDGjQkZEpBx78803iY+PJzY2ljZt2gDQt29f5syZw/z582nfvj1XXXUVEydOzPrr/nLGjx/P8OHDueKKKzh69CjffvstAQEBgHm1Z+bMmcyYMYPmzZszatQonnvuuXzvdGnVqhUTJkzgtddeo3nz5nzyySeMGzcuxz6dOnXi4Ycf5rbbbqNatWq8/vrrRfos6tatyxdffMGsWbNo2bIl7733XtZdS4GBgUU6ZkhICF988QUJCQm0b9+em2++mZ49e172lvOKFSty0003ERoaWqRRf8ePH89NN93EnXfeSdu2bdm5cyfff/89lStXLlIeealWrRr/+c9/+Prrr2nevDnjx4/njTfeKLHjF9gluwL7gDK7aynridOGcWSBYfw22jCS95Xoe5Y13fFif76eY5nf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RI/tLXw9R1/PD3w/R+Vnf76eo/IruvPf2+e/x/Pj84XM6dOnAYiNjbU4EhERESms06dPU7FixXyfdxiXK3VszuPxcPjwYcLCwnA4HCV23KSkJGJjYzlw4ADh4eEldlxv4us5+np+4Ps5Kj/78/UclV/RGYbB6dOniYmJwc8v/54wPn9Fxs/Pj5o1a5ba8cPDw33yh/NCvp6jr+cHvp+j8rM/X89R+RXNpa7EnKfOviIiImJbKmRERETEtlTIFFFgYCAvvfQSgYGBVodSanw9R1/PD3w/R+Vnf76eo/IrfT7f2VdERER8l67IiIiIiG2pkBERERHbUiEjIiIitqVCRkRERGxLhUw+li5dyoABA4iJicHhcDB79uzLvmbx4sW0bduWwMBAGjRowJQpU0o9zqIqbH6LFy/G4XDkehw9erRsAi6kcePG0b59e8LCwqhevTqDBg1i27Ztl33d559/TuPGjQkKCqJFixbMmzevDKItmqLkOGXKlFznMCgoqIwiLpz33nuPli1bZg201bFjR7777rtLvsZO56+w+dnp3OVl/PjxOBwORowYccn97HQOL1aQHO10HkeNGpUr1saNG1/yNVacPxUy+Thz5gytWrXi3XffLdD+e/bsoX///vTo0YN169YxYsQI7r//fr7//vtSjrRoCpvfedu2bePIkSNZj+rVq5dShMWzZMkSHnnkEVauXEl8fDxut5s+ffpw5syZfF+zYsUK7rjjDu677z7Wrl3LoEGDGDRoEBs3bizDyAuuKDmCOQLnhedw3759ZRRx4dSsWZPx48ezZs0afvnlF6655hoGDhzIpk2b8tzfbuevsPmBfc7dxVavXs0HH3xAy5YtL7mf3c7hhQqaI9jrPDZr1ixHrMuWLct3X8vOnyGXBRhfffXVJfd5+umnjWbNmuXYdttttxl9+/YtxchKRkHyW7RokQEYCQkJZRJTSTt27JgBGEuWLMl3n1tvvdXo379/jm0dOnQwHnroodIOr0QUJMfJkycbFStWLLugSljlypWNjz76KM/n7H7+DOPS+dn13J0+fdpo2LChER8fb3Tr1s0YPnx4vvva9RwWJkc7nceXXnrJaNWqVYH3t+r86YpMCfnpp5/o1atXjm19+/blp59+siii0tG6dWuio6Pp3bs3y5cvtzqcAktMTASgSpUq+e5j93NYkBwBkpOTqV27NrGxsZe9AuAtMjMzmTFjBmfOnKFjx4557mPn81eQ/MCe5+6RRx6hf//+uc5NXux6DguTI9jrPO7YsYOYmBjq1avHkCFD2L9/f777WnX+fH7SyLJy9OhRIiMjc2yLjIwkKSmJs2fPEhwcbFFkJSM6Opr333+fdu3akZaWxkcffUT37t1ZtWoVbdu2tTq8S/J4PIwYMYLOnTvTvHnzfPfL7xx6az+gCxU0x7i4OP7zn//QsmVLEhMTeeONN+jUqRObNm0q1clVi2rDhg107NiR1NRUQkND+eqrr2jatGme+9rx/BUmP7udO4AZM2bw66+/snr16gLtb8dzWNgc7XQeO3TowJQpU4iLi+PIkSOMHj2aq6++mo0bNxIWFpZrf6vOnwoZKZC4uDji4uKy1jt16sSuXbuYOHEi06ZNszCyy3vkkUfYuHHjJdt27a6gOXbs2DHHX/ydOnWiSZMmfPDBB7z88sulHWahxcXFsW7dOhITE/niiy8YOnQoS5YsyffL3m4Kk5/dzt2BAwcYPnw48fHxXtuZtbiKkqOdzmO/fv2yllu2bEmHDh2oXbs2M2fO5L777rMwspxUyJSQqKgofv/99xzbfv/9d8LDw21/NSY/V155pdcXB48++ihz5sxh6dKll/1rJ79zGBUVVZohFlthcryYy+WiTZs27Ny5s5SiK56AgAAaNGgAwBVXXMHq1at56623+OCDD3Lta8fzV5j8Lubt527NmjUcO3YsxxXbzMxMli5dyjvvvENaWhpOpzPHa+x2DouS48W8/TxeqFKlSjRq1CjfWK06f+ojU0I6duzIwoULc2yLj4+/ZHu33a1bt47o6Girw8iTYRg8+uijfPXVV/zwww/UrVv3sq+x2zksSo4Xy8zMZMOGDV57Hi/m8XhIS0vL8zm7nb+8XCq/i3n7uevZsycbNmxg3bp1WY927doxZMgQ1q1bl+cXvN3OYVFyvJi3n8cLJScns2vXrnxjtez8lWpXYhs7ffq0sXbtWmPt2rUGYEyYMMFYu3atsW/fPsMwDOPZZ5817rzzzqz9d+/ebYSEhBgjR440tmzZYrz77ruG0+k0/ve//1mVwiUVNr+JEycas2fPNnbs2GFs2LDBGD58uOHn52csWLDAqhQuadiwYUbFihWNxYsXG0eOHMl6pKSkZO1z5513Gs8++2zW+vLlyw1/f3/jjTfeMLZs2WK89NJLhsvlMjZs2GBFCpdVlBxHjx5tfP/998auXbuMNWvWGLfffrsRFBRkbNq0yYoULunZZ581lixZYuzZs8f47bffjGeffdZwOBzG/PnzDcOw//krbH52Onf5ufiOHrufw7xcLkc7ncennnrKWLx4sbFnzx5j+fLlRq9evYyqVasax44dMwzDe86fCpl8nL/d+OLH0KFDDcMwjKFDhxrdunXL9ZrWrVsbAQEBRr169YzJkyeXedwFVdj8XnvtNaN+/fpGUFCQUaVKFaN79+7GDz/8YE3wBZBXbkCOc9KtW7esfM+bOXOm0ahRIyMgIMBo1qyZMXfu3LINvBCKkuOIESOMWrVqGQEBAUZkZKRx3XXXGb/++mvZB18A9957r1G7dm0jICDAqFatmtGzZ8+sL3nDsP/5K2x+djp3+bn4S97u5zAvl8vRTufxtttuM6Kjo42AgACjRo0axm233Wbs3Lkz63lvOX8OwzCM0r3mIyIiIlI61EdGREREbEuFjIiIiNiWChkRERGxLRUyIiIiYlsqZERERMS2VMiIiIiIbamQEREREdtSISMiIiK2pUJGREREbEuFjIiIiNiWChkRERGxLRUyImIrf/zxB1FRUYwdOzZr24oVKwgICGDhwoUWRiYiVtCkkSJiO/PmzWPQoEGsWLGCuLg4WrduzcCBA5kwYYLVoYlIGVMhIyK29Mgjj7BgwQLatWvHhg0bWL16NYGBgVaHJSJlTIWMiNjS2bNnad68OQcOHGDNmjW0aNHC6pBExALqIyMitrRr1y4OHz6Mx+Nh7969VocjIhbRFRkRsZ309HSuvPJKWrduTVxcHJMmTWLDhg1Ur17d6tBEpIypkBER2xk5ciRffPEF69evJzQ0lG7dulGxYkXmzJljdWgiUsbUtCQitrJ48WImTZrEtGnTCA8Px8/Pj2nTpvHjjz/y3nvvWR2eiJQxXZERERER29IVGREREbEtFTIiIiJiWypkRERExLZUyIiIiIhtqZARERER21IhIyIiIralQkZERERsS4WMiIiI2JYKGREREbEtFTIiIiJiWypkRERExLb+H29Am9aqMhJkAAAAAElFTkSuQmCC
"
class="
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>Lagrange Polynomial:
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedLatex jp-OutputArea-output " data-mime-type="text/latex">
$$10 \cdot \left(\frac{5}{4} - \frac{x}{4}\right) \left(\frac{3}{2} - \frac{x}{2}\right) \left(2 - x\right) + 4 \cdot \left(\frac{5}{3} - \frac{x}{3}\right) \left(3 - x\right) \left(x - 1\right) + 4 \cdot \left(\frac{5}{2} - \frac{x}{2}\right) \left(\frac{x}{2} - \frac{1}{2}\right) \left(x - 2\right) + 7 \left(\frac{x}{4} - \frac{1}{4}\right) \left(\frac{x}{3} - \frac{2}{3}\right) \left(\frac{x}{2} - \frac{3}{2}\right)$$
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>Polynomial:
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedLatex jp-OutputArea-output " data-mime-type="text/latex">
$$- \frac{5 x^{3}}{8} + \frac{27 x^{2}}{4} - \frac{175 x}{8} + \frac{103}{4}$$
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>f(7) = -11
</pre>
</div>
</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[6]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-python"><pre><span></span><span class="n">function</span> <span class="o">=</span> <span class="p">[</span><span class="mi">12</span><span class="p">,</span><span class="mi">13</span><span class="p">,</span><span class="mi">14</span><span class="p">,</span><span class="mi">15</span><span class="p">]</span>
<span class="n">x_values</span> <span class="o">=</span> <span class="p">[</span><span class="mi">5</span><span class="p">,</span><span class="mi">6</span><span class="p">,</span><span class="mi">7</span><span class="p">,</span><span class="mi">8</span><span class="p">]</span>
<span class="n">lagrange_poly</span><span class="o">=</span><span class="n">interpolate_and_plot</span><span class="p">(</span><span class="n">function</span><span class="p">,</span> <span class="n">x_values</span><span class="p">)</span>
<span class="n">x_value</span> <span class="o">=</span> <span class="mi">10</span>
<span class="n">y_value</span> <span class="o">=</span> <span class="n">lagrange_poly</span><span class="o">.</span><span class="n">subs</span><span class="p">(</span><span class="s1">'x'</span><span class="p">,</span> <span class="n">x_value</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s1">'f(</span><span class="si">{</span><span class="n">x_value</span><span class="si">}</span><span class="s1">) = </span><span class="si">{</span><span class="n">y_value</span><span class="si">}</span><span class="s1">'</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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vPHGG059T5w4kb59+7Jr1y4ef/xxR/vo0aN577332LJlC5UqVaJ3796OEaJt27bRr18/HnroIXbt2sX48eN58803mT17drbH4OHhwb/+9S/27NnDnDlz+Omnn3jppZcA+5PRp02bRlBQECdPnuTkyZO8+OKL2fY1adIk+vXrx86dO7nrrrt45JFH+PPPPwGIi4vjgQceoE+fPuzYsYOnn36al19+OZcZBy8vL7y9vUlJSeHy5cv06NGDcuXKsWXLFr7++mtWrVrFsGHDstz3wQcfJC0tzakwO3PmDEuXLmXIkCGOttjYWBYvXsySJUtYsmQJP//8M2+99ZZj/UsvvcQ333zDnDlz2L59O7Vq1aJHjx6OY003ceJEpk+fzoYNGzh69Cj9+vVj2rRpfPnllyxdupSVK1fywQcfZHusVquV1157jR07drB48WIOHz7M4MGDc50zESkAV8/A6p6wYYD9cvdrlappTkyFzZBMLl68aADGxYsXM627cuWK8dtvvxlXrlzJvONv7xnGoio5ftkWVTFSou400tLSnPdd0/uG+xqLqthfIw8GDRpk3HvvvY7l22+/3ejQoYPTNi1btjTGjBnjWAaMb7/91mmbLl26GG+++aZT29y5c43Q0FCn/UaMGOG0zerVqw3AmD9/vqPt3Llzhr+/v7FgwQLDMAxjwIABRrdu3Rzr09LSjOeee85o0KCBo6169erG1KlTsz3Or7/+2qhQoYJj+bPPPjPKlCmTabvr+wGMV155xbGcmJhoAMaPP/5oGIZhjBkzxmjUqJFTHy+//LIBGOfPn882nmtfJzk52XjzzTcNwFiyZInx4YcfGuXKlTMSExMd2y9dutTw8PAwTp06ZRhG5p/b0KFDjZ49ezqW33vvPaNmzZpGamqqcf78eWP8+PFGQECAkZCQ4Nhm9OjRRuvWrR3H5e3tbcybN8+xPiUlxQgLCzPeeecdwzAyflarVq1ybDN58mQDMGJjYx1tTz/9tNGjRw/H8u23324MHz4821xs2bLFAIxLly45vU52+cvxd+0mpKSkGIsXLzZSUlLytd+SSLlyXbHK1anVhrEo1DDmYf/K49+VvCrIXOX09/t6JXt8q7BZE+DK8Rw3sQAW37DMK66eveG+jtfIJ7feeqvTcmho6A1PUezYsYP169c7jfikpaVx9epVkpKSHPNqWrRokeX+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
"
class="
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>Lagrange Polynomial:
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedLatex jp-OutputArea-output " data-mime-type="text/latex">
$$12 \cdot \left(\frac{8}{3} - \frac{x}{3}\right) \left(\frac{7}{2} - \frac{x}{2}\right) \left(6 - x\right) + 13 \cdot \left(4 - \frac{x}{2}\right) \left(7 - x\right) \left(x - 5\right) + 14 \cdot \left(8 - x\right) \left(\frac{x}{2} - \frac{5}{2}\right) \left(x - 6\right) + 15 \left(\frac{x}{3} - \frac{5}{3}\right) \left(\frac{x}{2} - 3\right) \left(x - 7\right)$$
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>Polynomial:
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedLatex jp-OutputArea-output " data-mime-type="text/latex">
$$x + 7$$
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>f(10) = 17
</pre>
</div>
</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[7]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-python"><pre><span></span><span class="n">function</span> <span class="o">=</span> <span class="s1">'np.sin(3*x)'</span>
<span class="n">x_values</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mf">2.2</span><span class="p">,</span> <span class="mf">1.2</span><span class="o">/</span><span class="mi">5</span><span class="p">)</span>
<span class="n">lagrange_poly</span><span class="o">=</span><span class="n">interpolate_and_plot</span><span class="p">(</span><span class="n">function</span><span class="p">,</span> <span class="n">x_values</span><span class="p">)</span>
<span class="n">x_value</span> <span class="o">=</span> <span class="mf">1.5</span>
<span class="n">y_value</span> <span class="o">=</span> <span class="n">lagrange_poly</span><span class="o">.</span><span class="n">subs</span><span class="p">(</span><span class="s1">'x'</span><span class="p">,</span> <span class="n">x_value</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s1">'f(</span><span class="si">{</span><span class="n">x_value</span><span class="si">}</span><span class="s1">) = </span><span class="si">{</span><span class="n">y_value</span><span class="si">}</span><span class="s1">'</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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
"
class="
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>Lagrange Polynomial:
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedLatex jp-OutputArea-output " data-mime-type="text/latex">
$$0.141120008059867 \cdot \left(1.83333333333333 - 0.833333333333333 x\right) \left(2.04166666666667 - 1.04166666666667 x\right) \left(2.38888888888889 - 1.38888888888889 x\right) \left(3.08333333333333 - 2.08333333333333 x\right) \left(5.16666666666667 - 4.16666666666667 x\right) - 0.546691047069287 \cdot \left(2.29166666666667 - 1.04166666666667 x\right) \left(2.72222222222222 - 1.38888888888889 x\right) \left(3.58333333333333 - 2.08333333333333 x\right) \left(6.16666666666667 - 4.16666666666667 x\right) \left(4.16666666666667 x - 4.16666666666667\right) - 0.963130930573316 \cdot \left(3.05555555555556 - 1.38888888888889 x\right) \left(4.08333333333333 - 2.08333333333333 x\right) \left(7.16666666666667 - 4.16666666666667 x\right) \left(2.08333333333333 x - 2.08333333333333\right) \left(4.16666666666667 x - 5.16666666666667\right) - 0.901483655966355 \cdot \left(4.58333333333333 - 2.08333333333333 x\right) \left(8.16666666666667 - 4.16666666666667 x\right) \left(1.38888888888889 x - 1.38888888888889\right) \left(2.08333333333333 x - 2.58333333333333\right) \left(4.16666666666667 x - 6.16666666666667\right) - 0.392350223991454 \cdot \left(9.16666666666666 - 4.16666666666666 x\right) \left(1.04166666666667 x - 1.04166666666667\right) \left(1.38888888888889 x - 1.72222222222222\right) \left(2.08333333333333 x - 3.08333333333333\right) \left(4.16666666666667 x - 7.16666666666667\right) + 0.311541363513379 \cdot \left(0.833333333333333 x - 0.833333333333333\right) \left(1.04166666666667 x - 1.29166666666667\right) \left(1.38888888888889 x - 2.05555555555555\right) \left(2.08333333333333 x - 3.58333333333333\right) \left(4.16666666666666 x - 8.16666666666666\right)$$
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>Polynomial:
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedLatex jp-OutputArea-output " data-mime-type="text/latex">
$$0.158971738189597 x^{5} - 4.15677756965995 x^{4} + 22.1418723414744 x^{3} - 44.5116803448296 x^{2} + 35.5457283025997 x - 9.0369944597141$$
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>f(1.5) = -0.977358438732647
</pre>
</div>
</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[9]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-python"><pre><span></span><span class="n">function</span> <span class="o">=</span> <span class="s1">'np.sqrt(1+x**2)'</span>
<span class="n">x_values</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="o">/</span><span class="mi">3</span><span class="p">)</span>
<span class="n">lagrange_poly</span><span class="o">=</span><span class="n">interpolate_and_plot</span><span class="p">(</span><span class="n">function</span><span class="p">,</span> <span class="n">x_values</span><span class="p">)</span>
<span class="n">x_value</span> <span class="o">=</span> <span class="n">x_values</span><span class="p">[</span><span class="mi">2</span><span class="p">]</span>
<span class="n">y_value</span> <span class="o">=</span> <span class="n">lagrange_poly</span><span class="o">.</span><span class="n">subs</span><span class="p">(</span><span class="s1">'x'</span><span class="p">,</span> <span class="n">x_value</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s1">'f(</span><span class="si">{</span><span class="n">x_value</span><span class="si">}</span><span class="s1">) = </span><span class="si">{</span><span class="n">y_value</span><span class="si">}</span><span class="s1">'</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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6dN8P/30E7Vr1zbuf48ePbh79+4zcyWEyFwTJsBffxneL97dn73nG6PVWePSdh1YZ8yDgXMbsxZTUVFR+Pj4sCDxaYnPERcXR+HChRk/fjw+Pj4p9tmwYQPBwcHG15kzZ7C0tOStt94y6ffaa6+Z9FuzZs1L709utHz5chwdHfnnn3+YOXMmU6ZMISAgAMD45bps2TKCg4ON0/v37+fdd99l2LBhnDt3ju+//x5/f38+//xzk3VPmjSJN954g9OnT9O3b19j+8cff8zs2bM5evQohQoVonv37sYjV8ePH6dLly5069aN06dPM2nSJD777DP8/f1T3QcLCwu+/vprzp49y/Lly/nrr78YPXo0APXr12fevHk4OzsbPwujRo1KdV2TJ0+mS5cunDp1ijZt2vD222/z4MEDAIKCgujcuTMdO3bk5MmTvP/++3z66afpzDhYWVlhbW1NfHw8UVFRtGrVCldXV44ePcq6devYs2cPQ4cOTXHZt956C51OZ1Lk3b17ly1btpjk+MqVK2zatInNmzezefNm9u7dy4wZM4zzR48eza+//sry5cv5999/KVOmDK1atTLua6JJkybx7bff8vfff3Pz5k26dOnCvHnzWL16NVu2bGHHjh188803qe6rVqtl6tSpnDx5kk2bNnHt2jV69+6d7pwJITLGb7/B9OlJ07cfFKOn/188rrcXy8K1zRdYdqeyCUBt3Lgxzf2bNGmihg0b9tx+c+fOVU5OTioyMtLY1qtXL9WhQ4f0B/mER48eKUA9evQo2byYmBh17tw5FRMTYzrj3GylNhR95ku/oaiKD3hN6XQ602X3tHvusmpDUcM2XtDTeWnSpIlq2LChSZ86deqoMWPGGKdT+rm9+uqr6osvvjBp++mnn5SHh4fJcsOHDzfps3v3bgWotWvXGtvu3bun7O3t1Zo1a5RSSvXo0UO1aNHCZLmPP/5YVapUyThdokQJNXfu3FT3c/369apgwYLG6WXLlqn8+fMn6/f0egA1fvx443RkZKQC1J9//qmUUmrMmDGqSpUqJuv49NNPFaAePnyYajxPbicuLk598cUXClCbN29WP/zwg3J1dTV+fnU6nVq3bp2ysLBQISEhSqnkP7cPPvhAtW7d2jg9e/ZsVapUKaXX65VSSk2cOFE5ODioiIgIY5+PP/5Y1atXz7hf1tbWatWqVcb5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
"
class="
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>Lagrange Polynomial:
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedLatex jp-OutputArea-output " data-mime-type="text/latex">
$$3.16227766016838 x \left(2.0 - 3.0 x\right) + 1.80277563773199 x \left(3.0 x - 1.0\right) + 1.0 \cdot \left(1.0 - 3.0 x\right) \left(1.0 - 1.5 x\right)$$
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>Polynomial:
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedLatex jp-OutputArea-output " data-mime-type="text/latex">
$$0.421493932690847 x^{2} + 0.0217796826047643 x + 1.0$$
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>f(0.6666666666666666) = 1.20185042515466
</pre>
</div>
</div>

</div>

</div>

</div>





</body>







</html>
</div>
