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
 	[Link to a post]({% link _posts/2019-06-23-2019-first_post.md %})
  
 	

{% endfor %}

