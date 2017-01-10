Faster git-fat for cygwin

= Usage = 

Copy all files (git-fat.{exe,py,pyc}) somewhere where your cygwin shell finds it ($PATH).

It runs only on cygwin (choose platform!). 
Msys requires other binaries are needed.

= How it works ? = 

git-fat.exe is an simplified "python" executor which i
executes python file directly via CPython C API.
It takes it's executable PATH c:/tools/git-fat.exe and searches for
 - c:/tools/git-fat.pyc
 - c:/tools/git-fat.py
and executes the first that is found.
   
There is no synchronization and/or automatic compilation .py -> .pyc.
If you change .py, then either remove .pyc or recompile.pyc:

    $ python -m compileall git-fat.py

= Changes = 

v0.2 2015-02-11:
   - fixed minor bugs
   - readme is shown if 'git-fat.{py,pyc}' file is missing
   - cygwin64 & cygwin32 binaries provided

v0.1s 2015-02-03:
   - same, but with sources

v0.1 2015-02-03:
   - initial version
   - git-fat.exe starts git-fat.pyc or git-fat.py
   - git-fat.py improvements:
       - don't start 2 git subprocesses on startup (GitFat constructor)
       - when doing checkout, pass 100 files to git checkout-index
   - gives 2-3x performance speedup in some cases (git-fat initial pull, checkout etc ...)

= Source =

Sources (git-repos are here:)
 - Patched git-fat: src/git-fat-zbigg 
 - win-py-spawner: src/win-py-spawner

= jenkins = 

For now, to test how it behaves on jenkins, use:

rem Git-Fat optimization hack
set PATH=d:\zzg_takietam\git-fat-cygwin;%PATH%
bash -c "which git-fat"
