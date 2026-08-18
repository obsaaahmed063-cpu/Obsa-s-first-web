<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Student Record Archive — Amara N. Okafor</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Source+Serif+4:opsz,wght@8..60,400;8..60,600;8..60,700&family=IBM+Plex+Mono:wght@400;500;600&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#1B2A41;
    --manila:#D8C9A3;
    --manila-dark:#C4B183;
    --paper:#FAF7F0;
    --paper-dim:#F1ECDF;
    --stamp:#A33B2E;
    --graphite:#4A4A45;
    --rule:#C7BFAE;
    --serif: "Source Serif 4", Georgia, serif;
    --mono: "IBM Plex Mono", monospace;
    --sans: "Inter", sans-serif;
  }

  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--paper);
    color:var(--graphite);
    font-family:var(--sans);
    line-height:1.6;
    -webkit-font-smoothing:antialiased;
  }
  a{color:inherit;}
  img{max-width:100%;display:block;}

  ::selection{background:var(--stamp);color:var(--paper);}

  :focus-visible{
    outline:2px solid var(--stamp);
    outline-offset:3px;
  }

  /* ===== Texture ===== */
  .grain{
    position:fixed; inset:0; pointer-events:none; z-index:999;
    opacity:0.035; mix-blend-mode:multiply;
    background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='120' height='120'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  }

  /* ===== Folder tab nav ===== */
  .tabbar{
    position:sticky; top:0; z-index:100;
    display:flex; align-items:flex-end;
    gap:2px;
    padding:14px 32px 0;
    background:var(--paper);
    border-bottom:3px solid var(--ink);
    overflow-x:auto;
    scrollbar-width:none;
  }
  .tabbar::-webkit-scrollbar{display:none;}
  .tabbar .filecode{
    font-family:var(--mono); font-size:11px; letter-spacing:0.08em;
    color:var(--graphite); opacity:0.55;
    padding-bottom:14px; white-space:nowrap; margin-right:18px;
  }
  .tab{
    font-family:var(--mono);
    font-size:12px;
    letter-spacing:0.06em;
    text-transform:uppercase;
    text-decoration:none;
    color:var(--graphite);
    background:var(--paper-dim);
    border:1px solid var(--rule);
    border-bottom:none;
    padding:10px 16px 9px;
    border-radius:6px 6px 0 0;
    white-space:nowrap;
    transition:background .2s ease, color .2s ease, transform .15s ease;
    cursor:pointer;
  }
  .tab:hover{background:var(--manila); transform:translateY(-2px);}
  .tab.active{
    background:var(--ink); color:var(--paper); border-color:var(--ink);
  }

  /* ===== Cover / hero ===== */
  .cover{
    position:relative;
    padding:80px 32px 96px;
    max-width:1000px;
    margin:0 auto;
  }
  .stamp-mark{
    position:absolute;
    top:64px; right:36px;
    width:128px; height:128px;
    border:3px solid var(--stamp);
    border-radius:50%;
    display:flex; align-items:center; justify-content:center;
    transform:rotate(-14deg);
    opacity:0;
    animation: stampIn .5s cubic-bezier(.2,.8,.2,1) .6s forwards;
  }
  .stamp-mark span{
    font-family:var(--mono);
    font-size:11px; font-weight:600;
    letter-spacing:0.12em;
    color:var(--stamp);
    text-align:center;
    line-height:1.5;
  }
  @keyframes stampIn{
    0%{opacity:0; transform:rotate(-14deg) scale(1.8);}
    60%{opacity:1;}
    100%{opacity:0.9; transform:rotate(-14deg) scale(1);}
  }

  .eyebrow{
    font-family:var(--mono); font-size:12px; letter-spacing:0.14em;
    text-transform:uppercase; color:var(--stamp); margin-bottom:18px;
    display:flex; align-items:center; gap:10px;
  }
  .eyebrow::before{content:"";width:24px;height:1px;background:var(--stamp);}

  h1.title{
    font-family:var(--serif);
    font-weight:700;
    font-size:clamp(2.6rem, 6vw, 4.4rem);
    color:var(--ink);
    letter-spacing:-0.01em;
    line-height:1.02;
    max-width:11ch;
  }
  .subtitle{
    font-family:var(--serif);
    font-style:italic;
    font-size:1.2rem;
    color:var(--graphite);
    margin-top:18px;
    max-width:46ch;
  }

  .ledger-line{
    display:flex; flex-wrap:wrap; gap:28px;
    margin-top:44px;
    padding-top:24px;
    border-top:1px solid var(--rule);
    font-family:var(--mono);
    font-size:12px;
  }
  .ledger-line dt{color:var(--graphite); opacity:0.55; text-transform:uppercase; letter-spacing:0.08em; margin-bottom:4px;}
  .ledger-line dd{color:var(--ink); font-size:14px;}

  /* ===== Section shell ===== */
  section{
    max-width:1000px;
    margin:0 auto;
    padding:96px 32px;
    border-top:1px solid var(--rule);
  }
  .section-head{
    display:flex; align-items:baseline; gap:16px;
    margin-bottom:48px;
  }
  .exhibit{
    font-family:var(--mono); font-size:13px; color:var(--stamp);
    letter-spacing:0.08em; white-space:nowrap;
  }
  h2.section-title{
    font-family:var(--serif); font-weight:600;
    font-size:clamp(1.8rem, 3.2vw, 2.6rem);
    color:var(--ink);
  }

  /* ===== About ===== */
  .about-grid{
    display:grid;
    grid-template-columns:1.3fr 1fr;
    gap:56px;
    align-items:start;
  }
  .about-text p{margin-bottom:18px; font-size:1.02rem; max-width:56ch;}
  .about-text p:first-of-type::first-letter{
    font-family:var(--serif); font-size:3.4em; float:left;
    line-height:0.8; padding:6px 8px 0 0; color:var(--stamp); font-weight:700;
  }
  .card{
    background:var(--paper-dim);
    border:1px solid var(--rule);
    border-radius:4px;
    padding:22px 24px;
  }
  .card h3{
    font-family:var(--mono); font-size:11px; letter-spacing:0.1em;
    text-transform:uppercase; color:var(--graphite); opacity:0.6; margin-bottom:14px;
  }
  .card ul{list-style:none;}
  .card li{
    display:flex; justify-content:space-between; gap:12px;
    font-size:13.5px; padding:8px 0; border-bottom:1px dashed var(--rule);
  }
  .card li:last-child{border-bottom:none;}
  .card li span:first-child{color:var(--graphite); opacity:0.7;}
  .card li span:last-child{font-family:var(--mono); color:var(--ink); text-align:right;}

  /* ===== Timeline ===== */
  .timeline{position:relative; padding-left:2px;}
  .timeline::before{
    content:""; position:absolute; left:88px; top:6px; bottom:6px; width:2px;
    background:repeating-linear-gradient(var(--rule) 0 6px, transparent 6px 11px);
  }
  .entry{
    display:grid;
    grid-template-columns:88px 1fr;
    gap:28px;
    position:relative;
    padding-bottom:44px;
    opacity:0; transform:translateY(14px);
    transition:opacity .6s ease, transform .6s ease;
  }
  .entry.in{opacity:1; transform:none;}
  .entry:last-child{padding-bottom:0;}
  .entry .date{
    font-family:var(--mono); font-size:12px; color:var(--graphite); opacity:0.6;
    padding-top:2px; text-align:right;
  }
  .entry .node{
    position:absolute; left:83px; top:5px;
    width:11px; height:11px; border-radius:50%;
    background:var(--paper); border:2px solid var(--stamp);
  }
  .entry .body{
    background:var(--paper-dim);
    border:1px solid var(--rule);
    border-radius:4px;
    padding:18px 22px;
  }
  .entry .body .tag{
    display:inline-block; font-family:var(--mono); font-size:10px;
    letter-spacing:0.08em; text-transform:uppercase;
    color:var(--stamp); border:1px solid var(--stamp);
    border-radius:3px; padding:2px 8px; margin-bottom:10px;
  }
  .entry .body h3{font-family:var(--serif); font-size:1.15rem; color:var(--ink); margin-bottom:6px; font-weight:600;}
  .entry .body p{font-size:14px;}

  /* ===== Projects ===== */
  .exhibits{
    display:grid;
    grid-template-columns:repeat(auto-fit, minmax(260px,1fr));
    gap:1px;
    background:var(--rule);
    border:1px solid var(--rule);
  }
  .exhibit-card{
    background:var(--paper);
    padding:26px 24px 24px;
    position:relative;
    transition:background .25s ease;
  }
  .exhibit-card:hover{background:var(--paper-dim);}
  .exhibit-card .num{
    font-family:var(--mono); font-size:11px; color:var(--graphite); opacity:0.5;
    margin-bottom:14px; display:block;
  }
  .exhibit-card h3{font-family:var(--serif); font-size:1.2rem; color:var(--ink); margin-bottom:8px; font-weight:600;}
  .exhibit-card p{font-size:13.5px; margin-bottom:14px;}
  .exhibit-card .meta{
    display:flex; flex-wrap:wrap; gap:6px;
  }
  .pill{
    font-family:var(--mono); font-size:10px; letter-spacing:0.04em;
    background:var(--manila); color:var(--ink);
    padding:3px 9px; border-radius:20px;
  }

  /* ===== Documents ===== */
  .filecabinet{border:1px solid var(--rule); border-radius:4px; overflow:hidden;}
  .doc-row{
    display:grid;
    grid-template-columns:44px 1fr auto auto;
    gap:16px;
    align-items:center;
    padding:16px 20px;
    background:var(--paper);
    border-bottom:1px solid var(--rule);
    transition:background .2s ease;
  }
  .doc-row:last-child{border-bottom:none;}
  .doc-row:hover{background:var(--paper-dim);}
  .doc-icon{
    font-family:var(--mono); font-size:10px; font-weight:600;
    width:36px; height:44px; border:1.5px solid var(--ink);
    border-radius:2px; display:flex; align-items:center; justify-content:center;
    color:var(--ink); background:var(--paper-dim);
  }
  .doc-name{font-size:14.5px; color:var(--ink); font-weight:500;}
  .doc-sub{font-family:var(--mono); font-size:11px; color:var(--graphite); opacity:0.55; margin-top:3px;}
  .doc-date{font-family:var(--mono); font-size:11.5px; color:var(--graphite); opacity:0.7; white-space:nowrap;}
  .doc-btn{
    font-family:var(--mono); font-size:11px; letter-spacing:0.05em;
    text-transform:uppercase; text-decoration:none;
    color:var(--stamp); border:1px solid var(--stamp);
    padding:7px 13px; border-radius:3px; white-space:nowrap;
    transition:background .2s ease, color .2s ease;
  }
  .doc-btn:hover{background:var(--stamp); color:var(--paper);}

  /* ===== Contact / footer ===== */
  footer{
    background:var(--ink);
    color:var(--paper);
    padding:80px 32px 40px;
  }
  .footer-inner{max-width:1000px; margin:0 auto;}
  .footer-top{
    display:flex; flex-wrap:wrap; justify-content:space-between;
    gap:40px; padding-bottom:48px; border-bottom:1px solid rgba(250,247,240,0.15);
  }
  footer h2.section-title{color:var(--paper);}
  footer .exhibit{color:#E8A798;}
  .contact-line{
    font-family:var(--serif); font-size:1.5rem; margin-top:10px;
  }
  .contact-line a{text-decoration:none; border-bottom:1px solid rgba(250,247,240,0.35);}
  .contact-line a:hover{border-color:var(--paper);}
  .footer-links{display:flex; flex-direction:column; gap:10px; font-family:var(--mono); font-size:12.5px;}
  .footer-links a{text-decoration:none; opacity:0.8;}
  .footer-links a:hover{opacity:1;}
  .footer-bottom{
    display:flex; justify-content:space-between; flex-wrap:wrap; gap:12px;
    padding-top:28px; font-family:var(--mono); font-size:11px; opacity:0.5;
  }

  @media (max-width:760px){
    .about-grid{grid-template-columns:1fr;}
    .stamp-mark{width:96px; height:96px; top:24px; right:20px;}
    .cover{padding:56px 20px 72px;}
    section{padding:64px 20px;}
    .timeline::before{left:60px;}
    .entry{grid-template-columns:60px 1fr; gap:16px;}
    .entry .node{left:55px;}
    .doc-row{grid-template-columns:36px 1fr; row-gap:6px;}
    .doc-date, .doc-btn{grid-column:2; justify-self:start;}
  }

  @media (prefers-reduced-motion: reduce){
    html{scroll-behavior:auto;}
    .stamp-mark, .entry{animation:none !important; transition:none !important; opacity:1 !important; transform:none !important;}
  }
</style>
</head>
<body>

<div class="grain"></div>

<nav class="tabbar" id="tabbar">
  <span class="filecode">FILE NO. 2026-0847-AN</span>
  <a class="tab active" data-target="about">About</a>
  <a class="tab" data-target="timeline">Record</a>
  <a class="tab" data-target="projects">Exhibits</a>
  <a class="tab" data-target="documents">Documents</a>
  <a class="tab" data-target="contact">Contact</a>
</nav>

<main>

  <section class="cover" style="border-top:none;">
    <div class="stamp-mark"><span>ARCHIVE<br>VERIFIED</span></div>
    <div class="eyebrow">Student Record Archive</div>
    <h1 class="title">Amara N. Okafor</h1>
    <p class="subtitle">A working archive of coursework, research, and correspondence — kept the way a case file is kept: dated, sourced, and open to inspection.</p>

    <dl class="ledger-line">
      <div><dt>Program</dt><dd>B.Sc. Environmental Engineering</dd></div>
      <div><dt>Institution</dt><dd>Lagos State University</dd></div>
      <div><dt>Status</dt><dd>Year 4 · Class of 2027</dd></div>
      <div><dt>Archive opened</dt><dd>Sept 2023</dd></div>
    </dl>
  </section>

  <section id="about">
    <div class="section-head">
      <span class="exhibit">EXHIBIT A</span>
      <h2 class="section-title">About</h2>
    </div>
    <div class="about-grid">
      <div class="about-text">
        <p>I study how small water systems fail — the pumps, the pipes, the decisions made under budget pressure — and I document what I find so the next person doesn't start from zero. Most of my work lives in the gap between fieldwork and paperwork.</p>
        <p>This site is that paperwork, organized. Every project below has a paper trail: proposals, field notes, datasets, and the reports that came out the other end. I'd rather show the process than a polished summary of it.</p>
      </div>
      <div class="card">
        <h3>Record Summary</h3>
        <ul>
          <li><span>Focus areas</span><span>Water systems, GIS, field research</span></li>
          <li><span>Languages</span><span>English, Yoruba, French</span></li>
          <li><span>Tools</span><span>QGIS, Python, AutoCAD</span></li>
          <li><span>Documents on file</span><span>14</span></li>
        </ul>
      </div>
    </div>
  </section>

  <section id="timeline">
    <div class="section-head">
      <span class="exhibit">EXHIBIT B</span>
      <h2 class="section-title">Record of Activity</h2>
    </div>
    <div class="timeline">
      <div class="entry">
        <div class="date">Mar 2026</div>
        <div class="node"></div>
        <div class="body">
          <span class="tag">Research</span>
          <h3>Rural Water Access Survey published</h3>
          <p>Led a 6-village field survey on borehole reliability; findings adopted by the university's civil engineering dept. for a follow-on study.</p>
        </div>
      </div>
      <div class="entry">
        <div class="date">Nov 2025</div>
        <div class="node"></div>
        <div class="body">
          <span class="tag">Internship</span>
          <h3>Field engineer, Delta Water Trust</h3>
          <p>Ten-week placement assessing pump station maintenance logs and training two local technicians on basic diagnostics.</p>
        </div>
      </div>
      <div class="entry">
        <div class="date">Jun 2025</div>
        <div class="node"></div>
        <div class="body">
          <span class="tag">Award</span>
          <h3>Dean's List, third consecutive term</h3>
          <p>Recognized for coursework in fluid mechanics and environmental systems design.</p>
        </div>
      </div>
      <div class="entry">
        <div class="date">Sept 2023</div>
        <div class="node"></div>
        <div class="body">
          <span class="tag">Admission</span>
          <h3>Enrolled, Environmental Engineering</h3>
          <p>Began coursework at Lagos State University with a focus on water infrastructure.</p>
        </div>
      </div>
    </div>
  </section>

  <section id="projects">
    <div class="section-head">
      <span class="exhibit">EXHIBIT C</span>
      <h2 class="section-title">Work on File</h2>
    </div>
    <div class="exhibits">
      <div class="exhibit-card">
        <span class="num">01 / Field Research</span>
        <h3>Borehole Reliability Index</h3>
        <p>A scoring model for predicting pump failure in rural boreholes, built from six villages' worth of maintenance records.</p>
        <div class="meta"><span class="pill">Python</span><span class="pill">QGIS</span><span class="pill">Fieldwork</span></div>
      </div>
      <div class="exhibit-card">
        <span class="num">02 / Capstone</span>
        <h3>Greywater Recovery for Campus Housing</h3>
        <p>A low-cost filtration retrofit proposal for student dormitories, currently under review by facilities.</p>
        <div class="meta"><span class="pill">AutoCAD</span><span class="pill">Cost Modeling</span></div>
      </div>
      <div class="exhibit-card">
        <span class="num">03 / Coursework</span>
        <h3>Flood Risk Mapping, Lagos Mainland</h3>
        <p>Semester-long GIS project layering rainfall, drainage, and elevation data to flag high-risk flood corridors.</p>
        <div class="meta"><span class="pill">GIS</span><span class="pill">Data Viz</span></div>
      </div>
      <div class="exhibit-card">
        <span class="num">04 / Internship</span>
        <h3>Maintenance Log Digitization</h3>
        <p>Converted a decade of paper maintenance logs at Delta Water Trust into a searchable spreadsheet system still in use.</p>
        <div class="meta"><span class="pill">Excel</span><span class="pill">Field Training</span></div>
      </div>
    </div>
  </section>

  <section id="documents">
    <div class="section-head">
      <span class="exhibit">EXHIBIT D</span>
      <h2 class="section-title">Documents</h2>
    </div>
    <div class="filecabinet">
      <div class="doc-row">
        <div class="doc-icon">PDF</div>
        <div><div class="doc-name">Rural Water Access Survey — Full Report</div><div class="doc-sub">42 pages · Research</div></div>
        <div class="doc-date">Mar 2026</div>
        <a href="#" class="doc-btn">View</a>
      </div>
      <div class="doc-row">
        <div class="doc-icon">PDF</div>
        <div><div class="doc-name">Greywater Recovery — Capstone Proposal</div><div class="doc-sub">18 pages · Capstone</div></div>
        <div class="doc-date">Jan 2026</div>
        <a href="#" class="doc-btn">View</a>
      </div>
      <div class="doc-row">
        <div class="doc-icon">XLS</div>
        <div><div class="doc-name">Maintenance Log Dataset (cleaned)</div><div class="doc-sub">1,204 rows · Internship</div></div>
        <div class="doc-date">Nov 2025</div>
        <a href="#" class="doc-btn">Download</a>
      </div>
      <div class="doc-row">
        <div class="doc-icon">PDF</div>
        <div><div class="doc-name">Academic Transcript</div><div class="doc-sub">Official · Registrar</div></div>
        <div class="doc-date">Updated Jul 2026</div>
        <a href="#" class="doc-btn">View</a>
      </div>
      <div class="doc-row">
        <div class="doc-icon">CRT</div>
        <div><div class="doc-name">Dean's List Certificate</div><div class="doc-sub">Term 6</div></div>
        <div class="doc-date">Jun 2025</div>
        <a href="#" class="doc-btn">View</a>
      </div>
    </div>
  </section>

  <footer id="contact">
    <div class="footer-inner">
      <div class="footer-top">
        <div>
          <span class="exhibit">EXHIBIT E</span>
          <h2 class="section-title">Get in Touch</h2>
          <div class="contact-line"><a href="mailto:amara.okafor@example.edu">amara.okafor@example.edu</a></div>
        </div>
        <div class="footer-links">
          <a href="#">LinkedIn ↗</a>
          <a href="#">GitHub ↗</a>
          <a href="#">Download CV (PDF) ↓</a>
        </div>
      </div>
      <div class="footer-bottom">
        <span>Archive maintained since Sept 2023</span>
        <span>File No. 2026-0847-AN · Last updated Aug 2026</span>
      </div>
    </div>
  </footer>

</main>

<script>
  // Tab nav: active state + smooth scroll
  const tabs = document.querySelectorAll('.tab');
  const sections = document.querySelectorAll('main section, footer');

  tabs.forEach(tab => {
    tab.addEventListener('click', (e) => {
      e.preventDefault();
      const targetId = tab.dataset.target;
      const targetEl = document.getElementById(targetId);
      if (targetEl) {
        const y = targetEl.getBoundingClientRect().top + window.scrollY - 60;
        window.scrollTo({ top: y, behavior: 'smooth' });
      }
    });
  });

  const setActive = () => {
    let current = 'about';
    sections.forEach(sec => {
      const rect = sec.getBoundingClientRect();
      if (rect.top <= 120) current = sec.id || current;
    });
    tabs.forEach(t => t.classList.toggle('active', t.dataset.target === current));
  };
  window.addEventListener('scroll', setActive, { passive: true });

  // Timeline reveal on scroll
  const entries = document.querySelectorAll('.entry');
  const io = new IntersectionObserver((items) => {
    items.forEach(item => {
      if (item.isIntersecting) {
        item.target.classList.add('in');
        io.unobserve(item.target);
      }
    });
  }, { threshold: 0.2 });
  entries.forEach(el => io.observe(el));
</script>

</body>
</html>
