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
{%   if ent[1].status == "passed" %}
{%     assign color = "gree" %}
{%   elsif ent[1].status == "queued" %}
{%     assign color = "purple" %}
{%   elsif ent[1].status == "failed" %}
{%     assign color = "red" %}
{%   else %}
{%     assign color = "black" %}
{%   endif %}
{%   assign total = total | plus: 1 %}
{%   assign passed = total | plus: ent[1].passed %}
* {{ ent[0] }}: {{tag}} <span style="color:{{ color }}">{{ ent[1].status }}</span>

{% endfor %}
Total: {{passed}} / {{total}}
