---
layout: default
---

{% include navigation.html %}

<main class="library__patterns">
    
    {% include intro-blocks.html %}

	{% for block in site.blocks %}
			
		<section id="{{ block.title | slugify }}" class="library__pattern">
				
			<header>
				<h2>{{ block.title }}</h2>
				<p>{{ block.description }}</p>
			</header>
            
            <hr>
				
			<div class="library__block">
				{% if site.markdown-blocks %}
					{{ block.content | markdownify }}
				{% else %}
					{{ block.content }}
				{% endif %}
			</div>

			{% if block.show_code %}
				<div id="example-{{ block.title | slugify }}" class="library__source">
					<pre><code>{% if site.markdown-blocks %}{{ block.content | markdownify | xml_escape }}{% else %}{{ block.content | xml_escape }}{% endif %}
					</code></pre>
				</div>
			{% endif %}

		</section><!-- .lib__pattern -->	

	{% endfor %}
</main>
