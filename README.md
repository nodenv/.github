# nodenv GitHub Workflows

This repository houses [reusable workflows][] for the [nodenv organization][].
It also contains [starter workflows][] (templates) for _calling_ these reusable workflows.

## Versioning

The reusable workflows attempt to adhere to [SemVer](https://semver.org) with
the release tags. For convenience, each tagged release will also advance the
corresponding "major version" branch. e.g. Tagging a release like `v2.5.0`
will fast-forward the `v2` branch to the latest 2.x tag. This way consumers of
these reusable workflows may "soft-pin" to a major version and automatically
get minor and patch updates. see [Contributing#releasing](/docs/CONTRIBUTING.md#releasing)

  [nodenv organization]: https://github.com/nodenv
  [reusable workflows]: https://docs.github.com/en/actions/using-workflows/reusing-workflows
  [starter workflows]: https://docs.github.com/en/actions/using-workflows/creating-starter-workflows-for-your-organization
