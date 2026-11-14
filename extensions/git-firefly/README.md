# Git Firefly for Symbiont

<img width="720" src="https://s2.loli.net/2024/05/02/n8PkoAaFdrNsGZ5.png" />

Provide the syntax highlighting for the following Languages:

- [Git Attributes](https://github.com/tree-sitter-grammars/tree-sitter-gitattributes): .gitattributes, .git/info/attributes, etc
- [Git Config](https://github.com/the-mikedavis/tree-sitter-git-config): .gitconfig, .gitmodules, .lfsconfig, config.worktree
- [Git Ignore](https://github.com/shunsambongi/tree-sitter-gitignore): .gitignore, .dockerignore, .npmignore, .prettierignore, etc
- [Git Rebase](https://github.com/the-mikedavis/tree-sitter-git-rebase): git-rebase-todo

Adapted from the upstream Git Firefly extension by d1y and Peter Tripp.

## Configuration

This extension recognizes most filenames out of the box. For uncommon paths, add `file_types` in Symbiont settings:

```json
{
  "file_types": {
    "Git Attributes": ["**/{git,.git,.git/info}/attributes"],
    "Git Config": ["*.gitconfig", "**/{git,.git,.git/modules,.git/modules/*}/config"],
    "Git Ignore": ["**/{git,.git}/ignore", "**/.git/info/exclude"]
  },
}
```

See the [repository README](../../README.md) for development and publishing.
