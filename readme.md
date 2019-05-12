# Import Pika Web

A Babel plugin for transforming imports on files to ESM imports for @pika/web.

```js
import preact from 'preact'; // Transforms this 🚫
import preact from './web_modules/preact.js'; // Into this ✅
```

## Installation

```bash
npm i -D babel-plugin-import-pika-web
```

## Usage

Add the following to `.babelrc`:

```json
{
  "plugins": [
    [
      "import-pika-web",
      {
        "dir": "dist/web_modules",
        "ignore": ["jest"]
      }
    ]
  ]
}
```

This plugin will resolve all paths to a module relative to the web modules
folder set. Also, according to the ES spec, it will also add a `.js`
extension to any extension-less imports.

## Options

| Name     | Default         | Description                                                                                                                                       |
| :------- | :-------------- | :------------------------------------------------------------------------------------------------------------------------------------------------ |
| `dir`    | `"web_modules"` | Location of the web modules. Should usually match the `--dest` option for @pika/web.                                                              |
| `ignore` | `[]`            | Exact names of modules to ignore, if you find it transforming things it shouldn’t (e.g. `"react"` will match `"react"` but ignore `"react-dom"`). |

## Examples

[TypeScript + @pika/web][pika-web-preact]

[pika-web-preact]: https://github.com/dangodev/pika-web-preact
