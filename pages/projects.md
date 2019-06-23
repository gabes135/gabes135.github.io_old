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
 		<a href="{{ post.url }}">
    	<h2>{{ post.title }}</h2>
   		<p>{{ post.date | date_to_string }}</p>
  		</a>
	{% endfor %}
</ul>