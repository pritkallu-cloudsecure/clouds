---
layout: default
---

{% include navigation.html %}

<main class="library__patterns">
    
	{% for type in site.typography %}
			
		<section id="{{ type.title | slugify }}" class="library__pattern">
				
			<header>
				<h2>{{ type.title }}</h2>
				<p>{{ type.description }}</p>
			</header>
            
            <hr>
				
			<div class="library__block">
				{% if site.markdown-typography %}
					{{ type.content | markdownify }}
				{% else %}
					{{ type.content }}
				{% endif %}
			</div>

			{% if type.show_code %}
				<div id="example-{{ type.title | slugify }}" class="library__source">
					<pre><code>{% if site.markdown-typography %}{{ type.content | markdownify | xml_escape }}{% else %}{{ type.content | xml_escape }}{% endif %}
					</code></pre>
				</div>
			{% endif %}

		</section><!-- .lib__pattern -->	

	{% endfor %}
</main>

<script src="assets/js/accordion.min.js"></script>
