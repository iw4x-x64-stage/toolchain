# toolchain - Repository maintenance tools for IW4x projects.

`toolchain` is a collection of tools for maintaining the repositories of the
IW4x organization. Each tool derives one part of a repository, such as its
`.mailmap` or `AUTHORS` file, from a single source and keeps it up to date
across every repository at once.

## Usage

Each tool is a separate package with its own `README.md` in the package
directory, which describes how to install and run it:

- [`mailmap`](mailmap/README.md): Contributor identity mapping for IW4x projects.
- [`authors`](authors/README.md): Contributor list generation for IW4x projects.
- [`headers`](headers/README.md): Source header maintenance for IW4x projects.
- [`ignorerevs`](ignorerevs/README.md): Formatting commit tracking for IW4x projects.

## Development

The tools are written in bash and require bash 4.3 or later, git, the
`build2` toolchain 0.18.0 or later, and a C++ compiler, which builds the
`libbutl.bash` support programs the tools use. The development setup uses the
standard `bdep`-based workflow. For example:

```
git clone https://github.com/iw4x-x64-stage/toolchain.git
cd toolchain

bdep init -C @gcc cc config.cxx=g++
bdep update
bdep test
```

On Windows, the bash that Git for Windows installs meets this requirement.

## Contributing

Report problems and propose changes through this repository's issues and
pull requests. Pull requests target `main`.

## License

toolchain is licensed under the GNU General Public License, version 3,
subject to the additional permissions described in version 1.1 of the IW4x
Linking Exception.

See LICENSE.md, LICENSE-EXCEPTION.md, and AUTHORS.
