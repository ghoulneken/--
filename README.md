--
==

脚本类
#!/bin/bash
function set_perm_recursive()
{
    if [ $# -lt 5 ];then
        return
    fi
    uid=$1
    gid=$2
    dir_mode=$3
    file_mode=$4
    path=$5
    echo uid=$uid,gid=$gid
    chown $uid.$gid $path
    find $path -type d |xargs chmod $dir_mode
    find $path -type f |xargs chmod $file_mode
}
function set_perm()
{
    if [ $# -lt 4 ];then
        return
    fi
    uid=$1
    gid=$2
    mode=$3
    path=$4
    echo uid=$uid,gid=$gid
    chown $uid.$gid $path
    chmod $mode $path
}
function symlink()
{
    if [ $# -lt 2 ];then
        return
    fi
    exe=$1
    shift
    for lname in $*
    do
        rm -f $lname
        ln -s $exe $lname
    done
}

chmod a+x system/bin/*
chmod a+x system/xbin/*

symlink  /system/bin/aee_aed system/bin/debuggerd
symlink  /system/bin/mksh system/bin/sh
symlink  /system/bin/toolbox system/bin/cat system/bin/chmod system/bin/chown system/bin/cmp system/bin/cp system/bin/date system/bin/dd system/bin/df system/bin/dmesg system/bin/du system/bin/getevent system/bin/getprop system/bin/grep system/bin/hd system/bin/id system/bin/ifconfig system/bin/iftop system/bin/insmod system/bin/ioctl system/bin/ionice system/bin/kill system/bin/ln system/bin/log system/bin/ls system/bin/lsmod system/bin/lsof system/bin/md5 system/bin/mkdir system/bin/mount system/bin/mv system/bin/nandread system/bin/netstat system/bin/newfs_msdos system/bin/notify system/bin/printenv system/bin/ps system/bin/reboot system/bin/renice system/bin/rm system/bin/rmdir system/bin/rmmod system/bin/route system/bin/schedtop system/bin/sendevent system/bin/setconsole system/bin/setprop system/bin/sleep system/bin/smd system/bin/start system/bin/stop system/bin/sync system/bin/top system/bin/touch system/bin/umount system/bin/uptime system/bin/vmstat system/bin/watchprops system/bin/wipe
symlink  /system/fonts/Roboto-Bold.ttf system/fonts/DroidSans-Bold.ttf
symlink  /system/fonts/Roboto-Regular.ttf system/fonts/DroidSans.ttf system/fonts/EmojiPlaceholder.ttf
symlink  /system/lib/modules/wlan_mt6628.ko system/lib/modules/wlan.ko
symlink  /system/xbin/busybox system/bin/[ system/bin/[[ system/bin/acpid system/bin/addgroup system/bin/adduser system/bin/adjtimex system/bin/arp system/bin/arping system/bin/ash system/bin/awk system/bin/basename system/bin/beep system/bin/blkid system/bin/bootchartd system/bin/brctl system/bin/bunzip2 system/bin/bzcat system/bin/bzip2 system/bin/cal system/bin/catv system/bin/chat system/bin/chattr system/bin/chgrp system/bin/chpasswd system/bin/chpst system/bin/chroot system/bin/chrt system/bin/chvt system/bin/cksum system/bin/clear system/bin/comm system/bin/cpio system/bin/crond system/bin/crontab system/bin/cryptpw system/bin/cttyhack system/bin/cut system/bin/dc system/bin/deallocvt system/bin/delgroup system/bin/deluser system/bin/depmod system/bin/devmem system/bin/dhcprelay system/bin/diff system/bin/dirname system/bin/dnsd system/bin/dnsdomainname system/bin/dos2unix system/bin/dumpkmap system/bin/dumpleases system/bin/echo system/bin/ed system/bin/egrep system/bin/eject system/bin/env system/bin/envdir system/bin/envuidgid system/bin/ether-wake system/bin/expand system/bin/expr system/bin/fakeidentd system/bin/false system/bin/fbset system/bin/fbsplash system/bin/fdflush system/bin/fdformat system/bin/fdisk system/bin/fgconsole system/bin/fgrep system/bin/find system/bin/findfs system/bin/flock system/bin/fold system/bin/free system/bin/freeramdisk system/bin/fsck system/bin/fsck.minix system/bin/fsync system/bin/ftpd system/bin/ftpget system/bin/ftpput system/bin/fuser system/bin/getopt system/bin/getty system/bin/gunzip system/bin/halt system/bin/hdparm system/bin/head system/bin/hexdump system/bin/hostid system/bin/hostname system/bin/httpd system/bin/hush system/bin/hwclock system/bin/ifdown system/bin/ifenslave system/bin/ifplugd system/bin/ifup system/bin/inetd system/bin/init system/bin/install system/bin/ipaddr system/bin/ipcalc system/bin/ipcrm system/bin/ipcs system/bin/iplink system/bin/iproute system/bin/iprule system/bin/iptunnel system/bin/kbd_mode system/bin/killall system/bin/killall5 system/bin/klogd system/bin/last system/bin/length system/bin/less system/bin/linux32 system/bin/linux64 system/bin/linuxrc system/bin/loadfont system/bin/loadkmap system/bin/logger system/bin/login system/bin/logname system/bin/logread system/bin/losetup system/bin/lpd system/bin/lpq system/bin/lpr system/bin/lsattr system/bin/lspci system/bin/lsusb system/bin/lzcat system/bin/lzma system/bin/lzop system/bin/lzopcat system/bin/makedevs system/bin/makemime system/bin/man system/bin/md5sum system/bin/mdev system/bin/mesg system/bin/microcom system/bin/mkdosfs system/bin/mkfifo system/bin/mkfs.ext2 system/bin/mkfs.minix system/bin/mkfs.vfat system/bin/mknod system/bin/mkpasswd system/bin/mkswap system/bin/mktemp system/bin/modinfo system/bin/modprobe system/bin/more system/bin/mountpoint system/bin/mt system/bin/nameif system/bin/nc system/bin/nice system/bin/nmeter system/bin/nohup system/bin/nslookup system/bin/ntpd system/bin/od system/bin/openvt system/bin/passwd system/bin/patch system/bin/pgrep system/bin/pidof system/bin/ping6 system/bin/pipe_progress system/bin/pivot_root system/bin/pkill system/bin/popmaildir system/bin/poweroff system/bin/printf system/bin/pscan system/bin/pwd system/bin/raidautorun system/bin/rdate system/bin/rdev system/bin/readahead system/bin/readlink system/bin/readprofile system/bin/realpath system/bin/reformime system/bin/reset system/bin/resize system/bin/rev system/bin/rpm system/bin/rpm2cpio system/bin/rtcwake system/bin/run-parts system/bin/runlevel system/bin/runsv system/bin/runsvdir system/bin/rx system/bin/script system/bin/scriptreplay system/bin/sed system/bin/sendmail system/bin/seq system/bin/setarch system/bin/setfont system/bin/setkeycodes system/bin/setlogcons system/bin/setsid system/bin/setuidgid system/bin/sha1sum system/bin/sha256sum system/bin/sha512sum system/bin/showkey system/bin/slattach system/bin/smemcap system/bin/softlimit system/bin/sort system/bin/split system/bin/start-stop-daemon system/bin/stat system/bin/strings system/bin/stty system/bin/sulogin system/bin/sum system/bin/sv system/bin/svlogd system/bin/swapoff system/bin/swapon system/bin/switch_root system/bin/sysctl system/bin/syslogd system/bin/tac system/bin/tail system/bin/tar system/bin/tcpsvd system/bin/tee system/bin/telnet system/bin/telnetd system/bin/test system/bin/tftp system/bin/tftpd system/bin/time system/bin/timeout system/bin/tr system/bin/traceroute system/bin/traceroute6 system/bin/true system/bin/tty system/bin/ttysize system/bin/tunctl system/bin/udhcpc system/bin/udhcpd system/bin/udpsvd system/bin/uname system/bin/unexpand system/bin/uniq system/bin/unix2dos system/bin/unlzma system/bin/unlzop system/bin/unxz system/bin/unzip system/bin/usleep system/bin/uudecode system/bin/uuencode system/bin/vconfig system/bin/vi system/bin/vlock system/bin/volname system/bin/wall system/bin/watch system/bin/watchdog system/bin/wc system/bin/wget system/bin/which system/bin/who system/bin/whoami system/bin/xargs system/bin/xz system/bin/xzcat system/bin/yes system/bin/zcat system/bin/zcip system/xbin/[ system/xbin/[[ system/xbin/acpid system/xbin/addgroup system/xbin/adduser system/xbin/adjtimex system/xbin/arp system/xbin/arping system/xbin/ash system/xbin/awk system/xbin/basename system/xbin/beep system/xbin/blkid system/xbin/bootchartd system/xbin/brctl system/xbin/bunzip2 system/xbin/bzcat system/xbin/bzip2 system/xbin/cal system/xbin/cat system/xbin/catv system/xbin/chat system/xbin/chattr system/xbin/chgrp system/xbin/chmod system/xbin/chown system/xbin/chpasswd system/xbin/chpst system/xbin/chroot system/xbin/chrt system/xbin/chvt system/xbin/cksum system/xbin/clear system/xbin/cmp system/xbin/comm system/xbin/cp system/xbin/cpio system/xbin/crond system/xbin/crontab system/xbin/cryptpw system/xbin/cttyhack system/xbin/cut system/xbin/date system/xbin/dc system/xbin/dd system/xbin/deallocvt system/xbin/delgroup system/xbin/deluser system/xbin/depmod system/xbin/devmem system/xbin/df system/xbin/dhcprelay system/xbin/diff system/xbin/dirname system/xbin/dmesg system/xbin/dnsd system/xbin/dnsdomainname system/xbin/dos2unix system/xbin/du system/xbin/dumpkmap system/xbin/dumpleases system/xbin/echo system/xbin/ed system/xbin/egrep system/xbin/eject system/xbin/env system/xbin/envdir system/xbin/envuidgid system/xbin/ether-wake system/xbin/expand system/xbin/expr system/xbin/fakeidentd system/xbin/false system/xbin/fbset system/xbin/fbsplash system/xbin/fdflush system/xbin/fdformat system/xbin/fdisk system/xbin/fgconsole system/xbin/fgrep system/xbin/find system/xbin/findfs system/xbin/flock system/xbin/fold system/xbin/free system/xbin/freeramdisk system/xbin/fsck system/xbin/fsck.minix system/xbin/fsync system/xbin/ftpd system/xbin/ftpget system/xbin/ftpput system/xbin/fuser system/xbin/getopt system/xbin/getty system/xbin/grep system/xbin/gunzip system/xbin/gzip system/xbin/halt system/xbin/hd system/xbin/hdparm system/xbin/head system/xbin/hexdump system/xbin/hostid system/xbin/hostname system/xbin/httpd system/xbin/hush system/xbin/hwclock system/xbin/id system/xbin/ifconfig system/xbin/ifdown system/xbin/ifenslave system/xbin/ifplugd system/xbin/ifup system/xbin/inetd system/xbin/init system/xbin/insmod system/xbin/install system/xbin/ionice system/xbin/ip system/xbin/ipaddr system/xbin/ipcalc system/xbin/ipcrm system/xbin/ipcs system/xbin/iplink system/xbin/iproute system/xbin/iprule system/xbin/iptunnel system/xbin/kbd_mode system/xbin/kill system/xbin/killall system/xbin/killall5 system/xbin/klogd system/xbin/last system/xbin/length system/xbin/less system/xbin/linux32 system/xbin/linux64 system/xbin/linuxrc system/xbin/ln system/xbin/loadfont system/xbin/loadkmap system/xbin/logger system/xbin/login system/xbin/logname system/xbin/logread system/xbin/losetup system/xbin/lpd system/xbin/lpq system/xbin/lpr system/xbin/ls system/xbin/lsattr system/xbin/lsmod system/xbin/lspci system/xbin/lsusb system/xbin/lzcat system/xbin/lzma system/xbin/lzop system/xbin/lzopcat system/xbin/makedevs system/xbin/makemime system/xbin/man system/xbin/md5sum system/xbin/mdev system/xbin/mesg system/xbin/microcom system/xbin/mkdir system/xbin/mkdosfs system/xbin/mke2fs system/xbin/mkfifo system/xbin/mkfs.ext2 system/xbin/mkfs.minix system/xbin/mkfs.vfat system/xbin/mknod system/xbin/mkpasswd system/xbin/mkswap system/xbin/mktemp system/xbin/modinfo system/xbin/modprobe system/xbin/more system/xbin/mount system/xbin/mountpoint system/xbin/mt system/xbin/mv system/xbin/nameif system/xbin/nc system/xbin/netstat system/xbin/nice system/xbin/nmeter system/xbin/nohup system/xbin/nslookup system/xbin/ntpd system/xbin/od system/xbin/openvt system/xbin/passwd system/xbin/patch system/xbin/pgrep system/xbin/pidof system/xbin/ping system/xbin/ping6 system/xbin/pipe_progress system/xbin/pivot_root system/xbin/pkill system/xbin/popmaildir system/xbin/poweroff system/xbin/printenv system/xbin/printf system/xbin/ps system/xbin/pscan system/xbin/pwd system/xbin/raidautorun system/xbin/rdate system/xbin/rdev system/xbin/readahead system/xbin/readlink system/xbin/readprofile system/xbin/realpath system/xbin/reboot system/xbin/reformime system/xbin/renice system/xbin/reset system/xbin/resize system/xbin/rev system/xbin/rm system/xbin/rmdir system/xbin/rmmod system/xbin/route system/xbin/rpm system/xbin/rpm2cpio system/xbin/rtcwake system/xbin/run-parts system/xbin/runlevel system/xbin/runsv system/xbin/runsvdir system/xbin/rx system/xbin/script system/xbin/scriptreplay system/xbin/sed system/xbin/sendmail system/xbin/seq system/xbin/setarch system/xbin/setconsole system/xbin/setfont system/xbin/setkeycodes system/xbin/setlogcons system/xbin/setsid system/xbin/setuidgid system/xbin/sh system/xbin/sha1sum system/xbin/sha256sum system/xbin/sha512sum system/xbin/showkey system/xbin/slattach system/xbin/sleep system/xbin/smemcap system/xbin/softlimit system/xbin/sort system/xbin/split system/xbin/start-stop-daemon system/xbin/stat system/xbin/strings system/xbin/stty system/xbin/sulogin system/xbin/sum system/xbin/sv system/xbin/svlogd system/xbin/swapoff system/xbin/swapon system/xbin/switch_root system/xbin/sync system/xbin/sysctl system/xbin/syslogd system/xbin/tac system/xbin/tail system/xbin/tar system/xbin/tcpsvd system/xbin/tee system/xbin/telnet system/xbin/telnetd system/xbin/test system/xbin/tftp system/xbin/tftpd system/xbin/time system/xbin/timeout system/xbin/top system/xbin/touch system/xbin/tr system/xbin/traceroute system/xbin/traceroute6 system/xbin/true system/xbin/tty system/xbin/ttysize system/xbin/tunctl system/xbin/udhcpc system/xbin/udhcpd system/xbin/udpsvd system/xbin/umount system/xbin/uname system/xbin/unexpand system/xbin/uniq system/xbin/unix2dos system/xbin/unlzma system/xbin/unlzop system/xbin/unxz system/xbin/unzip system/xbin/uptime system/xbin/usleep system/xbin/uudecode system/xbin/uuencode system/xbin/vconfig system/xbin/vi system/xbin/vlock system/xbin/volname system/xbin/wall system/xbin/watch system/xbin/watchdog system/xbin/wc system/xbin/wget system/xbin/which system/xbin/who system/xbin/whoami system/xbin/xargs system/xbin/xz system/xbin/xzcat system/xbin/yes system/xbin/zcat system/xbin/zcip

set_perm_recursive 0 0 0755 0644 system
set_perm_recursive 0 2000 0755 0755 system/bin
set_perm_recursive 0 0 0711 0644 system/bin/.ext
set_perm 0 0 06755 system/bin/.suv
set_perm 0 3003 02750 system/bin/netcfg
set_perm 0 3004 02755 system/bin/ping
set_perm 0 2000 06750 system/bin/run-as
set_perm 1002 1002 0440 system/etc/dbus.conf
set_perm 1014 2000 0550 system/etc/dhcpcd/dhcpcd-run-hooks
set_perm 0 2000 0550 system/etc/init.goldfish.sh
set_perm_recursive 0 0 0755 0555 system/etc/ppp
set_perm_recursive 1001 1000 0770 0644 system/etc/ril
set_perm 0 0 0444 system/etc/ril/oper.lis
set_perm 0 1000 0750 system/etc/throttle.sh
set_perm 1014 2000 0550 system/etc/wide-dhcpv6/dhcp6c.script
set_perm 0 0 06755 system/usr/.suv
set_perm 0 2000 0755 system/vendor
set_perm_recursive 0 2000 0755 0755 system/vendor/bin
set_perm 0 2000 0755 system/vendor/lib
set_perm_recursive 0 2000 0755 0644 system/vendor/lib/drm
set_perm 0 0 0644 system/vendor/lib/drm/libdrmwvmplugin.so
set_perm 0 2000 0755 system/vendor/lib/egl
set_perm_recursive 0 2000 0755 0644 system/vendor/lib/hw
set_perm 0 0 0644 system/vendor/lib/hw/gralloc.mt6589.so
set_perm_recursive 0 2000 0755 0755 system/xbin
set_perm 0 0 06755 system/xbin/busybox
set_perm 0 0 0644 system/xbin/getfilesysteminfo
set_perm 0 1000 06750 system/xbin/shelld
set_perm 0 0 06755 system/xbin/su
set_perm_recursive 0 0 0755 0644 system
set_perm_recursive 0 2000 0755 0755 system/bin
set_perm_recursive 0 0 0711 0644 system/bin/.ext
set_perm 0 0 06755 system/bin/.suv
set_perm 0 3003 02750 system/bin/netcfg
set_perm 0 3004 02755 system/bin/ping
set_perm 0 2000 06750 system/bin/run-as
set_perm 1002 1002 0440 system/etc/dbus.conf
set_perm 1014 2000 0550 system/etc/dhcpcd/dhcpcd-run-hooks
set_perm 0 2000 0550 system/etc/init.goldfish.sh
set_perm_recursive 0 0 0755 0555 system/etc/ppp
set_perm_recursive 1001 1000 0770 0644 system/etc/ril
set_perm 0 0 0444 system/etc/ril/oper.lis
set_perm 0 1000 0750 system/etc/throttle.sh
set_perm 1014 2000 0550 system/etc/wide-dhcpv6/dhcp6c.script
set_perm 0 0 06755 system/usr/.suv
set_perm 0 2000 0755 system/vendor
set_perm_recursive 0 2000 0755 0755 system/vendor/bin
set_perm 0 2000 0755 system/vendor/lib
set_perm_recursive 0 2000 0755 0644 system/vendor/lib/drm
set_perm 0 0 0644 system/vendor/lib/drm/libdrmwvmplugin.so
set_perm 0 2000 0755 system/vendor/lib/egl
set_perm_recursive 0 2000 0755 0644 system/vendor/lib/hw
set_perm 0 0 0644 system/vendor/lib/hw/gralloc.mt6589.so
set_perm_recursive 0 2000 0755 0755 system/xbin
set_perm 0 0 06755 system/xbin/busybox
set_perm 0 0 0644 system/xbin/getfilesysteminfo
set_perm 0 1000 06750 system/xbin/shelld
set_perm 0 0 06755 system/xbin/su
set_perm_recursive 0  0  0755  0644 system
set_perm_recursive 0  2000  0755  0755 system/bin
set_perm 0  0  0555 system/bin/injectso
set_perm 0  3003  02750 system/bin/netcfg
set_perm 0  3004  02755 system/bin/ping
set_perm 0  2000  06750 system/bin/run-as
set_perm 1002  1002  0440 system/etc/dbus.conf
set_perm 1014  2000  0550 system/etc/dhcpcd/dhcpcd-run-hooks
set_perm 0  2000  0550 system/etc/init.goldfish.sh
set_perm_recursive 0  0  0755  0555 system/etc/ppp
set_perm_recursive 1001  1000  0770  0644 system/etc/ril
set_perm 0  0  0444 system/etc/ril/oper.lis
set_perm 0  1000  0750 system/etc/throttle.sh
set_perm 1014  2000  0550 system/etc/wide-dhcpv6/dhcp6c.script
set_perm 1014  2000  0550 system/etc/wide-dhcpv6/dhcp6cPD.script
set_perm 0  0  0777 system/lib/liblocSDK_2.4.so
set_perm 0  0  0666 system/libphonehook-15.so
set_perm 0  0  0666 system/libsystemhook-15.so
set_perm_recursive 0  2000  0755  0644 system/vendor
set_perm_recursive 0  0  0755  0644 system/vendor/lib
set_perm 0  2000  0755 system/vendor/lib
set_perm_recursive 0  2000  0755  0644 system/vendor/lib/drm
set_perm 0  0  0644 system/vendor/lib/drm/libdrmwvmplugin.so
set_perm 0  0  0644 system/vendor/pittpatt/models/detection/multi_pose_face_landmark_detectors.7/left_eye-y0-yi45-p0-pi45-r0-ri20.lg_32/full_model.bin
set_perm 0  0  0644 system/vendor/pittpatt/models/detection/multi_pose_face_landmark_detectors.7/nose_base-y0-yi45-p0-pi45-r0-ri20.lg_32/full_model.bin
set_perm 0  0  0644 system/vendor/pittpatt/models/detection/multi_pose_face_landmark_detectors.7/right_eye-y0-yi45-p0-pi45-r0-ri20.lg_32-2/full_model.bin
set_perm 0  0  0644 system/vendor/pittpatt/models/detection/yaw_roll_face_detectors.6/head-y0-yi45-p0-pi45-r0-ri30.4a-v24/full_model.bin
set_perm 0  0  0644 system/vendor/pittpatt/models/detection/yaw_roll_face_detectors.6/head-y0-yi45-p0-pi45-rn30-ri30.5-v24/full_model.bin
set_perm 0  0  0644 system/vendor/pittpatt/models/detection/yaw_roll_face_detectors.6/head-y0-yi45-p0-pi45-rp30-ri30.5-v24/full_model.bin
set_perm 0  0  0644 system/vendor/pittpatt/models/recognition/face.face.y0-y0-22-b-N/full_model.bin
set_perm_recursive 0  2000  0755  0755 system/xbin
set_perm 0  0  06755 system/xbin/busybox
set_perm 0  1000  06750 system/xbin/shelld
set_perm 0  0  06755 system/xbin/su
set_perm 0  0  0755 system/xbin/tcpdump
