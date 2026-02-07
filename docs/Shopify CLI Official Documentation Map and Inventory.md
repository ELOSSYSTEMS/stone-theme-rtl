# Shopify CLI Official Documentation Map and Inventory

## Scope and criteria for official sources

This inventory is limited to sources that are unambiguously official and maintained by Shopify, and that directly document how to install, run, configure, and operate Shopify CLI across app, theme, and headless storefront workflows. The backbone is the Shopify Dev Docs command reference and workflow guides, complemented by Shopify’s official release channels and changelog entries that document behavior changes and new commands. citeturn12search13turn6search1turn21search3turn21search1turn21search2

For “current to February 2026”, the “currentness” check is anchored to Shopify CLI’s public release channels showing the latest stable version available in late January 2026 (and still current in early February), plus Shopify’s developer changelog entries posted in January 2026 that describe new Shopify CLI behaviors and commands. citeturn21search1turn21search2turn21search3turn21search12

## Core Shopify CLI reference on Shopify Dev Docs

The canonical, centralized reference for Shopify CLI is the Shopify Dev Docs “Shopify CLI” page. It defines baseline requirements (including Node.js minimum version, supported Node package managers, and Git minimum version), provides installation commands (global install via npm/Yarn/pnpm and macOS installation via Homebrew), and explains the topic-based command structure (`shopify [topic] [command]`). citeturn11view1

This same reference page documents operational essentials that affect real-world usage: upgrading via `shopify version` plus reinstalling the latest package, configuring network proxy support in newer CLI versions via `SHOPIFY_HTTP_PROXY` / `SHOPIFY_HTTPS_PROXY`, and opting out of anonymous usage reporting via `SHOPIFY_CLI_NO_ANALYTICS=1`. citeturn11view1

The official command reference is organized into topic indexes, each of which links to dedicated per-command documentation pages (flags, examples, environment variable mappings). The topic index pages and their command sets are:

**App topic index (Shopify CLI app commands)**: `app build`; `app config link`; `app config pull`; `app config use`; `app deploy`; `app dev`; `app dev clean`; `app env pull`; `app env show`; `app function build`; `app function info`; `app function replay`; `app function run`; `app function schema`; `app function typegen`; `app generate extension`; `app import-custom-data-definitions`; `app import-extensions`; `app info`; `app init`; `app logs`; `app logs sources`; `app release`; `app versions list`; `app webhook trigger`. citeturn4view0turn21search3

**Theme topic index (Shopify CLI theme commands)**: `theme check`; `theme console`; `theme delete`; `theme dev`; `theme duplicate`; `theme info`; `theme init`; `theme language-server`; `theme list`; `theme metafields pull`; `theme open`; `theme package`; `theme profile`; `theme publish`; `theme pull`; `theme push`; `theme rename`; `theme share`. citeturn4view1turn22view0

**Hydrogen topic index (Shopify CLI hydrogen commands)**: `hydrogen build`; `hydrogen check`; `hydrogen codegen`; `hydrogen customer-account-push`; `hydrogen debug cpu`; `hydrogen deploy`; `hydrogen dev`; `hydrogen env list`; `hydrogen env pull`; `hydrogen env push`; `hydrogen generate route`; `hydrogen generate routes`; `hydrogen init`; `hydrogen link`; `hydrogen list`; `hydrogen login`; `hydrogen logout`; `hydrogen preview`; `hydrogen setup`; `hydrogen setup css`; `hydrogen setup markets`; `hydrogen setup vite`; `hydrogen shortcut`; `hydrogen unlink`; `hydrogen upgrade`. citeturn20view0turn4view2

**General command index (Shopify CLI general commands)**: `auth login`; `auth logout`; `commands`; `config autocorrect off`; `config autocorrect on`; `config autocorrect status`; `help`; `search`; `upgrade`; `version`. citeturn4view3turn1search3

A complementary “front door” on Shopify Dev Docs highlights Shopify CLI as the recommended accelerator for initializing apps, themes, and headless storefronts, reinforcing Shopify CLI as the common toolchain entry point across these tracks. citeturn12search14

## Official guides for app development workflows

Shopify’s primary “how to use Shopify CLI for apps” guide is the “About Shopify CLI for apps” documentation. It frames Shopify CLI as an app development tool, lists core features (templates, extension generation, Dev Dashboard app record creation, local preview via tunnels, deploy of configuration and extensions, and doc search), and establishes the “Getting started” entrypoint (`shopify app init`) aligned to Shopify CLI’s conventional app directory structure expectations. citeturn6search1

That guide also documents operational choices that materially affect teams: using Shopify CLI globally vs as a local dependency, and the workflow to switch between them. It explicitly notes that, as of Shopify CLI version 3.59.0, installing the separate `@shopify/app` package is no longer required because it is bundled with `@shopify/cli`. citeturn6search1

For the core local development loop, Shopify’s “Test apps locally” guide explains `shopify app dev` as the mechanism for dev-store previews and real-time iteration. It describes `app dev` as orchestrating dev previews and file watching for configuration/extensions, serving embedded web apps where applicable, and starting a local dev server for extensions that support browser-based preview. citeturn5search6

When a team needs specific networking behavior, Shopify’s “Select a networking option for local development” guide documents `shopify app dev --use-localhost` (noting version gating and the use of a local HTTPS certificate via mkcert), plus a reverse proxy port that can be overridden via a flag. It also documents limitations of localhost-based development for Shopify features that require externally reachable endpoints (for example, webhooks and other direct invocations). citeturn1search7

For configuration-as-code, Shopify’s “App configuration” reference documents TOML-based app configuration, clarifying that updates to `shopify.app.toml` apply automatically during `app dev` for the chosen dev store, while production-impacting configuration requires `deploy`. It also states that `shopify app config push` is no longer supported, and directs developers to use `deploy` instead (including CI/CD migration guidance). citeturn6search0

For multi-environment management, “Manage app config files” describes linking and managing multiple configuration files in a single repo, using `shopify app config link` to create additional configs, `shopify app config use` to select a default, and `--config` flags to override defaults in scripted or automated contexts. citeturn6search3

For teams migrating away from Dev Dashboard–managed apps, “Migrate from a Dev Dashboard-managed app to Shopify CLI” documents the official migration path using `shopify app init`, `shopify app config link`, and then `shopify app deploy`, along with rationale such as version controlling configuration and unlocking CLI-only configuration elements. citeturn6search2

For deployment semantics, the dedicated `app deploy` command documentation clarifies that `deploy` builds and deploys app configuration and extensions into a versioned snapshot that can be released to users, while explicitly stating that it does not deploy the web app component, which must be deployed to the developer’s own hosting solution. citeturn5search15

For CI/CD, Shopify provides a tutorial on deploying app components programmatically via Shopify CLI in a pipeline, including constraints such as deploying “everything at once” rather than deploying only subsets of extensions or configuration. citeturn5search1

Shopify’s “About app versions” documentation further anchors deployment behavior by describing that Shopify CLI `deploy` creates an app version that is then released, and that app configuration and extensions are versioned together. citeturn21search4

## Official guides for theme development workflows

Shopify’s primary “how to use Shopify CLI for themes” guide is “Shopify CLI for themes”. It documents Shopify CLI as the theme developer toolchain, outlines features (including development themes for safe preview/share workflows, hot reload behavior, initializing themes, pushing/publishing from the command line, and using environments), and points to the official theme command reference. citeturn10view0turn11view0

Within that same guide, Shopify defines “development themes” as temporary hidden themes connected to a store for local testing, notes that they do not count toward theme limits, and states they are deleted from the store after seven days of inactivity. It also describes lifecycle behaviors such as deletion of the development theme on `shopify auth logout`, and the recommendation to push to an unpublished theme when a preview link must remain accessible after logout. citeturn10view0

Shopify’s “Tools for building and editing themes” page explicitly distinguishes current and legacy tooling, listing Shopify CLI (major version three) as the primary tool and identifying Shopify CLI (major version two) and Theme Kit as legacy tools. citeturn1search2

For authentication and store access, “Shopify CLI for themes” documents multiple supported methods (logging in with a Shopify account, using a Theme Access password, or using a custom app access token) and documents store selection via `--store`, plus checking the active store via `shopify theme info`. citeturn10view0

To support reproducible workflows across stores and contexts, “Theme environments for Shopify CLI” documents environments configured in `shopify.theme.toml`, selectable via `--environment` (and the `-e` alias), and defines precedence rules across command flags, environment variables, and environment settings. It also documents multi-environment execution for selected theme commands. citeturn7search0

For excluding non-theme files from CLI operations, “Shopify CLI for themes” documents `.shopifyignore` at the theme repo root, the supported pattern formats (file names, wildcards, regex), and how `.shopifyignore` interacts with the `--ignore` flag during `push`/`pull`. citeturn22view0

For CI/CD automation on themes, “Use Shopify CLI in a CI/CD pipeline” documents the Theme Access password requirement, and provides the environment variable interface (`SHOPIFY_CLI_THEME_TOKEN`, `SHOPIFY_FLAG_STORE`, optional `SHOPIFY_FLAG_FORCE`) along with a high-level pipeline structure (Node setup, global CLI install, and the desired theme command). citeturn7search2

For credentials provisioning, “Manage theme access” documents the Theme Access app as the mechanism for creating scoped passwords for theme development with Shopify CLI (and Theme Kit), and describes the passwords as scoped to theme write access. citeturn1search17

For linting and best-practice checks in a CLI workflow, Shopify’s Theme Check documentation includes a “Theme Check commands” page describing that Theme Check can be run through Shopify CLI, and specifies that running Theme Check commands requires installing `@shopify/cli` and `@shopify/theme`. citeturn1search11turn4view1

For editor tooling, “Shopify Liquid Language Server” documents the language server as a Shopify CLI theme command (invoked via `shopify theme language-server`) and outlines the kinds of editor features it enables. citeturn7search3turn4view1

For historical and migration context, “Migrate to Shopify CLI” documents that theme support was added to Shopify CLI (major version three) in October 2022, and provides a structured comparison of workflow changes between the older and newer CLI approaches (including authentication flow differences and command renames). citeturn7search1turn22view0

## Official guides for Hydrogen storefront workflows

For headless storefronts, Shopify’s Hydrogen documentation treats Shopify CLI as the primary local-development and deployment interface. The “Getting started with Hydrogen and Oxygen” tutorial uses CLI commands to run a local dev server (`shopify hydrogen dev`), link a local project to Shopify (`npx shopify hydrogen link`), pull environment variables (`npx shopify hydrogen env pull`), and deploy to Oxygen hosting (`npx shopify hydrogen deploy`). citeturn15search0turn17search0

The Hydrogen “Deployments” guide documents manual deployment via the Hydrogen CLI `deploy` command and positions the Hydrogen CLI as the interface for both manual and custom CI/CD workflows (in addition to the GitHub-based path). citeturn15search4turn17search3

For custom CI/CD outside of GitHub, “Deploy from any CI/CD system with deployment tokens” documents the requirement for an Oxygen deployment token for the `deploy` command, and provides examples for multiple CI/CD systems. It also documents token lifecycle and operational guidance, including that tokens are time-limited and that separate tokens per service are preferred for security. citeturn16search4turn17search5

For automated testing, “End-to-end testing” documents how to generate an authentication bypass token through the Hydrogen CLI deploy flow (writing a deploy log file with the deployment URL and bypass token), and how to use the token in CI-driven test execution. citeturn16search5turn17search15

For runtime parity and local debugging implications, “Oxygen runtime” documents that local development should run via `shopify hydrogen dev` and notes a legacy runtime flag for older Hydrogen versions, positioning the Shopify CLI command reference as the authoritative list of options. citeturn15search1turn17search1

The authoritative command-level reference for Hydrogen CLI remains the Shopify Dev Docs Shopify CLI “Hydrogen commands” index (with each command linking to its own flags-and-examples page). citeturn20view0turn12search1

## Release, versioning, and change tracking through early February

To validate the documentation set against “current to February 2026”, Shopify CLI’s public release channels indicate the latest stable release available in late January 2026: the Shopify CLI repository release list shows version 3.90.0 published on January 29, 2026, and the `@shopify/cli` npm package metadata reflects the same latest version and publish date. citeturn21search1turn21search2

Shopify’s official developer changelog provides additional “what changed” context tied to Shopify CLI versions in January 2026, including an entry describing Shopify CLI 3.89 introducing `shopify app import-custom-data-definitions` for migrating metafield/metaobject definitions to declarative TOML, and a separate entry describing more control for CI/CD deploy safety via new flags on `shopify app deploy` and `shopify app release`. citeturn21search3turn21search12

For legacy context (useful when encountering older internal tooling or archived projects), the older Shopify CLI repository (the legacy major line) shows releases ending in 2023, reinforcing that the actively evolving CLI is the newer `Shopify/cli` line referenced by the current Shopify Dev Docs. citeturn21search11turn21search1

Shopify’s theme tooling documentation also frames this split operationally by labeling Shopify CLI (major version two) as a legacy tool alongside Theme Kit, while positioning Shopify CLI (major version three) as the primary current theme developer tool. citeturn1search2turn7search1turn21search1
