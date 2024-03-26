---
layout: ../../../layouts/MarkdownPostLayout.astro

title: 'The evolution of effective CSS writing'
pubDate: 2022-07-01
description: 'This is the first post of my blog.'
author: 'Ondřej Konečný'
image:
    url: 'https://docs.astro.build/assets/full-logo-light.png'
    alt: 'The full Astro logo.'
tags: ["post"]
---

How do you work effectively with CSS so that you feel comfortable with every modification? In this article, you will find a very brief overview of the development of CSS writing and description of the most common problems.

## A little history
In 1994, Håkon Wium Lie realized that there was a need to create a language that would create ways to visually edit documents on the web. The main idea was based on the need to separate the content from the presentation. Lie, together with other designers, created the first version of CSS, which over time was implemented by all browsers. After HTML, CSS became the second standardized language for W3.

This [archived e-mail communication](http://1997.webhistory.org/www.lists/www-talk.1994q1/0648.html) shows the origins of the idea of visual editing of HTML documents. As you can see, after pasting the same HTML, the content was displayed differently on two different browsers (Netscape and Mosaic). The developers of the Mosaic browser decided to add an indent from above before the list (now known as an unordered list). They just thought it would look better. Everyone then perceived it as a bug and this resulted in the need to have control over how their content appeared on the web.

In the mid-1990s, when the first websites began to appear, differentiating from the default browser display settings was a real challenge. At a time when cascading styles were still being tested, it was only possible to modify the design using HTML attributes. However, the first web browsers like ViolaWWW did not allow you to adjust the visual appearance almost at all.

## What came before CSS
In the 1990s, website designers began to make the first attempts at what we now call web design. A common example of a 90's site is the Space Jam site. The site of the famous WarnerBros animated film is still online in its original state after 24 years; it is still possible to go through and explore it.

It is interesting to see on this website how color and text differentiation was approached in this era and how the layout was organized. All colors are defined in the body of the page, where the creators set the basic rules for the display using HTML attributes. Specifically, the attributes bgcolor, text, link, vlink and alink. The attributes defined in this way then made it possible to display the colors of texts, links, and backgrounds differently.

Another nice example on this site is the layout. At the time, it was modified only with the help of one or more embedded tables. This technique was then used for several more years to create all web document layouts.

First for the circular layout at the time (example of the Space Jam website) and then for the Holy Grail Layout, which has been a trend in web design for many years. This spreadsheet technique is still recommended today for creating newsletters and PDFs generated using HTML, because many e-mail clients simply did not choose to change their systems.

This example shows how designers came to the result of this circular layout, which was popular at the time. Companies wanted to differentiate themselves from the competition, and so the first attempts were made to change the default visual settings.

Placing images in a circular layout was then achieved again using the attributes of tables (specifically align and valign) and also using the HTML tags br. This was the basis of web design for several years.

## The arrival of CSS
The advent of cascading styles was revolutionary at the time. In 1998, Eric Meyer and his team began to describe how it is possible to implement and use cascading styles. Over time, CSS made its way to the first website and soon became the standard for website design.

In the beginning, it was a great revolution. There was no need to rewrite the attribute values on all pages to change the title color; one small change in cascading styles was enough. This was a great time-saving breakthrough for developers everywhere. 

Developers started using CSS more frequently, but few had addressed the need to organize and maintain styles in any way. Writing CSS without any organization or idea for sustainability was no longer enough.

There were no ways to maintain cascading styles and manage the often inconsistent design of large sites (which in some cases continues to this day). Thus, complications began to arise.

## Problems with properties of CSS
What complications can arise when writing CSS? Writing CSS can be a tough nut to crack, especially for beginners. On the one hand, cascading styles are very easy to understand due to their straightforwardness, but on the other hand, they are quite complicated to maintain, modify and structure. Many problems can occur. I will try to briefly describe some of them.

### High specificity
Everyone who has ever worked with CSS has certainly encountered this problem. The developer receives input from the graphic designer, considers which HTML element could be used, and starts writing the selector. Developer decides to use an unordered list from which he wants to create a list with blue link colors and a font size of 20px. He will use simple selector.

Then he inserts HTML into the codebase - deep into the structure of the web, where it belongs and where it should be displayed.

Then he writes the following CSS:

This is not the result he wanted. The links are red, the font is 16px and bold. He looks at DevTools and finds that the selector is already overridden by another selector that prevents the correct result from being plotted:

What option does the developer have now? All that remains is to increase the specificity of the newly-created selector, modify the overridden selector or use !important. Of course, there are more possibilities, but in principle it is still a struggle with specificity.

Very few people make adjustments to an already-finished selector, and we know why not to do so. There is no choice but to increase the specificity by adding a .list class to our unordered list.

This creates a new selector in a fixed location that can no longer be used. If you need to use it elsewhere, you have to add another piece of code.

### Nesting hell
Most developers rarely realize that CSS can be used to design web documents and applications. With the advent of the popularity of preprocessors, the writing of cascading styles has become a bit closer to a programming language (thanks to the possibility of using variables, cycles, or mixins, for example). Preprocessors also came with one novelty, and that was the immersion of selectors into each other.

The deciphering of such code and its subsequent modifications was thus in some cases almost impossible. The following code looks threatening, but it's nothing special, and we often come across something like this when refactoring CSS.

What will the resulting compiled selector look like? I did not dare to publish the result of this selector, but from the following picture you can get an idea of what such outputs look like.

Such immersion of selectors do not allow such code to appear in the preprocessor file or in the resulting CSS and should be avoided.

It is good practice to use selector plunges up to the second level. In some situations, they can be used up to the third level. Then the code will be easy to read and won’t cause endless headaches.

Such code is then easily readable. The developer can immediately understand what is happening, how he can further expand the record, and how he can work with it.

### Cascade
The order matters. Another typical mistake when writing CSS is to ignore the fact that we have to pay attention to the order in which we write selectors. This feature of CSS discourages many developers from engaging in and developing styles because they simply do not understand and cannot deal with these features.

When we talk about cascade, we mean a combination of the following rules: order of rules, specificity of selectors and importance of rules.

If you look closely at the previous example, you will see that:
- If the selectors of two declarations have the same weight (specificity), then the browser will use the one that is later in the code.
- CSS order matters
- On the other hand, the order in which the classes are listed in HTML does not matter at all.
- Wrongly chosen order of files in the project can cause great complications
- !important overrides all selectors

If you add some messy organisation for CSS files, then you get a spaghetti code which would lead to a lot of troubles, errors, code duplication as new developers enters the ring over time.

This extreme dependency between the HTML structure makes the code be especially fragile: even if it’s clean, a simple mistake of a non-expert can ruined it completely.

## Methodologies and architectures
To address the inherent complexity of CSS, various types of best practices and techniques have been introduced to help you create meaningful, sustainable, and extensible code for the design of your websites and applications.

For most web design needs, there is more than one way to approach a problem. There are four methods that stand out among others when considering how to structure code and name classes.