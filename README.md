ESP-IDF template app for Visual Studio Code
====================
This is a template application to be used with `Espressif IoT Development Framework`_ (ESP-IDF) in conjunction with VSCode on Windows & Linux.

VSCode works best if ``C/C++`` extension is installed and esp-idf is located inside the workspace folder otherwise specify its location in ``c_cpp_properties``.

Clang format needs to be specified in ``settings.json`` for Windows.   
For linux it just needs to be in your ``PATH`` environment variable.

Set all the environment variables in ``task.json``. Namely ``IDF_PATH``, ``PATH``, ``projectname``, ``openOCDPath``.   
Set the ``gdbpath`` to the GDB executable in ``launch.json``, and the workspace path to the elf in ``executable``.

Runable tasks by name are ``Clean``, ``Build``, ``Flash``, ``OpenOCD``, ``DumpELF``, ``Monitor``, ``Erase``

OpenOCD needs to run before starting GDB. OpenOCD will keep running until the task is terminated.

You can add a keyboard shortcut to terminate a task. By adding the following line to ``keybindings.json``
``{ "key": "shift+ctrl+c", "command": "workbench.action.tasks.terminate" },``

Debug Console will show the GDB Output.
Tasks output will show the OpenOCD Output.

My routine is:
```
    run "task Build" - (CTRL+P) then type "task build"
    Set my esp32 in upload mode.
    run "task Flash"
    run "task OpenOCD"
    reset the esp32
    start debugging
```
My first setup is:
```
    OS: arch linux x64
    esp32: Pycom LoPy
    Debugger: Olimex ARM-USB-OCD-H
```
My Second setup is:
```
    OS: Windows 10 x64
    esp32: DOIT esp32
    Debugger: Olimex ARM-USB-OCD-H
```

The folder esp-idf contains modifications I have made to ``idf_monitor.py``, an additional build target called ``log`` which requires ``idf_log.py``.

``make monitor`` will now output a log file in the ``logs/`` directory, and functions like the original.   
``make log`` also outputs a log file in ``logs/`` but does not contain a console. It pipes all output to stderr which can be read by VSCode task window.

## Windows Specific
Msys2 needs to be installed and its path to bash.exe needs to be specified.