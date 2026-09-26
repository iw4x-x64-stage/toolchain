# ignorerevs - Formatting commit tracking for IW4x projects.

`ignorerevs` maintains the `.git-blame-ignore-revs` file of a git repository,
which lists the commits that `git blame` skips, attributing the lines they
touch to the commits before them. It lists every commit that only changes
whitespace (indentation, trailing whitespace, blank lines, line endings) and
keeps the commits added to the file by hand.

## Usage

`ignorerevs` requires bash 4.3 or later. To build and install it with `bpkg`:

```
bpkg create -d ignorerevs-host --
bpkg build -d ignorerevs-host \
  ignorerevs@https://github.com/iw4x-x64-stage/toolchain.git#main
bpkg install -d ignorerevs-host \
  config.install.root=/usr/local config.install.sudo=sudo ignorerevs
```

To update and commit the `.git-blame-ignore-revs` of the repository in the
current directory, showing the changes and asking for confirmation first:

```
ignorerevs
```

GitHub reads the file by default. For `git blame` to read it as well, set
`blame.ignoreRevsFile` in the repository:

```
git config blame.ignoreRevsFile .git-blame-ignore-revs
```

A commit that reformats code without only changing whitespace (for example,
one that also moves line breaks) is not detected and can be added to the
file by hand. Such commits are kept on every update.

The options are the same as those of `mailmap`. To only update the file,
pass `--no-commit`. To see what would be done without doing anything, pass
`--print-only`. To also push the commit, pass `--push`, and to update every
repository under a directory, pass `--all`.

The comments at the beginning of the `ignorerevs` script describe what
counts as a commit that only changes whitespace and the options.
