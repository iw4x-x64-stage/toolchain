# ignorerevs - Formatting commit tracking for IW4x projects.

`ignorerevs` maintains the `.git-blame-ignore-revs` file of IW4x repositories,
which lists the commits that `git blame` skips since they only change
formatting. This version provides the command line only. The file maintenance
itself is not implemented yet.

## Usage

`ignorerevs` requires bash 4.3 or later. To build and install it with `bpkg`:

```
bpkg create -d ignorerevs-host --
bpkg build -d ignorerevs-host \
  ignorerevs@https://github.com/iw4x-x64-stage/toolchain.git#main
bpkg install -d ignorerevs-host \
  config.install.root=/usr/local config.install.sudo=sudo ignorerevs
```

Then run `ignorerevs --help` for the command line.
