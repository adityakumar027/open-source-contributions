# Open Source Contributions

Live tracker of my open source pull requests across major projects. Updated as PRs move through review.

## 📊 Stats

| Opened | In review | Approved | Merged |
| :---: | :---: | :---: | :---: |
| 3 | 1 | 1 | 0 |

## 🔀 Pull Requests

| Project | Pull Request | Status | Opened |
| :--- | :--- | :--- | :--- |
| [Backstage](https://github.com/backstage/backstage) (Spotify) | [#37096 - gitlab:group:ensureExists: support GitLab user namespaces](https://github.com/backstage/backstage/pull/37096) | 🔴 Closed (duplicate of [#36876](https://github.com/backstage/backstage/pull/36876)) | 23 Nov 2026 |
| [Apicurio Registry](https://github.com/Apicurio/apicurio-registry) (CNCF) | [#11418 - docs(mcp): document missing MCP server tools and fix transport comment](https://github.com/Apicurio/apicurio-registry/pull/11418) | 🟢 Approved, awaiting merge | 20 Nov 2026 |
| [Jaeger](https://github.com/jaegertracing/jaeger) (CNCF) | [#10263 - fix(memory): match trace_id and span_id filter constants case-insensitively](https://github.com/jaegertracing/jaeger/pull/10263) | 🟡 In review | 23 Nov 2026 |

## Details

### Backstage #37096
Fixes [#32785](https://github.com/backstage/backstage/issues/32785). The `gitlab:group:ensureExists` scaffolder action failed when the owner path is a GitLab user namespace, because the Groups API returns 404 for user namespaces and the action then tried to create a group at an existing path. The fix resolves the first path segment through the Namespaces API: an existing user namespace is reused, and requesting subgroups under a user namespace fails with a clear error. Includes 4 new regression tests and a changeset. Closed unmerged on 23 Nov 2026: [#36876](https://github.com/backstage/backstage/pull/36876) already covered the same fix and was ahead in review.

### Apicurio Registry #11418
Fixes [#11346](https://github.com/Apicurio/apicurio-registry/issues/11346). Documents the MCP server tools that were missing from the docs and fixes a transport comment. DCO sign-off and SonarCloud pass; approved by a maintainer, waiting for merge.

### Jaeger #10263
Fixes [#10224](https://github.com/jaegertracing/jaeger/issues/10224). The in-memory storage backend ignored uppercase trace/span IDs; the fix matches the filter constants case-insensitively.
