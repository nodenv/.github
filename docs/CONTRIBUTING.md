<!--
This is a default contributing guide that applies to the entire nodenv organization.
It may be overridden by a repo-specific contributing guide.
https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file
-->

# Contributing

## Releasing

From a clean working copy, run `npm version major|minor|patch|VERSION`.
This will bump the package version, commit, tag, and push.
The tag-push event triggers the release workflow on GitHub.
