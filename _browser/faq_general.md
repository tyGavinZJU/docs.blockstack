---
layout: usenew
description: Use a Blockstack ID with a DApp
permalink: /:collection/:path.html
---
# 用户常见问题(FAQ)
{:.no_toc}

这是一个面向去中心化应用程序用户的常见问题解答。一个全面的常见问题列表，涉及一般，技术，和应用程序挖掘问题[也可用]({{site.baseurl}}/faqs/allFAQS.html)。

* TOC
{:toc}

{% for faq in site.data.theFAQs.faqs %}
   {% if faq.category == 'appusers' %}
### {{ faq.question }}
{{ faq.answer }}
  {% endif %}
{% endfor %}
