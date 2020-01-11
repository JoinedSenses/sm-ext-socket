# SourceMod Socket Extension
This has been forked from [sfPlayer´s origin Git repository](http://player.to/gitweb/index.cgi?p=sm-ext-socket.git). Get to the [AlliedModders forum thread](https://forums.alliedmods.net/showthread.php?t=67640) for more information.

## Building with AMBuild

### Dependencies
- [SourceMod][] (follow the instructions on [Building SourceMod][])
- [Boost][]

[SourceMod]: https://github.com/alliedmodders/sourcemod/
[Building SourceMod]: https://wiki.alliedmods.net/Building_SourceMod
[Boost]: http://www.boost.org/

### Configuration

1. Configure Boost.
  - Download the release archive from the site and extract the archive to a location
  `${BOOST_PATH}`.  Set that location as your working directory.
  - Run the `bootstrap` script for your platform to build `b2`.
  - Invoke `b2 define=BOOST_TYPE_INDEX_FORCE_NO_RTTI_COMPATIBILITY address-model=32 link=static --build-dir=build/x86 --build-type=complete --stagedir=stage/x86 --with-thread --with-date_time --with-regex`
  to build the required libraries in mixed RTTI mode (boost will use RTTI, the extension will
  not).
    - If an existing build is present with a different configuration, use `-a` to force
    rebuilding the libraries.
2. `cd build/` and run `../configure.py --sm-path ${SM_PATH} --boost-path ${BOOST_PATH}`
3. `ambuild` as normal.
