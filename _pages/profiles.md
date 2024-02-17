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
<div id="{{member.profile.name}}" class="row" style="padding-top: 60px; margin-top: -60px;">
    <div class="col-sm-8">
        <img style="float: right; width: 30%; padding-left: 20px;" src="{{ member.profile.image | prepend: '/assets/img/' | prepend: site.baseurl | prepend: site.url }}" alt="photo of {{member.profile.name}}">
        <h4>{{member.profile.name}}{% if member.profile.degrees %}, {{member.profile.degrees}} {% endif %}</h4> 
        {{member.profile.position}} <br>
        <i class="fa fa-envelope"></i> <em>{{member.profile.email}}</em> <br>
        {% if member.url %}
          <i class="fa fa-globe"></i> <a href= "{{member.url}}" target="_blank">{{member.url}}</a> <br>
        {% endif %}
        {% if member.profile.github %}
          <i class="fab fa-github"></i> <a href= "https://github.com/{{member.profile.github}}" target="_blank"> {{member.profile.github}} </a> <br>
        {% endif %}
        {% if member.profile.scholar %}
          <i class="ai ai-google-scholar"></i> <a href= "http://scholar.google.com/citations?user={{member.profile.scholar}}" target="_blank"> Scholar Citations </a> <br>
        {% endif %}
        {% if member.profile.orcid %}
          <i class="ai ai-orcid"></i> <a href="http://{{member.profile.orcid}}" target="_blank"> {{member.profile.orcid}}</a> <br>
        {% endif %}
        <p class="text-justify"><a href="{{member.url}}>{{member.teaser | markdownify}</a></p>
    </div>
</div>
<hr>
</p>
    {% endfor %}
{% endfor %}
