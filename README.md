# RecipeLogger Plugins

Bring your family's recipes, meal plans, and shopping lists into supported
ChatGPT and Codex clients. This repository contains the RecipeLogger plugin
and its installation marketplace.

The plugin connects to [RecipeLogger](https://recipelogger.com) through its
remote MCP server at `https://recipelogger.com/mcp`. Each person signs in with
their own RecipeLogger account and authorizes access to their family's data.
The RecipeLogger application and server are maintained separately.

## What you can do

- Browse, search, create, and update family recipes, including an interactive gallery.
- Plan meals and prepare shopping lists from saved recipes.
- Use saved household shopping habits and store layouts.

## Use on ChatGPT web

For personal testing, add `https://recipelogger.com/mcp` through **Plugins → + →
Add custom MCP server** and configure OAuth. Availability depends on account
and workspace policies. See the [official quickstart](https://developers.openai.com/plugins/quickstart).

A custom repository marketplace is a separate distribution mechanism; adding
one locally does not import it into ChatGPT web. Workspace admins can use
**Admin → Plugins → Add → Import marketplace** with
`https://github.com/recipe-logger/plugins`, then configure the imported plugin's
required apps. See [workspace marketplace import](https://learn.chatgpt.com/docs/enterprise/plugin-management).

For public discovery across supported ChatGPT and Codex surfaces, the intended
route is the universal plugin directory, which requires submission, review, and
publication. This GitHub repository alone does not create a public directory
listing. Individual capabilities and availability can still vary by surface.

## Install from a marketplace (desktop and Codex)

You need a RecipeLogger account and a client that supports plugins and plugin
marketplaces.

For desktop installation, add the marketplace from GitHub:

```sh
codex plugin marketplace add recipe-logger/plugins
```

Then:

1. Restart your client and open **Plugins**.
2. Select **RecipeLogger Plugins** and install **RecipeLogger**.
3. Complete the plugin's RecipeLogger OAuth connection when prompted. No separate
   custom MCP server registration is needed for the local plugin.
4. Start a new conversation with the plugin selected.

Try asking:

> Find dinner ideas in my family's RecipeLogger recipes.

> Help me plan next week's meals.

> Prepare a shopping list from my meal plan.

In Codex CLI, use `/plugins` to browse a configured marketplace and install
the plugin, then start a new session. See [supported plugin surfaces](https://learn.chatgpt.com/docs/plugins).

Plugin availability and installation interfaces depend on your client and
workspace policies.

## Connect the installed plugin

The plugin bundles its remote MCP connection. Do not add a duplicate server with
`codex mcp add` or **Add custom MCP server** for desktop/Codex use.

For CLI installation without the plugin browser:

```sh
codex plugin add recipelogger@recipelogger
```

Start a new session, open `/mcp`, and check the plugin's RecipeLogger server and
its authentication status. Complete OAuth through the client's authentication
flow. On desktop, check **Settings → MCP servers** for authentication when needed.
Installation and account authorization are separate steps; `ON_INSTALL` requests
authentication but does not itself authorize your account.

If the plugin is installed but its server is absent, refresh the marketplace and
reinstall the plugin through `/plugins`, then start a new session:

```sh
codex plugin marketplace upgrade recipelogger
```

The source includes portable `mcp.json` plus a Codex compatibility manifest that
explicitly loads `.mcp.json`. Both describe the same endpoint. Keep their URLs
synchronized; the compatibility file uses Codex's `http` transport spelling.

See [plugin-provided MCP servers](https://learn.chatgpt.com/docs/extend/mcp?surface=cli)
and [plugin packaging](https://developers.openai.com/plugins/build/plugins).

## Install from a local checkout

From the repository root, add the local marketplace:

```sh
codex plugin marketplace add .
```

Restart your client, then install **RecipeLogger** from **RecipeLogger Plugins**.

## Repository layout

```text
.agents/plugins/marketplace.json   # Marketplace catalog
plugins/recipelogger/plugin.json   # Portable identity and metadata
plugins/recipelogger/mcp.json      # Portable MCP connection and OAuth settings
plugins/recipelogger/.codex-plugin/plugin.json # Codex listing and MCP reference
plugins/recipelogger/.mcp.json     # Codex HTTP connection compatibility
plugins/recipelogger/assets/       # Brand assets
```

For repository working conventions, see [AGENTS.md](AGENTS.md).

## License

This repository is licensed under the [MIT License](LICENSE).
