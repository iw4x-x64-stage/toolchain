# authors - Contributor list generation for IW4x projects.

`authors` generates the `AUTHORS` file of a git repository from the identity
register that `mailmap` uses. Every author and `Co-authored-by` identity in
the history is attributed to its person, and `AUTHORS` lists each person
once, by their preferred name, in alphabetical order. `authors` fails if the
register does not account for an identity.

## Usage

`authors` requires bash 4.3 or later and a C++ compiler to build. To build
and install it with `bpkg`:

```
bpkg create -d authors-host cc config.cxx=g++ config.bin.lib=static
bpkg build -d authors-host \
  authors@https://github.com/iw4x-x64-stage/toolchain.git#main
bpkg install -d authors-host \
  config.install.root=/usr/local config.install.sudo=sudo authors
```

The static libraries make the installed `authors` depend on no shared library
outside the system.

The identity register is a manifest list with one manifest per person. The
`authors` value says how the person is listed: by name (the default), by
name and email, or not at all:

```
: 1
name: Jane Doe
email: jane@example.org
alias: J. Doe <jane@old.example.org>
authors: email
:
name: Build Bot
email: bot@example.org
authors: none
```

To update and commit the `AUTHORS` of the repository in the current
directory, showing the changes and asking for confirmation first:

```
authors identities
```

`AUTHORS` only grows. The people it already lists stay listed even if the
history does not carry them, which keeps the credit of a predecessor
repository. They are rewritten the way the register lists them now, and a
person is removed only with `authors: none`.

The options are the same as those of `mailmap`. To only update the file,
pass `--no-commit`. To see what would be done without doing anything, pass
`--print-only`. To also push the commit, pass `--push`, and to update every
repository under a directory, pass `--all`:

```
authors --all --push identities repositories/
```

The comments at the beginning of the `authors` script describe the register
values and the options.
