---
title: "Teaching"
layout: single
showToc: false
hideMeta: true 
---

<style>
/* === Teaching timeline — strong, thick maroon corner hover =============== */

.nk-teach {
  --accent:#7a0019;
  --line:#D9DEE3;
  --line-dark:#3a424a;

  --radius:12px;
  --gap:1rem;
  --left-col:170px;
  --rail-x:22px;
  --dot:12px;

  --pill-bg:Canvas;
  --pill-fg:CanvasText;
}
/* Dark mode: transparent pill, inherit text color */
@media (prefers-color-scheme: dark){
  .nk-teach{
    --line:var(--line-dark);
    --pill-bg: transparent;
    --pill-fg: currentColor;
  }
}

/* Cover theme’s class-based dark modes too */
html[data-theme='dark'] .nk-teach,
html.dark .nk-teach,
body.dark .nk-teach{
  --line:var(--line-dark);
  --pill-bg: transparent;
  --pill-fg: currentColor;
}

/* Layout */
.nk-timeline { position:relative; padding-left:calc(var(--rail-x) + 28px); }
.nk-item {
  position:relative;
  display:grid;
  grid-template-columns:var(--left-col) 1fr;
  gap:var(--gap);
  align-items:center;
  min-height:88px;
  margin:0 0 1rem 0;
}

/* Dot outside pill */
.nk-item::before { content: none; }


/* Pill */
.nk-item > :first-child {
  position: relative;
  display:flex; align-items:center; min-height:56px;
  padding-left:calc(var(--dot) + 25px);
}
.nk-item > :first-child::before {
  content:"";
  position:absolute;
  left:calc(var(--rail-x) - var(--dot) - 6px);
  top:28px;                          /* half of 56px min-height */
  transform:translateY(-50%);
  width:var(--dot); 
  height:var(--dot);
  border-radius:50%;
  background:var(--dot-idle, currentColor);
  box-shadow:0 0 0 3px var(--line);
  opacity:.9; 
  z-index:1;
  transition: background-color .25s ease, box-shadow .25s ease, transform .25s ease;
}
/* Dot goes maroon when the card is interacted with */
/* Dot active when hovered OR while countdown is running */
.nk-item:hover > :first-child::before,
.nk-item:has(.nk-card.nk-active) > :first-child::before {
  background: var(--dot-active, var(--accent, #500000));
  box-shadow: 0 0 0 3px var(--dot-active, var(--accent, #500000));
}


.nk-sem {
  display:inline-block;
  padding:.25rem .6rem;
  border:2px solid var(--pill-fg);
  border-radius:999px;
  background:var(--pill-bg);
  color:var(--pill-fg);
  font-weight:600; white-space:nowrap;
  position:relative; isolation:isolate;
}

/* Card (vertical flip) */
.nk-card {
  position:relative; cursor:pointer; outline:none;
  min-height:120px; perspective:1000px; perspective-origin:50% 35%;
  contain:layout paint; border-radius:var(--radius);
}
.nk-card:focus-visible { outline:2px solid var(--accent); outline-offset:3px; }
.nk-card .nk-conn-h, .nk-card .nk-conn-elbow { display:none !important; }
.nk-card-inner {
  position:relative; width:100%; height:100%; min-height:112px;
  transform-style:preserve-3d; transition:transform .45s ease;
  transform-origin:center center; will-change:transform; transform:translateZ(0);
}
.nk-card.is-flipped .nk-card-inner { transform:rotateX(180deg); }

.nk-face {
  position:relative;  padding:.9rem 1rem;
  border:1.5px solid transparent; border-radius:var(--radius);
  background:transparent; -webkit-backface-visibility:hidden;
  backface-visibility:hidden; transition:border-color .15s ease;
  height: auto; box-sizing: border-box;
  /* hover/active tint */
  .nk-card:hover &.front { 
    background: color-mix(in srgb, #500000 7%, transparent);
  }
  .nk-card.is-flipped &.back {
    background: color-mix(in srgb, #500000 7%, transparent);
  }

  /* dark mode tint */
  body.dark .nk-card:hover &.front {
    background: color-mix(in srgb, #ddd8d8 8%, transparent);
  }
  body.dark .nk-card.is-flipped &.back {
    background: color-mix(in srgb, #ddd8d8 8%, transparent);
  }
}

/* === Dark mode adaptive colors for pills, dots, borders, progress bars === */
body.dark .nk-teach {
  --accent: #ddd8d8;                 /* creamy white in dark mode */
  --dot-active: #ddd8d8;             /* active dot tint */
  --pill-fg: #ddd8d8;                /* pill text/border */
  --pill-bg: transparent;
}
.nk-face.front { transform:rotateX(0); }
.nk-face.back  { transform:rotateX(180deg); position: absolute; inset:0; }
.nk-card:not(.is-flipped) .back { pointer-events:none; }
.nk-card.is-flipped .front { pointer-events:none; }


/* === Ultra-bold, long maroon corner hover lines ========================== */
.nk-card::before,
.nk-card::after,
.nk-card > .corner-tl,
.nk-card > .corner-br {
  content:"";
  position:absolute;
  width:46px; height:46px;              /* longer reach inward */
  border:6px solid var(--accent);       /* much thicker */
  opacity:0;
  transition:opacity .35s cubic-bezier(.4,0,.2,1),
             transform .35s cubic-bezier(.4,0,.2,1);
  pointer-events:none;
}

/* top-left & bottom-right corners drawn by ::before/::after */
.nk-card::before {
  top:-4px; left:-4px;
  border-right:none; border-bottom:none;
  transform:translate(-12px,-12px);
}
.nk-card::after {
  bottom:-4px; right:-4px;
  border-left:none; border-top:none;
  transform:translate(12px,12px);
}

/* extra top-right and bottom-left */
.nk-card > .corner-tl {
  top:-4px; right:-4px;
  border-left:none; border-bottom:none;
  transform:translate(12px,-12px);
}
.nk-card > .corner-br {
  bottom:-4px; left:-4px;
  border-right:none; border-top:none;
  transform:translate(-12px,12px);
}

/* show on hover/focus */
.nk-card:hover::before,
.nk-card:hover::after,
.nk-card:hover > .corner-tl,
.nk-card:hover > .corner-br,
.nk-card:focus-visible::before,
.nk-card:focus-visible::after,
.nk-card:focus-visible > .corner-tl,
.nk-card:focus-visible > .corner-br {
  opacity:1;
  transform:translate(0,0);
}

/* Typography */
.nk-face.front .nk-title { font-weight:700; }
.nk-face.front .nk-desc  { margin-top:.15rem; opacity:.85; }
.nk-face.back .nk-duty-title { font-weight:700; margin-bottom:.25rem; }
.nk-face.back .nk-duty { margin-top:.15rem; opacity:.9; }

/* Dynamic dot color */
.nk-item:has(.nk-card:hover)::before,
.nk-item:has(.nk-card:focus-visible)::before,
.nk-item:has(.nk-card.is-flipped)::before {
  background:var(--accent);
  box-shadow:0 0 0 3px color-mix(in srgb, var(--accent) 35%, var(--line));
}
.nk-item:hover::before { background:var(--accent); }

/* Pill progress ring */
@property --p { syntax:'<angle>'; initial-value:0turn; inherits:false; }
.nk-sem::after {
  content:""; position:absolute; inset:0; border-radius:999px; padding:2.5px;
  background:conic-gradient(var(--accent) var(--p), transparent 0) border-box;
  -webkit-mask:
    linear-gradient(#000 0 0) content-box,
    linear-gradient(#000 0 0);
  -webkit-mask-composite:xor; mask-composite:exclude;
  pointer-events:none; opacity:.98;
}
.nk-item.is-timing .nk-sem::after {
  animation:nk-sem-progress var(--timer-ms, 5000ms) linear both;
}
@keyframes nk-sem-progress { from{ --p:0turn; } to{ --p:1turn; } }

/* Mobile */
@media (max-width:640px) {
  .nk-item { grid-template-columns:1fr; align-items:start; }
}
/* === Font sizing to match site typography ======================= */
.nk-face.front .nk-title {
  font-size: 1.15rem;          /* match paragraph text size */
  font-weight: 600;         /* consistent with h4/h5 tone */
  line-height: 1.3;
}

.nk-face.front .nk-desc {
  font-size: 1rem;       /* slightly smaller than title */
  line-height: 1.4;
  opacity: 0.9;
}

.nk-face.back .nk-duty-title {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 0.25rem;
}

.nk-face.back .nk-duty {
  font-size: 0.95rem;        /* same as small text elsewhere */
  line-height: 1.45;
  opacity: 0.9;
}

/* Optional: improve readability on narrow screens */
@media (max-width: 640px) {
  .nk-face.front .nk-title { font-size: 1.05rem; }
  .nk-face.front .nk-desc,
  .nk-face.back .nk-duty { font-size: 0.95rem; }
}

</style>


<h2 class="section-title">Texas A&M University </h2>
<h3 class="section-subtitle">Teaching Assistant – Department of Statistics</h3>


<div class="nk-teach">
  <div class="nk-timeline">

<!-- ITEM -->
<div class="nk-item">
    <div><span class="nk-sem">Fall 2025</span></div>
    <div class="nk-card" tabindex="0" role="button" aria-pressed="false" aria-label="Toggle duties for STAT 638">
    <!-- connectors -->
    <span class="nk-conn-h" aria-hidden="true"></span>
    <span class="nk-conn-elbow" aria-hidden="true"></span>

<div class="nk-card-inner">
    <!-- Front -->
    <div class="nk-face front">
        <div class="nk-title">STAT 638 – Applied Bayesian Methods</div>
        <div class="nk-desc">Bayesian modeling and computation, including prior specification, posterior inference, MCMC, and hierarchical models.</div>
    </div>
    <!-- Back -->
    <div class="nk-face back">
        <div class="nk-duty-title">Duties</div>
        <div class="nk-duty">Graded HWs, held office hours, prepared solutions, and helped make course materials accessibility-compliant.</div>
    </div>
</div>
</div>
</div>

<!-- ITEM -->
<div class="nk-item">
    <div><span class="nk-sem">Spring 2025</span></div>
    <div class="nk-card" tabindex="0" role="button" aria-pressed="false" aria-label="Toggle duties for STAT 613">
    <span class="nk-conn-h" aria-hidden="true"></span>
    <span class="nk-conn-elbow" aria-hidden="true"></span>
    <div class="nk-card-inner">
        <div class="nk-face front">
        <div class="nk-title">STAT 613 – Statistical Methodology I</div>
        <div class="nk-desc">Foundations of likelihood-based inference, exponential family theory, estimation and testing methods, and regression modeling frameworks.</div>
        </div>
        <div class="nk-face back">
        <div class="nk-duty-title">Duties</div>
        <div class="nk-duty">Held office hours and assisted in grading.</div>
        </div>
    </div>
    </div>
</div>

<!-- ITEM -->
<div class="nk-item">
    <div><span class="nk-sem">Fall 2024</span></div>
    <div class="nk-card" tabindex="0" role="button" aria-pressed="false" aria-label="Toggle duties for STAT 604">
    <span class="nk-conn-h" aria-hidden="true"></span>
    <span class="nk-conn-elbow" aria-hidden="true"></span>
    <div class="nk-card-inner">
        <div class="nk-face front">
        <div class="nk-title">STAT 604 – Statistical Computations</div>
        <div class="nk-desc">Systematic introduction to statistical programming in R and Python, simulation studies, random number generation, and data management for modern data analysis.</div>
        </div>
        <div class="nk-face back">
        <div class="nk-duty-title">Duties</div>
        <div class="nk-duty">Held office hours and assisted in grading.</div>
        </div>
    </div>
    </div>
</div>

<!-- ITEM -->
<div class="nk-item">
    <div><span class="nk-sem">Spring 2024</span></div>
    <div class="nk-card" tabindex="0" role="button" aria-pressed="false" aria-label="Toggle duties for STAT 415">
    <span class="nk-conn-h" aria-hidden="true"></span>
    <span class="nk-conn-elbow" aria-hidden="true"></span>
    <div class="nk-card-inner">
        <div class="nk-face front">
        <div class="nk-title">STAT 415 – Mathematical Statistics II</div>
        <div class="nk-desc">Principles of statistical inference, including estimation theory, interval estimation, hypothesis testing, and Bayesian methods.</div>
        </div>
        <div class="nk-face back">
        <div class="nk-duty-title">Duties</div>
        <div class="nk-duty">Led weekly recitations, held office hours, and assisted in grading.</div>
        </div>
    </div>
    </div>
</div>

<!-- ITEM -->
<div class="nk-item">
    <div><span class="nk-sem">Fall 2023</span></div>
    <div class="nk-card" tabindex="0" role="button" aria-pressed="false" aria-label="Toggle duties for STAT 604">
    <span class="nk-conn-h" aria-hidden="true"></span>
    <span class="nk-conn-elbow" aria-hidden="true"></span>
    <div class="nk-card-inner">
        <div class="nk-face front">
        <div class="nk-title">STAT 604 – Statistical Computations</div>
        <div class="nk-desc">Systematic introduction to statistical programming in R and Python, simulation studies, random number generation, and data management for modern data analysis.</div>
        </div>
        <div class="nk-face back">
        <div class="nk-duty-title">Duties</div>
        <div class="nk-duty">Held office hours and assisted in grading.</div>
        </div>
    </div>
    </div>
</div>

<!-- ITEM -->
<div class="nk-item">
    <div><span class="nk-sem">Spring 2023</span></div>
    <div class="nk-card" tabindex="0" role="button" aria-pressed="false" aria-label="Toggle duties for STAT 656">
    <span class="nk-conn-h" aria-hidden="true"></span>
    <span class="nk-conn-elbow" aria-hidden="true"></span>
    <div class="nk-card-inner">
        <div class="nk-face front">
        <div class="nk-title">STAT 656 – Applied Analytics</div>
        <div class="nk-desc"><div class="nk-desc">Practical introduction to modern statistical learning and predictive modeling in R, including trees, neural networks, and ensemble methods.</div>
        </div>
        </div>
        <div class="nk-face back">
        <div class="nk-duty-title">Duties</div>
        <div class="nk-duty">Held office hours and assisted in grading.</div>
        </div>
    </div>
    </div>
</div>

<!-- ITEM (last; rail stops here) -->
<div class="nk-item">
    <div><span class="nk-sem">Fall 2022</span></div>
    <div class="nk-card" tabindex="0" role="button" aria-pressed="false" aria-label="Toggle duties for STAT 650">
    <span class="nk-conn-h" aria-hidden="true"></span>
    <span class="nk-conn-elbow" aria-hidden="true"></span>
    <div class="nk-card-inner">
        <div class="nk-face front">
        <div class="nk-title">STAT 650 – Statistical Foundations for Data Science</div>
        <div class="nk-desc">Introduction to probability and statistical inference with emphasis on data science applications using Python.</div>
        </div>
        <div class="nk-face back">
        <div class="nk-duty-title">Duties</div>
        <div class="nk-duty">Held office hours and assisted in grading.</div>
        </div>
    </div>
    </div>
</div>

  </div>
</div>

<script>
(function(){
  const FLIP_MS = 5000;                // match your auto-revert time
  const timers = new WeakMap();

  function markTiming(card, on){
    const item = card.closest('.nk-item');
    if(!item) return;
    if(on){
      item.style.setProperty('--timer-ms', FLIP_MS + 'ms');
      item.classList.add('is-timing');
      card.classList.add('nk-active');
    }else{
      // reset animation so next start begins from 0
      item.classList.remove('is-timing');
      item.style.removeProperty('--timer-ms');
      void item.offsetWidth; // reflow to restart animation next time
      card.classList.remove('nk-active');
    }
  }

  function clearAuto(card){
    const id = timers.get(card);
    if(id){ clearTimeout(id); timers.delete(card); }
  }

  function revert(card){
    if(!card.classList.contains('is-flipped')) return;
    card.classList.remove('is-flipped');
    card.setAttribute('aria-pressed','false');
    markTiming(card, false);
    clearAuto(card);
  }

  function setAutoRevert(card){
    clearAuto(card);
    timers.set(card, setTimeout(()=>revert(card), FLIP_MS));
  }

  function toggle(card){
    const flipped = card.classList.toggle('is-flipped');
    card.setAttribute('aria-pressed', String(flipped));
    if(flipped){ markTiming(card,true);  setAutoRevert(card); }
    else       { markTiming(card,false); clearAuto(card);     }
  }

  document.addEventListener('click', (e)=>{
    const card = e.target.closest('.nk-card');
    if(card) toggle(card);
  });

  document.addEventListener('keydown', (e)=>{
    if((e.key === 'Enter' || e.key === ' ') && e.target.classList.contains('nk-card')){
      e.preventDefault(); toggle(e.target);
    }
  });
})();
</script>


