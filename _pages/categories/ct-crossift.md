---
title : "CROSSFIT"
layout : archive
permalink : categories/crossfit
author_profile : true
sidebar_main : true
---

{% assign posts = site.categories['CROSSFIT'] %}

{% for post in posts %}
    {% include archive-single.html type = page.entries_layout %}
{% endfor %}
