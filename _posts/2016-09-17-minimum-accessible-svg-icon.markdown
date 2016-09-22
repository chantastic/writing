---
layout: post
title:  "Minimum Accessible SVG Icon"
date:   2016-09-17 23:23:23 -0700
categories: SVG a11y
---

Here's my archetype for an accessible SVG icon.

{% highlight html %}
<svg viewBox="0 0 16 16" role="img" aria-labelledby="title desc">
  <title id="title">Star Icon</title>
  <desc id="desc">Image of a star indicating "favorite."</desc>
  <path role="presentation" fill="#000" d="..."></path>
</svg>
{% endhighlight %}

<!-- fold -->

Here are the bits.

### `title`

The `title` tag  is the `alt` attribute of an `svg`. These examples are conceptually identical:

{% highlight html %}
<img src="..." alt="Star Icon" />

<svg>
  <title>Star Icon</title>
  ...
</svg>
{% endhighlight %}

### `desc`

The `desc` tag is an extension of the `title`. If you're wordy, be wordy here. If the title is clear, don't feel the need to repeat yourself.

{% highlight html %}
<svg>
  <title>Star Icon</title>
  <desc>Image of a star indicating "favorite."</desc>
  ...
</svg>
{% endhighlight %}

### `aria-labelledby`

You'll need to smooth over some of the quirks of assisted devices. `aria-labelledby` is an attribute on your root SVG element that points devices to your accessible text and description.

{% highlight html %}
<svg aria-labelledby="title desc">
  <title id="title">Star Icon</title>
  <desc id="desc">Image of a star indicating "favorite."</desc>
  ...
</svg>
{% endhighlight %}

Note that the `aria-labelledby` attribute uses `id`s to identify content, not the elements.

### `role`

`roles` help to assisted devices identify the SVG as an image. Use `role="img"` on the root SVG element and `role="presentation"` on the `path`.

{% highlight html %}
<svg role="img" aria-labelledby="title desc">
  <title id="title">Star Icon</title>
  <desc id="desc">Image of a star indicating "favorite."</desc>
  <path role="presentation" fill="#000" d="..."></path>
</svg>
{% endhighlight %}



*[Using ARIA to enhance SVG accessibility](https://www.paciellogroup.com/blog/2013/12/using-aria-enhance-svg-accessibility/)* is the best article I've foundon this topic. It's more technical. The author dives deep into each attribute and triggers specific browser support.
