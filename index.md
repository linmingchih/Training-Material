---
layout: default
title: 文件索引
permalink: /
---

# 文件索引

以下為目前站內可見的 Markdown 文件：

{% assign markdown_pages = site.pages | where_exp: "p", "p.path != 'index.md' and p.ext == '.md'" | sort: "path" %}

{% if markdown_pages.size > 0 %}
{% for page in markdown_pages %}
- [{{ page.path | replace: ".md", "" }}]({{ page.url | relative_url }})
{% endfor %}
{% else %}
目前找不到 Markdown 檔案。
{% endif %}
