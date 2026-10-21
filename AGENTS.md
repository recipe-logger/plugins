# Repository guidelines

## Workflow

- Work directly on `main`. Feature branches and pull requests are not required.
- Keep commits focused and leave `main` ready to install.
- Write documentation and commit messages in English.
- Never commit credentials, signing keys, tokens, or personal data.
- Inspect the diff and stage explicit paths before committing.
- Commit, push, tag, or publish only when requested by the user.
- Never force-push `main` or rewrite published history.

## Commits

Use Conventional Commits:

```text
<type>(<scope>): <imperative description>
```

Types: `feat`, `fix`, `docs`, `chore`, `ci`, `refactor`, `test`.
Use the plugin name as scope, or `marketplace` or `repo` for shared
changes. Keep subjects concise, preferably under 72 characters, without a final
period. Add a body when motivation or migration details help.

```text
feat(recipelogger): add meal planning support
fix(recipelogger): correct the OAuth resource URL
docs(repo): clarify plugin installation
```

Use `!` and a `BREAKING CHANGE:` footer for incompatible changes.
Never claim checks passed unless they were run.

## Repository structure

- `.agents/plugins/marketplace.json`: marketplace catalog and installation policy.
- `plugins/<name>/plugin.json`: plugin identity and listing.
- `plugins/<name>/mcp.json`: remote MCP connection and OAuth configuration.
- `plugins/<name>/assets/`: plugin icons and brand assets.
- `README.md`: public purpose, features, and installation instructions.

The application and MCP server live outside this repository. Keep changes here
focused on plugin packages and the marketplace.

## Validation

- Validate edited JSON and check marketplace paths and referenced assets.
- Review authentication scopes and endpoint changes carefully.
- For functional plugin changes, verify installation, OAuth, tool discovery,
  and a read-only request in a supported client when available.
- Use test accounts when checking family isolation; never store their data here.
- Run `git diff --check` and report checks that could not be performed.
- Keep README instructions consistent with the actual configuration.
