---
layout: default
title: Crypto Signals - BTC/ETH Live
---

<style>
.live-prices { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; padding: 20px; border-radius: 15px; text-align: center; margin: 20px 0; }
.price-card { display: inline-block; background: rgba(255,255,255,0.2); padding: 15px; margin: 10px; border-radius: 10px; backdrop-filter: blur(10px); }
.change-up { color: #00ff88; } .change-down { color: #ff4757; }
.news-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin: 20px 0; }
.news-item { border: 1px solid #e1e4e8; border-radius: 10px; overflow: hidden; transition: transform 0.3s; }
.news-item:hover { transform: translateY(-5px); box-shadow: 0 10px 25px rgba(0,0,0,0.1); }
.news-title { font-size: 1.1em; font-weight: bold; padding: 15px; margin: 0; }
.news-excerpt { padding: 0 15px 15px; color: #666; }
.gallery { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 15px; margin: 30px 0; }
.gallery img { width: 100%; height: 200px; object-fit: cover; border-radius: 10px; transition: transform 0.3s; }
.gallery img:hover { transform: scale(1.05); }
.cta-button { background: linear-gradient(45deg, #ff6b35, #f7931e); color: white; padding: 15px 30px; text-decoration: none; border-radius: 50px; font-weight: bold; display: inline-block; margin: 20px 0; box-shadow: 0 10px 30px rgba(255,107,53,0.4); }
.cta-button:hover { transform: translateY(-3px); box-shadow: 0 15px 40px rgba(255,107,53,0.6); }
</style>

<div class="live-prices">
  <h2>🪙 Live Цены (обновление каждые 30 сек)</h2>
  <div>
    <div class="price-card">
      <div style="font-size: 2em; font-weight: bold;" id="btc-price">BTC: Загрузка...</div>
      <div id="btc-change" style="font-size: 1.2em;"></div>
    </div>
    <div class="price-card">
      <div style="font-size: 2em; font-weight: bold;" id="eth-price">ETH: Загрузка...</div>
      <div id="eth-change" style="font-size: 1.2em;"></div>
    </div>
  </div>
</div>

<div class="gallery">
  <img src="https://images.cointelegraph.com/images/528_aHR0cHM6Ly9zMy5jb2ludGVsZWdyYXBoLmNvbS91cGxvYWRzLzIwMjYtMDIvMDE5YzIyZGYtNTQ2Yi03YWVjLTg1NjItMDI4NjNiZjAzYTFlLmpwZw==.jpg" alt="BTC Chart">
  <img src="https://images.cointelegraph.com/images/528_aHR0cHM6Ly9zMy5jb2ludGVsZWdyYXBoLmNvbS91cGxvYWRzLzIwMjYtMDIvMDE5YzIyYzktMTBjZi03ZTQ2LThjNjYtYWVkNzgwMTYxMTJjLmpwZw==.jpg" alt="ETF Flows">
  <img src="https://images.cointelegraph.com/images/528_aHR0cHM6Ly9zMy5jb2ludGVsZWdyYXBoLmNvbS91cGxvYWRzLzIwMjYtMDIvMDE5YzIyOGMtNDVmMi03NzdjLTgxMTUtZDQxZTc4ODQxOGM4LmpwZw==.jpg" alt="Market Analysis">
  <img src="https://images.cointelegraph.com/images/528_aHR0cHM6Ly9zMy5jb2ludGVsZWdyYXBoLmCvbS91cGxvYWRzLzIwMjYtMDIvMDE5YzIyNjktYzNkZi03YWFkLTkwZmUtNTliNmY3MTVjYjA3LmpwZw==.jpg" alt="Crypto ETP">
</div>

<h2>📈 Последние сигналы</h2>
<div class="posts-list">
{% for post in site.posts limit:5 %}
  <div class="post-preview">
    <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
    <small>{{ post.date | date: "%d.%m.%Y %H:%M" }}</small>
    <p>{{ post.excerpt | strip_html | truncate: 100 }}</p>
    <a href="{{ post.url }}" class="read-more">→ Сигнал</a>
  </div>
{% endfor %}
</div>

<h2>📰 Top Новости BTC (CoinTelegraph)</h2>
<div class="news-grid">
{% for item in site.data.news limit:6 %}
  <div class="news-item">
    <div class="news-title">
      <a href="{{ item.url }}" target="_blank">{{ item.title | truncate: 60 }}</a>
    </div>
    <div class="news-excerpt">{{ item.description | strip_html | truncate: 120 }}</div>
  </div>
{% endfor %}
</div>

<a href="https://shop.fanxxx.click/register" class="cta-button">🚀 Получить VIP Сигналы на Email</a>

<script>
function updatePrices() {
  fetch('https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum&vs_currencies=usd&include_24hr_change=true')
    .then(r => r.json())
    .then(data => {
      // BTC
      const btcPrice = data.bitcoin.usd.toLocaleString();
      const btcChange = data.bitcoin.usd_24h_change.toFixed(1);
      document.getElementById('btc-price').innerHTML = `BTC: $${btcPrice}`;
      document.getElementById('btc-change').innerHTML = 
        `<span class="${btcChange > 0 ? 'change-up' : 'change-down'}">${btcChange > 0 ? '🟢' : '🔴'} ${btcChange}%</span>`;
      
      // ETH
      const ethPrice = data.ethereum.usd.toLocaleString();
      const ethChange = data.ethereum.usd_24h_change.toFixed(1);
      document.getElementById('eth-price').innerHTML = `ETH: $${ethPrice}`;
      document.getElementById('eth-change').innerHTML = 
        `<span class="${ethChange > 0 ? 'change-up' : 'change-down'}">${ethChange > 0 ? '🟢' : '🔴'} ${ethChange}%</span>`;
    })
    .catch(e => {
      document.getElementById('btc-price').innerHTML = 'BTC: API Error';
      document.getElementById('eth-price').innerHTML = 'ETH: API Error';
    });
}

// Обновление каждые 30 секунд
updatePrices();
setInterval(updatePrices, 30000);
</script>
