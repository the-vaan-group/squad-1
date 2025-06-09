# 🚀 Merging Tasks

This document outlines the expectations for the information that needs to be included in the PR description to ensure a smooth deployment process.

Include a clear section in your PR changes that outlines:

- Any additional steps required on the deployed UAT theme for the PR to function correctly.
- Any dependencies, manual actions, or order of operations to follow.
- Whether any data or configuration is expected to change (e.g., metafields, theme settings).

## 1. 🌍 Global Translations

Whenever possible, use [section-scoped locales](https://shopify.dev/docs/storefronts/themes/architecture/sections/section-schema#locales) instead of global ones (like `locales/*.json`). This approach reduces the need for manual translation updates with each deployment and helps ensure consistency.

If section-scoped locales cannot be used and the PR includes new or updated global translations:

- Add the new translation keys/values to the relevant `locales/*.json` files.
- Ensure translations are consistent across all supported languages.
- Mention any translation requirements in this section.

## 2. 🧩 JSON Templates and Section Settings

If the PR includes updates to JSON templates or section settings:

- Specify which templates have been added or modified.
- Describe any new blocks, settings, or schema changes that need to be applied when this PR is deployed to a new UAT environment.

## 3. 🔧 App Configurations / 3rd-Party Integrations

If the PR introduces or updates app integrations:

- Detail any apps that need to be installed or configured.
- List required credentials, API keys, or webhooks.
- Describe any steps needed to sync or initialize the integration in the UAT environment.

## 4. 🧬 Metaobjects and Metafields

If the PR involves adding or updating Shopify metafields or metaobjects:

- All metaobject or metafield changes, along with their related functionality, must be created and fully tested on the dev store before the PR is approved.
- New metaobjects or metafields should be created in all stores (including expansion stores) by the engineer working on the task as part of task completion. Modifications or updates to existing metafields should follow the outlined process of being explicitly called out for inclusion in a release.
- Clearly document any new metaobjects or metafields added, including their namespace, key, and type.
- For changes to existing metafields or metaobjects, describe what was modified (e.g., schema, validations, allowed values).
- List any required values or test data that should be created in the UAT store.