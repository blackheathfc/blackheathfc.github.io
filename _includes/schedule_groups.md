<style>
@media print {
  @page {
    size: portrait;
  }

  html, body {
    width: 1048px;
  }

  section {
    border: none;
  }

  .groups {
    column-count: 2;
    column-gap: 6em;
  }

  .group {
    font-size: 14pt;
    page-break-inside: avoid;
  }

  header, footer, h1 {
    display: none;
  }
}
</style>

<article>
<h1 id="{{ page.title | slugify }}">{{ page.title }} match schedule</h1>

<section class="groups">
{% for group in page.groups %}
<section class="group">
<hr>
<h2 id="{{ group[0] | slugify }}">{{ page.title }} {{ group[0] }}</h2>
<hr>

{% assign pitches = group[1] %}
{% for pitch in pitches %}
<h3 id="{{ pitch[0] | slugify }}">{{ pitch[0] }}</h3>

<table>
  <tbody>
{% assign matches = pitch[1] %}
{% for match in matches %}
    <tr>
      <td>{{ match.time | date: "%H:%M" }}</td>
      <td>{{ match.home }}</td>
      <td>v</td>
      <td>{{ match.away }}</td>
    </tr>
{% endfor %}
  </tbody>
</table>

{% endfor %}
</section>
{% endfor %}

</section>
</article>
