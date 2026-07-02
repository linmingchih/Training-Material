---
layout: default
title: 文件索引
permalink: /
---

# 文件索引

以下為目前站內可見的資料夾：

{% assign markdown_pages = site.pages | sort: "path" %}
{% assign has_dirs = false %}
{% assign seen_dirs = "|" %}

{% for page in markdown_pages %}
	{% if page.path contains ".md" %}
		{% if page.path != "index.md" %}
			{% if page.dir != "/" %}
				{% assign dir_name = page.dir | remove_first: "/" | remove_last: "/" %}
				{% capture marker %}|{{ dir_name }}|{% endcapture %}
				{% unless seen_dirs contains marker %}
					{% assign seen_dirs = seen_dirs | append: dir_name | append: "|" %}
					{% assign has_dirs = true %}
- [{{ dir_name }}]({{ page.dir | relative_url }})
				{% endunless %}
			{% endif %}
		{% endif %}
	{% endif %}
{% endfor %}

{% unless has_dirs %}
目前找不到資料夾。
{% endunless %}
