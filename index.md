---
title: "トップページ"
date: "2022-10-06"
lastmod: "2022-10-21"
---

{% if page.lastmod %}
  {% assign lastmod = page.lastmod %}
{% else %}
  {% assign lastmod = page.date %}
{% endif %}

<span class="date">最終更新日:{{ lastmod }}</span>
## 目次

1. [Pythonの環境構築について](./python_environment.md)
2. [Streamlitで遊ぼう](./streamlit.md)
3. [Cloud Vision APIのセットアップ手順](./setup_gcp.md)
3. [Google Cloudのコスト管理について](./gcp_cost_monitoring.md)