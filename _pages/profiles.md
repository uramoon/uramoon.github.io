---
layout: page
permalink: /people
title: people
description: members by group in chronological order.
nav: true
nav_rank: 1
---

{% assign groups = site.members | sort: "group_rank" | map: "group" | uniq %}
{% for group in groups %}

## {{ group }}

    {% assign members = site.members | sort: "order" | where: "group", group %}
    {% for member in members %}

<p>
<div id="{{member.profile.name}}" class="row" style="padding-top: 60px; margin-top: -60px;">
    <div class="col-sm-8">
       {% if member.inline == false %}<a href="{{member.url}}" style="text-decoration: none; color: inherit;">{% endif %} <img style="float: right; width: 42%; padding-left: 20px;" src="{{ member.profile.image | prepend: '/assets/img/' | prepend: site.baseurl | prepend: site.url }}" alt="photo of {{member.profile.name}}"> {% if member.inline == false %}</a>{% endif %}
        {% if member.inline == false %}<a href="{{member.url}}" style="text-decoration: none; color: inherit;">{% endif %}<h4>{{member.profile.name}}{% if member.inline == false %}</a>{% endif %}{% if member.profile.degrees %}, {{member.profile.degrees}} {% endif %}</h4> 
        {{member.profile.position}} <br>
        <i class="fa fa-envelope"></i> <em>{{member.profile.email}}</em> <br>
        {% if member.profile.website %}
          <i class="fa fa-globe"></i> <a href= "{{member.profile.website}}" target="_blank"> {{member.profile.website}} </a> <br>
        {% endif %}
        {% if member.profile.linkedin %}
          <i class="fab fa-linkedin"></i> <a href= "https://linkedin.com/in/{{member.profile.linkedin}}" target="_blank"> {{member.profile.linkedin}} </a> <br>
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
        <p class="text-justify">{% if member.inline == false %}<a href="{{member.url}}" style="text-decoration: none; color: inherit;">{% endif %}{{member.teaser | markdownify}}{% if member.inline == false %}</a>{% endif %}</p>
    </div>
</div>
</p>
    {% endfor %}
<hr>
{% endfor %}
