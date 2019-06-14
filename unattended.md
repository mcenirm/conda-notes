# Other approaches

* https://github.com/david-rc-dayton/portable-anaconda Converts exe installer into zip file containing extracted files (minus package metadata and compiled python files).


# Official documentation

https://docs.anaconda.com/anaconda/install/silent-mode/#installing-in-silent-mode

* `/InstallationType=[JustMe|AllUsers]` - Default is `JustMe`.
* `/AddToPath=[0|1]` - Default is `1`
* `/RegisterPython=[0|1]` - Make this the system’s default Python. `0` indicates `JustMe`, which is the default. `1` indicates `AllUsers`.
* `/S` - Install in silent mode.
* `/D=<installation path>` - Destination installation path. Must be the last argument. Do not wrap in quotation marks. Required if you use `/S`.


# Examples

## Install Miniconda2 in work area

```cmd
start /wait "" %cd%\Miniconda2-4.6.14-Windows-x86_64.exe /InstallationType=JustMe /AddToPath=0 /S /D=%cd%\mc2
```

Unfortunately, this also places shortcuts under `%AppData%\Microsoft\Windows\Start Menu\Programs\Anaconda2 (64-bit)`.

* `Anaconda Prompt`
    ```cmd
    %windir%\System32\cmd.exe "/K" «workarea»\mc2\Scripts\activate.bat «workarea»\mc2
    ```

* `Anaconda Powershell Prompt`
    ```cmd
    %windir%\System32\WindowsPowerShell\v1.0\powershell.exe -ExecutionPolicy ByPass -NoExit -Command "& '«workarea»\mc2\shell\condabin\conda-hook.ps1' ; conda activate '«workarea»\mc2' "
    ```
