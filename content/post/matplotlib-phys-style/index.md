---
title: "Matplotlib style for publications"
description:
date: 2024-06-01T15:15:52+10:00
image:
math: true
license:
hidden: false
comments: true
draft: false
tags: [matplotlib]
categories: []
---


# Matplotlib style for publications

The defalt matplotlib style is not very pretty out of the box. I always found myself doing the same minor adjustmenst over and over again. Finially, I got bored and found a way of how to tweak the style file one time, and then just include it like this:
```python
plt.rcdefaults()  # reset to default
plt.style.use('phys-plots.mplstyle')
```

What is changes:
- Default figure size is set to `(3.28, 2.5)` inc as it is default for the most two column papers
- dpi is increased to `250`
- font size increased and set to `7`
- make legend more minimal 
- default cmap is `inferno`
- other minor tweaks

Here is the content of `phys-plots.mplstyle` file:
```python
# all default values can be found here
# https://matplotlib.org/stable/tutorials/introductory/customizing.html


# size
figure.figsize:     3.28, 2.5  # figure size in inches
figure.dpi:         250       # figure dots per inch
figure.autolayout: True

## font settings
font.size : 7

font.family:  sans-serif
#font.style:   normal
#font.variant: normal
#font.weight:  normal
#font.stretch: normal

# https://askubuntu.com/a/1148258
font.serif:      DejaVu Serif, Bitstream Vera Serif, Computer Modern Roman, New Century Schoolbook, Century Schoolbook L, Utopia, ITC Bookman, Bookman, Nimbus Roman No9 L, Times New Roman, Times, Palatino, Charter, serif
font.sans-serif: Nimbus Sans, Helvetica, Computer Modern Sans Serif, DejaVu Sans, Bitstream Vera Sans, Lucida Grande, Verdana, Geneva, Lucid, Arial, Avant Garde, sans-serif
font.cursive:    Apple Chancery, Textile, Zapf Chancery, Sand, Script MT, Felipa, Comic Neue, Comic Sans MS, cursive
font.fantasy:    Chicago, Charcoal, Impact, Western, Humor Sans, xkcd, fantasy
font.monospace:  DejaVu Sans Mono, Bitstream Vera Sans Mono, Computer Modern Typewriter, Andale Mono, Nimbus Mono L, Courier New, Courier, Fixed, Terminal, monospace

# no x margins
axes.xmargin : 0
# no y margins 
# axes.ymargin : 0

## colors
# seaborn deep palette
#axes.prop_cycle : cycler('color', ['4C72B0', '55A868', 'C44E52', '8172B2', 'CCB974', '64B5CD'])

# default but rearranged
#axes.prop_cycle : cycler('color', ['1f77b4', 'd62728', 'ff7f0e', '2ca02c',  '9467bd', '8c564b', 'e377c2', '7f7f7f', 'bcbd22', '17becf'])


# Tick properties
# x-axis
#xtick.top: True
#xtick.direction: in
xtick.major.size: 2.5  # default 3.5
xtick.major.width: 0.5  # default 0.8
#xtick.minor.size: 3
#xtick.minor.width: 1

# y-axis
#ytick.right: True
#ytick.direction: in
ytick.major.size: 2.5  # default 3.5
ytick.major.width: 0.5  # default 0.8
#ytick.minor.size: 3
#ytick.minor.width: 1

## ticks and lines
#lines.linewidth : 2  # default 1.5
axes.linewidth : 0.5  # default 0.8

## Legend properties
legend.framealpha: 0.6
#legend.frameon: False
legend.fancybox : False
#legend.shadow: True
legend.edgecolor : none

# colormaps
image.aspect: auto
image.cmap: inferno


# Always save as 'tight'
savefig.bbox : tight
savefig.pad_inches : 0.01  # Use virtually all space when we specify figure dimensions


# LaTeX packages
text.latex.preamble : \usepackage{amsmath} \usepackage{amssymb} \usepackage{sfmath} 
```