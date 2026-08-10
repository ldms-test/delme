TESTS
=====

{% assign total = 0 %}
{% assign passed = 0 %}

{% assign filtered_files = site.static_files | where_exp: "file", "file.path contains '/test'" %}
{% for file in filtered_files %}
{% if file.name contains 'status.md' %}
{% include_relative {{ file.path }} %}
{% assign total = total | plus: 1 %}
{% endif %}
{% endfor %}

Total: {{ passed }}/{{ total }}


DATA
====

{% assign total = 0 %}
{% assign passed = 0 %}

{% for ent in site.data %}
* {{ ent[0] }}: {{ ent[1].status }}
{% endfor %}
