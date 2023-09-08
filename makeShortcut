#!/bin/bash

writeDesktop () { 
echo "[Desktop Entry]
Exec=$(echo $1 | xargs)
Name=$(echo $2 | xargs)
Icon=$(echo $3 | xargs)
Keywords=$(echo $4 | xargs)
Categories=$(echo $5 | xargs)
Terminal=$(echo $6 | xargs)
StartupNotify=$(echo $7 | xargs)
Type=$(echo $8 | xargs)"  | tee ~/Desktop/$(echo $2 | xargs).desktop
}

writeMenu () { 
echo "[Desktop Entry]
Exec=$(echo $1 | xargs)
Name=$(echo $2 | xargs)
Icon=$(echo $3 | xargs)
Keywords=$(echo $4 | xargs)
Categories=$(echo $5 | xargs)
Terminal=$(echo $6 | xargs)
StartupNotify=$(echo $7 | xargs)
Type=$(echo $8 | xargs)"  | sudo tee /usr/share/applications/$(echo $2 | xargs).desktop
}

writeAdDesktop () {
echo "[Desktop Entry]
Type=$(echo $1 | xargs)
Version=$(echo $2 | xargs)
Name=$(echo $3 | xargs)
GenericName=$(echo $4 | xargs)
NoDisplay=$(echo $5 | xargs)
Comment=$(echo $6 | xargs)
Icon=$(echo $7 | xargs)
Hidden=$(echo $8 | xargs)
OnlyShowIn=$(echo $9 | xargs)
NotShowIn=$(echo ${10} | xargs)
DBusActivatable=$(echo ${11} | xargs)
TryExec=$(echo ${12} | xargs)
Exec=$(echo ${13} | xargs)
Path=$(echo ${14} | xargs)
Terminal=$(echo ${15} | xargs)
Actions=$(echo ${16} | xargs)
MimeType=$(echo ${17} | xargs)
Categories=$(echo ${18} | xargs)
Implements=$(echo ${19} | xargs)
Keywords=$(echo ${20} | xargs)
StartupNotify=$(echo ${21} | xargs)
StartupWMClass=$(echo ${22} | xargs)
URL=$(echo ${23} | xargs)
PrefersNonDefaultGPU=$(echo ${24} | xargs)
SingleMainWindow=$(echo ${25} | xargs)" | tee ~/Desktop/$(echo $3 | xargs).desktop
}

writeAdMenu () {
echo "[Desktop Entry]
Type=$(echo $1 | xargs)
Version=$(echo $2 | xargs)
Name=$(echo $3 | xargs)
GenericName=$(echo $4 | xargs)
NoDisplay=$(echo $5 | xargs)
Comment=$(echo $6 | xargs)
Icon=$(echo $7 | xargs)
Hidden=$(echo $8 | xargs)
OnlyShowIn=$(echo $9 | xargs)
NotShowIn=$(echo ${10} | xargs)
DBusActivatable=$(echo ${11} | xargs)
TryExec=$(echo ${12} | xargs)
Exec=$(echo ${13} | xargs)
Path=$(echo ${14} | xargs)
Terminal=$(echo ${15} | xargs)
Actions=$(echo ${16} | xargs)
MimeType=$(echo ${17} | xargs)
Categories=$(echo ${18} | xargs)
Implements=$(echo ${19} | xargs)
Keywords=$(echo ${20} | xargs)
StartupNotify=$(echo ${21} | xargs)
StartupWMClass=$(echo ${22} | xargs)
URL=$(echo ${23} | xargs)
PrefersNonDefaultGPU=$(echo ${24} | xargs)
SingleMainWindow=$(echo ${25} | xargs)"  | sudo tee /usr/share/applications/$(echo $3 | xargs).desktop
}

if [ "$1" == "-d" ] ; then
    if [ "$9" != " " ] | [ "$9" != "" ] ; then
            writeDesktop "$2 " "$3 " "$4 " "$5 " "$6 " "$7 " "$8 " "$9 "
    else
        if [ "$3" != " " ] |  [ "$3" != "" ] ; then
            writeDesktop "$2 " "$3 " "$4 " "$5 " "$6 " "$7 " "$8 " "Application "
        else 
            writeDesktop "$2 " "$2 " "$2 " "$5 " "$6 " "$7 " "$8 " "Application "
        fi
    fi
fi

if [ "$1" == "-m" ] ; then
    if [ "$9" != " " ] | [ "$9" != "" ] ; then
            writeMenu "$2 " "$3 " "$4 " "$5 " "$6 " "$7 " "$8 " "$9 "
    else
        if [ "$3" != " " ] |  [ "$3" != "" ] ; then
            writeMenu "$2 " "$3 " "$4 " "$5 " "$6 " "$7 " "$8 " "Application "
        else 
            writeMenu "$2 " "$2 " "$2 " "$5 " "$6 " "$7 " "$8 " "Application "
        fi
    fi
fi 


if [ "$1" == "-ad" ] ; then
    writeAdDesktop "$2 " "$3 " "$4 " "$5 " "$6 " "$7 " "$8 " "$9 " "${10} " "${11} " "${12} " "${13} " "${14} " "${15} " "${16} " "${17} " "${18} " "${19} " "${20} " "${21} " "${22} " "${23} " "${24} " "${25} " "${26} "
fi 

if [ "$1" == "-am" ] ; then
    writeDesktop "$2 " "$3 " "$4 " "$5 " "$6 " "$7 " "$8 " "$9 " "${10} " "${11} " "${12} " "${13} " "${14} " "${15} " "${16} " "${17} " "${18} " "${19} " "${20} " "${21} " "${22} " "${23} " "${24} " "${25} " "${26} "
fi 
