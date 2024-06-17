---
layout: ../../../layouts/MarkdownPostLayout.astro

title: 'OOCSS - Object Oriented CSS'
pubDate: 2023-05-26
upDate: 2023-05-26
description: 'Nicole Sullivan borrowed the concept of object-oriented design to provide structure to CSS. Read about its history and why it is a timeless principle for the community and developers.'
image:
    url: 'https://docs.astro.build/assets/arc.webp'
    alt: 'The Astro logo on a dark background with a pink glow.'
tags: ["CSS", "front-end"]
---

<figure>

It's 2023 and we have a lot of methods and techniques that make CSS writing better and easier. However, there is one method that was one of the first to tackle object-oriented CSS writing and lay a solid foundation for other frameworks that followed.

This method is called [Object Oriented CSS](http://oocss.org/) (OOCSS) and, in this article, I will describe the basic principles and ideas of this methodology.

## Introduction

In 2008, Nicole Sullivan borrowed the concept of object-oriented design to provide structure to CSS. She presented her Object Oriented CSS (OOCSS) concept at [Web Directions North](https://www.slideshare.net/stubbornella/object-oriented-css) to the world.

The main idea behind [OOCSS](https://github.com/stubbornella/oocss/wiki/) is to treat page elements as objects, assign classes to these objects, treat these classes as single entities in style sheets, and reuse them when necessary.

> Object Oriented CSS is a methodology or framework (whichever you prefer) for organizing and extending your CSS in a way that is lightweight, highly performant, and easily used by developers at all skill levels.

## Basic principles

The idea of OOCSS is timeless. <a href="http://www.stubbornella.org/content/">Nicole Sullivan</a> started with the approach we use today when we create design systems. Take a look at <a href="https://www.slideshare.net/stubbornella/our-best-practices-are-killing-us">Nicole's presentation</a> where she analyzes the websites of large companies such as Facebook and Salesforce and points out stylistic inconsistencies in their interfaces.

This approach might have also inspired web designer <a href="https://bradfrost.com/">Brad Frost</a> when he introduced the <a href="https://bradfrost.com/blog/post/interface-inventory/">interface inventory</a> method, which is based on similar principles but in a wider context and without reference to technology.

<figure>
  <img src="interface-inventory.webp" alt="" width="750">
  <figcaption>PNC bank has many button styles as Brad Frost described in his article “<a href="https://bradfrost.com/blog/post/interface-inventory/" tabindex="-1">Interface inventory</a>.”</figcaption>
</figure>
The issue of inconsistent interfaces continues to be addressed today and will probably never be completely solved because there will still be new challenges and problems.
Although we already know how important it is to monitor consistency of the interfaces, we are still figuring out how to do it properly. This is also the reason why we build <a href="../basic-structure-of-design-systems">design systems</a>.
<figure>
  <img src="lego.webp" alt="" width="750">
  <figcaption>We often associate this mental model with LEGO bricks.</figcaption>
</figure>
However, this is an issue we need to solve if we want to improve the quality of our interfaces, save development costs, and speed up the entire design process.
Nicole Sullivan had the same goal and her work took CSS writing a step further. Let's take a look at the principles of her framework.
This methodology defines a CSS object as a visual pattern that can be used throughout the site. It serves as a guideline when designing reusable code that is scalable, sustainable and easy to use. There are two main principles of OOCSS:
<ol>
<li>Separation of structure and skin</li>
<li>Separation of container and content</li>
</ol>
<h2 id="separation-of-structure-and-skin">Separation of structure and skin</h2>
<em>Structure</em> is the basic core element which is <em>invisible</em>. These are the recurring elements that make up various page layouts and are not expected to change significantly over time. This includes properties such as <code>width</code>, <code>height</code>, <code>padding</code>, <code>margin</code>, <code>overflow</code>, etc.
<figure>
  <img src="structure.webp" alt="" width="750">
  <figcaption>Picture from presentation “<a href="https://www.slideshare.net/stubbornella/what-is-object-oriented-css" tabindex="-1">What is Object Oriented CSS?.</a>”</figcaption>
</figure>
<em>Skin</em> is a decorative part and it's about everything related to the brand of the site. It is bits and pieces that make your website different from the competition. You can think about properties like colors, borders, typography, shadows, gradients etc.
Skin, on the other hand, is the decorative part and it's about everything related to the website’s brand. These are the little things that set your website apart from the competition. This includes properties like <code>color</code>, <code>border</code>, <code>font-size</code>, <code>box-shadow</code>, <code>background</code>, etc.
<figure>
  <img src="skin.webp" alt="" width="750">
  <figcaption>Picture from presentation “<a href="https://www.slideshare.net/stubbornella/what-is-object-oriented-css" tabindex="-1">What is Object Oriented CSS?.</a>”</figcaption>
</figure>
Take a look at the following CSS and focus on repeating styles.
<pre class="language-css" tabindex="-1">
<code class="language-css">
.button-primary {
  /* Repeating styles */
  display: inline-block;
  padding: 16px 32px;
  margin-bottom: 0;
  font-size: 18px;
  line-height: 32px;
  text-align: center;
  cursor: pointer;
  /* Decorative part */
  color: white;
  background: black;
  border: 0;
}
.button-secondary {
  /* Repeating styles */
  display: inline-block;
  padding: 16px 32px;
  margin-bottom: 0;
  font-size: 18px;
  line-height: 32px;
  text-align: center;
  cursor: pointer;
  /* Decorative part */
  color: black;
  background: white;
  border: 1px solid black;
}
</code>
</pre>
We can use the following HTML for this stylesheet.
<pre class="language-markup" tabindex="-1">
<code class="language-markup">
<script type="prism-html-markup">
<button class="button-primary">Button</button>
<button class="button-secondary">Button</button>
</script>
</code>
</pre>
In this example, we are styling two buttons. If you look at the code carefully, you will notice a significant amount of repetition. This can clutter your stylesheet over time and lead to potential inconsistencies.
Based on the concept of OOCSS, you can abstract the above CSS into structures and skins.
<div class="code-example">
<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="GRYQYPe" data-user="ondrejko">
  <span>See the Pen <a href="https://codepen.io/ondrejko/pen/GRYQYPe">
  OOCSS - Without using the object oriented approach </a> by Ondřej Konečný (<a href="https://codepen.io/ondrejko">@ondrejko</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>

<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>
By separating them, we can reuse the classes and change their appearance by using another class for skin. Here is the refactored CSS according to the OOCSS principle.
<pre class="language-css" tabindex="-1">
<code class="language-css">
/* Repeating styles for button */
.button {
  display: inline-block;
  padding: 16px 32px;
  margin-bottom: 0;
  font-size: 18px;
  line-height: 32px;
  text-align: center;
  cursor: pointer;
}
/* Decorative parts - visual variants */
.button-primary {
  color: white;
  background: black;
  border: 0;
}
.button-secondary {
  color: black;
  background: white;
  border: 1px solid black;
}
</code>
</pre>
Then we can use the following HTML (notice how classes are used to change the appearance).
<pre class="language-markup" tabindex="-1">
<code class="language-markup">
<script type="prism-html-markup">
<button class="button button-primary">Button</button>
<button class="button button-secondary">Button</button>
</script>
</code>
</pre>
This way we can save code, use modularity and easily create other variants. If we change our mind that we want to increase the font size of the button, you can do it in one place and change all buttons at once.
This way, we can save code, use modularity, and easily create other variants. If we decide to increase the <code>font-size</code> of the <code>button</code>, we can do it in one place and change all the buttons at once.
<div class="code-example">
<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="GRYQYba" data-user="ondrejko">
  <span>See the Pen <a href="https://codepen.io/ondrejko/pen/GRYQYba">
  OOCSS - Separate structure and skin</a> by Ondřej Konečný (<a href="https://codepen.io/ondrejko">@ondrejko</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>

<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>
<h2 id="separation-of-container-and-content">Separation of container and content</h2>
We should avoid writing styles that are location-dependent. The main motivation is that objects should look the same regardless of their location.
Content refers to objects such as media, images, paragraphs, which are nested inside other elements that serve as <em>containers</em>.
Styles used for <em>content</em> objects (elements) should be independent of the container class, allowing them to be used independently of their parent objects (elements). Take a look at the following example.
<pre class="language-css" tabindex="-1">
<code class="language-css">
.widget {
  /* foo */
}
.widget .list {
  /* foo */
}
.widget .list .title {
  /* foo */
}
.widget .list .content {
  /* foo */
}
</code>
</pre>
Now, let's separate the content from the container.
<pre class="language-css" tabindex="-1">
<code class="language-css">
.widget {
  /* foo */
}
.list {
  /* foo */
}
.list-title {
  /* foo */
}
.list-content {
  /* foo */
}
</code>
</pre>
Now these classes can be used in many situations without the restriction of having a parent with the class  <code>.widget</code> or  <code>.list</code>.
Learning how to use this principle may take some time, but the reward is the ability to write better code.
<h2 id="takeaway">Takeaway</h2>
This method helps us think about styles in a more modular and object-oriented way. It also sets our mindset to write less repetitive code and helps us understand that extending selectors rarely leads to writing better code.
By trying to use or understand this methodology, you will gain a basic understanding of the issues related to the <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity">specificity</a> and selectors structure, and you will understand how fragile CSS is.
I recommend <a href="https://www.slideshare.net/stubbornella/presentations">checking out more</a> of Nicole Sullivan's presentation resources.
