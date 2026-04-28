<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
  @import url('https://fonts.googleapis.com/css2?family=Rajdhani:wght@400;600;700&family=Nunito:wght@400;600;700;800&display=swap');

  * { margin: 0; padding: 0; box-sizing: border-box; }

  :root {
    --red: #E8212B;
    --dark: #111111;
    --darker: #0a0a0a;
    --card-bg: #1a1a1a;
    --surface: #222222;
    --muted: #888;
    --text: #f0f0f0;
    --accent: #E8212B;
  }

  body {
    background: var(--dark);
    color: var(--text);
    font-family: 'Nunito', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }
  /* NAV */
  nav {
    background: #0d0d0d;
    border-bottom: 2px solid var(--red);
    padding: 0 32px;
    display: flex;
    align-items: center;
    gap: 0;
    height: 52px;
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .nav-logo {
    font-family: 'Rajdhani', sans-serif;
    font-size: 20px;
    font-weight: 700;
    color: var(--text);
    margin-right: 28px;
    white-space: nowrap;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .nav-logo span { color: var(--red); }
  .nav-links { display: flex; gap: 0; flex: 1; }
  .nav-links a {
    color: #bbb;
    text-decoration: none;
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    padding: 0 16px;
    height: 52px;
    display: flex;
    align-items: center;
    transition: color 0.2s, background 0.2s;
    cursor: pointer;
  }
  .nav-links a:hover, .nav-links a.active { color: #fff; background: rgba(232,33,43,0.15); }
  .nav-right { display: flex; align-items: center; gap: 12px; margin-left: auto; }
  .nav-search {
    background: #222;
    border: 1px solid #333;
    color: #eee;
    padding: 6px 14px;
    border-radius: 4px;
    font-size: 13px;
    font-family: 'Nunito', sans-serif;
    width: 200px;
    outline: none;
  }
  .nav-search:focus { border-color: var(--red); }
  .nav-icon {
    width: 32px; height: 32px;
    background: #2a2a2a;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    cursor: pointer;
    font-size: 14px;
    color: #bbb;
    transition: background 0.2s;
  }
  .nav-icon:hover { background: #333; color: #fff; }

  /* PAGES */
  .page { display: none; }
  .page.active { display: block; }

  /* === HOME PAGE === */
  /* Banner */
  .banner {
    position: relative;
    height: 220px;
    background: linear-gradient(135deg, #1a0505 0%, #2d0a0a 50%, #1a0505 100%);
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    border-bottom: 1px solid #333;
  }
  .banner-inner {
    text-align: center;
    z-index: 2;
    position: relative;
  }
  .banner-inner .event-label {
    font-size: 11px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: #999;
    margin-bottom: 8px;
  }
  .banner-title {
    font-family: 'Rajdhani', sans-serif;
    font-size: 42px;
    font-weight: 700;
    line-height: 1;
    color: #fff;
    letter-spacing: 0.05em;
  }
  .banner-title .tga { font-size: 28px; display: block; color: #ddd; letter-spacing: 0.2em; }
  .banner-title .date { font-size: 16px; color: #aaa; font-family: 'Nunito', sans-serif; font-weight: 600; margin-top: 6px; display: block; }
  .banner-bg-lines {
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    background: repeating-linear-gradient(45deg, transparent, transparent 40px, rgba(232,33,43,0.04) 40px, rgba(232,33,43,0.04) 41px);
  }
  .banner-btn {
    position: absolute;
    left: 16px; top: 50%; transform: translateY(-50%);
    background: rgba(255,255,255,0.08);
    border: none; color: #fff; width: 36px; height: 36px;
    border-radius: 4px; cursor: pointer; font-size: 18px;
    display: flex; align-items: center; justify-content: center;
    z-index: 3;
  }
  .banner-btn.right { left: auto; right: 16px; }
  .banner-btn:hover { background: rgba(255,255,255,0.15); }

  /* Sections */
  .home-content { padding: 0 0 48px; }
  .section { padding: 28px 32px 8px; }
  .section-header {
    display: flex; align-items: center; gap: 10px;
    margin-bottom: 16px;
  }
  .section-star { color: var(--red); font-size: 18px; }
  .section-title {
    font-family: 'Rajdhani', sans-serif;
    font-size: 18px; font-weight: 700;
    letter-spacing: 0.04em; color: #fff;
    text-transform: uppercase;
  }
  .section-sub { font-size: 12px; color: #888; margin-left: 4px; font-weight: 600; }

  .games-row { display: flex; gap: 12px; overflow-x: auto; padding-bottom: 8px; }
  .games-row::-webkit-scrollbar { height: 4px; }
  .games-row::-webkit-scrollbar-track { background: #1a1a1a; }
  .games-row::-webkit-scrollbar-thumb { background: var(--red); border-radius: 2px; }

  .game-card {
    flex: 0 0 140px;
    cursor: pointer;
    transition: transform 0.2s, filter 0.2s;
    position: relative;
  }
  .game-card:hover { transform: translateY(-4px) scale(1.03); }
  .game-card img {
    width: 140px; height: 190px;
    object-fit: cover;
    border-radius: 6px;
    display: block;
    background: #2a2a2a;
  }
  .game-card .placeholder-cover {
    width: 140px; height: 190px;
    background: #2a2a2a;
    border-radius: 6px;
    display: flex; align-items: center; justify-content: center;
    font-size: 11px; color: #555; font-weight: 700;
    letter-spacing: 0.05em; text-align: center; padding: 12px;
    border: 1px dashed #333;
  }
  .game-card .card-name {
    font-size: 12px; color: #ccc; margin-top: 6px;
    font-weight: 700; white-space: nowrap; overflow: hidden; text-overflow: ellipsis;
  }
  .coming-soon-card {
    flex: 0 0 140px;
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    gap: 8px;
  }
  .coming-soon-box {
    width: 140px; height: 190px;
    background: #222;
    border: 1px dashed #444;
    border-radius: 6px;
    display: flex; align-items: center; justify-content: center;
    font-size: 11px; color: #555; font-weight: 700;
    letter-spacing: 0.08em; text-transform: uppercase;
  }

  /* Category sections */
  .category-badge {
    display: inline-flex; align-items: center; gap: 6px;
    background: var(--red);
    color: #fff;
    padding: 2px 10px 2px 6px;
    border-radius: 4px;
    font-size: 11px; font-weight: 800; letter-spacing: 0.06em;
    text-transform: uppercase;
  }

  /* Saved section */
  .saved-section { padding: 20px 32px; }
  .saved-box {
    background: #1a1a1a;
    border: 1px dashed #333;
    border-radius: 8px;
    width: 60px; height: 60px;
    display: flex; align-items: center; justify-content: center;
    cursor: pointer; color: #555; font-size: 22px;
    transition: border-color 0.2s, color 0.2s;
  }
  .saved-box:hover { border-color: var(--red); color: var(--red); }

  /* CTA */
  .cta-section {
    background: linear-gradient(135deg, #1a0505, #0d0d0d);
    border-top: 1px solid #2a2a2a;
    padding: 36px 32px;
    text-align: center;
    margin-top: 16px;
  }
  .cta-title { font-family: 'Rajdhani', sans-serif; font-size: 24px; font-weight: 700; color: #fff; margin-bottom: 6px; }
  .cta-sub { font-size: 14px; color: #888; margin-bottom: 20px; }
  .cta-sub span { color: var(--red); font-weight: 700; }
  .cta-buttons { display: flex; gap: 12px; justify-content: center; }
  .btn-primary {
    background: var(--red); color: #fff;
    border: none; padding: 10px 24px;
    border-radius: 4px; font-family: 'Nunito', sans-serif;
    font-size: 13px; font-weight: 700;
    cursor: pointer; transition: background 0.2s;
  }
  .btn-primary:hover { background: #c01822; }
  .btn-outline {
    background: transparent; color: #ccc;
    border: 1px solid #444; padding: 10px 24px;
    border-radius: 4px; font-family: 'Nunito', sans-serif;
    font-size: 13px; font-weight: 700;
    cursor: pointer; transition: border-color 0.2s, color 0.2s;
  }
  .btn-outline:hover { border-color: #888; color: #fff; }

  /* Footer */
  footer {
    background: #0a0a0a;
    border-top: 1px solid #222;
    padding: 24px 32px;
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
  }
  footer .footer-links { display: flex; gap: 16px; flex-wrap: wrap; }
  footer .footer-links a { font-size: 12px; color: #666; text-decoration: none; cursor: pointer; }
  footer .footer-links a:hover { color: #aaa; }
  footer .footer-logo { font-family: 'Rajdhani', sans-serif; font-size: 18px; font-weight: 700; color: #555; }
  footer .footer-logo span { color: var(--red); }

  /* === DETAIL PAGE === */
  .detail-page {
    min-height: calc(100vh - 52px);
    background: var(--darker);
    padding: 40px 48px;
    display: none;
  }
  .detail-page.active { display: flex; }
  .detail-layout { display: flex; gap: 48px; max-width: 900px; margin: 0 auto; }
  .detail-cover {
    flex: 0 0 300px;
  }
  .detail-cover img {
    width: 300px; height: 400px;
    object-fit: cover;
    border-radius: 10px;
    display: block;
    box-shadow: 0 8px 40px rgba(0,0,0,0.7);
  }
  .detail-cover .placeholder-img {
    width: 300px; height: 400px;
    background: #2a2a2a;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 14px; color: #555; font-weight: 700;
  }
  .detail-info { flex: 1; padding-top: 8px; }
  .detail-title {
    font-family: 'Rajdhani', sans-serif;
    font-size: 38px; font-weight: 700;
    line-height: 1.1; color: #fff;
    text-transform: uppercase;
    letter-spacing: 0.04em;
    margin-bottom: 20px;
  }
  .detail-about {
    font-size: 14px; line-height: 1.65; color: #ccc;
    margin-bottom: 20px; font-weight: 400;
  }
  .detail-about strong { color: #aaa; font-size: 13px; font-weight: 700; text-transform: uppercase; letter-spacing: 0.05em; margin-right: 4px; }
  .detail-meta { margin-bottom: 8px; font-size: 14px; color: #bbb; line-height: 1.8; }
  .detail-meta strong { color: #999; font-weight: 700; }
  .detail-meta a { color: #5a9fd4; text-decoration: none; font-weight: 700; }
  .detail-meta a:hover { text-decoration: underline; }
  .detail-price { font-size: 14px; color: #bbb; margin-top: 2px; margin-bottom: 24px; }
  .detail-price strong { font-weight: 700; color: #999; }
  .detail-price .price-val { color: #fff; font-size: 16px; font-weight: 800; }

  .similares-title {
    font-family: 'Rajdhani', sans-serif;
    font-size: 16px; font-weight: 700;
    letter-spacing: 0.1em; color: #fff;
    text-transform: uppercase;
    margin-bottom: 12px;
  }
  .similares-row { display: flex; gap: 10px; }
  .sim-card {
    width: 90px; height: 120px;
    border-radius: 6px;
    cursor: pointer;
    overflow: hidden;
    position: relative;
    transition: transform 0.2s;
  }
  .sim-card:hover { transform: scale(1.05); }
  .sim-card img { width: 100%; height: 100%; object-fit: cover; display: block; }
  .sim-coming {
    width: 90px; height: 120px;
    border-radius: 6px;
    background: #2a2a2a;
    border: 1px dashed #444;
    display: flex; align-items: center; justify-content: center;
    font-size: 9px; color: #555; font-weight: 800;
    letter-spacing: 0.05em; text-transform: uppercase;
  }

  .back-btn {
    display: inline-flex; align-items: center; gap: 8px;
    background: transparent;
    border: 1px solid #444;
    color: #ccc;
    padding: 8px 18px;
    border-radius: 4px;
    font-family: 'Nunito', sans-serif;
    font-size: 13px; font-weight: 700;
    cursor: pointer;
    margin-top: 28px;
    transition: border-color 0.2s, color 0.2s;
    float: right;
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }
  .back-btn:hover { border-color: #888; color: #fff; }

  /* divider */
  .detail-divider { width: 100%; height: 1px; background: #2a2a2a; margin: 16px 0; }

  /* Genre tags */
  .genre-tags { display: flex; gap: 6px; flex-wrap: wrap; margin-bottom: 16px; }
  .genre-tag {
    background: #2a2a2a; color: #aaa;
    padding: 3px 10px; border-radius: 4px;
    font-size: 11px; font-weight: 700;
    letter-spacing: 0.04em; border: 1px solid #333;
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">Jogos <span>Indies</span> 🎮</div>
  <div class="nav-links">
    <a class="active" onclick="showPage('home')">Home</a>
    <a onclick="showPage('home')">Biblioteca</a>
    <a onclick="showPage('home')">Categorias</a>
    <a onclick="showPage('home')">Favoritos</a>
  </div>
  <div class="nav-right">
    <input type="text" class="nav-search" placeholder="Buscar um jogo específico..." />
    <div class="nav-icon">🔔</div>
    <div class="nav-icon">👤</div>
  </div>
</nav>

<!-- HOME PAGE -->
<div id="page-home" class="page active">
  <!-- Banner -->
  <div class="banner">
    <div class="banner-bg-lines"></div>
    <button class="banner-btn">&#8249;</button>
    <div class="banner-inner">
      <div class="event-label">Eventos no Mundo dos Games</div>
      <div class="banner-title">
        <span class="tga">THE GAME AWARDS</span>
        <span class="date">DECEMBER 10</span>
      </div>
    </div>
    <button class="banner-btn right">&#8250;</button>
  </div>

  <div class="home-content">

    <!-- Populares -->
    <div class="section">
      <div class="section-header">
        <span class="section-star">★</span>
        <span class="section-title">Os INDIES mais populares do MOMENTO!</span>
      </div>
      <div class="games-row">
        <div class="game-card" onclick="showDetail('silksong')">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #1a0808, #3d1010); color: #c44; font-size:13px; font-weight:800;">HOLLOW KNIGHT<br>SILKSONG</div>
          <div class="card-name">HK: Silksong</div>
        </div>
        <div class="game-card" onclick="showDetail('terraria')">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #0a1a08, #1a3d10); color: #4a4; font-size:13px; font-weight:800;">TERRARIA</div>
          <div class="card-name">Terraria</div>
        </div>
        <div class="game-card" onclick="showDetail('cuphead')">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #1a100a, #3d2a10); color: #c84; font-size:13px; font-weight:800;">CUPHEAD</div>
          <div class="card-name">Cuphead</div>
        </div>
        <div class="game-card" onclick="showDetail('celeste')">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #0a0f1a, #10203d); color: #48c; font-size:13px; font-weight:800;">CELESTE</div>
          <div class="card-name">Celeste</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
      </div>
    </div>

    <!-- Jogos Salvos -->
    <div class="saved-section">
      <div class="section-header">
        <span style="color:var(--red); font-size:16px;">★</span>
        <span class="section-title" style="font-size:14px; color:#ccc;">Jogos Salvos – Seus jogos FAVORITOS estão AQUI!</span>
      </div>
      <div style="display:flex; gap:10px;">
        <div class="saved-box">+</div>
      </div>
    </div>

    <!-- Indie Casual -->
    <div class="section">
      <div class="section-header">
        <div class="category-badge"><span>😊</span> Indie Casual</div>
        <span class="section-sub">– Jogos para Relaxar e Passar o Tempo!</span>
      </div>
      <div class="games-row">
        <div class="game-card" onclick="showDetail('stardew')">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #0d1a08, #1a3a12); color: #6c4; font-size:13px; font-weight:800;">STARDEW VALLEY</div>
          <div class="card-name">Stardew Valley</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
      </div>
    </div>

    <!-- Indie Puzzle -->
    <div class="section">
      <div class="section-header">
        <div class="category-badge" style="background:#7c3af7;"><span>🧩</span> Indie Puzzle</div>
        <span class="section-sub">– Jogos para Desafiar a sua Mente!</span>
      </div>
      <div class="games-row">
        <div class="game-card" onclick="showDetail('demonbluff')">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #0a0a1a, #1a1040); color: #88c; font-size:13px; font-weight:800;">DEMON BLUFF</div>
          <div class="card-name">Demon Bluff</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
      </div>
    </div>

    <!-- Indie RPG -->
    <div class="section">
      <div class="section-header">
        <div class="category-badge" style="background:#1a6e3d;"><span>⚔️</span> Indie RPG</div>
        <span class="section-sub">– Jogos de Desafios e Turnos!</span>
      </div>
      <div class="games-row">
        <div class="game-card" onclick="showDetail('deltarune')">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #050510, #0d0d2a); color: #66a; font-size:13px; font-weight:800;">DELTARUNE</div>
          <div class="card-name">Deltarune</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
      </div>
    </div>

    <!-- Indie Pixel Art -->
    <div class="section">
      <div class="section-header">
        <div class="category-badge" style="background:#c4731a;"><span>🎨</span> Indie Pixel Art</div>
        <span class="section-sub">– Jogos no Estilo que muitos Amam!</span>
      </div>
      <div class="games-row">
        <div class="game-card" onclick="showDetail('shovel')">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #0a1420, #101e30); color: #4a8; font-size:13px; font-weight:800;">SHOVEL KNIGHT</div>
          <div class="card-name">Shovel Knight</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
      </div>
    </div>

    <!-- Indie Multiplayer -->
    <div class="section">
      <div class="section-header">
        <div class="category-badge" style="background:#1a4a8a;"><span>👥</span> Indie Multiplayer</div>
        <span class="section-sub">– Jogos para Jogar com os Amigos!</span>
      </div>
      <div class="games-row">
        <div class="game-card" onclick="showDetail('peak')">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #081420, #102040); color: #46a; font-size:13px; font-weight:800;">PEAK</div>
          <div class="card-name">Peak</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
      </div>
    </div>

    <!-- Indie Brasileiro -->
    <div class="section">
      <div class="section-header">
        <div class="category-badge" style="background:#1f7a1f;"><span>🇧🇷</span> Indie Brasileiro</div>
        <span class="section-sub">– Venha conhecer os Nacionais!</span>
      </div>
      <div class="games-row">
        <div class="game-card">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #1a0808, #3a1010); color: #c44; font-size:11px; font-weight:800;">CHROMA SQUAD</div>
          <div class="card-name">Chroma Squad</div>
        </div>
        <div class="game-card">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #0a100a, #1a2a1a); color: #4a8; font-size:11px; font-weight:800;">ENIGMA DO MEDO</div>
          <div class="card-name">Enigma do Medo</div>
        </div>
        <div class="game-card">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #0a0f1a, #101830); color: #68c; font-size:11px; font-weight:800;">MOONLEAP</div>
          <div class="card-name">Moonleap</div>
        </div>
        <div class="game-card">
          <div class="placeholder-cover" style="background: linear-gradient(145deg, #1a1008, #3a2a08); color: #c84; font-size:11px; font-weight:800;">MULLET MADJACK</div>
          <div class="card-name">Mullet MadJack</div>
        </div>
        <div class="coming-soon-card">
          <div class="coming-soon-box">EM BREVE</div>
        </div>
      </div>
    </div>

    <!-- CTA -->
    <div class="cta-section">
      <div class="cta-title">Faça um perfil para ter uma <span style="color:var(--red);">MELHOR EXPERIÊNCIA!</span></div>
      <div class="cta-sub">Salve seus jogos favoritos e tenha uma experiência personalizada!</div>
      <div class="cta-buttons">
        <button class="btn-primary">Primeira vez aqui? Se CADASTRE!</button>
        <button class="btn-outline">Já tem um perfil? Faça o LOGIN!</button>
      </div>
    </div>

  </div>

  <!-- Footer -->
  <footer>
    <div>
      <div class="footer-links">
        <a>Home</a>
        <a>Biblioteca</a>
        <a>Categorias</a>
        <a>Favoritos</a>
      </div>
      <div style="margin-top:8px; font-size:11px; color:#444;">© 2024 Jogos Indies. Todos os direitos reservados.</div>
    </div>
    <div class="footer-logo">Jogos <span>Indies</span></div>
  </footer>
</div>

<!-- DETAIL PAGE: HOLLOW KNIGHT -->
<div id="page-detail-hollow" class="detail-page">
  <div class="detail-layout">
    <div class="detail-cover">
      <div class="placeholder-img" style="background: linear-gradient(160deg, #050d1a 0%, #0d1e35 40%, #081428 100%); flex-direction:column; gap:8px;">
        <span style="font-family:'Rajdhani',sans-serif; font-size:26px; font-weight:700; color:#a8d8f0; text-align:center; line-height:1.2; letter-spacing:0.1em;">HOLLOW<br>KNIGHT</span>
        <span style="font-size:30px;">🦋</span>
      </div>
    </div>
    <div class="detail-info">
      <div class="detail-title">HOLLOW KNIGHT</div>
      <div class="detail-about">
        <strong>Sobre:</strong>
        Explore um vasto reino esquecido de insetos e heróis. Desvende os mistérios mais profundos de um antigo reino caído através de uma aventura classicamente elaborada.
      </div>
      <div class="detail-divider"></div>
      <div class="genre-tags">
        <span class="genre-tag">Ação</span>
        <span class="genre-tag">Aventura</span>
        <span class="genre-tag">Metroidvania</span>
        <span class="genre-tag">Indie</span>
      </div>
      <div class="detail-meta"><strong>Gênero:</strong> Ação, Aventura, Indie.</div>
      <div class="detail-meta"><strong>Desenvolvedor:</strong> <a href="#">Team Cherry</a>.</div>
      <div class="detail-meta"><strong>Distribuidora:</strong> <a href="#">Team Cherry</a>.</div>
      <div class="detail-meta"><strong>Série:</strong> <strong>Hollow Knight.</strong></div>
      <div class="detail-meta"><strong>Data de lançamento:</strong> 24/02/2017</div>
      <div class="detail-divider"></div>
      <div class="detail-meta"><strong>Onde Jogar:</strong> <a href="#">Steam</a>.</div>
      <div class="detail-price"><strong>Preço:</strong> <span class="price-val">R$ 19,99</span></div>
      <div class="similares-title">SIMILARES:</div>
      <div class="similares-row">
        <div class="sim-card" onclick="showDetail('silksong')">
          <div class="placeholder-img" style="background:linear-gradient(145deg,#2a0808,#5a1010); display:flex; align-items:center; justify-content:center; height:120px; font-family:'Rajdhani',sans-serif; font-size:9px; color:#c44; font-weight:800; text-align:center; padding:6px; line-height:1.2;">HOLLOW KNIGHT<br>SILKSONG</div>
        </div>
        <div class="sim-coming">EM BREVE</div>
      </div>
      <button class="back-btn" onclick="showPage('home')">&#8249; VOLTAR</button>
    </div>
  </div>
</div>

<!-- DETAIL PAGE: SILKSONG -->
<div id="page-detail-silksong" class="detail-page">
  <div class="detail-layout">
    <div class="detail-cover">
      <div class="placeholder-img" style="background: linear-gradient(160deg, #1a0505 0%, #3d0d0d 50%, #2a0808 100%); flex-direction:column; gap:8px;">
        <span style="font-family:'Rajdhani',sans-serif; font-size:20px; font-weight:700; color:#f0a0a0; text-align:center; line-height:1.2; letter-spacing:0.08em;">HOLLOW KNIGHT</span>
        <span style="font-family:'Rajdhani',sans-serif; font-size:30px; font-weight:700; color:#fff; text-align:center; letter-spacing:0.05em;">SILKSONG</span>
        <span style="font-size:24px;">⚔️</span>
      </div>
    </div>
    <div class="detail-info">
      <div class="detail-title">HOLLOW KNIGHT: SILKSONG</div>
      <div class="detail-about">
        <strong>Sobre:</strong>
        Descubra um reino vasto e amaldiçoado em Hollow Knight: Silksong! Explore, lute e sobreviva enquanto você ascende ao pico de uma terra governada pela seda e por canções.
      </div>
      <div class="detail-divider"></div>
      <div class="genre-tags">
        <span class="genre-tag">Ação</span>
        <span class="genre-tag">Aventura</span>
        <span class="genre-tag">Indie</span>
      </div>
      <div class="detail-meta"><strong>Gênero:</strong> Ação, Aventura, Indie.</div>
      <div class="detail-meta"><strong>Desenvolvedor:</strong> <a href="#">Team Cherry</a>.</div>
      <div class="detail-meta"><strong>Distribuidora:</strong> <a href="#">Team Cherry</a>.</div>
      <div class="detail-meta"><strong>Série:</strong> <strong>Hollow Knight.</strong></div>
      <div class="detail-meta"><strong>Data de lançamento:</strong> 04/09/2025</div>
      <div class="detail-divider"></div>
      <div class="detail-meta"><strong>Onde Jogar:</strong> <a href="#">Steam</a>.</div>
      <div class="detail-price"><strong>Preço:</strong> <span class="price-val">R$ 59,99</span></div>
      <div class="similares-title">SIMILARES:</div>
      <div class="similares-row">
        <div class="sim-card" onclick="showDetail('hollow')">
          <div class="placeholder-img" style="background:linear-gradient(145deg,#050d1a,#0d1e35); display:flex; align-items:center; justify-content:center; height:120px; font-family:'Rajdhani',sans-serif; font-size:9px; color:#a8d8f0; font-weight:800; text-align:center; padding:6px; line-height:1.2;">HOLLOW KNIGHT</div>
        </div>
        <div class="sim-coming">EM BREVE</div>
      </div>
      <button class="back-btn" onclick="showPage('home')">&#8249; VOLTAR</button>
    </div>
  </div>
</div>

<!-- GENERIC DETAIL PAGES -->
<div id="page-detail-generic" class="detail-page">
  <div class="detail-layout">
    <div class="detail-cover">
      <div class="placeholder-img" id="generic-cover" style="background: linear-gradient(160deg, #101010 0%, #1a1a1a 100%); flex-direction:column; gap:8px;">
        <span id="generic-icon" style="font-size:40px;">🎮</span>
        <span id="generic-cover-title" style="font-family:'Rajdhani',sans-serif; font-size:22px; font-weight:700; color:#ccc; text-align:center; padding:0 16px; line-height:1.2;"></span>
      </div>
    </div>
    <div class="detail-info">
      <div class="detail-title" id="generic-title"></div>
      <div class="detail-about">
        <strong>Sobre:</strong> <span id="generic-about"></span>
      </div>
      <div class="detail-divider"></div>
      <div class="genre-tags" id="generic-genres"></div>
      <div class="detail-meta"><strong>Gênero:</strong> <span id="generic-genre-text"></span></div>
      <div class="detail-meta"><strong>Desenvolvedor:</strong> <span id="generic-dev"></span></div>
      <div class="detail-meta"><strong>Data de lançamento:</strong> <span id="generic-date"></span></div>
      <div class="detail-divider"></div>
      <div class="detail-meta"><strong>Onde Jogar:</strong> <a href="#">Steam</a>.</div>
      <div class="detail-price"><strong>Preço:</strong> <span class="price-val" id="generic-price"></span></div>
      <div class="similares-title">SIMILARES:</div>
      <div class="similares-row">
        <div class="sim-coming">EM BREVE</div>
        <div class="sim-coming">EM BREVE</div>
      </div>
      <button class="back-btn" onclick="showPage('home')">&#8249; VOLTAR</button>
    </div>
  </div>
</div>

<script>
const games = {
  terraria: {
    title: 'TERRARIA',
    about: 'Cave a fundo, construa monumentos épicos, lute contra criaturas lendárias e descubra tesouros escondidos neste sandbox de ação e aventura em 2D.',
    genre: 'Ação, Aventura, Sandbox',
    dev: 'Re-Logic',
    date: '16/05/2011',
    price: 'R$ 19,99',
    icon: '⛏️',
    color: 'linear-gradient(160deg, #0a1a08, #1a3d10)',
    textColor: '#6c4'
  },
  cuphead: {
    title: 'CUPHEAD',
    about: 'Um jogo de ação e tiro com corrida de plataforma clássica com foco em combates de chefes. Inspirado nas animações da década de 1930.',
    genre: 'Ação, Plataforma, Indie',
    dev: 'Studio MDHR',
    date: '29/09/2017',
    price: 'R$ 59,99',
    icon: '☕',
    color: 'linear-gradient(160deg, #1a100a, #3d2a10)',
    textColor: '#c84'
  },
  celeste: {
    title: 'CELESTE',
    about: 'Ajude Madeline a sobreviver em sua jornada interior rumo ao topo da Montanha Celeste, em um jogo de plataforma preciso e apaixonante.',
    genre: 'Plataforma, Indie, Aventura',
    dev: 'Extremely OK Games',
    date: '25/01/2018',
    price: 'R$ 47,99',
    icon: '🏔️',
    color: 'linear-gradient(160deg, #0a0f1a, #10203d)',
    textColor: '#48c'
  },
  stardew: {
    title: 'STARDEW VALLEY',
    about: 'Você herdou a antiga fazenda do seu avô. Com algumas ferramentas velhas e algumas moedas, você começa uma nova vida. Cultive, construa e conecte-se.',
    genre: 'Simulação, RPG, Indie',
    dev: 'ConcernedApe',
    date: '26/02/2016',
    price: 'R$ 27,99',
    icon: '🌾',
    color: 'linear-gradient(160deg, #0d1a08, #1a3a12)',
    textColor: '#6c4'
  },
  demonbluff: {
    title: 'DEMON BLUFF',
    about: 'Um jogo de cartas e blefe ambientado em um mundo sombrio e místico. Engane seus adversários demoníacos e sobreviva com astúcia e estratégia.',
    genre: 'Puzzle, Estratégia, Indie',
    dev: 'Indie Studio',
    date: 'Em breve',
    price: 'A confirmar',
    icon: '🃏',
    color: 'linear-gradient(160deg, #0a0a1a, #1a1040)',
    textColor: '#88c'
  },
  deltarune: {
    title: 'DELTARUNE',
    about: 'Kris, Susie e Ralsei devem fechar o Fountain das Trevas e salvar o mundo — mas quem realmente controla o destino? Um RPG emocionante e cheio de surpresas.',
    genre: 'RPG, Aventura, Indie',
    dev: 'Toby Fox',
    date: '28/10/2018',
    price: 'Grátis',
    icon: '🔺',
    color: 'linear-gradient(160deg, #050510, #0d0d2a)',
    textColor: '#66a'
  },
  shovel: {
    title: 'SHOVEL KNIGHT',
    about: 'Um jogo de plataforma clássico em pixel art onde um cavaleiro com uma pá enfrenta a Ordem sem Armadura para resgatar sua parceira Shield Knight.',
    genre: 'Plataforma, Ação, Pixel Art',
    dev: 'Yacht Club Games',
    date: '26/06/2014',
    price: 'R$ 39,99',
    icon: '⚔️',
    color: 'linear-gradient(160deg, #0a1420, #101e30)',
    textColor: '#4a8'
  },
  peak: {
    title: 'PEAK',
    about: 'Escale montanhas brutais com seus amigos em uma aventura cooperativa de sobrevivência. Trabalhe em equipe, gerencie recursos e conquiste o cume.',
    genre: 'Aventura, Cooperativo, Indie',
    dev: 'Aggro Crab',
    date: '2024',
    price: 'R$ 49,99',
    icon: '🏔️',
    color: 'linear-gradient(160deg, #081420, #102040)',
    textColor: '#46a'
  }
};

function showPage(name) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.detail-page').forEach(p => p.classList.remove('active'));
  const el = document.getElementById('page-' + name);
  if (el) el.classList.add('active');
  window.scrollTo(0, 0);
}

function showDetail(id) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.detail-page').forEach(p => p.classList.remove('active'));

  if (id === 'hollow') {
    document.getElementById('page-detail-hollow').classList.add('active');
  } else if (id === 'silksong') {
    document.getElementById('page-detail-silksong').classList.add('active');
  } else if (games[id]) {
    const g = games[id];
    document.getElementById('generic-title').textContent = g.title;
    document.getElementById('generic-about').textContent = g.about;
    document.getElementById('generic-genre-text').textContent = g.genre;
    document.getElementById('generic-dev').textContent = g.dev;
    document.getElementById('generic-date').textContent = g.date;
    document.getElementById('generic-price').textContent = g.price;
    document.getElementById('generic-icon').textContent = g.icon;
    document.getElementById('generic-cover-title').textContent = g.title;
    document.getElementById('generic-cover').style.background = g.color;
    document.getElementById('generic-cover-title').style.color = g.textColor;

    const genresEl = document.getElementById('generic-genres');
    genresEl.innerHTML = g.genre.split(',').map(t => `<span class="genre-tag">${t.trim()}</span>`).join('');

    document.getElementById('page-detail-generic').classList.add('active');
  }
  window.scrollTo(0, 0);
}
</script>
</body>
</html>
