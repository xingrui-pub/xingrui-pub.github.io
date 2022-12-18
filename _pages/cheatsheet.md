---
layout: cheatsheet
permalink: /cheatsheets/
title: Cheatsheets
nav: true
nav_order: 5
---

<div class="cheatsheet">
<div class="accordion" id="cheatsheet-list">
{% for cheat in site.cheats %}
<div class="card">
    <div class="card-header" id="heading-{{cheat.title | strip | remove:" "}}">
        <h2 class="mb-0">
            <button class="btn btn-link btn-block text-left" type="button" data-toggle="collapse" data-target="#collapse-{{cheat.title | strip | remove:" "}}" aria-expanded="true" aria-controls="collapse-{{cheat.title | strip | remove:" "}}">
            {{ cheat.title }}
            </button>
        </h2>
    </div>

    <div id="collapse-{{cheat.title | strip | remove:" "}}" class="collapse" aria-labelledby="heading-{{cheat.title | strip | remove:" "}}" data-parent="#cheatsheet-list">
        <div class="card-body">
        {{ cheat.content }}
        </div>
    </div>
</div>
{% endfor %}
</div>
</div>
