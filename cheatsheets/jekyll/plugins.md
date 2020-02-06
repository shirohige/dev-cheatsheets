# Jekyll Plugins

## Gemfile

### Samples

Install a gem:

```
gem 'foo'
gem 'foo', '~> x.y.z'
gem install foo -v x.y.z
```

Install a Jekyll plugin:

```ruby
gem 'foo', group: :jekyll_plugins
```

Example of `Gemfile` for a Jekyll project:

<!-- TODO add links to these plugins, using my other quick start repos -->

```ruby
source 'https://rubygems.org'

gem 'jekyll', '~> 3.8.5'

group :jekyll_plugins do
  gem 'jekyll-feed'
  gem 'jekyll-sitemap'
end
```

Additional plugins:

```
  gem 'github-pages'
  gem 'jekyll-github-metadata'
```

### Resources

- Bundler
    - [Gemfile](https://bundler.io/v1.5/gemfile.html).
    - [Groups](https://bundler.io/v1.12/groups.html)
- [Jekyll Plugin Installation](https://jekyllrb.com/docs/plugins/installation/) doc.
- Plugins
    - Github Pages Plugin
        - [github/pages-gem](https://github.com/github/pages-gem) repo
        - [Github Pages](https://jekyllrb.com/docs/github-pages/) plugin in the Jekyll docs. This gives you a couple of Jekyll plugins and themes, which may be unnessary if you are running locally and only need to install one or two of those.
        - [Versions](https://pages.github.com/versions/) - Plugins supported by the `github-pages` plugin.
    - Github Metadata
        - [jekyll/github-metadata](https://github.com/jekyll/github-metadata) repo.
        - This is loaded by the Github Pages plugin. Sample output [here](https://github.com/jekyll/github-metadata/blob/master/docs/site.github.md) for `site.github` namespace.
- See a fuller Gemfile with comments in one of my repos [here](https://github.com/MichaelCurrin/jekyll-blog-demo/blob/master/Gemfile).

Why the jekyll_plugins group in the samples above? The docs say:

> Jekyll gives this particular group of gems in your Gemfile a different treatment. Any gem included in this group is loaded before Jekyll starts processing the rest of your source directory.

A gem included here will be activated even if its not explicitly listed under the plugins: key in your site’s config file.

## Jekyll Plugins

### Local

Put plugins as `.rb` files in your `_plugins` directory.

Guides:
- [Your first plugin](https://jekyllrb.com/docs/plugins/your-first-plugin/)
- [Generators](https://jekyllrb.com/docs/plugins/generators/)

### External

If you are building on Github Pages, then in addition to a _Gemfile_ you must add plugins to your `_config.yml` file as such:

```yml
plugins:
  - jekyll-feed
  - jekyll-sitemap
```

Additional:

```yml
  - github-pages
  - jekyll-github-metadata
```

## Remote themes

For themes not supported by Github Pages plugin, you can set a remote theme using a plugin.

- [benbalter/jekyll-remote-theme](https://github.com/benbalter/jekyll-remote-theme)

Add to `Gemfile`:

```ruby
gem "jekyll-remote-theme"
```

Add to `_config.yml`:

```yml
plugins:
  - jekyll-remote-theme

remote_theme: benbalter/retlab
```