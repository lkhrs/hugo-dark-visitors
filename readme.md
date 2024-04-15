# hugo-dark-visitors
Give AI company scraper bots a gentle "no" with this Hugo module. Uses the [Dark Visitors API](https://darkvisitors.com/docs/robots-txts-api) to import the latest `robots.txt`.

## Installing

1. Grab your Dark Visitors API key from the [Projects](https://darkvisitors.com/projects) page
2. Add the API key to the `HUGO_DARKVISITORS` environment variable
3. Import the module
4. Tell Hugo to generate `robots.txt`
5. Configure API options (optional)

Import the module in your Hugo config:
```yaml
module:
  imports:
    - path: github.com/lkhrs/hugo-dark-visitors
```

Tell Hugo to generate `robots.txt` by adding this line to your Hugo config:
```yaml
enableRobotsTXT: true
```

## API options

By default, the module uses the "AI Data Scraper" category. The API supports more categories that you can request by adding them to your Hugo config:

```yaml
params:
  darkVisitors:
    - AI Assistant
    - AI Data Scraper
    - AI Search Crawler
```

## Customizing robots.txt

You can override the template provided by this module and use a partial to add the rules after your custom directives. Add `layouts/robots.txt` to the root of your Hugo site and import the partial inside `robots.txt`:

```go
{{ partial "dark-visitors.html" . }}
```

Add your custom directives before or after the partial.