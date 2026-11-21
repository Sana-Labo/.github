# CI and runners

This page describes how the Sana-Labo organization runs GitHub Actions safely.

## Pull requests from forks

Workflow runs on pull requests from forks wait for approval from a member with
Write access or higher, and each new push needs another approval. Approved runs
get a read-only token and no secrets. See
[CI for pull requests from forks](../CONTRIBUTING.md#ci-for-pull-requests-from-forks).

## Self-hosted runners

Jobs on self-hosted runners must skip pull requests from forks. The condition to
add is described in
[Writing workflows](../CONTRIBUTING.md#writing-workflows).

Self-hosted runners must meet these conditions:

- Each job runs in a clean, single-use environment.
- Network access is limited to what the job needs.
- Runner images do not contain secrets.

## Deployments

Deployments use a separate runner group from other CI jobs, and run only from
protected branches.

## Secrets

Keep secrets out of repositories. If a secret is exposed, report it to a
repository maintainer so it can be rotated.
