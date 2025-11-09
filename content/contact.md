---
title: "Contact"
date: 2025-10-21
hidemeta: true
hideTitle: true
description: "How to reach me — email, office, and a quick map."
slug: "contact"
---
<h1 class="title-wave">
  Get in Touch
  <img class="wave-emoji" src="/img/waving_hand_animated_default.png" alt="Waving hand" width="60" height="60">
</h1>

<style>
  .title-wave {
    display: inline-flex;
    align-items: center;
    gap: .6rem;
  }

  .wave-emoji {
    display: inline-block;
    width: 60px;
    height: 60px;
    vertical-align: middle;
    position: relative;
    top: -8px;          /* move upward; tweak between -6px and -10px to taste */
    transform-origin: 70% 70%;
    animation: wave 2.2s ease-in-out infinite;
  }

  @keyframes wave {
    0%, 100% { transform: rotate(0deg); }
    15%      { transform: rotate(10deg); }  /* gentle rise */
    30%      { transform: rotate(-6deg); }
    45%      { transform: rotate(8deg); }
    60%      { transform: rotate(-4deg); }
    75%      { transform: rotate(5deg); }
  }
</style>
<style>
  /* 1) Remove extra space PaperMod puts between header and content */
  .post-single .post-header { margin-bottom: 0 !important; }
  .post-single .post-content { padding-top: 0 !important; margin-top: 0 !important; }

  /* 2) Ensure the first element (your custom title) has no top margin */
  .post-single .post-content > *:first-child { margin-top: 0 !important; }

  /* 3) Last-mile nudge (only if you still see a sliver of space) */
  .post-single .title-wave { margin-top: -0.35rem; }
  @media (max-width: 768px) {
    .post-single .title-wave { margin-top: -0.2rem; }
  }
</style>


<!-- Reusable icons (once per page/site) -->
<svg xmlns="http://www.w3.org/2000/svg" style="display:none">
  <symbol id="icon-mail" viewBox="0 0 24 24">
    <path d="M3 5h18a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2H3a2 2 0 0 1-2-2V7a2 2 0 0 1 2-2zm0 2v.01l9 5.49 9-5.5V7H3zm0 2.51V17h18V9.5l-9 5.5-9-5.49z"/>
    </symbol>
  <symbol id="icon-pin" viewBox="0 0 24 24">
    <path d="M12 2a7 7 0 0 0-7 7c0 5.25 7 13 7 13s7-7.75 7-13a7 7 0 0 0-7-7zm0 9.5a2.5 2.5 0 1 1 0-5 2.5 2.5 0 0 1 0 5z"/>
  </symbol>
</svg>

<style>
  /* Let headings keep their theme styles, just arrange icon + text nicely */
  .icon {
    width: 1em;         /* scales with heading font-size */
    height: 1em;
    vertical-align: -0.15em;
    fill: currentColor; /* auto light/dark */
    color: var(--accent, #500000);
  }

  /* Dark mode overrides — cover common theme toggles */
  html.dark .icon,
  body.dark .icon,
  html[data-theme="dark"] .icon,
  :root[data-theme="dark"] .icon {
    color: currentColor !important; /* or #ddd if you want fixed gray */
    fill: currentColor;
  }
  /* If your content container uses a different selector (e.g., .post-content),
     feel free to scope these to `.post-content h4` instead of `h4`. */
  h4.iconized {
    display: inline-flex;
    align-items: center;
    gap: .45em;
    margin-bottom: 0.4rem;
  }

  /* Columns */
  .contact-row {
    display: flex;
    flex-wrap: wrap;
    gap: 2rem;
    justify-content: space-between;
    align-items: flex-start;
    margin-top: 1rem;
  }
  .contact-col {
    flex: 1;
    min-width: 250px;
    line-height: 1.6;
  }

</style>



<style>
  /* Indent text that follows the contact-label */
  .contact-col {
    flex: 1;
    min-width: 250px;
    line-height: 1.6;
    font-weight: 450;
    font-size: 1rem; /* slightly larger for breathing room */
    margin-bottom: 0.3rem; /* Margin at bottm */
  }

  .contact-col .contact-label {
    display: inline-flex;
    align-items: center;
    gap: .4em;
    font-weight: 800;
    color: var(--accent, #500000);
    text-transform: uppercase;
    letter-spacing: .05em;
    font-size: 1rem;
    margin-bottom: 0.8rem; /* Margin at bottm */
  }

  /* indent text only (not the label) */
  .contact-col {
    display: flex;
    flex-direction: column;
  }
  .contact-col .contact-label + br,
  .contact-col .contact-label + * {
    margin-left: 1.35em; /* adjust between 1.2–1.6em for your taste */
  }

  
   /* Match PaperMod gray tone in dark mode */
  html.dark .contact-label,
  body.dark .contact-label,
  html[data-theme="dark"] .contact-label {
    color: #b4b4b4; /* neutral gray matching PaperMod's text tone in dark mode */
  }
</style>




<div style="display: flex; flex-wrap: wrap; gap: 2rem; justify-content: space-between; align-items: flex-start;">


<div class="contact-col">

<h3 class="contact-label">
  <svg class="icon" aria-hidden="true"><use href="#icon-mail"/></svg> EMAIL
</h3>

<span style="font-family: monospace;">niladrik[at]tamu[dot]edu</span>

</div>

<div class="contact-col">

  <h3 class="contact-label"> 
    <svg class="icon" aria-hidden="true"><use href="#icon-pin"/></svg> Office location
  </h3>

  
  Room 460<br>
  Blocker Building (BLOC)<br>
  3143 TAMU | 155 Ireland St<br>
  College Station, TX 77843-3143<br>
  USA

</div>




</div>



<iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d1743.5804583667828!2d-96.34321489613892!3d30.619516895521986!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x864683966993d2d7%3A0x5c96a35581fb22a4!2sDepartment%20of%20Statistics!5e1!3m2!1sen!2sus!4v1762360573317!5m2!1sen!2sus" width="700" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>


<style>
  iframe {
    border-radius: 0.6rem;         /* roundness */
    overflow: hidden;
    box-shadow: 0 3px 10px rgba(0,0,0,0.08); /* optional soft shadow */
  }

  @media (prefers-color-scheme: dark) {
    iframe {
      filter: brightness(0.9) contrast(1.05); /* optional dark mode tweak */
    }
  }
</style>

