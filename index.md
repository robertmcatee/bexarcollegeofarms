---
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500;1,600&display=swap" rel="stylesheet">
<style>
  body { font-family: "Cormorant Garamond", "Cormorant", Palatino, Georgia, serif; font-size: 20px; max-width: 44em; margin: 2em auto; padding: 0 1em; line-height: 1.5; color: #1a1a1a; background: #fdfcf8; }
  .masthead { text-align: center; }
  .masthead h1 { font-size: 2em; font-weight: 600; letter-spacing: .12em; text-transform: uppercase; margin: 0; line-height: 1.2; text-align: center; }
  .masthead .spanish { text-transform: uppercase; letter-spacing: .32em; font-size: .72em; color: #6b6252; margin-top: .7em; }
  .masthead .registrum { font-style: italic; font-size: 1.18em; color: #9e1b1b; margin-top: .45em; }
  .rule { border: 0; border-top: 2px solid #8a6d2f; margin: 1.4em 0; }
  h2 { text-align: center; letter-spacing: .04em; font-weight: 600; }
  .entry { margin: 2.5em 0; }
  .entry img { display: block; margin: 0 auto; max-height: 340px; max-width: 100%; }
  .blazon { margin-top: 1em; }
  .label { font-variant: small-caps; letter-spacing: .06em; color: #8a6d2f; font-weight: 600; }
  .credit { font-size: .85em; color: #666; text-align: center; }
  .filters { text-align: center; margin: 1.5em 0 .5em; }
  .filters button { font-family: inherit; font-variant: small-caps; letter-spacing: .06em; font-size: 1em; color: #8a6d2f; background: none; border: 1px solid #8a6d2f; border-radius: 2em; padding: .25em 1em; margin: 0 .25em .4em; cursor: pointer; }
  .filters button:hover { background: #f3ecd9; }
  .filters button.active { background: #8a6d2f; color: #fff; }
</style>

<div class="masthead">
  <h1>College of Arms of Bexar</h1>
  <div class="spanish">Colegio de Armas de Béxar</div>
  <div class="registrum">Registrum Armorum San Antonio de Béxar</div>
</div>

<hr class="rule">

<p>The Roll of Arms of Bexar County, Texas, records the arms borne by the governments, military commands, institutions, and persons of this county and its neighbouring country — each entered with its blazon and the authority for it. The College of Arms of Bexar keeps the Roll and admits no entry that is not documented; what is shown is the heraldic element alone, never a seal or a logo in its place.</p>

<div class="filters" role="group" aria-label="Filter the Roll">
  <button type="button" data-filter="all" class="active">All ({{ site.data.arms | size }})</button>
  <button type="button" data-filter="government">Government ({{ site.data.arms | where: "category", "government" | size }})</button>
  <button type="button" data-filter="military">Military ({{ site.data.arms | where: "category", "military" | size }})</button>
  <button type="button" data-filter="institutions">Institutions ({{ site.data.arms | where: "category", "institutions" | size }})</button>
  <button type="button" data-filter="ecclesiastical">Ecclesiastical ({{ site.data.arms | where: "category", "ecclesiastical" | size }})</button>
  <button type="button" data-filter="academic">Academic ({{ site.data.arms | where: "category", "academic" | size }})</button>
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
  {% if arm.website %}<p><span class="label">Website</span> — <a href="{{ arm.website }}">{{ arm.website | remove: "https://" | remove: "http://" }}</a></p>{% endif %}
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
