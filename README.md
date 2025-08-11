<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Viewfinder Photography</title>
<meta name="description" content="Viewfinder Photography — photoshoots, wedding photography, portraits and more." />
<style>
  :root{
    --bg:#0e0e10;
    --panel:#121215;
    --accent:#ffcc00;
    --muted:#9a9a9a;
    --glass: rgba(255,255,255,0.03);
    --maxw:1100px;
    --radius:14px;
  }
  *{box-sizing:border-box}
  html,body{height:100%}
  body{
    margin:0;
    font-family: Inter, system-ui, Arial, sans-serif;
    background: linear-gradient(180deg,#070709 0%, var(--bg) 100%);
    color:#fff;
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
    line-height:1.45;
  }

  /* Top nav / hero */
  .wrap{max-width:var(--maxw); margin:0 auto; padding:28px;}
  header{
    display:flex; align-items:center; justify-content:space-between;
    gap:20px;
  }
  .brand{
    display:flex; gap:14px; align-items:center;
  }
  .viewfinder{
    width:64px; height:64px; border-radius:12px;
    background:
      radial-gradient(circle at 35% 35%, rgba(255,255,255,0.06) 0 6px, transparent 7px),
      conic-gradient(#0000,#0003);
    border:2px solid rgba(255,255,255,0.04);
    display:grid; place-items:center; color:var(--accent);
    font-weight:700; font-size:12px;
  }
  nav a{
    color:#ddd; text-decoration:none; margin:0 10px; font-weight:600;
  }
  nav a:hover{color:var(--accent)}

  /* Hero */
  .hero{
    margin-top:18px;
    display:grid;
    grid-template-columns: 1fr 460px;
    gap:28px;
    align-items:center;
  }
  .hero-left{
    padding:28px;
    background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
    border-radius:var(--radius);
    border:1px solid rgba(255,255,255,0.03);
    box-shadow: 0 10px 30px rgba(0,0,0,0.6);
  }
  .kicker{color:var(--muted); font-size:14px; letter-spacing:1px}
  h1{margin:8px 0 12px; font-size:40px; line-height:1.03; color:var(--accent)}
  p.lead{margin:0 0 18px; color:#e8e8e8}
  .cta{
    display:flex; gap:12px; flex-wrap:wrap;
  }
  .btn{
    background:var(--accent); color:#111; padding:12px 18px; border-radius:10px;
    text-decoration:none; font-weight:700; box-shadow: 0 6px 18px rgba(255,204,0,0.12);
  }
  .btn.ghost{
    background:transparent; color:#fff; border:1px solid rgba(255,255,255,0.06)
  }

  /* Hero gallery preview */
  .hero-right{
    position:relative; border-radius:var(--radius); overflow:hidden;
    min-height:300px;
    box-shadow: 0 8px 30px rgba(0,0,0,0.6);
  }
  .hero-right img{ width:100%; height:100%; object-fit:cover; display:block; transform:scale(1.02); transition:transform .8s}
  .hero-right:hover img{ transform:scale(1.06) }
  .viewfinder-frame{
    position:absolute; inset:14px; border-radius:10px; pointer-events:none;
    box-shadow: inset 0 0 0 2px rgba(255,255,255,0.035);
    border: 3px solid rgba(0,0,0,0.3);
  }

  /* Sections */
  section{padding:48px 0}
  h2.section-title{color:var(--accent); margin:0 0 12px}
  .grid{
    display:grid; gap:18px;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  }
  .card{
    background:var(--panel); border-radius:12px; overflow:hidden;
    border:1px solid rgba(255,255,255,0.03);
  }
  .card .img{height:180px; overflow:hidden}
  .card img{width:100%; height:100%; object-fit:cover; display:block; transition:transform .4s}
  .card:hover img{transform:scale(1.06)}
  .card .body{padding:16px}
  .muted{color:var(--muted); font-size:14px}

  /* Gallery */
  .gallery{
    display:grid; grid-template-columns: repeat(auto-fit,minmax(160px,1fr)); gap:12px;
  }
  .thumb{position:relative; overflow:hidden; border-radius:8px; cursor:pointer; border:2px solid rgba(255,255,255,0.03)}
  .thumb img{width:100%; height:170px; object-fit:cover; display:block; transition:transform .35s}
  .thumb:hover img{transform:scale(1.05)}

  /* Lightbox */
  .lightbox{
    position:fixed; inset:0; display:none; align-items:center; justify-content:center;
    background:rgba(0,0,0,0.8); z-index:80;
  }
  .lightbox.open{display:flex}
  .lightbox img{max-width:92%; max-height:84%; border-radius:8px; box-shadow: 0 30px 80px rgba(0,0,0,0.8)}
  .lb-close{
    position:fixed; top:22px; right:24px; background:rgba(255,255,255,0.06);
    color:#fff; border-radius:8px; padding:8px 10px; cursor:pointer; font-weight:700;
  }

  /* Contact */
  .contact-box{display:grid; grid-template-columns:1fr 360px; gap:18px; align-items:start}
  form{background:var(--panel); padding:16px; border-radius:12px; border:1px solid rgba(255,255,255,0.03)}
  label{display:block; font-size:14px; margin-bottom:6px}
  input,textarea,select{
    width:100%; padding:10px 12px; border-radius:8px; border:1px solid rgba(255,255,255,0.04);
    background:transparent; color:#fff; font-size:14px; outline:none;
  }
  textarea{min-height:120px; resize:vertical}
  .note{font-size:13px; color:var(--muted); margin-top:8px}
  footer{padding:24px 0; color:var(--muted); text-align:center; font-size:14px}

  /* Responsive */
  @media (max-width:980px){
    .hero{grid-template-columns:1fr; }
    .contact-box{grid-template-columns:1fr}
  }
  @media (max-width:520px){
    h1{font-size:28px}
    .viewfinder{width:48px;height:48px}
  }
</style>
</head>
<body>

<div class="wrap">
  <header>
    <div class="brand">
      <div class="viewfinder" aria-hidden="true">VF</div>
      <div>
        <div style="font-weight:800">Viewfinder</div>
        <div style="font-size:13px;color:var(--muted)">Photography Studio</div>
      </div>
    </div>

    <nav aria-label="Main navigation">
      <a href="#photoshoot">Photoshoot</a>
      <a href="#wedding">Wedding</a>
      <a href="#portfolio">Portfolio</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <!-- HERO -->
  <main class="hero" role="main" aria-labelledby="main-heading">
    <div class="hero-left" >
      <div class="kicker">PROFESSIONAL • CREATIVE • TIMELESS</div>
      <h1 id="main-heading">Viewfinder Photography</h1>
      <p class="lead">We frame real emotion. Portraits, fashion shoots, and unforgettable wedding storytelling — shot with care and edited with style.</p>

      <div class="cta">
        <a class="btn" href="#contact">Book a shoot</a>
        <a class="btn ghost" href="#portfolio">See portfolio</a>
      </div>

      <p class="note" style="margin-top:14px">Based in India • Travel for destination weddings • Custom packages available</p>
    </div>

    <div class="hero-right" aria-hidden="true">
      <!-- Sample cover image (Unsplash). Replace with your hero image -->
      <img src="https://images.unsplash.com/photo-1504198453319-5ce911bafcde?q=80&w=1400&auto=format&fit=crop" alt="Hero photo preview">
      <div class="viewfinder-frame"></div>
    </div>
  </main>

  <!-- Sections -->
  <section id="photoshoot" aria-labelledby="photoshoot-title">
    <div style="display:flex;align-items:center;justify-content:space-between;gap:18px">
      <div>
        <h2 class="section-title" id="photoshoot-title">Photoshoot</h2>
        <p class="muted">Portraits, fashion, product & lifestyle — studio or on-location sessions tailored to your vibe.</p>
      </div>
    </div>

    <div class="grid" style="margin-top:18px">
      <div class="card">
        <div class="img"><img src="https://images.unsplash.com/photo-1517841905240-472988babdf9?q=80&w=1400&auto=format&fit=crop" alt="Portrait sample"></div>
        <div class="body">
          <div style="font-weight:700">Studio Portraits</div>
          <div class="muted" style="margin-top:6px">Controlled light, dramatic looks, headshots and creative portraiture.</div>
        </div>
      </div>

      <div class="card">
        <div class="img"><img src="https://images.unsplash.com/photo-1491553895911-0055eca6402d?q=80&w=1400&auto=format&fit=crop" alt="Fashion sample"></div>
        <div class="body">
          <div style="font-weight:700">Fashion & Editorial</div>
          <div class="muted" style="margin-top:6px">Lookbooks, portfolios and creative direction for models & designers.</div>
        </div>
      </div>

      <div class="card">
        <div class="img"><img src="https://images.unsplash.com/photo-1504198458649-3128b932f49f?q=80&w=1400&auto=format&fit=crop" alt="Lifestyle sample"></div>
        <div class="body">
          <div style="font-weight:700">Lifestyle</div>
          <div class="muted" style="margin-top:6px">Candid moments that feel real — for families, influencers and brands.</div>
        </div>
      </div>
    </div>
  </section>

  <section id="wedding" aria-labelledby="wedding-title">
    <h2 class="section-title" id="wedding-title">Wedding Photography</h2>
    <p class="muted">Documentary-style coverage with elegant portraits and cinematic edits. Packages start from intimate celebrations to full multi-day events.</p>

    <div class="gallery" style="margin-top:18px">
      <div class="thumb" data-full="https://images.unsplash.com/photo-1524504388940-b1c1722653e1?q=80&w=2000&auto=format&fit=crop"><img src="https://images.unsplash.com/photo-1524504388940-b1c1722653e1?q=80&w=800&auto=format&fit=crop" alt="Wedding 1"></div>
      <div class="thumb" data-full="https://images.unsplash.com/photo-1505577058444-a3dab43f2d7d?q=80&w=2000&auto=format&fit=crop"><img src="https://images.unsplash.com/photo-1505577058444-a3dab43f2d7d?q=80&w=800&auto=format&fit=crop" alt="Wedding 2"></div>
      <div class="thumb" data-full="https://images.unsplash.com/photo-1487412947147-5cebf100ffc2?q=80&w=2000&auto=format&fit=crop"><img src="https://images.unsplash.com/photo-1487412947147-5cebf100ffc2?q=80&w=800&auto=format&fit=crop" alt="Wedding 3"></div>
      <div class="thumb" data-full="https://images.unsplash.com/photo-1533779181886-5f85f8a1e672?q=80&w=2000&auto=format&fit=crop"><img src="https://images.unsplash.com/photo-1533779181886-5f85f8a1e672?q=80&w=800&auto=format&fit=crop" alt="Wedding 4"></div>
    </div>
  </section>

  <section id="portfolio" aria-labelledby="portfolio-title">
    <h2 class="section-title" id="portfolio-title">Portfolio Highlights</h2>
    <p class="muted">A curated selection — click images to view larger.</p>

    <div class="gallery" style="margin-top:18px">
      <div class="thumb" data-full="https://images.unsplash.com/photo-1502685104226-ee32379fefbe?q=80&w=2000&auto=format&fit=crop"><img src="https://images.unsplash.com/photo-1502685104226-ee32379fefbe?q=80&w=800&auto=format&fit=crop" alt="Portfolio 1"></div>
      <div class="thumb" data-full="https://images.unsplash.com/photo-1544005313-94ddf0286df2?q=80&w=2000&auto=format&fit=crop"><img src="https://images.unsplash.com/photo-1544005313-94ddf0286df2?q=80&w=800&auto=format&fit=crop" alt="Portfolio 2"></div>
      <div class="thumb" data-full="https://images.unsplash.com/photo-1496307042754-b4aa456c4a2d?q=80&w=2000&auto=format&fit=crop"><img src="https://images.unsplash.com/photo-1496307042754-b4aa456c4a2d?q=80&w=800&auto=format&fit=crop" alt="Portfolio 3"></div>
      <div class="thumb" data-full="https://images.unsplash.com/photo-1524253482453-3fed8d2fe12b?q=80&w=2000&auto=format&fit=crop"><img src="https://images.unsplash.com/photo-1524253482453-3fed8d2fe12b?q=80&w=800&auto=format&fit=crop" alt="Portfolio 4"></div>
    </div>
  </section>

  <section id="contact" aria-labelledby="contact-title">
    <h2 class="section-title" id="contact-title">Contact & Bookings</h2>
    <p class="muted">Fill the form — we'll reply within 24-48 hours. For urgent enquiries call: +91 98765 43210</p>

    <div class="contact-box" style="margin-top:18px">
      <form id="contactForm" aria-label="Booking form">
        <label for="name">Name</label>
        <input id="name" name="name" placeholder="Your name" required>

        <label for="email">Email</label>
        <input id="email" name="email" type="email" placeholder="you@example.com" required>

        <label for="service">Service</label>
        <select id="service" name="service">
          <option>Photoshoot (portrait/fashion)</option>
          <option>Wedding</option>
          <option>Commercial / Brand</option>
          <option>Pre-wedding / Destination</option>
        </select>

        <label for="message">Message</label>
        <textarea id="message" name="message" placeholder="Tell us dates, location and any special requests"></textarea>

        <div style="margin-top:12px; display:flex; gap:10px">
          <button type="submit" class="btn">Send enquiry</button>
          <button type="button" class="btn ghost" onclick="location.href='#portfolio'">View portfolio</button>
        </div>

        <p class="note" style="margin-top:12px">This form is client-side only in this demo. To receive messages, connect it to your email service (Netlify Forms, Formspree, or backend).</p>
      </form>

      <aside style="padding:16px; background:var(--panel); border-radius:12px; border:1px solid rgba(255,255,255,0.03)">
        <strong>Studio Info</strong>
        <p class="muted" style="margin-top:8px">City: Mumbai, India<br>Email: hello@viewfinder.example<br>Phone: +91 98765 43210</p>

        <div style="margin-top:12px">
          <strong>Why choose us</strong>
          <ul class="muted" style="padding-left:18px; margin-top:8px; line-height:1.6">
            <li>Full-day & half-day wedding coverage</li>
            <li>Professional retouching & colour grading</li>
            <li>Custom albums & prints</li>
          </ul>
        </div>
      </aside>
    </div>
  </section>

  <footer>
    &copy; <span id="year"></span> Viewfinder Photography • Designed with care
  </footer>
</div>

<!-- Lightbox -->
<div class="lightbox" id="lightbox" role="dialog" aria-modal="true" aria-hidden="true">
  <button class="lb-close" id="lbClose" aria-label="Close (escape)">✕</button>
  <img src="" alt="Expanded photo" id="lbImg">
</div>

<script>
  // Fill current year
  document.getElementById('year').textContent = new Date().getFullYear();

  // Gallery -> Lightbox
  const lightbox = document.getElementById('lightbox');
  const lbImg = document.getElementById('lbImg');
  const thumbs = document.querySelectorAll('.thumb');

  thumbs.forEach(t => {
    t.addEventListener('click', () => {
      const src = t.getAttribute('data-full') || (t.querySelector('img')?.src);
      lbImg.src = src;
      lightbox.classList.add('open');
      lightbox.setAttribute('aria-hidden', 'false');
    });
  });

  document.getElementById('lbClose').addEventListener('click', closeLB);
  lightbox.addEventListener('click', (e) => { if(e.target === lightbox) closeLB(); });
  document.addEventListener('keydown', (e)=>{ if(e.key==='Escape') closeLB(); });
  function closeLB(){
    lightbox.classList.remove('open');
    lightbox.setAttribute('aria-hidden','true');
    lbImg.src='';
  }

  // Contact form: demo behaviour (client-side only)
  const form = document.getElementById('contactForm');
  form.addEventListener('submit', (e) => {
    e.preventDefault();
    // Basic validation
    const name = form.name.value.trim();
    const email = form.email.value.trim();
    if(!name || !email){ alert('Please add name and email.'); return; }
    // Show a friendly message — replace with actual submit logic on backend
    alert('Thanks, ' + (name || '') + '! Your enquiry was recorded in this demo. Connect a backend or form service to receive emails.');
    form.reset();
  });

  // Smooth scrolling for anchor links (native fallback)
  document.querySelectorAll('a[href^="#"]').forEach(a=>{
    a.addEventListener('click', e=>{
      const href = a.getAttribute('href');
      if(href.length>1){
        e.preventDefault();
        const el = document.querySelector(href);
        if(el) el.scrollIntoView({behavior:'smooth', block:'start'});
      }
    });
  });
</script>

</body>
</html>
