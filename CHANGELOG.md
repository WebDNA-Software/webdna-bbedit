# Changelog

## 2026-06-17

- Initial public export of the WebDNA BBEdit Codeless Language Module.
- Keyword list synced with the WebDNA VS Code extension grammar
  (added `default`, `permredirect`, `listvariables`, `sqlresult`; removed
  duplicate and empty entries).
- Added `BBLMPredefinedNameList` so WebDNA built-in value tags (`[index]`,
  `[value]`, `[name]`, `[filename]`, `[sku]`, …) colour distinctly from
  container/function tags.
- Fixed string handling (proper double-quoted strings with `\` escape;
  removed the non-functional `=`-as-close-delimiter config).
- Disabled the empty Functions menu (`BBLMScansFunctions` off — no function
  pattern is defined).
