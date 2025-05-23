---
layout: single
title: "Blog"
permalink: /blog/
author_profile: true
---

Welcome to my blog! Here I share my musings on software engineering, AI/ML, and technology in general.

<div>
  {% for post in site.posts %}
    <article>
      <h2>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h2>
      <p class="page__meta">
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time>
      </p>
      <p class="archive__item-excerpt">{{ post.excerpt | markdownify | strip_html | truncate: 200 }}</p>
    </article>
  {% endfor %}
</div>
