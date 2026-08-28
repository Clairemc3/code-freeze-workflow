# Code Freeze Workflow Demo

This demo project shows one way to run an annual code freeze gate for `main` using GitHub Actions.

## Goal

For about one month each year, pull requests to `main` are blocked by default.

During the freeze window, a maintainer must explicitly add an agreement label to allow merge.

## How It Works

1. A workflow runs on pull requests targeting `main`.
2. The workflow checks whether today's date is inside the configured freeze window.
3. If there is no active freeze window, the check passes.
4. If there is an active freeze window and the PR is missing the label, the check fails.
5. A maintainer can unblock by adding the required label to the PR.

In this demo, the required label is:

- `freeze-exception-approved`

## Files

- `.github/freeze-policy.json`: annual freeze dates and approval rules.
- `.github/workflows/code-freeze-gate.yml`: workflow that enforces the freeze rule.
- `.github/pull_request_template.md`: reminder checklist for PR authors.

## Branch Protection

Require the `Code Freeze Gate` check before merging to `main`.

Note: this workflow is intentionally triggered by `pull_request`, so workflow updates can be tested from the incoming PR branch.

## Example Freeze Window

The sample policy is configured for:

- Start: `12-01`
- End: `12-31`

You can update these values to any annual window.
