# Contributing to Sana Labo repositories

This guide applies to every repository in the Sana-Labo organization that does
not have its own `CONTRIBUTING.md`. A repository's own guide takes precedence.

## Protected branches

The default branch, `main`, and `develop` are protected in every active
repository:

- Changes land only through pull requests. Direct pushes are rejected.
- Force pushes are blocked.
- The branches cannot be deleted.
- Some repositories also require status checks to pass before merging.

These rules apply to everyone, including organization owners. Ruleset bypass is
reserved for emergencies and is not used for normal merges.

## How you contribute depends on your repository role

| Role | How you work | Who merges |
| --- | --- | --- |
| Write, Maintain, Admin | Create a branch in the repository and open a pull request | You can merge your own pull request once required checks pass |
| Read, Triage, Moderate | Fork the repository, push to your fork, and open a pull request from the fork | A member with write access reviews and merges it |

Maintain and Admin do not add merge rights beyond Write. They add repository
settings and administration.

### Working from a fork

1. Fork the repository to your personal account.
2. Create a branch in your fork and push your changes there.
3. Open a pull request against the upstream repository.
4. A member with write access approves the workflow run (see below), reviews
   the change, and merges it.

Forks of private repositories stay private and are tied to your access. If your
access to the upstream repository is removed, your fork is deleted. Get your
work merged or saved locally before your access ends.

## Pull requests

- Keep each pull request to one purpose that can be reviewed and reverted on its
  own.
- Describe what changed, why, and how you verified it.
- Keep your branch up to date with the target branch before asking for a merge.
- Do not commit secrets, credentials, or personal data. If you push one by
  mistake, tell a repository maintainer immediately so it can be rotated.

## CI for pull requests from forks

Workflows on pull requests from forks do not start automatically. A member with
write access must approve the run after reviewing the change. Reviewers should
pay particular attention to changes under `.github/workflows/`.

Approved runs use a read-only `GITHUB_TOKEN` and receive no repository secrets.
Checks that need secrets run after the change is merged.

## Writing workflows

A pull request from a fork runs the workflow files as changed in that pull
request. Write workflows so that this cannot reach trusted infrastructure:

- Every job that runs on a self-hosted runner must skip pull requests from
  forks. Add this condition to the job:

  ```yaml
  jobs:
    build:
      runs-on: [self-hosted, linux]
      if: >-
        github.event_name != 'pull_request' ||
        github.event.pull_request.head.repo.full_name == github.repository
  ```

- Deployment jobs run only on pushes to protected branches or on manual
  dispatch, never on `pull_request` events.
- Do not use `pull_request_target` or `workflow_run` to check out or run code
  from a pull request.

## Reporting security issues

Do not open a public issue for a security problem. Report it privately to:

- Lim Jeong Un — <jeongun.lim.001@sanalabo.com>
