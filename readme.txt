
TIL2 - Tray Icon Launcher
---------------------------

    Launches executables and provides the minimize-to-tray functionality.
    Meant to be run from batch scripts or from the command prompt.
    If no command line program provided, attempts to start a hard-coded
    execuatable with the following name: "run_me_no_parameters.exe".
    This is for hex editing (NB. this may've been hexed alrady).

    Using '-C1' option may be used to instruct the CMD
    to create its own, new command prompt.

    https://github.com/ike9000e/tray-icon-launcher

    Build: 2023-11-04, 64-bit

Features
-----------
    * Tray-minimizes window the command creates.
    * Tray-minimizes the CMD console. Has options to search
      for CMD in the parent or child process list.
    * Can attach a DLL library to the starting process.
    * Shows icon in the system tray.
    * Handles Ctrl+C and auto unhides the window.


Usage
-------
    program.exe [OPTIONS] -- {COMMAND}

OPTIONS
---------
    -T1 - Move to the tray: first CMD window from the parent process list.
    -T2 - Move to the tray: first CMD window from the child process list.
    -T3 - Move to the tray: window that the command creates.

    -W1 - Wait for the command to finish. The default.
    -W0 - Don't wait for the command to finish.

    -DL FILE
        - Provide a DLL file that is attached|injected to
          the created process.

    -C1 - Instruct CLI program that it should recieve its
          own, new console window. Eg. if the command is CMD,
          it starts with the new command prompt.
    -TI - Move the window (or command prompt) to the
          tray, initially.

    -WI MILLISECS
        Interval of how long to wait, in milliseconds, for the target process
        between re-tries, in case if not finding its window initially.
        Default: 200

    -WN NUM
        Number of times to wait using the '-WI' option.
        Default: 8

    -S1 - Don't hide the helper window that the program
          uses inernally. It's created only with
          the -T1 -T2 or -T3 option.
    -S2 - Show options being used.
    -AE1 - Setup an environment variable for further console attach functionality.
           Environment variable 'HXDW_PID_STDOUT_7LL55C3O' gets
           assigned to the PID of the current process.
           This is an internal functionality for programs created with the same library.


    Utility Mode Options
    ------------------------
        In Utility mode the program only performs specified
        operation and exits.

        --u_timestamp
            Returns POSIX timestamp value in seconds. Eg.: 1664630997
        --u_timestamp_ms
            Same as '--u_timestamp' but in milliseconds.
        --u_file_md5 FILE
            Calculates MD5 hash|digest for the file.
        --u_gbt3 FILE
            Get binary type.
            Returns binary type of the executable (EXE or DLL), which can be
            WIN32(x86), WIN64(x64) or Intel Itanium. Returned value to the
            shell - as the errorlevel - is either 32, 64 or 70, respectivelly.


Examples
----------
    program.exe -T2 -W1 -C1 -TI -S1   -- cmd
    program.exe -T2 -C1 -WN 8 -WI 200 -- cmd
    program.exe -T1 -W1 -C1 -TI -S1   -- calc
    program.exe -T1 -C1 -TI -S1       -- mpv.exe m.mkv
    program.exe -T3 -S1               -- notepad
    program.exe -W0                   -- notepad

