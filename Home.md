**Welcome to the DOSBox-X Wiki!**

### Introduction

DOSBox-X is a cross-platform DOS emulator based on [[DOSBox|http://www.dosbox.com]]. Like DOSBox, it emulates a PC necessary for running many MS-DOS games and applications that simply cannot be run on modern PCs and operating systems. However, while the main focus of DOSBox is for running DOS games, DOSBox-X goes much further than this. As a fork of DOSBox, it retains compatibility with the wide base of DOS games and DOS gaming DOSBox was designed for. But it is also a platform for emulating DOS applications, including emulating the environments to run Windows 3.x, 9x and ME and software written for those versions of Windows. DOSBox-X supports multiple operating systems such as Windows, Linux and macOS (Mac OS X). Windows binaries (both 32-bit and 64-bit) are released periodically for testing. You can download them from the [[Releases|https://github.com/joncampbell123/dosbox-x/releases]] page.

### DOSBox-X's Main Focus

Apart from DOSBox's original focus on DOS games, DOSBox-X gives more focus on accurate emulation of the hardware and many more ways to tweak and configure the DOS virtual machine. We believe that a better way to emulate the legacy PC platform is to give the user all the options they need to emulate everything from original IBM PC hardware with 64KB of RAM all the way up to late 1990's hardware, whatever it takes to get that game or software package to run. Our goal is to eventually make DOSBox-X a complete emulation package that covers all pre-2000 DOS and Windows 9x based hardware scenarios, including peripherals, motherboards, CPUs, and all manner of hardware that was made for PC hardware of that time.

### What DOSBox-X Can Do
Derived from DOSBox, DOSBox-X emulates a PC complete with keyboard, mouse, joystick, sound, graphics, modem, printer, network, communication and storage devices, etc, in order to have a working DOS environment to run software designed for DOS. The vast majority of DOS (MS-DOS and PC DOS in particular) games and applications should run in DOSBox-X, although some of them may require additional configurations. DOSBox-X not only emulates a IBM PC, but also legacy systems such as PC-98. With the help of DOSBox-X, you will be able to run your favorite DOS games and programs on modern operating systems (32-bit and 64-bit) such as Microsoft Windows Vista, 7, 8, 10 and various Linux distributions. DOSBox-X also provides additional features that are useful but generally do not exist in a real DOS system, such as support for keyboard remapping and saving/loading states. With all these features it is usually very simple to make your DOS games or programs run smoothly within DOSBox-X.

### DOSBox-X's Feature Highlights
Apart from having virtually all existing features of DOSBox, DOSBox-X supports much more. Examples of DOSBox-X's unique features include:
* GUI menu bar and configuration tool  
* Built-in debugger and logging options
* Automatic drive mounting (Windows only)
* NEC PC-98 support  
* Save and load states  
* CPU optimization and Turbo mode  
* Improved customization on the title bar  
* Better compatibility with DOS applications  
* Built-in external tools such as CWSDPMI, DOSIDLE and IMGMAKE
* Support for more DOS commands (e.g. VOL, LABEL, PROMPT, and MOUSE)  
* Support for CONFIG.SYS commands (e.g. DEVICE, BUFFERS, FCBS, LASTDRIV)  
* Support for more CPU types (e.g. Pentium MMX and Pro)
* Support for ROM BIOS images
* Support for printer output  
* Support for vertical sync (V-Sync)  
* Support for Direct3D with pixel shaders (Windows only)  
* Support for OpenglHQ  
* Support for Innovation SSI-2001 emulation  
* Support for 3dfx Glide and Voodoo chip emulation
* Support for NE2000 Ethernet  
* Support for beeping  
* Support for features such as overscan border and stereo swapping  
* Various patches such as font, DBCS and Ctrl-Break patch

Note: Some features such as support for saving/loading states and running ROM BIOS images are currently experimental.

### Running and Configuring DOSBox-X

After you download DOSBox-X and extract its files, the easiest way to run DOSBox-X is to start the DOSBox-X.exe program. You will see an emulated DOS command line inside the DOSBox-X window within a few seconds. Unlike MS-DOS, where you usually see either C:\\> or A:\\> as the DOS prompt when it finishes booting, at the beginning you will get a Z:\\> when DOSBox-X loads. This is because DOSBox-X automatically creates a Virtual Internal Drive called Z: which contains various utilities that make a reasonable approximation of a fully setup DOS compatible environment. These are DOSBox-X's emulated DOS's external commands. You can check the **DOSBox-X's Supported Commands** section below for more information about them.

If you want to access other drives such as the C: drive, you have to make your directories available as drives in DOSBox-X.  There are two ways to do this:

1. Using the MOUNT command: This command allows you to mount your host drives/directories as DOSBox-X's drives. For example, in Windows "mount C D:\GAMES" (without quotes) will give you a C drive in DOSBox-X which points to your Windows D:\GAMES directory (that was created before). In Linux, "mount c /home/username" will give you a C drive in DOSBox-X which points to /home/username in Linux. To change to the drive mounted like above, type "C:". If everything went fine, DOSBox-X will display the prompt "C:\\>". To mount your CD drives in DOSBox-X you have to specify additional options. For example, you can use the command "mount D E:\ -t cdrom" to enable CD support (including MSCDEX) in Windows.

2. Auto-mount drives: If you are using Windows, DOSBox-X will ask if you want to give it access to your Windows drive when you try to go to a drive (e.g. C:), but that drive has not yet been mounted inside DOSBox-X. This basically makes DOSBox-X access to the same drives as in your Windows system. If you answer Y for Yes, then the whole Windows drive will be mounted and accessible within DOSBox-X. It is not recommended to mount your Windows Drive C: inside DOSBox-X because DOSBox-X will then be able to access all files and directories in your Windows Drive C:, and there is already a chance that something unexpected may happen in this case.

DOSBox-X features a configuration GUI which allows you to change its settings via its graphical interface. Similar to DOSBox, there is a configuration file (dosbox.conf in the current directory or in your user directory) where you can modify the DOSBox-X settings. But instead of editing this configuration file, you can change DOSBox-X settings directly within the DOSBox-X program. If DOSBox-X is not yet running, you can start this configuration GUI by using the command-line option -startui (or -startgui) of dosbox-x.exe program. On the other hand, if DOSBox-X is already running, you can do so by clicking on the "Configuration GUI" option from the "Main" menu in the DOSBox-X menu bar, or using the STARTGUI command from the DOS command line inside DOSBox-X.

For example, if you are using the MOUNT command method to mount your host drives/directories as DOSBox-X's drives, you do not have to always type these commands. Instead, you can put these commands in the "autoexec" section of the DOSBox-X configuration interface, and then save them. These correspond to the [autoexec] section of DOSBox-X's configuration file. The commands present there are run each time when DOSBox-X starts, so you can use this section for the mounting.

Even though DOSBox-X runs in a window by default, you can also change it to full-screen mode. Simply press the shortcut F11+F, and DOSBox-X will become full-screen. Alternatively, you may modify this setting in the Sdl section of the DOSBox-X configuration interface (or change the option fullscreen=false to fullscreen=true under the [sdl] section of DOSBox-X's configuration file). To get back from fullscreen mode, simply press the shortcut F11+F again.

You can try the various commands and options in order to be more familiar with the DOSBox-X interface. Once you get used to it, you should be able to do various things such as running DOS applications inside DOSBox-X. If you have questions, you can also ask the community for support.

### DOSBox-X's GUI Menus

DOSBox-X features a GUI menu bar that does not exist in DOSBox. In DOSBox-X, there are 7 menus shown in the menu bar, namely "Main", "CPU", "Video", "Sound", "DOS", "Capture" and "Drive".

**1. The "Main" menu**

* **Mapper editor**: Enters DOSBox-X's keyboard mapper editor, where you can map different keys for use with the emulated DOS. Press the Esc key three times to exit the editor.

* **Configuration GUI**: Enters the configuration GUI dialog for reviewing or changing DOSBox-X settings.

* **Send Key**: Sends special keys such as Ctrl+Esc, Alt+Tab, and Ctrl+Alt+Del to the emulated DOS system.

* **Wait on error**: Select this if you want DOSBox-X to wait when an error occurs.

* **Show details**: Select this if you want to show information such as cycles count (FPS) and emulation speed on the DOSBox-X title bar.

* **Debugger**: Starts the DOSBox-X Debugger.

* **Show console**: Shows the DOSBox-X console window. You will see debugging information in the console.

* **Capture mouse**: DOSBox-X will capture the mouse immediately for use with the emulated DOS.

* **Autolock mouse**: DOSBox-X will lock the mouse automatically for use with the emulated DOS.

* **Pause**: Check to pause the emulated DOS inside DOSBox-X completely. The emulated DOS will resume when it is unchecked.

* **Pause with interrupts enabled**: Pauses the emulated DOS inside DOSBox-X without disabling the DOS interrupts. This allows certain DOS functions to continue to work. For example, if you are running Demoscene games and use this function, then the game itself will be paused but the game music may continue to play. It is also a good way to hear the entire music in a Demoscene production when the demo exits long before the music has time to loop.

* **Reset guest system**: Restarts the emulated DOS inside DOSBox-X.

* **Quit**: Exit from DOSBox-X.

**2. The "CPU" menu**

* **Turbo (Fast Forward)**: Increases the emulated DOS's current CPU speed to 200%-300% of the normal speed.

* **Normal speed**: Restores the emulated DOS's current speed relative to real-time to the normal speed.

* **Speed up**: Increases the emulated DOS's current speed relative to real-time. You can speed up the emulation with this if you want to play a game at greater than 100% normal speed.

* **Speed down**: Decreases the emulated DOS's current speed relative to real-time. You can slow down the emulation with this if you want to play a game at less than 100% normal speed.

* **Increment cycles**: Increases the amount of CPU instructions DOSBox-X tries to emulate each millisecond.

* **Decrement cycles**: Decreases the amount of CPU instructions DOSBox-X tries to emulate each millisecond.

* **Edit cycles**: Sets the amount of CPU instructions DOSBox-X tries to emulate each millisecond to a specific value.

* **CPU core**: Selects the emulated DOS's CPU core - normal, full, simple, dynamic, or auto.

* **CPU type**: Selects the emulated DOS's CPU type, such as 8086, 80286, 80386, 80486, Pentium, or Pentium Pro.

**3. The "Video" menu**

* **Fit to aspect ratio**: Select whether to fit DOSBox-X's emulated DOS screen to the aspect ratio (width-to-height ratio) correction mode.

* **Toggle fullscreen**: Toggles the full-screen mode of DOSBox-X's emulated DOS screen.

* **Always on top**: Select whether the DOSBox-X window will always be the topmost one.

* **Double Buffering (Fullscreen)**: Toggles the double-buffering feature in the fullscreen mode. It can reduce screen flickering, but it can also result in a slower speed.

* **Hide/show menu bar**: Select whether to show DOSBox-X's GUI menu bar where supported.

* **Reset window size**: Resets the DOSBox-X window to the default size.

* **Frameskip**: Changes the frameskip setting, i.e. how many frames DOSBox-X skips before drawing one, from 0 to 10.

* **Force scaler**: Forces the use of a scaler even if the result might not be desired. To fit a scaler in the resolution used at full screen may require a border or side bars. To fill the screen entirely, depending on your hardware, a different scaler/fullresolution might work.

* **Scaler**: Selects a scaler used to enlarge/enhance low resolution modes.

* **Output**: Selects the video system to use for output, such as Surface, Direct3D or OpenGL.

* **V-Sync**: Synchronizes V-Sync timing to the host display. This requires calibration within DOSBox-X.

* **Overscan**: Selects the width of the overscan border, from 0 to 10. This works only if the video output is set to surface.

* **Compatibility**: Selects whether to allow 9-pixel wide text mode fonts and to enable double-scan mode (double-scanned output emits two scanlines for each source line).

* **PC-98**: Changes the PC-98 related settings, such as whether to allow EGC and GRCG graphics functions.

* **Debug**: Enables video debugging functions, such as blank screen refresh tests.

* **Select pixel shader...**: Selects a Direct3D pixel shader file for use with DOSBox-X in Windows. In case the shader fails to load, there is no visual indication but it will be written to the log file. If you want more immediate feedback on success or failure, use the menu to show the DOSBox-X console which will also show the reason for the shader failure.

**4. The "Sound" menu**

* **Increase volume**: Increases the sound volume of DOSBox-X's emulated DOS.

* **Decrease volume**: Decreases the sound volume of DOSBox-X's emulated DOS.

* **Mute**: Mutes or unmutes the sound volume of DOSBox-X's emulated DOS.

* **Swap stereo**: Selects whether to swap the left and right stereo channels.

**5. The "DOS" menu**

* **Mouse**: Changes the mouse settings for the emulated DOS inside DOSBox-X, such as the mouse sensitivity.

* **PC-98 PIT master clock**: Selects the PIT master clock for the PC-98 system (4MHz/8MHz or 5MHz/10MHz).

* **Swap floppy**: Swaps the floppy image if you are using multiple floppy disk images.

* **Swap CD**: Swaps the CD image if you are using multiple CD images.

* **Rescan all drives**: Refreshes the cache for all DOS drives inside DOSBox-X.

**6. The "Capture" menu**

* **Take screenshot**: Takes a screenshot of the current DOS screen in PNG format.

* **Capture format**: Selects the video format for DOSBox-X's captures.

* **Record video to AVI**: Starts/stops the recording of the current DOS session to an AVI video.

* **Record audio to WAV**: Starts/stops the recording of the current DOS session to a WAV audio.

* **Record audio to multi-track AVI**: Starts/stops the recording of the current DOS session to a multi-track audio-only AVI file.

* **Record FM (OPL) output**: Starts/stops the recording of Yamaha FM (OPL) commands in DRO format.

* **Record MIDI output**: Starts/stops the recording of raw MIDI commands.

**7. The "Drive" menu**

* **A**-**Z**: For each DOS drive, re-scans (refreshes the cache) or un-mounts this drive.

### DOSBox-X's Special Keys

You can use these special keys to achieve certain functions in DOSBox-X, such as switching between the window and full-screen modes. These shortcuts are different from the ones in DOSBox.

* **[F11/F12]+F**  
Switch to full-screen mode and back.
* **[F11/F12]+R**  
Restart the emulated DOS inside DOSBox-X.
* **[F11/F12]+M**  
Start DOSBox-X's keyboard mapper.
* **[F11/F12]+Esc**  
Show/hide the GUI menu bar.
* **[F11/F12]+{+}**  
Increase the sound volume of DOSBox-X's emulated DOS.
* **[F11/F12]+{-}**  
Decrease the sound volume of DOSBox-X's emulated DOS.
* **[F11/F12]+]**  
Increases the emulated DOS's current speed relative to real-time.
* **[F11/F12]+[**  
Decreases the emulated DOS's current speed relative to real-time.
* **[F11/F12]+{=}**  
Increase DOSBox-X's emulation CPU cycles.
* **[F11/F12]+{-}**  
Decrease DOSBox-X's emulation CPU cycles.
* **[F11/F12]+Left**  
Reset the emulated DOS's current CPU speed to the normal speed.
* **[F11/F12]+LCtrl+C**  
Swap between mounted CD images.
* **[F11/F12]+LCtrl+D**  
Swap between mounted floppy images.
* **[F11/F12]+LShift+S**  
Take a screenshot of the current screen in PNG format.
* **[F11/F12]+LShift+V**  
Start/Stop capturing an AVI video of the current session.
* **[F11/F12]+LShift+W**  
Start/Stop recording a WAV audio of the current session.
* **LAlt+Pause**  
Start DOSBox-X's Debugger.
* **LCtrl+F9**  
Exit DOSBox-X.
* **LCtrl+F10**  
Capture the mouse for use with the emulated DOS.
* **LCtrl+Pause**  
Pause emulation (press again to continue).

Notes:

* **1.** **[F11/F12]** is the host key, meaning either F11 or F12 (depending on the operating system). F11 is the host key in Windows, and F12 is the host key in all other platforms (Linux, macOS, etc). The F12 key is avoided being the host key in Windows because it is used internally by Windows for debugging functions. The host key can be redefined in DOSBox-X's keyboard mapper as needed, if you want to use a different key than F11 or F12.

* **2:** **LCtrl** means the Left Ctrl key, **LShift** means the Left Shift key, and **LAlt** means the Left Alt key.

### DOSBox-X's Supported Commands

Many internal or external MS-DOS commands are supported by DOSBox-X. Also, DOSBox-X offers additional commands such as MOUNT and CAPMOUSE, which are not found in MS-DOS or compatibles.

* **25/28/50** (external command)  
Changes the DOSBox-X screen to 25/28/50 line mode.  
Usage: Simply enter 25, 28, or 50 without any parameters.
* **A20GATE** (external command)  
Turns on/off or changes the A20 gate mode.  
Usage: A20GATE SET [off | off_fake | on | on_fake | mask | fast] or A20GATE [ON | OFF]
* **ADDKEY** (internal command)  
Generates artificial keypresses.  
Usage: ADDKEY key
* **APPEND** (external command)  
Enables programs to open data files in specified directories as if the files were in the current directory.  
Usage: APPEND [ [drive]:path[;...] ] [/X[:ON|:OFF]] [/PATH:ON|/PATH:OFF] [/E]  
Note: It uses the APPEND command from FreeDOS.
* **BOOT** (external command)  
Starts disk or BIOS images independent of the operating system emulation offered by DOSBox-X.  
Usage: BOOT [diskimg1.img diskimg2.img] [-l driveletter] [-bios image]  
Note: Loading a BIOS image is currently experimental - at this time it will only work for custom code and assembly experiments.
* **BUFFERS** (external command)  
Displays or changes the CONFIG.SYS's BUFFERS setting.  
Usage: BUFFERS [buffernum]
* **CALL** (internal command)  
Starts a batch file from within another batch file.  
Usage: CALL [drive:][path]filename [batch-parameters]
* **CAPMOUSE** (external command)  
Captures or releases the mouse inside DOSBox-X.  
Usage: CAPMOUSE [/C|/R]
* **CD/CHDIR** (internal command)  
Displays or changes the current directory.  
Usage: CD [drive:][path] or CHDIR [drive:][path]
* **CHOICE** (internal command)  
Waits for a key press and sets ERRORLEVEL. Displays the given prompt followed by [Y,N]? for yes or no response.  
Usage: CHOICE [/C:choices] [/N] [/S] text
* **CLS** (internal command)  
Clears the screen of all input and returns just the current prompt in the upper left hand corner.  
Usage: Simply enter CLS without any parameters.
* **COMMAND** (external command)  
Restarts DOSBox-X's command shell.  
Usage: COMMAND [options]
* **CONFIG** (external command)  
Starts DOSBox-X's config tool to change it settings.  
Usage: CONFIG [options]
* **COPY** (internal command)  
Copies one or more files.  
Usage: COPY source [destination]
* **CTTY** (internal command)  
Changes the standard I/O device.  
Usage: CTTY device
* **CWSDPMI** (external command)  
Starts CWSDPMI, a 32-bit DPMI server used by various DOS games/applications.  
Usage: CWSDPMI [options]
* **DATE** (internal command)  
Displays or changes the internal date.  
Usage: DATE [ [/T] [/H] [/S] | MM-DD-YYYY ]
* **DEBUG** (external command)  
The DOS DEBUG tool used to test and edit programs.  
Usage: DEBUG [ [drive:][path]progname [arglist] ]
* **DEL/ERASE** (internal command)  
Removes one or more files.  
Usage: DEL [/P] [/Q] names or ERASE [/P] [/Q] names
* **DEVICE** (external command)  
Load device drivers as CONFIG.SYS's DEVICE command.  
Usage: DEVICE [program] [options]
* **DIR** (internal command)  
Lists available files and sub-directories inside the current directory.  
Usage: DIR [drive:][path][filename] [options]
* **DOS32A** (external command)  
Starts DOS32A, a 32-bit DOS extender used by various DOS games/applications.  
Usage: DOS32A executable.xxx
* **DOS4GW** (external command)  
Starts DOS4GW, a 32-bit DOS extender used by various DOS games/applications.  
Usage: DOS4GW executable.xxx
* **DOSIDLE** (external command)  
Puts the DOS emulator into idle mode for lower CPU usages.    
Usage: Simply enter DOSIDLE without any parameters.
* **DSXMENU** (external command)  
Runs DOSLIB's DSXMENU tool, a simple DOS menu system.  
Usage: DSXMENU [-d] INI_file  
Note: This is an open-source tool; its source code is in the related DOSLIB project.
* **DX-CAPTURE** (internal command)  
Starts capture (AVI, WAV, etc. as specified), runs program, then automatically stops capture when the program exits.  
Usage: DX-CAPTURE [command] [options]  
Note: This built-in command name is deliberately longer than 8 characters so that there is no conflict with external .COM/.EXE executables that are limited to 8.3 filenames. It can be used for example to make Demoscene captures and to make sure the capture stops when it exits.
* **ECHO** (internal command)  
Displays messages and enable/disable command echoing.  
Usage: ECHO [message] or ECHO [ON | OFF]
* **EDIT** (external command)  
Starts the full-screen file editor.  
Usage: EDIT [/B] [/I] [/H] [/R] [file(s)]  
Note: It uses the EDIT command from FreeDOS.
* **EXIT** (internal command)  
Exits from the batch file or DOSBox-X.  
Usage: Simply enter EXIT without any parameters.
* **FCBS** (external command)  
Displays or changes the CONFIG.SYS's FCBS setting.  
Usage: FCBS [fcbnum]
* **FIND** (external command)  
Prints lines of a file that contains the specified string.  
Usage: FIND [/C] [/I] [/N] [/V] "string" [file(s)]  
Note: It uses the FIND command from FreeDOS.
* **GOTO** (internal command)  
Jumps to a labeled line in a batch script.  
Usage: GOTO label
* **HELP** (internal command)             
Shows command help.  
Usage: HELP [/all]
* **HEXMEM16/HEXMEM32** (external command)  
Runs DOSLIB's HEXMEM tool, a memory viewer/dumper.  
Usage: HEXMEM16 [options] or HEXMEM32 [options]  
Note: Included in the related DOSLIB project, this open-source tool was specifically written as a way to poke around the addressable memory available to the CPU and to show how a 16-bit DOS program can access extended memory, including flat real mode, and the 286 reset vector trick for 80286 systems. There is also code to access memory above 4GB if the CPU supports 64-bit long mode or the PAE page table extensions, although these are not yet supported by DOSBox-X.
* **IF** (internal command)  
Performs conditional processing in batch programs.  
Usage: IF [NOT] ERRORLEVEL number command or IF [NOT] string1==string2 command or IF [NOT] EXIST filename command
* **IMGMAKE** (external command)  
Makes floppy drive or hard-disk images.  
Usage: IMGMAKE file [-t type] [-size size|-chs geometry] [-nofs] [-source source] [-r retries] [-bat]
* **IMGMOUNT** (external command)  
Mounts drives from floppy drive, hard-disk, or CD images in the host system.  
Usage: IMGMOUNT drive filename [options] or IMGMOUNT -u drive|driveLocation
* **INTRO** (external command)  
A full-screen introduction.  
Usage: Simply enter INTRO without any parameters.
* **KEYB** (external command)  
Changes the layout of the keyboard used for different countries.  
Usage: KEYB [keyboard layout ID [codepage number [codepage file]]]
* **LABEL** (external command)  
Changes the label of a drive.   
Usage: LABEL [drive:][label]
* **LASTDRIV** (external command)  
Displays or changes the CONFIG.SYS's LASTDRIVE setting.  
Usage: LASTDRIV [driveletter]
* **LOADFIX** (external command)  
Loads a program above the first 64K of memory.  
Usage: LOADFIX [program] [options]
* **LOADROM** (external command)  
Loads the specified Video BIOS ROM image file.  
Usage: LOADROM ROM_file
* **LH/LOADHIGH** (internal command)  
Loads a program into upper memory (if UMB is available).  
Usage: LH [program] [options] or Usage: LOADHIGH [program] [options]
* **MD/MKDIR** (internal command)  
Makes a directory.  
Usage: MD [drive:][path] or MKDIR [drive:][path]
* **MEM** (external command)  
Displays the status of the DOS memory, such as the amount of free memory.  
Usage: MEM [options]  
Note: It uses the MEM command from FreeDOS.
* **MIXER** (external command)  
Displays current sound levels.  
Usage: Simply enter MIXER without any parameters.
* **MODE** (external command)  
Configures DOS system devices.  
Usage: MODE display-type or MODE CON RATE=r DELAY=d
* **MORE** (internal command)  
Displays output one screen at a time.  
Usage: MORE [filename]
* **MOUNT** (external command)  
Mounts drives from directories or drives in the host system.  
Usage: MOUNT driveletter host_directory [options]  
Note: It accepts a -nocachedir option to not cache the drive, so that the RESCAN command is not needed and DIR will always show the most recent contents on this drive.
* **MOUSE** (external command)  
Turns on/off mouse support.  
Usage: MOUSE [/U] [/V]
* **MOVE** (external command)  
Moves a file or directory to another location.  
Usage: MOVE [/Y | /-Y] source1[, source2[,...]] destination  
Note: It uses the MOVE command from FreeDOS.
* **NMITEST** (external command)  
Generates a non-maskable interrupt (NMI).  
Usage: NMITEST [options]  
Note: This is a debugging tool to test that it and the interrupt handler work properly. Currently the only use of the NMI is PCjr emulation which receives an NMI every time a key is pressed on the keyboard.
* **PATH** (internal command)  
Displays/Sets a search patch for executable files.  
Usage: PATH [drive:]path[;...][;PATH] or PATH ;
* **PAUSE** (internal command)  
Waits for a keystroke to continue.  
Usage: PAUSE [message]
* **PROMPT** (internal command)  
Changes the DOS command prompt.  
Usage: PROMPT [text]
* **RD/RMDIR** (internal command)  
Removes a directory.  
Usage: RD [drive:][path] or RMDIR [drive:][path]
* **RE-DOS** (external command)  
Sends a signal to re-boot the kernel of the emulated DOS, without rebooting DOSBox-X itself.  
Usage: Simply enter RE-DOS without any parameters.
* **REM** (internal command)  
Adds comments in a batch file.  
Usage: REM [comment]
* **REN/RENAME** (internal command)  
Renames one or more files.  
Usage: REN [drive:][path]filename1 filename2 or RENAME [drive:][path]filename1 filename2
* **RESCAN** (external command)  
Refreshes mounted drives by clearing their caches.  
Usage: Simply enter RESCAN without any parameters.
* **SET** (internal command)  
Displays and sets environment variables.  
Usage: SET [variable=[string]]
* **SHIFT** (internal command)  
Left-shifts command-line parameters in a batch script.  
Usage: Simply enter SHIFT without any parameters.
* **SHOWGUI** (external command)  
Starts DOSBox-X's configuration GUI dialog, where you can review or change its settings.  
Usage: Simply enter SHOWGUI without any parameters.
* **SUBST** (internal command)  
Assigns an internal directory to a drive.  
Usage: SUBST [drive1: [drive2:]path] or SUBST drive1: /D
* **TIME** (internal command)  
Displays the internal time.  
Usage: TIME [/T] [/H]
* **TREE** (external command)  
Graphically displays the directory structure of a drive or path.  
Usage: TREE [drive:][path] [/F] [/A]  
Note: It uses the TREE command from FreeDOS.
* **TYPE** (internal command)  
Displays the contents of a text-file.  
Usage: TYPE [drive:][path][filename]
* **VER** (internal command)  
Views and sets the reported DOS version. Also displays the running DOSBox-X version.  
Usage: VER [SET major minor]
* **VESAMOED** (external command)  
Runs the VESA BIOS mode editor utility, which can be used to add, modify or delete VESA BIOS modes.  
Usage: VESAMOED [options]  
Note: It was originally written because some old DOS games or demoscene productions, especially those shipped with a UNIVBE binary, assumed video mode numbers instead of enumerating like they should. It can also be used to rearrange VESA BIOS modes for retro developers who want to make sure their code works properly no matter what strange VESA BIOS their code runs into on real hardware. Because of limitations in DOSBox-X SVGA emulation and the render scaler architecture, the maximum resolution possible resolution is 1920x1440.
* **VFRCRATE** (external command)  
Forces video emulation to a specific refresh rate (or turn off the forced rate).  
Usage: VFRCRATE [SET OFF|PAL|NTSC|rate]  
Note: It was originally written to run demoscene games at 59.94Hz (NTSC) so that no frame blending is needed to author to DVD. It can also be used for development and testing to simulate a PC whose refresh rate is locked in hardware, such as what happens when running a DOS program on laptops. Even though standard VGA is 60Hz or 70Hz, laptops will lock the refresh rate to 60Hz when sending video to the internal display.
* **VOL** (internal command)  
Displays the disk volume label and serial number, if they exist.  
Usage: VOL [drive]
* **XCOPY** (external command)  
Copies files and directory trees.  
Usage: XCOPY source [destination] [options]  
Note: It uses the XCOPY command from FreeDOS.

### DOSBox-X's Command-line Options

DOSBox-X supports command-line options. You can start DOSBox-X without any option, or with any of the following options.

* **-h** or **-help**                              
Shows DOSBox-X's help message.
* **-editconf [program]**                             
Calls program with as first parameter the configuration file. You can specify this command more than once. In this case it will move to second program if the first one fails to start.
* **-opencaptures [program]**                              
Calls program with as first parameter the location of the captures folder.                        
* **-opensaves [program]**                              
Calls program with as first parameter the location of the saves folder.
* **-eraseconf**                              
Erases DOSBox-X's default config file.
* **-resetconf**                              
Erases DOSBox-X's default config file.
* **-printconf**                              
Generates DOSBox-X's config file in the user directory and prints its location.
* **-erasemapper**                            
Erases the mapper file used by the default clean configuration file.
* **-resetmapper**                            
Erases the mapper file used by the default clean configuration file.
* **-console**                                
Starts DOSBox-X with the console window (win32 only).
* **-noconsole**                              
Starts DOSBox-X without showing the console window (debug+win32 only).
* **-nogui**                                  
Starts DOSBox-X without showing its GUI menu (win32 only).
* **-nomenu**                                 
Starts DOSBox-X without showing its GUI menu (win32 only).
* **-userconf**                               
Loads the configuration from the user's profile or home directory.
* **-conf [file]**                           
Uses the specified file as DOSBox-X's config file.
* **-startui** or **-startgui**                      
Starts DOSBox-X with its configuration GUI dialog, where you can review or change its settings.
* **-startmapper**                            
Starts DOSBox-X and enters to the keyboard mapper editor directly.
* **-showcycles**                             
Shows cycles count (FPS) on the DOSBox-X title bar.
* **-showrt**                                 
Shows emulation speed relative to realtime on the DOSBox-X title bar.
* **-fullscreen**                             
Starts DOSBox-X in full-screen mode.
* **-savedir [path]**                         
Uses the specified path as DOSBox-X's save path.
* **-disable-numlock-check**                  
Disables numlock check (win32 only).
* **-date-host-forced**                       
Forces synchronization of date with the host system.
* **-debug**                                  
Sets all logging levels to debug.
* **-early-debug**                            
Logs early initialization messages in DOSBox-X (this option implies -console).
* **-keydbg**                                 
Logs all SDL key events (debugging).
* **-lang [message file]**                    
Uses specific message file instead of language= setting.
* **-nodpiaware**                             
Ignores (don't signal) Windows DPI awareness.
* **-securemode**                             
Enables DOSBox-X's secure mode. The [autoexec] section of the loaded configuration file will be skipped, and commands such as MOUNT and IMGMOUNT are disabled.
* **-noautoexec**                             
Skips the [autoexec] section of the loaded configuration file.
* **-exit**                                   
Exits after executing the [autoexec] section of the loaded configuration file.
* **-c [command string]**                              
Execute this command in addition to the [autoexec] section of the loaded configuration file. Make sure to surround the command in quotes to cover spaces.
* **-break-start**                              
Starts DOSBox-X and breaks into its debugger directly.
* **-time-limit [n]**                              
Starts and terminates DOSBox-X after 'n' seconds.
* **-fastbioslogo**                              
Skips the 1-second BIOS pause with Fast BIOS logo.
* **-log-con**                              
Logs CON output to a log file.

### Compatibility
We are making efforts to ensure that most DOS games and applications will run in DOSBox-X. Below are some test results.

DOSBox-X vs Demoscene test results (up to date): https://htmlpreview.github.io/?https://github.com/joncampbell123/demotest/blob/master/compat-chart.html

* [[Guide: MS-DOS demoscene|Guide:MS-DOS:demoscene]]  
* [[Guide: MS-DOS games|Guide:MS-DOS:games]]  
* [[Guide: PC-DOS or MS-DOS in DOSBox-X|Guide:MS-DOS]]  
* [[Guide: Windows in DOSBox|Guide:Windows]]  

### Frequently Asked Questions (FAQ)
* **What is DOS?**  
DOS is short for "**D**isk **O**perating **S**ystem". It refers to the series of operating systems that dominated the IBM PC compatible market in the 1980s and the 1990s. Early versions of Microsoft Windows (1.0-3.x, as well as 9x/ME) are also largely DOS-based. The relevant systems were usually called "X DOS", "X-DOS" or "XDOS" with the X being the brand name (e.g. PC DOS, DR-DOS, and FreeDOS respectively). Despite common usage, none of them were actually called just DOS. Microsoft's system, MS-DOS, was the most-widely used among these operating systems.

* **What is DOSBox-X's release pattern?**  
Currently, new DOSBox-X versions are made public at the start of each month, including the source code and binary releases. Then the DOSBox-X developments will be re-opened for new features, pull requests, etc. There will be no new features added 6 days before the end of the month, but only bug fixes. The last day of the month is DOSBox-X's build day to compile for binary releases the first of the next month, so there will be no source code changes on this day including pull requests or bug fixes. This is DOSBox-X's official release pattern, although it may change later.
