---
layout: page
title: Writeups
icon: fa-regular fa-pen-to-square
permalink: /writeups/
order: 2
---

{% include lang.html %}

{% assign writeup_posts = site.posts | where_exp: "post", "post.categories contains 'Writeups'" | sort: 'date' | reverse %}

{% if writeup_posts.size == 0 %}
  <p>No writeups yet. Check back soon!</p>
{% else %}
  <div id="post-list" class="flex-grow-1 px-xl-1">
    {% for post in writeup_posts %}
      {% include post-card.html post=post %}
    {% endfor %}
  </div>
{% endif %}
