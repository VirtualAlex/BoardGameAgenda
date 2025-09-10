---
layout: home
---

<!-- Hero Article - Latest Post -->
{% assign latest_post = site.posts.first %}
<article class="hero-article">
    {% if latest_post.hero_image %}
        <img src="{{ latest_post.hero_image }}" alt="{{ latest_post.title }}" class="hero-image">
    {% endif %}
    <div class="hero-content">
        <h1 class="hero-title">{{ latest_post.title }}</h1>
        <div class="hero-meta">
            By {{ latest_post.author | default: "Board Game Agenda" }} • {{ latest_post.date | date: "%B %d, %Y" }} • 
            {% if latest_post.categories.first %}{{ latest_post.categories.first | capitalize }}{% endif %}
        </div>
        <p class="hero-excerpt">
            {% if latest_post.description %}
                {{ latest_post.description }}
            {% else %}
                {{ latest_post.excerpt | strip_html | truncate: 200 }}
            {% endif %}
        </p>
        <a href="{{ latest_post.url | relative_url }}" class="read-more">Read Full Article</a>
    </div>
</article>

<!-- All Other Posts Grid -->
<section class="all-posts">
    <h2 class="section-title">All Posts</h2>
    <div class="posts-grid">
        {% assign remaining_posts = site.posts | offset: 1 %}
        {% for post in remaining_posts limit:12 %}
        <article class="post-card">
            {% if post.hero_image %}
                <img src="{{ post.hero_image }}" alt="{{ post.title }}" class="post-image">
            {% endif %}
            <div class="post-content">
                <h3 class="post-title">
                    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                </h3>
                <div class="post-meta">
                    {{ post.date | date: "%B %d, %Y" }} • 
                    {% if post.categories.first %}{{ post.categories.first | capitalize }}{% endif %}
                </div>
                <p class="post-excerpt">
                    {% if post.description %}
                        {{ post.description | truncate: 100 }}
                    {% else %}
                        {{ post.excerpt | strip_html | truncate: 100 }}
                    {% endif %}
                </p>
            </div>
        </article>
        {% endfor %}
    </div>
</section>