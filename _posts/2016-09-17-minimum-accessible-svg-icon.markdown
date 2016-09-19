---
layout: post
title:  "Minimum Accessible SVG Icon"
date:   2016-09-17 23:23:23 -0700
categories: SVG a11y
---

Here's my archtype for a static, accessible SVG icon.

{% highlight ruby %}
<svg viewBox="0 0 16 16" role="img" aria-labelledby="title desc">
  <title id="title">Star Icon</title>
  <desc id="desc">Image of a star indicating "favorite."</desc>
  <path role="presentation" fill="#000" d="..."></path>
</svg>
{% endhighlight %}

Let's talk through the bits.

<!-- fold -->

### `title`

The `title` tag  is the `alt` attribute of an `svg`. These examples are conceptually identical:

{% highlight ruby %}
<img src="..." alt="Star Icon" />

<svg>
  <title id="title">Star Icon</title>
  ...
</svg>
{% endhighlight %}

Setting the `id` helps smooth over the differences between screen readers. We'll talk about that in a sec.

### `desc`

The `desc` is just an extension of the `title`. If you're wordy, be wordy here. If the title is clear, don't feel the need to repeart yourself here.

Again, setting the `id` helps smooth over the differences between screen readers.

### `aria-labelledby`

This is where you tie in your `text`/`desc` values into the root of your SVG&mdash;communicating to assisted devices where descriptive text should be found.

{% highlight ruby %}
<svg aria-labelledby="title desc">
  <title id="title">Star Icon</title>
  <desc id="desc">Image of a star indicating "favorite."</desc>
  ...
</svg>
{% endhighlight %}

It's worth noting that the `aria-labelledby` attribute is using the `id`s not the tag names.

### `role`

`roles` help to assisted devices properly identify the SVG as an image. Use `role="img"` on the root SVG element and `role="presentation"` on the `path`.

{% highlight ruby %}
<svg role="img" aria-labelledby="title desc">
  <title id="title">Star Icon</title>
  <desc id="desc">Image of a star indicating "favorite."</desc>
  <path role="presentation" fill="#000" d="..."></path>
</svg>
{% endhighlight %}

### Further Reading

*[Using ARIA to enhance SVG accessibility](https://www.paciellogroup.com/blog/2013/12/using-aria-enhance-svg-accessibility/)* is the best article I've foundon this topic. It's more technical. The author dives deep into each attribute and triggers specific browser support.
