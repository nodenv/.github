# Contributing

## PR Tests

The test workflow in this repository is rather convoluted,
because it is simultaneously the reusable workflow that is called via `workflow_call`,
while also running most of those same tests within this repository itself.
(That is why [test.yml][] has so many `on` triggers.)

## Releasing

1. [Draft a new release](https://github.com/nodenv/.github/releases/new)
2. Decide on next tag based on SemVer
3. Generate release notes (button)
4. Publish

Once the tag is created by the release,
it will kick off the [tag-major.yml][] workflow
which will bump the vN ref for downstream users to pin to.

[test.yml]: https://github.com/nodenv/.github/blob/main/.github/workflows/test.yml
[tag-major.yml]: https://github.com/nodenv/.github/blob/main/.github/workflows/tag-major.yml
