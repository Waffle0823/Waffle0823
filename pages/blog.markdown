---
layout: page
title: Blog
permalink: /blog/
---

{%- assign all_categories = "" | split: "," -%}
{%- assign all_types = "" | split: "," -%}
{%- for post in site.posts -%}
  {%- for cat in post.categories -%}
    {%- unless all_categories contains cat -%}
      {%- assign all_categories = all_categories | push: cat -%}
    {%- endunless -%}
  {%- endfor -%}
  {%- assign t = post.type | default: "Article" -%}
  {%- unless all_types contains t -%}
    {%- assign all_types = all_types | push: t -%}
  {%- endunless -%}
{%- endfor -%}
{%- assign all_categories = all_categories | sort -%}
{%- assign all_types = all_types | sort -%}

<section class="blog-section">
  <h1 class="blog-title">Blog</h1>
  <p class="blog-intro">Notes, tutorials and project updates. Filter by type or category, or search the full archive.</p>

  <div class="blog-controls">
    <div class="blog-search">
      <svg class="blog-search__icon" viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
        <circle cx="11" cy="11" r="7"></circle>
        <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
      </svg>
      <input id="blog-search-input" type="search" placeholder="Search posts by title, category, or content…" autocomplete="off" />
    </div>

    <div class="blog-filter-group" role="group" aria-label="Filter by type">
      <span class="blog-filter-label">Type</span>
      <div class="blog-filters" data-filter-type="type">
        <button type="button" class="blog-chip is-active" data-value="">All</button>
        {%- for t in all_types -%}
          <button type="button" class="blog-chip" data-value="{{ t | downcase }}">{{ t }}</button>
        {%- endfor -%}
      </div>
    </div>

    <div class="blog-filter-group" role="group" aria-label="Filter by category">
      <span class="blog-filter-label">Category</span>
      <div class="blog-filters" data-filter-type="category">
        <button type="button" class="blog-chip is-active" data-value="">All</button>
        {%- for cat in all_categories -%}
          <button type="button" class="blog-chip" data-value="{{ cat | downcase }}">#{{ cat }}</button>
        {%- endfor -%}
      </div>
    </div>
  </div>

  <p class="blog-result-count" id="blog-result-count" aria-live="polite"></p>

  <div class="blog-grid" id="blog-grid">
    {%- for post in site.posts -%}
      {%- assign type = post.type | default: "Article" -%}
      {%- assign cat_string = post.categories | join: " " | downcase -%}
      <article class="blog-card"
               data-title="{{ post.title | downcase | escape }}"
               data-content="{{ post.content | strip_html | strip_newlines | downcase | truncate: 600 | escape }}"
               data-type="{{ type | downcase }}"
               data-category="{{ cat_string }}">
        <a class="blog-card__link" href="{{ post.url | relative_url }}" aria-label="{{ post.title | escape }}">
          <div class="blog-card__thumb">
            {%- if post.thumbnail and post.thumbnail != "" -%}
              <img src="{{ post.thumbnail | relative_url }}" alt="" loading="lazy" />
            {%- else -%}
              <div class="blog-card__thumb-fallback" data-letter="{{ type | slice: 0 | upcase }}"></div>
            {%- endif -%}
            <span class="blog-card__type">{{ type }}</span>
          </div>
          <div class="blog-card__body">
            {%- if post.categories.size > 0 -%}
              <div class="blog-card__categories">
                {%- for cat in post.categories -%}
                  <span>#{{ cat }}</span>
                {%- endfor -%}
              </div>
            {%- endif -%}
            <h2 class="blog-card__title">{{ post.title | escape }}</h2>
            {%- if post.excerpt -%}
              <p class="blog-card__excerpt">{{ post.excerpt | strip_html | strip_newlines | truncate: 140 }}</p>
            {%- endif -%}
            <div class="blog-card__date">
              <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%b %-d, %Y" }}</time>
            </div>
          </div>
        </a>
      </article>
    {%- endfor -%}
  </div>

  <p class="blog-empty" id="blog-empty" hidden>No posts match your filters.</p>
</section>

<script>
(function() {
  const input = document.getElementById('blog-search-input');
  const grid = document.getElementById('blog-grid');
  const cards = Array.from(grid.querySelectorAll('.blog-card'));
  const empty = document.getElementById('blog-empty');
  const count = document.getElementById('blog-result-count');
  const filters = { type: '', category: '' };
  let query = '';

  function apply() {
    let visible = 0;
    cards.forEach(card => {
      const title = card.dataset.title || '';
      const content = card.dataset.content || '';
      const type = card.dataset.type || '';
      const cats = card.dataset.category || '';
      const matchQuery = !query || title.includes(query) || content.includes(query) || cats.includes(query);
      const matchType = !filters.type || type === filters.type;
      const matchCat = !filters.category || cats.split(' ').includes(filters.category);
      const show = matchQuery && matchType && matchCat;
      card.style.display = show ? '' : 'none';
      if (show) visible++;
    });
    empty.hidden = visible !== 0;
    count.textContent = visible + (visible === 1 ? ' post' : ' posts');
  }

  input.addEventListener('input', e => {
    query = e.target.value.trim().toLowerCase();
    apply();
  });

  document.querySelectorAll('.blog-filters').forEach(group => {
    const kind = group.dataset.filterType;
    group.addEventListener('click', e => {
      const btn = e.target.closest('.blog-chip');
      if (!btn) return;
      group.querySelectorAll('.blog-chip').forEach(c => c.classList.remove('is-active'));
      btn.classList.add('is-active');
      filters[kind] = btn.dataset.value;
      apply();
    });
  });

  // Pre-fill category from query string (?category=foo)
  const params = new URLSearchParams(window.location.search);
  const initCat = params.get('category');
  if (initCat) {
    const target = document.querySelector('.blog-filters[data-filter-type="category"] .blog-chip[data-value="' + initCat.toLowerCase() + '"]');
    if (target) target.click();
  }

  apply();
})();
</script>

<style>
.blog-section {
  padding: 80px 40px;
  max-width: 1400px;
  margin: 0 auto;
  animation: fadeIn 0.4s ease-out;
}
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}
.blog-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  color: var(--text-heading);
  letter-spacing: -0.02em;
  border-left: 4px solid var(--text-heading);
  padding-left: 20px;
}
.blog-intro {
  max-width: 720px;
  margin: 0 0 3rem;
  font-size: 1.05rem;
  line-height: 1.7;
  color: var(--text-secondary);
  font-weight: 300;
  padding-left: 24px;
}

.blog-controls {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  margin-bottom: 1.25rem;
  padding: 1.5rem;
  background-color: var(--bg-secondary);
  border: 1px solid var(--border-color);
  border-radius: 4px;
}
.blog-search {
  position: relative;
  display: flex;
  align-items: center;
}
.blog-search__icon {
  position: absolute;
  left: 14px;
  color: var(--text-secondary);
  pointer-events: none;
}
.blog-search input {
  width: 100%;
  padding: 12px 14px 12px 42px;
  background-color: var(--bg-primary);
  border: 1px solid var(--border-color);
  color: var(--text-primary);
  font-family: inherit;
  font-size: 0.95rem;
  border-radius: 3px;
  transition: border-color var(--transition-speed) ease;
}
.blog-search input:focus {
  outline: none;
  border-color: var(--text-heading);
}

.blog-filter-group {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.75rem;
}
.blog-filter-label {
  font-size: 0.7rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--text-secondary);
  font-weight: 700;
  min-width: 70px;
}
.blog-filters {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}
.blog-chip {
  padding: 6px 12px;
  background: transparent;
  border: 1px solid var(--border-color);
  color: var(--text-secondary);
  font-family: inherit;
  font-size: 0.8rem;
  letter-spacing: 0.04em;
  cursor: pointer;
  border-radius: 999px;
  transition: all var(--transition-speed) ease;
}
.blog-chip:hover {
  color: var(--text-heading);
  border-color: var(--text-secondary);
}
.blog-chip.is-active {
  background-color: var(--text-heading);
  color: var(--bg-primary);
  border-color: var(--text-heading);
}

.blog-result-count {
  font-size: 0.8rem;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--text-secondary);
  margin: 0 0 1.5rem;
  font-weight: 600;
}

.blog-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 1.5rem;
}

.blog-card {
  background-color: var(--bg-secondary);
  border: 1px solid var(--border-color);
  border-radius: 4px;
  overflow: hidden;
  transition: transform var(--transition-speed) ease, border-color var(--transition-speed) ease, background-color var(--transition-speed) ease;
}
.blog-card:hover {
  transform: translateY(-4px);
  border-color: var(--text-secondary);
  background-color: var(--bg-tertiary);
}
.blog-card__link {
  display: block;
  color: inherit;
  text-decoration: none;
}
.blog-card__link:hover { text-decoration: none; color: inherit; }

.blog-card__thumb {
  position: relative;
  aspect-ratio: 16 / 9;
  overflow: hidden;
  background-color: var(--bg-tertiary);
  padding: 18px;
  box-sizing: border-box;
}
.blog-card__thumb img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  object-position: center;
  transition: transform 0.4s ease;
}
.blog-card:hover .blog-card__thumb img { transform: scale(1.04); }
.blog-card__thumb-fallback {
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, #1a1a1a 0%, #2a2a2a 50%, #0f0f0f 100%);
  display: flex;
  align-items: center;
  justify-content: center;
}
.blog-card__thumb-fallback::after {
  content: attr(data-letter);
  font-size: 4rem;
  font-weight: 800;
  color: rgba(255,255,255,0.08);
  letter-spacing: -0.04em;
}
.blog-card__type {
  position: absolute;
  top: 12px;
  left: 12px;
  background-color: rgba(0,0,0,0.7);
  backdrop-filter: blur(6px);
  color: var(--text-heading);
  font-size: 0.65rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  font-weight: 700;
  padding: 4px 10px;
  border-radius: 2px;
  border: 1px solid rgba(255,255,255,0.1);
}

.blog-card__body {
  padding: 1.25rem 1.4rem 1.4rem;
}
.blog-card__categories {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 0.6rem;
  font-size: 0.7rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--text-secondary);
  font-weight: 600;
}
.blog-card__title {
  font-size: 1.2rem;
  font-weight: 700;
  line-height: 1.3;
  margin: 0 0 0.6rem;
  color: var(--text-heading);
  letter-spacing: -0.01em;
}
.blog-card__excerpt {
  font-size: 0.9rem;
  line-height: 1.6;
  color: var(--text-secondary);
  font-weight: 300;
  margin: 0 0 0.9rem;
}
.blog-card__date {
  font-size: 0.75rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--text-secondary);
  font-weight: 600;
}

.blog-empty {
  text-align: center;
  padding: 3rem 1rem;
  color: var(--text-secondary);
  font-size: 0.95rem;
}

@media screen and (max-width: 768px) {
  .blog-section { padding: 60px 20px; }
  .blog-title { font-size: 2rem; }
  .blog-grid { grid-template-columns: 1fr; }
  .blog-filter-group { flex-direction: column; align-items: flex-start; }
}
</style>
