---
layout: archive
title: "ಸೈಟ್ ನಕ್ಷೆ"
permalink: /kn/sitemap/
author_profile: true
lang: kn
locale: kn
ref: sitemap
---

{% include base_path %}

ವೆಬ್‌ಸೈಟ್‌ನ ಎಲ್ಲಾ ಬರಹಗಳು ಮತ್ತು ಪುಟಗಳ ಪಟ್ಟಿ. ಬಾಟ್‌ಗಳಿಗೆ [XML ರೂಪ]({{ base_path }}/sitemap.xml) ಸಹ ಲಭ್ಯವಿದೆ.

<h2>ಪುಟಗಳು</h2>
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
