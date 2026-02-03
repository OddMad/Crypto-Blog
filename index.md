---
layout: default
title: "Crypto Signal Blog"
---

<style>
/* Сброс навигации слева */
* { box-sizing: border-box; }
body { margin: 0; padding: 20px; max-width: 1200px; margin: auto; font-family: -apple-system, BlinkMacSystemFont, sans-serif; }
header nav { display: none !important; } /* Скрыть GitHub навигацию */

/* Остальные стили */
.hero { text-align: center; margin: 40px 0; }
.live-prices { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; padding: 30px; border-radius: 20px; margin: 20px auto; max-width: 700px; text-align: center; }
.price-card { display: inline-block; background: rgba(255,255,255,0.2); padding: 25px; margin: 15px; border-radius: 15px; min-width: 200px; }
.change-up { color: #00ff88; } .change-down { color: #ff4757; }
.subscribe-cta { display: block; margin: 25px auto; background: linear-gradient(45deg, #ff6b35, #f7931e); color: white; padding: 20px 50px; text-decoration: none; border-radius: 50px; font-weight: bold; font-size: 1.3em; max-width: 450px; box-shadow: 0 15px 35px rgba(255,107,53,0.4); }
.subscribe-cta:hover { transform: translateY(-5px); box-shadow: 0 20px 45px rgba(255,107,53,0.6); }
.posts-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 25px; margin: 50px auto; max-width: 1200px; }
.post-card { border: 2px solid #e1e4e8; border-radius: 15px; padding: 25px; height: 280px; transition: all 0.3s; background: #fafbfc; }
.post-card:hover { transform: translateY(-8px); border-color: #0366d6; box-shadow: 0 20px 40px rgba(0,0,0,0.15); }
.post-title { font-size: 1.4em; margin: 0 0 12px 0; line-height: 1.3; }
.post-title a { color: #0366d6; text-decoration: none; }
.post-title a:hover { text-decoration: underline; }
.gallery-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; margin: 40px auto; max-width: 1200px; }
.gallery-grid img { width: 100%; height: 220px; object-fit: cover; border-radius: 15px; box-shadow: 0 10px 30px rgba(0,0,0,0.2); }
h1 { font-size: 3.5em; margin: 0; background: linear-gradient(45deg, #667eea, #764ba2); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
h2 { text-align: center; color: #24292f; margin: 40px 0 20px 0; }
</style>

<div class="hero">
  <h1>💹 Crypto Signal Blog</h1>
  <p style="color: #666; font-size: 1.3em; margin-top: 10px;">Live BTC/ETH Analysen & Signale</p>
</div>

<div class="live-prices">
  <h2>🪙 Live Kurse (Update alle 30 Sek.)</h2>
  <div>
    <div class="price-card">
      <div style="font-size: 2.8em; font-weight: bold;" id="btc-price">BTC: Laden...</div>
      <div id="btc-change" style="font-size: 1.4em;"></div>
    </div>
    <div class="price-card">
      <div style="font-size: 2.8em; font-weight: bold;" id="eth-price">ETH: Laden...</div>
      <div id="eth-change" style="font-size: 1.4em;"></div>
    </div>
  </div>
</div>

<a href="https://shop.fanxxx.click/register" class="subscribe-cta">
  🚀 VIP Signale per Email abonnieren
</a>

<div style="text-align: center; margin: 50px 0;">
  <h2>📊 Markt Charts</h2>
  <div class="gallery-grid">
    {% assign images = 'btc-chart.jpg,eth-chart.jpg,market-overview.jpg,etf-flows.jpg' | split: ',' %}
    {% for image in images %}
      <img src="/images/{{ image }}" alt="{{ image }}" onerror="this.src='https://via.placeholder.com/300x200/667eea/ffffff?text={{ image | replace: '-', ' ' }}'">
    {% endfor %}
  </div>
</div>

<div>
  <h2>📈 Neueste Signale (2x2 Tabelle)</h2>
  <div class="posts-grid">
    {% for post in site.posts limit:4 %}
    <div class="post-card">
      <h3 class="post-title">
        <a href="{{ post.url | prepend: site.baseurl | append: '.html' }}">{{ post.title }}</a>
      </h3>
      <small style="color: #666; display: block; margin-bottom: 12px;">{{ post.date | date: "%d.%m.%Y %H:%M" }}</small>
      <p style="color: #666; margin: 0 0 20px 0; line-height: 1.5;">{{ post.excerpt | strip_html | truncate: 140 }}</p>
      <a href="{{ post.url | prepend: site.baseurl | append: '.html' }}" style="color: #ff6b35; font-weight: bold; font-size: 1.1em;">→ Signal lesen</a>
    </div>
    {% endfor %}
  </div>
</div>

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
    .catch(() => {
      document.getElementById('btc-price').innerHTML = 'BTC: Fehler';
      document.getElementById('eth-price').innerHTML = 'ETH: Fehler';
    });
}
updatePrices();
setInterval(updatePrices, 30000);
</script>
