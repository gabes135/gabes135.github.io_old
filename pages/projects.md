---
layout: single
title: "My Personal Projects"
permalink: /projects/
auhtor_profile: true 
header:
	image: "/images/header.jpg"
---

{% for post in site.posts %}
* {{post.excerpt}}
* [Link to post]({{site.url}}{{post.url}})

{% endfor %}

{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}
