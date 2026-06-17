---
layout: page
title: Systems
menu: main
weight: 2
hide_title: true
permalink: /systems/
---

{% assign systems = site.systems | sort: "title" %}
{% assign core_items_alpha = systems | where: "state", "core" | where_exp: "item", "item.order == nil" | sort: "title" %}
{% assign core_items_ordered = systems | where: "state", "core" | where_exp: "item", "item.order != nil" | sort: "order" %}
{% assign core_items = core_items_ordered | concat: core_items_alpha %}
{% assign major_items_alpha = systems | where: "state", "major" | where_exp: "item", "item.order == nil" | sort: "title" %}
{% assign major_items_ordered = systems | where: "state", "major" | where_exp: "item", "item.order != nil" | sort: "order" %}
{% assign major_items = major_items_ordered | concat: major_items_alpha %}
{% assign experimental_items_alpha = systems | where: "state", "experimental" | where_exp: "item", "item.order == nil" | sort: "title" %}
{% assign experimental_items_ordered = systems | where: "state", "experimental" | where_exp: "item", "item.order != nil" | sort: "order" %}
{% assign experimental_items = experimental_items_ordered | concat: experimental_items_alpha %}
{% assign deprecated_items_alpha = systems | where: "state", "deprecated" | where_exp: "item", "item.order == nil" | sort: "title" %}
{% assign deprecated_items_ordered = systems | where: "state", "deprecated" | where_exp: "item", "item.order != nil" | sort: "order" %}
{% assign deprecated_items = deprecated_items_ordered | concat: deprecated_items_alpha %}
{% assign ordered_systems = core_items | concat: major_items | concat: experimental_items | concat: deprecated_items %}

{% include callout.html
   tone="green"
   link="<https://github.com/potassco/>"
    icon='<i class="fa-brands fa-github"></i>'
   text='Our systems are <b>open source</b>, feel free to contribute and report issues.
The source code of our projects is available on <a href="https://github.com/potassco/">GitHub</a>.' %}

<!-- {% include callout.html
   tone="blue"
   icon='<i class="fa-solid fa-trophy"></i>'
   link="/trophies/"
   text='Our systems won shiny awards in different competitions.
Check out our <a href="/trophies/">trophy page</a>.' %} -->

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
 <div id="search_results" class="posts"></div>
</div>

<div id="systems_sections">

<div class="posts">
{% for item in ordered_systems %}
 {% include system_list_item.html item=item %}
{% endfor %}
</div>
</div>

<script type="text/javascript" charset="utf-8">
 var posts = [
  {% for item in ordered_systems %}
   {% assign summary = item.summary | default: item.excerpt | default: item.content %}
   {% assign system_state = item.state | default: item.section | default: item.system_type | downcase %}
   {% assign state_label = system_state | capitalize %}
   {% if system_state == 'core' or system_state == 'core' %}
    {% assign system_state = 'core' %}
    {% assign state_label = 'Core' %}
   {% elsif system_state == 'stable' or system_state == 'major' %}
    {% assign system_state = 'major' %}
    {% assign state_label = 'Major' %}
   {% elsif system_state == 'experimental' or system_state == 'labs' %}
    {% assign system_state = 'experimental' %}
    {% assign state_label = 'Experimental' %}
   {% elsif system_state == 'cemetery' or system_state == 'deprecated' %}
    {% assign system_state = 'deprecated' %}
    {% assign state_label = 'Deprecated' %}
   {% endif %}
   {
    title: {{ item.title | strip_html | jsonify }},
    summary: {{ summary | strip_html | normalize_whitespace | jsonify }},
    content: {{ item.content | strip_html | normalize_whitespace | jsonify }},
    url: {{ item.url | strip_html | jsonify }},
    order: {{ forloop.index0 }},
    stateLabel: {{ state_label | jsonify }},
    stateClass: {{ system_state | jsonify }}
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
    var badge = post.stateLabel ? ' <span class="system-badge system-badge--' + post.stateClass + '">' + post.stateLabel + '</span>' : '';
    return '<div><a href="' + post.url + '">' + post.title + '</a>' + badge + '<p>' + post.summary + '</p></div>';
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

   var results = jsonSearch.getResults(query, posts).sort(function(a, b) {
    return a.order - b.order;
   });
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
<script type="text/javascript" src="{{ "/assets/js/jquery.min.js" | prepend: full_base_url }}" charset="utf-8"></script>
<script type="text/javascript" src="{{ "/assets/js/json_search.0.9.0.js" | prepend: full_base_url }}" charset="utf-8"></script>
