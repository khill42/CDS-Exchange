---
layout: page
title: Events
---

<div>


{%- if site.posts.size > 0 -%}
    <h2 class="post-list-heading">Upcoming Events</h2>
    <ul class="post-list">

      {% capture now %}{{'now' | date: '%s' | plus: 0 }}{% endcapture %}
        {% for post in site.posts %}
        {% if post.hide == null or post.hide == false %}
    {% capture date %}{{ post.dateofevent | date: '%s' | plus: 0 }}{% endcapture %}
    {% if date >= now %}
      <li>
        {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        <span class="post-meta">{{ post.dateofevent | date: date_format }}</span>
        <h3>
          {% if post.content.size <= 1 %}
          <a class="post-link" href="{{ post.eventurl }}">
            {{ post.title | escape }}
          </a>
          {% else %}
            <a class="post-link" href="{{ post.url }}">
            {{ post.title | escape }}
          </a>
          {% endif %}
        </h3>
        {%- if site.show_excerpts -%}
          {{ post.excerpt }}
        {%- endif -%}
      </li>
      {% endif %}
      {%- endif -%}
      {%- endfor -%}
    </ul>
{%- endif -%}

<hr>

{%- if site.posts.size > 0 -%}
    <h2 class="post-list-heading">Past Events</h2>
    <ul class="post-list">

     {% capture now %}{{'now' | date: '%s' | plus: 0 }}{% endcapture %}
        {% for post in site.posts %}
        {% if post.hide == null or post.hide == false %}
    {% capture date %}{{ post.dateofevent | date: '%s' | plus: 0 }}{% endcapture %}
    {% if date < now %}
      <li>
        {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        <span class="post-meta">{{ post.dateofevent | date: date_format }}</span>
        <h3>
          {% if post.content.size <= 1 %}
          <a class="post-link" href="{{ post.eventurl }}">
            {{ post.title | escape }}
          </a>
          {% else %}
            <a class="post-link" href="{{ post.url }}">
            {{ post.title | escape }}
          </a>
          {% endif %}
        </h3>
        {%- if site.show_excerpts -%}
          {{ post.excerpt }}
        {%- endif -%}
      </li>
      {% endif %}
      {% endif %}
      {%- endfor -%}
    </ul>
{%- endif -%}
</div>