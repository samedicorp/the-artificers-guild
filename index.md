---
title: The Artificers Guild
layout: page
---

## The Artificers Guild

The Artificers Guild is an organisation dedicated to the sharing of scripting knowledge in Dual Universe.

We don't have a political motive, and aim to stay neutral in all conflicts.

We also understand that our members may have other political affiliations and be members of other organisations. 

We realise that this means that it may not be possible for everyone to share all of their work.

This is fine. We simply ask all members:

1. **Share Knowledge**: If you know something about scripting that you can share, please do so. If you can't share whole scripts, maybe you can share techniques and tips?
2. **Be excellent to each other**: If a member of the guild needs help and you can give it, please do. See also (1).


<div class="container">

    <!-- This loops through the paginated posts -->
    {% for post in paginator.posts %}
    <news>

        <hr>
        <div class="row">
            <!-- title -->
            <div class="group1 col-sm-6 col-md-6">
                <span class="news-title"><a href="{{post.url}}">{{ post.title }}</a></span>
            </div>

            <!-- date -->
            <div class="group2 col-sm-6 col-md-6">
                <span class="news-date">{{ post.date | date: '%B %d, %Y' }}</span>
            </div>
        </div>

        <!-- image -->
        <img src="{{ post.image }}" class="img-responsive">

        <!-- content -->
        <div class="news-content">
            {{ post.excerpt }}
        </div>

        <!-- more -->
        <span class="news-more"><a href="{{ post.url }}">more...</a></span>
    </news>

{% endfor %}

</div>

<!-- Pagination links -->
{% if paginator.total_pages > 1 %}
<div class="container">
    <table width="100%">
        <tr>
            <td align="center">
<div class="pagination text-center">
    {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">&laquo;</a>
    {% else %}
    <span>&laquo;</span>
    {% endif %}

    {% assign offset = 3 %}
    {% assign pagemin = paginator.page | minus: offset %}
    {% assign pagemax = paginator.page | plus: offset %}

    {% if pagemin > 1 %}
    <div class="pagination-item">
    <a href="/">1</a>
    </div>
    ...
    {% endif %}

    {% for page in (1..paginator.total_pages) %}
    {% if page >= pagemin and page <= pagemax %}
    {% if page == paginator.page %}
    <div class="pagination-selected-item">
    {{ page }}
    {% elsif page == 1 %}
    <div class="pagination-item">
    <a href="/">1</a>
    {% else %}
    <div class="pagination-item">
    <a href="{{ site.paginate_path | prepend: site.baseurl | replace: '//', '/' | replace: ':num', page }}">{{ page }}</a>
    {% endif %}
    </div>
    {% endif %}
    {% endfor %}

    {% if pagemax < paginator.total_pages %}
    ...
    <div class="pagination-item">
    <a href="{{ site.paginate_path | prepend: site.baseurl | replace: '//', '/' | replace: ':num', paginator.total_pages }}">{{ paginator.total_pages }}</a>
    </div>
    {% endif %}

    {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">&raquo;</a>
    {% else %}
    <span>&raquo;</span>
    {% endif %}
</div>
</td>
</tr>
</table>
</div>
{% endif %}
