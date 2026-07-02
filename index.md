---
layout: default
title: 文件索引
permalink: /
---

# 文件索引

以下為目前站內可見的 Markdown 文件：

{% assign markdown_paths = "" | split: "" %}

{% for page in site.pages %}
  {% if page.path != "index.md" and page.path contains ".md" %}
    {% assign markdown_paths = markdown_paths | push: page.path %}
  {% endif %}
{% endfor %}

{% for file in site.static_files %}
  {% if file.extname == ".md" and file.path != "/index.md" %}
    {% assign path = file.path | remove_first: "/" %}
    {% unless markdown_paths contains path %}
      {% assign markdown_paths = markdown_paths | push: path %}
    {% endunless %}
  {% endif %}
{% endfor %}

{% assign markdown_paths = markdown_paths | sort %}

{% if markdown_paths.size > 0 %}
{% for path in markdown_paths %}
- [{{ path | replace: ".md", "" }}]({{ path | relative_url }})
{% endfor %}
{% else %}
目前找不到 Markdown 檔案。
{% endif %}
