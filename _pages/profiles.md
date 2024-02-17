---
layout: page
permalink: /people
title: people
description: members by group in alphabetical order.
nav: true
nav_rank: 1
---

{% assign groups = site.members | sort: "group_rank" | map: "group" | uniq %}
{% for group in groups %}

## {{ group }}

    {% assign members = site.members | sort: "lastname" | where: "group", group %}
    {% for member in members %}

<p>
<div id = "{{member.profile.name}}" class="row" style="padding-top: 60px; margin-top: -60px;">
    <img style="float: right; width: 42%; padding-left: 20px;" src="{{ member.profile.image | prepend: '/assets/img/' | prepend: site.baseurl | prepend: site.url }}" alt="photo of {{member.profile.name}}">
    <div>
        <h4>{{member.profile.name}}{% if member.profile.degrees %}, {{member.profile.degrees}} {% endif %}</h4> 
        {{member.profile.position}} <br>
        <i class="fa fa-envelope"></i> <em>{{member.profile.email}}</em> <br>
        {% if person.website %}
          <i class="fa fa-globe"></i> <a href= "{{member.url}}" target="_blank">{{member.url}}</a> <br>
        {% endif %}
        {% if member.profile.github %}
          <i class="fab fa-github"></i> <a href= "https://github.com/{{person.github}}" target="_blank"> {{person.github}} </a> <br>
        {% endif %}
        {% if member.profile.scholar %}
          <i class="ai ai-google-scholar"></i> <a href= "http://scholar.google.com/citations?user={{person.scholar}}" target="_blank"> Scholar Citations </a> <br>
        {% endif %}
        {% if person.orcid %}
          <i class="ai ai-orcid"></i> <a href="http://{{person.orcid}}" target="_blank"> {{person.orcid}}</a> <br>
        {% endif %}

    </div>
    <div class="col-sm-8">
        <p class="text-justify">{{member.teaser | markdownify}}</p>
    </div>
</div>
<hr>
</p>
    {% endfor %}
<hr>
{% endfor %}
