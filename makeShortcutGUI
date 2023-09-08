#!/bin/bash

plug=$RANDOM


getOpp () {
    if [ "${1,,}" == "true" ] ; then
       echo "^True!False"
    else
       echo "True!^False"
    fi
}

getTypeB () {
    if [ "${1,,}" == "link" ] ; then
       echo "Application!^Link"
    else
        echo "^Application!Link"
    fi
}

getTypeA () {
    if [ "${1,,}" == "directory" ] ; then
       echo "Application!Link!^Directory"
    elif [ "${1,,}" == "link" ] ; then
       echo "Application!^Link!Directory"
    else
        echo "^Application!Link!Directory"
    fi
}

echo "$1"

if [ "$1" != "" ] ; then
    Type=$(grep -oP '^Type=\K.*' $1 | head -n1 )
    Version=$(grep -oP '^Version=\K.*' $1 | head -n1 )
    Name=$(grep -oP '^Name=\K.*' $1 | head -n1 )
    GenericName=$(grep -oP '^GenericName=\K.*' $1 | head -n1 )
    NoDisplay=$(grep -oP '^NoDisplay=\K.*' $1 | head -n1 )
    Comment=$(grep -oP '^Comment=\K.*' $1 | head -n1 )
    Icon=$(grep -oP '^Icon=\K.*' $1 | head -n1 )
    Hidden=$(grep -oP '^Hidden=\K.*' $1 | head -n1 )
    OnlyShowIn=$(grep -oP '^OnlyShowIn=\K.*' $1 | head -n1 )
    NotShowIn=$(grep -oP '^NotShowIn=\K.*' $1 | head -n1 )
    DBusActivatable=$(grep -oP '^DBusActivatable=\K.*' $1 | head -n1 )
    TryExec=$(grep -oP '^TryExec=\K.*' $1 | head -n1 )
    Exec=$(grep -oP '^Exec=\K.*' $1 | head -n1 )
    Path=$(grep -oP '^Path=\K.*' $1 | head -n1 )
    Terminal=$(grep -oP '^Terminal=\K.*' $1 | head -n1)
    Actions=$(grep -oP '^Actions=\K.*' $1 | head -n1 )
    MimeType=$(grep -oP '^MimeType=\K.*' $1 | head -n1 )
    Categories=$(grep -oP '^Categories=\K.*' $1 | head -n1 )
    Implements=$(grep -oP '^Implements=\K.*' $1 | head -n1 )
    Keywords=$(grep -oP '^Keywords=\K.*' $1 | head -n1 )
    StartupNotify=$(grep -oP '^StartupNotify=\K.*' $1 | head -n1 )
    StartupWMClass=$(grep -oP '^StartupWMClass=\K.*' $1 | head -n1 )
    URL=$(grep -oP '^URL=\K.*' $1 | head -n1 )
    PrefersNonDefaultGPU=$(grep -oP '^PrefersNonDefaultGPU=\K.*' $1 | head -n1 )
    SingleMainWindow=$(grep -oP '^SingleMainWindow=\K.*' $1 | head -n1 )
fi

exitCode=0
    yad --form --plug=$plug --tabnum=1 \
        --text="Unused fields may be left blank. Hover over an item for help." \
        --field="Type"!"Application Shortcut to a program, Link Shortcut to a website":CB "$(getTypeB $Type)" \
        --field="Title*"!"[REQUIRED] The Title that is displayed as the launchers name.":TB "$Name" \
        --field="Command/URL*"!"[REQUIRED] The command that is run to execute the app.":TB "$Exec" \
        --field="Icon"!"Path to the icon or the name of the app to be looked up in the icon table":TB "$Icon" \
        --field="Tags"!"Other words that can this laucher can be searched for in menus.":TB "$Keywords" \
        --field="Category"!"":CBE "$Categories!Utility!Settings!Office!Network!Graphics!Game!Education!Development!Video!Audio!AudioVideo" \
        --field="Launch With Terminal"!"If checked, the laucher will run the command in a terminal window.":CHK "$Terminal" \
        --field="Launch Notification"!"If checked, the laucher will send a \"__ is ready\" notification when the app has started.":CHK "$StartupNotify" \
        --field=" Add To Menus"!application-menu!"Add To all app gui menus.":BTN "bash -c \"makeShortcut -m '%3' '%2' '%4' '%5' '%6' '%7' '%8' '%1'\"" \
        --field=" Add To Desktop"!desktop!"Make desktop file at ~/Desktop.":BTN "bash -c \"makeShortcut -d '%3 ' '%2 ' '%4 ' '%5 ' '%6 ' '%7 ' '%8 ' '%1 '\"" \
    & \
    yad --form --plug=$plug --tabnum=2 --scroll --hscroll-policy=never \
        --text="Unused fields may be left blank. Hover over an item for help." \
        --field="Type"!"This specification defines 3 types of desktop entries: Application (type 1), Link (type 2) and Directory (type 3). To allow the addition of new types in the future, implementations should ignore desktop entries with an unknown type. ":CB "$(getTypeA $Type)" \
        --field="Version"!"Version of the Desktop Entry Specification that the desktop entry conforms with. Entries that confirm with this version of the specification should use 1.5. Note that the version field is not required to be present. ":TB "$Version" \
        --field="Name"!"Specific name of the application, for example \"Mozilla\". ":TB "$Name" \
        --field="GenericName"!"Generic name of the application, for example \"Web Browser\". ":TB "$GenericName" \
        --field="NoDisplay"!"NoDisplay means \"this application exists, but don't display it in the menus\". This can be useful to e.g. associate this application with MIME types, so that it gets launched from a file manager (or other apps), without having a menu entry for it (there are tons of good reasons for this, including e.g. the netscape -remote, or kfmclient openURL kind of stuff). ":CB "$(getOpp $NoDisplay)" \
        --field="Comment"!"Tooltip for the entry, for example \"View sites on the Internet\". The value should not be redundant with the values of Name and GenericName. ":TB "$Comment" \
        --field="Icon"!"Icon to display in file manager, menus, etc. If the name is an absolute path, the given file will be used. If the name is not an absolute path, the algorithm described in the Icon Theme Specification will be used to locate the icon. ":TB "$Icon" \
        --field="Hidden"!"Hidden should have been called Deleted. It means the user deleted (at their level) something that was present (at an upper level, e.g. in the system dirs). It's strictly equivalent to the .desktop file not existing at all, as far as that user is concerned. This can also be used to \"uninstall\" existing files (e.g. due to a renaming) - by letting make install install a file with Hidden=true in it. ":CB "$(getOpp $Hidden)" \
        --field="OnlyShowIn"!"A list of strings identifying the desktop environments that should display a given desktop entry. ":TB "$OnlyShowIn" \
        --field="NotShowIn"!"A list of strings identifying the desktop environments that should not display a given desktop entry. ":TB "$NotShowIn" \
        --field="DBusActivatable"!"A boolean value specifying if D-Bus activation is supported for this application. If this key is missing, the default value is false. If the value is true then implementations should ignore the Exec key and send a D-Bus message to launch the application. See D-Bus Activation for more information on how this works. Applications should still include Exec= lines in their desktop files for compatibility with implementations that do not understand the DBusActivatable key.":CB "$(getOpp $DBusActivatable)" \
        --field="TryExec"!"Path to an executable file on disk used to determine if the program is actually installed. If the path is not an absolute path, the file is looked up in the $PATH environment variable. If the file is not present or if it is not executable, the entry may be ignored (not be used in menus, for example).":TB "$TryExec" \
        --field="Exec"!"Program to execute, possibly with arguments. See the Exec key for details on how this key works. The Exec key is required if DBusActivatable is not set to true. Even if DBusActivatable is true, Exec should be specified for compatibility with implementations that do not understand DBusActivatable.":TB "$Exec" \
        --field="Path"!"If entry is of type Application, the working directory to run the program in.":TB "$Path" \
        --field="Terminal"!"Whether the program runs in a terminal window. ":CB "$(getOpp $Terminal)" \
        --field="Actions"!"Identifiers for application actions. This can be used to tell the application to make a specific action, different from the default behavior.":TB "$Actions" \
        --field="MimeType"!"The MIME type(s) supported by this application.":TB "$MimeType" \
        --field="Categories"!"Categories in which the entry should be shown in a menu (for possible values see the Desktop Menu Specification). ":CBE "$Category!Utility!Settings!Office!Network!Graphics!Game!Education!Development!Video!Audio!AudioVideo" \
        --field="Implements"!"A list of interfaces that this application implements. By default, a desktop file implements no interfaces.":TB "$Implements" \
        --field="Keywords"!"A list of strings which may be used in addition to other metadata to describe this entry. This can be useful e.g. to facilitate searching through entries. The values are not meant for display, and should not be redundant with the values of Name or GenericName.":TB "$Keywords" \
        --field="StartupNotify"!"If true, it is KNOWN that the application will send a \"remove\" message when started with the DESKTOP_STARTUP_ID environment variable set. If false, it is KNOWN that the application does not work with startup notification at all (does not shown any window, breaks even when using StartupWMClass, etc.). If absent, a reasonable handling is up to implementations (assuming false, using StartupWMClass, etc.). (See the Startup Notification Protocol Specification for more details).":CB "$(getOpp $StartupNotify)" \
        --field="StartupWMClass"!"If specified, it is known that the application will map at least one window with the given string as its WM class or WM name hint":TB "$StartupWMClass" \
        --field="[LINK] URL"!"If entry is Link type, the URL to access. ":TB "$URL" \
        --field="PrefersNonDefaultGPU"!"If true, the application prefers to be run on a more powerful discrete GPU if available, which we describe as “a GPU other than the default one” in this spec to avoid the need to define what a discrete GPU is and in which cases it might be considered more powerful than the default GPU. This key is only a hint and support might not be present depending on the implementation.":CB "$(getOpp $PrefersNonDefaultGPU)" \
        --field="SingleMainWindow"!"If true, the application has a single main window, and does not support having an additional one opened. This key is used to signal to the implementation to avoid offering a UI to launch another window of the app. This key is only a hint and support might not be present depending on the implementation.":CB "$(getOpp $SingleMainWindow)" \
        --field=" Add to Menus"!application-menu!"Add to Menus":BTN "makeShortcut -am '%1 ' '%2 ' '%3 ' '%4 ' '%5 ' '%6 ' '%7 ' '%8 ' '%9 ' '%10 ' '%11 ' '%12 ' '%13 ' '%14 ' '%15 ' '%16 ' '%17 ' '%18 ' '%19 ' '%20 '%21 %22 %23 %24 %25" \
        --field=" Add to Desktop"!desktop!"Add to Desktop":BTN "makeShortcut -ad %1 %2 %3 %4 %5 %6 %7 %8 %9 %10 %11 %12 %13 %14 %15 %16 %17 %18 %19 %20 %21 %22 %23 %24 %25" \
    & \

    yad --notebook --key=$plug --title="Make Shortcut" --tab="Basic" --tab="Advanced" --button="Done":252
