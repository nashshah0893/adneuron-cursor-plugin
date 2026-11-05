# AdNeuron for Cursor

Your AI advertising copilot to create, launch, and analyze ads.

Publisher: **AdNeuron LLC**. Version: **0.2.1**.

AdNeuron connects Cursor directly to the existing hosted AdNeuron MCP service at `https://mcp.adneuron.ai/mcp`. Sign in with your own AdNeuron account and authorize the requested access. Available platforms, tools, accounts and actions depend on the connected service, your permissions, and provider eligibility. This package does not add support for future platforms by itself.

## Capabilities

- Read advertising accounts, campaign status, and stored performance.
- Analyze available metrics and explain coverage and freshness limits.
- Prepare campaign creation with an exact preview and create paused after approval.
- Review and activate campaigns only with separate explicit authorization.
- Manage campaigns using actions actually exposed by the server, subject to permissions and required approvals.

Meta and Google Ads are the scope of the integration work documented here. Amazon, LinkedIn and other planned integrations should not be assumed available until the live service supports them. Exposed tools are not a claim that every workflow has passed a live test.

## Architecture and authentication

The plugin uses Cursor's remote MCP and OAuth support. No local Node server, API adapter, demo dataset, manual bearer token, or additional advertising backend is included. Your data and actions are handled by the AdNeuron service. The package contains connection configuration, commands and guidance, not authentication credentials. Authorization and approval checks must be enforced by the server; instructions alone are not security controls.

## Local installation

1. Extract the ZIP and copy the entire `adneuron` folder, including hidden `.cursor-plugin`, to `~/.cursor/plugins/local/adneuron`.
2. Disable an existing standalone AdNeuron MCP entry while testing to avoid duplicate tool sets.
3. Restart Cursor or run **Developer: Reload Window**. Local plugin imports must be allowed.
4. In Customize, confirm the plugin components and enable the plugin MCP source. Complete sign-in if prompted.
5. Start a new Agent chat and run `/adneuron-accounts`.

No Homebrew, GitHub CLI, Node.js or npm installation is required by this plugin.

## Commands

| Command | Purpose |
| --- | --- |
| `/adneuron-accounts` | Read accounts, connection state and data source |
| `/adneuron-report` | Read stored performance with date and coverage labels |
| `/adneuron-preview-change` | Read-only preview of a proposed campaign change |
| `/adneuron-create-campaign` | Collect inputs, preview, and create paused after approval |
| `/adneuron-launch` | Preview and activate an existing campaign after separate approval |

You may also ask in ordinary language. Commands discover available server schemas rather than implementing a second set of advertising APIs. Missing metrics remain unavailable, not zero. Provider-sourced data is not necessarily fresh.

## Confirmation and spending

Campaigns are created paused. Preview the exact account, objects, currency, budgets, targeting, creative, destination and status before a write. Asset uploads also require approval. Activation and spending require explicit approval of the concrete action. Follow server-required in-app approval for AdNeuron recommendations; a chat response cannot bypass it. Never automatically retry an uncertain write.

## Validation status

The previous 0.1.0 package was observed loading locally in user-provided Cursor screenshots, with its rule, commands, MCP tool discovery and account listing. A reporting call returned no observations for an inactive/excluded account. A read-only change-preview flow stopped for campaign selection.

This 0.2.1 package has static JSON, file-path and archive checks. Its new creation/launch commands and branding still need local loading verification. Fresh OAuth sign-in, refresh and revocation, retrieval of actual performance totals, campaign creation, activation and other live writes have not been verified in this review. Do not present them as completed tests.

## GitHub upload

Upload the **contents** of the extracted `adneuron` folder to the repository root, preserving `.cursor-plugin/plugin.json`, `assets/`, `commands/`, `rules/`, `mcp.json` and this README. Use Finder's Command-Shift-period to reveal hidden files. Do not upload customer data or credentials.

## License and marketplace status

The plugin package is licensed under the MIT License. Copyright (c) 2026 AdNeuron LLC. See LICENSE for the complete terms. This license covers the files in this package; it does not license the separately hosted AdNeuron backend, grant API access, or replace the service terms. This package has not been submitted or approved for the marketplace. Local acceptance checks and unverified workflows above remain pending.

Website: https://adneuron.ai
Support: https://adneuron.ai/support
Privacy: https://adneuron.ai/privacy
Terms: https://adneuron.ai/terms
Plugin documentation: https://cursor.com/docs/plugins
