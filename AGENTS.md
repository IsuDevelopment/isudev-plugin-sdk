# isudev/plugin-sdk

Shared cloud plumbing for isuDev WordPress plugins: API client, site registration (with the `site-verify` REST route), license cache and the `register`/`license` WP-CLI subcommands. Read `README.md` for the classes and how a plugin installs it.

## Rules

1. **Plugins vendor this with Strauss** under their own namespace (`IsuDev\<Product>\Vendor\`). Never rely on it being loaded globally.
2. **The API contract is the platform's** (`~/Other Projects/isudev-platform`, `AGENTS.md` there; shared rules in the `isudev-plugins` skill). Changes here must stay compatible with installed plugins: additive only, unless the user agrees.
3. **Secrets are write-only:** the site token and license key are never printed, logged or put in URLs.
4. **Degrade, don't break:** keep the last good Pro state through API outages (`License`).
5. **WordPress coding standards:** `composer lint` must pass (CI runs it).
6. **Release:** bump nothing in files; tag `vX.Y.Z` (semver: a new feature is a minor, a fix a patch). Then in each plugin: `composer update isudev/plugin-sdk`, test, commit its `vendor-prefixed/`.

## Used by

- `isudev-reviews` (`IsuDevelopment/wp-reviews`), prefix `isurev`.
