# Linux-Backups-Tools
A set of shell tools for creating and restoring backups of Unix and Linux installs. Provides a minimal CLI interface that displays the selected backup or restore folder, the total data processed vs original size, and running or finished status. Includes `mksysbak` for creating bootable TAR/GZ backups of the system itself, `mkusrbak` for creating backups of individual user's home folders, `mkandrbak` for creating no-root backups of Android device data (user APKs, user data, and external and internal SD card contents). Also includes `rstsysbak` for restoring backups to a specified directory, and `rstusrbak` for restoring user home folders. 

UPDATE: `mkbase` is a less granular but more robust tool that combines the functions of `mksysbak`, `mkusrbak`, `rstsysbak`, and `rstusrbak` into one. It can be used to directly create a bootable clone from a live system. Just point it at the target disk and the rest is taken care of. Partitioning, cloning, and bootloader installation are all automated. This tool is intended for use at scale (i.e. for deploying identical copies of a Linux installation from a master/capture machine to target/client machines, or for cloning and tarballing a Linux install for external distribution), but it also serves as a tool for creating whole-system bootable backups to external disk. This is the recommended tool for both scenarios unless more granular control like backups of individual user profiles is required.

NOTE: If a user was not originally present in an install before restoring a home folder, be sure to first add the user and assign them to the necessary groups, then restore over the newly created home folder. When creating user backups with `mkusrbak` be sure to edit the static user names in the script to match the one you are trying to back up! Additionally when creating Android backups be sure to edit the Internal and External SD card sections of the `mkandrbak` script to match which directories you need to back up. I needed to exclude specific directories and there is no way to do this easily with ADB, so user storage directories are staticlly specified.

Dependencies: `mksysbak`: none
              `mkusrbak`: none
              `mkandrbak`: ADB platform tools (newest)
              `rstsysbak`: none
              `rstusrbak`: none
