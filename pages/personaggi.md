---
layout: layouts/base.njk
permalink: /personaggi/
title: "Dramatis Personae"
templateEngineOverride: njk
---
<div class="pergamena-container">
  <h1>Dramatis Personae</h1>
  <p>Qui trovate l'elenco dei Protagonisti (PG) e dei principali Personaggi Non Giocanti (PNG) incontrati durante l'avventura nelle terre di Ansalon.</p>

  <div class="sezioni-grid">
  {% for pg in collections.personaggi %}
    <div class="sezione-card scheda-personaggio">
      <div class="personaggio-header">
        <h2>{{ pg.data.title }}</h2>
        {% if pg.data.tipo %}
          <div class="tipo-badge">[{{ pg.data.tipo }}]</div>
        {% endif %}
      </div>

      {% if pg.data.image %}
        <div class="ritratto-container" style="margin: 0 auto 1rem auto;">
          <img src="{{ pg.data.image }}" alt="{{ pg.data.title }}" class="ritratto-img">
        </div>
      {% endif %}

      <p style="text-align: center;">
        <strong>
          {% if pg.data.info_base.razza %}{{ pg.data.info_base.razza }}{% endif %}<br> 
          {% if pg.data.info_base.classi %}
            {% for c in pg.data.info_base.classi %}
              {{ c.nome }} (Liv. {{ c.livello }}){% if not loop.last %} / {% endif %}
            {% endfor %}
          {% else %}
            {{ pg.data.info_base.classe }} (Liv. {{ pg.data.info_base.livello }})
          {% endif %}
        </strong>
      </p>

      <div class="statistiche-grid" style="margin-bottom: 1rem;">
        {% if pg.data.combattimento.ca %}
          <div class="stat-box">
            <span class="stat-label">CA</span>
            <span class="stat-value">{{ pg.data.combattimento.ca }}</span>
          </div>
        {% endif %}
        {% if pg.data.combattimento.pf_max %}
          <div class="stat-box">
            <span class="stat-label">PF</span>
            <span class="stat-value">{{ pg.data.combattimento.pf_max }}</span>
          </div>
        {% endif %}
      </div>

      <p class="cta-link"><a href="{{ pg.url }}">Leggi la scheda completa &rarr;</a></p>
    </div>
  {% else %}
    <p><em>Nessun personaggio registrato per il momento.</em></p>
  {% endfor %}
  </div>
</div>
