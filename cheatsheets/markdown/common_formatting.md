# Common formatting


## Headings

```markdown
# Header 1

## Header 2

### Header 3

Alternative below - note there is no whitespace and no `#`.

Header 1
===

Header 2
---
```


## Horizontal rule

```markdown
See the triple dash with white space before it.

---

More content here.
```


```markdown
**Bold**
__Bold alt__

_Italics_
*Italtics alt*

_**Nested styling**_
```

The following are equivalent, though Github's markdown editor only shows a preview in the edit window for the later.

```markdown
~Strikethrough~
~~Strikethrough~~
```


## Links

```markdown
[Link](url)

![Image](src)
```


## Paragraph

If there are two paragraph lines with no break between, Markdown will show them on online. Therefore you can either add white space between, use a `<br>` tag, or use a double white space at the end of the line (not pratical if your IDE trims whitespace).

```markdown
Line 1

Line 2

Line 3 and
continuation of line 3.
```


## Quotes

Single line.

```markdown
> Quote
```

Multi-line. Note that the line break rule from the previous section applies to quotes as below.

```markdown
> Multi-line quote.
>
> Note the empty line above.

> This quote
> actually appears on one line.
```

Nesting quotes.

```markdown
> How to nest a quote.
> > Repeat the quote symbol.
```

Quote a list of bullet points (from one source).

```markdown
> - Point A
> - Point B
> - Point C
```

Add quotes from multiple sources to separate bullet points.

```markdown
- > Point A
- > Point B
- > Point C
```