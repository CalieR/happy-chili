---
title: The CSS box model
date: '2019-04-24T14:03:34.505Z'
subtitle: V Important.
excerpt: V. Important!!
thumb_img_path: images/The-CSS-box-model/1*WAKPFpLlZbWoZb59-TunRQ.jpeg
layout: post
---
![](/images/The-CSS-box-model/1*WAKPFpLlZbWoZb59-TunRQ.jpeg)

For most of us CSS is tricky at best, infuriatingly frustrating for the rest of the time. A huge breakthrough for me when I first started learning to code was this single revelation:

> Everything sits in a box

That’s every heading, every paragraph, and every other element they are nested within.

Understanding the CSS box model is crucial — it underpins everything else that you learn about constructing the layout of a page. If you know what’s going on with each box and how it naturally behaves, you begin to understand what can be done with it, how to pick the most appropriate element for each task and hopefully spend less time randomly adding and removing varying amounts of margin in the hope you’ll get the outcome you want.

![](/images/The-CSS-box-model/1*BPVcLFwBPeCoNhjdkk141Q.gif)

<figcaption>For the sake of your blinds, learn the box&nbsp;model…</figcaption>

* * *

![](/images/The-CSS-box-model/1*7g499pgB1FNiPZ-tFX7Vsw.png)

<figcaption>the box model is in the bottom right-hand corner&nbsp;^^^</figcaption>

#### **Firstly, go find the box model:**

Open your browser and navigate to any webpage. Now open the Devtools by your preferred method, click on Elements, then click on any element in the HTML and in the right hand pane you’ll be able to see the box model for that element.

Here it is in more detail:

![](/images/The-CSS-box-model/1*ghmnqQBm9ewfrwezMMhDRQ.png)

<figcaption>close-up of the box&nbsp;model</figcaption>

The four parts of the box model are margin, border, padding and content (the blue box in the centre). The position box only appears when the position of an element is set to anything other that its default, which is static.

#### Content (the blue box)

As the name suggests, this is where all the content sits — this includes text, and any elements like images that are nested within it. The simplest way of controlling the absolute sizing of this box is with the CSS *width* and *height* properties. Use settings like *min-width* and *max-width* (and the same for height) if you want to be a little less rigid.

#### Padding (the green box)

Padding is the space immediately outside of the content area, but before the border — it may help to think of it like an inner margin, since it sits within the border. Padding is set with the CSS property *padding*, followed by *\-top/-bottom/-left/-right*, then the amount you want to add, eg:

***padding-top: 1rem;***

If you don’t specify a side, the same amount of padding will be added on each side of the content in that element. Padding is especially useful for adding a bit of breathing room to text, for instance on a button, because it has the effect of pushing the border away from it.

#### Border (the yellowy box)

The border separates the margin and the padding areas (or the inner and outer margins if you wish). To alter the border there are 3 properties you can change — *width(*thickness*), style* and *colour*. As with the padding properties they can be set for one side specifically, or for all sides at once. For quickness it is possible to set all 3 properties for all 4 sides in one line:

***border: 5px solid black;***

There are lots of cool styles you can set like dotted, dashed, inset, etc. You can also set a bit of border radius to give boxes a nice rounded edge.

**Top-tip:** to make it easier to see whats actually happening to the elements you are trying to position on a page, add a small border in varying colours and styles to each one. It removes some of the guesswork. Just set the thickness back to 0px when you’re done.

#### Margin (the orangey-beigey box)

The margin surrounds the box that the element is sitting in. Because it is on the outside of the border, it is the margin that pushes up against the nearest elements in the layout. Margin is declared in the same way as padding, either one side individually or all sides at once.

* * *

On the MDN website there’s a cool playground where you can try all these settings out:

[**The box model**  
*The CSS box model is the foundation of layout on the Web - each element is represented as a rectangular box, with the…*developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model#Active_learning_playing_with_boxes "https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model#Active_learning_playing_with_boxes")[](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model#Active_learning_playing_with_boxes)

* * *

#### Elements have default values

Something you should bear in mind when choosing an element is that many of them come with default amounts of margin or padding. You maybe never gave any thought thought to why or how an unordered list appears inset from the surrounding text…? It’s because <ul> elements have a default padding-left value of 40px.

If you don’t want certain characteristics by default you’ll need to set them to 0 manually. All the default values are listed here:

[**CSS Default Browser Values for HTML Elements**  
*Well organized and easy to understand Web building tutorials with lots of examples of how to use HTML, CSS, JavaScript…*www.w3schools.com](https://www.w3schools.com/cssref/css_default_values.asp "https://www.w3schools.com/cssref/css_default_values.asp")[](https://www.w3schools.com/cssref/css_default_values.asp)

* * *

#### Total dimensions of a box

The total width of a box is the sum of the width of its content, plus any padding (left and right), plus any border (left and right); height works the same way but with top and bottom instead of left and right. By default, any width and height you specify on an element is applied only to the content (the blue box), as we saw above. This means that if you want to think about the dimensions of a box as a whole you’d need to do that sum every time. If you want to increase the width or height you’d then need to decrease the border and/or padding accordingly to keep the overall box dimensions the same.

![](/images/The-CSS-box-model/1*mpf3XwCJJbIfqCfIRdxDmA.png)

<figcaption>box-sizing: border-box;</figcaption>

But what if you wanted it so that you could specify the width of the *entire* box (including the border and padding) in one dimension? Thankfully, there is a property called *box-sizing* to help with this. Use ***box-sizing: content-width;***  to continue as just described, or choose ***box-sizing: border-box;*** to tell the browser that the width and height values are now inclusive of border and padding— now if you change the width of an element, the border and padding amounts will be automatically adjusted…no more maths for you!

Go here for a good demonstration: [https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing)
