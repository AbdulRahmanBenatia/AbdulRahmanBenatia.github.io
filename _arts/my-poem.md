---
layout: single
title: "On Linguistics"
type: poetry
date: 2026-04-02
---
<div class="poem">
  <button id="toggle-translation">Show translation</button>

  <div class="line">
    <span class="original">أَنا مُتَشَوِّق لِلتَّعلُّمِ</span>
    <span class="translation">I am eager to learn</span>
  </div>

  <div class="line">
    <span class="original">وَأُحِبُّ اللُّغَةَ</span>
    <span class="translation">And I love language</span>
  </div>

  <div class="line">
    <span class="original">وَأُحِبُّ أَن أُطبِّقَ مَعْرِفَتِي</span>
    <span class="translation">And I love to apply my knowledge</span>
  </div>
</div>


<script>
document.addEventListener('DOMContentLoaded', () => {
  const button = document.getElementById('toggle-translation');
  const translations = document.querySelectorAll('.poem .translation');

  // hide all translations initially
  translations.forEach(t => t.style.display = 'none');

  button.addEventListener('click', () => {
    const isVisible = translations[0].style.display === 'inline';
    translations.forEach(t => t.style.display = isVisible ? 'none' : 'inline');
    button.textContent = isVisible ? 'Show translation' : 'Hide translation';
  });
});
</script>

<style>
.poem .line {
  margin-bottom: 0.6em;
}

.poem .original {
  font-size: 1.2em;
}

.poem .translation {
  display: none; /* start hidden */
  font-style: italic;
  color: #555;
  margin-left: 0.5em;
}

#toggle-translation {
  margin-bottom: 1em;
  background: #f0f0f0;
  border: 1px solid #ccc;
  padding: 0.3em 0.8em;
  cursor: pointer;
  border-radius: 4px;
  font-size: 0.95em;
}
</style>