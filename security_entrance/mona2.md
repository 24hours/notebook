# Mona2
Scipt written for Immunity Debugger, now support WinGdb as well.

## Installation Steps:
1. Install Python 2.7
2. Download the right zip package from [here](http://pykd.codeplex.com/), and extract and run `vcredist_x86.exe` and `vcredist_x64.exe`.
3. Copy `pykd.pykd` to` C:\Program Files (x86)\Windows Kits\8.0\Debuggers\x86\winext` for both architecture
4. Download `windbglib.py` and `mona.py` from [here](https://github.com/corelan/) and put them in the same directories as windbg.exe (32-bit and 64-bit versions).
5. Configure the `symbol search path` as follows:
 - File → Symbol File Path
 - `SRV*C:\windbgsymbols*http://msdl.microsoft.com/download/symbols`
 - File → Save Workspace
