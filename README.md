# SourceMod Socket Extension
This has been forked from [sfPlayer's origin Git repository][socket-git].
Get to the [AlliedModders forum thread][socket-am] for more information.

[socket-git]: http://player.to/gitweb/index.cgi?p=sm-ext-socket.git
[socket-am]: https://forums.alliedmods.net/showthread.php?t=67640

## Building with AMBuild

### Dependencies
- [SourceMod][] toolchain (follow the instructions on [Building SourceMod][] to set up your
environment, if you haven't already)
- [Boost][]

[SourceMod]: https://github.com/alliedmodders/sourcemod/
[Building SourceMod]: https://wiki.alliedmods.net/Building_SourceMod
[Boost]: http://www.boost.org/

### Configuration

1. Configure Boost.
  - Download the release archive from the site and extract the archive to a location
  `${BOOST_PATH}`.  Set that location as your working directory.
  - Run the `bootstrap` script for your platform to build `b2`.  Pass `--with-toolset` with
  either `msvc`, `gcc`, or `clang` depending on what compiler you plan on building with.
  - Invoke `b2 define=BOOST_TYPE_INDEX_FORCE_NO_RTTI_COMPATIBILITY address-model=32 runtime-link=static link=static --build-dir=build/x86 --stagedir=stage/x86 --with-thread --with-date_time --with-regex`
  to build the required libraries in mixed RTTI mode (boost will use RTTI, the extension will
  not).  The configuration should build fully static x86 libraries on both Withdows and Linux,
  with versioned filenames on the former and system names on the latter (which allows us to use
  `-lboost_*` without additional extensions when setting up the link flags on `ambuild`).
    - If an existing build is present with a different configuration, use `-a` to force
    rebuilding the libraries.
2. `cd build/` and run `../configure.py --sm-path ${SM_PATH} --boost-path ${BOOST_PATH}`
3. `ambuild` as normal.
