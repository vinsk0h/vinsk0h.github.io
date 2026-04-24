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
  <ul class="writeup-list">
    {% for post in writeup_posts %}
      {% assign img_src = post.image.path | default: post.image %}
      <li class="writeup-item">
        {% if img_src %}
          <div class="writeup-thumb">
            <img src="{{ img_src }}" alt="{{ post.image.alt | default: post.title | escape }}" loading="lazy">
          </div>
        {% endif %}
        <div class="writeup-content">
          <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
          <div class="writeup-meta">
            <i class="far fa-calendar fa-fw"></i> {{ post.date | date: "%B %d, %Y" }}
            {% for tag in post.tags %}<code>{{ tag }}</code>{% endfor %}
          </div>
          {% if post.description %}
            <p class="writeup-desc">{{ post.description }}</p>
          {% endif %}
        </div>
      </li>
    {% endfor %}
  </ul>
{% endif %}
