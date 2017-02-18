---
layout: page
show_meta: false
title: "Develop your Application!"
subheadline: "Different techniques, Snippets, Tips and Tricks..."
header:
   image_fullwidth: "header_unsplash_5.jpg"
permalink: "/programming/"
comments: false
breadcrumb: true
---
<ul>
    {% for post in site.categories.programming %}
    <li><a href="{{ site.url }}{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
</ul>