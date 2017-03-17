# babel-plugin-template-strings-postcss

Babel plugin for running [PostCSS](https://github.com/postcss/postcss) on template strings containing CSS at build time.

Works with [`csjs`](https://github.com/rtsao/csjs) or  [`template-css`](https://github.com/arturi/template-css), or any other CSS solution that uses template strings.

### [Autoprefixer](https://github.com/postcss/autoprefixer) example

**Before:**
```javascript
var style = css`
  .foo {
    transform: ${foo};
  }
`
```

**After:**
```javascript
var style = css`
  .foo {
    -webkit-transform: ${ foo };
            transform: ${ foo };
  }
`
```

**.babelrc**
```
{
  "plugins": [["template-strings-postcss", {
    "plugins": [["autoprefixer", {"browsers": ["last 2 versions"]}]]
  }]]
}

### Supply custom CSS function name

By default its `css`. Atom (and possibly other editors) will automatically syntax highlight your CSS inside template strings, when passed to a function called `css`.

```
{
  "plugins": [["template-strings-postcss", {
    "tagName: "csjs",
    "plugins": [["autoprefixer", {"browsers": ["last 2 versions"]}]]
  }]]
}
```

