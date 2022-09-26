
TIL2 - Tray Icon Launcher
---------------------------

    Launches executables and provides the minimize-to-tray functionality.
    Meant to be run from batch scripts or from command prompt.
    If no command line progream provided, starts a hard-coded
    execuatable with name 'run_me_no_parameters.exe'.
    This is for hex editing (NB. this may be hexed alrady)
    Using '-C1' option may be used to instruct the CMD
    to create its own, new console.

Features
-----------
    * Tray minimize the CMD console. Has option to search
      for CMD in the parent or child process list.
    * Tray minimize window the command creates.
    * Provide DLL and attach it to the starting process.
    * Shows icon in the system tray.
    * Handles Ctrl+C and auto unhides the window.

Usage
-------
    program.exe [OPTIONS] -- {COMMAND}

OPTIONS
---------
    -T3 - Move to the tray: window that the command creates.
    -T2 - Move to the tray: first CMD window from the
          child process list.
    -T1 - Move to the tray: first CMD window from the
          parent process list.
    -S1 - Don't hide the helper window that the program
          uses inernally. It's created only with
          the -T1 -T2 or -T3 option.
    -S2 - Show options being used.
    -W0 - Don't wait for the command to finish.
    -W1 - Wait for the command to finish. The default.
    -DL FILE
        - Provide a DLL file that is attached|injected to
          the created process.
    -C1 - Instruct CLI program that it should recieve its
          own, new console window. Eg. if the command is CMD,
          it starts with the new command prompt.
    -TI - Move the window (or command prompt) to the
          tray, initially.

Examples
----------
    program.exe -T2 -W1 -C1 -TI -S1   -- cmd
    program.exe -T2 -C1 -WN 8 -WI 200 -- cmd
    program.exe -T1 -W1 -C1 -TI -S1   -- calc
    program.exe -T1 -C1 -TI -S1       -- mpv.exe m.mkv
    program.exe -T3 -S1               -- notepad
    program.exe -W0                   -- notepad

