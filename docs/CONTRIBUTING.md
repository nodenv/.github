<!--
This is a default contributing guide that applies to the entire nodenv organization.
It may be overridden by a repo-specific contributing guide.
https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file
-->

# Contributing

## Rbenv Tags Git Configuration

Many repositories in the nodenv organization are forks from the rbenv
ecosystem. To support pulling changes from the upstream rbenv repository into
nodenv, it is necessary to add rbenv as a Git remote. However, this adds some
complication because (by default), Git tags for nodenv and rbenv will collide.
(ie, rbenv's `v1.0.0` tag conflicts with nodenv's `v1.0.0`) Additionally,
having rbenv's tags exist locally introduces complications to the release
process: `git push --follow-tags` would push rbenv's tags to nodenv's `origin`
remote.

The following special Git configuration avoids these and other headaches while
still allowing `origin` to be pushed using `--tags` or `--follow-tags`
options—without the risk of pushing rbenv's tags into nodenv's tagspace. The
configuration assumes nodenv's remote is `origin`, and rbenv's remote is
`rbenv`.

1. Configure rbenv to not fetch tags by default:

```console
git config remote.rbenv.tagOpt --no-tags
```

2. Fetch rbenv's tags to their own refspec namespace (`rbtags`, in this case):

```console
git config --add remote.rbenv.fetch '+refs/tags/*:refs/rbtags/*'
```

> [!WARNING]
> The `--tags` option to `fetch` et. al. will override this setting.

Resulting snippet in `.git/config`:

```gitconfig
[remote "origin"]
    url = git@github.com:nodenv/nodenv.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[remote "rbenv"]
    url = git@github.com:rbenv/rbenv.git
    fetch = +refs/heads/*:refs/remotes/rbenv/*
    fetch = +refs/tags/*:refs/rbtags/*
    tagopt = --no-tags
```

To reference rbenv's tags, use the fully qualified refspec: `refs/rbtags/vX.Y.Z`

```console
git show refs/rbtags/v1.1.2
git checkout refs/rbtags/v1.1.2
git merge refs/rbtags/v1.1.2
```

## Releasing

From a clean working copy, run `npm version major|minor|patch|VERSION`.
This will bump the package version, commit, tag, and push.

The tag-push event triggers the release workflow on GitHub, which creates a
GitHub Release for the tag. It also (when applicable) publishes to npm and
opens a pull request to bump the corresponding formula in its Homebrew tap.
