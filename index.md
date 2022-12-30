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
4. [Google Cloudの料金アラート設定について](./gcp_cost_monitoring.md)
5. [Streamlitで文字検出アプリを作る](./ocr_app.md)
6. [後片付け](./clean_up.md)