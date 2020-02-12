---
title: 'puts, prints and more — printing to the console in Ruby…'
date: '2019-03-13T16:39:12.538Z'
excerpt: Why do we need these methods in the first place?
thumb_img_path: >-
  images/puts--prints-and-more---printing-to-the-console-in-Ruby/1*5JxVDF_N-tmfNVcrhjZbUg.png
layout: post
---
![](/images/puts--prints-and-more---printing-to-the-console-in-Ruby/1*5JxVDF_N-tmfNVcrhjZbUg.png)

<figcaption>thanks to vinoth from stack overflow&nbsp;:)</figcaption>

Why do we need these methods in the first place?

When you run a program, Ruby will read the lines but not print anything out. If you want to display something to the person using your program (like an instruction or a request for input), or for some help with debugging your code, you’ll need to use one of these in order to tell Ruby to output that something to the console:

* * *

### puts

Most of us, I think (me anyway) default to using *puts* also because it’s the first way of logging that comes to mind, but also because it shows our result in a nicely formatted way. There’s a reason for that: *puts* is shorthand for *put.to\_s*…looks familiar, right?

When you use *puts*, Ruby calls *.to\_s* on an object, converting it to a string then displaying on the screen. A neat thing about *puts* is that it adds a new line at the end of each statement so you can read it more easily.

The return value of *puts* is always nil.

![](/images/puts--prints-and-more---printing-to-the-console-in-Ruby/1*MM42jzGPU208JBspUqLOiw.png)

<figcaption>using puts to output multiple&nbsp;objects</figcaption>

I particularly like *puts* for debugging, I’m a fan of *puts*\-ing random words all over the place so I can see where my program is running up until(or not), which helps me find the bit where the code is broken.

If you do this just remember to take them all out of your finished product 😏

* * *

### print

*print* also calls *to\_s* on the object but unlike *puts* it DOESN’T add that handy line break, so if you *print* a lot of things you will see them all mashed together in the console like this:

![](/images/puts--prints-and-more---printing-to-the-console-in-Ruby/1*hTa2fOQ_wxsFSj9HZC7NgA.png)

<figcaption>using print on multiple&nbsp;objects</figcaption>

The return value of prints is also nil.

Using *puts* and *print* on the same object is a good way to illustrate the difference:

![](/images/puts--prints-and-more---printing-to-the-console-in-Ruby/1*ryKPngx9RxZ4S3u9cDzZhg.png)

<figcaption>using puts and print to display the same complex&nbsp;object</figcaption>

Notice how *puts* didn’t display the nil value?

* * *

### p

Yes, just the letter p, all by itself.

![](/images/puts--prints-and-more---printing-to-the-console-in-Ruby/0*6WK-qhFAgntk9IWl.jpg)

<figcaption>COPYRIGHT scopefeatures.com</figcaption>

Where *puts* calls *.to\_s* on the object, *p* calls *.inspect* (link to docs in references)*.* In the true Ruby tradition of making life easier, *p* is much nicer than writing *puts some\_object.inspect*

![](/images/puts--prints-and-more---printing-to-the-console-in-Ruby/1*6CW9RwBg7BeCRrEC22ek2g.png)

<figcaption>p is the same as puts object.inspect</figcaption>

The return value of *p* is the object you passed to it.

*p* is pretty good for debugging because you still get a sense of which class each object belongs to, since its not converting anything into a string:

![](/images/puts--prints-and-more---printing-to-the-console-in-Ruby/1*KCBE7OcShBcByqM0mnuMxg.png)

<figcaption>The return value of <em>p</em> is the object you passed to&nbsp;it.</figcaption>

One way *p* *is* similar to puts is that it adds a line break after each object.

![](/images/puts--prints-and-more---printing-to-the-console-in-Ruby/1*-OBemPqOGQ9On9W-yM2BjA.png)

<figcaption>using p to output multiple&nbsp;objects</figcaption>

* * *

### **\*\*\*BONUS\*\*\***

#### To finish, here’s *pp!*

*pp* stands for *pretty print*. It’s a rather less well-known method that you’ve possibly never heard of (I hadn’t). What it does, is call the *pretty\_inspect* method on the object, arranging its contents on separate lines to make it easier to read (and debug).

![](/images/puts--prints-and-more---printing-to-the-console-in-Ruby/1*5MIogHJePwpNIyXlSvwXzg.png)

<figcaption>using pp to output multiple&nbsp;objects</figcaption>

Where it really comes into it’s own is by taking a complex nested object like this:

![](/images/puts--prints-and-more---printing-to-the-console-in-Ruby/1*kHwsftg_fakFVgCCTdsJ0g.png)

<figcaption>Complex object example from <a href="https://github.com/awesome-print/awesome_print" data-href="https://github.com/awesome-print/awesome_print" class="markup--anchor markup--figure-anchor" rel="nofollow noopener" target="_blank">https://github.com/awesome-print/awesome_print</a></figcaption>

…and displaying it in a format that’s much easier to read, like this:

![](/images/puts--prints-and-more---printing-to-the-console-in-Ruby/1*X6TlT35vE7S1MVvTy78aGQ.png)

<figcaption>Same object, pretty-printed</figcaption>

All of these methods are part of the Kernel module (which is included by the Object class). As of Ruby 2.5 *pp* is automatically required, for earlier versions you’ll have to require manually whenever you want to use it. Same applies whether you want to add it to a file or just use it in irb.

* * *

### \*\*\*BONUS-BONUS!\*\*\*

#### Awesome\_print…

Yes, someone took *pp* to the next level and came up with the ultimate console logging method for Ruby. If you use it on the complex string from the previous example, you get this:

![](/images/puts--prints-and-more---printing-to-the-console-in-Ruby/1*g_6YdVobgLnsZFHjc0nqjA.png)

<figcaption>how awesome_print displays a complex&nbsp;object</figcaption>

Awesome\_print is a Ruby library (you can install it with `gem install awesome_print` ) created by Michael Dvorkin. You need to enter ‘*require* *ap’* in an irb session, then you can use it in place of *p*.

As you can see it uses colour coding to discern between data types, shows the indexes of array elements and even which classes embedded objects inherit from. Most of the features can be customised, and you can even make it your default formatter for irb, Rails console and pry.

#### References:

[**Class: Object (Ruby 2.6.1)**  
*Class : Object - Ruby 2.6.1*ruby-doc.org](https://ruby-doc.org/core-2.6.1/Object.html#method-i-inspect "https://ruby-doc.org/core-2.6.1/Object.html#method-i-inspect")[](https://ruby-doc.org/core-2.6.1/Object.html#method-i-inspect)

[**awesome-print/awesome\_print**  
*Pretty print your Ruby objects with style -- in full color and with proper indentation - awesome-print/awesome\_print*github.com](https://github.com/awesome-print/awesome_print "https://github.com/awesome-print/awesome_print")[](https://github.com/awesome-print/awesome_print)

[**Michael Dvorkin**  
*Github \* Twitter \* LinkedIn \* Copyright © 2000-2017 Michael Dvorkin*www.dvorkin.net](http://www.dvorkin.net/ "http://www.dvorkin.net/")[](http://www.dvorkin.net/)
