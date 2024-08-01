# zed-biome-reproduction-1

Repo for showing bug/inconsistency between `cli` and `zed` biome format.

## How to reproduce

1. run `npm test` - cli has issues
2. run `zed .`
3. open index.ts file and run formatter (cmd+shift+i)
4. zed did not apply formatting changes for quotes and indents

---

zed settings.json
```js
{
  ...
  "lsp": {
    "biome": {
      "settings": {
        "require_config_file": true
      }
    }
  },
  "formatter": {
    "language_server": {
      "name": "biome"
    }
  },
  "code_actions_on_format": {
    "source.organizeImports.biome": true,
    "source.fixAll.biome": true
  }
}
```
