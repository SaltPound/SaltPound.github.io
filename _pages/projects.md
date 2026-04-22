---
title: "Projects"
layout: single
permalink: /projects/
author_profile: false
classes: wide
---

<style>
  .projects-intro {
    color: #666;
    margin: 0 0 1.75rem;
  }
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1.25rem;
    margin: 0 0 2.5rem;
  }
  .project-card {
    display: flex;
    flex-direction: column;
    background: #fff;
    border: 1px solid rgba(0,0,0,0.08);
    border-radius: 0.5rem;
    overflow: hidden;
    text-decoration: none !important;
    color: inherit !important;
    transition: transform 0.18s ease, box-shadow 0.18s ease;
  }
  .project-card:hover,
  .project-card:focus {
    transform: translateY(-3px);
    box-shadow: 0 10px 28px rgba(0,0,0,0.14);
    text-decoration: none !important;
  }
  .project-card .thumb {
    aspect-ratio: 16 / 10;
    background: linear-gradient(135deg, #0F766E 0%, #0B3B44 100%);
    overflow: hidden;
    position: relative;
  }
  .project-card .thumb img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }
  .project-card .thumb-placeholder {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2.6rem;
    font-weight: 700;
    color: rgba(255,255,255,0.85);
    letter-spacing: -0.02em;
  }
  .project-card .body {
    padding: 0.95rem 1.05rem 1.1rem;
    flex: 1;
    display: flex;
    flex-direction: column;
  }
  .project-card .body h2 {
    margin: 0 0 0.3rem;
    font-size: 1.1rem;
    line-height: 1.25;
    border: 0;
    padding: 0;
  }
  .project-card .body p {
    margin: 0 0 0.6rem;
    color: #555;
    font-size: 0.92rem;
    line-height: 1.45;
  }
  .project-card .tags {
    margin-top: auto;
    font-size: 0.78rem;
    color: #888;
  }
  .project-card .tags .tag {
    display: inline-block;
    margin-right: 0.4em;
  }
  .project-card .status {
    display: inline-block;
    font-size: 0.72rem;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    padding: 0.15em 0.5em;
    border-radius: 0.25rem;
    background: #fef3c7;
    color: #92400e;
    margin-left: 0.4rem;
    vertical-align: middle;
  }

  /* Dark-ish skins keep readable */
  @media (prefers-color-scheme: dark) {
    .project-card { background: #1f2328; border-color: rgba(255,255,255,0.1); }
    .project-card .body p { color: #bbb; }
    .project-card .tags { color: #888; }
  }
</style>

<p class="projects-intro">A selection of things I've built, explored, or am
currently working on. Side projects, products, and whatever refuses to stay in a
notebook.</p>

<div class="projects-grid">
  {% assign items = site.projects | sort: "order" %}
  {% for p in items %}
    {% assign link = p.external_url | default: p.url %}
    {% assign is_external = p.external_url | default: false %}
    <a class="project-card" href="{{ link | relative_url }}"{% if is_external %} target="_blank" rel="noopener external"{% endif %}>
      <div class="thumb">
        {% if p.header.teaser %}
          <img src="{{ p.header.teaser | relative_url }}" alt="{{ p.title }}" loading="lazy">
        {% else %}
          <span class="thumb-placeholder">{{ p.title | slice: 0 }}</span>
        {% endif %}
      </div>
      <div class="body">
        <h2>
          {{ p.title }}{% if p.status %}<span class="status">{{ p.status }}</span>{% endif %}
        </h2>
        <p>{{ p.excerpt }}</p>
        {% if p.tags %}
          <div class="tags">
            {% for tag in p.tags %}<span class="tag">#{{ tag }}</span>{% endfor %}
          </div>
        {% endif %}
      </div>
    </a>
  {% endfor %}
</div>
