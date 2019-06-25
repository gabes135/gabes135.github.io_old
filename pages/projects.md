---
layout: single
title: "My Personal Projects"
permalink: /projects/
auhtor_profile: true 
header:
	image: "/images/header.jpg"
---

 {% for post in site.posts %}
  <a href="{{ post.url }}">
    ## {{ post.title }}
    {{ post.date | date_to_string }}
  </a>
{% endfor %}

