# toolchain - <SUMMARY>

`toolchain` is a <SUMMARY-OF-FUNCTIONALITY>.

This file contains setup instructions and other details that are more
appropriate for development rather than consumption. If you want to use
`toolchain` in your `build2`-based project, then instead see the accompanying
package [`README.md`](<PACKAGE>/README.md) file.

The development setup for `toolchain` uses the standard `bdep`-based workflow.
For example:

```
git clone .../toolchain.git
cd toolchain

bdep init -C @gcc cc config.cxx=g++
bdep update
bdep test
```
