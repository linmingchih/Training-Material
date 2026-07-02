---
layout: default
title: 文件索引
permalink: /
---

# 文件索引

以下為目前站內可見的 Markdown 文件：

{% assign markdown_pages = site.pages | sort: "path" %}
{% assign has_markdown = false %}

{% for page in markdown_pages %}
	{% if page.path != "index.md" %}
		{% if page.path contains ".md" %}
			{% assign has_markdown = true %}
- [{{ page.path | replace: ".md", "" }}]({{ page.url | relative_url }})
		{% endif %}
	{% endif %}
{% endfor %}

{% unless has_markdown %}
目前找不到 Markdown 檔案。
{% endunless %}
