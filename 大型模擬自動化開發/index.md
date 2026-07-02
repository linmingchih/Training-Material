---
layout: default
title: 大型模擬自動化開發
---

# 大型模擬自動化開發

以下為此資料夾中的 Markdown 文件：

{% assign markdown_pages = site.pages | sort: "path" %}
{% assign has_docs = false %}

{% for doc in markdown_pages %}
  {% if doc.dir == page.dir %}
    {% if doc.path contains ".md" %}
      {% if doc.path != page.path %}
        {% assign has_docs = true %}
- [{{ doc.title | default: doc.path | replace: ".md", "" | remove_first: page.dir }}]({{ doc.url | relative_url }})
      {% endif %}
    {% endif %}
  {% endif %}
{% endfor %}

{% unless has_docs %}
目前此資料夾找不到 Markdown 檔案。
{% endunless %}
