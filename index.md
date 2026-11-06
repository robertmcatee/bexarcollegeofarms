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
  .blazon { margin-top: 1em; }
  .label { font-variant: small-caps; letter-spacing: .06em; color: #8a6d2f; }
  .credit { font-size: .85em; color: #666; text-align: center; }
  .stub { text-align: center; color: #666; font-style: italic; }
  .filters { text-align: center; margin: 1.5em 0 .5em; }
  .filters button { font-family: inherit; font-variant: small-caps; letter-spacing: .06em; font-size: 1em; color: #8a6d2f; background: none; border: 1px solid #8a6d2f; border-radius: 2em; padding: .25em 1em; margin: 0 .25em; cursor: pointer; }
  .filters button:hover { background: #f3ecd9; }
  .filters button.active { background: #8a6d2f; color: #fff; }
</style>

# College of Arms of Bexar
<p class="latin">Colegio de Armas de Béxar</p>

<p class="latin">Registrum Armorum San Antonio de Béxar</p>

<hr class="rule">

This is the Roll of Arms of Bexar County, Texas, kept by the College of Arms of Bexar. The Roll is rendered from a single data file: one record per entry — name, category, blazon, crest, motto, notes — with one image per entry. Use the filter above the Roll to view it by kind: government, military, institutions, or people. Entries are added by adding a record, never by editing this page.

<p class="stub">The Roll is newly opened. The missions, the lineages, and the rest of the county's armory are to follow.</p>

<div class="filters" role="group" aria-label="Filter the Roll">
  <button type="button" data-filter="all" class="active">All ({{ site.data.arms | size }})</button>
  <button type="button" data-filter="government">Government ({{ site.data.arms | where: "category", "government" | size }})</button>
  <button type="button" data-filter="military">Military ({{ site.data.arms | where: "category", "military" | size }})</button>
  <button type="button" data-filter="institutions">Institutions ({{ site.data.arms | where: "category", "institutions" | size }})</button>
  <button type="button" data-filter="people">People ({{ site.data.arms | where: "category", "people" | size }})</button>
</div>

{% for arm in site.data.arms %}
<div class="entry" data-category="{{ arm.category }}">
  <h2>{{ arm.name }}</h2>
  {% if arm.image %}<img src="{{ arm.image | relative_url }}" alt="{{ arm.image_alt | default: 'Arms of ' | append: arm.name }}">{% endif %}
  {% if arm.image_credit %}<p class="credit">{{ arm.image_credit }}</p>{% endif %}
  {% if arm.blazon %}<p class="blazon"><span class="label">Blazon</span> — {{ arm.blazon }}</p>{% endif %}
  {% if arm.crest %}<p><span class="label">Crest</span> — {{ arm.crest }}</p>{% endif %}
  {% if arm.motto %}<p><span class="label">Motto</span> — {{ arm.motto }}</p>{% endif %}
  <p>{{ arm.notes }}</p>
  <hr class="rule">
</div>
{% endfor %}

<script>
  (function () {
    var buttons = document.querySelectorAll('.filters button');
    var entries = document.querySelectorAll('.entry');
    buttons.forEach(function (btn) {
      btn.addEventListener('click', function () {
        buttons.forEach(function (b) { b.classList.remove('active'); });
        btn.classList.add('active');
        var f = btn.getAttribute('data-filter');
        entries.forEach(function (e) {
          e.style.display = (f === 'all' || e.getAttribute('data-category') === f) ? '' : 'none';
        });
      });
    });
  })();
</script>
