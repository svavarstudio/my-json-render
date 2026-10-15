# Stripe App Examples

[Stripe Apps](https://stripe.com/docs/stripe-apps) examples demonstrating how to use json-render to build dynamic, AI-generated UI within the Stripe Dashboard.

## Structure

| Folder | Description |
|--------|-------------|
| [api/](./api) | Next.js server providing the `/api/generate` endpoint for AI-powered UI generation |
| [drawer-app/](./drawer-app) | Standard Stripe App that renders in the Dashboard drawer (sidebar) |
| [fullpage-app/](./fullpage-app) | Full-page Stripe App using `FullPageView` (requires alpha access) |

## Quick Start

These examples are packages in the repository's pnpm workspace. Install from
this checkout with its pinned pnpm version; the root `pnpm-lock.yaml` is the
shared lockfile, including when `pnpm install` runs from an example directory.
The `workspace:*` dependencies require the rest of this repository. A copied
example directory is not a standalone installable package.

### 1. Start the API server

```bash
cd api
pnpm install
cp .env.example .env  # Set AI_GATEWAY_API_KEY
pnpm dev
```

### 2. Start a Stripe App

For the standard drawer app:

```bash
cd drawer-app
pnpm install
pnpm setup
stripe apps start
```

For the full-page app (requires alpha access):

```bash
cd fullpage-app
pnpm install
cp .env.example .env  # Set STRIPE_APP_ID
pnpm setup
stripe apps start
# Navigate to https://dashboard.stripe.com/test/app/<your-app-id>
```

## Notes

- The AI generation feature requires the API server to be running. Without it, the apps fall back to locally generated specs using real Stripe data.
- The `fullpage-app` uses Stripe's full-page apps **private developer preview**. You need Stripe to enable the feature flag for your app and account. See [fullpage-app/README.md](./fullpage-app/README.md) for details.
