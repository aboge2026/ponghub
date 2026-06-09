---
layout: default
title: PongHub 监控面板
---

## 网站状态监控

{% for service in site.data.services %}
### {{ service.name }}
{% for endpoint in service.endpoints %}
- **URL**: {{ endpoint.url }}
  - 状态: {% if endpoint.status == 200 %} ✅ 正常 {% else %} ❌ 异常 {% endif %}
  - 响应时间: {{ endpoint.response_time }}ms
  - 备案号检测: {% if endpoint.regex_matched %} ✅ 包含 {% else %} ❌ 未找到 {% endif %}
{% endfor %}
{% endfor %}

---
最后更新时间: {{ site.time | date: "%Y-%m-%d %H:%M:%S" }}
