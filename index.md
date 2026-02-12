---
title: " " 
layout: splash 
author_profile: false
permalink: /
hidden: true
# header:
#  overlay_color: "#f2f3f3"
#  overlay_image: 
# excerpt: >
#  The personal website and home to the original Antonio Banderas.<br />
---

<!-- ### Recent -->
<h6>RECENT</h6>
<div class="feature__wrapper">
  {% for post in site.posts limit:6 %}
  <div class="feature__item">
    <div class="archive__item">
      {% if post.header.teaser %}
      <div class="archive__item-teaser">
        <img src="{{ post.header.teaser | relative_url }}" alt="{{ post.title }}">
      </div>
      {% endif %}
      <div class="archive__item-body">
        <h2 class="archive__item-title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
        <div class="archive__item-excerpt">
          {{ post.excerpt }}
        </div>
      </div>
    </div>
  </div>
{% endfor %}
</div>
