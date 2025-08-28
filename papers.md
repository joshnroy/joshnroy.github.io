---
layout: single
title: "Annotated Bibliography"
permalink: /papers/
author_profile: true
classes: wide
---

A collection of papers I've authored and key papers I've read, with notes and reflections. Each annotation includes both the original publication date and when I wrote my thoughts about it.

*Papers are sorted by annotation date (most recent first)*

---

{% assign papers_by_date = site.papers | sort: 'date' | reverse %}

{% for paper in papers_by_date %}
<article class="archive__item" itemscope itemtype="https://schema.org/CreativeWork">
  <h2 class="archive__item-title no_toc" itemprop="headline">
    <a href="{{ paper.url | relative_url }}" rel="permalink">{{ paper.title }}</a>
  </h2>
  
  <p class="page__meta">
    <strong>{{ paper.authors }}</strong><br>
    <em>{{ paper.venue }}</em>
    {% if paper.tags contains "award" %}
      {% for tag in paper.tags %}
        {% if tag == "award" %}
          <span style="color: #d4af37;">🏆</span>
        {% endif %}
      {% endfor %}
    {% endif %}
    <br>
    <small>Published: {{ paper.paper_date | date: "%B %Y" }} | Annotated: {{ paper.date | date: "%B %d, %Y" }}</small>
  </p>
  
  <p class="archive__item-excerpt" itemprop="description">
    {{ paper.excerpt | markdownify | strip_html | truncate: 250 }}
  </p>
  
  <p>
    <a href="{{ paper.paper_url }}" target="_blank" rel="noopener noreferrer">
      <small>📄 Original Paper</small>
    </a>
    &nbsp;&nbsp;
    <a href="{{ paper.url | relative_url }}">
      <small>📝 Read Annotation →</small>
    </a>
  </p>
</article>
<hr style="border: 0; border-top: 1px solid #eee; margin: 2em 0;">
{% endfor %}

---

## About This Bibliography

This annotated bibliography serves multiple purposes:

1. **Personal Learning**: Writing about papers helps me understand them deeply
2. **Knowledge Sharing**: My notes might help others understand these works
3. **Historical Record**: Capturing how my understanding evolves over time
4. **Research Context**: Connecting papers to broader themes and current work

Each annotation includes:
- Summary of key contributions
- Technical insights and implementation details  
- Personal reflections and connections to other work
- Questions and future directions
- How perspectives have changed since publication

Feel free to reach out if you'd like to discuss any of these papers!