---
layout: default
title: Blog
---

<ul class="unstyled">
  {% for page in site.posts %}
    <li>
      <h3><a href="{{ page.url }}">{{ page.title }}</a></h3>
      <p>Posted on <a href="{{ page.url }}">{{ page.date | date: "%B %d, %Y" }}</a> by {{ page.author }}. {% include x-post.html url=page.x-post %}</p>
      {% capture more %} <a href="{{ page.url }}">Continue reading →</a>{% endcapture %}
      {% if page.layout == "quickpost" %}
        {{page.content}}
      {% else %}
        {{ page.excerpt | truncatewords: 80 | append: more | markdownify }}
      {% endif %}
      <hr>
    </li>
  {% endfor %}
</ul>