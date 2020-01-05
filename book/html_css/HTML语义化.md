# HTML语义化

## Web语义化

Web语义化是指使用恰当语义的html标签、class类名等内容，让页面具有良好的结构与含义，从而让人和机器都能快速理解网页内容。

> 我们应该在发布内容的时候，就用机器可读的、被广泛认可的语义信息来描述内容，来降低机器处理 Web 内容的难度

web语义化包含了三部分：

* html标签语义化
* css命名语义化
* URL语义化

## Web语义化的优点

* 正确的标签做正确的事情。
* 页面内容结构化。
* 无CSS样子时也容易阅读，便于阅读维护和理解。
* 便于浏览器、搜索引擎解析。 利于爬虫标记、利于SEO。

## HTML语义化标签

HTML为网页文档内容提供上下文结构和含义。通常我们所说的HTML应该是完全脱离表现信息的，其中的标签应该都是语义化地定义了文档的结构。

代码栗子：

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <article>
            <header>
                <h1>
                    h1 - Web语义化
                </h1>
            </header>
            <nav>
                <ul>
                    <li>nav1 - HTML语义化</li>
                    <li>nav2 - CSS语义化</li>
                </ul>
            </nav>
            <section>
                setction1 - HTML语义化
            </section>
            <section>
                section2 - CSS语义化
            </section>
            <time datetime="2020-02-14" pubdate>time - 2020年02月14日</time>
            <footer>footer - by danni</footer>
        </article>
    </body>
</html>
    
```

html语义化标签包括 body, article, nav, aside, section, header, footer, hgroup, 还有 h1-h6 address等。

### 常用的HTML5语义化标签

#### header元素

`header`元素代表“网页”或者“section”的页眉，通常包含h1-h6 元素或者 hgroup, 作为整个页面或者一个内容块的标题。也可以包裹一节的目录部分，一个搜索框，一个nav，或者相关logo。

代码栗子：

```html
<header>
    <hgroup>
        <h1>网站标题<h1>
        <h2>网站副标题</h2>
    </hgroup>
<header>
```

**注意：**

* `header`元素可以是“网页”或者任意“section”的头部部分。
* 没有个数限制。
* 如果hgroup或者h1-h6自己就能工作得很好，那么就没必要用header。

#### hgroup元素

`hgroup`元素代表“网页”或“section”的标题，当元素有多个层级时，该元素可以将`h1`到`h6`元素放在其内。可用于文章的主标题和副标题组合。

代码栗子：

```html
<hgroup>
    <h1>这是一个主标题</h1>
    <h2>这是一个副标题</h2>
</hgroup>
```

**注意：**

* 如果只需要一个h1-h6标签就不用hgroup。
* 如果有连续多个h1-h6标签就用hgroup。
* 如果有连续多个标题和其他文章数据，h1-h6标签就用hgroup包住，和其他文章元数据一起放入header标签。

#### footer 元素

`footer`元素代表“网页”或任意“section”的页脚，通常含有该节的一些基本信息，譬如：作者，相关文档链接，版权资料。如果`footer`元素包含了整个节，那么它们就代表附录，索引，提拔，许可协议，标签，类别等一些其他类似信息。

代码栗子：

```html
<footer>
    @danni
</footer>
```

**注意：**

* 可以是“网页”或者任意“section”的底部部分。
* 没有个数限制，除了包裹的内容不一样，其他跟header类似。

#### nav 元素

`nav `元素代表页面的导航链接区域。用于定义页面的主要导航部分。

代码栗子：

```html
<nav>
    <ul>
        <li>HTML语义化</li>
        <li>CSS 语义化</li>
    </ul>
</nav>
```

规范上说nav只能用在页面主要导航部分上。页脚区域中的链接列表，虽然指向不同网站的不同区域，譬如服务条款，版权页等，这些footer元素就能够用了。

**注意：**

* 用于整个页面的主要导航部分，不适合就不要用nav元素了。

#### article 元素

`article`元素 代表一个在文档，页面或者网站中自成一体的内容，其目的是为了让开发者独立开发或重用。

除了它的内容，`article`会有一个标题(通常会在`header`里)和一个`footer`页脚。

代码栗子：

```html
<article>
    <h1>你好，我是这边文章的标题</h1>
    <p>你好，我是文章的内容</p>
    <footer>
        <p>最终解释权归XXX所有</p>
    </footer>
</article>
```

`article` 内部可以嵌套`article`，表示评论或者其他跟文章有关联的内容。`article`内部还可以嵌套`section`，如下：

```html
<article>

    <h1>web语义化</h1>
    <p>什么是语义化？</p>

    <section>
        <h2>语义化详解</h2>
        <p>语义化就是。。。</p>
    </section>

    <section>
        <h2>语义化特点</h2>
        <p>语义化特点就是。。。</p>
    </section>

</article>
```

文章内`section`是独立的部分，但是它们只能算是组成整体的一部分，从属关系，`article`是大主体，`section`是构成这个大主体的一个部分。

**注意：**

* 自身独立情况下：用`article`。

* 是相关内容： 用`section`。

* 没有语义的： 用`div`。

#### section 元素

`section` 元素代表文档中的“节”或“段”，“段”可以是指一片文章里按照主题的分段；“节”可以是指一个页面里的分组。`section`通常还带标题，虽然html5中section会自动给标题h1-h6降级，但是最好手动给他们降级。

代码栗子：

```html
<section>
    <h1>section是啥？</h1>
    <article>
        <h2>关于section</h2>
        <p>section的介绍</p>
        <section>
            <h3>关于其他</h3>
            <p>关于其他section的介绍</p>
        </section>
    </article>
</section>
```

**注意：**

* 一张页面可以用`section`划分为简介、文章条目和联系信息。不过在文章内页，最好用`article`。`section`不是一般意义上的容器元素，如果想作为样式展示和脚本的便利，可以用`div`。
* 表示文档中的节或者段。
* `acticle`、`nav`、`aside`可以理解为特殊的`section`，如果可以用`article`、`nav`、`aside`就不要用`section`，没有实际意义的就用`div`。

#### aside元素

`aside` 元素被包含在`article`元素中作为主要内容的附属信息部分，其中的内容可以是与当前文章有关的相关资料，标签，名词解释等。

代码栗子：

```html
<article>
    <p>内容</p>
    <aside>
        <h1>作者简介</h1>
        <p>小维,哈哈哈</p>
    </aside>
</article>
```

**注意：**

* `aside` 在 `article` 内表示主要内容的附属信息。

* 在`article`之外侧可以做侧边栏，没有`article`与之对应，最好不用。

* 如果是广告，其他日志链接或者其他分类导航也可以用。

#### HTML语义化小结

总之，HTML语义化是反对大篇幅使用无语义化的div+span+class，而鼓励使用HTML定义好的语义化标签。

当然，如果需要兼容低版本的IE浏览器，比如说IE8以及以下，那就需要考虑一些HTML5标签兼容性解决方案了。

## END

内容和知识参考:

* [HTML5 标签列表](<https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/HTML5/HTML5_element_list>)
* [快速理解web语义化](<https://juejin.im/entry/5ab5f229518825558a069304>)

