---
layout: post
title: Single Page Application Layout using Flexbox
tags:
  css
  flexbox
---

In a recent project I wanted a single page application layout. There should be a fixed header and footer, possibly left and right panels and the center area should scroll. Normally I do it using `position: absolute;` or `position: fixed;`. However in this project I had modals bundled with components inside the panels. Because of how z-indexes work this can cause issues with layering other panels since the `position: absolute;` will fix any of that element and its children at its spot in the z layering.

My solution was to use flexbox since it wouldn't require any positioning of the panels. Unfortunately I needed to add another flex box container for the middle row.

[JSFiddle of my solution](https://jsfiddle.net/c1uxeh3q/)

The way it works is by first defining a container that fills 100% of the height, dropping a `display: flex;` on that which will keep the header at the top, the footer at the bottom and the middle row filling up the rest of the space. Headers and footers also have

```
height: 50px;
flex: 0 0 auto;
```

meaning don't grow, don't shrink, take your default size (i.e. height) from the height value.

Once we have that we add another `display: flex;` onto the middle row but make it a row flex instead. Similarily here left and right both have 

```
width: 50px;
flex: 0 0 auto;
```

with the same meaning as header and footer.

The final trick we need is to get the center panel to scroll, normally it would just expand the containers and scroll the whole page instead. The trick is to add `flex: 0 1 100%;` to the middle row panel. This means don't grow, but you can shrink, start with your size (height) at 100%. This makes it so that this middle row can shrink in height but won't let it grow. Also don't forget to add `overflow: auto;` onto the center panel so those scroll bars show up.

As an added bonus, the left and right panels can be removed and it will auto expand the center area.
