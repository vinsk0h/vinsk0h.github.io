---
layout: page
title: Writeups
icon: fa-regular fa-pen-to-square
permalink: /writeups/
order: 2
---

{% assign writeup_posts = site.posts | where_exp: "post", "post.categories contains 'Writeups'" | sort: 'date' | reverse %}

{% if writeup_posts.size == 0 %}
  <p>No writeups yet. Check back soon!</p>
{% else %}
  <ul class="post-list">
    {% for post in writeup_posts %}
      <li>
        <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
        <small>
          <i class="far fa-calendar fa-fw"></i> {{ post.date | date: "%B %d, %Y" }}
          {% for tag in post.tags %}
            <code>{{ tag }}</code>
          {% endfor %}
        </small>
        {% if post.description %}
          <p>{{ post.description }}</p>
        {% endif %}
      </li>
    {% endfor %}
  </ul>
{% endif %}
