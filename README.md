# GhostJSON

GhostJSON is a theme for [Ghost](http://tryghost.com) that attempts to provide a clean, JSON based API for consuming Ghost blogs. It is designed to work in tandem with [my fork of Ghost](https://github.com/carsondarling/Ghost), which has only minimal modifications from the official Ghost.

In general, I've attempted to keep all of the fields that are availalble while building templates available in the JSON rendering, including as much meta-data as I can. If you find any errors, please don't hesitate to let me know.

## Dependencies

In order to run this theme, you should be using [my fork of Ghost](https://github.com/carsondarling/Ghost), or you make similar changes. The theme depends on two custom Handlebars helpers, `cleanJSON` and `safe`.

#### safe ([source](https://github.com/carsondarling/Ghost/blob/json-api/custom/helpers.js#L4))

`safe` is a block-level helper that consumes HTML, and returns a JSON-safe string. The primary use is for formatting the content of each post.

#### cleanJSON ([source](https://github.com/carsondarling/Ghost/blob/json-api/custom/helpers.js#L13))

`cleanJSON` is a block-level helper that consumes JSON, and removes all newlines and leading whitespace. The goal is to be a quick method of saving bandwidth, while still allowing the theme to be written in a sane manner.

## Example Objects

To see what values are available, the [Ghost Theme documentation](http://themes.ghost.org/) is the best resource. The [Context Table](http://themes.ghost.org/v0.5.8/docs/structure#context-table) is particularly useful.

In general, I've tried to keep it so that if a value is not available, it is set to `null`.

### @blog

```
{
  "url": "http://this.is.my.url/",
  "title": "Blog Title",
  "description": "This is my blog description",
  "logo": "http://this.is.my.url/logo.gif",
  "cover": "http://this.is.my.url/cover.gif"
}
```

### author

```
{
  "id": 1,
  "name": "Carson",
  "bio": "Carson writes code.",
  "location": "Boston, MA",
  "website": "http://carsondarling.com",
  "image": "http://this.is.my.url/carson.gif",
  "cover": "http://this.is.my.url/carson-cover.gif",
  "url": "http://this.is.my.url/author/carson/"
}
```

### tag

```
{
  "image": "http://this.is.my.url/tag.gif",
  "slug": "getting-started",
  "name": "Getting Started",
  "description": "Information about Ghost"
}
```

### post

```
{
  "id": 1,
  "title": "My Post Title",
  "excerpt": "This is the start of my post",
  "content": "This is the content of my <a href=\"Well hello\">post</a>.",
  "url": "http://this.is.my.url/post1",
  "image": "http://this.is.my.url/image.gif",
  "featured": false,
  "page": false,
  "meta_title": "Meta title for this post",
  "meta_description": "meta description for this post",
  "published_at": "2015-01-05T12:54:10.048Z",
  "author": {
    "id": 1,
    "name": "Carson",
    "bio": "Carson writes code.",
    "location": "Boston, MA",
    "website": "http://carsondarling.com",
    "image": "http://this.is.my.url/carson.gif",
    "cover": "http://this.is.my.url/carson-cover.gif",
    "url": ""http://this.is.my.url/author/carson/"
  },
  "tags": [{
    "image": "http://this.is.my.url/tag.gif",
    "slug": "getting-started",
    "name": "Getting Started",
    "description": "Information about Ghost"
  }]
}
```


### pagination

```
{
  "page": 1,
  "prev": null,
  "next": 2,
  "pages": 2,
  "total": 5,
  "limit": 3
}
```