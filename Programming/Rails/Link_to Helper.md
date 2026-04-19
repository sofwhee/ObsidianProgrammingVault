#rails #helper 

## syntax

`link_to(name = nil, options = nil, html_options = nil, &block)`

```
link_to(body, url, html_options = {})
```

url is a String; you can use [[URL helpers]] like `posts_path`

`link_to(body, url_options = {}, html_options = {})`

`url_options`, except `:method`, is passed to `url_for`

```
link_to(options = {}, html_options = {}) do
  # `name`
end
```

```
link_to(url, html_options = {}) do
  # name
end

link_to(active_record_model)
```

### classes and ids
`link_to "Articles", articles_path, id: "news", class: "article"
`#= <a href="/articles" class="article" id="news">Articles</a>`
