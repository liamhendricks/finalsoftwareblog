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

{% include bilboard_image.html image-path="/assets/character-creation3.png" %}
{% include bilboard_image.html image-path="/assets/character-creation4.png" %}
{% include bilboard_image.html image-path="/assets/statue.png" %}
{% include bilboard_image.html image-path="/assets/ss1.png" %}
{% include bilboard_image.html image-path="/assets/ss9.png" %}
{% include bilboard_image.html image-path="/assets/ss2.png" %}
{% include bilboard_image.html image-path="/assets/ss10.png" %}
{% include bilboard_image.html image-path="/assets/assets1.png" %}
{% include bilboard_image.html image-path="/assets/ss3.png" %}
{% include bilboard_image.html image-path="/assets/ss4.png" %}
{% include bilboard_image.html image-path="/assets/ss5.png" %}
{% include bilboard_image.html image-path="/assets/ss6.png" %}
{% include bilboard_image.html image-path="/assets/assets2.png" %}
{% include bilboard_image.html image-path="/assets/ss7.png" %}
{% include bilboard_image.html image-path="/assets/ss8.png" %}

</section>
