---
title : "맛집"
layout : archive
permalink : categories/food
author_profile : true
sidebar_main : true
---

{% assign posts = site.categories['Food'] %}

{% for post in posts %}
    {% include archive-single.html type = page.entries_layout %}
{% endfor %}
