<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>NoteKu — Buku Custom Premium</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      font-family: 'Poppins', sans-serif;
      background: #f1f5f9;
      color: #1e293b;
      scroll-behavior: smooth;
    }

    /* ===== NAVBAR ===== */
    nav {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      padding: 18px 60px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      z-index: 1000;
      background: rgba(15, 23, 42, 0.75);
      backdrop-filter: blur(12px);
      box-shadow: 0 2px 20px rgba(0,0,0,0.2);
      transition: all 0.4s ease;
    }

    nav img {
      height: 55px;
      border-radius: 50%;
      background: white;
      padding: 5px;
    }

    nav .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      color: white;
      font-weight: 700;
      font-size: 1.5em;
      letter-spacing: 0.5px;
    }

    nav ul {
      display: flex;
      list-style: none;
      gap: 35px;
    }

    nav ul li a {
      color: #e2e8f0;
      text-decoration: none;
      font-weight: 500;
      transition: 0.3s;
      font-size: 1em;
    }

    nav ul li a:hover {
      color: #60a5fa;
    }

    /* ===== HEADER ===== */
    header {
      position: relative;
      overflow: hidden;
      text-align: center;
      padding: 200px 20px 160px;
      color: white;
      background: radial-gradient(circle at top left, #1e3a8a, #0f172a 80%);
    }

    /* Gradient animasi halus */
    header::before {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(120deg, #2563eb, #1e3a8a, #3b82f6);
      background-size: 400% 400%;
      animation: gradientMove 12s ease infinite;
      opacity: 0.9;
      z-index: -2;
    }

    /* Partikel cahaya lembut */
    header::after {
      content: "";
      position: absolute;
      inset: 0;
      background: radial-gradient(ellipse at 30% 40%, rgba(255,255,255,0.15), transparent 70%),
                  radial-gradient(ellipse at 70% 60%, rgba(255,255,255,0.1), transparent 70%);
      background-size: cover;
      z-index: -1;
    }

    @keyframes gradientMove {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    header img {
      width: 130px;
      height: 130px;
      border-radius: 50%;
      background: white;
      padding: 10px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.3);
      animation: float 4s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }

    header h1 {
      font-size: 3.2em;
      font-weight: 700;
      margin-top: 25px;
      letter-spacing: 1px;
    }

    header p {
      font-size: 1.2em;
      opacity: 0.95;
      max-width: 700px;
      margin: 15px auto 0;
    }

    /* ===== MAIN, CARD, FOOTER (tidak diubah) ===== */
    main {
      max-width: 1200px;
      margin: 0 auto;
      background: white;
      border-radius: 35px;
      box-shadow: 0 12px 40px rgba(0,0,0,0.1);
      padding: 70px 50px;
      position: relative;
      z-index: 10;
      margin-top: -80px;
    }

    h2 {
      font-size: 1.9em;
      color: #1e3a8a;
      border-left: 6px solid #3b82f6;
      padding-left: 15px;
      margin-bottom: 20px;
      font-weight: 700;
    }

    p { line-height: 1.8; font-size: 1.05em; color: #334155; margin-bottom: 15px; }

    .desain-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 35px;
      margin-top: 40px;
    }

    .card {
      background: #ffffff;
      border-radius: 20px;
      box-shadow: 0 8px 30px rgba(0,0,0,0.08);
      overflow: hidden;
      transform: translateY(30px);
      opacity: 0;
      transition: all 0.8s ease;
    }

    .card.visible { transform: translateY(0); opacity: 1; }

    .card img {
      width: 100%;
      height: 300px;
      object-fit: cover;
      border-bottom: 1px solid #e2e8f0;
      transition: transform 0.4s ease, box-shadow 0.4s ease;
    }

    .card:hover img {
      transform: scale(1.05);
      box-shadow: 0 6px 15px rgba(0,0,0,0.15);
    }

    .card-content { text-align: center; padding: 25px 25px 35px; }

    .card-content p {
      color: #1e3a8a;
      font-weight: 600;
      font-size: 1.05em;
      margin-bottom: 8px;
    }

    .price { font-size: 1.1em; font-weight: 600; color: #0f172a; margin-bottom: 10px; }

    .btn {
      display: inline-block;
      padding: 12px 25px;
      background: linear-gradient(90deg, #1e3a8a, #2563eb);
      color: white;
      border-radius: 10px;
      text-decoration: none;
      font-weight: 500;
      transition: all 0.3s ease;
      box-shadow: 0 4px 12px rgba(37,99,235,0.3);
    }

    .btn:hover { background: linear-gradient(90deg, #2563eb, #3b82f6); transform: translateY(-3px); }

    footer {
      background: #0f172a;
      color: white;
      text-align: center;
      padding: 35px 10px;
      margin-top: 100px;
      border-top: 5px solid #3b82f6;
      font-size: 0.95em;
    }

    footer a { color: #93c5fd; text-decoration: none; font-weight: 500; }
    footer a:hover { text-decoration: underline; }

    @media (max-width: 768px) {
      nav { padding: 15px 25px; }
      nav ul { display: none; }
      header h1 { font-size: 2.3em; }
      main { padding: 40px 25px; }
      .card img { height: 240px; }
    }
  </style>
</head>
<body>

  <!-- ===== NAVBAR ===== -->
  <nav>
    <div class="brand">
      <img src="image/logo.jpg" alt="Logo NoteKu">
      NoteKu
    </div>
    <ul>
      <li><a href="#tentang">Tentang</a></li>
      <li><a href="#koleksi">Koleksi</a></li>
      <li><a href="#kontak">Kontak</a></li>
    </ul>
  </nav>

  <!-- ===== HEADER ===== -->
  <header>
    <img src="image/logo.jpg" alt="Logo NoteKu">
    <h1>NoteKu</h1>
    <p>Buku Custom Premium — Elegan, Eksklusif, dan Penuh Gaya</p>
  </header>

  <!-- ===== MAIN CONTENT (sisanya tetap sama) ===== -->
  <!-- ... (kode kamu selanjutnya tidak perlu diubah) ... -->
</body>
</html>


  <!-- ===== MAIN CONTENT ===== -->
  <main>
    <section>
      <h2>Tentang NoteKu</h2>
      <p><b>NoteKu</b> adalah usaha kreatif yang menghadirkan <b>buku custom premium</b> dengan desain elegan dan sentuhan personal.
      Setiap produk dibuat dengan bahan berkualitas tinggi dan desain modern yang cocok untuk hadiah, koleksi pribadi, maupun keperluan bisnis.</p>

      <p>Kami percaya setiap catatan memiliki cerita, dan melalui NoteKu, kami membantu kamu menulis kisah dengan penuh gaya.</p>
    </section>

    <section>
      <h2>Koleksi Desain</h2>
      <div class="desain-container">

        <!-- Card 001 -->
        <div class="card">
          <img src="image/22.png" alt="Desain 001">
          <div class="card-content">
            <p>Kode Desain: 001</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20001%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>

        <!-- Card 002 -->
        <div class="card">
          <img src="image/23.png" alt="Desain 002">
          <div class="card-content">
            <p>Kode Desain: 002</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20002%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>

        <!-- Card 003 -->
        <div class="card">
          <img src="image/24.png" alt="Desain 003">
          <div class="card-content">
            <p>Kode Desain: 003</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20003%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>

        <!-- Card 004 -->
        <div class="card">
          <img src="image/25.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 004</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
<div class="card">
          <img src="image/26.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 005</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/27.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 006</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/28.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 007</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/29.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 008</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/30.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 009</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/31.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 010</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/32.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 011</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/33.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 012</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/34.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 013</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/35.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 014</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/36.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 015</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/37.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 016</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/38.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 017</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/39.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 017</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
<div class="card">
          <img src="image/40.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 018</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
        <div class="card">
          <img src="image/41.png" alt="Desain 004">
          <div class="card-content">
            <p>Kode Desain: 019</p>
            <p class="price">Rp 4.000</p>
            <a href="https://wa.me/6285143967392?text=📚%20Halo%20NoteKu!%0A✨%20Saya%20ingin%20memesan%20buku%20custom%20dengan%20detail:%0A🔖%20Kode%20Desain:%20004%0A👤%20Nama:%20_____%0A📦%20Jumlah:%20_____%0A📝%20Catatan:%20_____" 
               class="btn" target="_blank">Pesan Sekarang</a>
          </div>
        </div>
      </div>
    </section>
  </main>

  

  <!-- ===== SCROLL ANIMATION ===== -->
  <script>
    const cards = document.querySelectorAll('.card');
    const observer = new IntersectionObserver(entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) entry.target.classList.add('visible');
      });
    }, { threshold: 0.1 });

    cards.forEach(card => observer.observe(card));
  </script>
<!-- ===== FOOTER ===== -->
<footer id="kontak" style="background:#0f172a; color:white; text-align:center; padding:50px 20px; border-top:5px solid #3b82f6; border-radius:20px 20px 0 0;">
  <h3 style="margin-bottom:25px; font-size:1.8em; color:#fff;">Hubungi Kami</h3>
  <p style="margin-bottom:30px; font-size:1em; color:#cbd5e1;">Pesan desain custom atau konsultasi ide bukumu.</p>
  
  <div style="display:flex; justify-content:center; gap:20px; flex-wrap:wrap;">
    <!-- WhatsApp -->
    <a href="https://wa.me/6285143967392" target="_blank" 
       style="display:flex; align-items:center; gap:10px; padding:12px 20px; background:#25D366; color:white; border-radius:12px; font-weight:600; text-decoration:none; box-shadow:0 5px 15px rgba(0,0,0,0.2); transition:0.3s;">
      <img src="image/wa.png" alt="WhatsApp" style="width:24px; height:24px;">
      WhatsApp
    </a>

    <!-- Instagram -->
    <a href="https://instagram.com/ketik_solusi" target="_blank"
       style="display:flex; align-items:center; gap:10px; padding:12px 20px; background:linear-gradient(45deg, #f09433, #e6683c, #dc2743, #cc2366, #bc1888); color:white; border-radius:12px; font-weight:600; text-decoration:none; box-shadow:0 5px 15px rgba(0,0,0,0.2); transition:0.3s;">
      <img src="image/instagram.png" alt="Instagram" style="width:24px; height:24px;">
      Instagram
    </a>
  </div>

  <p style="margin-top:40px; font-size:0.9em; color:#cbd5e1;">&copy; 2025 <b>NoteKu</b> — Buku Custom Premium & Elegan</p>
</footer>


</body>
</html>
