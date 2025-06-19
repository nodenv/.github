# nodenv

## Reusable Workflows

This repository houses [reusable workflows][] for the [nodenv organization][].
Unfortunately, GitHub doesn't allow them to live in any other directory, so the
reusable workflows are all in the same location as the workflows _for this
repository. To distinguish them, the workflows for this repository are
prefixed with `.github_` (and they mostly call the reusable workflows
themselves).

It also contains [starter workflows][] (templates) that generate the
workflows that _call_ these reusable workflows.

## Versioning

The reusable workflows attempt to adhere to [SemVer][]
with the release tags. For convenience, each tagged release will also
advance the corresponding "major version" branch. e.g. Tagging a release
like `v2.5.0` will fast-forward the `v2` branch to the latest 2.x tag.
This way consumers of these reusable workflows may "soft-pin" to a major
version and automatically get minor and patch updates.

## Releasing

1. [Draft a new release](../../releases/new)
2. Decide on next tag based on SemVer
3. Generate release notes (button)
4. Publish

Once the tag is created by the release, it will kick off the [release.yml][]
workflow which will bump the vN ref for downstream users to pin to.

[semver]: https://semver.org
[nodenv organization]: https://github.com/nodenv
[reusable workflows]: https://docs.github.com/en/actions/using-workflows/reusing-workflows
[starter workflows]: https://docs.github.com/en/actions/using-workflows/creating-starter-workflows-for-your-organization
[release.yml]: .github/workflows/release.yml
