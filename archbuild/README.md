# Raspberry-Pi Utilities : ArchBuild 

ArchBuild will build a new root filesystem for the Raspberry Pi. Use it instead of
the official image if you want to tweak the installation.

## Source Files

The directory 'source_files' contains the files needed to complete the build
of a new root filesystem. This directory can be re-created using the collect
script described below.

## Collect

This is a simple script to collect the required files from a running raspberry-Pi
Arch Linux system.

## ArchBuild

This is a script to build a new  baseline Arch Linux root filesystem image. It 
requires that the source files directory (described above) exists.

### Unmount

This is a quick and dirty script to unmount the archroot created by build if,
for some reason, the build script fails uncleanly.
