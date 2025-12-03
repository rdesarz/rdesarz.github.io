---
layout: single
title: "Projects"
permalink: /projects/
author_profile: true
classes: wide
---

<style>
  .projects-intro {
    margin-bottom: 2em;
  }
  .projects-intro p {
    font-size: 1em;
    color: #6c757d;
    line-height: 1.6;
  }
  .project-card {
    margin-bottom: 2em;
    padding: 1.5em;
    border: 1px solid #e9ecef;
    border-radius: 8px;
  }
  .project-content {
    display: flex;
    gap: 1.5em;
    align-items: flex-start;
  }
  .project-image {
    flex: 0 0 250px;
  }
  .project-image img {
    width: 100%;
    border-radius: 6px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  }
  .project-body {
    flex: 1;
    min-width: 0;
  }
  .project-body h3 {
    margin-top: 0;
    margin-bottom: 0.5em;
  }
  .project-excerpt {
    color: #6c757d;
    margin-bottom: 1em;
  }
  .tag-list {
    margin-bottom: 1em;
  }
  .tag {
    background: #e9ecef;
    padding: 0.3em 0.8em;
    border-radius: 15px;
    font-size: 0.85em;
    margin-right: 0.5em;
    display: inline-block;
    margin-bottom: 0.5em;
  }
  
  /* Mobile responsive styles */
  @media (max-width: 768px) {
    .projects-intro {
      margin-bottom: 1.5em;
    }
    .project-card {
      padding: 1em;
      margin-bottom: 1.5em;
    }
    .project-content {
      flex-direction: column;
      gap: 1em;
    }
    .project-image {
      flex: 1 1 100%;
      max-width: 100%;
    }
  }
</style>

<div class="projects-intro">
  <p>A collection of my work in robotics, control systems, and autonomous systems—from biped locomotion and motion planning to production autonomous vehicle deployments.</p>
</div>

{% assign projects = site.projects | sort: 'date' | reverse %}
{% for project in projects %}
<div class="project-card">
  <div class="project-content">
    {% if project.header.teaser %}
    <div class="project-image">
      <a href="{{ project.url | relative_url }}">
        <img src="{{ project.header.teaser | relative_url }}" alt="{{ project.title }}">
      </a>
    </div>
    {% endif %}
    <div class="project-body">
      <h3>
        <a href="{{ project.url | relative_url }}" style="text-decoration: none;">{{ project.title }}</a>
      </h3>
      <p class="project-excerpt">{{ project.excerpt }}</p>
      {% if project.tags %}
      <div class="tag-list">
        {% for tag in project.tags %}
        <span class="tag">{{ tag }}</span>
        {% endfor %}
      </div>
      {% endif %}
      <a href="{{ project.url | relative_url }}" class="btn btn--primary">View Project →</a>
    </div>
  </div>
</div>
{% endfor %}
