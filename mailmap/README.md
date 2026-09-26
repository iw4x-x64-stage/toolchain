# mailmap - Contributor identity mapping for IW4x projects.

`mailmap` maintains the `.mailmap` file of IW4x repositories, which maps the
names and addresses a contributor has committed under to one preferred
identity. This version provides the command line only. The mapping itself is
not implemented yet.

## Usage

`mailmap` requires bash 4.3 or later. To build and install it with `bpkg`:

```
bpkg create -d mailmap-host --
bpkg build -d mailmap-host \
  mailmap@https://github.com/iw4x-x64-stage/toolchain.git#main
bpkg install -d mailmap-host \
  config.install.root=/usr/local config.install.sudo=sudo mailmap
```

Then run `mailmap --help` for the command line.
