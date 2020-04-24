# Developers Document

## How-to-Build

### Visual Studio or Build Tools 2017+

Use `Developer Command Prompt for Visual Studio` or run these in the Windows Command Prompt
```cmd
:: initialize x64 build environment
CALL "%ProgramFiles(x86)%\\Microsoft Visual Studio\\2017\\Community\\VC\\Auxiliary\\Build\\vcvarsall.bat" x64
```

To compile Launcher.exe
```cmd
cl /nologo /O2 /W4 /WX /Ob2 /Oi /Oy /Gs- /GF /Gy /Tc main.c /Fe:Launcher.exe Advapi32.lib Shell32.lib shlwapi.lib
```

Optionally, to add an icon to the exe, create and link a resource with
```cmd
SET YourDistroName=Fedora

:: create resources
rc /nologo res\%YourDistroName%\res.rc

:: compile to %YourDistroName%.exe
cl /nologo /O2 /W4 /WX /Ob2 /Oi /Oy /Gs- /GF /Gy /Tc main.c /Fe:%YourDistroName%.exe ^
  Advapi32.lib Shell32.lib shlwapi.lib res\%YourDistroName%\res.res
```

### MinGW
This software can be built using MingW on either Windows (MSYS2) or GNU/Linux.
In MSYS2, you'll need to use the "MingW" variant of the terminal, or prepend
``/mingw64`` to ``$PATH`` yourself.

```bash
$ pacman -S mingw-w64-x86_64-gcc
$ make Launcher.exe
```

To build the launcher with an embedded icon, use eg.
```bash
$ make Fedora.exe
```

See the ``res`` directory for details.
