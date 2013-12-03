# Lesson 4 - Even more CSS!

**Transitions, Transformations & Animations!**

## Overview

We've spent the last couple of weeks learning both basic and more advanced CSS, and this week we're going to make our pages *move*. What do I mean by *move*? I mean that we're going to learn about how to add *movement* to our websites using CSS transitions and animations! We're going to start out by playing around with how transitions and animations work on their own, and then we're going to take what we've learned and write some transitions or animations for the pages we've been working on over the past four weeks.

## Diving In

We're going to get back to your projects in a bit, but for now we're just going to get our hands dirty. I want everybody to go to CodePen and [create a new pen](http://codepen.io/pen/). Uncheck the checkbox in the JS panel:

![](http://f.cl.ly/items/2n1z1d2c1m3p0Y121j2l/Screen-Shot-2013-12-02-at-7.52.32-PM.jpg)

and then click on the gear next to the CSS section, and make sure that the box that says "Prefix free" is checked.

![](http://f.cl.ly/items/3s3C2r281s193P1V2g0z/Screen-Shot-2013-12-02-at-8.00.30-PM.jpg)

## Transitions

To get a better idea of how transitions work, we're going to create a simple example. In our HTML, we're going to create a single element, a `<div>` with a class of `box`.

``` html
<div class="box"></div>
```

And to our CSS we'll add some simple styles to center the box, set its width and height, and make the background silver.

``` css
.box {
  width: 100px;
  height: 100px;
  margin: 20px auto;
  background: silver;
}
.box:hover {
  background: silver;
}
```

Nothing complicated. You should see a box on your screen, centered horizontally, with a grey-ish background. We want to change the color of our box when we hover on it. In our `.box:hover` selector, I want you to change value of our background to something different. Try one of these:

* Salmon
* SpringGreen
* LightPink
* CornflowerBlue

Now when we hover on our box, it changes to the new color we specified. By default, when a value changes in CSS, the browser applies the changes immediately. The box is grey, you hover on it, and then it's not grey. This is where transitions come in.

**CSS Transitions allow us animate the changing of a property in CSS.** Let's add a few more lines of CSS:

``` css
.box {
  width: 100px;
  height: 100px;
  margin: 20px auto;
  background: silver;
  transition-property: background;
  transition-duration: 1s;
  transition-timing-function: ease;
}
.box:hover {
  background: silver;
}
```
We've added three new properties, all starting with “transition-”. These three properties tell the browser the three things it needs to know about what you want to transition: the *properties* you want to transition, *how many seconds*, or *how long*, it should take to transition from one value to the next, and the *timing* of the transition.

*Try hovering on your box again.* Tada! With our new CSS, we're now *transitioning* from one background color to the next. Now try changing the `transition-duration` value to something longer, like “5s”. When you hover on your box again, it will take much longer (5 seconds, to be exact) to transition from your first color, “silver”, to your second color. After you've experimented, let's go ahead and set the duration to “0.5s”, or a half of a second, to make it quick to see our transitions when we make changes.

## Transforms

Let's make our box do something else when we hover on it. Let's say that when we hover on the box we want it to get *bigger*. In order to do this we're going to need to use something called **CSS Transforms**, a part of CSS that allows us to change the size, position and rotation of objects. 
