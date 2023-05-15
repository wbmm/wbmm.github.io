---
layout: page
title: Equipe
---

<section id="people">
  <div class="columns is-desktop is-variable is-8">

{% unless site.data.people == empty %}
  {% assign per_column = site.data.people.size | divided_by: 3 %}
  {% assign range = per_column | times: 3 | plus: 1 %}
  {% assign i = 0 %}
  {% assign j = 0 %}
  {% for n in (0..range) %}
    {% assign index = i | times: 3 | plus: j %}
    {% if site.data.people[index] %}
      {% assign person = site.data.people[index] %}
      {% if i == 0 %}
        <div class="column is-full-mobile is-one-quarter-dektop">
      {% endif %}
          <div class="card">
            <figure class="image is-128x128">
              <img class="is-rounded" src="{{ person.image | absolute_url }}" alt="{{ person.name }}">
            </figure>
            <div class="card-content has-text-centered">
              <p class="title is-size-6 is-size-4-widescreen">
              {% if person.website %}
                <a href="{{ person.website }}" target="_blank">{{ person.name }}</a>
              {% else %}
                {{ person.name }}
              {% endif %}
              </p>
              <p class="subtitle is-size-7 is-size-6-widescreen">{{ person.position }}</p>
            </div>
          </div>
    {% endif %}
    {% if i == per_column or forloop.last %}
      </div>
      {% assign i = 0 %}
      {% assign j = j | plus: 1 %}
    {% else %}
      {% assign i = i | plus: 1 %}
    {% endif %}
  {% endfor %}
{% endunless %}

  </div>
</section>
