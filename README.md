# Code Freeze Workflow Demo

This demo project shows one way to enforce an annual code freeze for `main` using GitHub Actions.

## Goal

For about one month each year, merges into `main` are blocked by default.

During the freeze window, only pull requests that have been explicitly approved by the team can merge.

## How It Works

1. A workflow runs on pull requests targeting `main`.
2. The workflow checks whether today's date is inside the configured freeze window.
3. If there is no active freeze window, the check passes.
4. If there is an active freeze window, the PR must include a required approval label.

In this demo, the required label is:

- `freeze-exception-approved`

## Files

- `.github/freeze-policy.json`: annual freeze dates and approval rules.
- `.github/workflows/code-freeze-gate.yml`: workflow that enforces the rule.
- `.github/pull_request_template.md`: reminder checklist for PR authors.

## Team Agreement Model

Use GitHub permissions so only trusted maintainers can add the `freeze-exception-approved` label.
That label acts as evidence that the team agreed this change can merge during freeze.

## Suggested Branch Protection

In your repository settings, require the `Code Freeze Gate` check to pass before merging into `main`.

## Example Freeze Window

The sample policy is configured for:

- Start: `12-01`
- End: `12-31`

You can update these values to any annual window.
