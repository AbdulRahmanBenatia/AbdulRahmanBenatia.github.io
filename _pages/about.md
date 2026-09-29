---
permalink: /
title: "AbdulRahman Morsy"
description: "PhD student at GWU · Multilingual & cross-cultural NLP for health"
author_profile: true
hide_title: true
redirect_from: 
  - /about/
  - /about.html
---

<section class="hero">
  <p class="hero__kicker"><span class="hero__abdu">Abdu</span> PhD Student · Computer Science · The George Washington University</p>
  <h1 class="hero__name">
    <span class="hero__line">Abdul<em>Rahman</em></span>
    <span class="hero__line hero__line--indent">Morsy</span>
    <span class="hero__ar" lang="ar" dir="rtl" aria-hidden="true">عبد الرحمن</span>
  </h1>
  <button class="namenote__btn namehint" type="button" aria-expanded="false" aria-controls="namenote"><span class="namehint__mark" aria-hidden="true">✱</span> Call me <b>Abdu</b> or <b>AbdulRahman</b>, never <s>Abdul</s>. <span class="namehint__why">why?</span></button>
  <p class="hero__lede">Multilingual &amp; cross-cultural <em>NLP</em>, for health.</p>
  <div class="namenote" id="namenote" role="dialog" aria-label="On my name" hidden>
    <p class="namenote__head"><span>On my name</span><button class="namenote__close" type="button" aria-label="Close">&times;</button></p>
    <div class="namenote__code">
      <p class="namenote__row"><span class="k">s1 = "<bdi class="ar" lang="ar">عبدُ</bdi>"</span><span class="c"># Abdu: "servant of"; also works as "عبدُه" -> Him</span></p>
      <p class="namenote__row"><span class="k">s2 = "<bdi class="ar ar--stop" lang="ar">ال</bdi>"</span><span class="c"># al: "the"; a very bad stop :D</span></p>
      <p class="namenote__row"><span class="k">s3 = "<bdi class="ar" lang="ar">رحمن</bdi>"</span><span class="c"># Rahman: "the Most Merciful (i.e. God)"</span></p>
      <p class="namenote__rule"></p>
      <p class="namenote__line"><span class="k">name ∈ {s1, s1 + s2 + s3}</span></p>
      <p class="namenote__line"><span class="c"># Abdu <b class="ok">✓</b> &nbsp;AbdulRahman <b class="ok">✓</b> &nbsp;Abdul <b class="no">✗</b></span></p>
      <p class="namenote__line"><span class="k">re.fullmatch(r"Abdu|AbdulRahman", name)</span></p>
    </div>
  </div>
</section>

<div class="about">
  <aside class="about__card" aria-label="About the author">
    <figure class="margin__portrait">
      <button class="portrait-open" type="button" data-full="/images/formal.jpg" aria-label="View full-size photo"><span class="margin__crop"><img src="/images/{{ site.author.avatar }}" alt="Portrait of {{ site.author.name }}" width="96" height="96"></span></button>
    </figure>
    <p class="margin__name">{{ site.author.name }}</p>
    <p class="about__bio">{{ site.author.bio }}</p>
    <p class="margin__role"><i class="fas fa-location-dot" aria-hidden="true"></i> {{ site.author.location }}</p>
    {% include social-links.html class="margin__links" %}
  </aside>

  <div class="about__text" markdown="1">

I am a PhD student at The George Washington University, advised by Aya Zirikly. My research focuses on multilingual and cross-cultural NLP, with a particular emphasis on health-related applications.

A lifelong passion for linguistics drives my research, and I am constantly seeking to integrate deep linguistic insights into AI solutions.

Beyond academia, my interests span diverse domains, including literature and poetry, music and singing, logical reasoning, theology, and philosophy, fueling a broad and interdisciplinary perspective that informs both my work and my worldview.

<p class="about__contact"><span>Correspondence</span> abdulrahman [dot] morsy [at] gwu [dot] edu</p>

  </div>

  <figure class="plate">
    <img src="/images/cartoon_image.png" alt="Illustration of the PhD journey: AbdulRahman at a desk surrounded by Arabic poetry, papers and a small robot" width="520">
    <figcaption><span>Fig. 1</span> The PhD journey, as imagined.</figcaption>
  </figure>
</div>

<nav class="index" aria-label="Sections">
  <a href="/publications/"><span>01</span><strong>Publications</strong><em>papers &amp; preprints</em></a>
  <a href="/year-archive/"><span>02</span><strong>Blog</strong><em>essays &amp; reflections</em></a>
  <a href="/arts/"><span>03</span><strong>Art</strong><em>poetry, <span lang="ar">شعر</span>, song</em></a>
  <a href="/cv/"><span>04</span><strong>CV</strong><em>the long version</em></a>
</nav>

<script>
(function () {
  var btn = document.querySelector('.namenote__btn');
  var note = document.getElementById('namenote');
  if (!btn || !note) return;
  var hero = note.parentElement;
  var hoverable = window.matchMedia('(hover: hover) and (pointer: fine)').matches;
  var timer, byHover = false;

  function place() {
    var h = hero.getBoundingClientRect(), b = btn.getBoundingClientRect();
    var w = note.offsetWidth;
    var left = b.left + b.width / 2 - h.left - w / 2;
    left = Math.max(0, Math.min(left, h.width - w));
    note.style.left = left + 'px';
    note.style.top = (b.bottom - h.top + 14) + 'px';
    note.style.setProperty('--nub', (b.left + b.width / 2 - h.left - left) + 'px');
  }
  function open(viaHover) {
    byHover = viaHover === true;
    clearTimeout(timer);
    if (!note.hidden && note.classList.contains('is-open')) return;
    note.hidden = false;
    place();
    void note.offsetWidth;
    note.classList.add('is-open');
    btn.setAttribute('aria-expanded', 'true');
  }
  function close() {
    note.classList.remove('is-open');
    btn.setAttribute('aria-expanded', 'false');
    timer = setTimeout(function () { note.hidden = true; }, 260);
  }
  btn.addEventListener('click', function (e) {
    e.stopPropagation();
    if (btn.getAttribute('aria-expanded') === 'true' && !byHover) { close(); } else { open(); }
  });
  note.querySelector('.namenote__close').addEventListener('click', close);
  note.addEventListener('click', function (e) { e.stopPropagation(); });
  document.addEventListener('click', function () { if (!note.hidden) close(); });
  document.addEventListener('keydown', function (e) {
    if (e.key === 'Escape' && !note.hidden) { close(); btn.focus(); }
  });
  window.addEventListener('resize', function () { if (!note.hidden) place(); });
  if (location.hash === '#name') { setTimeout(open, 600); }
  if (hoverable) {
    [btn, note].forEach(function (el) {
      el.addEventListener('mouseenter', function () { if (note.hidden) { open(true); } else { clearTimeout(timer); } });
      el.addEventListener('mouseleave', function () { if (byHover) { timer = setTimeout(close, 220); } });
    });
  }
})();
</script>
