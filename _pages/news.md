---
title: "Experience"
permalink: /experience/
author_profile: true
---

{% assign experience = site.news | sort: 'date' | reverse %}
{% for item in experience %}
<div style="margin-bottom: 1em;">
 <strong>{{ item.date | date: "%b %Y" }}</strong> — {{ item.title }}<br>
 {{ item.content | markdownify }}
</div>
{% endfor %}
