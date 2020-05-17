# Links

## Local paths

Use the `link` tag. The smart way to do links for local pages. 

This will figure out the appropriate URL. And it will give build error if the page path is not valid.  Note - do NOT use quotes around the URL otherwise they will be rendered as escaped quote tags and possibly break the HTML.

e.g.

```
-  [Link description]({% link about.md %})
```

Result:

```html
<a href="/my-base-url/about.html">Link description</a>
```

## Footer links

More Markdown then Jekyll, but still useful to keep text readable. Also this link be just below the paragraph rather than the end of the page.

```
This paragraph covers [CircleCI][0], [GitHub][1] and also [Bitbucket][2].

[0]: https://circleci.com/
[1]: https://github.com/
[2]: https://bitbucket.org/
```

## Liquid links

Link to an internal page using the path to the file in the project, not on the URL. This means you will get an error if a link is invalid.

*Since Jekyll 4.0 , you don’t need to prepend `link` and `post_url` tags with `site.baseurl`.*


Examples from [docs](https://jekyllrb.com/docs/liquid/tags/).


### Link to page

Extension must be included.

```liquid
{% link _collection/name-of-document.md %}
{% link _posts/2016-07-26-name-of-post.md %}
{% link news/index.html %}
{% link /assets/files/doc.pdf %}
```


### Link to post


```liquid
{% post_url 2010-07-21-name-of-post %}
{% post_url /subdir/2010-07-21-name-of-post %}
```

Markdown:

```liquid
[Link Text]({% post_url 2010-09-08-welcome-to-jekyll %})
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMzA0NzcwNTFdfQ==
-->