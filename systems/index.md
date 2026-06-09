---
layout: page
title: Systems
menu: main
weight: 2
hide_title: true
permalink: /systems/
---

{% assign systems = site.systems | sort: "title" %}
{% assign core_items_alpha = systems | where: "section", "core" | where_exp: "item", "item.order == nil" | sort: "title" %}
{% assign core_items_ordered = systems | where: "section", "core" | where_exp: "item", "item.order != nil" | sort: "order" %}
{% assign core_items = core_items_ordered | concat: core_items_alpha %}
{% assign stable_items_alpha = systems | where: "section", "stable" | where_exp: "item", "item.order == nil" | sort: "title" %}
{% assign stable_items_ordered = systems | where: "section", "stable" | where_exp: "item", "item.order != nil" | sort: "order" %}
{% assign stable_items = stable_items_ordered | concat: stable_items_alpha %}
{% assign experimental_items_alpha = systems | where: "section", "experimental" | where_exp: "item", "item.order == nil" | sort: "title" %}
{% assign experimental_items_ordered = systems | where: "section", "experimental" | where_exp: "item", "item.order != nil" | sort: "order" %}
{% assign experimental_items = experimental_items_ordered | concat: experimental_items_alpha %}
{% assign cemetery_items_alpha = systems | where: "section", "cemetery" | where_exp: "item", "item.order == nil" | sort: "title" %}
{% assign cemetery_items_ordered = systems | where: "section", "cemetery" | where_exp: "item", "item.order != nil" | sort: "order" %}
{% assign cemetery_items = cemetery_items_ordered | concat: cemetery_items_alpha %}


{% include callout.html
   tone="green"
   link="https://github.com/potassco/"
    icon='<i class="fa-solid fa-code"></i>'
   text='Our systems are <b>open source</b>, feel free to contribute and report issues.
The source code of our projects is available on <a href="https://github.com/potassco/">GitHub</a> and <a href="https://sourceforge.net/p/potassco/code">Legacy code</a>.' %}



{% include callout.html
   tone="blue"
   icon='<i class="fa-solid fa-trophy"></i>'
   link="/trophies/"
   text='Our systems won shiny awards in different competitions.
Check out our <a href="/trophies/">trophy page</a>.' %}

<div style="height: 20pt;"></div>

<div id="search_area">
	<div class="search_box">
		<span class="search_icon" aria-hidden="true"></span>
		<input id="search" type="search" placeholder="Search across all systems">
		<button class="search_clear" type="button" aria-label="Clear search" style="display: none;">&times;</button>
	</div>
</div>

<div id="search_results_area" style="display: none;">
	<h2 id="search_results_heading" style="display:none">Search results: <span id="result_count"></span></h2>
	<ul id="search_results" class="posts"></ul>
</div>

<div id="systems_sections">

<h2 id="core-systems">Core systems</h2>

<h3>Systems that form the foundation of our tools.</h3>

<ul class="posts">
{% for item in core_items %}
	{% include system_list_item.html item=item %}
{% endfor %}
</ul>

<h2 id="stable-systems">Stable systems</h2>

<h3>Stable up to date systems that are currently maintained and supported.</h3>

<ul class="posts">
{% for item in stable_items %}
	{% include system_list_item.html item=item %}
{% endfor %}
</ul>

<h2 id="experimental-systems">Experimental systems</h2>

<h3>These are either small utilities or projects in an early or unfinished development phase.</h3>

<ul class="posts">
{% for item in experimental_items %}
	{% include system_list_item.html item=item %}
{% endfor %}
</ul>

<h2 id="cemetery">Cemetery</h2>

<h3>Superseded programs that no longer belong to the Potassco suite.</h3>

<ul class="posts">
{% for item in cemetery_items %}
	{% include system_list_item.html item=item %}
{% endfor %}
</ul>
</div>

<script type="text/javascript" charset="utf-8">
	var posts = [
		{% for item in systems %}
			{% assign summary = item.summary | default: item.excerpt | default: item.content %}
			{
				title: {{ item.title | strip_html | jsonify }},
				summary: {{ summary | strip_html | normalize_whitespace | jsonify }},
				content: {{ item.content | strip_html | normalize_whitespace | jsonify }},
				url: {{ item.url | strip_html | jsonify }}
			}{% unless forloop.last %},{% endunless %}
		{% endfor %}
	];

	document.addEventListener('DOMContentLoaded', function() {
		var searchField = $('#search');
		var searchClear = $('#search_area .search_clear');
		var searchResultsArea = $('#search_results_area');
		var searchCount = $('#result_count');
		var searchResults = $('#search_results');
		var searchResultsHeading = $('#search_results_heading');
		var systemsSections = $('#systems_sections');
		var jsonSearch = new JSONSearch({
			fields: {
				title: 'infix',
				summary: 'word_prefix',
				content: 'word_prefix'
			},
			ranks: {
				title: 3,
				summary: 2,
				content: 1
			}
		});

		var renderResults = function(results) {
			searchCount.text('(' + results.length + ')');
			searchResults.html(results.map(function(post) {
				return '<li><a href="' + post.url + '">' + post.title + '</a><p>' + post.summary + '</p></li>';
			}).join(''));
		};

		var clear = function() {
			searchField.val('');
			search();
		};

		var search = function(event) {
			if (event && event.keyCode == 27) {
				clear();
				return;
			}

			var query = searchField.val();

			if (!query) {
				searchClear.hide();
				searchResultsHeading.hide();
				searchResultsArea.hide();
				systemsSections.show();
				return;
			}

			var results = jsonSearch.getResults(query, posts);
			searchClear.show();
			searchResultsHeading.show();
			searchResultsArea.show();
			systemsSections.hide();
			renderResults(results);
		};

		searchField.on('keyup', search);
		searchClear.on('click', clear);
	});
</script>
<script type="text/javascript" src="{{ "/js/jquery.min.js" | prepend: full_base_url }}" charset="utf-8"></script>
<script type="text/javascript" src="{{ "/js/json_search.0.9.0.js" | prepend: full_base_url }}" charset="utf-8"></script>

