# Symbiont extensions

Source and registry for extensions owned by the Symbiont project. Symbiont began as a fork of Zed by Zed Industries.

The registry is [registry/index.json](registry/index.json). Published archives live in GitHub Releases, tagged `<id>-v<version>` with an `<id>.tar.gz` asset. HTML, Emmet, and Git Firefly are the first extensions; GLSL and Proto are here as source but are not yet published.

## Write and try an extension

1. Create `extensions/<id>/extension.toml` with an `id`, `name`, `description`, `version`, `schema_version = 1`, `authors`, and this repository URL. Add `languages/` and grammar entries if needed.
2. For Rust code, add a `cdylib` crate in that folder. Depend on `symbiont_extension_api = { version = "0.1.0", path = "../../../Symbiont/crates/extension_api" }`, implement `symbiont_extension_api::Extension`, and call `symbiont_extension_api::register_extension!`.
3. Open Symbiont's Extensions page, choose **Install Dev Extension**, and select the extension folder. Edit and reload it there until it works.

Use [HTML](extensions/html) as a worked example. Its `extension.toml` declares the HTML language server and grammar; `languages/html/` holds the language configuration and tree sitter queries; `src/html.rs` starts `vscode-html-language-server`, installing its npm package when needed. Its `Cargo.toml` shows the API dependency and `cdylib` settings. The API crate is currently a local path dependency to the private sibling `Symbiont` checkout, so building a coded extension requires that checkout at the path above.

## Build and publish

The local `symbiont-extension` CLI from Symbiont must be on `PATH`, along with `gh`, `jq`, Python 3, and `tar`. Authenticate `gh` to an account with release and push access. Run from this repo:

```sh
script/test-publish
script/publish html --dry-run
script/publish html
```

The dry run builds and prints the proposed registry entry without changing the index or GitHub. Publishing refuses an existing `<id>-v<version>` release, builds an archive, creates the release, replaces that extension's index entry, commits the index, and pushes. Bump the extension's version before publishing an update. The first publication also requires this repo to exist on GitHub with an `origin` remote; creating it and pushing the source are separate owner actions.

To build directly for inspection:

```sh
symbiont-extension --source-dir extensions/html --output-dir /tmp/symbiont-html-build --scratch-dir /tmp/symbiont-html-scratch
```

The CLI produces `archive.tar.gz` and `manifest.json` in the output directory. Run `script/publish emmet --dry-run` and `script/publish git-firefly --dry-run` before publishing those extensions too.

The `extensions/emmet` and `extensions/git-firefly` folders retain their upstream Apache licenses and list their changes in `NOTICE`. The other extension folders retain their upstream license files.
