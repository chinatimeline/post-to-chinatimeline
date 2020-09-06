# post-to-chinatimeline
通过uri和bookmarklet分享新闻到chinatimeline

两种方法均需要手动编辑文字内容，手动选择影响力、分类和时间线主题等内容。

## URI
如果你是新闻网站站长，可按以下方法添加分享按钮，方便用户将新闻快速分享到chinatimeline
以github pages支持的jekyll静态网站模板为例，其它类似网站如hugo也类似，使用[Social Share Kit](https://socialsharekit.com/)。
```html
<!-- Social Share Kit CSS -->
<link rel="stylesheet" href="{{ site.baseurl }}/assets/css/social-share-kit.css" type="text/css">

{% assign shareurl = site.url | append: site.baseurl | append: page.url %}
{% assign sharetitle = site.name | append: '-' | append: site.description %}
<div class="ssk-sticky ssk-right ssk-center ssk-sticky-hide-xs ssk-group ssk-round">
  <a href="https://chinatimeline.github.io/form/?u={{ shareurl | url_encode }}&t={{ page.title | url_encode }}&d={{ page.date | slice: 0, 10 }}&e={{ page.content | strip_html | truncate: 400 }}" target="_blank" class="ssk ssk-github"  title="Github 时代透镜"></a>
</div>
```
参考实例 [NodeBE4/waimei](https://github.com/NodeBE4/waimei/blob/master/_includes/social-share.html)

#### 具体URI解释
`https://chinatimeline.github.io/form/`是提交网页的链接，`?`后的内容是自动填表的内容，其中`u=`后为编码后的新闻链接，`t=`后的内容为新闻标题，`d=`后为ISO格式的日期YYYY-MM-DD，`e=`后为正文内容（不超过400字符）

## bookmarklet
如果您是普通用户，希望方便的添加新闻到chinatimeline，可将以下链接添加到浏览器书签(bookmark)
```html
javascript:window.location=%22https://chinatimeline.github.io/form/?u=%22+encodeURIComponent(document.location)+%22&t=%22+encodeURIComponent(document.title)+%22&e=%22+encodeURIComponent(document.body.innerText)
```
由于不同网页的日期内容不同，日期需手动填写，内容也需要手动修改。
