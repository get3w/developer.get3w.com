---
layout: default
title: "按标签调取所有文章"
current: "tags-article"
navigation: true
disqus: true
---

按照文章分类调取所有的文章

{% highlight text %}
{% raw %}
{% capture site_tags %}
  {% for tag in site.tags %}
    {{ tag | first }}
    {% unless forloop.last %},{% endunless %}
  {% endfor %}
{% endcapture %}
<!-- site_tags: {{ site_tags }} -->
{% assign tag_words = site_tags | split:',' | sort %}
<!-- tag_words: {{ tag_words }} -->

<ul class="tag-box">
  {% for item in (0..site.tags.size) %}
  {% unless forloop.last %}
  {% capture this_word %}
  {{ tag_words[item] | strip_newlines }}
  {% endcapture %}
  <li>
    <a href="#{{ this_word | cgi_escape }}" rel="nofollow">{{ this_word }}
      <sup>{{ site.tags[this_word].size }}</sup></a>
  </li>
  {% endunless %}{% endfor %}
</ul>

{% for item in (0..site.tags.size) %}
  {% unless forloop.last %}
    {% capture this_word %}
    {{ tag_words[item] | strip_newlines }}
    {% endcapture %}
    <h4 id="{{ this_word | cgi_escape }}">{{ this_word }}</h4>
    {% for post in site.tags[this_word] %}
      {% if post.title != null %}
        <ul>
          <li>{{ post.date | date: "%Y-%m-%d" }}
          &raquo; <a href="{{ post.url }}">{{ post.title }}</a>
          </li>
        </ul>
      {% endif %}
    {% endfor %}
  {% endunless %}
{% endfor %}
{% endraw %}
{% endhighlight %}