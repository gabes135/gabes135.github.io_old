---
layout: single
title: "My Personal Projects"
permalink: /projects/
auhtor_profile: true 
header:
	image: "/images/header.jpg"
---




<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>