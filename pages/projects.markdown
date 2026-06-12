---
layout: page
title: Projects
permalink: /projects/
---

<section class="projects-section">
  <h1 class="projects-title">Projects</h1>
  <p class="projects-intro">A selection of open source projects I've built and maintain across GitHub and GitLab.</p>

  <ol class="project-list">
    <li class="project-row">
      <span class="project-row__index">01</span>
      <div class="project-row__body">
        <div class="project-row__head">
          <h2><a href="https://gitlab.waffly.xyz/inner-voice/civic-ai/main" target="_blank" rel="noopener">Civic AI</a></h2>
          <span class="project-row__year">In Development · Rust</span>
        </div>
        <p>A civic complaint management system powered by AI, designed to streamline how citizen reports are collected, triaged, and resolved. Currently learning Rust while building it.</p>
        <div class="project-row__meta">
          <span>Rust</span><span>AI</span><span>Civic Tech</span>
        </div>
      </div>
      <a class="project-row__arrow" href="https://gitlab.waffly.xyz/inner-voice/civic-ai/main" target="_blank" rel="noopener" aria-label="Open Civic AI on GitLab">↗</a>
    </li>

    <li class="project-row">
      <span class="project-row__index">02</span>
      <div class="project-row__body">
        <div class="project-row__head">
          <h2><a href="https://gitlab.waffly.xyz/inner-voice/civic-ai/core-api" target="_blank" rel="noopener">Civic AI · Core API</a></h2>
          <span class="project-row__year">In Development · Rust</span>
        </div>
        <p>The core backend API powering Civic AI — handles complaint intake, processing pipelines, and service endpoints. A subproject of Civic AI.</p>
        <div class="project-row__meta">
          <span>Rust</span><span>API</span><span>Backend</span>
        </div>
      </div>
      <a class="project-row__arrow" href="https://gitlab.waffly.xyz/inner-voice/civic-ai/core-api" target="_blank" rel="noopener" aria-label="Open Civic AI Core API on GitLab">↗</a>
    </li>

    <li class="project-row">
      <span class="project-row__index">03</span>
      <div class="project-row__body">
        <div class="project-row__head">
          <h2><a href="https://github.com/Waffle0823/Roblox-Supabase" target="_blank" rel="noopener">Roblox-Supabase</a></h2>
          <span class="project-row__year">Luau · Backend</span>
        </div>
        <p>Full-featured Supabase integration for Roblox, bringing modern backend capabilities — auth, database, storage — to Roblox experiences.</p>
        <div class="project-row__meta">
          <span>Luau</span><span>Supabase</span><span>Roblox</span>
        </div>
      </div>
      <a class="project-row__arrow" href="https://github.com/Waffle0823/Roblox-Supabase" target="_blank" rel="noopener" aria-label="Open Roblox-Supabase on GitHub">↗</a>
    </li>

    <li class="project-row">
      <span class="project-row__index">04</span>
      <div class="project-row__body">
        <div class="project-row__head">
          <h2><a href="https://github.com/Waffle0823/WaffleEngine" target="_blank" rel="noopener">WaffleEngine</a></h2>
          <span class="project-row__year">In Development · Engine</span>
        </div>
        <p>A custom game engine currently in active development.</p>
        <div class="project-row__meta">
          <span>Engine</span><span>OpenGL</span><span>Game Dev</span>
        </div>
      </div>
      <a class="project-row__arrow" href="https://github.com/Waffle0823/WaffleEngine" target="_blank" rel="noopener" aria-label="Open WaffleEngine on GitHub">↗</a>
    </li>

  </ol>
</section>

<style>
.projects-section {
  padding: 80px 40px;
  max-width: 1400px;
  margin: 0 auto;
  animation: fadeIn 0.4s ease-out;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}

.projects-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  color: var(--text-heading);
  letter-spacing: -0.02em;
  border-left: 4px solid var(--text-heading);
  padding-left: 20px;
}

.projects-intro {
  max-width: 720px;
  margin: 0 0 3rem;
  font-size: 1.05rem;
  line-height: 1.7;
  color: var(--text-secondary);
  font-weight: 300;
  padding-left: 24px;
}

.project-list {
  list-style: none;
  margin: 0;
  padding: 0;
  border-top: 1px solid var(--border-color);
}

.project-row {
  display: grid;
  grid-template-columns: 80px 1fr 60px;
  align-items: start;
  gap: 2rem;
  padding: 3.5rem 1rem;
  min-height: 200px;
  border-bottom: 1px solid var(--border-color);
  position: relative;
  transition: background-color 0.25s ease, padding 0.25s ease;
}

.project-row:hover {
  background-color: var(--bg-secondary);
  padding-left: 1.5rem;
}

.project-row__index {
  font-size: 0.85rem;
  font-weight: 700;
  letter-spacing: 0.18em;
  color: var(--text-secondary);
  padding-top: 0.55rem;
  font-variant-numeric: tabular-nums;
}

.project-row__body {
  min-width: 0;
}

.project-row__head {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  gap: 1rem;
  flex-wrap: wrap;
  margin-bottom: 0.6rem;
}

.project-row__head h2 {
  margin: 0;
  font-size: 1.9rem;
  font-weight: 700;
  letter-spacing: -0.02em;
  line-height: 1.15;
}

.project-row__head h2 a {
  color: var(--text-heading);
  text-decoration: none;
  background-image: linear-gradient(var(--text-heading), var(--text-heading));
  background-repeat: no-repeat;
  background-size: 0 2px;
  background-position: 0 100%;
  transition: background-size 0.3s ease;
  padding-bottom: 2px;
}

.project-row:hover .project-row__head h2 a,
.project-row__head h2 a:hover {
  background-size: 100% 2px;
}

.project-row__year {
  font-size: 0.72rem;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--text-secondary);
  font-weight: 600;
  white-space: nowrap;
}

.project-row__body p {
  margin: 0 0 0.9rem;
  line-height: 1.7;
  font-weight: 300;
  color: var(--text-primary);
  max-width: 65ch;
}

.project-row__meta {
  display: flex;
  flex-wrap: wrap;
  gap: 1.25rem;
  font-size: 0.75rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--text-secondary);
  font-weight: 600;
}

.project-row__meta span {
  position: relative;
}

.project-row__meta span + span::before {
  content: "";
  position: absolute;
  left: -0.65rem;
  top: 50%;
  width: 4px;
  height: 4px;
  background-color: var(--text-secondary);
  border-radius: 50%;
  transform: translateY(-50%);
  opacity: 0.6;
}

.project-row__arrow {
  align-self: center;
  justify-self: end;
  font-size: 1.5rem;
  color: var(--text-heading);
  text-decoration: none;
  width: 48px;
  height: 48px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border: 1px solid var(--border-color);
  transition: transform 0.25s ease, background-color 0.25s ease, color 0.25s ease, border-color 0.25s ease;
}

.project-row:hover .project-row__arrow {
  background-color: var(--text-heading);
  color: var(--bg-primary);
  border-color: var(--text-heading);
  transform: translate(4px, -4px);
}

@media screen and (max-width: 768px) {
  .projects-section { padding: 60px 20px; }
  .projects-title { font-size: 2rem; }
  .projects-intro { padding-left: 24px; }

  .project-row {
    grid-template-columns: 50px 1fr;
    grid-template-areas:
      "index body"
      ".     arrow";
    gap: 1rem 1rem;
    padding: 1.75rem 0.5rem;
  }

  .project-row:hover { padding-left: 0.75rem; }
  .project-row__index { grid-area: index; padding-top: 0.4rem; }
  .project-row__body  { grid-area: body; }
  .project-row__arrow {
    grid-area: arrow;
    justify-self: start;
    width: 42px;
    height: 42px;
    font-size: 1.25rem;
  }

  .project-row__head h2 { font-size: 1.5rem; }
}
</style>
