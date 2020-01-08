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
  `${BOOST_PATH}`.
  - Run the `bootstrap` script for your platform to build `b2`.
  - Invoke `b2 --build-dir=build/x86 address-model=32 --build-type=complete --with-thread --with-date_time --with-regex -link=static --stagedir=stage/x86`
2. Run `configure.py --sm-path ${SM_PATH} --boost-path ${BOOST_PATH}`
