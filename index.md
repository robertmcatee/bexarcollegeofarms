---
---

<style>
  body { font-family: Palatino, "Palatino Linotype", Georgia, serif; max-width: 44em; margin: 2em auto; padding: 0 1em; line-height: 1.5; color: #1a1a1a; }
  h1, h2 { text-align: center; letter-spacing: .04em; }
  h1 { margin-bottom: 0; }
  .latin { text-align: center; font-style: italic; margin-top: .2em; color: #555; }
  .rule { border: 0; border-top: 2px solid #8a6d2f; margin: 1.5em 0; }
  .entry { margin: 2.5em 0; }
  .entry img { display: block; margin: 0 auto; max-height: 340px; }
  .name-es { color: #555; font-style: italic; }
  .blazon { margin-top: 1em; }
  .label { font-variant: small-caps; letter-spacing: .06em; color: #8a6d2f; }
  .credit { font-size: .85em; color: #666; text-align: center; }
  .stub { text-align: center; color: #666; font-style: italic; }
</style>

# College of Arms of Bexar
<p class="latin">Colegio de Armas de Béxar</p>

<p class="latin">Registrum Armorum San Antonio de Béxar</p>

<hr class="rule">

This is the Roll of Arms of Bexar County, Texas, kept by the College of Arms of Bexar. The Roll is rendered from a single data file: one record per entry — name, blazon, motto, notes — with one image per entry. Entries are added by adding a record, never by editing this page.

<p class="stub">The Roll is newly opened. Two entries stand recorded; the missions, the lineages, and the rest of the county's armory are to follow.</p>

<hr class="rule">

{% for arm in site.data.arms %}
<div class="entry">
  <h2>{{ arm.name }} <span class="name-es">· {{ arm.name_es }}</span></h2>
  <img src="{{ arm.image | relative_url }}" alt="Arms of {{ arm.name }}">
  <p class="credit">{{ arm.image_credit }}</p>
  <p class="blazon"><span class="label">Blazon</span> — {{ arm.blazon }}</p>
  {% if arm.motto %}<p><span class="label">Motto</span> — {{ arm.motto }}</p>{% endif %}
  <p>{{ arm.notes }}</p>
</div>
<hr class="rule">
{% endfor %}
