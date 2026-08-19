<!-- markdownlint-disable -->

# Hardening Report: threeal--setup-yarn-action/v2.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **threeal--setup-yarn-action/v2.0.0** was hardened automatically. 4 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Workflow file uses action references pinned to mutable tags or branches instead of immutable full-length commit SHAs. Failing references:
- `actions/checkout@v4.1.1` (tag)
- `actions/setup-node@v4.0.2` (tag)
- `threeal/setup-yarn-action@main` (branch)

Locations:

- `.github/workflows/build.yaml:12`
- `.github/workflows/build.yaml:16`
- `.github/workflows/build.yaml:20`

### unpinned-uses (severity: high)

Workflow file uses action references pinned to mutable tags or branches instead of immutable full-length commit SHAs. Failing references:
- `actions/checkout@v4.1.1` (tag, used multiple times)
- `actions/setup-node@v4.0.2` (tag, used multiple times)
- `threeal/setup-yarn-action@main` (branch)
- `threeal/setup-yarn-action@v1.0.0` (tag)

Locations:

- `.github/workflows/test.yaml:12`
- `.github/workflows/test.yaml:16`
- `.github/workflows/test.yaml:20`
- `.github/workflows/test.yaml:33`
- `.github/workflows/test.yaml:37`
- `.github/workflows/test.yaml:41`

### missing-permissions (severity: medium)

Workflow file has no top-level `permissions:` key and no job-level `permissions:` key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially write) permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/build.yaml:1`

### missing-permissions (severity: medium)

Workflow file has no top-level `permissions:` key and no job-level `permissions:` key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially write) permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/test.yaml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all 4 findings across both workflow files:

**build.yaml:**
- Added `permissions: {}` at the top level to enforce least privilege
- Pinned `actions/checkout@v4.1.1` → `@b4ffde65f46336ab88eb53be808477a3936bae11 # v4.1.1`
- Pinned `actions/setup-node@v4.0.2` → `@60edb5dd545a775178f52524783378180af0d1f8 # v4.0.2`
- Pinned `threeal/setup-yarn-action@main` → `@9a888f5a12e9edf0527f392ee6dc86409248f642 # main`

**test.yaml:**
- Added `permissions: {}` at the top level to enforce least privilege
- Pinned `actions/checkout@v4.1.1` → `@b4ffde65f46336ab88eb53be808477a3936bae11 # v4.1.1` (all occurrences)
- Pinned `actions/setup-node@v4.0.2` → `@60edb5dd545a775178f52524783378180af0d1f8 # v4.0.2` (all occurrences)
- Pinned `threeal/setup-yarn-action@main` → `@9a888f5a12e9edf0527f392ee6dc86409248f642 # main`
- Pinned `threeal/setup-yarn-action@v1.0.0` → `@862ec12b0121a37ad21e06a21bbe3b5ad259a829 # v1.0.0`

Local action references (`uses: ./setup-yarn-action`) were left unchanged as they are not mutable remote references.

