# headers - Source header maintenance for IW4x projects.

`headers` adds the SPDX header to the source files of a git repository, which
names the copyright holder and the license of each file:

```
// Copyright (c) the IW4x authors (see the AUTHORS file).
// SPDX-License-Identifier: GPL-3.0-only WITH AdditionRef-IW4x-Exception-1.1
```

The header is written in the comment syntax of each file type and the
license expression comes from the `license` value of the repository manifest.
`headers` fails if a file is of a type it does not know, if a file already
carries a notice of its own, or if a header is incomplete or names another
license.

## Usage

`headers` requires bash 4.3 or later and a C++ compiler to build. To build
and install it with `bpkg`:

```
bpkg create -d headers-host cc config.cxx=g++ config.bin.lib=static
bpkg build -d headers-host \
  headers@https://github.com/iw4x-x64-stage/toolchain.git#main
bpkg install -d headers-host \
  config.install.root=/usr/local config.install.sudo=sudo headers
```

The static libraries make the installed `headers` depend on no shared library
outside the system.

To add the header to the source files of the repository in the current
directory, showing the files and asking for confirmation first:

```
headers
```

Third-party and generated files are excluded with the `spdx` attribute unset
in `.gitattributes`, for example:

```
deps/** -spdx
```

A file whose leading comment already mentions a copyright or license is never
changed. It is listed for review and either excluded or given the header by
hand, next to its notice. For a repository without a manifest, pass the
license expression with `--license`.

The other options are the same as those of `mailmap` and `authors`. To only
change the files, pass `--no-commit`. To see what would be done without doing
anything, pass `--print-only`. To also push the commit, pass `--push`, and to
update every repository under a directory, pass `--all`.

The comments at the beginning of the `headers` script describe the file
types, the placement of the header, and the options.
