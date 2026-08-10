{% if page.mathjax %}
<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
<script>
  window.MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']],
      displayMath: [['$$', '$$'], ['\\[', '\\]']],
      processEscapes: true
    }
  };
</script>
{% endif %}


DELME
=====

Delete me.

${\textbf{\color{green}GREEN}}$

${\color{red}RED}$

Pretext: <span style="color:red">RED</span>


TESTS
=====

Include ...

{% assign filtered_files = site.static_files | where_exp: "file", "file.path contains '/test'" %}
{% for file in filtered_files %}
{% if file.name contains 'status.md' %}
{% include_relative {{ file.path }} %}
{% endif %}
{% endfor %}


Statically include 
{% include_relative test0/status.md %}
