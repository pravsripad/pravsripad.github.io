---
layout: archive
title: "Seitenübersicht"
permalink: /de/seitenplan/
author_profile: true
lang: de
locale: de
ref: sitemap
---

{% include base_path %}

Eine Liste aller Beiträge und Seiten auf dieser Website. Für Crawler gibt es auch eine [XML-Version]({{ base_path }}/sitemap.xml).

<h2>Seiten</h2>
{% for post in site.pages %}
  {% include archive-single.html %}
{% endfor %}

{% capture written_label %}'None'{% endcapture %}

{% for collection in site.collections %}
{% unless collection.output == false or collection.label == "posts" %}
  {% capture label %}{{ collection.label }}{% endcapture %}
  {% if label != written_label %}
  <h2>{{ label }}</h2>
  {% capture written_label %}{{ label }}{% endcapture %}
  {% endif %}
{% endunless %}
{% for post in collection.docs %}
  {% unless collection.output == false or collection.label == "posts" %}
  {% include archive-single.html %}
  {% endunless %}
{% endfor %}
{% endfor %}
