---
title: The Persistence of Memory
date: '2019-04-10T13:51:08.765Z'
subtitle: "…a brief look at Windows\_dumps."
excerpt: A quick look into memory dumps.
thumb_img_path: images/The-Persistence-of-Memory/1*GuAhkT0e67ieN_9tmxAB1g.jpeg
layout: post
---
![](/images/The-Persistence-of-Memory/1*GuAhkT0e67ieN_9tmxAB1g.jpeg)

Whilst I was writing my first blog of bootcamp (which was about ways of printing to the console in Ruby) I came across the website of Michael Dvorkin, the man who came up with ‘awesome-print’. The homepage of his website is pretty striking….

![](/images/The-Persistence-of-Memory/1*BPF67FvQ5oUyL5mTF86W4w.png)

<figcaption>go to <a href="http://www.dvorkin.net/" data-href="http://www.dvorkin.net/" class="markup--anchor markup--figure-anchor" rel="noopener" target="_blank">http://www.dvorkin.net/</a> to see this in&nbsp;action…</figcaption>

A voice from over my shoulder said ‘cool, that looks like a memory dump…’, to which I said ‘what’s a memory dump?’, then I had my subject for blog three.

* * *

A memory dump happens when Windows operating system software crashes unexpectedly, an event commonly known as the ‘blue screen of death’. These ‘crash dump’ (aka ‘core dump’, aka ‘system dump’) files contain a copy of the computer’s memory at the time of the crash, so they can be used to identify what caused it in the first place.

### Types of dump files:

There are 4 different types of memory dump; each operating system has one type set by default but this can be changed (or even switched off) in user settings:

![](/images/The-Persistence-of-Memory/1*YbJDb-NaeLiWzvnqsHhqTA.png)

<figcaption>courtesy of howtogeek.com</figcaption>

#### Complete memory dump

As the name suggests, this is the largest type of dump, and therefore contains the most amount of information. The size of this file will be equal to the amount of memory in use by the computer at the time of the crash, eg a 16GB system using 8GB of memory when it crashed will produce a complete memory dump file of 8GB. For this reason, there needs to be plenty of space available to hold it…a ‘paging’ file (hidden system file on the hard disk) of adequate size, plus an additional 1MB.

When a subsequent system crash occurs, any previously stored file of this type is overwritten.

#### Kernel memory dump

The kernel is the central part of an operating system. It is the part that loads first, so it is usually stored in a protected part of memory in order to prevent it being accidentally overwritten. This type of memory dump records only the kernel memory, so the recording process is much quicker and the resulting file is much smaller in comparison to a complete memory dump, about one third in fact. Kernel memory usually takes up between 150MB and 2GB.

Because this file only includes records of memory that relates to the kernel and directly related programs, it is more useful in diagnosis because it holds information about the parts of memory that are most likely to have been involved in the reason for the crash.

Any subsequent crash will also overwrite this type of dump file unless a specific option is selected.

#### Small memory dump (64 KB)

As the name suggests, this is the smallest type of memory dump file. It requires a paging file of about 2MB and will not overwrite any previous files — subsequent files are given unique names and stored in a specific folder.

Small memory dump files don’t store a huge amount of detail, only information and context relating to the process that stopped at the time of the crash such as the stop message and a list of loaded drivers. Because it contains so little information, it is less useful in debugging that the kernel or complete types.

#### Automatic memory dump

Available from Window 8 onwards, this type of file contains the same information as a Kernel dump file. The difference is in the way the size of the paging file is set.

If paging file size is set to ‘System Managed’ and dump type is set to ‘Automatic’, Windows sets the size of the paging file to less than the size of RAM. Most of the time this will be large enough to record a Kernel dump file, but if it isn’t, Windows temporarily (for 4 weeks) increases the size of the file to match the size of RAM.

![](/images/The-Persistence-of-Memory/1*HiJCg-QL75z3lUM-tX37lA.png)

<figcaption>Setting the paging file&nbsp;size</figcaption>

Whichever type is enabled it is possible to use a command line utility called Dumpchk.exe, in order to check that the crash dump file was created correctly. Some basic information is provided, along with any error messages.

#### Minidumps

In addition to the above types, you will also get a minidump file (stored in the Minidump folder by default). These files show the exact driver files involved in a crash, and are pretty useful in identifying the problem that caused the crash. For this reason it isn’t recommended to turn off Minidump recordings.

#### Using the stored dump file…

So once you have the dump file, what should you do with it?

![](/images/The-Persistence-of-Memory/1*q8rnQTxbto4VZiIyvCycDw.gif)

<figcaption><a href="http://blog.frizk.net/2018/03/" data-href="http://blog.frizk.net/2018/03/" class="markup--anchor markup--figure-anchor" rel="noopener" target="_blank">http://blog.frizk.net/2018/03/</a> — PCILeech</figcaption>

Unless you are a Windows developer, or you fix pc’s for a living, the larger memory dump files aren’t really going to interest you much. The average Windows user is most likely to post one to Microsoft or Symantec for diagnostic purposes. An engineer who is developing drivers may want to intentionally crash a system, which is possible with a ‘crash on demand’ utility called Bang!, or with a built-in Windows shortcut (holding down the right CTRL key and pressing the SCROLL LOCK key two times).

Minidumps on the other hand are much more useful. They can be read with a program like Blue Screen View (Nirsoft). This summarises the crash information like time, date, basic crash information that was displayed on the blue screen, stop code, along with a pointer towards which driver or module may have caused the crash.

![](/images/The-Persistence-of-Memory/1*I8Fr_ge1ghSog90boteg-g.gif)

<figcaption>courtesy of Nirsoft.com</figcaption>

* * *

### References:

[**Blue screen of death (STOP error) information in dump files.**  
*Displays information about blue screen crashes occured on your system. (MiniDump Reader)*www.nirsoft.net](http://www.nirsoft.net/utils/blue_screen_view.html "http://www.nirsoft.net/utils/blue_screen_view.html")[](http://www.nirsoft.net/utils/blue_screen_view.html)

[**Downloads:BANG! -- Crash on Demand Utility**  
*OSR Open Systems Resources, Inc. The Windows device driver and file systems experts. Seminars - Development …*www.osronline.com](http://www.osronline.com/article.cfm%5earticle=153.htm "http://www.osronline.com/article.cfm%5earticle=153.htm")[](http://www.osronline.com/article.cfm%5earticle=153.htm)
