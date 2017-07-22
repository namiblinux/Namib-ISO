Switching between 32 and 64 bit ISO creation
--------------------------------------------

NOTE: There is no UEFI support for 32bit ISOs.
      Support of i686 have been stopped the 2017-01-25

1. Clear out the pacman cache (prevents mixing of 32 and 64 bit versions of the same packages)
pacman -Scc

2. Edit /syslinux/archiso_sys_both_inc.cfg 
2a. Unhash the desired system build, and hash the undesired one. The example below is for 64bit:

INCLUDE boot/syslinux/archiso_sys64.cfg
#INCLUDE boot/syslinux/archiso_sys32.cfg

This is for 32 bit:
#INCLUDE boot/syslinux/archiso_sys64.cfg
INCLUDE boot/syslinux/archiso_sys32.cfg

2. Edit /pacman.conf
2a. Unhash multilib if you build for 64, or hash if you build for 32

4. Run ./build.sh for 64 bit, or ./build-32.sh for 32 bit.