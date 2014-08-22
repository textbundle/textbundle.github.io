---
layout: page
title: Changelog
navigationTitle: Changelog
position: 2
---

<div class="home">
  <ul class="posts">
    {% for post in site.posts %}
      <li>
        <h3>{{ post.title }}</h3>
        <span class="post-date">{{ post.date | date: "%b %-d, %Y" }}</span>
	   <div class="post-body">{{ post.content }}</div>
      </li>
    {% endfor %}
	<li>
		<p class="rss-subscribe">Subscribe <a href="{{ "/feed.xml" | prepend: site.baseurl }}">via RSS</a></p>
	</li>
  </ul>

  

</div>