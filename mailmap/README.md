# mailmap - Contributor identity mapping for IW4x projects.

`mailmap` updates the `.mailmap` file of a git repository from an identity
register, which lists each contributor with their preferred name and email
and the other identities they committed under. Every author and
`Co-authored-by` identity in the history is mapped to the preferred identity
of its person, and `mailmap` fails if the register does not account for one.

## Usage

`mailmap` requires bash 4.3 or later and a C++ compiler to build. To build
and install it with `bpkg`:

```
bpkg create -d mailmap-host cc config.cxx=g++ config.bin.lib=static
bpkg build -d mailmap-host \
  mailmap@https://github.com/iw4x-x64-stage/toolchain.git#main
bpkg install -d mailmap-host \
  config.install.root=/usr/local config.install.sudo=sudo mailmap
```

The static libraries make the installed `mailmap` depend on no shared library
outside the system.

The identity register is a manifest list with one manifest per person:

```
: 1
name: Jane Doe
email: jane@example.org
alias: J. Doe <jane@old.example.org>
alias: <jdoe@example.com>
```

To update the `.mailmap` of the repository in the current directory, showing
the changes and asking for confirmation first:

```
mailmap identities
```

To also commit the update, with the added and removed entries listed in the
commit message:

```
mailmap --commit identities
```

To also push the commit to the upstream of the current branch:

```
mailmap --push identities
```

The branch must not be ahead of its upstream beforehand, so that the push
carries only the `.mailmap` commit.

To update every repository under a directory, for example the clones of all
the repositories of an organization, with one confirmation for all of them:

```
mailmap --all --push identities repositories/
```

All the repositories are prepared before any of them is changed, so a problem
in one leaves them all unchanged. Repositories inside another repository's
working tree, such as submodules, are not visited.

To check that it is up to date, for example in CI:

```
mailmap --check identities
```

The comments at the beginning of the `mailmap` script describe the register
rules and the options.
