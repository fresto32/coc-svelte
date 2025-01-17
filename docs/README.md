# Docs for coc-svelte

## Setup

Do you want to use TypeScript/SCSS/Less/..? See [Using with preprocessors](#using-with-preprocessors).

### Using with preprocessors

[Generic setup](./preprocessors/in-general.md)

#### Language specific setup

-   [SCSS/Less](./preprocessors/scss-less.md)
-   [Other CSS languages, TailwindCSS](./preprocessors/other-css-preprocessors.md)
-   [TypeScript](./preprocessors/typescript.md)

## Documenting components

To add documentation on a Svelte component that will show up as a docstring in
LSP-compatible editors, you can use an HTML comment with the `@component` tag:

```html
<!--
 @component
 Here's some documentation for this component. It will show up on hover for
 JavaScript/TypeScript projects using a LSP-compatible editor such as VSCode or
 Vim/Neovim with coc.nvim.

 - You can use markdown here.
 - You can use code blocks here.
 - JSDoc/TSDoc will be respected by LSP-compatible editors.
 - Indentation will be respected as much as possible.
-->

<!-- @component You can use a single line, too -->

<!-- @component But only the last documentation comment will be used -->

<main>
    <h1>
        Hello world
    </h1>
</main>
```

## Troubleshooting / FAQ

### Using TypeScript? See [this section](./preprocessors/typescript.md#troubleshooting--faq)

If using TypeScript with SvelteKit, to add syntax highlighting to `<script lang="ts">` blocks, add the following to your `init.vim`.

```
let g:vim_svelte_plugin_load_full_syntax = 1
let g:vim_svelte_plugin_use_typescript = 1
```

### Using SCSS or Less? See [this section](./preprocessors/scss-less.md#troubleshooting--faq)

#### If I update a TS/JS file, Svelte does not seem to recognize it

You need to save the file to see the changes. If the problem persists after saving, check if you have something like this set in your settings:

```json
"files.watcherExclude": {
  "**/*": true,
}
```

If so, this will prevent the language server from getting noticed about updates, because it uses a file watcher for `js`/`ts` files.

#### My Code does not get formatted

Your default formatter for Svelte files may be wrong.
- Maybe you set all files to be formatted by the prettier extension. Install `prettier-plugin-svelte` from npm.
