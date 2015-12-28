---
layout: default
title: "调取指定栏目文章列表"
current: "single-article"
navigation: true
disqus: true
---

如果我们要调取特定的某一个栏目的内容，可以这样做：

{% highlight text %}
{% raw %}
{% for post in site.categories.[栏目名称] %}
      <a href="http://{{ post.title }}" title="{{ post.content | remove: '<p>' | remove: '</p>' |  remove: '<!--break-->' }}" target="_blank">
          {% if post.tags %}
              <i class="icon-tags">{{ post.tags }}</i>
          {% endif %}
          #如果内容中填写了标签，则显示
          {% if post.attr %}
              <i class="icon-hot">{{ post.attr }}</i>
          {% endif %}
          #判断是否设置热点，内容如果设置热点属性，即显示，否则不显示
          {{ post.name }}
          <span class="link-content">{{ post.content | remove: '<p>' | remove: '</p>' | split:'<!--break-->' | first }}</span>
      </a>
{% endfor %}
{% endraw %}
{% endhighlight %}
