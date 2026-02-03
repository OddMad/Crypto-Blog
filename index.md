---
layout: default
title: "Crypto Signals - BTC/ETH Live"
---

<style>
/* Центрирование */
.hero { text-align: center; margin: 30px 0; }
.live-prices { 
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); 
  color: white; 
  padding: 25px; 
  border-radius: 20px; 
  margin: 20px auto; 
  max-width: 600px;
  text-align: center;
}
.price-card { display: inline-block; background: rgba(255,255,255,0.2); padding: 20px; margin: 10px; border-radius: 15px; }
.change-up { color: #00ff88; } .change-down { color: #ff4757; }

/* Кнопка подписки ПОД ценами */
.subscribe-cta { 
  text-align: center; 
  margin: 20px auto; 
  display: block; 
  background: linear-gradient(45deg, #ff6b35, #f7931e); 
  color: white; 
  padding: 18px 40px; 
  text-decoration: none; 
  border-radius: 50px; 
  font-weight: bold; 
  font-size: 1.2em;
  max-width: 400px;
  box-shadow: 0 10px 30px rgba(255,107,53,0.4); 
}
.subscribe-cta:hover { transform: translateY(-3px); box-shadow: 0 15px 40px rgba(255,107,53,0.6); }

/* Таблица статей 2x2 */
.posts-grid { 
  display: grid; 
  grid-template-columns: 1fr 1fr; 
  gap: 20px; 
  margin: 40px 0; 
  max-width: 1200px; 
  margin-left: auto; 
  margin-right: auto;
}
.post-card { 
  border: 1px solid #e1e4e8; 
  border-radius: 12px; 
  padding: 20px; 
  height: 250px; 
  transition: all 0.3s;
}
.post-card:hover { transform: translateY(-5px); box-shadow: 0 15px 30px rgba(0,0,0,0.1); }
.post-title { font-size: 1.3em; margin: 0 0 10px 0; }

/* Галерея */
.gallery-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 15px; margin: 30px auto; max-width: 1200px; }
.gallery-grid img { width: 100%; height: 200px; object-fit: cover; border-radius: 12px; }
</style>

<!-- НАЗВАНИЕ БЛОГА ПО ЦЕНТРУ -->
<div class="hero">
  <h1 style="font-size: 3em; margin: 0; background: linear-gradient(45deg, #667eea, #764ba2); -webkit-background-clip: text; -webkit-text-fill-color: transparent;">
    💹 Crypto Signal Blog
  </h1>
  <p style="color: #666; font-size: 1.2em;">Live BTC/ETH Analysen & Signale</p>
</div>

<!-- ЖИВЫЕ ЦЕНЫ -->
<div class="live-prices">
  <h2>🪙 Live Kurse (Update alle 30 Sek.)</h2>
  <div>
    <div class="price-card">
      <div style="font-size: 2.5em;" id="btc-price">BTC: Laden...</div>
      <div id="btc-change" style="font-size: 1.3em;"></div>
    </div>
    <div class="price-card">
      <div style="font-size: 2.5em;" id="eth-price">ETH: Laden...</div>
      <div id="eth-change" style="font-size: 1.3em;"></div>
    </div>
  </div>
</div>

<!-- КНОПКА ПОДПИСКИ ПОД ЦЕНами -->
<a href="https://shop.fanxxx.click/register" class="subscribe-cta">
  🚀 VIP Signale per Email abonnieren
</a>

<!-- ГАЛЕРЕЯ 4x4 -->
<div style="text-align: center; margin: 40px 0;">
  <h2>📊 Markt Charts</h2>
  <div class="gallery-grid">
    <img src="https://images.cointelegraph.com/images/528_aHR0cHM6Ly9zMy5jb2ludGVsZWdyYXBoLmNvbS91cGxvYWRzLzIwMjYtMDIvMDE5YzIyZGYtNTQ2Yi03YWVjLTg1NjItMDI4NjNiZjAzYTFlLmpwZw==.jpg" alt="BTC Chart">
    <img src="https://images.cointelegraph.com/images/528_aHR0cHM6Ly9zMy5jb2ludGVsZWdyYXBoLmCvbS91cGxvYWRzLzIwMjYtMDIvMDE5YzIyYzktMTBjZi03ZTQ2LThjNjYtYWVkNzgwMTYxMTJjLmpwZw==.jpg" alt="ETF">
    <img src="https://images.cointelegraph.com/images/528_aHR0cHM6Ly9zMy5jb2ludGVsZWdyYXBoLmNvbS91cGxvYWRzLzIwMjYtMDIvMDE5YzIyOGMtNDVmMi03NzdjLTgxMTUtZDQxZTc4ODQxOGM4LmpwZw==.jpg" alt="Analysis">
    <img src="https://images.cointelegraph.com/images/528_aHR0cHM6Ly9zMy5jb2ludGVsZWdyYXBoLmNvbS91cGxvYWRzLzIwMjYtMDIvMDE5YzIyNjktYzNkZi03YWFkLTkwZmUtNTliNmY3MTVjYjA3LmpwZw==.jpg" alt="ETP">
  </div>
</div>

<!-- ТАБЛИЦА СТАТЕЙ 2x2 -->
<div style="max-width: 1200px; margin: 0 auto;">
  <h2 style="text-align: center;">📈 Neueste Signale</h2>
  <div class="posts-grid">
  {% for post in site.posts limit:4 %}
    <div class="post-card">
      <h3 class="post-title">
        <a href="{{ site.baseurl }}{{ post.url }}" style="color: #0366d6; text-decoration: none;">{{ post.title }}</a>
      </h3>
      <small>{{ post.date | date: "%d.%m.%Y %H:%M" }}</small>
      <p style="color: #666; margin: 15px 0;">{{ post.excerpt | strip_html | truncate: 120 }}</p>
      <a href="{{ site.baseurl }}{{ post.url }}" style="color: #ff6b35; font-weight: bold;">→ Signal lesen</a>
    </div>
  {% endfor %}
  </div>
</div>

<!-- Live цены JS -->
<script>
function updatePrices() {
  fetch('https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum&vs_currencies=usd&include_24hr_change=true')
    .then(r => r.json())
    .then(data => {
      document.getElementById('btc-price').innerHTML = `BTC: $${data.bitcoin.usd.toLocaleString()}`;
      document.getElementById('btc-change').innerHTML = `<span class="${data.bitcoin.usd_24h_change > 0 ? 'change-up' : 'change-down'}">${data.bitcoin.usd_24h_change > 0 ? '🟢' : '🔴'} ${data.bitcoin.usd_24h_change.toFixed(1)}%</span>`;
      
      document.getElementById('eth-price').innerHTML = `ETH: $${data.ethereum.usd.toLocaleString()}`;
      document.getElementById('eth-change').innerHTML = `<span class="${data.ethereum.usd_24h_change > 0 ? 'change-up' : 'change-down'}">${data.ethereum.usd_24h_change > 0 ? '🟢' : '🔴'} ${data.ethereum.usd_24h_change.toFixed(1)}%</span>`;
    })
    .catch(e => {
      document.getElementById('btc-price').innerHTML = 'BTC: Fehler';
      document.getElementById('eth-price').innerHTML = 'ETH: Fehler';
    });
}
updatePrices();
setInterval(updatePrices, 30000);
</script>
