# Lesson 4 - Even more CSS!

**Transitions, transformations & animations!**

## Overview

We've spent the last couple of weeks learning both basic and more advanced CSS, and this week we're going to make our pages *move*. What do I mean by *move*? I mean that we're going to learn about how to add *movement* to our websites using CSS “transitions” and “animations”, and another thing called “transforms”! We're going to start out by playing around with how transitions, transforms, and animations work on their own, and then we're going to take what we've learned and write some transitions or animations for the pages we've been working on over the past three lessons.

## Diving in

We're going to get back to your projects in a bit, but for now we're just going to get our hands dirty. I want everybody to go to CodePen and [create a new pen](http://codepen.io/pen/). Uncheck the checkbox in the JS panel to give ourselves some more room to work:

![](http://f.cl.ly/items/2n1z1d2c1m3p0Y121j2l/Screen-Shot-2013-12-02-at-7.52.32-PM.jpg)

and then click on the gear next to the CSS section, and make sure that the checkbox labeled "Prefix free" is checked.

![](http://f.cl.ly/items/3s3C2r281s193P1V2g0z/Screen-Shot-2013-12-02-at-8.00.30-PM.jpg)

## Basic transitions

To get a better idea of how transitions work, we're going to create a simple example. In our HTML, we're going to create a single element, a `<div>` with a class of `box`.

``` html
<div class="box"></div>
```

To our CSS we'll add some simple styles to center the box, set its width and height, and make the background silver. Go ahead and just copy and paste this into your CSS area:

``` scss
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

Nothing complicated. You should see a box on your screen, centered horizontally, with a grey-ish background.

Now we want to change the color of our box when we hover on it. In our `.box:hover` selector, I want you to change the value of our background to something different. Try one of these:

* Salmon
* SpringGreen
* LightPink
* CornflowerBlue

Now when we hover on our box, it changes to the new color we specified. By default, when a value changes in CSS, the browser applies the changes immediately. The box is grey, you hover on it, and then it's not grey. This is where transitions come in.

**CSS Transitions allow us animate, or “transition”, the changing of a property in CSS.** Let's add a few more lines of CSS:

``` scss
.box {
  // ...
  transition-property: background;
  transition-duration: 1s;
  transition-timing-function: ease;
}
```

We've added three new properties, all starting with “transition-”. These three properties tell the browser the three things it needs to know about what you want to transition, or animate: the *properties* you want to transition, *how many seconds*, or *how long*, it should take to transition from one value to the next, and the *timing* of the transition.

*Try hovering on your box again.* **Tada!** With our new CSS, we're now *transitioning* from one background color to the next. Now try changing the `transition-duration` value to something longer, like “5s”. When you hover on your box again, it will take much longer (5 seconds, to be exact) to transition from your first color, “silver”, to your second color. After you've experimented, let's go ahead and set the duration to “0.5s”, or a half of a second, to make it quick to see our transitions when we make changes.

## Basic transforms

Let's make our box do something else when we hover on it. Let's say that when we hover on the box we want it to get *bigger*. One way to do this would be to change the height and width of the element when we hover on it. However, changing the height and the width will affect the position of elements *around* our box, and we might not want that. Instead we're going to use something called **CSS Transforms**, a part of CSS that allows us to change the size, position and rotation of objects *without* affecting things around it, or what we would say is the “flow” of our document. To start, let's add a few lines of CSS to what we have.

``` scss
body {
  perspective: 1000;
}
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

Now I want you to think of a combination of transforms that you want to apply to your box when you hover on it. Maybe you want it to shrink, move to the left, and do a full spin. Maybe it will grow only horizontally, and rotate just slightly to the left. Take some time now to create an interesting combination of transforms, You can combine any of these, and if you're trying to do something that you just can't figure out, put your hand up and one of us will help you get the right combo:

* scale(2) - Makes the box double its original size
* scaleX(1.5) - Scales the *width* of the box to be 1.5 times its original width
* scaleY(3) - Scales the *height* of the box to be 3 times its original height
* rotate(10deg) - Rotates the whole box by 10 degrees
* rotateX(15deg) - Rotates the box 15 degrees on its X-axis
* rotateY(-25deg) - Rotates the box -25 degrees on its Y-axis
* translateX(50px) - Moves the box 50 pixels to the *right*. Negative values move it *left*.
* translateY(100px) - Moves the box 100 pixels *down*. Negative values move it *up*.

Here's an example:

``` scss
transform: rotateY(30deg) rotateX(10deg) scale(1.5);
```

This transform would make our box rotate a little bit to the right (`rotateY(3deg)`), rotate a little bit away from us (`rotateX(10deg)`) and grow to be 1.5 times its original size (`scale(1.5)`).

Here's my box for you to check out: http://codepen.io/mikefowler/pen/DyIHE

## Back to our projects!

Ok, believe it or not, we just learned enough to go back to our projects that we've been working on and make something cool with the help of transitions and transforms. We're going to make an interesting way to show captions for your images. It's going to look something like this: http://codepen.io/mikefowler/pen/vKowl

@todo

## Advanced lesson notes!

Working ahead? Bored? Done this before? No problem. Here are some more advanced topics related to the lesson that you can explore or read more about.

### Timing functions

Remember that `transition-timing-function` property we've been using? Curious about what it's for?

@todo

### Stacking contexts

In the [Transforms sections](#transforms) did you notice how we defined `transform` twice, once to set the scale to 1 and again to set it to 1.5 when we hover? Try removing that first one and then hover on your square again. Notice how the box flickers a little before it starts animating? This is because CSS Transforms create a new [stacking context](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Understanding_z_index/The_stacking_context). The flicker is caused by our box moving onto a new stacking context when we hover on it. By setting the transform in both places, we tell the browser to make sure the box is *already* on its own stacking context. That way, when we hover on it, it doesn't need to switch contexts, and it doesn't flicker.
