---
layout: page
permalink: /news/
title: news
description: All news and updates, most recent first.
nav: false
---

<div class="news">
{%- assign news = site.news | sort: 'date' | reverse -%}
{%- assign current_year = '' -%}
<div class="table-responsive">
  <table class="table table-sm table-borderless">
  {% for item in news %}
    {%- assign item_year = item.date | date: "%Y" -%}
    {% if item_year != current_year %}
      {%- assign current_year = item_year -%}
      <tr><td colspan="2"><h2 class="year">{{ item_year }}</h2></td></tr>
    {% endif %}
    <tr>
      <th scope="row">{{ item.date | date: "%b %-d, %Y" }}</th>
      <td>
        {% if item.inline -%}
          {{ item.content | remove: '<p>' | remove: '</p>' | emojify }}
        {%- else -%}
          <a class="news-title" href="{{ item.url | relative_url }}">{{ item.title }}</a>
        {%- endif %}
      </td>
    </tr>
  {% endfor %}
  </table>
</div>
</div>
