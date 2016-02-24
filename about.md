---
layout: page
title: About
---

## Things I have done

<ul class="projects">
{% for project in site.data.projects %}
    <li class="project">
        <img src="/img/{{ project.image }}" alt="{{ project.title }}" width="300">
        <h2><a href="{{ project.url }}" target="_blank">{{ project.title }}</a></h2>
        <p>{{ project.description }}</p>
    </li>
{% endfor %}
</ul>

## Things I like

{% highlight json %}
[{% assign skills = (site.data.skills | sort: "title") %}
{% for skill in skills %}    {
        "title": "{{ skill.title }}"{% if skill.url != null %}, "moreInfo": "{{ skill.url }}"{% endif %}
    }{% if forloop.length != forloop.index %},{% endif %}
{% endfor %}]
{% endhighlight %}