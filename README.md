# dotvscode

Personal VS Code configuration assets that need to be hosted at a stable URL. Served via GitHub Pages.

## Files

- [`markdown-preview.css`](./markdown-preview.css) — custom CSS for VS Code's built-in Markdown preview. Caps line length at ~800px, softens body text from pure white to off-white, keeps `strong` at pure white. Sharper hierarchy and easier on the eyes than the default.

## Why hosted

VS Code's `markdown.styles` user setting only accepts `https://` URLs or workspace-relative paths — absolute filesystem paths are [rejected for webview security](https://github.com/microsoft/vscode/issues/116881). Hosting at a stable URL gives a single source of truth that applies in every workspace, no per-repo files or symlinks.

GitHub Pages serves `.css` with the correct `Content-Type: text/css`. A gist's raw URL won't work — it serves `text/plain` + `X-Content-Type-Options: nosniff`, which the VS Code webview silently refuses to apply.

## Usage

In VS Code user settings:

```jsonc
"markdown.styles": [
  "https://davidheryanto.github.io/dotvscode/markdown-preview.css"
]
```

Reload the preview tab (or `Cmd+Shift+P` → "Developer: Reload Window") to apply.

## Editing

Edit the file in this repo, commit, push. GitHub Pages auto-deploys; new content is usually live within a minute. The VS Code preview caches per-session, so reload the preview tab to see edits.
