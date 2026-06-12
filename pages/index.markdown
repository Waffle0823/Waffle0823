---
layout: page
title: ""
---

<section id="home" class="hero-section">
  <h1>Hi, I am Waffle</h1>
  <p class="subtitle">Software Developer from Korea</p>
  <p class="description">
    Hobby developer exploring game development with C++ and Raylib. I use C#, Lua, and JavaScript as primary languages. Currently learning Rust while building Civic AI — an AI-powered civic complaint management system.
  </p>
  <div class="hero-links">
    <a href="https://github.com/Waffle0823" target="_blank" class="hero-btn">GitHub</a>
    <a href="https://gitlab.waffly.xyz/waffle" target="_blank" class="hero-btn">GitLab</a>
    <a href="https://www.youtube.com/@WaffleYTChannel" target="_blank" class="hero-btn">YouTube</a>
    <a href="mailto:csshin9928@gmail.com" class="hero-btn">Contact</a>
  </div>
</section>

<section id="highlights" class="highlights-section">
  <h2>Highlights</h2>
  
  <div class="highlight-grid">
    <div class="highlight-card">
      <h3>Farmomatica</h3>
      <p>Currently developing an innovative farming game with unique automation mechanics.</p>
      <span class="tech-badge">C++</span>
      <span class="tech-badge">Raylib</span>
    </div>

    <div class="highlight-card">
      <h3>Roblox-Supabase</h3>
      <p>Full-featured Supabase integration for Roblox, enabling modern backend capabilities.</p>
      <a href="https://github.com/Waffle0823/Roblox-Supabase" target="_blank" class="card-link">View on GitHub →</a>
      <br>
      <span class="tech-badge">Luau</span>
      <span class="tech-badge">Supabase</span>
    </div>

    <div class="highlight-card">
      <h3>Civic AI</h3>
      <p>An AI-powered civic complaint management system I'm building while learning Rust. The Core API subproject is currently in active development.</p>
      <a href="https://gitlab.waffly.xyz/inner-voice/civic-ai/main" target="_blank" class="card-link">View on GitLab →</a>
      <br>
      <span class="tech-badge">Rust</span>
      <span class="tech-badge">AI</span>
    </div>

    <div class="highlight-card">
      <h3>Open Source Contributor</h3>
      <p>Active contributor to various open source projects and maintainer of multiple repositories.</p>
      <span class="tech-badge">Open Source</span>
    </div>
  </div>
</section>

<section id="about" class="about-section">
  <h2>About Me</h2>

  <div class="about-intro">
    <p>I'm a hobby developer based in Suwon, South Korea. I enjoy exploring how things work under the hood — from game engines to backend systems — and building tools that solve real problems. These days I'm learning Rust and building Civic AI, a civic complaint management system, while continuing to ship projects across the Roblox and web ecosystems.</p>
  </div>

  <div class="about-grid">
    <div class="about-block">
      <span class="about-label">Currently</span>
      <h3>Learning Rust &amp; building Civic AI</h3>
      <p>Working on <em>Civic AI</em>, an AI-powered civic complaint management system, and its <em>Core API</em> subproject. Also tinkering with <em>Farmomatica</em> in C++ &amp; Raylib. Daily-driving Arch Linux as my development environment.</p>
    </div>

    <div class="about-block">
      <span class="about-label">Languages</span>
      <ul class="skill-list">
        <li><span>Luau</span><span class="level">Proficient</span></li>
        <li><span>TypeScript / JavaScript</span><span class="level">Proficient</span></li>
        <li><span>C#</span><span class="level">Mid-level</span></li>
        <li><span>C++</span><span class="level">Learning</span></li>
        <li><span>Rust</span><span class="level">Learning</span></li>
      </ul>
    </div>

    <div class="about-block">
      <span class="about-label">Tools &amp; Stack</span>
      <div class="tag-cloud">
        <span>CMake</span>
        <span>Cargo</span>
        <span>Git</span>
        <span>Supabase</span>
        <span>PostgreSQL</span>
        <span>Raylib</span>
        <span>Roblox Studio</span>
      </div>
    </div>

    <div class="about-block">
      <span class="about-label">Elsewhere</span>
      <ul class="link-list">
        <li><a href="https://github.com/Waffle0823" target="_blank">GitHub</a></li>
        <li><a href="https://gitlab.waffly.xyz/waffle" target="_blank">GitLab</a></li>
        <li><a href="https://www.youtube.com/@WaffleYTChannel" target="_blank">YouTube</a></li>
        <li><a href="https://www.instagram.com/waffle0823" target="_blank">Instagram</a></li>
        <li><a href="https://orcid.org/0009-0007-2403-4984" target="_blank">ORCID</a></li>
        <li><a href="mailto:csshin9928@gmail.com">csshin9928@gmail.com</a></li>
      </ul>
    </div>
  </div>
</section>

<style>
html {
  scroll-behavior: smooth;
}

section {
  padding: 80px 40px;
  max-width: 1400px;
  margin: 0 auto;
  animation: fadeIn 0.4s ease-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.hero-section {
  text-align: center;
  padding: 120px 40px 80px;
  border-bottom: 1px solid var(--border-color);
}

.hero-section h1 {
  font-size: 3.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  color: var(--text-heading);
  letter-spacing: -0.03em;
  line-height: 1.1;
}

.subtitle {
  font-size: 1.5rem;
  color: var(--text-secondary);
  margin-bottom: 1.5rem;
  font-weight: 300;
  letter-spacing: 0.02em;
}

.description {
  font-size: 1.05rem;
  line-height: 1.7;
  margin-bottom: 2.5rem;
  color: var(--text-primary);
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
  font-weight: 300;
}

.hero-links {
  display: flex;
  gap: 12px;
  justify-content: center;
  flex-wrap: wrap;
}

.hero-btn {
  padding: 14px 30px;
  background-color: transparent;
  color: var(--text-heading);
  text-decoration: none;
  font-weight: 600;
  transition: background-color 0.2s ease, color 0.2s ease;
  border: 2px solid var(--text-heading);
  font-size: 0.9rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
}

.hero-btn:visited {
  color: var(--text-heading);
}

.hero-btn:hover {
  background-color: var(--text-heading);
  color: var(--bg-primary);
}

.highlights-section h2,
.about-section h2 {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 3rem;
  text-align: left;
  color: var(--text-heading);
  letter-spacing: -0.02em;
  border-left: 4px solid var(--text-heading);
  padding-left: 20px;
}

.highlight-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 0;
  margin-top: 2rem;
  border: 1px solid var(--border-color);
}

.highlight-card {
  background-color: var(--bg-primary);
  padding: 2rem;
  border: none;
  border-right: 1px solid var(--border-color);
  border-bottom: 1px solid var(--border-color);
  transition: all 0.2s ease;
}

.highlight-card:hover {
  background-color: var(--bg-secondary);
}

.highlight-card h3 {
  margin-bottom: 1rem;
  font-size: 1.6rem;
  font-weight: 700;
  color: var(--text-heading);
  letter-spacing: -0.01em;
}

.highlight-card p {
  margin-bottom: 1.2rem;
  line-height: 1.7;
  font-weight: 300;
}

.card-link {
  color: var(--text-heading);
  text-decoration: none;
  font-weight: 600;
  display: inline-block;
  margin-bottom: 0.8rem;
  border-bottom: 2px solid var(--text-heading);
  padding-bottom: 2px;
  transition: all 0.2s ease;
}

.card-link:hover {
  border-bottom-color: var(--text-secondary);
}

.tech-badge {
  display: inline-block;
  background-color: var(--text-heading);
  color: var(--bg-primary);
  padding: 6px 14px;
  font-size: 0.75rem;
  margin-right: 0.5rem;
  margin-top: 0.5rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  transition: all 0.2s ease;
}

.tech-badge:hover {
  background-color: var(--bg-primary);
  color: var(--text-heading);
  outline: 2px solid var(--text-heading);
}

.about-intro {
  max-width: 760px;
  margin: 0 0 3rem;
}

.about-intro p {
  font-size: 1.1rem;
  line-height: 1.8;
  color: var(--text-primary);
  font-weight: 300;
}

.about-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
  margin-top: 1rem;
}

.about-block {
  padding: 1.75rem 0 0;
  border-top: 1px solid var(--border-color);
}

.about-block .about-label {
  display: inline-block;
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--text-secondary);
  margin-bottom: 1rem;
}

.about-block h3 {
  font-size: 1.15rem;
  font-weight: 600;
  color: var(--text-heading);
  margin-bottom: 0.75rem;
  letter-spacing: -0.01em;
  line-height: 1.4;
}

.about-block p {
  font-size: 0.95rem;
  line-height: 1.7;
  color: var(--text-secondary);
  font-weight: 300;
}

.about-block em {
  color: var(--text-primary);
  font-style: normal;
  font-weight: 500;
}

.skill-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.skill-list li {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  padding: 0.55rem 0;
  border-bottom: 1px solid var(--border-color);
  font-size: 0.95rem;
  color: var(--text-primary);
  font-weight: 400;
}

.skill-list li:last-child {
  border-bottom: none;
}

.skill-list .level {
  font-size: 0.72rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--text-secondary);
  font-weight: 500;
}

.tag-cloud {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tag-cloud span {
  display: inline-block;
  padding: 6px 12px;
  border: 1px solid var(--border-color);
  font-size: 0.78rem;
  font-weight: 500;
  color: var(--text-primary);
  letter-spacing: 0.02em;
  transition: border-color 0.2s ease, color 0.2s ease;
}

.tag-cloud span:hover {
  border-color: var(--text-heading);
  color: var(--text-heading);
}

.link-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.link-list li {
  padding: 0.5rem 0;
  border-bottom: 1px solid var(--border-color);
  font-size: 0.95rem;
}

.link-list li:last-child {
  border-bottom: none;
}

.link-list a {
  color: var(--text-primary);
  text-decoration: none;
  transition: color 0.2s ease;
}

.link-list a:hover {
  color: var(--text-heading);
}

@media screen and (max-width: 768px) {
  .hero-section h1 {
    font-size: 2.5rem;
  }

  .subtitle {
    font-size: 1.2rem;
  }

  .description {
    font-size: 1rem;
    max-width: 100%;
  }

  .highlights-section h2,
  .about-section h2 {
    font-size: 2rem;
  }

  section {
    padding: 60px 20px;
  }

  .hero-section {
    padding: 100px 20px 60px;
  }

  .hero-btn {
    padding: 14px 28px;
    font-size: 0.85rem;
  }

  .highlight-grid {
    grid-template-columns: 1fr;
  }

  .highlight-card {
    padding: 1.5rem;
    border-right: none;
  }

  .highlight-card:last-child {
    border-bottom: none;
  }

  .about-grid {
    grid-template-columns: 1fr;
    gap: 0.5rem;
  }

  .about-intro p {
    font-size: 1rem;
  }
}
</style>
