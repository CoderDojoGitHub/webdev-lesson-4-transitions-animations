# Lesson 4 - Even more CSS!

**Transitions, transformations & animations!**

## Overview

We've spent the last couple of weeks learning both basic and more advanced CSS, and this week we're going to make our pages *move*. What do I mean by *move*? I mean that we're going to learn about how to add *movement* to our websites using CSS transitions and animations! We're going to start out by playing around with how transitions and animations work on their own, and then we're going to take what we've learned and write some transitions or animations for the pages we've been working on over the past four weeks.

## Diving in

We're going to get back to your projects in a bit, but for now we're just going to get our hands dirty. I want everybody to go to CodePen and [create a new pen](http://codepen.io/pen/). Uncheck the checkbox in the JS panel:

![](http://f.cl.ly/items/2n1z1d2c1m3p0Y121j2l/Screen-Shot-2013-12-02-at-7.52.32-PM.jpg)

and then click on the gear next to the CSS section, and make sure that the box that says "Prefix free" is checked.

![](http://f.cl.ly/items/3s3C2r281s193P1V2g0z/Screen-Shot-2013-12-02-at-8.00.30-PM.jpg)

## Basic transitions

To get a better idea of how transitions work, we're going to create a simple example. In our HTML, we're going to create a single element, a `<div>` with a class of `box`.

``` html
<div class="box"></div>
```

And to our CSS we'll add some simple styles to center the box, set its width and height, and make the background silver.

``` css
.box {
  width: 100px;
  height: 100px;
  margin: 100px auto;
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
  // ...
  transition-property: background;
  transition-duration: 1s;
  transition-timing-function: ease;
}
```
We've added three new properties, all starting with “transition-”. These three properties tell the browser the three things it needs to know about what you want to transition: the *properties* you want to transition, *how many seconds*, or *how long*, it should take to transition from one value to the next, and the *timing* of the transition.

*Try hovering on your box again.* **Tada!** With our new CSS, we're now *transitioning* from one background color to the next. Now try changing the `transition-duration` value to something longer, like “5s”. When you hover on your box again, it will take much longer (5 seconds, to be exact) to transition from your first color, “silver”, to your second color. After you've experimented, let's go ahead and set the duration to “0.5s”, or a half of a second, to make it quick to see our transitions when we make changes.

## Basic transforms

Let's make our box do something else when we hover on it. Let's say that when we hover on the box we want it to get *bigger*. In order to do this we're going to need to use something called **CSS Transforms**, a part of CSS that allows us to change the size, position and rotation of objects. To start, let's add a few lines of CSS to what we have.

``` scss
.box {
  // ...
  transform: scale(1);
  backface-visibility: hidden;
}
.box:hover {
  // ...
  transform: scale(1.5);
}
```

Once again, hover over your box. AH! What's happening? The square is getting bigger when we hover, but it's *jumping* to the new property value, just like our background color was earlier. *Who thinks they know how to have the scale be transitioned as well?*

After appending `transform` to the value of `transition-property`, we get something that looks like this:

``` scss
transform-property: background, transform;
}
```

This line now tells the browser that for our class `.box` we want to transition *both* the background and transform properties. Hover over that box again and see that we've successfully instructed the browser to smoothly transition the scale of the box as well.

So now the question is: **what else can we do with transforms**? Well, for one, we can chain transforms together by adding to the value of our `transform` property. Try changing the `transform` property for when we hover on the box to include rotation:

``` scss
.box:hover {
  // ...
  transform: scale(1.5) rotate(45deg);
}
```

Rotation transforms use “degrees” as a unit. These are the same kind of degrees you may have learned in math class, like how a circle has 360 degrees, or a halfpipe in sports is 180 degrees. We're saying that we want to rotate our box 45 degrees when we hover on it, or about 1/8th of a full rotation.

Now I want you to think of a chain of transforms that you want to apply to your box when you hover on it. Maybe you want it to shrink, move to the left, and do a full spin. Maybe it will grow only horizontally, and rotate just slightly as if to say, “may I help you?”. Take some time now to create an interesting chain of transforms. You can combine any of these:

* scale(2) - Makes the box double its original size
* scaleX(1.5) - Scales the *width* of the box to be 1.5 times its original width
* scaleY(3) - Scales the *height* of the box to be 3 times its original height
* rotate(10deg) - Rotates the whole box by 10 degrees
* translateX(50px) - Moves the box 50 pixels to the *right*. Negative values move it *left*.
* translateY(100px) - Moves the box 100 pixels *down*. Negative values move it *up*.

Here's an example:

``` scss
transform: translateX(-50px) translateY(100px) rotate(90deg);
```

This transform would make our box move 50 pixels to the left (`translateX(-50px)`), 100 pixels down (`translateY(100px)`) and rotate 90 degrees (`rotate(90deg)`).

## Advanced lesson notes!

Working ahead? Bored? Done this before? No problem. Here are some more advanced topics related to the lesson that you can explore or read more about.

### Timing functions

Remember that `transition-timing-function` property we've been using? Curious about what it's for?

@todo

### Stacking contexts

In the [Transforms sections](#transforms) did you notice how we defined `transform` twice, once to set the scale to 1 and again to set it to 1.5 when we hover? Try removing that first one and then hover on your square again. Notice how the box flickers a little before it starts animating? This is because CSS Transforms create a new [stacking context](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Understanding_z_index/The_stacking_context). The flicker is caused by our box moving onto a new stacking context when we hover on it. By setting the transform in both places, we tell the browser to make sure the box is *already* on its own stacking context. That way, when we hover on it, it doesn't need to switch contexts, and it doesn't flicker.
