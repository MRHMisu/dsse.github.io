---
title: "DSSE->Posts"
layout: default
excerpt: "DSSE -- Posts"
sitemap: false
permalink: /posts/
---



<ul class="posts">

	  {% for post in site.posts %}  
    <div class="card" >
	  <a href="{{ post.url | absolute_url }}">
      <h2 class="post-title">{{ post.title }}</h2>

      {% if post.subtitle %}
        <h3 class="post-subtitle">
        {{ post.subtitle }}
        </h3>
      {% endif %}
    </a>
	
	<p class="post-meta">
      {% assign date_format = site.date_format | default: "%B %-d, %Y" %}
      Posted on {{ post.date | date: date_format }}
    </p>
        
	<div class="post-entry-container">
      {%- capture thumbnail -%}
        {% if post.thumbnail-img %}
          {{ post.thumbnail-img }}
        {% elsif post.cover-img %}
          {% if post.cover-img.first %}
            {{ post.cover-img[0].first.first }}
          {% else %}
            {{ post.cover-img }}
          {% endif %}
        {% else %}
        {% endif %}
      {% endcapture %}
      {% assign thumbnail=thumbnail | strip %}
      {% if thumbnail != "" %}
	 <!-- <div class="post-image">
        <a href="{{ post.url | absolute_url }}">
          <img src="{{ thumbnail | absolute_url }}">
        </a>
      </div>-->
      </div>
      {% endif %}
      <div class="post-entry">
        {% assign excerpt_length = site.excerpt_length | default: 50 %}
        {{ post.excerpt | strip_html | xml_escape | truncatewords: excerpt_length }}
        {% assign excerpt_word_count = post.excerpt | number_of_words %}
        {% if post.content != post.excerpt or excerpt_word_count > excerpt_length %}
          <a href="{{ post.url | absolute_url }}" class="post-read-more">[Read&nbsp;More]</a>
        {% endif %}
      </div>
    </div>
	  {% endfor %}
</ul>