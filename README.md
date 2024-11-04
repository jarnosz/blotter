# blopentype
Basic LuaTeX OpenType Manager

# Description

In his terse documentation for `PiTeX`, Paul Isambert lists, among the "mandatory PiTeX" files, the following:

| file name            | Description  |
|-|-|
| fonts.ptx            | Interface for fonts; relies on the next file.    |
| fonts.ptxlua         | The Lua fontloader; should become independant some day. |
| foundry-settings.lua | Default settings for the fontloader.             |

Well: the day has come, and the fontloader has now become `blopentype`: a *Basic LuaTeX OpenType Manager*.

The basic code is copied almost verbatim from Isambert's `PiTeX`, save the adoption of the canonical filename extensions `tex` for *LuaTeX macros*, `lua` for *LuaTeX scripts*, and `blot-sets.lua` for the basic basic settings. 
The required dependencies are Isambert packages [texapi](https://ctan.org/pkg/texapi), [YaX](https://ctan.org/pkg/yax) and [Gates](https://ctan.org/pkg/gates), as stated in `DEPENDS.txt`.

You may find an example of usage in the `blottest.[tex|pdf]` files, and some basic documentation in `blopentype.md`.

# Bugs and caveats

On LuaTeX <0.17 a security hole allowed the package to write on `$TEXMFLOCAL`, so the program actually worked almost by accident. Now the hole is plugged, so the package must be run with the `--shell-escape` flag enabled, otherwise it will not write the fontname `readable.txt` database, or the individual `*.lua` font metrics. This procedure is only required to regenerate the database or to add new font metrics on the system; once these files are in the `blotfonts` directory in `$TEXMFLOCAL` the flag is no longer required.

This update on the LuaTeX engine now requires then a font database generating/updating script, which is top in the to do list now. Meanwhile, the workaround described should work.

The macros are still barely documented, and massively keep the names of their parent (`PiTeX`) package; that may be fixed some day.

The font database is stored at `$TEXMFLOCAL/texmf/luatex/blotfonts/readable.txt`.
It is updated automatically after installing *and using* new fonts, but you may edit it, or else delete/rename(backup) the database by hand, and rerun LuaTeX to rebuild it.

The character table for each typeface is stored in the `luatex/blotfonts` directory as a flat `lua` file; it would be nice to have it compiled as a `luac/luc` file to save some space, some day.

Good luck, and happy LuaTeXing

# Authors 

(C) 2022-2023 Paul Isambert (author) and Luis Rivera (maintainer).

LaTeX Project Public License, LPPL Version 1.3c 2008-05-04 or MIT License
