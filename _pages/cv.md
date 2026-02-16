---
layout: single
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---
Last Update: 2026.2.17

<style>
.cv-btn {
  padding: 0.2rem 0.9rem;
  border: 1px solid #000000;
  border-radius: 6px;
  background: #ffffff;
  color: #3d3d3d;
  text-decoration: none;
  cursor: pointer;
  font-family: "Avenir Next", "Segoe UI", "Helvetica Neue", sans-serif;
  font-size: 0.82rem;
  font-weight: 600;
  letter-spacing: 0.02em;
  opacity: 0.35;
  transition: opacity 0.2s ease, background-color 0.2s ease;
}
.cv-btn:hover {
  opacity: 1;
}
.cv-btn.is-active {
  opacity: 1;
  background: #ffffff;
}
#cv-frame {
  display: block;
  border: 0;
  opacity: 1;
  transition: opacity 0.24s ease;
}
</style>

<div id="cv-switcher" style="margin: 0 0 1rem 0; display: flex; gap: 0.6rem; flex-wrap: wrap; align-items: center;">
  <button id="btn-toggle" class="cv-btn is-active" type="button">Current: EN | Switch to CN</button>
  <a id="btn-download" class="cv-btn" href="/files/cv-en.pdf" download>Download CV (PDF)</a>
  <a id="btn-open" class="cv-btn" href="/files/cv-en.pdf" target="_blank" rel="noopener">Open in new tab</a>
</div>

<div style="border: 1px solid #ddd; border-radius: 8px; overflow: hidden;">
  <iframe
    id="cv-frame"
    src="/files/cv-en.pdf"
    title="CV Viewer"
    width="100%"
    height="980"
  ></iframe>
</div>

<script>
(function () {
  const zhPdf = '/files/cv-zh.pdf';
  const enPdf = '/files/cv-en.pdf';

  const frame = document.getElementById('cv-frame');
  const btnToggle = document.getElementById('btn-toggle');
  const btnDownload = document.getElementById('btn-download');
  const btnOpen = document.getElementById('btn-open');

  let isZh = false;

  function updateUi() {
    const pdf = isZh ? zhPdf : enPdf;
    btnToggle.textContent = isZh ? 'Cn Ver' : 'En Ver';
    btnDownload.href = pdf;
    btnOpen.href = pdf;
  }

  function switchCv() {
    isZh = !isZh;
    const pdf = isZh ? zhPdf : enPdf;

    frame.style.opacity = '0.15';
    window.setTimeout(function () {
      frame.src = pdf;
      updateUi();
      frame.style.opacity = '1';
    }, 160);
  }

  btnToggle.addEventListener('click', switchCv);
  updateUi();
})();
</script>