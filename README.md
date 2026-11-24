# Open Source Contributions

Live tracker of my open source pull requests across major projects. Updated as PRs move through review.

## 📊 Stats

| Opened | In review | Approved | Merged |
| :---: | :---: | :---: | :---: |
| 13 | 9 | 3 | 0 |

## 🔀 Pull Requests

| Project | Pull Request | Status | Opened |
| :--- | :--- | :--- | :--- |
| [Backstage](https://github.com/backstage/backstage) (Spotify) | [#37096 - gitlab:group:ensureExists: support GitLab user namespaces](https://github.com/backstage/backstage/pull/37096) | 🔴 Closed (duplicate of [#36876](https://github.com/backstage/backstage/pull/36876)) | 23 Nov 2026 |
| [Backstage](https://github.com/backstage/backstage) (Spotify) | [#37097 - catalog: use presentation API for CatalogTable name and title columns](https://github.com/backstage/backstage/pull/37097) | 🟡 In review | 23 Nov 2026 |
| [Apicurio Registry](https://github.com/Apicurio/apicurio-registry) (CNCF) | [#11418 - docs(mcp): document missing MCP server tools and fix transport comment](https://github.com/Apicurio/apicurio-registry/pull/11418) | 🟢 Approved, awaiting merge | 20 Nov 2026 |
| [Jaeger](https://github.com/jaegertracing/jaeger) (CNCF) | [#10263 - fix(memory): match trace_id and span_id filter constants case-insensitively](https://github.com/jaegertracing/jaeger/pull/10263) | 🟡 In review | 23 Nov 2026 |
| [flagd testbed](https://github.com/open-feature/flagd-testbed) (CNCF) | [#453 - feat(targeting): add single-clause if scenario](https://github.com/open-feature/flagd-testbed/pull/453) | 🟡 In review | 23 Nov 2026 |
| [Backstage](https://github.com/backstage/backstage) (Spotify) | [#37103 - catalog: use presentation API for EntityLayout header title](https://github.com/backstage/backstage/pull/37103) | 🟡 In review | 23 Nov 2026 |
| [Backstage](https://github.com/backstage/backstage) (Spotify) | [#37104 - home: use presentation API for the WelcomeTitle display name](https://github.com/backstage/backstage/pull/37104) | 🟡 In review | 23 Nov 2026 |
| [Backstage](https://github.com/backstage/backstage) (Spotify) | [#37112 - cli-module-lint: resolve eslint and globby for repo lint workers from the module](https://github.com/backstage/backstage/pull/37112) | 🟡 In review | 24 Nov 2026 |
| [Grafana](https://github.com/grafana/grafana) (Grafana Labs) | [#138730 - Alerting: clean up state of rules deleted before the scheduler’s first tick](https://github.com/grafana/grafana/pull/138730) | 🟡 In review | 24 Nov 2026 |
| [Grafana](https://github.com/grafana/grafana) (Grafana Labs) | [#138737 - Alerting: retry file provisioning on optimistic-lock conflicts](https://github.com/grafana/grafana/pull/138737) | 🟡 In review | 24 Nov 2026 |
| [Grafana](https://github.com/grafana/grafana) (Grafana Labs) | [#138752 - Live: start datasource streams only after the subscribe reply is sent](https://github.com/grafana/grafana/pull/138752) | 🟡 In review | 24 Nov 2026 |
| [Kyverno Policies](https://github.com/kyverno/policies) (CNCF) | [#1758 - fix(other-vpol/check-nvidia-gpu): check image exemptions against exceptions.allowedImages](https://github.com/kyverno/policies/pull/1758) | 🟢 Approved, awaiting merge | 23 Nov 2026 |
| [Kyverno Policies](https://github.com/kyverno/policies) (CNCF) | [#1759 - fix(other-vpol/block-large-images): check image exemptions against exceptions.allowedImages](https://github.com/kyverno/policies/pull/1759) | 🟢 Approved, awaiting merge | 23 Nov 2026 |

## Details

### Backstage #37096
Fixes [#32785](https://github.com/backstage/backstage/issues/32785). The `gitlab:group:ensureExists` scaffolder action failed when the owner path is a GitLab user namespace, because the Groups API returns 404 for user namespaces and the action then tried to create a group at an existing path. The fix resolves the first path segment through the Namespaces API: an existing user namespace is reused, and requesting subgroups under a user namespace fails with a clear error. Includes 4 new regression tests and a changeset. Closed unmerged on 23 Nov 2026: [#36876](https://github.com/backstage/backstage/pull/36876) already covered the same fix and was ahead in review.

### Backstage #37097
Part of [#20955](https://github.com/backstage/backstage/issues/20955). Threads the entity presentation API through `CatalogTable`'s default columns and uses it for the title column's sort, search and rendering, so entity titles stay consistent across Backstage. Includes a changeset and new unit tests for the column factories.

### Apicurio Registry #11418
Fixes [#11346](https://github.com/Apicurio/apicurio-registry/issues/11346). Documents the MCP server tools that were missing from the docs and fixes a transport comment. DCO sign-off and SonarCloud pass; approved by a maintainer, waiting for merge.

### Grafana #138730
Fixes [#138611](https://github.com/grafana/grafana/issues/138611). A rule deleted between state-cache warmup and the scheduler's first tick kept its alert state forever; the first tick now removes cache entries for rules that no longer exist, with resolved notifications via the normal deleted-rule path. Unit test included.

### Grafana #138737
Fixes [#138729](https://github.com/grafana/grafana/issues/138729). Concurrent file-provisioning reloads on HA replicas could hit an optimistic-lock version conflict and fail the whole reload with a 500. The provisioner now retries rule operations up to 3 times on `ErrOptimisticLock`, re-fetching the rule for a fresh version each attempt, with 3 new tests.

### Grafana #138752
Fixes [#138739](https://github.com/grafana/grafana/issues/138739). A datasource stream could publish its whole result before the client’s subscription completed; those publications are dropped and the search list loads forever. The stream now starts only after the subscribe reply is written, via centrifuge’s `SubscriptionReady`. Includes 2 new dispatcher tests.

### Backstage #37112
Part of [#37107](https://github.com/backstage/backstage/issues/37107). `repo lint` workers are eval'd `Worker` threads whose `require` resolves from the current directory, so they failed with strict `node_modules` layouts like pnpm's isolated linker. The parent now resolves `eslint` and `globby` via `require.resolve` and passes the paths to the worker. Split with the issue author, who keeps the `eslint-factory` part.

### Backstage #37104
Part of [#20955](https://github.com/backstage/backstage/issues/20955). `WelcomeTitle` now renders the signed-in user's name through `EntityDisplayName` for their entity ref instead of the raw identity profile display name, so the greeting matches the rest of Backstage. Changeset and presentation-API test included.

### Backstage #37103
Part of [#20955](https://github.com/backstage/backstage/issues/20955). `EntityLayout`'s header/document title now resolves through the catalog presentation API instead of raw `metadata.title`/`name`, keeping it consistent with the rest of Backstage. Includes a changeset and a test with a mocked presentation API.

### flagd testbed #453
Adds a single-clause `if` targeting scenario to the flagd end-to-end testbed, extending targeting coverage.

### Kyverno Policies #1758 and #1759
Fix the `check-nvidia-gpu` and `block-large-images` validating policies to check image exemptions against `exceptions.allowedImages`, so exempted images are not wrongly blocked. Both approved by a reviewer, waiting on maintainer merge.

### Jaeger #10263
Fixes [#10224](https://github.com/jaegertracing/jaeger/issues/10224). The in-memory storage backend ignored uppercase trace/span IDs; the fix matches the filter constants case-insensitively.
