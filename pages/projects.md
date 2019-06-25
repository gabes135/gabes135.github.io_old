---
layout: single
title: "My Personal Projects"
permalink: /projects/
auhtor_profile: true 
header:
	image: "/images/header.jpg"
---

 {% for post in site.posts %}
 	{{ post.url }}
 	

{% endfor %}

