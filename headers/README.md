# headers - Source header maintenance for IW4x projects.

`headers` adds the SPDX header to the source files of IW4x repositories,
which names the copyright holder and the licence of each file. This version
provides the command line only. The header maintenance itself is not
implemented yet.

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

Then run `headers --help` for the command line.
