# MCP Connectors

Jellyfish supports **20 MCP connectors** that give your agents real-time access to external platforms. Connectors run as local MCP servers and can be assigned to one or more agents.

## Multi-Instance Support

You can connect **multiple accounts of the same platform** (e.g. two Shopify stores, three Google Ads accounts). Each instance gets a unique label (like "Spain", "US-East") so agents know which account they're working with.

## Available Connectors

### Productivity

| Connector | What it connects to | Required keys |
|-----------|-------------------|---------------|
| **Shopify** | Store monitoring: orders, inventory, products, sales | `SHOPIFY_STORE_URL`, `SHOPIFY_CLIENT_ID`, `SHOPIFY_CLIENT_SECRET` |
| **GitHub** | Repo monitoring: PRs, issues, CI pipelines | `GITHUB_TOKEN` |
| **Notion** | Read/write databases and pages | `NOTION_TOKEN` |
| **Google Drive** | Search and read documents | `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`, `GOOGLE_REFRESH_TOKEN` |

### Advertising

| Connector | What it connects to | Required keys |
|-----------|-------------------|---------------|
| **Google Ads** | Campaigns: spend, ROAS, CPC, CTR | `GOOGLE_ADS_DEVELOPER_TOKEN`, `GOOGLE_ADS_CLIENT_ID`, `GOOGLE_ADS_CLIENT_SECRET`, `GOOGLE_ADS_REFRESH_TOKEN`, `GOOGLE_ADS_CUSTOMER_ID` |
| **Meta Ads** | Facebook/Instagram campaigns: spend, creative fatigue | `META_ADS_ACCESS_TOKEN`, `META_ADS_ACCOUNT_ID` |
| **TikTok Ads** | Campaigns: spend, CVR, CPM, video views | `TIKTOK_ACCESS_TOKEN`, `TIKTOK_ADVERTISER_ID` |
| **LinkedIn Ads** | Campaigns: spend, leads, CPL, engagement | `LINKEDIN_ADS_ACCESS_TOKEN`, `LINKEDIN_ADS_ACCOUNT_ID` |
| **Amazon Ads** | Sponsored Products/Brands: ACoS, ROAS, keywords | `AMAZON_ADS_CLIENT_ID`, `AMAZON_ADS_CLIENT_SECRET`, `AMAZON_ADS_REFRESH_TOKEN`, `AMAZON_ADS_PROFILE_ID` |
| **Pinterest Ads** | Campaigns: impressions, conversions, pin engagement | `PINTEREST_ACCESS_TOKEN` |

### Email & SMS

| Connector | What it connects to | Required keys |
|-----------|-------------------|---------------|
| **Klaviyo** | Flows, campaigns: open rates, subscribers, revenue | `KLAVIYO_API_KEY` |

### Analytics

| Connector | What it connects to | Required keys |
|-----------|-------------------|---------------|
| **Google Analytics** | GA4: sessions, conversions, bounce rate, traffic | `GA_PROPERTY_ID`, `GA_CLIENT_EMAIL`, `GA_PRIVATE_KEY` |
| **Mixpanel** | Events, funnels, retention, user flows | `MIXPANEL_PROJECT_TOKEN`, `MIXPANEL_API_SECRET` |

### Logistics

| Connector | What it connects to | Required keys |
|-----------|-------------------|---------------|
| **ShipStation** | Fulfillment: unshipped orders, carrier delays | `SHIPSTATION_API_KEY`, `SHIPSTATION_API_SECRET` |
| **ShipBob** | Warehouse: inventory, processing, fulfillment times | `SHIPBOB_ACCESS_TOKEN` |

### Finance (Restricted)

These connectors are only accessible to the agent that owns them — no other agent on the team can read the data.

| Connector | What it connects to | Required keys |
|-----------|-------------------|---------------|
| **Holded** | Accounting: invoices, expenses, treasury, P&L | `HOLDED_API_KEY` |
| **Qonto** | Business banking: transactions, balances, cash flow | `QONTO_LOGIN`, `QONTO_SECRET_KEY` |
| **Stripe** | Payments: revenue, subscriptions, disputes | `STRIPE_SECRET_KEY` |
| **Wise** | Transfers: multi-currency balances, exchange rates | `WISE_API_TOKEN` |
| **Revolut Business** | Accounts: transactions, card spending, analytics | `REVOLUT_API_KEY`, `REVOLUT_ENVIRONMENT` |

## How to Add a Connector

1. Go to **Gallery > Connectors** (or click "Add MCP" in the sidebar)
2. Select the connector you want
3. Enter the required API keys
4. Optionally add a **label** (e.g. "Spain", "US-East") for multi-instance setups
5. Assign it to an agent — the agent will now have real-time access to that platform
