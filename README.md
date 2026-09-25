# Facebook AutoBusiness — Claude plugin

Connects Claude to a [Seller AutoBusiness](https://autobusiness.daamdekhi.com)
account so you can run day-to-day selling operations for a Facebook-based
store, in the same place you are already working: catalog, campaigns,
Facebook comments and Messenger, leads, storefront analytics, courier
delivery, and Daraz/Shopify sync.

Works in **Claude Cowork** and **Claude Code**. The server is remote, so the
desktop-only restriction that applies to plugins bundling *local* MCP servers
does not apply here — Cowork on web and mobile can use it too.

This plugin ships **no code of its own** — it is a one-line configuration that
points Claude at Seller AutoBusiness's hosted MCP server at
`https://autobusiness-mcp.daamdekhi.com/mcp`.

## Requirements

A Seller AutoBusiness account, and it must be the **owner** account — an
employee login is declined at the connector's consent screen, and a
connection already made under an employee role stops working the next time a
tool is called.

The plugin acts as **you**: the first tool call triggers a standard OAuth 2.1
+ PKCE sign-in against Seller AutoBusiness, you approve the connection, and
every request afterwards runs with your own permissions. Nothing is shared
between accounts, and you can revoke the connection at any time from inside
the assistant (`revoke_connected_app`) or the app itself.

The sign-in page is served from `shop.daamdekhi.com`, which is Seller
AutoBusiness's own backend host rather than a third party.

## Install

Once the plugin is listed in the community marketplace:

```
/plugin marketplace add anthropics/claude-plugins-community
/plugin install facebook-autobusiness@claude-community
```

To try it in Claude Code before then, clone this repo and run:

```bash
claude --plugin-dir ./autobusiness-mcp-plugin
```

## What you can ask for

- **Catalog** — "Add this product with these variants and prices" or "Bulk
  import my catalog from this spreadsheet."
- **Campaigns** — "Create a campaign for these products with a discount code
  and schedule it for this weekend."
- **Facebook** — "Reply to the new comments on my last post" or "Turn that
  older post into a product listing."
- **Messenger** — "Read my unread conversations and draft replies to the
  customers asking about stock."
- **Orders and leads** — "What are today's orders?" and "How are my leads
  trending this week?"
- **Delivery and marketplaces** — book a Steadfast consignment, or sync
  products and orders with Daraz or Shopify.

## What it will not tell you

Plan name, subscription status, prices and renewal dates are deliberately
absent from every tool result, an assistant's transcript is not a safe place
for them. Bare quota counters are the one exception, so an agent can warn you
before it burns the last of your credits. For anything billing-related, open
the Seller AutoBusiness app.

## Support

- Product: <https://autobusiness.daamdekhi.com>
- Privacy: <https://autobusiness.daamdekhi.com/privacy>
- Terms: <https://autobusiness.daamdekhi.com/terms>
- Security or support issues: **support@daamdekhi.com**, or the `submit_report`
  tool from inside a connected assistant.

## License

MIT — see [LICENSE](LICENSE).
