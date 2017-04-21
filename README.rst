ESP-IDF template app for Visual Studio Code
====================

This is a template application to be used with `Espressif IoT Development Framework`_ (ESP-IDF). 

Set all the environment variables in Task.json 

::
    "options": {
        "cwd": "${workspaceRoot}",
        "env": {
            "IDF_PATH": "/home/fhfs/ESP/esp-idf",
            "PATH": "${env.PATH}:/home/fhfs/ESP/xtensa-esp32-elf/bin",
            "projectname": "app-template",
            "openOCDPath": "/home/fhfs/ESP/openocd-esp32",
            "XtensaEsp32ELFBinPath": "/home/fhfs/ESP/xtensa-esp32-elf/bin"
        }
    },
::