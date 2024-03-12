---
layout: page
title: Summoning
tag-name: summoning
---

Summoning is a 3D open world action RPG being developed in the Godot game engine. My motto for this project
has always been "create something every day". Slowly but surely a real game is coming to life. Stay tuned
for a playable demo in the future.

<section>
  {% if site.posts[0] %}

    <h3>Posts about Summoning</h3>
    {%for post in site.posts %}
      {% if post.tag contains page.tag-name %}
        {% unless post.next %}
          <ul>
        {% else %}
          {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
          {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
          {% if year != nyear %}
            </ul>
            <h3>{{ post.date | date: '%Y' }}</h3>
            <ul>
          {% endif %}
        {% endunless %}
          <li><time>{{ post.date | date:"%d %b" }} - </time>
            <a href="{{ post.url | prepend: site.baseurl | replace: '//', '/' }}">
              {{ post.title }}
            </a>
          </li>
      {% endif %}
    {% endfor %}
    </ul>

  {% endif %}
</section>

<section>

  <h3>Dev screenshots</h3>

{% include bilboard_image.html image-path="/assets/character-creation1.png" %}
{% include bilboard_image.html image-path="/assets/action-combat.png" %}
{% include bilboard_image.html image-path="/assets/assets1.png" %}
{% include bilboard_image.html image-path="/assets/assets2.png" %}

</section>
