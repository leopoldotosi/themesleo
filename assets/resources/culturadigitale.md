---
layout: layout1
root: ../
---
<!-- culturadigitale -->

<p>
<div class="tiles">

	{% for post in site.posts %}
    {% if post.path contains 'culturadigitale' %}
    <div class="relative_left w3-round-xlarge">
	<article>
		<b>{{ post.title }}</b>
		<b>{{ post.category }}</b>
	
		<ul class="actions"> <li><a href="{{site.baseurl}}{{post.url}}" class="button">More</a></li> </ul>
	</article>
    </div>
    {% endif %}
	{% endfor %}
</div>
</p>


