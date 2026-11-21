# Protected branches

This page describes the branch rules that the Sana-Labo organization applies to
every active repository.

The default branch, `main`, and `develop` accept changes only through pull
requests. Force pushes and branch deletion are blocked for everyone, including
organization owners. Some repositories also require status checks to pass
before merging.

Anyone with Write access or higher can merge a pull request that meets these
rules.

Only organization owners can bypass the organization's branch rules, and only
through a pull request. In an emergency, such as an urgent fix while a required
check is broken, an owner can merge a pull request that does not meet the
requirements, and GitHub records the bypass. Owners still cannot push directly
to these branches. Bypass is not used to merge routine work.

For how to open and merge pull requests in each role, see the
[contributing guide](../CONTRIBUTING.md#protected-branches).
