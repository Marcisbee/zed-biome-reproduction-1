# zed-biome-reproduction-1

Repo for showing bug/inconsistency between `cli` and `zed` biome format.

## How to reproduce

1. run `npm test` - no issues
2. run `zed .`
3. open index.ts file and run formatter (cmd+shift+i)
4. run `npm test` - issues found

This is what formatter from zed produce:
```
./index.ts format ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  ✖ Formatter would have printed the following content:

    1 1 │   try {
    2   │ - ··//·Something·here
    3   │ - }·catch·(_e)·{·}
      2 │ + → //·Something·here
      3 │ + }·catch·(_e)·{}
    4 4 │


Checked 3 files in 13ms. No fixes applied.
Found 1 error.
```

---

zed settings.json
```js
{
  ...
  "lsp": {
    "biome": {
      "settings": {
        "require_config_file": true,
        "config_path": "<path>/biome.json"
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
