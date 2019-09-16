---
layout: blogger-snippets-index
title: Blogger Snippets
description: Library of commonly used snippets for Blogger.
permalink: /blogger-snippets/
---

<div class="list-group list-group-flush">
  {% for post in site.blogger-snippets %}
    <a class="list-group-item list-group-item-action" href="{{ post.url }}">
      {{ post.title }}
    </a>
  {% endfor %}
</div>
