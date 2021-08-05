# Linux-Backups-Tools
A set of shell tools for creating and restoring backups of Unix and Linux installs. Provides a minimal CLI interface that displays the selected backup or restore folder, the total data processed vs original size, and running or finished status. Includes `mksysbak` for creating bootable TAR/GZ backups of the system itself, `mkusrbak` for creating backups of individual user's home folders, `mkandrbak` for creating no-root backups of Android device data (user APKs, user data, and external and internal SD card contents). Also includes `rstsysbak` for restoring backups to a specified directory, and `rstusrbak` for restoring user home folders. 

NOTE: If a user was not originally present in an install before restoring a home folder, be sure to first add the user and assign them to the necessary groups, then restore over the newly created home folder. When creating user backups with `mkusrbak` be sure to edit the static user names in the script to match the one you are trying to back up! Additionally when creating Android backups be sure to edit the Internal and External SD card sections of the `mkandrbak` script to match which directories you need to back up. I needed to exclude specific directories and there is no way to do this easily with ADB, so user storage directories are staticlly specified.

Dependencies: `mksysbak`: none
              `mkusrbak`: none
              `mkandrbak`: ADB platform tools (newest)
              `rstsysbak`: none
              `rstusrbak`: none
