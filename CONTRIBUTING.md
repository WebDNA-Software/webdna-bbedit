# Contributing

Thanks for your interest in improving the WebDNA BBEdit Codeless Language
Module! All changes land through **pull requests** — the `main` branch is
protected and does not accept direct pushes.

## Workflow

1. **Fork** the repository (or, if you're a collaborator, create a branch).
2. **Create a branch** for your change:
   ```sh
   git checkout -b my-change
   ```
3. **Make your edit.** This project is a single property list, `webdna.plist`.
   - `BBLMKeywordList` — container/function tags (coloured as Keywords).
   - `BBLMPredefinedNameList` — built-in value tags (coloured as Predefined
     Names).
   - Keep each tag name **lowercase** (matching is case-insensitive).
   - Don't put the same name in both arrays.
4. **Validate** the file before committing:
   ```sh
   plutil -lint webdna.plist
   ```
5. **Test** in BBEdit by copying the module into the Language Modules folder and
   relaunching:
   ```sh
   cp webdna.plist ~/Library/Application\ Support/BBEdit/Language\ Modules/
   ```
6. **Open a pull request** against `main` describing what you changed and why.

## Scope

- This repo is a **Codeless Language Module only**. A compiled BBEdit plugin
  (`.bblm`) is out of scope.

## License

By contributing, you agree that your contributions are licensed under the
[Apache License 2.0](LICENSE).
