# Lesson 4 - CSS Transitions, Transformations & Animations 

## Overview

We've spent the last couple of weeks learning both basic and more advanced CSS, and this week we're going to make our pages *move*. What do I mean by *move*? I mean that we're going to learn about how to add *movement* to our websites using CSS transitions and animations! We're going to start out by playing around with how transitions and animations work on their own, and then we're going to take what we've learned and write some transitions or animations for the pages we've been working on over the past four weeks.

## Diving In

We're going to get back to your projects in a bit, but for now we're just going to get our hands dirty. I want everybody to go to CodePen and create a new pen. Uncheck the checkbox in the JS panel:

![](http://f.cl.ly/items/2n1z1d2c1m3p0Y121j2l/Screen-Shot-2013-12-02-at-7.52.32-PM.jpg)

and then click on the gear next to the CSS section, and make sure that the box that says "Prefix free" is checked.

![](http://f.cl.ly/items/3s3C2r281s193P1V2g0z/Screen-Shot-2013-12-02-at-8.00.30-PM.jpg)

## Transitions

To get a better idea of how transitions work, we're going to create a simple example. In our HTML, we're going to create a single element, a `<div>` with a class of `box`.

``` html
<div class="box"></div>
```

And to our CSS we'll add some simple styles to center the box, set its width and height, and make the background a light grey.

``` css
.box {
  width: 100px;
  height: 100px;
  margin: 20px auto;
  background: #ccc;
}
```






