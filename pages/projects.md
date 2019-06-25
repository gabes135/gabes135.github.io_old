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
	* [Name of Link]({% link {{ site.baseurl }}{2019-06-23-2019-first_post %}})
 
  
 	2019-06-23-2019-first_post

{% endfor %}
</ul>
