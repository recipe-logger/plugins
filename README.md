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

## Install

You need a RecipeLogger account and a client that supports plugins and plugin
marketplaces.

Add the marketplace from GitHub:

```sh
codex plugin marketplace add recipe-logger/plugins
```

Then:

1. Restart your client and open **Plugins**.
2. Select **RecipeLogger Plugins** and install **RecipeLogger**.
3. Sign in to RecipeLogger and review the requested permissions.
4. Start a new conversation with the plugin selected.

Try asking:

> Find dinner ideas in my family's RecipeLogger recipes.

> Help me plan next week's meals.

> Prepare a shopping list from my meal plan.

Plugin availability and installation interfaces depend on your client and
workspace policies.

## Install from a local checkout

From the repository root, add the local marketplace:

```sh
codex plugin marketplace add .
```

Restart your client, then install **RecipeLogger** from **RecipeLogger Plugins**.

## Repository layout

```text
.agents/plugins/marketplace.json   # Marketplace catalog
plugins/recipelogger/plugin.json   # Plugin manifest and listing
plugins/recipelogger/mcp.json      # MCP connection and OAuth settings
plugins/recipelogger/assets/       # Brand assets
```

For repository working conventions, see [AGENTS.md](AGENTS.md).

## License

This repository is licensed under the [MIT License](LICENSE).
