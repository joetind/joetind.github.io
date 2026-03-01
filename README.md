<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Joe's Garden Planner — Lawrence, KS</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{--soil:#2C1810;--soil-light:#3D2317;--leaf:#4A7C59;--leaf-dark:#2D5A3A;--sun:#E8A832;--cream:#FAF3E8;--cream-dark:#EDE1CC;--text:#1A1208;--text-light:#5C4A2E;--card-bg:rgba(255,255,255,.92);--frost-blue:#5DADE2;--ar:#E74C3C;--ay:#F39C12;--ag:#27AE60}
*{margin:0;padding:0;box-sizing:border-box}
body{font-family:'Outfit',sans-serif;background:var(--cream);color:var(--text);overflow-x:hidden}

/* Hero */
.hero{background:linear-gradient(135deg,var(--soil),var(--soil-light) 40%,var(--leaf-dark));padding:3rem 2rem 2.5rem;position:relative;overflow:hidden}
.hero::before{content:'';position:absolute;top:-50%;right:-20%;width:500px;height:500px;background:radial-gradient(circle,rgba(232,168,50,.15),transparent 70%);border-radius:50%}
.hc{max-width:1200px;margin:0 auto;position:relative;z-index:1}
.hero h1{font-family:'DM Serif Display',serif;font-size:clamp(2rem,5vw,3.2rem);color:var(--cream);line-height:1.15}
.hero h1 span{color:var(--sun)}
.hm{display:flex;gap:1.5rem;margin-top:1rem;flex-wrap:wrap}
.badge{display:inline-flex;align-items:center;gap:.4rem;background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.15);padding:.35rem .8rem;border-radius:100px;color:#EDE1CC;font-size:.85rem;backdrop-filter:blur(4px)}

/* Weather */
.wb{background:var(--card-bg);border-bottom:1px solid var(--cream-dark);padding:1rem 2rem;position:sticky;top:0;z-index:100}
.wi{max-width:1200px;margin:0 auto;display:flex;align-items:center;gap:1.5rem;flex-wrap:wrap}
.wc{display:flex;align-items:center;gap:.75rem}
.wt{font-size:1.8rem;font-weight:700;line-height:1}
.wd{font-size:.8rem;color:var(--text-light)}
.wf{display:flex;gap:.75rem;margin-left:auto}
.fd{text-align:center;padding:.3rem .6rem;min-width:56px}
.fd .dn{font-size:.65rem;color:var(--text-light);text-transform:uppercase;font-weight:600;letter-spacing:.5px}
.fd .di{font-size:1.2rem;margin:.15rem 0}
.fd .dt{font-size:.7rem;font-weight:500}
.fa{width:100%;padding:.6rem 1rem;border-radius:8px;font-size:.82rem;font-weight:500;display:flex;align-items:center;gap:.5rem}
.fa.danger{background:rgba(231,76,60,.12);color:var(--ar);border:1px solid rgba(231,76,60,.25)}
.fa.warning{background:rgba(243,156,18,.12);color:var(--ay);border:1px solid rgba(243,156,18,.25)}
.fa.safe{background:rgba(39,174,96,.12);color:var(--ag);border:1px solid rgba(39,174,96,.25)}

/* Nav */
.nt{max-width:1200px;margin:0 auto;padding:1.25rem 2rem 0;display:flex;gap:.5rem;flex-wrap:wrap}
.tb{padding:.55rem 1.1rem;border:1px solid var(--cream-dark);border-bottom:none;border-radius:10px 10px 0 0;background:0 0;font-family:'Outfit',sans-serif;font-size:.85rem;font-weight:500;color:var(--text-light);cursor:pointer;transition:all .2s}
.tb:hover{background:rgba(74,124,89,.08)}
.tb.active{background:var(--card-bg);color:var(--leaf-dark);border-color:#6B9F7D;font-weight:600}

/* Sections */
.sec{display:none;max-width:1200px;margin:0 auto;padding:0 2rem 3rem}
.sec.active{display:block}
.sc{background:var(--card-bg);border-radius:0 12px 12px 12px;border:1px solid var(--cream-dark);padding:2rem;margin-bottom:1.5rem;box-shadow:0 2px 12px rgba(0,0,0,.04)}
h2{font-family:'DM Serif Display',serif;font-size:1.6rem;color:var(--soil);margin-bottom:1rem}
.desc{color:var(--text-light);font-size:.88rem;margin-bottom:1.25rem;line-height:1.5}

/* Trays */
.tg{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:1.25rem}
.tray{background:linear-gradient(145deg,#D2B48C,#C4A67A);border-radius:12px;padding:1.25rem 1rem 1rem;border:3px solid #A0826D;box-shadow:inset 0 2px 8px rgba(0,0,0,.15),0 4px 12px rgba(0,0,0,.1);position:relative}
.tl{position:absolute;top:-10px;left:12px;background:var(--soil);color:var(--cream);padding:.2rem .7rem;border-radius:6px;font-size:.6rem;font-weight:600;text-transform:uppercase;letter-spacing:1px;white-space:nowrap}
.tp{display:grid;grid-template-columns:1fr 1fr;gap:6px;margin-top:.3rem}
.pod{aspect-ratio:1;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:.48rem;font-weight:700;text-align:center;color:#fff;text-shadow:0 1px 2px rgba(0,0,0,.4);cursor:pointer;transition:transform .15s;line-height:1.15;padding:2px;border:2px solid rgba(255,255,255,.2);box-shadow:inset 0 -3px 6px rgba(0,0,0,.2),0 2px 4px rgba(0,0,0,.15)}
.pod:hover{transform:scale(1.1);z-index:2}
.pod.empty{background:#8B7355;opacity:.2;cursor:default;border-style:dashed}
.pod.empty:hover{transform:none}
.pod.tomato{background:radial-gradient(circle at 35% 35%,#E05545,#96281B)}
.pod.pepper{background:radial-gradient(circle at 35% 35%,#EF5350,#B71C1C)}
.pod.herb{background:radial-gradient(circle at 35% 35%,#4CAF50,#1B5E20)}
.pod.greens{background:radial-gradient(circle at 35% 35%,#66BB6A,#2E7D32)}
.pod.squash{background:radial-gradient(circle at 35% 35%,#FFC107,#F57F17)}
.pod.brassica{background:radial-gradient(circle at 35% 35%,#42A5F5,#1565C0)}
.pod.eggplant{background:radial-gradient(circle at 35% 35%,#AB47BC,#4A148C)}
.pod.lemongrass{background:radial-gradient(circle at 35% 35%,#AED581,#558B2F)}
.pod.chili{background:radial-gradient(circle at 35% 35%,#FF7043,#BF360C)}
.pod.asparagus{background:radial-gradient(circle at 35% 35%,#81C784,#1B5E20)}
.trd{grid-column:1/-1;height:1px;background:rgba(0,0,0,.08);margin:2px 0}

/* Plant Cards */
.pc-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(290px,1fr));gap:1.25rem}
.pc{background:#fff;border-radius:12px;overflow:hidden;border:1px solid var(--cream-dark);transition:transform .2s,box-shadow .2s}
.pc:hover{transform:translateY(-3px);box-shadow:0 8px 24px rgba(0,0,0,.08)}
.pi{height:140px;background-size:cover;background-position:center;position:relative;display:flex;align-items:center;justify-content:center}
.pi .cb{position:absolute;top:10px;right:10px;background:rgba(0,0,0,.65);color:#fff;padding:.25rem .6rem;border-radius:100px;font-size:.75rem;font-weight:600;z-index:2}
.pi .tb2{position:absolute;bottom:10px;left:10px;padding:.2rem .6rem;border-radius:100px;font-size:.7rem;font-weight:600;color:#fff;text-transform:uppercase;letter-spacing:.5px;z-index:2}
.pi .efb{font-size:5rem;z-index:1;filter:drop-shadow(0 4px 16px rgba(0,0,0,.3))}
.pb{padding:1rem}
.pb h4{font-family:'DM Serif Display',serif;font-size:1.05rem;color:var(--soil);margin-bottom:.4rem}
.pm{display:grid;grid-template-columns:1fr 1fr;gap:.4rem;margin-top:.75rem}
.pmi{font-size:.73rem;color:var(--text-light);display:flex;align-items:center;gap:.3rem}
.pmi strong{color:var(--text);font-weight:600}
.ps{margin-top:.75rem;padding-top:.75rem;border-top:1px solid var(--cream-dark)}
.sd{width:8px;height:8px;border-radius:50%;display:inline-block;margin-right:.4rem}
.sd.ready{background:var(--ag)}.sd.soon{background:var(--ay)}.sd.wait{background:var(--frost-blue)}

/* Layout selector */
.ls{display:flex;gap:.5rem;margin-bottom:1.25rem;flex-wrap:wrap}
.lb{padding:.5rem 1rem;border:2px solid var(--cream-dark);border-radius:8px;background:#fff;font-family:'Outfit',sans-serif;font-size:.82rem;font-weight:500;color:var(--text-light);cursor:pointer;transition:all .2s}
.lb:hover{border-color:#6B9F7D;color:var(--leaf-dark)}
.lb.active{border-color:var(--leaf);background:rgba(74,124,89,.08);color:var(--leaf-dark);font-weight:600}
.ld{font-size:.82rem;color:var(--text-light);margin-bottom:1rem;padding:.75rem 1rem;background:rgba(74,124,89,.06);border-radius:8px;border-left:3px solid var(--leaf);line-height:1.5}

/* Garden bed */
.gc{overflow-x:auto;padding:.5rem 0}
.gb{min-width:900px;background:#5C4033;border-radius:12px;padding:1.5rem;border:3px solid #3E2723}
.gbi{text-align:center;color:var(--cream);font-size:.72rem;margin-bottom:1rem;opacity:.6}
.gr{display:flex;gap:3px;align-items:stretch;margin-bottom:5px}
.grl{width:140px;display:flex;align-items:center;font-size:.68rem;color:var(--cream);font-weight:500;padding-right:8px;flex-shrink:0;justify-content:flex-end;text-align:right;line-height:1.2}
.gps{height:32px;border-radius:4px;display:flex;align-items:center;justify-content:center;font-size:.9rem;cursor:pointer;transition:all .15s;min-width:20px}
.gps:hover{transform:scaleY(1.25);z-index:2;filter:brightness(1.15)}
.gsp{height:32px;background:#6D4C30;opacity:.2;border-radius:3px;min-width:3px}
.sl{display:flex;align-items:center;padding-left:8px;font-size:.7rem;flex-shrink:0;min-width:36px}
.gl{display:flex;flex-wrap:wrap;gap:.75rem;margin-top:1.25rem;padding-top:1rem;border-top:1px solid rgba(255,255,255,.1)}
.gli{display:flex;align-items:center;gap:.35rem;font-size:.72rem;color:var(--cream);opacity:.85}
.gls{width:14px;height:14px;border-radius:4px;border:1px solid rgba(255,255,255,.2)}
.compass{display:flex;align-items:center;justify-content:space-between;padding:.5rem 0;font-size:.75rem;color:var(--text-light);min-width:900px}
.compass span{font-weight:600}

/* Timeline */
.tlc{overflow-x:auto}
.tl2{min-width:800px}
.tlh{display:grid;grid-template-columns:180px repeat(8,1fr);margin-bottom:.5rem}
.tlm{text-align:center;font-size:.72rem;font-weight:600;color:var(--text-light);text-transform:uppercase;letter-spacing:.5px;padding:.5rem 0;border-bottom:2px solid var(--cream-dark)}
.tlm.cur{color:var(--leaf-dark);border-color:var(--leaf)}
.tlr{display:grid;grid-template-columns:180px repeat(8,1fr);align-items:center;padding:.5rem 0;border-bottom:1px solid rgba(0,0,0,.04)}
.tln{font-size:.82rem;font-weight:600;padding-right:1rem}
.tlcl{height:28px;position:relative;display:flex;align-items:center}
.tlb{height:12px;border-radius:6px;position:absolute;opacity:.85}
.tlb.ind{background:var(--frost-blue)}.tlb.out{background:var(--leaf)}.tlb.har{background:#C0392B}
.tll{display:flex;gap:1.5rem;margin-top:1rem;flex-wrap:wrap}
.tlli{display:flex;align-items:center;gap:.4rem;font-size:.78rem;color:var(--text-light)}
.tlls{width:20px;height:8px;border-radius:4px}

/* Calendar */
.ct{width:100%;border-collapse:collapse;font-size:.82rem}
.ct th{text-align:left;padding:.6rem .8rem;border-bottom:2px solid var(--cream-dark);font-weight:600;color:var(--text-light);font-size:.72rem;text-transform:uppercase;letter-spacing:.5px}
.ct td{padding:.7rem .8rem;border-bottom:1px solid var(--cream-dark);vertical-align:middle}
.ct tr:hover td{background:rgba(74,124,89,.04)}

/* Tooltip */
.tt{display:none;position:fixed;background:var(--soil);color:var(--cream);padding:.6rem .9rem;border-radius:8px;font-size:.78rem;z-index:1000;pointer-events:none;max-width:240px;line-height:1.4;box-shadow:0 8px 24px rgba(0,0,0,.25)}
.tt.show{display:block}

.ld2{display:flex;align-items:center;gap:.5rem;color:var(--text-light);font-size:.85rem}
.ld2 .sp{width:18px;height:18px;border:2px solid var(--cream-dark);border-top-color:var(--leaf);border-radius:50%;animation:spin .8s linear infinite}
@keyframes spin{to{transform:rotate(360deg)}}
@keyframes fadeIn{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:translateY(0)}}
.sec.active .sc{animation:fadeIn .3s ease}
@media(max-width:768px){.hero{padding:2rem 1rem 1.5rem}.sc{padding:1.25rem}.tg{grid-template-columns:1fr 1fr}.pc-grid{grid-template-columns:1fr}.wf{display:none}.nt{padding:1rem 1rem 0}.sec{padding:0 1rem 2rem}}
</style>
</head>
<body>

<div class="hero"><div class="hc">
  <h1>Joe's <span>Garden Planner</span></h1>
  <div class="hm">
    <span class="badge">📍 Lawrence, KS</span><span class="badge">🌱 Zone 6b</span>
    <span class="badge">📐 30′ × 4′ Bed</span><span class="badge">❄️ Last Frost ~Apr 15</span>
    <span class="badge">🌰 43 Seeds</span>
  </div>
</div></div>

<div class="wb"><div class="wi" id="wBar"><div class="ld2"><div class="sp"></div>Fetching Lawrence, KS weather...</div></div></div>

<div class="nt" id="nav">
  <button class="tb active" data-t="trays">🌱 Seed Trays</button>
  <button class="tb" data-t="plants">🪴 Plant Guide</button>
  <button class="tb" data-t="garden">🗺️ Garden Layouts</button>
  <button class="tb" data-t="schedule">📅 Schedule</button>
</div>

<div class="sec active" id="trays"><div class="sc">
  <h2>Seed Trays</h2>
  <p class="desc">5 trays × 10 pods (2 wide × 5 rows). Plants fill in 2-wide blocks. Wildflowers removed from layout plan. Hover pods for info.</p>
  <div class="tg" id="tGrid"></div>
</div></div>

<div class="sec" id="plants"><div class="sc">
  <h2>Plant Reference Guide</h2>
  <p class="desc">All 14 varieties with growing info for Zone 6b Lawrence, KS. Images load when hosted on GitHub Pages.</p>
  <div class="pc-grid" id="pCards"></div>
</div></div>

<div class="sec" id="garden"><div class="sc">
  <h2>Garden Layout Options</h2>
  <p class="desc">30′ × 4′ bed, single-row planting. Each type gets one row running the 30ft length. Right (east) = most sun. Not every seedling needs to go in — extras are great for succession planting or gifts.</p>
  <div class="ls" id="lSel"></div>
  <div class="ld" id="lDesc"></div>
  <div class="gc">
    <div class="compass"><span>← WEST (shade)</span><span>EAST (full sun) → ☀️</span></div>
    <div class="gb" id="gBed"></div>
  </div>
</div></div>

<div class="sec" id="schedule"><div class="sc">
  <h2>Planting Schedule</h2>
  <p class="desc">Based on Zone 6b, last frost ~Apr 15. Weather bar shows live frost alerts via Open-Meteo.</p>
  <div class="tlc" id="tlCon"></div>
  <div class="tll">
    <div class="tlli"><div class="tlls" style="background:var(--frost-blue)"></div>Start Indoors</div>
    <div class="tlli"><div class="tlls" style="background:var(--leaf)"></div>Growing Outdoors</div>
    <div class="tlli"><div class="tlls" style="background:#C0392B"></div>Harvest</div>
  </div>
</div><div class="sc">
  <h2>Planting Calendar</h2>
  <table class="ct"><thead><tr><th>Plant</th><th>Tray Qty</th><th>Start Indoors</th><th>Transplant</th><th>Direct Sow</th><th>Spacing</th><th>Status</th></tr></thead><tbody id="cBody"></tbody></table>
</div></div>

<div class="tt" id="tip"></div>

<script>
// ============ PLANT DATA ============
const D = {
  cherokee_purple: {
    n:"Cherokee Purple Tomato",s:"Cherokee\nPurple",cnt:4,tray:1,ty:"tomato",cat:"Tomato",
    emoji:"🍅",bg:"#7B1F1F",
    img:"https://images.unsplash.com/photo-1592841200221-a6898f307baa?w=500&h=280&fit=crop&q=80",
    sp:24,sun:"Full Sun 8+ hrs",water:'1-2" per week',harv:"80-90 days",
    desc:"Large dusky rose-purple beefsteak heirloom. Rich, sweet, smoky flavor. Indeterminate — needs staking. One of the most popular heirloom tomatoes in America.",
    iw:8,ta:1,ha:12,hd:8,sn:5,col:"#96281B"
  },
  korean_long: {
    n:"Korean Long Tomato",s:"Korean\nLong",cnt:2,tray:1,ty:"tomato",cat:"Tomato",
    emoji:"🍅",bg:"#8B3A3A",
    img:"https://images.unsplash.com/photo-1471194402529-8e0f5a675de6?w=500&h=280&fit=crop&q=80",
    sp:24,sun:"Full Sun 8+ hrs",water:'1-2" per week',harv:"75-85 days",
    desc:"Elongated pinkish-red paste tomato with a pointed nose. Meaty, crack-resistant, superb for sauces. Indeterminate, heavy producer until frost.",
    iw:8,ta:1,ha:11,hd:8,sn:5,col:"#C0392B"
  },
  golden_tiger: {
    n:"Golden Tiger Tomato",s:"Golden\nTiger",cnt:2,tray:1,ty:"tomato",cat:"Tomato",
    emoji:"🍅",bg:"#7B6800",
    img:"https://images.unsplash.com/photo-1598512752271-33f913a5af13?w=500&h=280&fit=crop&q=80",
    sp:24,sun:"Full Sun 8+ hrs",water:'1-2" per week',harv:"70-80 days",
    desc:"Golden-yellow medium tomato with striking dark blue-black stripe markings. Sweet with slight tang. Indeterminate, great for canning.",
    iw:8,ta:1,ha:10,hd:10,sn:5,col:"#D4A017"
  },
  red_pepper: {
    n:"Red Bell Pepper",s:"Red\nPepper",cnt:2,tray:1,ty:"pepper",cat:"Pepper",
    emoji:"🫑",bg:"#8B0000",
    img:"https://images.unsplash.com/photo-1563565375-f3fdfdbefa83?w=500&h=280&fit=crop&q=80",
    sp:18,sun:"Full Sun 6-8 hrs",water:'1-2" per week',harv:"70-90 days",
    desc:"Classic sweet red bell pepper. Starts green, ripens to vibrant red. Kitchen staple for salads, roasting, stuffing, and stir-fry.",
    iw:10,ta:2,ha:10,hd:8,sn:4,col:"#E74C3C"
  },
  lemongrass: {
    n:"Lemongrass",s:"Lemon-\ngrass",cnt:4,tray:2,ty:"lemongrass",cat:"Herb",
    emoji:"🌿",bg:"#3B5323",
    img:"https://images.unsplash.com/photo-1509316975850-ff9c5deb0cd9?w=500&h=280&fit=crop&q=80",
    sp:24,sun:"Full Sun 6-8 hrs",water:"Regular, moist",harv:"75-100 days",
    desc:"Aromatic tropical grass for Thai and Vietnamese cooking. Natural mosquito repellent. Grows in tall 3-5ft clumps. Harvest by cutting stalks at base.",
    iw:8,ta:3,ha:12,hd:12,sn:4,col:"#7CB342"
  },
  thai_birds_eye: {
    n:"Thai Bird's Eye Chili",s:"Bird's\nEye",cnt:4,tray:2,ty:"chili",cat:"Pepper",
    emoji:"🌶️",bg:"#8B2500",
    img:"https://images.unsplash.com/photo-1588252303782-cb80119abd6d?w=500&h=280&fit=crop&q=80",
    sp:18,sun:"Full Sun 6-8 hrs",water:'1" per week',harv:"90-120 days",
    desc:"Fiery small chili peppers (50k-100k SHU). Essential for Thai cuisine. Extremely prolific — each plant produces hundreds of peppers.",
    iw:10,ta:2,ha:14,hd:10,sn:4,col:"#E64A19"
  },
  wasabi_arugula: {
    n:"Wasabi Arugula",s:"Wasabi\nArugula",cnt:2,tray:3,ty:"greens",cat:"Greens",
    emoji:"🥬",bg:"#2E8B57",
    img:"https://images.unsplash.com/photo-1622206151226-18ca2c9ab4a1?w=500&h=280&fit=crop&q=80",
    sp:6,sun:"Partial-Full Sun",water:"Even moisture",harv:"21-40 days",
    desc:"Spicy wasabi-flavored arugula. Ultra-fast cool-season green. Bolts in heat — plant early spring and again in fall. Succession sow every 3 weeks.",
    iw:0,ta:-4,ds:4,ha:4,hd:6,sn:2,col:"#43A047"
  },
  yod_fah: {
    n:"Yod Fah (Chinese Broccoli / Gai Lan)",s:"Yod Fah\nGai Lan",cnt:4,tray:3,ty:"brassica",cat:"Brassica",
    emoji:"🥦",bg:"#1B5E20",
    img:"https://images.unsplash.com/photo-1584270354949-c26b0d5b4a0c?w=500&h=280&fit=crop&q=80",
    sp:8,sun:"Full to Part Sun",water:"Consistent",harv:"55-70 days",
    desc:"Thai selection of Chinese broccoli (Gai Lan). Tender stalks taste like asparagus meets broccoli, only sweeter. Heat-tolerant. Leaves, stems, and florets all edible. Cut-and-come-again.",
    iw:6,ta:1,ha:8,hd:12,sn:3,col:"#2E7D32"
  },
  asparagus: {
    n:"Asparagus",s:"Aspar-\nagus",cnt:4,tray:3,ty:"asparagus",cat:"Perennial",
    emoji:"🌱",bg:"#006400",
    img:"https://images.unsplash.com/photo-1515471209610-dae1c92d8777?w=500&h=280&fit=crop&q=80",
    sp:18,sun:"Full Sun 8+ hrs",water:'1-2" per week',harv:"2-3 yrs (perennial)",
    desc:"Long-lived perennial. No real harvest for 2-3 years but produces for 20+ years every spring. Give it a permanent end-of-bed spot.",
    iw:12,ta:0,ha:104,hd:8,sn:4,col:"#388E3C"
  },
  brussel_sprouts: {
    n:"Brussels Sprouts",s:"Brussels\nSprouts",cnt:2,tray:4,ty:"brassica",cat:"Brassica",
    emoji:"🥬",bg:"#354F28",
    img:"https://images.unsplash.com/photo-1438118907704-7718ee9a191a?w=500&h=280&fit=crop&q=80",
    sp:24,sun:"Full Sun 6+ hrs",water:'1-1.5" per week',harv:"90-120 days",
    desc:"Cool-season brassica that sweetens after frost. Best planted for fall harvest in Zone 6b. Tall plants 2-3ft — may need staking in wind.",
    iw:6,ta:-2,ha:16,hd:6,sn:3,col:"#558B2F"
  },
  yellow_squash: {
    n:"Yellow Squash",s:"Yellow\nSquash",cnt:2,tray:4,ty:"squash",cat:"Squash",
    emoji:"🟡",bg:"#8B6914",
    img:"https://images.unsplash.com/photo-1596199019783-6dec94879fa9?w=500&h=280&fit=crop&q=80",
    sp:36,sun:"Full Sun 8+ hrs",water:'1-2" per week',harv:"50-65 days",
    desc:"Prolific summer squash — bush variety fits in tighter spaces. Harvest young and often for best flavor. Each plant produces 5-25 lbs per season.",
    iw:3,ta:2,ha:7,hd:10,sn:5,col:"#F9A825"
  },
  nagasaki_eggplant: {
    n:"Nagasaki Long Eggplant",s:"Nagasaki\nEggplant",cnt:2,tray:4,ty:"eggplant",cat:"Nightshade",
    emoji:"🍆",bg:"#3B0054",
    img:"https://images.unsplash.com/photo-1615484477778-ca3b77940c25?w=500&h=280&fit=crop&q=80",
    sp:24,sun:"Full Sun 6-8 hrs",water:'1-2" per week',harv:"65-80 days",
    desc:"Japanese long eggplant — tender, creamy flesh, less bitter than globe types. Excellent grilled, stir-fried, or in miso. Slender 8-12 inch fruits.",
    iw:10,ta:3,ha:10,hd:8,sn:4,col:"#6A1B9A"
  },
  thai_basil: {
    n:"Thai Basil",s:"Thai\nBasil",cnt:4,tray:4,ty:"herb",cat:"Herb",
    emoji:"🌿",bg:"#1B3D1B",
    img:"https://images.unsplash.com/photo-1618375569909-3c8616cf7733?w=500&h=280&fit=crop&q=80",
    sp:12,sun:"Full Sun 6-8 hrs",water:"Even moisture",harv:"60-90 days",
    desc:"Aromatic herb with anise/licorice notes. Purple stems and flowers. Essential for Thai curries, pho, and stir-fries. Pinch flowers to prolong harvest.",
    iw:6,ta:2,ha:8,hd:14,sn:4,col:"#2E7D32"
  },
  cilantro: {
    n:"Cilantro",s:"Cilantro",cnt:3,tray:5,ty:"herb",cat:"Herb",
    emoji:"🌿",bg:"#2D5A27",
    img:"https://images.unsplash.com/photo-1526346698789-22fd84314424?w=500&h=280&fit=crop&q=80",
    sp:6,sun:"Part-Full Sun",water:"Even moisture",harv:"45-70 days",
    desc:"Cool-season herb that bolts fast in Kansas heat. Succession plant every 3 weeks. Let some bolt — seeds become coriander for cooking.",
    iw:0,ta:-2,ds:2,ha:6,hd:4,sn:1,col:"#4CAF50"
  }
};

const TRAYS=[
  {l:"Tray 1 — Tomatoes & Pepper",p:["cherokee_purple","cherokee_purple","cherokee_purple","cherokee_purple","korean_long","korean_long","golden_tiger","golden_tiger","red_pepper","red_pepper"]},
  {l:"Tray 2 — Lemongrass & Chili",p:["lemongrass","lemongrass","lemongrass","lemongrass","thai_birds_eye","thai_birds_eye","thai_birds_eye","thai_birds_eye",null,null]},
  {l:"Tray 3 — Greens & Perennials",p:["wasabi_arugula","wasabi_arugula","yod_fah","yod_fah","yod_fah","yod_fah","asparagus","asparagus","asparagus","asparagus"]},
  {l:"Tray 4 — Mixed Vegetables",p:["brussel_sprouts","brussel_sprouts","yellow_squash","yellow_squash","nagasaki_eggplant","nagasaki_eggplant","thai_basil","thai_basil","thai_basil","thai_basil"]},
  {l:"Tray 5 — Cilantro",p:["cilantro","cilantro","cilantro",null,null,null,null,null,null,null]}
];

const BED=360; // 30ft
const LAYOUTS={
  maxVariety:{nm:"🌈 Max Variety",desc:"All 14 types — reduce tomatoes to 1 each to fit everything. Great diversity, extras become gifts or succession plants.",
    rows:[{k:"cherokee_purple",q:1},{k:"korean_long",q:1},{k:"golden_tiger",q:1},{k:"yellow_squash",q:2},{k:"lemongrass",q:3},{k:"thai_birds_eye",q:3},{k:"red_pepper",q:2},{k:"nagasaki_eggplant",q:2},{k:"thai_basil",q:4},{k:"asparagus",q:4},{k:"yod_fah",q:4},{k:"brussel_sprouts",q:2},{k:"wasabi_arugula",q:2},{k:"cilantro",q:3}]},
  tomatoHeavy:{nm:"🍅 Tomato & Pepper",desc:"All tomatoes at full count + peppers, chilies, herbs. Skip cool-season greens. Maximum warm-season harvest.",
    rows:[{k:"cherokee_purple",q:4},{k:"korean_long",q:2},{k:"golden_tiger",q:2},{k:"red_pepper",q:2},{k:"thai_birds_eye",q:4},{k:"nagasaki_eggplant",q:2},{k:"thai_basil",q:4},{k:"lemongrass",q:2},{k:"yellow_squash",q:2},{k:"asparagus",q:4}]},
  thaiKitchen:{nm:"🥘 Thai Kitchen",desc:"All chilies, lemongrass, Thai basil, Yod Fah, eggplant. Only 2 tomatoes. Optimized for Thai/Asian cooking.",
    rows:[{k:"thai_birds_eye",q:4},{k:"lemongrass",q:4},{k:"thai_basil",q:4},{k:"yod_fah",q:4},{k:"nagasaki_eggplant",q:2},{k:"cherokee_purple",q:2},{k:"cilantro",q:3},{k:"wasabi_arugula",q:2},{k:"red_pepper",q:2},{k:"asparagus",q:4}]},
  easyProd:{nm:"🌱 Easy & Productive",desc:"Most reliable, highest-yield plants. Proven performers plus asparagus for long-term investment. Skip fussier varieties.",
    rows:[{k:"cherokee_purple",q:3},{k:"korean_long",q:2},{k:"yellow_squash",q:2},{k:"red_pepper",q:2},{k:"thai_birds_eye",q:3},{k:"thai_basil",q:4},{k:"nagasaki_eggplant",q:2},{k:"lemongrass",q:2},{k:"brussel_sprouts",q:2},{k:"asparagus",q:4},{k:"cilantro",q:3}]}
};

// ============ WEATHER ============
const WMO={0:{i:"☀️",d:"Clear"},1:{i:"🌤️",d:"Mostly clear"},2:{i:"⛅",d:"Partly cloudy"},3:{i:"☁️",d:"Overcast"},45:{i:"🌫️",d:"Fog"},48:{i:"🌫️",d:"Rime fog"},51:{i:"🌦️",d:"Drizzle"},53:{i:"🌦️",d:"Drizzle"},55:{i:"🌧️",d:"Heavy drizzle"},61:{i:"🌧️",d:"Light rain"},63:{i:"🌧️",d:"Rain"},65:{i:"🌧️",d:"Heavy rain"},66:{i:"🌨️",d:"Freezing rain"},67:{i:"🌨️",d:"Heavy freezing rain"},71:{i:"❄️",d:"Snow"},73:{i:"❄️",d:"Snow"},75:{i:"❄️",d:"Heavy snow"},80:{i:"🌦️",d:"Showers"},81:{i:"🌧️",d:"Showers"},82:{i:"🌧️",d:"Heavy showers"},95:{i:"⛈️",d:"Storm"},96:{i:"⛈️",d:"Storm/hail"},99:{i:"⛈️",d:"Severe"}};

async function fetchWeather(){
  try{
    const r=await fetch('https://api.open-meteo.com/v1/forecast?latitude=38.9717&longitude=-95.2353&current=temperature_2m,weather_code,wind_speed_10m&daily=weather_code,temperature_2m_max,temperature_2m_min&temperature_unit=fahrenheit&wind_speed_unit=mph&timezone=America/Chicago&forecast_days=7');
    const d=await r.json(),c=d.current,dy=d.daily,w=WMO[c.weather_code]||{i:"🌡️",d:"Unknown"},dn=['Sun','Mon','Tue','Wed','Thu','Fri','Sat'];
    let mn=Infinity,fd='';
    for(let i=0;i<dy.temperature_2m_min.length;i++)if(dy.temperature_2m_min[i]<mn){mn=dy.temperature_2m_min[i];fd=dn[new Date(dy.time[i]).getDay()]}
    let a;
    if(mn<=32)a={l:'danger',m:`🥶 FROST ALERT: ${Math.round(mn)}°F on ${fd} — protect seedlings!`};
    else if(mn<=38)a={l:'warning',m:`⚠️ Cool nights: low ${Math.round(mn)}°F on ${fd}. Row covers ready.`};
    else a={l:'safe',m:`✅ No frost risk this week. Low: ${Math.round(mn)}°F.`};
    let fc='';
    for(let i=1;i<Math.min(6,dy.time.length);i++){const ww=WMO[dy.weather_code[i]]||{i:"🌡️"};fc+=`<div class="fd"><div class="dn">${dn[new Date(dy.time[i]).getDay()]}</div><div class="di">${ww.i}</div><div class="dt">${Math.round(dy.temperature_2m_max[i])}°/${Math.round(dy.temperature_2m_min[i])}°</div></div>`}
    document.getElementById('wBar').innerHTML=`<div class="wc"><span style="font-size:2rem">${w.i}</span><div><div class="wt">${Math.round(c.temperature_2m)}°F</div><div class="wd">${w.d} · ${Math.round(c.wind_speed_10m)} mph</div></div></div><div class="wf">${fc}</div><div class="fa ${a.l}">${a.m}</div>`;
  }catch(e){document.getElementById('wBar').innerHTML='<span>⚠️ Weather unavailable — will work when hosted</span>'}
}

// ============ TRAYS ============
function renderTrays(){
  document.getElementById('tGrid').innerHTML=TRAYS.map(t=>{
    let h='';
    for(let r=0;r<5;r++){
      if(r>0)h+='<div class="trd"></div>';
      for(let c=0;c<2;c++){
        const k=t.p[r*2+c];
        if(!k){h+='<div class="pod empty"></div>';continue}
        const p=D[k];
        h+=`<div class="pod ${p.ty}" onmouseenter="showTip(event,'${k}')" onmouseleave="hideTip()">${p.s}</div>`;
      }
    }
    return`<div class="tray"><div class="tl">${t.l}</div><div class="tp">${h}</div></div>`;
  }).join('');
}

// ============ PLANT CARDS ============
function renderPlantCards(){
  const tc={tomato:'#C0392B',pepper:'#E74C3C',herb:'#27AE60',greens:'#2ECC71',squash:'#F39C12',brassica:'#3498DB',eggplant:'#8E44AD',lemongrass:'#8BC34A',chili:'#FF5722',asparagus:'#4CAF50'};
  const now=new Date(),frost=new Date(now.getFullYear(),3,15);
  document.getElementById('pCards').innerHTML=Object.entries(D).map(([k,p])=>{
    let st='',sc='';
    if(p.iw>0){
      const s=new Date(frost);s.setDate(s.getDate()-p.iw*7);
      if(now<s){st=`Start indoors ${s.toLocaleDateString('en-US',{month:'short',day:'numeric'})}`;sc='wait'}
      else if(now<frost){st='Start indoors NOW';sc='ready'}
      else{st='Ready to transplant';sc='ready'}
    }else if(p.ds){
      const s=new Date(frost);s.setDate(s.getDate()-p.ds*7);
      st=now>=s?'Direct sow NOW':'Direct sow '+s.toLocaleDateString('en-US',{month:'short',day:'numeric'});
      sc=now>=s?'ready':'soon';
    }
    return`<div class="pc">
      <div class="pi" style="background-image:url('${p.img}');background-color:${p.bg}">
        <span class="efb" style="display:none">${p.emoji}</span>
        <span class="cb">×${p.cnt} in tray</span>
        <span class="tb2" style="background:${tc[p.ty]}">${p.cat}</span>
      </div>
      <div class="pb">
        <h4>${p.n}</h4>
        <p style="font-size:.78rem;color:var(--text-light);line-height:1.4">${p.desc}</p>
        <div class="pm">
          <div class="pmi">☀️ <strong>${p.sun}</strong></div>
          <div class="pmi">💧 <strong>${p.water}</strong></div>
          <div class="pmi">📏 <strong>${p.sp}″ apart</strong></div>
          <div class="pmi">🕐 <strong>${p.harv}</strong></div>
        </div>
        ${st?`<div class="ps"><div style="font-size:.78rem;display:flex;align-items:center"><span class="sd ${sc}"></span><strong>${st}</strong></div></div>`:''}
      </div></div>`;
  }).join('');

  // Show emoji fallback if images fail to load
  document.querySelectorAll('.pi').forEach(el=>{
    const img=new Image();
    img.src=el.style.backgroundImage.slice(5,-2);
    img.onerror=()=>{el.style.backgroundImage='none';el.querySelector('.efb').style.display='block'};
  });
}

// ============ GARDEN ============
let curLayout='maxVariety';

function renderLayoutSel(){
  const s=document.getElementById('lSel');
  s.innerHTML=Object.entries(LAYOUTS).map(([k,v])=>`<button class="lb ${k===curLayout?'active':''}" data-l="${k}">${v.nm}</button>`).join('');
  s.onclick=e=>{if(!e.target.dataset.l)return;curLayout=e.target.dataset.l;s.querySelectorAll('.lb').forEach(b=>b.classList.toggle('active',b.dataset.l===curLayout));renderGarden()};
}

function renderGarden(){
  const L=LAYOUTS[curLayout];
  document.getElementById('lDesc').textContent=L.desc;
  const bed=document.getElementById('gBed');
  const si={5:'☀️☀️',4:'☀️',3:'🌤️',2:'⛅',1:'🌥️'};
  const rows=[...L.rows].sort((a,b)=>D[b.k].sn-D[a.k].sn);
  let tot=0;rows.forEach(r=>tot+=r.q*D[r.k].sp);

  let h=`<div class="gbi">30′ bed (360″) — ${tot}″ planted (${Math.round(tot/BED*100)}%) — ${rows.length} rows</div>`;
  rows.forEach(r=>{
    const p=D[r.k],sw=p.sp/BED*100,tw=r.q*p.sp,lp=(BED-tw)/2/BED*100;
    h+=`<div class="gr"><div class="grl">${p.n.split('(')[0].trim()}<br><span style="opacity:.6;font-size:.58rem">×${r.q} · ${p.sp}″</span></div><div style="display:flex;gap:2px;flex:1;align-items:center">`;
    if(lp>1)h+=`<div class="gsp" style="flex:${lp}"></div>`;
    for(let i=0;i<r.q;i++)h+=`<div class="gps" style="flex:0 0 ${sw}%;background:${p.col}" onmouseenter="showTip(event,'${r.k}')" onmouseleave="hideTip()">${p.emoji}</div>`;
    if(lp>1)h+=`<div class="gsp" style="flex:${lp}"></div>`;
    h+=`</div><div class="sl">${si[p.sn]}</div></div>`;
  });

  const used={};rows.forEach(r=>{const p=D[r.k];if(!used[p.ty])used[p.ty]={n:p.cat,c:p.col}});
  h+='<div class="gl">';
  Object.values(used).forEach(u=>h+=`<div class="gli"><div class="gls" style="background:${u.c}"></div>${u.n}</div>`);
  h+='<div class="gli"><div class="gls" style="background:#6D4C30"></div>Open soil</div></div>';
  bed.innerHTML=h;
}

// ============ TIMELINE ============
function renderTimeline(){
  const ms=['Mar','Apr','May','Jun','Jul','Aug','Sep','Oct'],now=new Date(),cm=now.getMonth();
  const frost=new Date(now.getFullYear(),3,15),rs=new Date(now.getFullYear(),2,1),re=new Date(now.getFullYear(),9,31),td=(re-rs)/864e5;
  const pct=d=>Math.max(0,Math.min(100,((d-rs)/864e5/td)*100));

  let h=`<div class="tl2"><div class="tlh"><div class="tlm">Plant</div>`;
  ms.forEach((m,i)=>h+=`<div class="tlm${i+2===cm?' cur':''}">${m}</div>`);
  h+='</div>';

  Object.entries(D).forEach(([k,p])=>{
    const id=new Date(frost);id.setDate(id.getDate()-(p.iw||0)*7);
    const tp=new Date(frost);tp.setDate(tp.getDate()+(p.ta||0)*7);
    const hs=new Date(tp);hs.setDate(hs.getDate()+(p.ha||0)*7);
    const he=new Date(hs);he.setDate(he.getDate()+(p.hd||0)*7);

    h+=`<div class="tlr"><div class="tln">${p.n.split('(')[0].trim()}</div>`;
    for(let i=0;i<8;i++){
      const cs=i/8*100,ce=(i+1)/8*100;
      h+='<div class="tlcl">';
      if(p.iw>0){const bs=pct(id),be=pct(tp);if(bs<ce&&be>cs){const l=Math.max(0,(bs-cs)/(ce-cs)*100),r=Math.min(100,(be-cs)/(ce-cs)*100);h+=`<div class="tlb ind" style="left:${l}%;width:${r-l}%"></div>`}}
      {const bs=pct(tp),be=pct(hs);if(bs<ce&&be>cs){const l=Math.max(0,(bs-cs)/(ce-cs)*100),r=Math.min(100,(be-cs)/(ce-cs)*100);h+=`<div class="tlb out" style="left:${l}%;width:${r-l}%"></div>`}}
      if(p.ha<100){const bs=pct(hs),be=pct(he);if(bs<ce&&be>cs){const l=Math.max(0,(bs-cs)/(ce-cs)*100),r=Math.min(100,(be-cs)/(ce-cs)*100);h+=`<div class="tlb har" style="left:${l}%;width:${r-l}%"></div>`}}
      h+='</div>';
    }
    h+='</div>';
  });
  h+='</div>';
  document.getElementById('tlCon').innerHTML=h;
}

// ============ CALENDAR ============
function renderCalendar(){
  const now=new Date(),frost=new Date(now.getFullYear(),3,15);
  const fmt=d=>d?d.toLocaleDateString('en-US',{month:'short',day:'numeric'}):'—';
  document.getElementById('cBody').innerHTML=Object.entries(D).map(([k,p])=>{
    const id=new Date(frost);id.setDate(id.getDate()-(p.iw||0)*7);
    const tp=new Date(frost);tp.setDate(tp.getDate()+(p.ta||0)*7);
    const ds2=p.ds?(()=>{const d=new Date(frost);d.setDate(d.getDate()-p.ds*7);return d})():null;
    let st='',sc='';
    if(p.iw>0&&now>=id&&now<tp){st='Start Indoors';sc='ready'}
    else if(now>=tp&&now<new Date(tp.getTime()+14*864e5)){st='Transplant Now';sc='ready'}
    else if(now<id){st='Upcoming';sc='wait'}
    else{st='Growing';sc='soon'}
    return`<tr><td><strong>${p.n}</strong></td><td>${p.cnt}</td><td>${p.iw>0?fmt(id):'—'}</td><td>${fmt(tp)}</td><td>${ds2?fmt(ds2):'—'}</td><td>${p.sp}″</td><td><span class="sd ${sc}"></span>${st}</td></tr>`;
  }).join('');
}

// ============ TOOLTIP ============
function showTip(e,k){
  const p=D[k];if(!p)return;const t=document.getElementById('tip');
  t.innerHTML=`<strong>${p.n}</strong><br>☀️ ${p.sun}<br>📏 ${p.sp}″ spacing<br>🕐 ${p.harv}<br>🌱 ×${p.cnt} in trays`;
  t.classList.add('show');t.style.left=(e.clientX+14)+'px';t.style.top=(e.clientY-14)+'px';
}
function hideTip(){document.getElementById('tip').classList.remove('show')}
document.addEventListener('mousemove',e=>{const t=document.getElementById('tip');if(t.classList.contains('show')){t.style.left=(e.clientX+14)+'px';t.style.top=(e.clientY-14)+'px'}});

// ============ TABS ============
document.getElementById('nav').onclick=e=>{
  if(!e.target.classList.contains('tb'))return;
  document.querySelectorAll('.tb').forEach(b=>b.classList.remove('active'));
  document.querySelectorAll('.sec').forEach(s=>s.classList.remove('active'));
  e.target.classList.add('active');
  document.getElementById(e.target.dataset.t).classList.add('active');
};

// ============ INIT ============
fetchWeather();renderTrays();renderPlantCards();renderLayoutSel();renderGarden();renderTimeline();renderCalendar();
setInterval(fetchWeather,18e5);
</script>
</body>
</html>
