```
[root@localhost repo]# yum update -y
Loaded plugins: ulninfo
Resolving Dependencies
--> Running transaction check
---> Package NetworkManager.x86_64 1:1.18.8-1.el7 will be updated
---> Package NetworkManager.x86_64 1:1.18.8-2.el7_9 will be an update
---> Package NetworkManager-config-server.noarch 1:1.18.8-1.el7 will be updated
---> Package NetworkManager-config-server.noarch 1:1.18.8-2.el7_9 will be an update
---> Package NetworkManager-libnm.x86_64 1:1.18.8-1.el7 will be updated
---> Package NetworkManager-libnm.x86_64 1:1.18.8-2.el7_9 will be an update
---> Package NetworkManager-team.x86_64 1:1.18.8-1.el7 will be updated
---> Package NetworkManager-team.x86_64 1:1.18.8-2.el7_9 will be an update
---> Package NetworkManager-tui.x86_64 1:1.18.8-1.el7 will be updated
---> Package NetworkManager-tui.x86_64 1:1.18.8-2.el7_9 will be an update
---> Package bind-export-libs.x86_64 32:9.11.4-26.P2.el7 will be updated
---> Package bind-export-libs.x86_64 32:9.11.4-26.P2.el7_9.7 will be an update
---> Package binutils.x86_64 0:2.27-44.base.0.1.el7 will be updated
---> Package binutils.x86_64 0:2.27-44.base.0.3.el7 will be an update
---> Package btrfs-progs.x86_64 0:4.9.1-1.0.2.el7 will be updated
---> Package btrfs-progs.x86_64 0:5.12.1-1.el7 will be an update
--> Processing Dependency: libzstd.so.1()(64bit) for package: btrfs-progs-5.12.1-1.el7.x86_64
---> Package ca-certificates.noarch 0:2020.2.41-70.0.el7_8 will be updated
---> Package ca-certificates.noarch 0:2021.2.50-72.el7_9 will be an update
---> Package coreutils.x86_64 0:8.22-24.0.1.el7 will be updated
---> Package coreutils.x86_64 0:8.22-24.0.1.el7_9.2 will be an update
---> Package curl.x86_64 0:7.29.0-59.0.1.el7 will be updated
---> Package curl.x86_64 0:7.29.0-59.0.3.el7_9.1 will be an update
---> Package device-mapper.x86_64 7:1.02.170-6.0.3.el7 will be updated
---> Package device-mapper.x86_64 7:1.02.170-6.0.5.el7_9.5 will be an update
---> Package device-mapper-event.x86_64 7:1.02.170-6.0.3.el7 will be updated
---> Package device-mapper-event.x86_64 7:1.02.170-6.0.5.el7_9.5 will be an update
---> Package device-mapper-event-libs.x86_64 7:1.02.170-6.0.3.el7 will be updated
---> Package device-mapper-event-libs.x86_64 7:1.02.170-6.0.5.el7_9.5 will be an update
---> Package device-mapper-libs.x86_64 7:1.02.170-6.0.3.el7 will be updated
---> Package device-mapper-libs.x86_64 7:1.02.170-6.0.5.el7_9.5 will be an update
---> Package device-mapper-persistent-data.x86_64 0:0.8.5-3.el7 will be updated
---> Package device-mapper-persistent-data.x86_64 0:0.8.5-3.el7_9.2 will be an update
---> Package dhclient.x86_64 12:4.2.5-82.0.1.el7 will be updated
---> Package dhclient.x86_64 12:4.2.5-83.0.1.el7_9.1 will be an update
---> Package dhcp-common.x86_64 12:4.2.5-82.0.1.el7 will be updated
---> Package dhcp-common.x86_64 12:4.2.5-83.0.1.el7_9.1 will be an update
---> Package dhcp-libs.x86_64 12:4.2.5-82.0.1.el7 will be updated
---> Package dhcp-libs.x86_64 12:4.2.5-83.0.1.el7_9.1 will be an update
---> Package dmidecode.x86_64 1:3.2-5.el7 will be updated
---> Package dmidecode.x86_64 1:3.2-5.0.1.el7_9.1 will be an update
---> Package dracut.x86_64 0:033-572.0.1.el7 will be updated
---> Package dracut.x86_64 0:033-572.0.3.el7 will be an update
---> Package dracut-config-rescue.x86_64 0:033-572.0.1.el7 will be updated
---> Package dracut-config-rescue.x86_64 0:033-572.0.3.el7 will be an update
---> Package dracut-network.x86_64 0:033-572.0.1.el7 will be updated
---> Package dracut-network.x86_64 0:033-572.0.3.el7 will be an update
---> Package e2fsprogs.x86_64 0:1.42.9-19.el7 will be updated
---> Package e2fsprogs.x86_64 0:1.45.4-3.0.5.el7 will be an update
--> Processing Dependency: libfuse.so.2(FUSE_2.8)(64bit) for package: e2fsprogs-1.45.4-3.0.5.el7.x86_64
--> Processing Dependency: libfuse.so.2(FUSE_2.6)(64bit) for package: e2fsprogs-1.45.4-3.0.5.el7.x86_64
--> Processing Dependency: libfuse.so.2(FUSE_2.5)(64bit) for package: e2fsprogs-1.45.4-3.0.5.el7.x86_64
--> Processing Dependency: libfuse.so.2()(64bit) for package: e2fsprogs-1.45.4-3.0.5.el7.x86_64
---> Package e2fsprogs-libs.x86_64 0:1.42.9-19.el7 will be updated
---> Package e2fsprogs-libs.x86_64 0:1.45.4-3.0.5.el7 will be an update
---> Package firewalld.noarch 0:0.6.3-11.0.1.el7 will be updated
---> Package firewalld.noarch 0:0.6.3-13.0.1.el7_9 will be an update
---> Package firewalld-filesystem.noarch 0:0.6.3-11.0.1.el7 will be updated
---> Package firewalld-filesystem.noarch 0:0.6.3-13.0.1.el7_9 will be an update
---> Package freetype.x86_64 0:2.8-14.el7 will be updated
---> Package freetype.x86_64 0:2.8-14.el7_9.1 will be an update
---> Package glib2.x86_64 0:2.56.1-7.el7 will be updated
---> Package glib2.x86_64 0:2.56.1-9.el7_9 will be an update
---> Package grub2.x86_64 1:2.02-0.87.0.1.el7 will be updated
---> Package grub2.x86_64 1:2.02-0.87.0.13.el7_9.6 will be an update
---> Package grub2-common.noarch 1:2.02-0.87.0.1.el7 will be updated
---> Package grub2-common.noarch 1:2.02-0.87.0.13.el7_9.6 will be an update
---> Package grub2-pc.x86_64 1:2.02-0.87.0.1.el7 will be updated
---> Package grub2-pc.x86_64 1:2.02-0.87.0.13.el7_9.6 will be an update
---> Package grub2-pc-modules.noarch 1:2.02-0.87.0.1.el7 will be updated
---> Package grub2-pc-modules.noarch 1:2.02-0.87.0.13.el7_9.6 will be an update
---> Package grub2-tools.x86_64 1:2.02-0.87.0.1.el7 will be updated
---> Package grub2-tools.x86_64 1:2.02-0.87.0.13.el7_9.6 will be an update
---> Package grub2-tools-extra.x86_64 1:2.02-0.87.0.1.el7 will be updated
---> Package grub2-tools-extra.x86_64 1:2.02-0.87.0.13.el7_9.6 will be an update
---> Package grub2-tools-minimal.x86_64 1:2.02-0.87.0.1.el7 will be updated
---> Package grub2-tools-minimal.x86_64 1:2.02-0.87.0.13.el7_9.6 will be an update
---> Package hwdata.x86_64 0:0.252-9.7.el7 will be updated
---> Package hwdata.x86_64 0:0.252-9.7.0.1.el7 will be an update
---> Package initscripts.x86_64 0:9.49.53-1.0.1.el7 will be updated
---> Package initscripts.x86_64 0:9.49.53-1.0.1.el7_9.1 will be an update
---> Package iproute.x86_64 0:4.11.0-30.el7 will be updated
---> Package iproute.x86_64 0:5.4.0-1.0.1.el7 will be an update
---> Package iprutils.x86_64 0:2.4.17.1-3.el7 will be updated
---> Package iprutils.x86_64 0:2.4.17.1-3.el7_7 will be an update
---> Package iwl100-firmware.noarch 999:39.31.5.1-999.5.el7 will be updated
---> Package iwl100-firmware.noarch 999:39.31.5.1-999.8.el7 will be an update
---> Package iwl1000-firmware.noarch 999:39.31.5.1-999.5.el7 will be updated
---> Package iwl1000-firmware.noarch 999:39.31.5.1-999.8.el7 will be an update
---> Package iwl105-firmware.noarch 999:18.168.6.1-999.5.el7 will be updated
---> Package iwl105-firmware.noarch 999:18.168.6.1-999.8.el7 will be an update
---> Package iwl135-firmware.noarch 999:18.168.6.1-999.5.el7 will be updated
---> Package iwl135-firmware.noarch 999:18.168.6.1-999.8.el7 will be an update
---> Package iwl2000-firmware.noarch 999:18.168.6.1-999.5.el7 will be updated
---> Package iwl2000-firmware.noarch 999:18.168.6.1-999.8.el7 will be an update
---> Package iwl2030-firmware.noarch 999:18.168.6.1-999.5.el7 will be updated
---> Package iwl2030-firmware.noarch 999:18.168.6.1-999.8.el7 will be an update
---> Package iwl3160-firmware.noarch 999:22.0.7.0-999.5.el7 will be updated
---> Package iwl3160-firmware.noarch 999:22.0.7.0-999.8.el7 will be an update
---> Package iwl3945-firmware.noarch 999:15.32.2.9-999.5.el7 will be updated
---> Package iwl3945-firmware.noarch 999:15.32.2.9-999.8.el7 will be an update
---> Package iwl4965-firmware.noarch 999:228.61.2.24-999.5.el7 will be updated
---> Package iwl4965-firmware.noarch 999:228.61.2.24-999.8.el7 will be an update
---> Package iwl5000-firmware.noarch 999:8.83.5.1_1-999.5.el7 will be updated
---> Package iwl5000-firmware.noarch 999:8.83.5.1_1-999.8.el7 will be an update
---> Package iwl5150-firmware.noarch 999:8.24.2.2-999.5.el7 will be updated
---> Package iwl5150-firmware.noarch 999:8.24.2.2-999.8.el7 will be an update
---> Package iwl6000-firmware.noarch 999:9.221.4.1-999.5.el7 will be updated
---> Package iwl6000-firmware.noarch 999:9.221.4.1-999.8.el7 will be an update
---> Package iwl6000g2a-firmware.noarch 999:17.168.5.3-999.5.el7 will be updated
---> Package iwl6000g2a-firmware.noarch 999:17.168.5.3-999.8.el7 will be an update
---> Package iwl6000g2b-firmware.noarch 999:17.168.5.2-999.5.el7 will be updated
---> Package iwl6000g2b-firmware.noarch 999:17.168.5.2-999.8.el7 will be an update
---> Package iwl6050-firmware.noarch 999:41.28.5.1-999.5.el7 will be updated
---> Package iwl6050-firmware.noarch 999:41.28.5.1-999.8.el7 will be an update
---> Package iwl7260-firmware.noarch 999:22.0.7.0-999.5.el7 will be updated
---> Package iwl7260-firmware.noarch 999:22.0.7.0-999.8.el7 will be an update
---> Package kernel.x86_64 0:3.10.0-1160.42.2.el7 will be installed
---> Package kernel-tools.x86_64 0:3.10.0-1160.el7 will be updated
---> Package kernel-tools.x86_64 0:3.10.0-1160.42.2.el7 will be an update
---> Package kernel-tools-libs.x86_64 0:3.10.0-1160.el7 will be updated
---> Package kernel-tools-libs.x86_64 0:3.10.0-1160.42.2.el7 will be an update
---> Package kernel-uek.x86_64 0:5.4.17-2102.205.7.3.el7uek will be installed
---> Package kexec-tools.x86_64 0:2.0.15-51.0.1.el7 will be updated
---> Package kexec-tools.x86_64 0:2.0.15-51.0.3.el7_9.3 will be an update
---> Package kpartx.x86_64 0:0.4.9-133.0.1.el7 will be updated
---> Package kpartx.x86_64 0:0.4.9-135.0.1.el7_9 will be an update
---> Package krb5-libs.x86_64 0:1.15.1-50.el7 will be updated
---> Package krb5-libs.x86_64 0:1.15.1-50.0.1.el7 will be an update
---> Package libblkid.x86_64 0:2.23.2-65.0.1.el7 will be updated
---> Package libblkid.x86_64 0:2.23.2-65.0.1.el7_9.1 will be an update
---> Package libcom_err.x86_64 0:1.42.9-19.el7 will be updated
---> Package libcom_err.x86_64 0:1.45.4-3.0.5.el7 will be an update
---> Package libcroco.x86_64 0:0.6.12-4.el7 will be updated
---> Package libcroco.x86_64 0:0.6.12-6.el7_9 will be an update
---> Package libcurl.x86_64 0:7.29.0-59.0.1.el7 will be updated
---> Package libcurl.x86_64 0:7.29.0-59.0.3.el7_9.1 will be an update
---> Package libgudev1.x86_64 0:219-78.0.1.el7 will be updated
---> Package libgudev1.x86_64 0:219-78.0.7.el7_9.3 will be an update
---> Package libmount.x86_64 0:2.23.2-65.0.1.el7 will be updated
---> Package libmount.x86_64 0:2.23.2-65.0.1.el7_9.1 will be an update
---> Package libsmartcols.x86_64 0:2.23.2-65.0.1.el7 will be updated
---> Package libsmartcols.x86_64 0:2.23.2-65.0.1.el7_9.1 will be an update
---> Package libss.x86_64 0:1.42.9-19.el7 will be updated
---> Package libss.x86_64 0:1.45.4-3.0.5.el7 will be an update
---> Package libuuid.x86_64 0:2.23.2-65.0.1.el7 will be updated
---> Package libuuid.x86_64 0:2.23.2-65.0.1.el7_9.1 will be an update
---> Package libxml2.x86_64 0:2.9.1-6.0.1.el7.5 will be updated
---> Package libxml2.x86_64 0:2.9.1-6.0.3.el7.5 will be an update
---> Package libxml2-python.x86_64 0:2.9.1-6.0.1.el7.5 will be updated
---> Package libxml2-python.x86_64 0:2.9.1-6.0.3.el7.5 will be an update
---> Package linux-firmware.noarch 999:20200902-999.5.gitd5f9eea5.el7 will be updated
---> Package linux-firmware.noarch 999:20210617-999.8.git0f66b74b.el7 will be an update
---> Package lvm2.x86_64 7:2.02.187-6.0.3.el7 will be updated
---> Package lvm2.x86_64 7:2.02.187-6.0.5.el7_9.5 will be an update
---> Package lvm2-libs.x86_64 7:2.02.187-6.0.3.el7 will be updated
---> Package lvm2-libs.x86_64 7:2.02.187-6.0.5.el7_9.5 will be an update
---> Package microcode_ctl.x86_64 2:2.1-73.0.1.el7 will be updated
---> Package microcode_ctl.x86_64 2:2.1-73.11.0.1.el7_9 will be an update
---> Package nspr.x86_64 0:4.21.0-1.el7 will be updated
---> Package nspr.x86_64 0:4.25.0-2.el7_9 will be an update
---> Package nss.x86_64 0:3.44.0-7.el7_7 will be updated
---> Package nss.x86_64 0:3.53.1-7.el7_9 will be an update
---> Package nss-softokn.x86_64 0:3.44.0-8.0.1.el7_7 will be updated
---> Package nss-softokn.x86_64 0:3.53.1-6.0.1.el7_9 will be an update
---> Package nss-softokn-freebl.x86_64 0:3.44.0-8.0.1.el7_7 will be updated
---> Package nss-softokn-freebl.x86_64 0:3.53.1-6.0.1.el7_9 will be an update
---> Package nss-sysinit.x86_64 0:3.44.0-7.el7_7 will be updated
---> Package nss-sysinit.x86_64 0:3.53.1-7.el7_9 will be an update
---> Package nss-tools.x86_64 0:3.44.0-7.el7_7 will be updated
---> Package nss-tools.x86_64 0:3.53.1-7.el7_9 will be an update
---> Package nss-util.x86_64 0:3.44.0-4.el7_7 will be updated
---> Package nss-util.x86_64 0:3.53.1-1.el7_9 will be an update
---> Package numactl-libs.x86_64 0:2.0.12-5.el7 will be updated
---> Package numactl-libs.x86_64 0:2.0.12-5.0.3.el7 will be an update
---> Package openldap.x86_64 0:2.4.44-22.el7 will be updated
---> Package openldap.x86_64 0:2.4.44-24.el7_9 will be an update
---> Package openssl.x86_64 1:1.0.2k-19.0.1.el7 will be updated
---> Package openssl.x86_64 1:1.0.2k-21.0.3.el7_9 will be an update
---> Package openssl-libs.x86_64 1:1.0.2k-19.0.1.el7 will be updated
---> Package openssl-libs.x86_64 1:1.0.2k-21.0.3.el7_9 will be an update
---> Package pciutils.x86_64 0:3.5.1-3.el7 will be updated
---> Package pciutils.x86_64 0:3.5.1-3.0.1.el7 will be an update
---> Package pciutils-libs.x86_64 0:3.5.1-3.el7 will be updated
---> Package pciutils-libs.x86_64 0:3.5.1-3.0.1.el7 will be an update
---> Package python.x86_64 0:2.7.5-89.0.1.el7 will be updated
---> Package python.x86_64 0:2.7.5-90.0.3.el7 will be an update
---> Package python-firewall.noarch 0:0.6.3-11.0.1.el7 will be updated
---> Package python-firewall.noarch 0:0.6.3-13.0.1.el7_9 will be an update
---> Package python-libs.x86_64 0:2.7.5-89.0.1.el7 will be updated
---> Package python-libs.x86_64 0:2.7.5-90.0.3.el7 will be an update
---> Package python-perf.x86_64 0:3.10.0-1160.el7 will be updated
---> Package python-perf.x86_64 0:3.10.0-1160.42.2.el7 will be an update
---> Package redhat-release-server.x86_64 1:7.9-3.0.1.el7 will be updated
---> Package redhat-release-server.x86_64 1:7.9-6.0.1.el7_9 will be an update
---> Package rsyslog.x86_64 0:8.24.0-55.el7 will be updated
---> Package rsyslog.x86_64 0:8.24.0-57.0.1.el7_9.1 will be an update
---> Package selinux-policy.noarch 0:3.13.1-268.0.1.el7 will be updated
---> Package selinux-policy.noarch 0:3.13.1-268.0.13.el7_9.2 will be an update
---> Package selinux-policy-targeted.noarch 0:3.13.1-268.0.1.el7 will be updated
---> Package selinux-policy-targeted.noarch 0:3.13.1-268.0.13.el7_9.2 will be an update
---> Package sudo.x86_64 0:1.8.23-10.el7 will be updated
---> Package sudo.x86_64 0:1.8.23-10.el7_9.1 will be an update
---> Package systemd.x86_64 0:219-78.0.1.el7 will be updated
---> Package systemd.x86_64 0:219-78.0.7.el7_9.3 will be an update
---> Package systemd-libs.x86_64 0:219-78.0.1.el7 will be updated
---> Package systemd-libs.x86_64 0:219-78.0.7.el7_9.3 will be an update
---> Package systemd-sysv.x86_64 0:219-78.0.1.el7 will be updated
---> Package systemd-sysv.x86_64 0:219-78.0.7.el7_9.3 will be an update
---> Package tuned.noarch 0:2.11.0-9.0.3.el7 will be updated
---> Package tuned.noarch 0:2.11.0-11.0.1.el7_9 will be an update
---> Package tzdata.noarch 0:2020a-1.el7 will be updated
---> Package tzdata.noarch 0:2021a-1.el7 will be an update
---> Package util-linux.x86_64 0:2.23.2-65.0.1.el7 will be updated
---> Package util-linux.x86_64 0:2.23.2-65.0.1.el7_9.1 will be an update
---> Package vim-minimal.x86_64 2:7.4.629-7.0.1.el7 will be updated
---> Package vim-minimal.x86_64 2:7.4.629-8.0.1.el7_9 will be an update
---> Package virt-what.x86_64 0:1.18-4.el7 will be updated
---> Package virt-what.x86_64 0:1.18-4.el7_9.1 will be an update
---> Package wpa_supplicant.x86_64 1:2.6-12.el7 will be updated
---> Package wpa_supplicant.x86_64 1:2.6-12.el7_9.2 will be an update
---> Package xfsprogs.x86_64 0:4.5.0-22.0.1.el7 will be updated
---> Package xfsprogs.x86_64 0:5.4.0-1.0.1.el7 will be an update
---> Package zlib.x86_64 0:1.2.7-18.el7 will be updated
---> Package zlib.x86_64 0:1.2.7-19.el7_9 will be an update
--> Running transaction check
---> Package fuse-libs.x86_64 0:2.9.4-1.0.9.el7 will be installed
---> Package libzstd.x86_64 0:1.4.4-1.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

=====================================================================================================
 Package                        Arch    Version                              Repository         Size
=====================================================================================================
Installing:
 kernel                         x86_64  3.10.0-1160.42.2.el7                 local-repo-ol7     50 M
 kernel-uek                     x86_64  5.4.17-2102.205.7.3.el7uek           local-repo-uekr6   63 M
Updating:
 NetworkManager                 x86_64  1:1.18.8-2.el7_9                     local-repo-ol7    1.9 M
 NetworkManager-config-server   noarch  1:1.18.8-2.el7_9                     local-repo-ol7    151 k
 NetworkManager-libnm           x86_64  1:1.18.8-2.el7_9                     local-repo-ol7    1.7 M
 NetworkManager-team            x86_64  1:1.18.8-2.el7_9                     local-repo-ol7    165 k
 NetworkManager-tui             x86_64  1:1.18.8-2.el7_9                     local-repo-ol7    328 k
 bind-export-libs               x86_64  32:9.11.4-26.P2.el7_9.7              local-repo-ol7    1.1 M
 binutils                       x86_64  2.27-44.base.0.3.el7                 local-repo-ol7    5.3 M
 btrfs-progs                    x86_64  5.12.1-1.el7                         local-repo-uekr6  833 k
 ca-certificates                noarch  2021.2.50-72.el7_9                   local-repo-ol7    379 k
 coreutils                      x86_64  8.22-24.0.1.el7_9.2                  local-repo-ol7    3.3 M
 curl                           x86_64  7.29.0-59.0.3.el7_9.1                local-repo-ol7    272 k
 device-mapper                  x86_64  7:1.02.170-6.0.5.el7_9.5             local-repo-ol7    297 k
 device-mapper-event            x86_64  7:1.02.170-6.0.5.el7_9.5             local-repo-ol7    192 k
 device-mapper-event-libs       x86_64  7:1.02.170-6.0.5.el7_9.5             local-repo-ol7    192 k
 device-mapper-libs             x86_64  7:1.02.170-6.0.5.el7_9.5             local-repo-ol7    325 k
 device-mapper-persistent-data  x86_64  0.8.5-3.el7_9.2                      local-repo-ol7    422 k
 dhclient                       x86_64  12:4.2.5-83.0.1.el7_9.1              local-repo-ol7    286 k
 dhcp-common                    x86_64  12:4.2.5-83.0.1.el7_9.1              local-repo-ol7    176 k
 dhcp-libs                      x86_64  12:4.2.5-83.0.1.el7_9.1              local-repo-ol7    133 k
 dmidecode                      x86_64  1:3.2-5.0.1.el7_9.1                  local-repo-ol7     82 k
 dracut                         x86_64  033-572.0.3.el7                      local-repo-ol7    331 k
 dracut-config-rescue           x86_64  033-572.0.3.el7                      local-repo-ol7     62 k
 dracut-network                 x86_64  033-572.0.3.el7                      local-repo-ol7    106 k
 e2fsprogs                      x86_64  1.45.4-3.0.5.el7                     local-repo-uekr6  1.0 M
 e2fsprogs-libs                 x86_64  1.45.4-3.0.5.el7                     local-repo-uekr6  222 k
 firewalld                      noarch  0.6.3-13.0.1.el7_9                   local-repo-ol7    449 k
 firewalld-filesystem           noarch  0.6.3-13.0.1.el7_9                   local-repo-ol7     51 k
 freetype                       x86_64  2.8-14.el7_9.1                       local-repo-ol7    380 k
 glib2                          x86_64  2.56.1-9.el7_9                       local-repo-ol7    2.5 M
 grub2                          x86_64  1:2.02-0.87.0.13.el7_9.6             local-repo-ol7     35 k
 grub2-common                   noarch  1:2.02-0.87.0.13.el7_9.6             local-repo-ol7    733 k
 grub2-pc                       x86_64  1:2.02-0.87.0.13.el7_9.6             local-repo-ol7     35 k
 grub2-pc-modules               noarch  1:2.02-0.87.0.13.el7_9.6             local-repo-ol7    860 k
 grub2-tools                    x86_64  1:2.02-0.87.0.13.el7_9.6             local-repo-ol7    1.8 M
 grub2-tools-extra              x86_64  1:2.02-0.87.0.13.el7_9.6             local-repo-ol7    1.0 M
 grub2-tools-minimal            x86_64  1:2.02-0.87.0.13.el7_9.6             local-repo-ol7    178 k
 hwdata                         x86_64  0.252-9.7.0.1.el7                    local-repo-ol7    2.5 M
 initscripts                    x86_64  9.49.53-1.0.1.el7_9.1                local-repo-ol7    443 k
 iproute                        x86_64  5.4.0-1.0.1.el7                      local-repo-uekr6  619 k
 iprutils                       x86_64  2.4.17.1-3.el7_7                     local-repo-ol7    242 k
 iwl100-firmware                noarch  999:39.31.5.1-999.8.el7              local-repo-ol7    152 k
 iwl1000-firmware               noarch  999:39.31.5.1-999.8.el7              local-repo-ol7    215 k
 iwl105-firmware                noarch  999:18.168.6.1-999.8.el7             local-repo-ol7    236 k
 iwl135-firmware                noarch  999:18.168.6.1-999.8.el7             local-repo-ol7    245 k
 iwl2000-firmware               noarch  999:18.168.6.1-999.8.el7             local-repo-ol7    239 k
 iwl2030-firmware               noarch  999:18.168.6.1-999.8.el7             local-repo-ol7    248 k
 iwl3160-firmware               noarch  999:22.0.7.0-999.8.el7               local-repo-ol7    1.7 M
 iwl3945-firmware               noarch  999:15.32.2.9-999.8.el7              local-repo-ol7     90 k
 iwl4965-firmware               noarch  999:228.61.2.24-999.8.el7            local-repo-ol7    103 k
 iwl5000-firmware               noarch  999:8.83.5.1_1-999.8.el7             local-repo-ol7    296 k
 iwl5150-firmware               noarch  999:8.24.2.2-999.8.el7               local-repo-ol7    149 k
 iwl6000-firmware               noarch  999:9.221.4.1-999.8.el7              local-repo-ol7    169 k
 iwl6000g2a-firmware            noarch  999:17.168.5.3-999.8.el7             local-repo-ol7    312 k
 iwl6000g2b-firmware            noarch  999:17.168.5.2-999.8.el7             local-repo-ol7    312 k
 iwl6050-firmware               noarch  999:41.28.5.1-999.8.el7              local-repo-ol7    245 k
 iwl7260-firmware               noarch  999:22.0.7.0-999.8.el7               local-repo-ol7     18 M
 kernel-tools                   x86_64  3.10.0-1160.42.2.el7                 local-repo-ol7    8.1 M
 kernel-tools-libs              x86_64  3.10.0-1160.42.2.el7                 local-repo-ol7    8.0 M
 kexec-tools                    x86_64  2.0.15-51.0.3.el7_9.3                local-repo-ol7    356 k
 kpartx                         x86_64  0.4.9-135.0.1.el7_9                  local-repo-ol7     81 k
 krb5-libs                      x86_64  1.15.1-50.0.1.el7                    local-repo-ol7    809 k
 libblkid                       x86_64  2.23.2-65.0.1.el7_9.1                local-repo-ol7    183 k
 libcom_err                     x86_64  1.45.4-3.0.5.el7                     local-repo-uekr6   44 k
 libcroco                       x86_64  0.6.12-6.el7_9                       local-repo-ol7    105 k
 libcurl                        x86_64  7.29.0-59.0.3.el7_9.1                local-repo-ol7    224 k
 libgudev1                      x86_64  219-78.0.7.el7_9.3                   local-repo-ol7    110 k
 libmount                       x86_64  2.23.2-65.0.1.el7_9.1                local-repo-ol7    185 k
 libsmartcols                   x86_64  2.23.2-65.0.1.el7_9.1                local-repo-ol7    142 k
 libss                          x86_64  1.45.4-3.0.5.el7                     local-repo-uekr6   48 k
 libuuid                        x86_64  2.23.2-65.0.1.el7_9.1                local-repo-ol7     84 k
 libxml2                        x86_64  2.9.1-6.0.3.el7.5                    local-repo-ol7    668 k
 libxml2-python                 x86_64  2.9.1-6.0.3.el7.5                    local-repo-ol7    247 k
 linux-firmware                 noarch  999:20210617-999.8.git0f66b74b.el7   local-repo-ol7    173 M
 lvm2                           x86_64  7:2.02.187-6.0.5.el7_9.5             local-repo-ol7    1.3 M
 lvm2-libs                      x86_64  7:2.02.187-6.0.5.el7_9.5             local-repo-ol7    1.1 M
 microcode_ctl                  x86_64  2:2.1-73.11.0.1.el7_9                local-repo-ol7    4.2 M
 nspr                           x86_64  4.25.0-2.el7_9                       local-repo-ol7    126 k
 nss                            x86_64  3.53.1-7.el7_9                       local-repo-ol7    868 k
 nss-softokn                    x86_64  3.53.1-6.0.1.el7_9                   local-repo-ol7    354 k
 nss-softokn-freebl             x86_64  3.53.1-6.0.1.el7_9                   local-repo-ol7    322 k
 nss-sysinit                    x86_64  3.53.1-7.el7_9                       local-repo-ol7     65 k
 nss-tools                      x86_64  3.53.1-7.el7_9                       local-repo-ol7    535 k
 nss-util                       x86_64  3.53.1-1.el7_9                       local-repo-ol7     79 k
 numactl-libs                   x86_64  2.0.12-5.0.3.el7                     local-repo-ol7     30 k
 openldap                       x86_64  2.4.44-24.el7_9                      local-repo-ol7    356 k
 openssl                        x86_64  1:1.0.2k-21.0.3.el7_9                local-repo-ol7    493 k
 openssl-libs                   x86_64  1:1.0.2k-21.0.3.el7_9                local-repo-ol7    1.2 M
 pciutils                       x86_64  3.5.1-3.0.1.el7                      local-repo-ol7     94 k
 pciutils-libs                  x86_64  3.5.1-3.0.1.el7                      local-repo-ol7     46 k
 python                         x86_64  2.7.5-90.0.3.el7                     local-repo-ol7     96 k
 python-firewall                noarch  0.6.3-13.0.1.el7_9                   local-repo-ol7    355 k
 python-libs                    x86_64  2.7.5-90.0.3.el7                     local-repo-ol7    5.6 M
 python-perf                    x86_64  3.10.0-1160.42.2.el7                 local-repo-ol7    8.1 M
 redhat-release-server          x86_64  1:7.9-6.0.1.el7_9                    local-repo-ol7     12 k
 rsyslog                        x86_64  8.24.0-57.0.1.el7_9.1                local-repo-ol7    621 k
 selinux-policy                 noarch  3.13.1-268.0.13.el7_9.2              local-repo-ol7    499 k
 selinux-policy-targeted        noarch  3.13.1-268.0.13.el7_9.2              local-repo-ol7    7.2 M
 sudo                           x86_64  1.8.23-10.el7_9.1                    local-repo-ol7    842 k
 systemd                        x86_64  219-78.0.7.el7_9.3                   local-repo-ol7    5.1 M
 systemd-libs                   x86_64  219-78.0.7.el7_9.3                   local-repo-ol7    419 k
 systemd-sysv                   x86_64  219-78.0.7.el7_9.3                   local-repo-ol7     98 k
 tuned                          noarch  2.11.0-11.0.1.el7_9                  local-repo-ol7    270 k
 tzdata                         noarch  2021a-1.el7                          local-repo-ol7    501 k
 util-linux                     x86_64  2.23.2-65.0.1.el7_9.1                local-repo-ol7    2.0 M
 vim-minimal                    x86_64  2:7.4.629-8.0.1.el7_9                local-repo-ol7    443 k
 virt-what                      x86_64  1.18-4.el7_9.1                       local-repo-ol7     29 k
 wpa_supplicant                 x86_64  1:2.6-12.el7_9.2                     local-repo-ol7    1.2 M
 xfsprogs                       x86_64  5.4.0-1.0.1.el7                      local-repo-uekr6  1.0 M
 zlib                           x86_64  1.2.7-19.el7_9                       local-repo-ol7     89 k
Installing for dependencies:
 fuse-libs                      x86_64  2.9.4-1.0.9.el7                      local-repo-ol7     97 k
 libzstd                        x86_64  1.4.4-1.el7                          local-repo-uekr6  259 k

Transaction Summary
=====================================================================================================
Install    2 Packages (+2 Dependent packages)
Upgrade  109 Packages

Total download size: 406 M
Downloading packages:
-----------------------------------------------------------------------------------------------------
Total                                                                254 MB/s | 406 MB  00:00:01
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Updating   : zlib-1.2.7-19.el7_9.x86_64                                                      1/222
  Updating   : systemd-libs-219-78.0.7.el7_9.3.x86_64                                          2/222
  Updating   : nspr-4.25.0-2.el7_9.x86_64                                                      3/222
  Updating   : nss-util-3.53.1-1.el7_9.x86_64                                                  4/222
  Updating   : libcom_err-1.45.4-3.0.5.el7.x86_64                                              5/222
  Updating   : libuuid-2.23.2-65.0.1.el7_9.1.x86_64                                            6/222
  Updating   : 1:grub2-common-2.02-0.87.0.13.el7_9.6.noarch                                    7/222
  Updating   : 1:redhat-release-server-7.9-6.0.1.el7_9.x86_64                                  8/222
  Updating   : iproute-5.4.0-1.0.1.el7.x86_64                                                  9/222
  Updating   : e2fsprogs-libs-1.45.4-3.0.5.el7.x86_64                                         10/222
  Updating   : libxml2-2.9.1-6.0.3.el7.5.x86_64                                               11/222
  Updating   : numactl-libs-2.0.12-5.0.3.el7.x86_64                                           12/222
  Updating   : pciutils-libs-3.5.1-3.0.1.el7.x86_64                                           13/222
  Installing : fuse-libs-2.9.4-1.0.9.el7.x86_64                                               14/222
  Updating   : 1:grub2-pc-modules-2.02-0.87.0.13.el7_9.6.noarch                               15/222
  Updating   : libss-1.45.4-3.0.5.el7.x86_64                                                  16/222
  Updating   : nss-softokn-freebl-3.53.1-6.0.1.el7_9.x86_64                                   17/222
  Updating   : nss-softokn-3.53.1-6.0.1.el7_9.x86_64                                          18/222
  Updating   : freetype-2.8-14.el7_9.1.x86_64                                                 19/222
  Updating   : 2:vim-minimal-7.4.629-8.0.1.el7_9.x86_64                                       20/222
  Updating   : kernel-tools-libs-3.10.0-1160.42.2.el7.x86_64                                  21/222
  Updating   : 1:dmidecode-3.2-5.0.1.el7_9.1.x86_64                                           22/222
  Updating   : firewalld-filesystem-0.6.3-13.0.1.el7_9.noarch                                 23/222
  Updating   : libsmartcols-2.23.2-65.0.1.el7_9.1.x86_64                                      24/222
  Updating   : ca-certificates-2021.2.50-72.el7_9.noarch                                      25/222
  Updating   : coreutils-8.22-24.0.1.el7_9.2.x86_64                                           26/222
  Updating   : 1:openssl-libs-1.0.2k-21.0.3.el7_9.x86_64                                      27/222
  Updating   : krb5-libs-1.15.1-50.0.1.el7.x86_64                                             28/222
  Updating   : libblkid-2.23.2-65.0.1.el7_9.1.x86_64                                          29/222
  Updating   : libmount-2.23.2-65.0.1.el7_9.1.x86_64                                          30/222
  Updating   : glib2-2.56.1-9.el7_9.x86_64                                                    31/222
  Updating   : util-linux-2.23.2-65.0.1.el7_9.1.x86_64                                        32/222
  Updating   : python-libs-2.7.5-90.0.3.el7.x86_64                                            33/222
  Updating   : python-2.7.5-90.0.3.el7.x86_64                                                 34/222
  Updating   : virt-what-1.18-4.el7_9.1.x86_64                                                35/222
  Updating   : 999:linux-firmware-20210617-999.8.git0f66b74b.el7.noarch                       36/222
  Updating   : python-perf-3.10.0-1160.42.2.el7.x86_64                                        37/222
  Updating   : python-firewall-0.6.3-13.0.1.el7_9.noarch                                      38/222
  Updating   : 32:bind-export-libs-9.11.4-26.P2.el7_9.7.x86_64                                39/222
  Updating   : selinux-policy-3.13.1-268.0.13.el7_9.2.noarch                                  40/222
  Updating   : nss-sysinit-3.53.1-7.el7_9.x86_64                                              41/222
  Updating   : nss-3.53.1-7.el7_9.x86_64                                                      42/222
  Updating   : 1:NetworkManager-libnm-1.18.8-2.el7_9.x86_64                                   43/222
  Updating   : nss-tools-3.53.1-7.el7_9.x86_64                                                44/222
  Updating   : openldap-2.4.44-24.el7_9.x86_64                                                45/222
  Updating   : libcurl-7.29.0-59.0.3.el7_9.1.x86_64                                           46/222
  Updating   : systemd-219-78.0.7.el7_9.3.x86_64                                              47/222
  Updating   : initscripts-9.49.53-1.0.1.el7_9.1.x86_64                                       48/222
  Updating   : 7:device-mapper-libs-1.02.170-6.0.5.el7_9.5.x86_64                             49/222
  Updating   : 7:device-mapper-1.02.170-6.0.5.el7_9.5.x86_64                                  50/222
  Updating   : 7:device-mapper-event-libs-1.02.170-6.0.5.el7_9.5.x86_64                       51/222
  Updating   : 1:grub2-tools-minimal-2.02-0.87.0.13.el7_9.6.x86_64                            52/222
  Updating   : 12:dhcp-libs-4.2.5-83.0.1.el7_9.1.x86_64                                       53/222
  Updating   : 12:dhcp-common-4.2.5-83.0.1.el7_9.1.x86_64                                     54/222
  Updating   : 12:dhclient-4.2.5-83.0.1.el7_9.1.x86_64                                        55/222
  Updating   : 7:device-mapper-event-1.02.170-6.0.5.el7_9.5.x86_64                            56/222
  Updating   : 7:lvm2-libs-2.02.187-6.0.5.el7_9.5.x86_64                                      57/222
  Updating   : kpartx-0.4.9-135.0.1.el7_9.x86_64                                              58/222
  Updating   : dracut-033-572.0.3.el7.x86_64                                                  59/222
  Updating   : 1:grub2-tools-2.02-0.87.0.13.el7_9.6.x86_64                                    60/222
  Updating   : 1:grub2-tools-extra-2.02-0.87.0.13.el7_9.6.x86_64                              61/222
  Updating   : 1:grub2-pc-2.02-0.87.0.13.el7_9.6.x86_64                                       62/222
  Updating   : dracut-network-033-572.0.3.el7.x86_64                                          63/222
  Updating   : systemd-sysv-219-78.0.7.el7_9.3.x86_64                                         64/222
  Updating   : 1:wpa_supplicant-2.6-12.el7_9.2.x86_64                                         65/222
  Updating   : 1:NetworkManager-1.18.8-2.el7_9.x86_64                                         66/222
  Updating   : hwdata-0.252-9.7.0.1.el7.x86_64                                                67/222
  Updating   : device-mapper-persistent-data-0.8.5-3.el7_9.2.x86_64                           68/222
  Installing : libzstd-1.4.4-1.el7.x86_64                                                     69/222
  Updating   : btrfs-progs-5.12.1-1.el7.x86_64                                                70/222
  Updating   : 7:lvm2-2.02.187-6.0.5.el7_9.5.x86_64                                           71/222
  Updating   : pciutils-3.5.1-3.0.1.el7.x86_64                                                72/222
  Updating   : 1:NetworkManager-tui-1.18.8-2.el7_9.x86_64                                     73/222
  Updating   : 1:NetworkManager-team-1.18.8-2.el7_9.x86_64                                    74/222
  Updating   : kexec-tools-2.0.15-51.0.3.el7_9.3.x86_64                                       75/222
  Updating   : 1:grub2-2.02-0.87.0.13.el7_9.6.x86_64                                          76/222
  Installing : kernel-3.10.0-1160.42.2.el7.x86_64                                             77/222
  Installing : kernel-uek-5.4.17-2102.205.7.3.el7uek.x86_64                                   78/222
  Updating   : dracut-config-rescue-033-572.0.3.el7.x86_64                                    79/222
  Updating   : xfsprogs-5.4.0-1.0.1.el7.x86_64                                                80/222
  Updating   : rsyslog-8.24.0-57.0.1.el7_9.1.x86_64                                           81/222
  Updating   : firewalld-0.6.3-13.0.1.el7_9.noarch                                            82/222
  Updating   : 2:microcode_ctl-2.1-73.11.0.1.el7_9.x86_64                                     83/222
  Updating   : tuned-2.11.0-11.0.1.el7_9.noarch                                               84/222
  Updating   : curl-7.29.0-59.0.3.el7_9.1.x86_64                                              85/222
  Updating   : sudo-1.8.23-10.el7_9.1.x86_64                                                  86/222
  Updating   : selinux-policy-targeted-3.13.1-268.0.13.el7_9.2.noarch                         87/222
  Updating   : libxml2-python-2.9.1-6.0.3.el7.5.x86_64                                        88/222
  Updating   : libgudev1-219-78.0.7.el7_9.3.x86_64                                            89/222
  Updating   : libcroco-0.6.12-6.el7_9.x86_64                                                 90/222
  Updating   : e2fsprogs-1.45.4-3.0.5.el7.x86_64                                              91/222
  Updating   : 1:openssl-1.0.2k-21.0.3.el7_9.x86_64                                           92/222
  Updating   : binutils-2.27-44.base.0.3.el7.x86_64                                           93/222
  Updating   : kernel-tools-3.10.0-1160.42.2.el7.x86_64                                       94/222
  Updating   : iprutils-2.4.17.1-3.el7_7.x86_64                                               95/222
  Updating   : tzdata-2021a-1.el7.noarch                                                      96/222
  Updating   : 999:iwl6000g2b-firmware-17.168.5.2-999.8.el7.noarch                            97/222
  Updating   : 999:iwl105-firmware-18.168.6.1-999.8.el7.noarch                                98/222
  Updating   : 999:iwl1000-firmware-39.31.5.1-999.8.el7.noarch                                99/222
  Updating   : 999:iwl5150-firmware-8.24.2.2-999.8.el7.noarch                                100/222
  Updating   : 999:iwl5000-firmware-8.83.5.1_1-999.8.el7.noarch                              101/222
  Updating   : 999:iwl6000g2a-firmware-17.168.5.3-999.8.el7.noarch                           102/222
  Updating   : 999:iwl100-firmware-39.31.5.1-999.8.el7.noarch                                103/222
  Updating   : 1:NetworkManager-config-server-1.18.8-2.el7_9.noarch                          104/222
  Updating   : 999:iwl3945-firmware-15.32.2.9-999.8.el7.noarch                               105/222
  Updating   : 999:iwl4965-firmware-228.61.2.24-999.8.el7.noarch                             106/222
  Updating   : 999:iwl7260-firmware-22.0.7.0-999.8.el7.noarch                                107/222
  Updating   : 999:iwl135-firmware-18.168.6.1-999.8.el7.noarch                               108/222
  Updating   : 999:iwl6000-firmware-9.221.4.1-999.8.el7.noarch                               109/222
  Updating   : 999:iwl6050-firmware-41.28.5.1-999.8.el7.noarch                               110/222
  Updating   : 999:iwl2000-firmware-18.168.6.1-999.8.el7.noarch                              111/222
  Updating   : 999:iwl3160-firmware-22.0.7.0-999.8.el7.noarch                                112/222
  Updating   : 999:iwl2030-firmware-18.168.6.1-999.8.el7.noarch                              113/222
  Cleanup    : 2:microcode_ctl-2.1-73.0.1.el7.x86_64                                         114/222
  Cleanup    : tuned-2.11.0-9.0.3.el7.noarch                                                 115/222
  Cleanup    : firewalld-0.6.3-11.0.1.el7.noarch                                             116/222
  Cleanup    : selinux-policy-targeted-3.13.1-268.0.1.el7.noarch                             117/222
  Cleanup    : selinux-policy-3.13.1-268.0.1.el7.noarch                                      118/222
  Cleanup    : python-firewall-0.6.3-11.0.1.el7.noarch                                       119/222
  Cleanup    : dracut-config-rescue-033-572.0.1.el7.x86_64                                   120/222
  Cleanup    : 999:linux-firmware-20200902-999.5.gitd5f9eea5.el7.noarch                      121/222
  Cleanup    : 1:grub2-2.02-0.87.0.1.el7.x86_64                                              122/222
  Cleanup    : 1:grub2-pc-2.02-0.87.0.1.el7.x86_64                                           123/222
  Cleanup    : 1:grub2-pc-modules-2.02-0.87.0.1.el7.noarch                                   124/222
  Cleanup    : firewalld-filesystem-0.6.3-11.0.1.el7.noarch                                  125/222
  Cleanup    : tzdata-2020a-1.el7.noarch                                                     126/222
  Cleanup    : 999:iwl6000g2b-firmware-17.168.5.2-999.5.el7.noarch                           127/222
  Cleanup    : 999:iwl105-firmware-18.168.6.1-999.5.el7.noarch                               128/222
  Cleanup    : 999:iwl1000-firmware-39.31.5.1-999.5.el7.noarch                               129/222
  Cleanup    : 999:iwl5150-firmware-8.24.2.2-999.5.el7.noarch                                130/222
  Cleanup    : 999:iwl5000-firmware-8.83.5.1_1-999.5.el7.noarch                              131/222
  Cleanup    : 999:iwl6000g2a-firmware-17.168.5.3-999.5.el7.noarch                           132/222
  Cleanup    : 999:iwl100-firmware-39.31.5.1-999.5.el7.noarch                                133/222
  Cleanup    : 1:NetworkManager-config-server-1.18.8-1.el7.noarch                            134/222
  Cleanup    : 999:iwl3945-firmware-15.32.2.9-999.5.el7.noarch                               135/222
  Cleanup    : 999:iwl4965-firmware-228.61.2.24-999.5.el7.noarch                             136/222
  Cleanup    : 999:iwl7260-firmware-22.0.7.0-999.5.el7.noarch                                137/222
  Cleanup    : 999:iwl135-firmware-18.168.6.1-999.5.el7.noarch                               138/222
  Cleanup    : 999:iwl6000-firmware-9.221.4.1-999.5.el7.noarch                               139/222
  Cleanup    : 999:iwl6050-firmware-41.28.5.1-999.5.el7.noarch                               140/222
  Cleanup    : 999:iwl2000-firmware-18.168.6.1-999.5.el7.noarch                              141/222
  Cleanup    : 999:iwl3160-firmware-22.0.7.0-999.5.el7.noarch                                142/222
  Cleanup    : 999:iwl2030-firmware-18.168.6.1-999.5.el7.noarch                              143/222
  Cleanup    : 1:NetworkManager-tui-1.18.8-1.el7.x86_64                                      144/222
  Cleanup    : 7:lvm2-2.02.187-6.0.3.el7.x86_64                                              145/222
  Cleanup    : 1:openssl-1.0.2k-19.0.1.el7.x86_64                                            146/222
  Cleanup    : kexec-tools-2.0.15-51.0.1.el7.x86_64                                          147/222
  Cleanup    : curl-7.29.0-59.0.1.el7.x86_64                                                 148/222
  Cleanup    : e2fsprogs-1.42.9-19.el7.x86_64                                                149/222
  Cleanup    : 7:lvm2-libs-2.02.187-6.0.3.el7.x86_64                                         150/222
  Cleanup    : 1:grub2-tools-extra-2.02-0.87.0.1.el7.x86_64                                  151/222
  Cleanup    : libxml2-python-2.9.1-6.0.1.el7.5.x86_64                                       152/222
  Cleanup    : btrfs-progs-4.9.1-1.0.2.el7.x86_64                                            153/222
  Cleanup    : 1:grub2-tools-2.02-0.87.0.1.el7.x86_64                                        154/222
  Cleanup    : 7:device-mapper-event-1.02.170-6.0.3.el7.x86_64                               155/222
  Cleanup    : rsyslog-8.24.0-55.el7.x86_64                                                  156/222
  Cleanup    : dracut-network-033-572.0.1.el7.x86_64                                         157/222
  Cleanup    : 12:dhclient-4.2.5-82.0.1.el7.x86_64                                           158/222
  Cleanup    : initscripts-9.49.53-1.0.1.el7.x86_64                                          159/222
  Cleanup    : dracut-033-572.0.1.el7.x86_64                                                 160/222
  Cleanup    : 32:bind-export-libs-9.11.4-26.P2.el7.x86_64                                   161/222
  Cleanup    : sudo-1.8.23-10.el7.x86_64                                                     162/222
  Cleanup    : 1:grub2-tools-minimal-2.02-0.87.0.1.el7.x86_64                                163/222
  Cleanup    : virt-what-1.18-4.el7.x86_64                                                   164/222
  Cleanup    : python-perf-3.10.0-1160.el7.x86_64                                            165/222
  Cleanup    : pciutils-3.5.1-3.el7.x86_64                                                   166/222
  Cleanup    : kernel-tools-3.10.0-1160.el7.x86_64                                           167/222
  Cleanup    : binutils-2.27-44.base.0.1.el7.x86_64                                          168/222
  Cleanup    : 1:NetworkManager-team-1.18.8-1.el7.x86_64                                     169/222
  Cleanup    : 1:NetworkManager-1.18.8-1.el7.x86_64                                          170/222
  Cleanup    : 1:NetworkManager-libnm-1.18.8-1.el7.x86_64                                    171/222
  Cleanup    : 1:wpa_supplicant-2.6-12.el7.x86_64                                            172/222
  Cleanup    : systemd-sysv-219-78.0.1.el7.x86_64                                            173/222
  Cleanup    : xfsprogs-4.5.0-22.0.1.el7.x86_64                                              174/222
  Cleanup    : libcroco-0.6.12-4.el7.x86_64                                                  175/222
  Cleanup    : libgudev1-219-78.0.1.el7.x86_64                                               176/222
  Cleanup    : hwdata-0.252-9.7.el7.x86_64                                                   177/222
  Cleanup    : 12:dhcp-common-4.2.5-82.0.1.el7.x86_64                                        178/222
  Cleanup    : 12:dhcp-libs-4.2.5-82.0.1.el7.x86_64                                          179/222
  Cleanup    : glib2-2.56.1-7.el7.x86_64                                                     180/222
  Cleanup    : libxml2-2.9.1-6.0.1.el7.5.x86_64                                              181/222
  Cleanup    : python-2.7.5-89.0.1.el7.x86_64                                                182/222
  Cleanup    : python-libs-2.7.5-89.0.1.el7.x86_64                                           183/222
  Cleanup    : kpartx-0.4.9-133.0.1.el7.x86_64                                               184/222
  Cleanup    : 7:device-mapper-event-libs-1.02.170-6.0.3.el7.x86_64                          185/222
  Cleanup    : 7:device-mapper-1.02.170-6.0.3.el7.x86_64                                     186/222
  Cleanup    : 7:device-mapper-libs-1.02.170-6.0.3.el7.x86_64                                187/222
  Cleanup    : systemd-219-78.0.1.el7.x86_64                                                 188/222
  Cleanup    : libcurl-7.29.0-59.0.1.el7.x86_64                                              189/222
  Cleanup    : openldap-2.4.44-22.el7.x86_64                                                 190/222
  Cleanup    : nss-tools-3.44.0-7.el7_7.x86_64                                               191/222
  Cleanup    : util-linux-2.23.2-65.0.1.el7.x86_64                                           192/222
  Cleanup    : nss-sysinit-3.44.0-7.el7_7.x86_64                                             193/222
  Cleanup    : nss-3.44.0-7.el7_7.x86_64                                                     194/222
  Cleanup    : nss-softokn-3.44.0-8.0.1.el7_7.x86_64                                         195/222
  Cleanup    : nss-softokn-freebl-3.44.0-8.0.1.el7_7.x86_64                                  196/222
  Cleanup    : libmount-2.23.2-65.0.1.el7.x86_64                                             197/222
  Cleanup    : libblkid-2.23.2-65.0.1.el7.x86_64                                             198/222
  Cleanup    : krb5-libs-1.15.1-50.el7.x86_64                                                199/222
  Cleanup    : coreutils-8.22-24.0.1.el7.x86_64                                              200/222
  Cleanup    : 1:openssl-libs-1.0.2k-19.0.1.el7.x86_64                                       201/222
  Cleanup    : nss-util-3.44.0-4.el7_7.x86_64                                                202/222
  Cleanup    : e2fsprogs-libs-1.42.9-19.el7.x86_64                                           203/222
  Cleanup    : freetype-2.8-14.el7.x86_64                                                    204/222
  Cleanup    : libss-1.42.9-19.el7.x86_64                                                    205/222
  Cleanup    : iprutils-2.4.17.1-3.el7.x86_64                                                206/222
  Cleanup    : ca-certificates-2020.2.41-70.0.el7_8.noarch                                   207/222
  Cleanup    : 1:redhat-release-server-7.9-3.0.1.el7.x86_64                                  208/222
  Cleanup    : 1:grub2-common-2.02-0.87.0.1.el7.noarch                                       209/222
  Cleanup    : zlib-1.2.7-18.el7.x86_64                                                      210/222
  Cleanup    : libcom_err-1.42.9-19.el7.x86_64                                               211/222
  Cleanup    : nspr-4.21.0-1.el7.x86_64                                                      212/222
  Cleanup    : libuuid-2.23.2-65.0.1.el7.x86_64                                              213/222
  Cleanup    : libsmartcols-2.23.2-65.0.1.el7.x86_64                                         214/222
  Cleanup    : systemd-libs-219-78.0.1.el7.x86_64                                            215/222
  Cleanup    : kernel-tools-libs-3.10.0-1160.el7.x86_64                                      216/222
  Cleanup    : pciutils-libs-3.5.1-3.el7.x86_64                                              217/222
  Cleanup    : 1:dmidecode-3.2-5.el7.x86_64                                                  218/222
  Cleanup    : 2:vim-minimal-7.4.629-7.0.1.el7.x86_64                                        219/222
  Cleanup    : iproute-4.11.0-30.el7.x86_64                                                  220/222
  Cleanup    : device-mapper-persistent-data-0.8.5-3.el7.x86_64                              221/222
  Cleanup    : numactl-libs-2.0.12-5.el7.x86_64                                              222/222
  Verifying  : 1:grub2-tools-2.02-0.87.0.13.el7_9.6.x86_64                                     1/222
  Verifying  : python-libs-2.7.5-90.0.3.el7.x86_64                                             2/222
  Verifying  : kernel-3.10.0-1160.42.2.el7.x86_64                                              3/222
  Verifying  : 999:iwl2030-firmware-18.168.6.1-999.8.el7.noarch                                4/222
  Verifying  : selinux-policy-targeted-3.13.1-268.0.13.el7_9.2.noarch                          5/222
  Verifying  : nss-softokn-freebl-3.53.1-6.0.1.el7_9.x86_64                                    6/222
  Verifying  : 12:dhcp-libs-4.2.5-83.0.1.el7_9.1.x86_64                                        7/222
  Verifying  : 1:grub2-common-2.02-0.87.0.13.el7_9.6.noarch                                    8/222
  Verifying  : 1:NetworkManager-tui-1.18.8-2.el7_9.x86_64                                      9/222
  Verifying  : 7:device-mapper-libs-1.02.170-6.0.5.el7_9.5.x86_64                             10/222
  Verifying  : 1:grub2-pc-2.02-0.87.0.13.el7_9.6.x86_64                                       11/222
  Verifying  : libgudev1-219-78.0.7.el7_9.3.x86_64                                            12/222
  Verifying  : 7:device-mapper-event-libs-1.02.170-6.0.5.el7_9.5.x86_64                       13/222
  Verifying  : 999:iwl3160-firmware-22.0.7.0-999.8.el7.noarch                                 14/222
  Verifying  : libxml2-2.9.1-6.0.3.el7.5.x86_64                                               15/222
  Verifying  : libzstd-1.4.4-1.el7.x86_64                                                     16/222
  Verifying  : 1:NetworkManager-libnm-1.18.8-2.el7_9.x86_64                                   17/222
  Verifying  : kernel-uek-5.4.17-2102.205.7.3.el7uek.x86_64                                   18/222
  Verifying  : 999:iwl2000-firmware-18.168.6.1-999.8.el7.noarch                               19/222
  Verifying  : fuse-libs-2.9.4-1.0.9.el7.x86_64                                               20/222
  Verifying  : nss-3.53.1-7.el7_9.x86_64                                                      21/222
  Verifying  : 999:iwl6050-firmware-41.28.5.1-999.8.el7.noarch                                22/222
  Verifying  : libblkid-2.23.2-65.0.1.el7_9.1.x86_64                                          23/222
  Verifying  : rsyslog-8.24.0-57.0.1.el7_9.1.x86_64                                           24/222
  Verifying  : nss-util-3.53.1-1.el7_9.x86_64                                                 25/222
  Verifying  : btrfs-progs-5.12.1-1.el7.x86_64                                                26/222
  Verifying  : 1:NetworkManager-1.18.8-2.el7_9.x86_64                                         27/222
  Verifying  : 32:bind-export-libs-9.11.4-26.P2.el7_9.7.x86_64                                28/222
  Verifying  : firewalld-0.6.3-13.0.1.el7_9.noarch                                            29/222
  Verifying  : libcroco-0.6.12-6.el7_9.x86_64                                                 30/222
  Verifying  : device-mapper-persistent-data-0.8.5-3.el7_9.2.x86_64                           31/222
  Verifying  : 999:iwl6000-firmware-9.221.4.1-999.8.el7.noarch                                32/222
  Verifying  : 999:iwl135-firmware-18.168.6.1-999.8.el7.noarch                                33/222
  Verifying  : dracut-network-033-572.0.3.el7.x86_64                                          34/222
  Verifying  : python-perf-3.10.0-1160.42.2.el7.x86_64                                        35/222
  Verifying  : 7:device-mapper-1.02.170-6.0.5.el7_9.5.x86_64                                  36/222
  Verifying  : libxml2-python-2.9.1-6.0.3.el7.5.x86_64                                        37/222
  Verifying  : systemd-219-78.0.7.el7_9.3.x86_64                                              38/222
  Verifying  : 1:grub2-2.02-0.87.0.13.el7_9.6.x86_64                                          39/222
  Verifying  : 12:dhclient-4.2.5-83.0.1.el7_9.1.x86_64                                        40/222
  Verifying  : 999:iwl7260-firmware-22.0.7.0-999.8.el7.noarch                                 41/222
  Verifying  : 999:iwl4965-firmware-228.61.2.24-999.8.el7.noarch                              42/222
  Verifying  : 999:iwl3945-firmware-15.32.2.9-999.8.el7.noarch                                43/222
  Verifying  : curl-7.29.0-59.0.3.el7_9.1.x86_64                                              44/222
  Verifying  : freetype-2.8-14.el7_9.1.x86_64                                                 45/222
  Verifying  : xfsprogs-5.4.0-1.0.1.el7.x86_64                                                46/222
  Verifying  : 999:linux-firmware-20210617-999.8.git0f66b74b.el7.noarch                       47/222
  Verifying  : 2:microcode_ctl-2.1-73.11.0.1.el7_9.x86_64                                     48/222
  Verifying  : 1:NetworkManager-config-server-1.18.8-2.el7_9.noarch                           49/222
  Verifying  : kexec-tools-2.0.15-51.0.3.el7_9.3.x86_64                                       50/222
  Verifying  : util-linux-2.23.2-65.0.1.el7_9.1.x86_64                                        51/222
  Verifying  : krb5-libs-1.15.1-50.0.1.el7.x86_64                                             52/222
  Verifying  : 7:lvm2-libs-2.02.187-6.0.5.el7_9.5.x86_64                                      53/222
  Verifying  : iprutils-2.4.17.1-3.el7_7.x86_64                                               54/222
  Verifying  : libss-1.45.4-3.0.5.el7.x86_64                                                  55/222
  Verifying  : zlib-1.2.7-19.el7_9.x86_64                                                     56/222
  Verifying  : coreutils-8.22-24.0.1.el7_9.2.x86_64                                           57/222
  Verifying  : 1:redhat-release-server-7.9-6.0.1.el7_9.x86_64                                 58/222
  Verifying  : initscripts-9.49.53-1.0.1.el7_9.1.x86_64                                       59/222
  Verifying  : dracut-033-572.0.3.el7.x86_64                                                  60/222
  Verifying  : 999:iwl100-firmware-39.31.5.1-999.8.el7.noarch                                 61/222
  Verifying  : nspr-4.25.0-2.el7_9.x86_64                                                     62/222
  Verifying  : 1:NetworkManager-team-1.18.8-2.el7_9.x86_64                                    63/222
  Verifying  : ca-certificates-2021.2.50-72.el7_9.noarch                                      64/222
  Verifying  : libuuid-2.23.2-65.0.1.el7_9.1.x86_64                                           65/222
  Verifying  : 999:iwl6000g2a-firmware-17.168.5.3-999.8.el7.noarch                            66/222
  Verifying  : libsmartcols-2.23.2-65.0.1.el7_9.1.x86_64                                      67/222
  Verifying  : 1:grub2-tools-extra-2.02-0.87.0.13.el7_9.6.x86_64                              68/222
  Verifying  : binutils-2.27-44.base.0.3.el7.x86_64                                           69/222
  Verifying  : iproute-5.4.0-1.0.1.el7.x86_64                                                 70/222
  Verifying  : selinux-policy-3.13.1-268.0.13.el7_9.2.noarch                                  71/222
  Verifying  : 999:iwl5000-firmware-8.83.5.1_1-999.8.el7.noarch                               72/222
  Verifying  : dracut-config-rescue-033-572.0.3.el7.x86_64                                    73/222
  Verifying  : tuned-2.11.0-11.0.1.el7_9.noarch                                               74/222
  Verifying  : 1:wpa_supplicant-2.6-12.el7_9.2.x86_64                                         75/222
  Verifying  : libmount-2.23.2-65.0.1.el7_9.1.x86_64                                          76/222
  Verifying  : nss-softokn-3.53.1-6.0.1.el7_9.x86_64                                          77/222
  Verifying  : 1:openssl-libs-1.0.2k-21.0.3.el7_9.x86_64                                      78/222
  Verifying  : e2fsprogs-libs-1.45.4-3.0.5.el7.x86_64                                         79/222
  Verifying  : openldap-2.4.44-24.el7_9.x86_64                                                80/222
  Verifying  : kernel-tools-3.10.0-1160.42.2.el7.x86_64                                       81/222
  Verifying  : libcurl-7.29.0-59.0.3.el7_9.1.x86_64                                           82/222
  Verifying  : 1:openssl-1.0.2k-21.0.3.el7_9.x86_64                                           83/222
  Verifying  : pciutils-libs-3.5.1-3.0.1.el7.x86_64                                           84/222
  Verifying  : nss-tools-3.53.1-7.el7_9.x86_64                                                85/222
  Verifying  : virt-what-1.18-4.el7_9.1.x86_64                                                86/222
  Verifying  : firewalld-filesystem-0.6.3-13.0.1.el7_9.noarch                                 87/222
  Verifying  : 1:dmidecode-3.2-5.0.1.el7_9.1.x86_64                                           88/222
  Verifying  : e2fsprogs-1.45.4-3.0.5.el7.x86_64                                              89/222
  Verifying  : libcom_err-1.45.4-3.0.5.el7.x86_64                                             90/222
  Verifying  : 999:iwl5150-firmware-8.24.2.2-999.8.el7.noarch                                 91/222
  Verifying  : kernel-tools-libs-3.10.0-1160.42.2.el7.x86_64                                  92/222
  Verifying  : numactl-libs-2.0.12-5.0.3.el7.x86_64                                           93/222
  Verifying  : 12:dhcp-common-4.2.5-83.0.1.el7_9.1.x86_64                                     94/222
  Verifying  : 1:grub2-pc-modules-2.02-0.87.0.13.el7_9.6.noarch                               95/222
  Verifying  : systemd-sysv-219-78.0.7.el7_9.3.x86_64                                         96/222
  Verifying  : glib2-2.56.1-9.el7_9.x86_64                                                    97/222
  Verifying  : 999:iwl1000-firmware-39.31.5.1-999.8.el7.noarch                                98/222
  Verifying  : python-2.7.5-90.0.3.el7.x86_64                                                 99/222
  Verifying  : hwdata-0.252-9.7.0.1.el7.x86_64                                               100/222
  Verifying  : sudo-1.8.23-10.el7_9.1.x86_64                                                 101/222
  Verifying  : nss-sysinit-3.53.1-7.el7_9.x86_64                                             102/222
  Verifying  : pciutils-3.5.1-3.0.1.el7.x86_64                                               103/222
  Verifying  : 1:grub2-tools-minimal-2.02-0.87.0.13.el7_9.6.x86_64                           104/222
  Verifying  : 7:device-mapper-event-1.02.170-6.0.5.el7_9.5.x86_64                           105/222
  Verifying  : systemd-libs-219-78.0.7.el7_9.3.x86_64                                        106/222
  Verifying  : 2:vim-minimal-7.4.629-8.0.1.el7_9.x86_64                                      107/222
  Verifying  : 999:iwl105-firmware-18.168.6.1-999.8.el7.noarch                               108/222
  Verifying  : 999:iwl6000g2b-firmware-17.168.5.2-999.8.el7.noarch                           109/222
  Verifying  : python-firewall-0.6.3-13.0.1.el7_9.noarch                                     110/222
  Verifying  : 7:lvm2-2.02.187-6.0.5.el7_9.5.x86_64                                          111/222
  Verifying  : kpartx-0.4.9-135.0.1.el7_9.x86_64                                             112/222
  Verifying  : tzdata-2021a-1.el7.noarch                                                     113/222
  Verifying  : 2:microcode_ctl-2.1-73.0.1.el7.x86_64                                         114/222
  Verifying  : util-linux-2.23.2-65.0.1.el7.x86_64                                           115/222
  Verifying  : libcom_err-1.42.9-19.el7.x86_64                                               116/222
  Verifying  : 999:iwl100-firmware-39.31.5.1-999.5.el7.noarch                                117/222
  Verifying  : nss-3.44.0-7.el7_7.x86_64                                                     118/222
  Verifying  : libxml2-python-2.9.1-6.0.1.el7.5.x86_64                                       119/222
  Verifying  : kexec-tools-2.0.15-51.0.1.el7.x86_64                                          120/222
  Verifying  : freetype-2.8-14.el7.x86_64                                                    121/222
  Verifying  : glib2-2.56.1-7.el7.x86_64                                                     122/222
  Verifying  : libmount-2.23.2-65.0.1.el7.x86_64                                             123/222
  Verifying  : systemd-219-78.0.1.el7.x86_64                                                 124/222
  Verifying  : virt-what-1.18-4.el7.x86_64                                                   125/222
  Verifying  : 7:device-mapper-1.02.170-6.0.3.el7.x86_64                                     126/222
  Verifying  : 2:vim-minimal-7.4.629-7.0.1.el7.x86_64                                        127/222
  Verifying  : curl-7.29.0-59.0.1.el7.x86_64                                                 128/222
  Verifying  : selinux-policy-targeted-3.13.1-268.0.1.el7.noarch                             129/222
  Verifying  : 1:grub2-tools-minimal-2.02-0.87.0.1.el7.x86_64                                130/222
  Verifying  : libxml2-2.9.1-6.0.1.el7.5.x86_64                                              131/222
  Verifying  : 7:device-mapper-event-1.02.170-6.0.3.el7.x86_64                               132/222
  Verifying  : nss-softokn-freebl-3.44.0-8.0.1.el7_7.x86_64                                  133/222
  Verifying  : 999:iwl5000-firmware-8.83.5.1_1-999.5.el7.noarch                              134/222
  Verifying  : 1:grub2-pc-2.02-0.87.0.1.el7.x86_64                                           135/222
  Verifying  : 999:iwl2030-firmware-18.168.6.1-999.5.el7.noarch                              136/222
  Verifying  : libuuid-2.23.2-65.0.1.el7.x86_64                                              137/222
  Verifying  : 1:NetworkManager-team-1.18.8-1.el7.x86_64                                     138/222
  Verifying  : kernel-tools-libs-3.10.0-1160.el7.x86_64                                      139/222
  Verifying  : 999:iwl3945-firmware-15.32.2.9-999.5.el7.noarch                               140/222
  Verifying  : sudo-1.8.23-10.el7.x86_64                                                     141/222
  Verifying  : btrfs-progs-4.9.1-1.0.2.el7.x86_64                                            142/222
  Verifying  : ca-certificates-2020.2.41-70.0.el7_8.noarch                                   143/222
  Verifying  : 1:NetworkManager-libnm-1.18.8-1.el7.x86_64                                    144/222
  Verifying  : pciutils-3.5.1-3.el7.x86_64                                                   145/222
  Verifying  : zlib-1.2.7-18.el7.x86_64                                                      146/222
  Verifying  : 12:dhcp-common-4.2.5-82.0.1.el7.x86_64                                        147/222
  Verifying  : nss-tools-3.44.0-7.el7_7.x86_64                                               148/222
  Verifying  : 1:NetworkManager-tui-1.18.8-1.el7.x86_64                                      149/222
  Verifying  : e2fsprogs-1.42.9-19.el7.x86_64                                                150/222
  Verifying  : 1:wpa_supplicant-2.6-12.el7.x86_64                                            151/222
  Verifying  : initscripts-9.49.53-1.0.1.el7.x86_64                                          152/222
  Verifying  : 1:openssl-libs-1.0.2k-19.0.1.el7.x86_64                                       153/222
  Verifying  : nss-sysinit-3.44.0-7.el7_7.x86_64                                             154/222
  Verifying  : 1:grub2-2.02-0.87.0.1.el7.x86_64                                              155/222
  Verifying  : 1:grub2-common-2.02-0.87.0.1.el7.noarch                                       156/222
  Verifying  : systemd-libs-219-78.0.1.el7.x86_64                                            157/222
  Verifying  : 1:NetworkManager-1.18.8-1.el7.x86_64                                          158/222
  Verifying  : 999:iwl6000g2a-firmware-17.168.5.3-999.5.el7.noarch                           159/222
  Verifying  : systemd-sysv-219-78.0.1.el7.x86_64                                            160/222
  Verifying  : coreutils-8.22-24.0.1.el7.x86_64                                              161/222
  Verifying  : 32:bind-export-libs-9.11.4-26.P2.el7.x86_64                                   162/222
  Verifying  : rsyslog-8.24.0-55.el7.x86_64                                                  163/222
  Verifying  : e2fsprogs-libs-1.42.9-19.el7.x86_64                                           164/222
  Verifying  : firewalld-filesystem-0.6.3-11.0.1.el7.noarch                                  165/222
  Verifying  : python-libs-2.7.5-89.0.1.el7.x86_64                                           166/222
  Verifying  : 7:device-mapper-libs-1.02.170-6.0.3.el7.x86_64                                167/222
  Verifying  : tuned-2.11.0-9.0.3.el7.noarch                                                 168/222
  Verifying  : tzdata-2020a-1.el7.noarch                                                     169/222
  Verifying  : 1:redhat-release-server-7.9-3.0.1.el7.x86_64                                  170/222
  Verifying  : 1:grub2-tools-2.02-0.87.0.1.el7.x86_64                                        171/222
  Verifying  : 999:iwl6050-firmware-41.28.5.1-999.5.el7.noarch                               172/222
  Verifying  : krb5-libs-1.15.1-50.el7.x86_64                                                173/222
  Verifying  : libblkid-2.23.2-65.0.1.el7.x86_64                                             174/222
  Verifying  : kpartx-0.4.9-133.0.1.el7.x86_64                                               175/222
  Verifying  : libcurl-7.29.0-59.0.1.el7.x86_64                                              176/222
  Verifying  : 12:dhcp-libs-4.2.5-82.0.1.el7.x86_64                                          177/222
  Verifying  : nss-softokn-3.44.0-8.0.1.el7_7.x86_64                                         178/222
  Verifying  : 999:iwl6000-firmware-9.221.4.1-999.5.el7.noarch                               179/222
  Verifying  : 999:iwl7260-firmware-22.0.7.0-999.5.el7.noarch                                180/222
  Verifying  : libcroco-0.6.12-4.el7.x86_64                                                  181/222
  Verifying  : 999:linux-firmware-20200902-999.5.gitd5f9eea5.el7.noarch                      182/222
  Verifying  : 999:iwl105-firmware-18.168.6.1-999.5.el7.noarch                               183/222
  Verifying  : 1:dmidecode-3.2-5.el7.x86_64                                                  184/222
  Verifying  : binutils-2.27-44.base.0.1.el7.x86_64                                          185/222
  Verifying  : 1:openssl-1.0.2k-19.0.1.el7.x86_64                                            186/222
  Verifying  : 999:iwl3160-firmware-22.0.7.0-999.5.el7.noarch                                187/222
  Verifying  : hwdata-0.252-9.7.el7.x86_64                                                   188/222
  Verifying  : 999:iwl6000g2b-firmware-17.168.5.2-999.5.el7.noarch                           189/222
  Verifying  : 999:iwl2000-firmware-18.168.6.1-999.5.el7.noarch                              190/222
  Verifying  : 12:dhclient-4.2.5-82.0.1.el7.x86_64                                           191/222
  Verifying  : python-perf-3.10.0-1160.el7.x86_64                                            192/222
  Verifying  : 999:iwl4965-firmware-228.61.2.24-999.5.el7.noarch                             193/222
  Verifying  : libgudev1-219-78.0.1.el7.x86_64                                               194/222
  Verifying  : openldap-2.4.44-22.el7.x86_64                                                 195/222
  Verifying  : dracut-network-033-572.0.1.el7.x86_64                                         196/222
  Verifying  : iprutils-2.4.17.1-3.el7.x86_64                                                197/222
  Verifying  : python-2.7.5-89.0.1.el7.x86_64                                                198/222
  Verifying  : firewalld-0.6.3-11.0.1.el7.noarch                                             199/222
  Verifying  : 1:grub2-pc-modules-2.02-0.87.0.1.el7.noarch                                   200/222
  Verifying  : 7:lvm2-libs-2.02.187-6.0.3.el7.x86_64                                         201/222
  Verifying  : 999:iwl5150-firmware-8.24.2.2-999.5.el7.noarch                                202/222
  Verifying  : 7:device-mapper-event-libs-1.02.170-6.0.3.el7.x86_64                          203/222
  Verifying  : pciutils-libs-3.5.1-3.el7.x86_64                                              204/222
  Verifying  : dracut-033-572.0.1.el7.x86_64                                                 205/222
  Verifying  : 999:iwl135-firmware-18.168.6.1-999.5.el7.noarch                               206/222
  Verifying  : selinux-policy-3.13.1-268.0.1.el7.noarch                                      207/222
  Verifying  : xfsprogs-4.5.0-22.0.1.el7.x86_64                                              208/222
  Verifying  : iproute-4.11.0-30.el7.x86_64                                                  209/222
  Verifying  : dracut-config-rescue-033-572.0.1.el7.x86_64                                   210/222
  Verifying  : nspr-4.21.0-1.el7.x86_64                                                      211/222
  Verifying  : libsmartcols-2.23.2-65.0.1.el7.x86_64                                         212/222
  Verifying  : python-firewall-0.6.3-11.0.1.el7.noarch                                       213/222
  Verifying  : 999:iwl1000-firmware-39.31.5.1-999.5.el7.noarch                               214/222
  Verifying  : libss-1.42.9-19.el7.x86_64                                                    215/222
  Verifying  : kernel-tools-3.10.0-1160.el7.x86_64                                           216/222
  Verifying  : numactl-libs-2.0.12-5.el7.x86_64                                              217/222
  Verifying  : device-mapper-persistent-data-0.8.5-3.el7.x86_64                              218/222
  Verifying  : 7:lvm2-2.02.187-6.0.3.el7.x86_64                                              219/222
  Verifying  : nss-util-3.44.0-4.el7_7.x86_64                                                220/222
  Verifying  : 1:grub2-tools-extra-2.02-0.87.0.1.el7.x86_64                                  221/222
  Verifying  : 1:NetworkManager-config-server-1.18.8-1.el7.noarch                            222/222

Installed:
  kernel.x86_64 0:3.10.0-1160.42.2.el7         kernel-uek.x86_64 0:5.4.17-2102.205.7.3.el7uek

Dependency Installed:
  fuse-libs.x86_64 0:2.9.4-1.0.9.el7                   libzstd.x86_64 0:1.4.4-1.el7

Updated:
  NetworkManager.x86_64 1:1.18.8-2.el7_9
  NetworkManager-config-server.noarch 1:1.18.8-2.el7_9
  NetworkManager-libnm.x86_64 1:1.18.8-2.el7_9
  NetworkManager-team.x86_64 1:1.18.8-2.el7_9
  NetworkManager-tui.x86_64 1:1.18.8-2.el7_9
  bind-export-libs.x86_64 32:9.11.4-26.P2.el7_9.7
  binutils.x86_64 0:2.27-44.base.0.3.el7
  btrfs-progs.x86_64 0:5.12.1-1.el7
  ca-certificates.noarch 0:2021.2.50-72.el7_9
  coreutils.x86_64 0:8.22-24.0.1.el7_9.2
  curl.x86_64 0:7.29.0-59.0.3.el7_9.1
  device-mapper.x86_64 7:1.02.170-6.0.5.el7_9.5
  device-mapper-event.x86_64 7:1.02.170-6.0.5.el7_9.5
  device-mapper-event-libs.x86_64 7:1.02.170-6.0.5.el7_9.5
  device-mapper-libs.x86_64 7:1.02.170-6.0.5.el7_9.5
  device-mapper-persistent-data.x86_64 0:0.8.5-3.el7_9.2
  dhclient.x86_64 12:4.2.5-83.0.1.el7_9.1
  dhcp-common.x86_64 12:4.2.5-83.0.1.el7_9.1
  dhcp-libs.x86_64 12:4.2.5-83.0.1.el7_9.1
  dmidecode.x86_64 1:3.2-5.0.1.el7_9.1
  dracut.x86_64 0:033-572.0.3.el7
  dracut-config-rescue.x86_64 0:033-572.0.3.el7
  dracut-network.x86_64 0:033-572.0.3.el7
  e2fsprogs.x86_64 0:1.45.4-3.0.5.el7
  e2fsprogs-libs.x86_64 0:1.45.4-3.0.5.el7
  firewalld.noarch 0:0.6.3-13.0.1.el7_9
  firewalld-filesystem.noarch 0:0.6.3-13.0.1.el7_9
  freetype.x86_64 0:2.8-14.el7_9.1
  glib2.x86_64 0:2.56.1-9.el7_9
  grub2.x86_64 1:2.02-0.87.0.13.el7_9.6
  grub2-common.noarch 1:2.02-0.87.0.13.el7_9.6
  grub2-pc.x86_64 1:2.02-0.87.0.13.el7_9.6
  grub2-pc-modules.noarch 1:2.02-0.87.0.13.el7_9.6
  grub2-tools.x86_64 1:2.02-0.87.0.13.el7_9.6
  grub2-tools-extra.x86_64 1:2.02-0.87.0.13.el7_9.6
  grub2-tools-minimal.x86_64 1:2.02-0.87.0.13.el7_9.6
  hwdata.x86_64 0:0.252-9.7.0.1.el7
  initscripts.x86_64 0:9.49.53-1.0.1.el7_9.1
  iproute.x86_64 0:5.4.0-1.0.1.el7
  iprutils.x86_64 0:2.4.17.1-3.el7_7
  iwl100-firmware.noarch 999:39.31.5.1-999.8.el7
  iwl1000-firmware.noarch 999:39.31.5.1-999.8.el7
  iwl105-firmware.noarch 999:18.168.6.1-999.8.el7
  iwl135-firmware.noarch 999:18.168.6.1-999.8.el7
  iwl2000-firmware.noarch 999:18.168.6.1-999.8.el7
  iwl2030-firmware.noarch 999:18.168.6.1-999.8.el7
  iwl3160-firmware.noarch 999:22.0.7.0-999.8.el7
  iwl3945-firmware.noarch 999:15.32.2.9-999.8.el7
  iwl4965-firmware.noarch 999:228.61.2.24-999.8.el7
  iwl5000-firmware.noarch 999:8.83.5.1_1-999.8.el7
  iwl5150-firmware.noarch 999:8.24.2.2-999.8.el7
  iwl6000-firmware.noarch 999:9.221.4.1-999.8.el7
  iwl6000g2a-firmware.noarch 999:17.168.5.3-999.8.el7
  iwl6000g2b-firmware.noarch 999:17.168.5.2-999.8.el7
  iwl6050-firmware.noarch 999:41.28.5.1-999.8.el7
  iwl7260-firmware.noarch 999:22.0.7.0-999.8.el7
  kernel-tools.x86_64 0:3.10.0-1160.42.2.el7
  kernel-tools-libs.x86_64 0:3.10.0-1160.42.2.el7
  kexec-tools.x86_64 0:2.0.15-51.0.3.el7_9.3
  kpartx.x86_64 0:0.4.9-135.0.1.el7_9
  krb5-libs.x86_64 0:1.15.1-50.0.1.el7
  libblkid.x86_64 0:2.23.2-65.0.1.el7_9.1
  libcom_err.x86_64 0:1.45.4-3.0.5.el7
  libcroco.x86_64 0:0.6.12-6.el7_9
  libcurl.x86_64 0:7.29.0-59.0.3.el7_9.1
  libgudev1.x86_64 0:219-78.0.7.el7_9.3
  libmount.x86_64 0:2.23.2-65.0.1.el7_9.1
  libsmartcols.x86_64 0:2.23.2-65.0.1.el7_9.1
  libss.x86_64 0:1.45.4-3.0.5.el7
  libuuid.x86_64 0:2.23.2-65.0.1.el7_9.1
  libxml2.x86_64 0:2.9.1-6.0.3.el7.5
  libxml2-python.x86_64 0:2.9.1-6.0.3.el7.5
  linux-firmware.noarch 999:20210617-999.8.git0f66b74b.el7
  lvm2.x86_64 7:2.02.187-6.0.5.el7_9.5
  lvm2-libs.x86_64 7:2.02.187-6.0.5.el7_9.5
  microcode_ctl.x86_64 2:2.1-73.11.0.1.el7_9
  nspr.x86_64 0:4.25.0-2.el7_9
  nss.x86_64 0:3.53.1-7.el7_9
  nss-softokn.x86_64 0:3.53.1-6.0.1.el7_9
  nss-softokn-freebl.x86_64 0:3.53.1-6.0.1.el7_9
  nss-sysinit.x86_64 0:3.53.1-7.el7_9
  nss-tools.x86_64 0:3.53.1-7.el7_9
  nss-util.x86_64 0:3.53.1-1.el7_9
  numactl-libs.x86_64 0:2.0.12-5.0.3.el7
  openldap.x86_64 0:2.4.44-24.el7_9
  openssl.x86_64 1:1.0.2k-21.0.3.el7_9
  openssl-libs.x86_64 1:1.0.2k-21.0.3.el7_9
  pciutils.x86_64 0:3.5.1-3.0.1.el7
  pciutils-libs.x86_64 0:3.5.1-3.0.1.el7
  python.x86_64 0:2.7.5-90.0.3.el7
  python-firewall.noarch 0:0.6.3-13.0.1.el7_9
  python-libs.x86_64 0:2.7.5-90.0.3.el7
  python-perf.x86_64 0:3.10.0-1160.42.2.el7
  redhat-release-server.x86_64 1:7.9-6.0.1.el7_9
  rsyslog.x86_64 0:8.24.0-57.0.1.el7_9.1
  selinux-policy.noarch 0:3.13.1-268.0.13.el7_9.2
  selinux-policy-targeted.noarch 0:3.13.1-268.0.13.el7_9.2
  sudo.x86_64 0:1.8.23-10.el7_9.1
  systemd.x86_64 0:219-78.0.7.el7_9.3
  systemd-libs.x86_64 0:219-78.0.7.el7_9.3
  systemd-sysv.x86_64 0:219-78.0.7.el7_9.3
  tuned.noarch 0:2.11.0-11.0.1.el7_9
  tzdata.noarch 0:2021a-1.el7
  util-linux.x86_64 0:2.23.2-65.0.1.el7_9.1
  vim-minimal.x86_64 2:7.4.629-8.0.1.el7_9
  virt-what.x86_64 0:1.18-4.el7_9.1
  wpa_supplicant.x86_64 1:2.6-12.el7_9.2
  xfsprogs.x86_64 0:5.4.0-1.0.1.el7
  zlib.x86_64 0:1.2.7-19.el7_9

Complete!
[root@localhost repo]#
```
