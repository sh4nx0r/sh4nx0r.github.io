---
layout: page
permalink: /whoami/index.html
title: whoami
tags: 
imagefeature:
chart: false
---


{% assign total_words = 0 %}
{% assign total_readtime = 0 %}
{% assign featuredcount = 0 %}
{% assign statuscount = 0 %}

{% for post in site.posts %}
    {% assign post_words = post.content | strip_html | number_of_words %}
    {% assign readtime = post_words | append: '.0' | divided_by:200 %}
    {% assign total_words = total_words | plus: post_words %}
    {% assign total_readtime = total_readtime | plus: readtime %}
    {% if post.featured %}
    {% assign featuredcount = featuredcount | plus: 1 %}
    {% endif %}
{% endfor %}

For the :heart: of Markdown, My name is **Shankar Damodaran**, and am glad you are here on my personal blog. Enjoy your stay.

### Blog _Nerdy_ Stats

 The Blog currently has <b>{{ site.posts | size }}</b> posts in <b>{{ site.categories | size }}</b> categories that totally has <b>{{ total_words }}</b> words to be exact. This will take an average reader approximately <span class="time"><b>{{ total_readtime }}</b></span> minutes to read.

  {% if featuredcount != 0 %}There are <a href="{{ site.url }}/featured">{{ featuredcount }} featured posts</a> worth checking out.{% endif %} The most recent post {% for post in site.posts limit:1 %}{% if post.description %}<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}">"{{ post.title }}"</a>{% else %}<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}" title="Read more about {{ post.title }}">"{{ post.title }}"</a>{% endif %}{% endfor %} was published on {% for post in site.posts limit:1 %}{% assign modifiedtime = post.modified | date: "%Y%m%d" %}{% assign posttime = post.date | date: "%Y%m%d" %}<time datetime="{{ post.date | date_to_xmlschema }}" class="post-time">{{ post.date | date: "%d %b %Y" }}</time>{% if post.modified %}{% if modifiedtime != posttime %} and last modified on <time datetime="{{ post.modified | date: "%Y-%m-%d" }}" itemprop="dateModified">{{ post.modified | date: "%d %b %Y" }}</time>{% endif %}{% endif %}{% endfor %}. The latest update to the site was done on {{ site.time | date: "%A, %d %b %Y" }} at {{ site.time | date: "%I:%M %p" }} [UTC](http://en.wikipedia.org/wiki/Coordinated_Universal_Time "Temps Universel Coordonné").

### Professional Front

That's my CV.

<figure>
	<img src="{{ site.url }}/images/cvx.jpg" alt="Shankar Damodaran Resume">
	<figcaption>Shankar Damodaran - CV</figcaption>
</figure>
