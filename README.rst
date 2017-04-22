ESP-IDF template app for Visual Studio Code
====================
This is a template application to be used with `Espressif IoT Development Framework`_ (ESP-IDF) in conjunction with VSCode. 

Set all the environment variables in ``task.json``. Namely "IDF_PATH" "PATH" "projectname" "openOCDPath" 

Set the "gdbpath" to the GDB executable in ``launch.json``, and the workspace path to the elf in "executable".

Runable tasks by name are "Clean", "Build", "Flash", "OpenOCD", "DumpELF"

OpenOCD needs to run before starting GDB. OpenOCD will keep running until the task is terminated.

You can add a keyboard shortcut to terminate a task. By adding the following line to ``keybindings.json``
``{ "key": "shift+ctrl+c", "command": "workbench.action.tasks.terminate" },``

Debug Console will show the GDB Output.
Tasks output will show the OpenOCD Output.

My routine is:
.. ::
    run "task Build"
    Set my esp32 in upload mode.
    run "task Flash"
    run "task OpenOCD"
    reset the esp32
    start debugging

My devices are:
.. ::
    OS: arch linux x64
    esp32: Pycom LoPy
    Debugger: Olimex ARM-USB-OCD-H