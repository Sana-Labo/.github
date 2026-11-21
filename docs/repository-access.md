# Repository access

This page describes how the Sana-Labo organization grants repository access.
The organization uses the repository roles that GitHub provides, as GitHub
defines them, and does not add custom roles. For what each role allows, see
GitHub's
[repository roles for an organization](https://docs.github.com/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization).
This page states when the organization grants each role.

## How access is granted

Organization membership alone gives no access to repositories. The base role
for members is set to no access, and access is granted per repository, based on
what you need to do there. Only organization owners create repositories and
grant access.

Each repository grants access in one of two ways:

- A repository whose own policy, such as its `GOVERNANCE.md`, manages access
  through teams grants access only through those teams.
- Other repositories grant access to individual members.

## When each role is granted

| Role | Granted when |
| --- | --- |
| Read | You need to view the code and propose changes that someone else reviews |
| Triage or Moderate | You also manage issues and pull requests, without pushing code |
| Write | You are trusted to merge your own work |
| Maintain | You lead the repository |
| Admin | You administer the repository. In practice, only organization owners hold Admin |

The line is drawn at Write. If your changes must be reviewed before they land,
you receive a role below Write and work from a fork. The
[contributing guide](../CONTRIBUTING.md#how-you-contribute-depends-on-your-repository-role)
describes how to work in each role.

## Project teams

Repositories that manage access through teams use three teams per project,
without a parent and child hierarchy:

| Team | Repository role | Members |
| --- | --- | --- |
| `<project>-pilots` | Maintain | People who lead development and are responsible for code review and merges |
| `<project>-co-pilots` | Write | People who support the pilots and share responsibility for review and merges |
| `<project>-contributors` | Read | Everyone else, who contributes through forks |

## Requesting access

To request access or a role change, ask an organization owner.
