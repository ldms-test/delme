DELME
=====

Delete me.

${\textbf{\color{green}GREEN}}$

${\color{red}RED}$

Pretext: <span style="color:red">RED</span>


TESTS
=====

Include ...

{% assign total = 0 %}
{% assign passed = 0 %}

{% assign filtered_files = site.static_files | where_exp: "file", "file.path contains '/test'" %}
{% for file in filtered_files %}
{% if file.name contains 'status.md' %}
{% include_relative {{ file.path }} %}
{% assign total = total | plus: 1 %}
{% endif %}
{% endfor %}

Total: {{ total }}
