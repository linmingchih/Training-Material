---
layout: default
title: 文件索引
permalink: /
---

# 文件索引

以下為目前站內可見的資料夾：

{% assign all_pages = site.pages | sort: "path" %}
{% assign has_dirs = false %}

{% for p in all_pages %}
  {% if p.name == "index.md" %}
    {% if p.path != "index.md" %}
      {% assign has_dirs = true %}
- [{{ p.title | default: p.dir | remove_first: "/" | remove_last: "/" }}]({{ p.url | relative_url }})
    {% endif %}
  {% endif %}
{% endfor %}

{% unless has_dirs %}
目前找不到資料夾。
{% endunless %}
