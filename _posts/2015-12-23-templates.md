---
layout: default
title: "模板"
current: "templates"
navigation: true
disqus: true
---

get3w 使用 [Liquid](http://wiki.shopify.com/Liquid) 模板语言，支持所有标准的 Liquid [标签](http://wiki.shopify.com/Logic)和[过滤器](http://wiki.shopify.com/Filters)。get3w 甚至增加了几个过滤器和标签，方便使用。

## 过滤器

<div class="ct-table-wrapper ct-border --all">
<table class="ct-striped">
  <thead>
    <tr>
      <th styles="width: 40%;">描述</th>
      <th class='ct-center'><span class="filter">过滤器</span> 和 <span class="output">输出</span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p class='name'><strong>日期转化为 XML 模式</strong></p>
        <p>将日期转化为 XML 模式 (ISO 8601) 的格式。</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ site.time | date_to_xmlschema }}{% endraw %}</code>
        </p>
        <p>
          <code class='output'>2008-11-17T13:07:54-08:00</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>日期转化为 RFC-822 格式</strong></p>
        <p>将日期转化为 RFC-822 格式，用于 RSS 订阅。</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ site.time | date_to_rfc822 }}{% endraw %}</code>
        </p>
        <p>
          <code class='output'>Mon, 17 Nov 2008 13:07:54 -0800</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>日期转化为短格式</strong></p>
        <p>将日期转化为短格式。</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ site.time | date_to_string }}{% endraw %}</code>
        </p>
        <p>
          <code class='output'>17 Nov 2008</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>日期转化为长格式</strong></p>
        <p>将日期转化为长格式。</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ site.time | date_to_long_string }}{% endraw %}</code>
        </p>
        <p>
          <code class='output'>17 November 2008</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>检索</strong></p>
        <p>选取键值对应的所有对象，返回一个数组。</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ site.members | where:"graduation_year","2014" }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>分组</strong></p>
        <p>根据所给属性将对象分组，返回一个数组。</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ site.members | group_by:"graduation_year" }}{% endraw %}</code>
        </p>
        <p>
          <code class='output'>[{"name"=>"2013", "items"=>[...]},<br />{"name"=>"2014", "items"=>[...]}]</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>XML 转码</strong></p>
        <p>对一些字符串转码，已方便显示在 XML 。</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ page.content | xml_escape }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>CGI 转码</strong></p>
        <p>
          CGI 转码，用于 URL 中，将所有的特殊字符转化为 %XX 的形式。
        </p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ “foo,bar;baz?” | cgi_escape }}{% endraw %}</code>
        </p>
        <p>
          <code class='output'>foo%2Cbar%3Bbaz%3F</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>URI 转码</strong></p>
        <p>
          URI 转码。
        </p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ “'foo, bar \\baz?'” | uri_escape }}{% endraw %}</code>
        </p>
        <p>
          <code class='output'>foo,%20bar%20%5Cbaz?</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>统计字数</strong></p>
        <p>统计文章中的字数。</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ page.content | number_of_words }}{% endraw %}</code>
        </p>
        <p>
          <code class='output'>1337</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>数组转换为句子</strong></p>
        <p>将数组转换为句子，列举标签时尤其有用。</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ page.tags | array_to_sentence_string }}{% endraw %}</code>
        </p>
        <p>
          <code class='output'>foo, bar, and baz</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>Markdown 支持</strong></p>
        <p>将 Markdown 格式的字符串转换为 HTML 。</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ page.excerpt | markdownify }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>Sass / SCSS 转换</strong></p>
        <p>将 Sass / SCSS 格式的字符串转换为 CSS</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ some_scss | scssify }}{% endraw %}</code>
        </p>
        <p>
         <code class='filter'>{% raw %}{{ some_sass | sassify }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>slugify</strong></p>
        <p>将字符串转换为小写字母 URL “slug”。详见下面的参数。</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ "The _config.yml file" | slugify }}{% endraw %}</code>
        </p>
        <p>
          <code class='output'>the-config-yml-file</code>
        </p>
        <p>
         <code class='filter'>{% raw %}{{ "The _config.yml file" | slugify: 'pretty' }}{% endraw %}</code>
        </p>
        <p>
          <code class='output'>the-_config.yml-file</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>JSON 转换</strong></p>
        <p>将 Hash / 数组 格式的字符串转换为 JSON</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ site.data.projects | jsonify }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>排序</strong></p>
        <p>对数组排序，可选参数为：1.排序属性；2.顺序（正序或倒序）</p>
      </td>
      <td class='ct-center'>
        <p>
         <code class='filter'>{% raw %}{{ page.tags | sort }}{% endraw %}</code>
        </p>
        <p>
         <code class='filter'>{% raw %}{{ site.posts | sort: 'author' }}{% endraw %}</code>
        </p>
        <p>
         <code class='filter'>{% raw %}{{ site.pages | sort: 'title', 'last' }}{% endraw %}</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

### `slugify` 的可选参数

`slugify`接受一个参数，用来设定具体的过滤字符。默认值为`default`。可选参数如下（含过滤字符）：

- `none`：不过滤字符
- `raw`：空格
- `default`：空格和非字母数字字符
- `pretty`：空格和非字母数字字符，`._~!$&'()+,;=@`除外


## 标签

### 引用

如果你需要在多个地方引用一小代码片段，可以使用 `include` 标签。

{% highlight ruby %}
{% raw %}{% include footer.html %}{% endraw %}
{% endhighlight %}

get3w 要求所有被引用的文件放在根目录的 `_includes` 文件夹，上述代码将把 `<source>/_includes/footer.html` 的内容包含进来。

<div class="ct-alert ct-mb-lg ct-left --info">
  <div class="inner">
    <i class="fa fa-info-circle ct-color-yellow-a200"></i>
    <div class="content">
      <span class="ct-h6">提示™：使用变量作为文件名</span><br>
      文件名可以是文字（如上面的例子），也可以是 liquid 标记的使用变量，如<code>{% raw %}{% include {{my_variable}} %}{% endraw %}</code>。
    </div>
  </div>
</div>

你还可以对 include 传递参数。省略引用标记来传递变量： Liquid 弯括号不能在此处使用：

{% highlight ruby %}
{% raw %}{% include footer.html param="value" variable-param=page.variable %}{% endraw %}
{% endhighlight %}

这些变量可以通过 Liquid 调用：

{% highlight ruby %}
{% raw %}{{ include.param }}{% endraw %}
{% endhighlight %}

#### 相对于其他文件的 Permalink 引入

你也可以选择相对当前文件，引入其他文件的片段：
{% highlight ruby %}
{% raw %}{% include_relative somedir/footer.html %}{% endraw %}
{% endhighlight %}

引入的内容未必总在 `_includes` 文件夹。当该标签被使用时，引入的内容应位于对应的相对路径下。例如，`_posts/2014-09-03-my-file.markdown`文件试用了`include_relative`标签，引入的文件需要位于 `_posts` 文件夹或其子文件夹。在其他路径下将无法引入。

 `include` 标签的其他特征也同样适用于 `include_relative` 标签，如使用变量。

### 博文链接(Post URL)

如果你想使用你某篇文章的链接，标签 `post_url` 可以满足你的需求。

{% highlight text %}
{% raw %}
{% post_url 2010-07-21-name-of-post %}
{% endraw %}
{% endhighlight %}

如果你使用了子文件夹来组织你的博文，你需要在路径中加入子文件夹：

{% highlight text %}
{% raw %}
{% post_url /subdir/2010-07-21-name-of-post %}
{% endraw %}
{% endhighlight %}

当使用`post_url`标签时，不需要写文件后缀名。

还可以用 Markdown 这样为你的文章生成超链接：

{% highlight text %}
{% raw %}
[Name of Link]({% post_url 2010-07-21-name-of-post %})
{% endraw %}
{% endhighlight %}

### Gist

使用 `gist` 标签可以轻松的把 GitHub Gist 签入到网站中，对于公有和私有的 gist 均有效：

{% highlight text %}
{% raw %}
{% gist parkr/931c1c8d465a04042403 %}
{% endraw %}
{% endhighlight %}

你也可以为 gist 设置文件名：

{% highlight text %}
{% raw %}
{% gist parkr/931c1c8d465a04042403 get3w-private-gist.markdown %}
{% endraw %}
{% endhighlight %}
