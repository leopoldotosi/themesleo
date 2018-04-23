---
layout: layout1
---

<section>
  

  {% for article in cultura-digitale_ind.categories.all %}

<div class="relative">
    <article>
        <h3>{{ article.title }}</h3>
<ul class="actions"> <li><a href="{{site.baseurl}}/themesleo{{article.url}}" class="button">More</a></li> </ul>
    </article>
</div>




  {% endfor %}


{% for post in site.categories.[category_name] %}
    {% if post_index0 == forloop.index %}{% assign next_post = post %}{% endif %}
    {% if post_index1 == forloop.index0 %}{% assign prev_post = post %}{% endif %}
{% endfor %}


</section>


