# Working notes for symbiont-extensions

This repository owns Symbiont extension source, the static registry index, and the local release script. Keep upstream licenses and copyright notices. Build coded extensions against `symbiont_extension_api` 0.1.0 and use `script/test-publish` when changing publication logic. Publish only with the owner's authorization.

## Project layout

<!-- marga:layout:start -->
Kept up to date by Marga; edit folder notes with `marga describe <folder> "…"`.
Find any file by name with `marga find <name>`; `marga map` adds the files used most lately.

```
(top) README.md, Roadmap.md (+1 more)
extensions/ — Extension source folders, with manifests, languages, optional Rust code, and upstream licenses (emmet, git-firefly, glsl, html, proto)
registry/ — Static index of published extension metadata consumed by Symbiont
script/ — Local publication command and its stubbed regression test
```
<!-- marga:layout:end -->
