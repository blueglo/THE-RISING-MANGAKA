# THE-RISING-MANGAKA
A safe place for indie manga creators to share their stories, showcase their art, and connect with readers. Discover original manga, support independent artists, and help new talent rise.

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Rising Mangaka — Professional Indie Publishing Hub</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cabinet+Grotesk:wght@700;800&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --bg-main: #F4F8FC;
    --bg-card: #FFFFFF;
    --bg-accent: #E3EFFB;
    --border-color: #CBDCEF;
    --text-main: #1E2D42;
    --text-muted: #627792;
    --pastel-blue: #A2C8EC;
    --pastel-blue-hover: #7EB3E6;
    --coral-accent: #FF6B8B;
    --radius-sm: 6px;
    --radius-md: 12px;
    --shadow-sm: 0 2px 8px rgba(162, 200, 236, 0.15);
    --shadow-md: 0 8px 24px rgba(30, 45, 66, 0.06);
  }

  * { box-sizing: border-box; transition: all 0.2s ease; }
  html, body { margin: 0; padding: 0; background: var(--bg-main); color: var(--text-main); font-family: 'Inter', sans-serif; min-height: 100vh; }
  
  body::before {
    content: ""; position: fixed; inset: 0; pointer-events: none;
    background-image: radial-gradient(circle, rgba(126,179,230,0.08) 1px, transparent 1px);
    background-size: 24px 24px; z-index: 0;
  }
  .app { position: relative; z-index: 1; display: flex; flex-direction: column; min-height: 100vh; }
  a { color: inherit; text-decoration: none; }
  button { font-family: inherit; cursor: pointer; border: none; background: none; }

  /* ---------- TOP NAVIGATION ---------- */
  header.topbar {
    position: sticky; top: 0; z-index: 100;
    background: rgba(244, 248, 252, 0.85); backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border-color);
    display: flex; align-items: center; justify-content: space-between; gap: 20px;
    padding: 16px 40px;
  }
  .brand {
    font-family: 'Cabinet Grotesk', sans-serif; font-weight: 800; font-size: 26px;
    letter-spacing: -0.5px; color: var(--text-main); display: flex; align-items: center; gap: 6px;
  }
  .brand span { color: var(--pastel-blue-hover); }
  
  .search-wrap {
    flex: 1; display: flex; align-items: center; max-width: 500px;
    border: 1px solid var(--border-color); border-radius: var(--radius-md);
    background: var(--bg-card); padding: 8px 16px; box-shadow: var(--shadow-sm);
  }
  .search-wrap input {
    flex: 1; border: none; outline: none; font-size: 14px; color: var(--text-main); background: transparent;
  }
  .search-wrap button { color: var(--text-muted); font-size: 16px; padding: 0; }
  .search-wrap button:hover { color: var(--text-main); }

  .nav-actions { display: flex; align-items: center; gap: 12px; }
  .btn {
    font-weight: 600; font-size: 14px; padding: 10px 20px; border-radius: var(--radius-md);
    border: 1px solid var(--border-color); background: var(--bg-card); color: var(--text-main);
  }
  .btn:hover { background: var(--bg-accent); transform: translateY(-1px); }
  .btn-primary { background: var(--pastel-blue); border-color: var(--pastel-blue); color: #1E2D42; }
  .btn-primary:hover { background: var(--pastel-blue-hover); border-color: var(--pastel-blue-hover); }
  
  .avatar-btn {
    width: 40px; height: 40px; border-radius: 50%; background: var(--pastel-blue);
    color: var(--text-main); display: flex; align-items: center; justify-content: center;
    font-weight: 700; border: 1px solid var(--border-color); position: relative;
  }
  .user-menu { position: relative; }
  .dropdown {
    position: absolute; right: 0; top: 50px; background: var(--bg-card);
    border: 1px solid var(--border-color); border-radius: var(--radius-md);
    min-width: 200px; padding: 8px; display: none; flex-direction: column; box-shadow: var(--shadow-md);
  }
  .dropdown.open { display: flex; }
  .dropdown button {
    text-align: left; padding: 10px 12px; font-size: 14px; font-weight: 500;
    border-radius: var(--radius-sm); color: var(--text-main); width: 100%;
  }
  .dropdown button:hover { background: var(--bg-accent); }

  /* ---------- APP SHELL & HUB LAYOUT ---------- */
  .shell { max-width: 1400px; width: 100%; margin: 0 auto; padding: 32px 40px 100px; flex: 1; }
  
  .filter-row { display: flex; gap: 8px; overflow-x: auto; padding-bottom: 16px; margin-bottom: 24px; }
  .filter-row::-webkit-scrollbar { height: 4px; }
  .filter-row::-webkit-scrollbar-thumb { background: var(--border-color); border-radius: 2px; }
  .chip {
    flex-shrink: 0; padding: 8px 18px; border-radius: var(--radius-md);
    background: var(--bg-card); border: 1px solid var(--border-color);
    font-size: 13px; font-weight: 500; color: var(--text-muted);
  }
  .chip.active, .chip:hover { background: var(--text-main); color: #fff; border-color: var(--text-main); }

  .section-bar {
    display: flex; align-items: center; justify-content: space-between; margin: 40px 0 20px;
    border-bottom: 1px solid var(--border-color); padding-bottom: 12px;
  }
  .section-title { font-family: 'Cabinet Grotesk', sans-serif; font-size: 24px; font-weight: 700; color: var(--text-main); margin: 0; }
  
  /* ---------- REFINED MANGA GRID / CARDS ---------- */
  .grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(210px, 1fr)); gap: 28px; }
  .card {
    background: var(--bg-card); border: 1px solid var(--border-color);
    border-radius: var(--radius-md); overflow: hidden; box-shadow: var(--shadow-sm); position: relative;
  }
  .card:hover { transform: translateY(-4px); box-shadow: var(--shadow-md); border-color: var(--pastel-blue-hover); }
  .card-cover { width: 100%; aspect-ratio: 3/4; background-size: cover; background-position: center; position: relative; }
  .card-badge {
    position: absolute; bottom: 12px; left: 12px; background: rgba(30, 45, 66, 0.85);
    backdrop-filter: blur(4px); color: #fff; font-size: 11px; font-weight: 600; padding: 4px 10px; border-radius: var(--radius-sm);
  }
  .card-body { padding: 16px; }
  .card-title { font-weight: 700; font-size: 15px; margin: 0 0 4px; line-height: 1.3; }
  .card-author { font-size: 13px; color: var(--text-muted); margin: 0 0 12px; }
  .card-meta { display: flex; align-items: center; justify-content: space-between; font-size: 12px; color: var(--text-muted); border-top: 1px solid var(--bg-main); padding-top: 10px; }
  .card-meta span { display: flex; align-items: center; gap: 4px; }

  /* ---------- USER DASHBOARD ---------- */
  .dashboard-grid { display: grid; grid-template-columns: 280px 1fr; gap: 40px; margin-top: 20px; }
  .dashboard-sidebar { background: var(--bg-card); border: 1px solid var(--border-color); border-radius: var(--radius-md); padding: 24px; box-shadow: var(--shadow-sm); height: fit-content; }
  .stat-widget { background: var(--bg-accent); padding: 16px; border-radius: var(--radius-md); margin-bottom: 12px; }
  .stat-widget .num { font-family: 'Cabinet Grotesk', sans-serif; font-size: 28px; font-weight: 800; color: var(--text-main); }
  .stat-widget .label { font-size: 12px; color: var(--text-muted); font-weight: 500; text-transform: uppercase; letter-spacing: 0.5px; }
  
  .dashboard-manga-item {
    display: flex; align-items: center; justify-content: space-between; background: var(--bg-card);
    border: 1px solid var(--border-color); border-radius: var(--radius-md); padding: 16px; margin-bottom: 14px;
  }
  .dashboard-manga-info { display: flex; align-items: center; gap: 16px; }
  .dashboard-manga-thumb { width: 50px; height: 65px; background-size: cover; background-position: center; border-radius: var(--radius-sm); border: 1px solid var(--border-color); }

  /* ---------- SYSTEM OVERLAYS & MODALS ---------- */
  .overlay { position: fixed; inset: 0; background: rgba(30, 45, 66, 0.4); backdrop-filter: blur(4px); display: none; align-items: center; justify-content: center; z-index: 200; padding: 20px; }
  .overlay.open { display: flex; }
  .modal { background: var(--bg-card); border: 1px solid var(--border-color); border-radius: var(--radius-md); width: 100%; max-width: 500px; max-height: 90vh; overflow-y: auto; padding: 32px; box-shadow: var(--shadow-md); position: relative; }
  .modal.wide { max-width: 800px; }
  .modal-close { position: absolute; top: 20px; right: 20px; font-size: 24px; color: var(--text-muted); }
  .modal h2 { font-family: 'Cabinet Grotesk', sans-serif; font-size: 26px; margin: 0 0 8px; }
  .modal .sub { font-size: 14px; color: var(--text-muted); margin-bottom: 24px; }

  .field { margin-bottom: 18px; }
  .field label { display: block; font-size: 13px; font-weight: 600; margin-bottom: 6px; }
  .field input, .field textarea, .field select { width: 100%; border: 1px solid var(--border-color); border-radius: var(--radius-sm); padding: 12px; font-family: inherit; font-size: 14px; color: var(--text-main); background: var(--bg-main); }
  .field input:focus, .field textarea:focus, .field select:focus { outline: 2px solid var(--pastel-blue); background: #fff; }
  .field textarea { resize: vertical; min-height: 90px; }

  .form-error { color: var(--coral-accent); font-size: 13px; font-weight: 600; margin-bottom: 12px; }
  .modal-submit { width: 100%; padding: 14px; font-size: 15px; font-weight: 600; margin-top: 12px; }

  .email-notice-box {
    background: #FFF5F7; border: 1px solid #FFD3DC; color: #BC2B4C;
    padding: 14px; border-radius: var(--radius-md); font-size: 13px;
    line-height: 1.5; margin-bottom: 18px; display: flex; gap: 10px; align-items: flex-start;
  }

  /* ---------- SERIES & READER VIEW OVERLAYS ---------- */
  .detail-overlay { position: fixed; inset: 0; background: var(--bg-main); z-index: 150; display: none; overflow-y: auto; }
  .detail-overlay.open { display: block; }
  .detail-hero { border-bottom: 1px solid var(--border-color); padding: 20px 40px; display: flex; gap: 16px; align-items: center; background: #fff; position: sticky; top: 0; z-index: 10; }
  .back-btn { width: 36px; height: 36px; border-radius: 50%; border: 1px solid var(--border-color); background: #fff; display: flex; align-items: center; justify-content: center; font-size: 18px; }
  .back-btn:hover { background: var(--bg-accent); }
  
  .detail-body { max-width: 1000px; margin: 0 auto; padding: 40px 24px; display: flex; gap: 40px; flex-wrap: wrap; }
  .detail-cover { width: 260px; aspect-ratio: 3/4; border-radius: var(--radius-md); background-size: cover; background-position: center; border: 1px solid var(--border-color); box-shadow: var(--shadow-md); }
  .detail-info { flex: 1; min-width: 300px; }
  .detail-info h1 { font-family: 'Cabinet Grotesk', sans-serif; font-size: 36px; margin: 0 0 8px; }
  .detail-author { font-size: 16px; font-weight: 600; color: var(--pastel-blue-hover); margin-bottom: 16px; }
  .detail-stats { display: flex; gap: 24px; margin-bottom: 24px; background: #fff; padding: 16px; border-radius: var(--radius-md); border: 1px solid var(--border-color); }
  .stat b { display: block; font-size: 18px; font-family: 'Cabinet Grotesk', sans-serif; }
  
  .chapter-item { display: flex; align-items: center; justify-content: space-between; padding: 16px 20px; background: #fff; border: 1px solid var(--border-color); border-radius: var(--radius-md); margin-bottom: 12px; cursor: pointer; }
  .chapter-item:hover { border-color: var(--pastel-blue-hover); transform: translateX(4px); }

  /* ---------- MANGA CONTENT READER LAYER ---------- */
  .reader-overlay { position: fixed; inset: 0; background: #11161D; z-index: 250; display: none; flex-direction: column; }
  .reader-overlay.open { display: flex; }
  .reader-top { display: flex; align-items: center; justify-content: space-between; padding: 16px 32px; background: #1A222C; color: #fff; }
  .reader-pages { flex: 1; overflow-y: auto; display: flex; flex-direction: column; align-items: center; padding: 20px 0; gap: 16px; }
  .reader-pages img { max-width: min(750px, 95%); border: 1px solid rgba(250,250,250,0.05); box-shadow: 0 4px 30px rgba(0,0,0,0.5); }
  .reader-nav { display: flex; justify-content: space-between; padding: 16px 32px; background: #1A222C; }
  .reader-nav button { background: var(--pastel-blue); color: #1E2D42; padding: 10px 20px; border-radius: var(--radius-sm); font-weight: 600; }
  .reader-nav button:disabled { opacity: 0.3; }

  .empty-state { text-align: center; padding: 40px; color: var(--text-muted); font-size: 15px; }
  footer { text-align: center; padding: 40px; border-top: 1px solid var(--border-color); color: var(--text-muted); font-size: 13px; margin-top: auto; }
</style>
</head>
<body>
<div class="app" id="app">

  <header class="topbar">
    <div class="brand" id="logoHome" style="cursor:pointer">RISING<span>MANGAKA</span></div>
    <div class="search-wrap">
      <input id="searchInput" type="text" placeholder="Search standalone titles or creative authors...">
      <button id="searchBtn">🔍</button>
    </div>
    <div class="nav-actions" id="navActions"></div>
  </header>

  <main class="shell" id="mainContainer">
    <!-- HOME CORE HUB VIEW -->
    <div id="homeHubView">
      <div class="filter-row" id="filterRow"></div>
      
      <!-- FEATURED DISCOVERY UTILITY BAR -->
      <div class="section-bar" style="margin-top:20px;">
        <h2 class="section-title">🎲 Instant Discovery Portal</h2>
        <button class="btn btn-primary" id="randomMangaBtn">Surprise Me With Manga</button>
      </div>

      <!-- ROW: WOWED MANGA -->
      <div class="section-bar"><h2 class="section-title">🔥 Highly Wowed Series</h2></div>
      <div class="grid" id="wowedMangaGrid"></div>

      <!-- ROW: NEWEST MANGA -->
      <div class="section-bar"><h2 class="section-title">✨ Fresh Newest Releases</h2></div>
      <div class="grid" id="newestMangaGrid"></div>
    </div>

    <!-- DYNAMIC USER CREATOR DASHBOARD VIEW -->
    <div id="userDashboardView" style="display:none;">
      <div class="section-bar">
        <h2 class="section-title">📊 Creator Studio Dashboard</h2>
        <button class="btn btn-primary" onclick="openUploadModal()">+ Submit A New Series via Gmail</button>
      </div>
      <div class="dashboard-grid">
        <div class="dashboard-sidebar">
          <div class="stat-widget"><div class="num" id="dashTotalViews">0</div><div class="label">Gross Views</div></div>
          <div class="stat-widget"><div class="num" id="dashTotalLikes">0</div><div class="label">Fan Likes</div></div>
          <button class="btn" style="width:100%; margin-top:10px;" id="dashBackHomeBtn">← Exit Studio</button>
        </div>
        <div>
          <h3 style="margin-top:0; font-family:'Cabinet Grotesk', sans-serif;">Your Dynamic Properties</h3>
          <div id="dashboardMangaList"></div>
        </div>
      </div>
    </div>
  </main>

  <footer>
    &copy; 2026 Rising Mangaka Ecosystem. Content submissions routed via verified email channels.
  </footer>
</div>

<!-- ===== AUTH PLATFORM OVERLAY ===== -->
<div class="overlay" id="authOverlay">
  <div class="modal">
    <button class="modal-close" id="authClose">&times;</button>
    <h2 id="authTitle">Access Engine</h2>
    <div class="sub" id="authSub">Log in to enter the creator studio submission hub.</div>
    <form id="authForm">
      <div class="field" id="nameField" style="display:none;"><label for="authName">Creator Identity / Pen Name</label><input type="text" id="authName" placeholder="e.g., Kentaro Takahashi"></div>
      <div class="field"><label for="authEmail">Email Address</label><input type="email" id="authEmail" placeholder="name@domain.com"></div>
      <div class="field"><label for="authPass">Secure Password</label><input type="password" id="authPass" placeholder="••••••••"></div>
      <div class="form-error" id="authError"></div>
      <button type="submit" class="btn btn-primary modal-submit" id="authSubmitBtn">Initialize Connection</button>
    </form>
    <div style="text-align:center; margin-top:20px; font-size:13px;" id="authSwitchLine">
      New Author? <button type="button" style="color:var(--pastel-blue-hover); font-weight:600; text-decoration:underline;" id="authSwitchBtn">Register Workspace</button>
    </div>
  </div>
</div>

<!-- ===== MANGA EMAIL ROUTING SUBMISSION MODAL ===== -->
<div class="overlay" id="uploadOverlay">
  <div class="modal wide">
    <button class="modal-close" id="uploadClose">&times;</button>
    <h2>Submit New Series Meta</h2>
    <div class="sub">Fill out this metadata matrix to pre-compile your submission template package.</div>
    
    <div class="email-notice-box">
      <span>⚠️</span>
      <div><strong>Gmail Delivery Notice:</strong> Web browsers cannot attach system files to emails automatically. Clicking the launch button below will generate your pre-formatted application text. You just need to attach your cover image file and chapter pages bundle manually in Gmail before sending!</div>
    </div>

    <form id="uploadForm">
      <div class="field"><label for="upTitle">Manga Series Title</label><input type="text" id="upTitle" placeholder="e.g., Chrono Trigger Rebirth" required></div>
      <div class="field-row" style="display:flex; gap:16px;">
        <div class="field" style="flex:1;"><label for="upGenre">Primary Genre Tag</label><select id="upGenre"><option>Action</option><option>Romance</option><option>Fantasy</option><option>Slice of Life</option><option>Horror</option><option>Sci-Fi</option></select></div>
        <div class="field" style="flex:1;"><label for="upStatus">Production Lifecycle Status</label><select id="upStatus"><option>Ongoing</option><option>Completed</option><option>Hiatus</option></select></div>
      </div>
      <div class="field"><label for="upDesc">Synopsis / Story Description</label><textarea id="upDesc" placeholder="Summarize the core narrative path..." required></textarea></div>
      
      <div class="form-error" id="uploadError"></div>
      <button type="submit" class="btn btn-primary modal-submit" style="background-color: var(--coral-accent); border-color: var(--coral-accent); color:#fff;">✉️ Generate Submission & Open Gmail</button>
    </form>
  </div>
</div>

<!-- ===== APPEND CHAPTER MODAL VIA EMAIL ===== -->
<div class="overlay" id="chapterOverlay">
  <div class="modal">
    <button class="modal-close" id="chapterClose">&times;</button>
    <h2>Submit Next Chapter</h2>
    <div class="sub" id="chapterSub"></div>

    <div class="email-notice-box">
      <span>✉️</span>
      <div>Please remember to attach your image archive files (ZIP or sequential JPG files) inside your email container draft.</div>
    </div>

    <form id="chapterForm">
      <div class="field"><label for="chTitle">Chapter Title Token / Number</label><input type="text" id="chTitle" placeholder="e.g., Chapter 2: The Return" required></div>
      <button type="submit" class="btn btn-primary modal-submit">✉️ Open Gmail Chapter Portal</button>
    </form>
  </div>
</div>

<!-- ===== SERIES DETAIL INTERACTION OVERLAY ===== -->
<div class="detail-overlay" id="detailOverlay">
  <div class="detail-hero">
    <button class="back-btn" id="detailBack">&larr;</button>
    <div class="brand" style="font-size:20px;">RISING<span>MANGAKA</span></div>
  </div>
  <div class="detail-body" id="detailBody"></div>
</div>

<!-- ===== PROFILE DISCOVERY VIEWER ===== -->
<div class="detail-overlay" id="profileOverlay">
  <div class="detail-hero">
    <button class="back-btn" id="profileBack">&larr;</button>
    <div class="brand" style="font-size:20px;">RISING<span>MANGAKA</span></div>
  </div>
  <div class="shell" style="max-width:1000px;">
    <h1 id="profileNameBig" style="font-family:'Cabinet Grotesk', sans-serif; font-size:42px; margin-bottom:4px;">Name</h1>
    <p id="profileEmailSmall" style="color:var(--text-muted); margin-top:0; marg
