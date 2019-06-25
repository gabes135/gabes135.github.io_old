---
layout: single
title: "My Personal Projects"
permalink: /projects/
auhtor_profile: true 
header:
	image: "/images/header.jpg"
---

 {% for post in site.posts %}
 * [Link to a post]({% link _posts/{{ post.url }}%})
  
 	

{% endfor %}

