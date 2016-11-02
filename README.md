# handlebars-helper-url

Handlebars helper that format urls depending on the environment. This plugin is used along with [metalsmith-metadata](https://github.com/segmentio/metalsmith-metadata).

## Installation

```
npm install handlebars-helper-url
```

## Usage

Refer to `metalsmith-metadata` to know more, but basically you need to create your metadata as a YAML file in the root of your sources directory:

```yaml
// globals.yaml

author:
  name: Antonio Hernández
  email: ahdiaz [at] gmail

site:
  title: Work in progress
  url:
    devel: /
    prod: http://ahdiaz.euler.es/
```

In your metalsmith script:

```js
var handlebars = require('handlebars');
var metadata = require('metalsmith-metadata');
var hbturl = require('handlebars-helper-url')(handlebars);

new Metalsmith(__dirname)
    .use(metadata({
      globals: './path/to/globals.json'
    }))
    .build();
```

When you build your site the urls will be relatives or absolutes to your site depending on the specified environment:

```bash
$ NODE_ENV=production node index.js
```

### **`handlebars`** `Object`

    A Handlebars instance.

## License

MIT License, see [LICENSE](https://github.com/ahdiaz/handlebars-helper-url/blob/master/LICENSE.md) for details.
