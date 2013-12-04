# Lesson 4 - Even more CSS!

**Transitions and transforms!**

## Overview

We've spent the last couple of weeks learning both basic and more advanced CSS, and this week we're going to make our pages *move*. What do I mean by *move*? I mean that we're going to learn about how to add *movement* to our websites using CSS “transitions” and “transforms”! We're going to start out by playing around with how transitions and transforms work on their own, and then we're going to take what we've learned and write some transitions and transforms of our own for the pages we've been working on over the past three lessons.

## Diving in

We're going to get back to your projects in a bit, but for now we're just going to get our hands dirty. I want everybody to go to CodePen and [create a new pen](http://codepen.io/pen/). Uncheck the checkbox in the JS panel to give ourselves some more room to work:

![](http://f.cl.ly/items/2n1z1d2c1m3p0Y121j2l/Screen-Shot-2013-12-02-at-7.52.32-PM.jpg)

and then click on the gear next to the CSS section, and make sure that the checkbox labeled "Prefix free" is checked.

![](http://f.cl.ly/items/3s3C2r281s193P1V2g0z/Screen-Shot-2013-12-02-at-8.00.30-PM.jpg)

## Basic transitions

To get a better idea of how transitions work, we're going to create a simple example. In our HTML, we're going to create a single element, a `<div>` with a class of `box`.

```html
<div class="box"></div>
```

To our CSS we'll add some simple styles to center the box, set its width and height, and make the background silver. Go ahead and just copy and paste this into your CSS area:

```css
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

```css
.box {
  /* ... */
  transition-property: background;
  transition-duration: 1s;
  transition-timing-function: ease;
}
```

We've added three new properties, all starting with “transition-”. These three properties tell the browser the three things it needs to know about what you want to transition, or animate: the *properties* you want to transition, *how many seconds*, or *how long*, it should take to transition from one value to the next, and the *timing* of the transition.

*Try hovering on your box again.* **Tada!** With our new CSS, we're now *transitioning* from one background color to the next. Now try changing the `transition-duration` value to something longer, like “5s”. When you hover on your box again, it will take much longer (5 seconds, to be exact) to transition from your first color, “silver”, to your second color. After you've experimented, let's go ahead and set the duration to “0.5s”, or a half of a second, to make it quick to see our transitions when we make changes.

## Basic transforms

Let's make our box do something else when we hover on it. Let's say that when we hover on the box we want it to get *bigger*. One way to do this would be to change the height and width of the element when we hover on it. However, changing the height and the width will affect the position of elements *around* our box, and we might not want that. Instead we're going to use something called **CSS Transforms**, a part of CSS that allows us to change the size, position and rotation of objects *without* affecting things around it, or what we would say is the “flow” of our document. To start, let's add a few lines of CSS to what we have.

```css
body {
  perspective: 1000;
}
.box {
  /* ... */
  transform: scale(1);
  backface-visibility: hidden;
}
.box:hover {
  /* ... */
  transform: scale(1.5);
}
```

Once again, hover over your box. AH! What's happening? The square is getting bigger when we hover, but it's *jumping* to the new property value, just like our background color was earlier. *Who thinks they know how to have the scale be transitioned as well?*

After appending `transform` to the value of `transition-property`, we get something that looks like this:

```css
transform-property: background, transform;
}
```

This line now tells the browser that for our class `.box` we want to transition *both* the background and transform properties. Hover over that box again and see that we've successfully instructed the browser to smoothly transition the scale of the box as well.

So now the question is: **what else can we do with transforms**? Well, for one, we can chain transforms together by adding to the value of our `transform` property. Try changing the `transform` property for when we hover on the box to include rotation:

```css
.box:hover {
  /* ... */
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

```css
.box:hover {
  /* ... */
  transform: rotateY(30deg) rotateX(10deg) scale(1.5);
}
```

This transform would make our box rotate a little bit to the right (`rotateY(3deg)`), rotate a little bit away from us (`rotateX(10deg)`) and grow to be 1.5 times its original size (`scale(1.5)`).

Here's my box for you to check out: http://codepen.io/mikefowler/pen/DyIHE

## Back to our projects!

Ok, believe it or not, we just learned enough to go back to our projects that we've been working on and make something cool with the help of transitions and transforms. We're going to make an interesting way to show captions for your images. It's going to look something like this: http://codepen.io/mikefowler/pen/vKowl

We're going to call this a “card”, because it's a little bit like a playing card that you put face down on the table, and then you pick it up and turn it over to see the other side. Let's start by adding some HTML to our page, way down at the very bottom.

```html
<div class="card-container">
  <div class="card">
    <div class="card-image"></div>
    <div class="card-caption"></div>
  </div>
</div>
```

Of course, we're not going to see anything here at first, because there's no content! We just have a bunch of empty containers. *Let's change that.* The first thing we want to do is give our “card” some dimensions, and give it a background so we can see what's going on.

```css
.card-container {
  background: salmon;
  width: 400px;
  height: 200px;
}
```

Now we can see our card on the screen, with the background color we gave it. It's 400 pixels wide, and 200 pixels tall.

![](http://f.cl.ly/items/3w3d3p2H3r0m3D2K2k1U/Screen%20Shot%202013-12-03%20at%2011.53.28%20PM.png)

The first thing we'll do is get our image displaying. Up until now, we've been putting our images into our HTML as `<img>` tags. We can also add images via CSS by setting the background of an element to be an image. Let's use the same image we started with three lessons ago, of Hoyt's dogs at the park. We're going to add a selector in our CSS for the `card-image` class we wrote earlier. The `background-size` property will make sure that we can see our entire image.

```css
.card-image {
  background: url(http://f.cl.ly/items/2f473l1d233S0S1k3J3d/dogs-playing.jpg);
  background-size: cover;
}
```

Hmm, but we don't actually see anything, even after putting in our background image. Well... that's because the `<div>` that our background image is on doesn't actually have any content in it, so its height is still 0. What we really want is for the image to take up the entire width and height of our card. In fact, we want the caption to take up the whole height and width as well. To do that, we're going to use something we learned last session: absolute positioning. We're going to put the caption and the image directly on top of each other.

## Making our card flip

Imagine that the two sides of a playing card are actually two separate pieces of paper. In order to “build” the card we would want to put lay them flat on top of each other, and then flip the one on bottom around so it faces the other direction. We're going to do the same thing with our containers. First let's position them on top of one another and make them be the full width and height of our card.

```css
.card {
  position: relative;
  width: 100%;
  height: 100%;
}
.card-image,
.card-caption {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
```

We'll also add a caption to our HTML:

```html
<div class="card-caption">Today we played at the dog park.</div>
```

Now we can see both our caption *and* our image on the page:

![](http://f.cl.ly/items/0T1s0I1y3f2z3u0b0L3V/Screen%20Shot%202013-12-04%20at%2012.31.36%20AM.png)

Now it's time to use what we learned earlier with transitions and transforms! Remember what I said before about having two sides of a card, and needing to flip one around to face the other direction? *Can anybody think of something we learned earlier with our boxes that would allow us to **rotate** our caption to face the other way?*

By using a rotate transform, we can rotate our caption a half turn away from us, 180 degrees, so it's facing the other direction, just like the other side of a playing card.

```css
.card-caption {
  transform: rotateY(180deg);
}
```

But wait, we can still see it, it's just *backwards*!

![](http://f.cl.ly/items/2A463e353A3y1y3e1v1I/Screen%20Shot%202013-12-04%20at%2012.52.25%20AM.png)

When we can the reverse side of an object like this, we call it a “backface”. For those of you here who play Minecraft, do you know how sometimes the ground on the map disappears and you can see through the world down to caves and dungeons? Well... when that happens, what you're actually seeing are the *backfaces* of those other parts of the world. In our case, we really *don't* want to see the backface of our caption, so let's hide it.

In our selector for `.card-image, .card-caption` we're going to specify that backfaces should be “hidden”:

```css
.card-image,
.card-caption {
  /* ... */
  backface-visibility: hidden;
}
```

So now we're back to just seeing the image. The caption is still there, it's just on the other side, out of view. If you don't believe me, I'll prove it. At this point, what if we spun the entire card around again. We would expect to see the caption again, right? Let's try it:

```css
.card {
  transform: rotateY(180deg);
  transform-style: preserve-3d;
}
```

There's our caption again, and we can even see our background color through it!

![](http://f.cl.ly/items/1k0u403J0F3H2z453O2K/Screen%20Shot%202013-12-04%20at%2012.54.56%20AM.png)

So what's left? Well, we only want to see our caption when we're hovering on the image, so let's move the `transform` that we just added to a `:hover` selector. We're going to say that when we hover on the entire card, on the `.card-container`, we'll rotate the `.card` by 180 degrees. Move the transform from above into a new selector like this:

```css
.card-container:hover .card {
  transform: rotateY(180deg);
}
```

And *now* when we hover on our card we should see the caption appear! But it happens all at once, just like the changing background color on our boxes way back at the beginning. So what's the last step? That's right… **transitions**!

In the `.card` selector, we'll specify the simplest transition we can by just telling the browser *how long* the transition should take:

```css
.card {
  /* ... */
  transition-duration: 0.5s;
}
```

## Finishing up

@todo: card caption styles
@todo: perspective

## Advanced lesson notes!

Working ahead? Bored? Done this before? No problem. Here are some more advanced topics related to the lesson that you can explore or read more about.

### Timing functions

Remember that `transition-timing-function` property we've been using? Curious about what it's for?

@todo

### Stacking contexts

In the [Transforms sections](#transforms) did you notice how we defined `transform` twice, once to set the scale to 1 and again to set it to 1.5 when we hover? Try removing that first one and then hover on your square again. Notice how the box flickers a little before it starts animating? This is because CSS Transforms create a new [stacking context](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Understanding_z_index/The_stacking_context). The flicker is caused by our box moving onto a new stacking context when we hover on it. By setting the transform in both places, we tell the browser to make sure the box is *already* on its own stacking context. That way, when we hover on it, it doesn't need to switch contexts, and it doesn't flicker.
