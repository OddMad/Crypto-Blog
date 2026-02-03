---
layout: default
title: Crypto Blog - BTC/ETH Анализ
---

# 🪙 Последние сигналы BTC/ETH

<div class="posts-list">
{% for post in site.posts limit:10 %}
  <div class="post-preview">
    <h3>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </h3>
    <small>{{ post.date | date: "%d.%m.%Y %H:%M" }}</small>
    <p>{{ post.excerpt | strip_html | truncate: 120 }}</p>
    <a href="{{ post.url }}" class="read-more">Читать сигнал →</a>
  </div>
{% endfor %}
</div>

<div style="margin-top: 30px; padding: 20px; background: #f8f9fa; border-radius: 8px;">
  <h3>🎁 Получать сигналы на email</h3>
  <p><strong>Регистрация в магазине:</strong></p>
  <a href="https://shop.fanxxx.click/register" 
     style="background: #ff6b35; color: white; padding: 12px 24px; text-decoration: none; border-radius: 6px; font-weight: bold;">
    Зарегистрироваться → Получить доступ
  </a>
</div>
