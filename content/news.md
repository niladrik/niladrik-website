---
title: "Updates"
layout: single
showToc: false
hideMeta: true
---
<div class="ns-accord">

  <!-- ===== 2025 ===== -->
  <details class="ns-year" open>
    <summary>
      <span class="ns-yearlabel">2025</span>
      <span class="ns-yearhint">click to collapse</span>
    </summary>

<ul class="ns-list">
 <!-- <li>
  <span class="ns-month" id="visit-date"></span>
  <span class="ns-body fun">Someone (yes, <em>you</em>!) checked out this website. Thanks for stopping by! :P</span>
</li>
<script>
document.addEventListener("DOMContentLoaded", () => {
  const el = document.getElementById("visit-date");
  if (el) {
    const now = new Date();
    const options = { month: "short", day: "numeric" }; // e.g. "Nov 2"
    el.textContent = now.toLocaleDateString("en-US", options);
  }
});
</script> -->
    <li><span class="ns-month">Oct</span><span class="ns-body">Website launched.</span></li>
    <li><span class="ns-month">Aug</span><span class="ns-body">Preprint available for <em>Adaptive Divide and Conquer with Two Rounds of Communication</em> (Kal et&nbsp;al., 2025). [<a href="https://arxiv.org/abs/2508.17073" target="_blank" rel="noopener">arXiv</a>]</span></li>
    <li><span class="ns-month">Jun</span><span class="ns-body"> Received the Student Poster Award at the <em>2025 IISA Conference</em>.</span></li>
</ul>
  </details>

  <!-- ===== 2024 ===== -->
  <details class="ns-year" open>
    <summary>
      <span class="ns-yearlabel">2024</span>
      <span class="ns-yearhint">click to collapse</span>
    </summary>

<ul class="ns-list">
    <li><span class="ns-month">May</span><span class="ns-body"> Received the Silver Award at the <em>2024 SETCASA Poster Session</em>, Texas A&amp;M University.</span></li>
</ul>
  </details>

  <!-- ===== 2022 ===== -->
  <details class="ns-year" open>
    <summary>
      <span class="ns-yearlabel">2022</span>
      <span class="ns-yearhint">click to collapse</span>
    </summary>

<ul class="ns-list">
    <li><span class="ns-month">Aug</span><span class="ns-body">Received the Lechner Graduate Grant (2022–23), Texas A&M University.</span></li>
    <li><span class="ns-month">Aug</span><span class="ns-body">Joined the Department of Statistics, Texas A&M University.</span></li>
</ul>
  </details>

</div>

<script>
document.addEventListener("DOMContentLoaded", () => {
    // --- Close older years on first load ---
document.querySelectorAll("details.ns-year").forEach((el) => {
  const yearLabel = el.querySelector(".ns-yearlabel");
  const yearText  = yearLabel ? yearLabel.textContent.trim() : "";

  // Only keep 2025 open by default
  if (yearText !== "2025") {
    el.removeAttribute("open");
    const list = el.querySelector(".ns-list");
    if (list) list.style.height = "0px"; // start collapsed for animation script
  }
});

  const DURATION = 550;         // height animation ms
  const STAGGER  = 30;          // per-row text fade stagger

  document.querySelectorAll("details.ns-year").forEach((el) => {
    const list = el.querySelector(".ns-list");
    if (!list) return;

    // Start collapsed height if closed
    if (!el.open) list.style.height = "0px";

    el.addEventListener("click", (e) => {
      // Only toggle when the <summary> is clicked
      if (!e.target.closest("summary")) return;

      e.preventDefault(); // take control of the animation

      const isOpen = el.hasAttribute("open");
      const rows   = Array.from(list.querySelectorAll("li"));
      const texts  = rows.flatMap(li => [
        li.querySelector(".ns-month"),
        li.querySelector(".ns-body")
      ].filter(Boolean));

      const setTextState = (visible) => {
        texts.forEach((node, i) => {
          const delay = i * STAGGER;
          node.style.transitionDelay = visible ? `${delay}ms` : `${Math.max(0, (texts.length-1-i)*STAGGER)}ms`;
          node.style.opacity   = visible ? "1" : "0";
          node.style.transform = visible ? "translateY(0)" : "translateY(-2px)";
        });
      };

      // Prepare transitions
      list.style.overflow   = "hidden";
      list.style.transition = `height ${DURATION}ms ease`;

      if (isOpen) {
        // === Animate closing: fade text first, then shrink height ===
        setTextState(false);

        // lock current height, then go to 0
        list.style.height = list.scrollHeight + "px";
        requestAnimationFrame(() => {
          list.style.height = "0px";
        });

        const tidyClose = () => {
          el.removeAttribute("open");
          list.style.removeProperty("height");
          list.style.removeProperty("overflow");
          list.style.removeProperty("transition");
          texts.forEach(n => n.style.removeProperty("transition-delay"));
          list.removeEventListener("transitionend", tidyClose);
        };
        list.addEventListener("transitionend", tidyClose, { once:true });

      } else {
        // === Animate opening: set open, grow height, then fade text in ===
        el.setAttribute("open", "");

        // Start from 0 height for smooth expansion
        list.style.height = "0px";

        requestAnimationFrame(() => {
          const target = list.scrollHeight;
          list.style.height = target + "px";
          // Start text fade slightly after height growth begins (feels nicer)
          setTimeout(() => setTextState(true), 60);
        });

        const tidyOpen = () => {
          list.style.removeProperty("height");
          list.style.removeProperty("overflow");
          list.style.removeProperty("transition");
          texts.forEach(n => n.style.removeProperty("transition-delay"));
          list.removeEventListener("transitionend", tidyOpen);
        };
        list.addEventListener("transitionend", tidyOpen, { once:true });
      }
    });
  });
});
</script>
