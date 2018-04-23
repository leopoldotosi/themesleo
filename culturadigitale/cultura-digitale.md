---
layout: layout1
---

<section>
  

  {% for article in cultura-digitale_ind.categories.all %}

<div class="relative">
    <article>
        <h3>{{ article.title }}</h3>
	<ul class="actions"> <li><a href="{{article.url}}" class="button">More</a></li> </ul>
    </article>
</div>
{% endfor %}






{% for article in site.categories.[category_name] %}
<div>

  {{ article.title }}
#    {% if post_index0 == forloop.index %}{% assign next_post = post %}{% endif %}
#    {% if post_index1 == forloop.index0 %}{% assign prev_post = post %}{% endif %}
</div>
{% endfor %}


</section>


