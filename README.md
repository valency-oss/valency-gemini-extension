# Valency Gemini CLI Extension

A Gemini CLI extension that connects to the [Valency](https://app.valency.io) MCP server, giving Gemini direct access to scientific papers from arXiv, bioRxiv, medRxiv, and PubMed.

## Install

```
gemini extensions install https://github.com/valencyio/valency-gemini-extension
```

## Authenticate

Start `gemini`, then run:

```
/mcp auth valency
```

Sign in with the email you use at [app.valency.io](https://app.valency.io). The Valency account is independent of your Google account, so the two emails do not need to match.

## Verify

Inside `gemini`, run:

```
/mcp list
```

You should see `valency` listed as connected, with its tools enumerated underneath.

Try a prompt like:

> Search for papers about quantum computing.

Gemini will pick the right Valency tool and stream results back.

## Accounts and docs

Create or manage your account at [app.valency.io](https://app.valency.io). Documentation for the underlying tools and the research platform lives at [valency.io](https://valency.io).

## Troubleshooting

If `/mcp auth valency` fails, first confirm the extension installed cleanly:

```
gemini extensions list
```

If auth completes but no Valency tools appear, restart `gemini` so it picks up the new server connection.

<details>
<summary>Manual install (for environments where <code>gemini extensions install</code> is unavailable)</summary>

If you're on a corp-locked machine or otherwise can't use the extensions system, drop the MCP server config into your `~/.gemini/settings.json` directly:

```json
{
  "mcpServers": {
    "valency": {
      "httpUrl": "https://labs.valency.io/mcp",
      "authProviderType": "dynamic_discovery",
      "oauth": {
        "enabled": true,
        "clientId": "FslW0nVE1JMNobe1wQEsTr7bIwhZTi89",
        "redirectUri": "http://localhost:33418/oauth/callback"
      }
    }
  }
}
```

Then restart `gemini` and run `/mcp auth valency` as above.

</details>

## License

MIT. See [LICENSE](./LICENSE).
