# authors - Contributor list generation for IW4x projects.

`authors` generates the `AUTHORS` file of IW4x repositories, which lists
everyone who contributed to a repository once, by their preferred name. This
version provides the command line only. The generation itself is not
implemented yet.

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

Then run `authors --help` for the command line.
