---
layout: page
title: Welcome!
tagline: SOMETHING Li is interested in
---
{% include JB/setup %}

>A physicist who doesn't know machine learning is not a good Aikidoka

Li Li

* Physics PhD Candidate, University of California, Irvine
* Implementing Machine Learning in Density Functional Theory
* Sandan (3rd black belt) in Aikido, Certificated Instructor
* Gastronome 

## Recent Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

{{ post.content }}



