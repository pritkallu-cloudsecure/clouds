---
layout: default
---

{% include navigation.html %}

<main class="library__patterns">
    
    {% include intro-elements.html %}

	{% for element in site.elements %}
			
		<section id="{{ element.title | slugify }}" class="library__pattern">
				
			<header>
				<h2>{{ element.title }}</h2>
				<p>{{ element.description }}</p>
			</header>
            
            <hr>
				
			<div class="library__block">
				{% if site.markdown-elements %}
					{{ element.content | markdownify }}
				{% else %}
					{{ element.content }}
				{% endif %}
			</div>

			{% if element.show_code %}
				<div id="example-{{ element.title | slugify }}" class="library__source">
					<pre><code>{% if site.markdown-elements %}{{ element.content | markdownify | xml_escape }}{% else %}{{ element.content | xml_escape }}{% endif %}
					</code></pre>
				</div>
			{% endif %}

		</section><!-- .lib__pattern -->	

	{% endfor %}
</main>

<script src="assets/js/accordion.min.js"></script>
