---
title : "Dog"
layout : archive
permalink : categories/dog
author_profile : true
sidebar_main : true
---

{% assign posts = site.categories['Dog'] %}

{% for post in posts %}
    {% include archive-single.html type = page.entries_layout %}
{% endfor %}
