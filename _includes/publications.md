<section aria-labelledby="publications">
  <h2 id="publications" class="section-heading">Publications</h2>
  {% if site.data.publications.main.size > 0 %}
  {% for item in site.data.publications.main %}
  {% assign image_path = item.image | default: '' | strip %}
  {% assign conference = item.conference | default: '' %}
  {% assign conference_short = item.conference_short | default: '' %}
  {% assign title_link = item.page | default: '' | strip %}
  {% if title_link == '' %}{% assign title_link = item.pdf | default: '' | strip %}{% endif %}
  {% if title_link != '' %}
  {% assign title_link_prefix = title_link | slice: 0, 2 %}
  {% unless title_link contains ':' or title_link_prefix == '//' %}{% assign title_link = title_link | relative_url %}{% endunless %}
  {% endif %}
  {% assign inline_badge = false %}
  {% if image_path == '' and conference_short != '' %}{% assign inline_badge = true %}{% endif %}
  <article class="publication entry">
    {% if image_path != '' %}
    {% assign image_prefix = image_path | slice: 0, 2 %}
    {% unless image_path contains '://' or image_prefix == '//' %}{% assign image_path = image_path | relative_url %}{% endunless %}
    <div class="publication-media">
      <img class="publication-image" src="{{ image_path | escape }}" alt="{{ item.image_alt | default: '' | escape }}" loading="lazy" decoding="async">
      {% if conference_short != '' %}<span class="publication-badge">{{ conference_short | escape }}</span>{% endif %}
    </div>
    {% endif %}
    <div class="publication-body">
      <h3 class="entry-title">{% if title_link != '' %}<a href="{{ title_link | escape }}">{{ item.title | escape }}</a>{% else %}{{ item.title | escape }}{% endif %}</h3>
      {% if item.authors and item.authors != '' %}<div class="publication-authors">{{ item.authors | markdownify }}</div>{% endif %}
      {% if conference != '' or inline_badge %}
      <p class="publication-venue">{% if inline_badge %}<span class="publication-badge">{{ conference_short | escape }}</span>{% if conference != '' %} {% endif %}{% endif %}{{ conference | escape }}</p>
      {% endif %}
      {% if item.notes and item.notes != '' %}<div class="entry-detail">{{ item.notes | markdownify }}</div>{% endif %}
      {% capture publication_links %}
        {% assign link_types = 'pdf|PDF,code|Code,page|Project,bibtex|BibTeX' | split: ',' %}
        {% for link_type in link_types %}
        {% assign link_parts = link_type | split: '|' %}
        {% assign link_key = link_parts[0] %}
        {% assign link_path = item[link_key] | default: '' | strip %}
        {% if link_path != '' %}
        {% assign link_prefix = link_path | slice: 0, 2 %}
        {% unless link_path contains ':' or link_prefix == '//' %}{% assign link_path = link_path | relative_url %}{% endunless %}
        <a class="publication-link" href="{{ link_path | escape }}" aria-label="{{ link_parts[1] | escape }}: {{ item.title | escape }}">{{ link_parts[1] }}</a>
        {% endif %}
        {% endfor %}
      {% endcapture %}
      {% assign publication_links = publication_links | strip %}
      {% if publication_links != '' %}
      <div class="publication-links">
        {{ publication_links }}
      </div>
      {% endif %}
      {% if item.others and item.others != '' %}<div class="entry-detail">{{ item.others | markdownify }}</div>{% endif %}
    </div>
  </article>
  {% endfor %}
  {% else %}
  <p class="empty-state">No entries yet.</p>
  {% endif %}
</section>
