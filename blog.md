---
layout: default
---

# Posts
<div class="posts">
  {% for post in site.posts %}
    <article class="post">
      <hr>
      <div class="date">
        Written on {{ post.date | date: "%B %e, %Y" }}
      </div>
      <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>
      <div class="entry">
        {{ post.excerpt }}...<a href="{{ site.baseurl }}{{ post.url }}">Read More</a>
      </div>
      <br>
    </article>
  {% endfor %}
</div>
