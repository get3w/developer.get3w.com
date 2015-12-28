---
layout: default
title: "代码高亮"
current: "highlight"
navigation: true
disqus: true
---

get3w 已经支持[超过 100 种语言](http://pygments.org/languages/)代码高亮显示，在此感谢 [Pygments](http://pygments.org/)。要使用 Pygments ，你必须安装 Python 并且在配置文件中设置 `highlighter` 为 `pygments`。

另外，你也可以使用 Rouge 实现代码高亮。虽然它不像 Pygments 支持那么多语言，但也可以胜任大多数场景。而且，由于 Rouge 基于 Ruby ，你无须在系统中配置 Python 环境。

使用代码高亮的例子如下：

{% highlight text %}
{% raw %}
{% highlight ruby %}
def foo
  puts 'foo'
end
{% endhighlight %}
{% endraw %}
{% endhighlight %}

`highlight` 的参数 (本例中的 `ruby`) 是识别所用语言。为了确定最适合你所用语言的高亮方式，你可以在 [Pygments’ Lexers page](http://pygments.org/docs/lexers/) 和 [Rouge wiki](https://github.com/jayferd/rouge/wiki/List-of-supported-languages-and-lexers) 寻找对应语言的 “short name”。

#### 行号

`highlight` 的第二个可选参数是 `linenos` 。使用了 `linenos` 会强制在代码上加入行号。例如：

{% highlight text %}
{% raw %}
{% highlight ruby linenos %}
def foo
  puts 'foo'
end
{% endhighlight %}
{% endraw %}
{% endhighlight %}

#### 代码高亮的样式

要使用代码高亮，你还需要包含一个样式表。例如 [syntax.css](http://github.com/mojombo/tpw/tree/master/css/syntax.css) 。它包含了和 GitHub 一样的样式，并且免费。如果你使用了 `linenos` ，可能还需要在 `syntax.css` 加入 `.lineno` 样式。
