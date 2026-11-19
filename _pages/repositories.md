---
layout: page
permalink: /repositories/
title: open source
description: Research code and scientific software I create, maintain, or contribute to.
nav: true
nav_order: 4
---

- **[loopscape](https://github.com/gilpinlab/loopscape)** — co-creator & maintainer. We developed Loopscape in a private repository and released the code publicly without its private commit history.
- **[panda](https://github.com/abao1999/panda)**: co-creator & maintainer. Code for _Panda: Patched Attention for Nonlinear Dynamics_ (ICLR 2026); checkpoints and datasets on [Hugging Face](https://huggingface.co/GilpinLab).
- **[tsfm-lens](https://github.com/abao1999/tsfm-lens)**: co-creator & maintainer. Mechanistic-interpretability tools for time series foundation models; code for _Universal Redundancies in TSFMs_ (ICML 2026 Spotlight).
- **[dysts](https://github.com/gilpinlab/dysts)**: top contributor & maintainer. Numerical integration of a large database of chaotic ODEs.
- **[diffusion-gmm](https://github.com/abao1999/diffusion-gmm)**. Code to reproduce the experiments in _Gaussian Universality for Diffusion Models_.
- **[cphy](https://github.com/williamgilpin/cphy)**: contributor. Graduate computational physics course materials.

---

{% comment %}
{% if site.data.repositories.github_users %}

## GitHub users

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for user in site.data.repositories.github_users %}
    {% include repository/repo_user.liquid username=user %}
  {% endfor %}
</div>

---

{% if site.repo_trophies.enabled %}
{% for user in site.data.repositories.github_users %}
{% if site.data.repositories.github_users.size > 1 %}

  <h4>{{ user }}</h4>
  {% endif %}
  <div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% include repository/repo_trophies.liquid username=user %}
  </div>

---

{% endfor %}
{% endif %}
{% endif %}
{% endcomment %}

{% if site.data.repositories.github_repos %}

## GitHub Repositories

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.liquid repository=repo %}
  {% endfor %}
</div>
{% endif %}
