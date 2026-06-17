# WebDNA syntax colouring for BBEdit

A **Codeless Language Module (CLM)** that adds WebDNA syntax colouring to
[BBEdit](https://www.barebones.com/products/bbedit/). It colours WebDNA tags,
built-in value tags, comments and strings in `.dna`, `.tpl`, `.inc`, `.html`
and related files — no compilation or plugins required.

---

## What it does

- Colours **WebDNA tags** (`[showif]`, `[append]`, `[text]`, `[lookup]`,
  `[formvariables]`, `[sql]`, …) as **Keywords**.
- Colours **WebDNA built-in value tags** (`[index]`, `[value]`, `[name]`,
  `[filename]`, `[sku]`, `[numfound]`, …) as **Predefined Names**, so they stand
  out from container tags.
- Colours **comments** `[!] … [/!]`.
- Colours **quoted strings** (with `\` escapes).
- Recognises the file types: `.html` `.inc` `.dna` `.tpl` `.dnalib` `.lib`.
- Case-insensitive, matching WebDNA itself.

### Limitations (inherent to the Codeless Language Module format)

These are limits of BBEdit's *codeless* modules, not bugs:

- The whole file is treated as WebDNA — **embedded HTML is not separately
  coloured**.
- It **cannot distinguish opening `[tag]` from closing `[/tag]`** tags, and does
  not do per-context parameter colouring (e.g. `&db=`, `&value=`).

Full HTML-aware, context-sensitive colouring (like the VS Code extension) would
require a *compiled* BBEdit language module, which is a separate native project that we will not be creating.

---

## Requirements

- BBEdit (any reasonably recent version; codeless language modules are broadly
  compatible across versions).

---

## Installation

1. Quit BBEdit (recommended — modules load at launch).
2. Copy **`webdna.plist`** into your BBEdit **Language Modules** folder:

   ```
   ~/Library/Application Support/BBEdit/Language Modules/
   ```

   The quickest way to open that folder: in BBEdit choose
   **BBEdit ▸ Folders ▸ Language Modules** (older versions: the
   *Application Support* folder is under your user Library). If the
   `Language Modules` folder doesn't exist yet, create it.

3. Launch BBEdit and open a `.dna` file. You should see WebDNA colouring.

> **Tip:** the `~/Library` folder is hidden in Finder. In Finder press
> **⇧⌘G** and paste the path above, or hold **⌥ (Option)** and click the Finder
> **Go** menu to reveal **Library**.

### Verify it's active

With a `.dna` file open, the language pop-up at the bottom of the editing window
(or **View ▸ Text Display ▸ Language**) should show **WebDNA**.

---

## Changing the colours

**Important:** BBEdit applies syntax colours **by category, globally across all
languages** — there is no per-language colour list in a codeless module. To
recolour WebDNA, you change the colour of the *categories* it uses.

WebDNA elements map to these BBEdit colour categories:

| WebDNA element                                   | BBEdit category    |
| ------------------------------------------------ | ------------------ |
| Tags — `[showif]`, `[append]`, `[text]`, …       | **Keywords**       |
| Built-in value tags — `[index]`, `[value]`, …    | **Predefined Names** |
| Comments — `[!] … [/!]`                          | **Comments**       |
| Quoted strings                                   | **Strings**        |

### Steps

1. Open BBEdit **Settings** (older versions: **Preferences**) — **⌘,**.
2. Go to the **Text Colors** pane (in some versions this is under
   **Appearance**).
3. Pick the **Color Scheme** you use (or duplicate one first so you don't edit a
   built-in scheme).
4. Click the colour swatch next to **Keywords** to change the tag colour, and
   **Predefined Names** for the built-in value tags. Adjust **Comments** and
   **Strings** to taste.
5. Changes apply immediately to open documents.

### Sharing a colour scheme

Colour schemes are saved as `.bbColorScheme` files in:

```
~/Library/Application Support/BBEdit/Color Schemes/
```

You can copy that file to share your exact colours with other users. Note that a
colour scheme affects **all** languages, not only WebDNA.

---

## Updating the keyword list (advanced)

`webdna.plist` is a plain XML property list. To add or change recognised tags,
edit the arrays:

- `BBLMKeywordList` — container/function tags (coloured as Keywords).
- `BBLMPredefinedNameList` — built-in value tags (coloured as Predefined Names).

Keep each name lowercase (matching is case-insensitive) and avoid putting the
same name in both arrays. After editing, run:

```sh
plutil -lint webdna.plist
```

to confirm the file is still valid, then re-copy it into the Language Modules
folder and relaunch BBEdit.

---

## Uninstall

Remove `webdna.plist` from
`~/Library/Application Support/BBEdit/Language Modules/` and relaunch BBEdit.

---

## License

Licensed under the **Apache License 2.0** — see [LICENSE](LICENSE). You're free
to use, share, modify and redistribute this module, including commercially.

## Credits

Keyword and value-tag lists derived from the WebDNA language and kept in sync
with the WebDNA VS Code extension grammar.
