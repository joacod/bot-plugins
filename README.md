# Bot plugins

Plugins for Grok Bot, Cursor and Grok. Each plugin lives in `plugins/<name>/` with its own manifests, README, CHANGELOG and LICENSE.

## Plugins

| Plugin | Description |
|---|---|
| [`fleet-self-learning`](plugins/fleet-self-learning) | Lets one Grok Bot or a whole fleet learn from corrections, edits, reactions and always/never instructions through a shared lessons folder and a weekly review. Skill-only. |

## Installation

### Grok Bot and Cursor

Add this repository as a plugin source:

1. Open **Settings**.
2. Select **Plugins**.
3. Paste `https://github.com/joacod/bot-plugins` in the **Search or Paste Link** input.
4. Select the plugin and click **Add**.

- Marketplace: [`.cursor-plugin/marketplace.json`](.cursor-plugin/marketplace.json)

To test locally, copy `plugins/<name>` to `~/.cursor/plugins/local/<name>` and reload.

### Grok

Open the extensions modal with `/plugins`, go to the **Marketplace** tab, select the plugin and press `i` to install.

- Marketplace: [`.grok-plugin/marketplace.json`](.grok-plugin/marketplace.json)

## Layout

```
.cursor-plugin/marketplace.json
.grok-plugin/marketplace.json
plugins/<name>/
  .cursor-plugin/plugin.json
  .grok-plugin/plugin.json
  assets/logo.png, logo.svg
  skills/<skill>/SKILL.md
  README.md
  CHANGELOG.md
  LICENSE
```

## License

MIT. See [`LICENSE`](LICENSE). Each plugin also carries its own license file.
