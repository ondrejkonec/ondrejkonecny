---
layout: ../../../layouts/MarkdownPostLayout.astro

title: 'How the CSS box model works'
pubDate: 2020-11-10
upDate: 2020-11-10
description: 'CSS Box Model is a fundamental concept that every developer dealing with web interface should be familiar with. In this article, I explain how the CSS Box Model works and what its pitfalls are.'
tags: ["CSS", "front-end"]
---

When laying out a document, the browser's rendering engine represents each element as a rectangular box according to the standard CSS Box Model. How does it work?

## CSS Box Model
The basis of content distribution on the web is rooted in the box model. These rectangular boxes are generated for all web page's content elements in the [Document Object Model (DOM)](https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model/Using_the_Document_Object_Model#what_is_a_dom_tree) tree.

<figure>

  ![Box model visual representation](./box-model.svg "Box model visual representation")
  
  <figcaption>Visual representation and structure of the CSS Box Model as understood by the browser, which includes the content, padding, border and margin areas.</figcaption>
</figure>

Every HTML element in a Web document we use for creating content is a rectangle (or a box) and consists of four parts - `content`, `padding`, `border` and `margin`.

These areas are always part of every element, even if they are not defined in the style sheet (in which case they have either a value of zero or no value). This is how we can imagine every visible element.

<figure>

![Box model detail](./box-model-detail.svg)

  <figcaption>Each HTML element consists of a Box Model, which has various properties that we can change in CSS.</figcaption>
</figure>

Each area (except `content`) has all four sides defined, so it is possible to manipulate them individually; content only has `width` and `height`.

### Content box

The content of the element (as well as the `border` and `padding`) is located inside each HTML element. It's the area where your content is displayed. It can be a text, an `image`, a `video`, or any other element in a document.
  
  ![Box Model content](./box-model-content.svg "Box Model content")

<p>The content box is the area that the content lives in.</p>

```html
<h1>I'm content.</h1>
<p>I'm also content.</p>
<details>I'm content too!</details>
```

The `content` CSS property replaces an element with a generated value, which  means that it **can be manipulated by pseudo-elements**. We can change the size using properties such as `inline-size` and `block-size` or `width` and `height`.

<div class="code-example" loading="lazy">
<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="poQENjp" data-user="ondrejko">
  <span>See the Pen <a href="https://codepen.io/ondrejko/pen/poQENjp">
  How the CSS box model works - Padding Example</a> by Ondřej Konečný (<a href="https://codepen.io/ondrejko">@ondrejko</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>

### Padding box

Padding adds extra space between the content area and its border. It has the same background as the content itself.

![Box Model - Padding](./box-model-padding.svg "Box Model - Padding")

Padding has many notations that we can use.

```css
p { padding: 0;}
p { padding: 10rem 20% 30vmin 40ex;}
p { padding-left: 10em;}
p { padding-top: 20vw;}
p { padding-inline-start: 10ch;}
p { padding-block-end: 10mm;}
```

We can change the values using `padding` and related properties such as `padding-inline-start` or `padding-block-end`. The `padding` property is, therefore, an **indentation inside the element** itself and sets the padding area on all four sides of an element at once.

<div class="code-example" loading="lazy">
<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="VwVKKxR" data-user="ondrejko">
  <span>See the Pen <a href="https://codepen.io/ondrejko/pen/VwVKKxR">
  How the CSS box model works - Padding Example</a> by Ondřej Konečný (<a href="https://codepen.io/ondrejko">@ondrejko</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>

### Border box

The element's border is located between the area of the inner edge (`padding`) and the outer edge (`margin`). Its appearance **can be adjusted** according to the designer's preferences.

![Box Model - Border](./box-model-border.svg "Box Model - Border")

The border also has many definitions which can change its appearance.

<pre class="language-css" tabindex="-1">
<code class="language-css">
border: 0.5rem outset pink;
border: 4mm ridge rgba(211, 220, 50, .6);
border-width: 5pt dashed #ffcc00;
border-left-width: 4em;
border-bottom-style: none;
border-right-color: oklch(59.69% 0.156 49.77 / .5);
`
</pre>
<p>The border-box property is used to frame an element visually. Its color, size, and style can be controlled using `border` and related properties such as `border-color`, `border-width` or `border-style`.</p>
<div class="code-example" loading="lazy">
<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="xxQEEoQ" data-user="ondrejko">
  <span>See the Pen <a href="https://codepen.io/ondrejko/pen/xxQEEoQ">
  How the CSS box model works - Border Example</a> by Ondřej Konečný (<a href="https://codepen.io/ondrejko">@ondrejko</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>
<h3 id="margin-box-overview">Margin box</h3>
<p>The area of the outer margin expands the space around the element outside the border. This empty space separates one element from another.</p>
<figure>
  <img src="box-model-margin.svg" alt="">
</figure>
<p>The margin also **offers several options** for manipulating the layout.</p>
<pre class="language-css" tabindex="-1">
<code class="language-css">
margin: -3px;
margin: 5% auto;
margin: 2px 1.6em 0 auto;
margin-block-start: 10px;
margin-inline-start: revert-layer;
margin-inline: 20ch -40vh;
`
</pre>
<div class="code-example" loading="lazy">
<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="YzRGREx" data-user="ondrejko">
  <span>See the Pen <a href="https://codepen.io/ondrejko/pen/YzRGREx">
  How the CSS box model works - Padding Example</a> by Ondřej Konečný (<a href="https://codepen.io/ondrejko">@ondrejko</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>
<h3 id="summary-of-differences">Summary of differences</h3>
<p>The **content** and **border** areas are rarely confused. The former is the content of the element and the latter is its boundary. However, there is often a misunderstanding regarding the use of inner and outer indentation.</p>
<p>Both properties (`padding` and `margin`) create empty space around the content of the elements which is why it is easy to confuse them or disregard the differences in their behavior. The difference is in the way gaps are created and used.</p>
<p>Let's take a look at the three most important takeaways:</p>
<table>
<thead>
<tr>
  <th>Padding</th>
  <th>Margin</th>
</tr>
</thead>
<tbody>
<tr>
  <td>Padding is the inner space of an element.</td>
  <td>Margin is the outer space of an element.</td>
</tr>
<tr>
  <td>The styling of an element affects the padding.</td>
  <td>The styling of an element does not affect the margin.</td>
</tr>
<tr>
  <td>It does not allow negative values.</td>
  <td>It can have negative values.</td>
</tr>
</tbody>
</table>
<p>If you need help distinguishing these areas, <a href="https://web.dev/learn/css/box-model/#a-useful-analogy">check out this handy analogy</a> by <a href="https://una.im/">Una Kravets</a>.</p>
<p>Margin has two specific behaviors. Firstly, it is possible to use negative values; secondly, its vertical values merge in certain cases. This atypical behavior is called **margin collapsing**.</p>
<h2 id="margin-collapsing">Margin collapsing</h2>
<p>Let's define when this atypical behavior occurs. The outer edges of two elements merge if the following conditions are met:</p>
<ol>
  <li>Both elements are <a href="https://www.w3.org/TR/CSS22/visuren.html#block-boxes">block elements</a>.</li>
  <li>The merging elements are either top or bottom margins; merging does not apply to `margin-left` and `margin-right`.</li>
  <li>The elements are at the same level of the DOM structure and there is no separating content between them.</li>
  <li>The elements are in a parent-child relationship with an internal indentation or boundary defined.</li>
  <li>The `float` property is not applied to the element.</li>
  <li>Elements do not have an `absolute` positioning set.</li>
</ol>
<p>You can find an even more detailed description <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing">on the MDN page</a>.</p>
<h3 id="collapsing-behavior">Collapsing behavior</h3>
<p>Merging makes it easy to define vertical margins for multiple consecutive elements in the content.</p>
<p>This behavior is useful, for example, when designing a blog article containing various elements for which we want to have a unified indent. `figures`, `tables`, `headings`, `paragraphs`, and other elements can have the same outer indent, regardless of the order in which they appear. As a result, we don't have to define offsets for each combination.</p>
<p>The edges merge when two vertical edges (top and bottom) come into contact. When the merge occurs, only the larger indent value is applied. Think of it as a duel of two outer edges, where **the bigger one wins**.</p>
<figure>
  <img src="collapsing-1.svg" alt="">
</figure>
<p>If the offset values are the same for both of the elements, only one remains, or both values merge into one.</p>
<figure>
  <img src="collapsing-2.svg" alt="">
</figure>
<h3 id="parent-dominance">Parent dominance</h3>
<p>Merging also occurs for elements when their parent element has a defined outer edge in the vertical direction as well as elements inside. In this case, however, it depends on what properties the elements inside have.</p>
<p>If the elements inside the parent element have a `padding` or `border` property set, the `margin` will not be merged.</p>
<p>Take a look at the example and try to explore what happens, when all nested elements have an internal offset.</p>
<div class="code-example" loading="lazy">
<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="mdEGwMr" data-user="ondrejko">
  <span>See the Pen <a href="https://codepen.io/ondrejko/pen/mdEGwMr">
  Box Model: Collapsing Margins - Parents and Children Comparison</a> by Ondřej Konečný (<a href="https://codepen.io/ondrejko">@ondrejko</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>
<h3 id="negative-values">Negative values</h3>
<p>Merging works the same for negative outer offset values. It just needs to be carefully calculated.</p>
<p>If one outer offset value is negative, it is subtracted from the positive value. Therefore, if a `margin-bottom` is set to `-50px` followed by an element with a `margin-top` of `100px`, the resulting value of the offset will be `50px` after merging.</p>
<div class="code-example" loading="lazy">
<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="QWEVgMQ" data-user="ondrejko">
  <span>See the Pen <a href="https://codepen.io/ondrejko/pen/QWEVgMQ">
  Box Model: Collapsing Margins - Vertical and Negative</a> by Ondřej Konečný (<a href="https://codepen.io/ondrejko">@ondrejko</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>
<p>The same principle applies when we combine two negative offsets. Again, the higher (in this case more "negative") value applies after the merger.</p>
<h2 id="box-sizing">Box Sizing</h2>
<p>To further complicate things, the sizes of individual Box Model areas are calculated differently. How does it work?</p>
<p>The `box-sizing`, a property that defines how the `width` and `height` of an element are calculated, is set to `content-box` by default in browsers. However, there is another value that changes the behavior of the element size calculation: `border-box`. Historically, the `padding-box` value also appeared in the specification, but it has since been removed and no longer exists in today's specification. It calculated box size by summing the content and padding areas without a border.</p>
<h3 id="content-box">Content-Box</h3>
<p>The width and height calculation of an element is given by the sum of the `content`, `padding`, and `border` areas. The margin property does not affect the resulting size of individual elements.</p>
<p>This means that if the width and height of the element are set, the values of the padding and border properties will expand the total size of the box by the sum of their values. This behavior corresponds to the CSS setting of `box-sizing: content-box` property.</p>
<div class="code-example" loading="lazy">
<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="wvWEeee" data-user="ondrejko">
  <span>See the Pen <a href="https://codepen.io/ondrejko/pen/wvWEeee">
  Box Model: Content-Box</a> by Ondřej Konečný (<a href="https://codepen.io/ondrejko">@ondrejko</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>
<h3 id="border-box">Border-Box</h3>
<p>For this type of model, the defined width and height are equal to the resulting box size, regardless of the values of the `padding` or `border` properties. Again, the `margin` property does not affect the resulting size of the element. This behavior corresponds to the CSS setting of `box-sizing: border-box` property.</p>
<div class="code-example" loading="lazy">
<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="OJXogxm" data-user="ondrejko">
  <span>See the Pen <a href="https://codepen.io/ondrejko/pen/OJXogxm">
  Box Model: Border-Box</a> by Ondřej Konečný (<a href="https://codepen.io/ondrejko">@ondrejko</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>
<h2 id="box-model-settings">Box model settings</h2>
<p>Setting up a single box model for all elements is currently the best possible solution. There is a simple explanation for this. All elements on the site are handled the same, so their behavior is consistent throughout the document.</p>
<p>In addition, web design tools work with the same elements, making it easier for the designer and coder to collaborate. Decorations such as frames do not affect the defined dimensions of the elements, and the elements on the resulting site should behave in the same way.</p>
<p>It is recommended to set the `box-sizing` property to `border-box`. This is straightforward and intuitive, but we must set it manually in the font because the `content-box` is still the default value for backward compatibility.</p>
<p>However, there are exceptions when it is recommended to set the `content-box` value for the `box-sizing` property. For relative or absolute positioning, this setting ensures that the positioning setting values are relative to the content, and independent of frame or indent changes.</p>
<p>The following rule has thus been added to the basic style, which is now a common practice.</p>
<pre class="language-css" tabindex="-1">
<code class="language-css">
*, *::before, *::after {
  box-sizing: border-box;
}
`
</pre>
<p>Jon Neal <a href="https://blog.teamtreehouse.com/box-sizing-secret-simple-css-layouts">came up with another viable alternative</a>. Instead of resetting the `box-sizing` property on the `border-box` for all elements, it only sets it to the document’s root element. For other elements, it uses the `inherit` value, which allows the `box-sizing` property to inherit:</p>
<pre class="language-css" tabindex="-1">
<code class="language-css">
html {
  box-sizing: border-box;
}
*, *::before, *::after {
  box-sizing: inherit;
}
`
</pre>
<p>This can be useful when designing a component that assumes the default `box-sizing: content-box` behavior, and elements embedded inside. It can prevent unwanted breakage of nested components.</p>
<h2 id="takeaway">Takeaway</h2>
<p>The behavior of the CSS Box Model can be confusing due to its evolution. This is evidenced by the fact that <a href="https://css-tricks.com/international-box-sizing-awareness-day/">International Box-Sizing Awareness Day</a> was established on **February 1st**.</p>
<p>Due to backward compatibility, default browser settings have the `box-sizing` property set to `content-box`, even though the vast majority today use the `border-box` value. Therefore, we should remember to define the behavior of the box model in our CSS styles and understand the differences between these values.</p>
<p>It is up to each individual whether they want to use one calculation method or the other. What is crucial is to understand the core principles.</p>