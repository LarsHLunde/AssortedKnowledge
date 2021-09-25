```
[root@localhost repo]# yum search oracle
Loaded plugins: ulninfo
============================================================================================ N/S matc
kmod-oracleasm.x86_64 : oracleasm kernel module(s)
oracle-database-preinstall-18c.x86_64 : Sets the system for Oracle Database single instance and Real
oracle-database-preinstall-19c.x86_64 : Oracle Database Preinstallation RPM
oracle-database-preinstall-21c.x86_64 : Oracle Database Preinstallation RPM
oracle-database-server-12cR2-preinstall.x86_64 : Sets the system for Oracle Database single instance
oracle-graalvm-ce-release-el7.x86_64 : Oracle GraalVM Community yum repository configuration
oracle-instantclient-release-el7.x86_64 : Oracle Instant Client yum repository configuration
oracle-linux-manager-client-release-el7.x86_64 : Oracle Linux Manager Client yum repository configura
oracle-linux-manager-server-release-el7.x86_64 : Oracle Linux Manager Server yum repository configura
oracle-logos.noarch : Oracle-related icons and pictures
oracle-olcne-release-el7.x86_64 : Oracle Linux Cloud Native Environment yum repository configuration
oracle-openstack-release-el7.x86_64 : Oracle OpenStack for Oracle Linux yum repository configuration
oracle-rdbms-server-11gR2-preinstall.x86_64 : Sets the system for Oracle single instance and Real App
oracle-rdbms-server-12cR1-preinstall.x86_64 : Sets the system for Oracle Database single instance and
oracle-release-el7.x86_64 : Oracle Software yum repository configuration
oracleasm-support.x86_64 : The Oracle Automatic Storage Management support programs.
oraclelinux-developer-release-el7.x86_64 : Oracle Linux Developer yum repository configuration
oraclelinux-release.x86_64 : Oracle Linux 7 release file
oraclelinux-release-el7.x86_64 : Oracle Linux yum repository configuration
basesystem.noarch : The skeleton package which defines a simple Oracle Linux system
kabi-yum-plugins.noarch : The Oracle Linux kernel ABI yum plugin
kernel-uek.x86_64 : Oracle Unbreakable Enterprise Kernel Release 6
ocfs2-tools.x86_64 : Tools for managing the Oracle Cluster Filesystem 2
oracle-ceph-release-el7.x86_64 : Ceph Storage yum repository configuration
oracle-epel-release-el7.x86_64 : Extra Packages for Enterprise Linux (EPEL) yum repository configurat
oracle-gluster-release-el7.x86_64 : Gluster yum repository configuration
oracle-golang-release-el7.x86_64 : Go Language  yum repository configuration
oracle-nodejs-release-el7.x86_64 : Node.js yum repository configuration
oracle-ovirt-release-el7.x86_64 : oVirt yum repository configuration
oracle-php-release-el7.x86_64 : PHP yum repository configuration
oracle-softwarecollection-release-el7.x86_64 : Software Collection Library yum repository configurati
oracle-spacewalk-client-release-el7.x86_64 : Spacewalk Client yum repository configuration
oracle-spacewalk-server-release-el7.x86_64 : Spacewalk Server yum repository configuration
redhat-bookmarks.noarch : Oracle Linux bookmarks
redhat-upgrade-tool.noarch : The Oracle Linux Upgrade tool

  Name and summary matches only, use "search all" for everything.
[root@localhost repo]# yum install -y oracle-database-preinstall-19c
Loaded plugins: ulninfo
Resolving Dependencies
--> Running transaction check
---> Package oracle-database-preinstall-19c.x86_64 0:1.0-3.el7 will be installed
--> Processing Dependency: xorg-x11-xauth for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: xorg-x11-utils for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: unzip for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: sysstat for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: smartmontools for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: psmisc for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: nfs-utils for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: net-tools for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: libstdc++-devel for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: libaio-devel for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: ksh for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: glibc-devel for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: compat-libcap1 for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Processing Dependency: bind-utils for package: oracle-database-preinstall-19c-1.0-3.el7.x86_64
--> Running transaction check
---> Package bind-utils.x86_64 32:9.11.4-26.P2.el7_9.7 will be installed
--> Processing Dependency: bind-libs-lite(x86-64) = 32:9.11.4-26.P2.el7_9.7 for package: 32:bind-utils-9.11.4-26.P2.el7_9.7.x86_64
--> Processing Dependency: bind-libs(x86-64) = 32:9.11.4-26.P2.el7_9.7 for package: 32:bind-utils-9.11.4-26.P2.el7_9.7.x86_64
--> Processing Dependency: liblwres.so.160()(64bit) for package: 32:bind-utils-9.11.4-26.P2.el7_9.7.x86_64
--> Processing Dependency: libisccfg.so.160()(64bit) for package: 32:bind-utils-9.11.4-26.P2.el7_9.7.x86_64
--> Processing Dependency: libisc.so.169()(64bit) for package: 32:bind-utils-9.11.4-26.P2.el7_9.7.x86_64
--> Processing Dependency: libirs.so.160()(64bit) for package: 32:bind-utils-9.11.4-26.P2.el7_9.7.x86_64
--> Processing Dependency: libdns.so.1102()(64bit) for package: 32:bind-utils-9.11.4-26.P2.el7_9.7.x86_64
--> Processing Dependency: libbind9.so.160()(64bit) for package: 32:bind-utils-9.11.4-26.P2.el7_9.7.x86_64
--> Processing Dependency: libGeoIP.so.1()(64bit) for package: 32:bind-utils-9.11.4-26.P2.el7_9.7.x86_64
---> Package compat-libcap1.x86_64 0:1.10-7.el7 will be installed
---> Package glibc-devel.x86_64 0:2.17-324.0.1.el7_9 will be installed
--> Processing Dependency: glibc-headers = 2.17-324.0.1.el7_9 for package: glibc-devel-2.17-324.0.1.el7_9.x86_64
--> Processing Dependency: glibc = 2.17-324.0.1.el7_9 for package: glibc-devel-2.17-324.0.1.el7_9.x86_64
--> Processing Dependency: glibc-headers for package: glibc-devel-2.17-324.0.1.el7_9.x86_64
---> Package ksh.x86_64 0:20120801-142.0.1.el7 will be installed
---> Package libaio-devel.x86_64 0:0.3.109-13.el7 will be installed
---> Package libstdc++-devel.x86_64 0:4.8.5-44.0.3.el7 will be installed
---> Package net-tools.x86_64 0:2.0-0.25.20131004git.el7 will be installed
---> Package nfs-utils.x86_64 1:1.3.0-0.68.0.1.el7.1 will be installed
--> Processing Dependency: libtirpc >= 0.2.4-0.7 for package: 1:nfs-utils-1.3.0-0.68.0.1.el7.1.x86_64
--> Processing Dependency: gssproxy >= 0.7.0-3 for package: 1:nfs-utils-1.3.0-0.68.0.1.el7.1.x86_64
--> Processing Dependency: rpcbind for package: 1:nfs-utils-1.3.0-0.68.0.1.el7.1.x86_64
--> Processing Dependency: quota for package: 1:nfs-utils-1.3.0-0.68.0.1.el7.1.x86_64
--> Processing Dependency: libnfsidmap for package: 1:nfs-utils-1.3.0-0.68.0.1.el7.1.x86_64
--> Processing Dependency: libevent for package: 1:nfs-utils-1.3.0-0.68.0.1.el7.1.x86_64
--> Processing Dependency: keyutils for package: 1:nfs-utils-1.3.0-0.68.0.1.el7.1.x86_64
--> Processing Dependency: libtirpc.so.1()(64bit) for package: 1:nfs-utils-1.3.0-0.68.0.1.el7.1.x86_64
--> Processing Dependency: libnfsidmap.so.0()(64bit) for package: 1:nfs-utils-1.3.0-0.68.0.1.el7.1.x86_64
--> Processing Dependency: libevent-2.0.so.5()(64bit) for package: 1:nfs-utils-1.3.0-0.68.0.1.el7.1.x86_64
---> Package psmisc.x86_64 0:22.20-17.el7 will be installed
---> Package smartmontools.x86_64 1:7.0-2.el7 will be installed
--> Processing Dependency: mailx for package: 1:smartmontools-7.0-2.el7.x86_64
---> Package sysstat.x86_64 0:10.1.5-19.el7 will be installed
--> Processing Dependency: libsensors.so.4()(64bit) for package: sysstat-10.1.5-19.el7.x86_64
---> Package unzip.x86_64 0:6.0-22.el7_9 will be installed
---> Package xorg-x11-utils.x86_64 0:7.5-23.el7 will be installed
--> Processing Dependency: libxcb.so.1()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libxcb-shape.so.0()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libdmx.so.1()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libXxf86vm.so.1()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libXxf86misc.so.1()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libXxf86dga.so.1()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libXv.so.1()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libXtst.so.6()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libXrender.so.1()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libXrandr.so.2()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libXinerama.so.1()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libXi.so.6()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libXext.so.6()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libX11.so.6()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
--> Processing Dependency: libX11-xcb.so.1()(64bit) for package: xorg-x11-utils-7.5-23.el7.x86_64
---> Package xorg-x11-xauth.x86_64 1:1.0.9-1.el7 will be installed
--> Processing Dependency: libXmuu.so.1()(64bit) for package: 1:xorg-x11-xauth-1.0.9-1.el7.x86_64
--> Processing Dependency: libXau.so.6()(64bit) for package: 1:xorg-x11-xauth-1.0.9-1.el7.x86_64
--> Running transaction check
---> Package GeoIP.x86_64 0:1.5.0-14.el7 will be installed
--> Processing Dependency: geoipupdate for package: GeoIP-1.5.0-14.el7.x86_64
---> Package bind-libs.x86_64 32:9.11.4-26.P2.el7_9.7 will be installed
--> Processing Dependency: bind-license = 32:9.11.4-26.P2.el7_9.7 for package: 32:bind-libs-9.11.4-26.P2.el7_9.7.x86_64
---> Package bind-libs-lite.x86_64 32:9.11.4-26.P2.el7_9.7 will be installed
---> Package glibc.x86_64 0:2.17-317.0.1.el7 will be updated
--> Processing Dependency: glibc = 2.17-317.0.1.el7 for package: glibc-common-2.17-317.0.1.el7.x86_64
---> Package glibc.x86_64 0:2.17-324.0.1.el7_9 will be an update
---> Package glibc-headers.x86_64 0:2.17-324.0.1.el7_9 will be installed
--> Processing Dependency: kernel-headers >= 2.2.1 for package: glibc-headers-2.17-324.0.1.el7_9.x86_64
--> Processing Dependency: kernel-headers for package: glibc-headers-2.17-324.0.1.el7_9.x86_64
---> Package gssproxy.x86_64 0:0.7.0-30.el7_9 will be installed
--> Processing Dependency: libini_config >= 1.3.1-31 for package: gssproxy-0.7.0-30.el7_9.x86_64
--> Processing Dependency: libverto-module-base for package: gssproxy-0.7.0-30.el7_9.x86_64
--> Processing Dependency: libref_array.so.1(REF_ARRAY_0.1.1)(64bit) for package: gssproxy-0.7.0-30.el7_9.x86_64
--> Processing Dependency: libini_config.so.3(INI_CONFIG_1.2.0)(64bit) for package: gssproxy-0.7.0-30.el7_9.x86_64
--> Processing Dependency: libini_config.so.3(INI_CONFIG_1.1.0)(64bit) for package: gssproxy-0.7.0-30.el7_9.x86_64
--> Processing Dependency: libref_array.so.1()(64bit) for package: gssproxy-0.7.0-30.el7_9.x86_64
--> Processing Dependency: libini_config.so.3()(64bit) for package: gssproxy-0.7.0-30.el7_9.x86_64
--> Processing Dependency: libcollection.so.2()(64bit) for package: gssproxy-0.7.0-30.el7_9.x86_64
--> Processing Dependency: libbasicobjects.so.0()(64bit) for package: gssproxy-0.7.0-30.el7_9.x86_64
---> Package keyutils.x86_64 0:1.5.8-3.el7 will be installed
---> Package libX11.x86_64 0:1.6.7-4.el7_9 will be installed
--> Processing Dependency: libX11-common >= 1.6.7-4.el7_9 for package: libX11-1.6.7-4.el7_9.x86_64
---> Package libXau.x86_64 0:1.0.8-2.1.el7 will be installed
---> Package libXext.x86_64 0:1.3.3-3.el7 will be installed
---> Package libXi.x86_64 0:1.7.9-1.el7 will be installed
---> Package libXinerama.x86_64 0:1.1.3-2.1.el7 will be installed
---> Package libXmu.x86_64 0:1.1.2-2.el7 will be installed
--> Processing Dependency: libXt.so.6()(64bit) for package: libXmu-1.1.2-2.el7.x86_64
---> Package libXrandr.x86_64 0:1.5.1-2.el7 will be installed
---> Package libXrender.x86_64 0:0.9.10-1.el7 will be installed
---> Package libXtst.x86_64 0:1.2.3-1.el7 will be installed
---> Package libXv.x86_64 0:1.0.11-1.el7 will be installed
---> Package libXxf86dga.x86_64 0:1.1.4-2.1.el7 will be installed
---> Package libXxf86misc.x86_64 0:1.0.3-7.1.el7 will be installed
---> Package libXxf86vm.x86_64 0:1.1.4-1.el7 will be installed
---> Package libdmx.x86_64 0:1.1.3-3.el7 will be installed
---> Package libevent.x86_64 0:2.0.21-4.el7 will be installed
---> Package libnfsidmap.x86_64 0:0.25-19.el7 will be installed
---> Package libtirpc.x86_64 0:0.2.4-0.16.el7 will be installed
---> Package libxcb.x86_64 0:1.13-1.el7 will be installed
---> Package lm_sensors-libs.x86_64 0:3.4.0-8.20160601gitf9185e5.el7 will be installed
---> Package mailx.x86_64 0:12.5-19.el7 will be installed
---> Package quota.x86_64 1:4.01-19.el7 will be installed
--> Processing Dependency: quota-nls = 1:4.01-19.el7 for package: 1:quota-4.01-19.el7.x86_64
--> Processing Dependency: tcp_wrappers for package: 1:quota-4.01-19.el7.x86_64
---> Package rpcbind.x86_64 0:0.2.0-49.el7 will be installed
--> Running transaction check
---> Package bind-license.noarch 32:9.11.4-26.P2.el7_9.7 will be installed
---> Package geoipupdate.x86_64 0:2.5.0-1.el7 will be installed
---> Package glibc-common.x86_64 0:2.17-317.0.1.el7 will be updated
---> Package glibc-common.x86_64 0:2.17-324.0.1.el7_9 will be an update
---> Package kernel-headers.x86_64 0:3.10.0-1160.42.2.el7 will be installed
---> Package libX11-common.noarch 0:1.6.7-4.el7_9 will be installed
---> Package libXt.x86_64 0:1.1.5-3.el7 will be installed
--> Processing Dependency: libSM.so.6()(64bit) for package: libXt-1.1.5-3.el7.x86_64
--> Processing Dependency: libICE.so.6()(64bit) for package: libXt-1.1.5-3.el7.x86_64
---> Package libbasicobjects.x86_64 0:0.1.1-32.el7 will be installed
---> Package libcollection.x86_64 0:0.7.0-32.el7 will be installed
---> Package libini_config.x86_64 0:1.3.1-32.el7 will be installed
--> Processing Dependency: libpath_utils.so.1(PATH_UTILS_0.2.1)(64bit) for package: libini_config-1.3.1-32.el7.x86_64
--> Processing Dependency: libpath_utils.so.1()(64bit) for package: libini_config-1.3.1-32.el7.x86_64
---> Package libref_array.x86_64 0:0.1.5-32.el7 will be installed
---> Package libverto-libevent.x86_64 0:0.2.5-4.el7 will be installed
---> Package quota-nls.noarch 1:4.01-19.el7 will be installed
---> Package tcp_wrappers.x86_64 0:7.6-77.el7 will be installed
--> Running transaction check
---> Package libICE.x86_64 0:1.0.9-9.el7 will be installed
---> Package libSM.x86_64 0:1.2.2-2.el7 will be installed
---> Package libpath_utils.x86_64 0:0.2.1-32.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

=====================================================================================================
 Package                          Arch     Version                            Repository        Size
=====================================================================================================
Installing:
 oracle-database-preinstall-19c   x86_64   1.0-3.el7                          local-repo-ol7    27 k
Installing for dependencies:
 GeoIP                            x86_64   1.5.0-14.el7                       local-repo-ol7   1.5 M
 bind-libs                        x86_64   32:9.11.4-26.P2.el7_9.7            local-repo-ol7   157 k
 bind-libs-lite                   x86_64   32:9.11.4-26.P2.el7_9.7            local-repo-ol7   1.1 M
 bind-license                     noarch   32:9.11.4-26.P2.el7_9.7            local-repo-ol7    90 k
 bind-utils                       x86_64   32:9.11.4-26.P2.el7_9.7            local-repo-ol7   260 k
 compat-libcap1                   x86_64   1.10-7.el7                         local-repo-ol7    17 k
 geoipupdate                      x86_64   2.5.0-1.el7                        local-repo-ol7    34 k
 glibc-devel                      x86_64   2.17-324.0.1.el7_9                 local-repo-ol7   1.1 M
 glibc-headers                    x86_64   2.17-324.0.1.el7_9                 local-repo-ol7   693 k
 gssproxy                         x86_64   0.7.0-30.el7_9                     local-repo-ol7   110 k
 kernel-headers                   x86_64   3.10.0-1160.42.2.el7               local-repo-ol7   9.0 M
 keyutils                         x86_64   1.5.8-3.el7                        local-repo-ol7    53 k
 ksh                              x86_64   20120801-142.0.1.el7               local-repo-ol7   882 k
 libICE                           x86_64   1.0.9-9.el7                        local-repo-ol7    66 k
 libSM                            x86_64   1.2.2-2.el7                        local-repo-ol7    39 k
 libX11                           x86_64   1.6.7-4.el7_9                      local-repo-ol7   607 k
 libX11-common                    noarch   1.6.7-4.el7_9                      local-repo-ol7   164 k
 libXau                           x86_64   1.0.8-2.1.el7                      local-repo-ol7    28 k
 libXext                          x86_64   1.3.3-3.el7                        local-repo-ol7    38 k
 libXi                            x86_64   1.7.9-1.el7                        local-repo-ol7    40 k
 libXinerama                      x86_64   1.1.3-2.1.el7                      local-repo-ol7    13 k
 libXmu                           x86_64   1.1.2-2.el7                        local-repo-ol7    70 k
 libXrandr                        x86_64   1.5.1-2.el7                        local-repo-ol7    27 k
 libXrender                       x86_64   0.9.10-1.el7                       local-repo-ol7    25 k
 libXt                            x86_64   1.1.5-3.el7                        local-repo-ol7   172 k
 libXtst                          x86_64   1.2.3-1.el7                        local-repo-ol7    20 k
 libXv                            x86_64   1.0.11-1.el7                       local-repo-ol7    18 k
 libXxf86dga                      x86_64   1.1.4-2.1.el7                      local-repo-ol7    18 k
 libXxf86misc                     x86_64   1.0.3-7.1.el7                      local-repo-ol7    19 k
 libXxf86vm                       x86_64   1.1.4-1.el7                        local-repo-ol7    17 k
 libaio-devel                     x86_64   0.3.109-13.el7                     local-repo-ol7    12 k
 libbasicobjects                  x86_64   0.1.1-32.el7                       local-repo-ol7    25 k
 libcollection                    x86_64   0.7.0-32.el7                       local-repo-ol7    41 k
 libdmx                           x86_64   1.1.3-3.el7                        local-repo-ol7    15 k
 libevent                         x86_64   2.0.21-4.el7                       local-repo-ol7   208 k
 libini_config                    x86_64   1.3.1-32.el7                       local-repo-ol7    63 k
 libnfsidmap                      x86_64   0.25-19.el7                        local-repo-ol7    49 k
 libpath_utils                    x86_64   0.2.1-32.el7                       local-repo-ol7    28 k
 libref_array                     x86_64   0.1.5-32.el7                       local-repo-ol7    27 k
 libstdc++-devel                  x86_64   4.8.5-44.0.3.el7                   local-repo-ol7   1.5 M
 libtirpc                         x86_64   0.2.4-0.16.el7                     local-repo-ol7    89 k
 libverto-libevent                x86_64   0.2.5-4.el7                        local-repo-ol7   8.2 k
 libxcb                           x86_64   1.13-1.el7                         local-repo-ol7   213 k
 lm_sensors-libs                  x86_64   3.4.0-8.20160601gitf9185e5.el7     local-repo-ol7    41 k
 mailx                            x86_64   12.5-19.el7                        local-repo-ol7   244 k
 net-tools                        x86_64   2.0-0.25.20131004git.el7           local-repo-ol7   305 k
 nfs-utils                        x86_64   1:1.3.0-0.68.0.1.el7.1             local-repo-ol7   412 k
 psmisc                           x86_64   22.20-17.el7                       local-repo-ol7   141 k
 quota                            x86_64   1:4.01-19.el7                      local-repo-ol7   178 k
 quota-nls                        noarch   1:4.01-19.el7                      local-repo-ol7    90 k
 rpcbind                          x86_64   0.2.0-49.el7                       local-repo-ol7    59 k
 smartmontools                    x86_64   1:7.0-2.el7                        local-repo-ol7   546 k
 sysstat                          x86_64   10.1.5-19.el7                      local-repo-ol7   315 k
 tcp_wrappers                     x86_64   7.6-77.el7                         local-repo-ol7    78 k
 unzip                            x86_64   6.0-22.el7_9                       local-repo-ol7   171 k
 xorg-x11-utils                   x86_64   7.5-23.el7                         local-repo-ol7   114 k
 xorg-x11-xauth                   x86_64   1:1.0.9-1.el7                      local-repo-ol7    29 k
Updating for dependencies:
 glibc                            x86_64   2.17-324.0.1.el7_9                 local-repo-ol7   3.6 M
 glibc-common                     x86_64   2.17-324.0.1.el7_9                 local-repo-ol7    12 M

Transaction Summary
=====================================================================================================
Install  1 Package  (+57 Dependent packages)
Upgrade             (  2 Dependent packages)

Total download size: 37 M
Downloading packages:
-----------------------------------------------------------------------------------------------------
Total                                                                213 MB/s |  37 MB  00:00:00
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Updating   : glibc-common-2.17-324.0.1.el7_9.x86_64                                           1/62
  Updating   : glibc-2.17-324.0.1.el7_9.x86_64                                                  2/62
  Installing : libtirpc-0.2.4-0.16.el7.x86_64                                                   3/62
  Installing : rpcbind-0.2.0-49.el7.x86_64                                                      4/62
  Installing : libbasicobjects-0.1.1-32.el7.x86_64                                              5/62
  Installing : libevent-2.0.21-4.el7.x86_64                                                     6/62
  Installing : libref_array-0.1.5-32.el7.x86_64                                                 7/62
  Installing : libICE-1.0.9-9.el7.x86_64                                                        8/62
  Installing : libcollection-0.7.0-32.el7.x86_64                                                9/62
  Installing : libXau-1.0.8-2.1.el7.x86_64                                                     10/62
  Installing : libxcb-1.13-1.el7.x86_64                                                        11/62
  Installing : 32:bind-license-9.11.4-26.P2.el7_9.7.noarch                                     12/62
  Installing : libSM-1.2.2-2.el7.x86_64                                                        13/62
  Installing : libverto-libevent-0.2.5-4.el7.x86_64                                            14/62
  Installing : geoipupdate-2.5.0-1.el7.x86_64                                                  15/62
  Installing : GeoIP-1.5.0-14.el7.x86_64                                                       16/62
  Installing : 32:bind-libs-lite-9.11.4-26.P2.el7_9.7.x86_64                                   17/62
  Installing : 32:bind-libs-9.11.4-26.P2.el7_9.7.x86_64                                        18/62
  Installing : 32:bind-utils-9.11.4-26.P2.el7_9.7.x86_64                                       19/62
  Installing : net-tools-2.0-0.25.20131004git.el7.x86_64                                       20/62
  Installing : tcp_wrappers-7.6-77.el7.x86_64                                                  21/62
  Installing : libpath_utils-0.2.1-32.el7.x86_64                                               22/62
  Installing : libini_config-1.3.1-32.el7.x86_64                                               23/62
  Installing : gssproxy-0.7.0-30.el7_9.x86_64                                                  24/62
  Installing : ksh-20120801-142.0.1.el7.x86_64                                                 25/62
  Installing : compat-libcap1-1.10-7.el7.x86_64                                                26/62
  Installing : unzip-6.0-22.el7_9.x86_64                                                       27/62
  Installing : lm_sensors-libs-3.4.0-8.20160601gitf9185e5.el7.x86_64                           28/62
  Installing : sysstat-10.1.5-19.el7.x86_64                                                    29/62
  Installing : libnfsidmap-0.25-19.el7.x86_64                                                  30/62
  Installing : keyutils-1.5.8-3.el7.x86_64                                                     31/62
  Installing : mailx-12.5-19.el7.x86_64                                                        32/62
  Installing : 1:smartmontools-7.0-2.el7.x86_64                                                33/62
  Installing : psmisc-22.20-17.el7.x86_64                                                      34/62
  Installing : libX11-common-1.6.7-4.el7_9.noarch                                              35/62
  Installing : libX11-1.6.7-4.el7_9.x86_64                                                     36/62
  Installing : libXext-1.3.3-3.el7.x86_64                                                      37/62
  Installing : libXi-1.7.9-1.el7.x86_64                                                        38/62
  Installing : libXrender-0.9.10-1.el7.x86_64                                                  39/62
  Installing : libXrandr-1.5.1-2.el7.x86_64                                                    40/62
  Installing : libXtst-1.2.3-1.el7.x86_64                                                      41/62
  Installing : libXxf86misc-1.0.3-7.1.el7.x86_64                                               42/62
  Installing : libdmx-1.1.3-3.el7.x86_64                                                       43/62
  Installing : libXinerama-1.1.3-2.1.el7.x86_64                                                44/62
  Installing : libXv-1.0.11-1.el7.x86_64                                                       45/62
  Installing : libXxf86vm-1.1.4-1.el7.x86_64                                                   46/62
  Installing : libXxf86dga-1.1.4-2.1.el7.x86_64                                                47/62
  Installing : xorg-x11-utils-7.5-23.el7.x86_64                                                48/62
  Installing : libXt-1.1.5-3.el7.x86_64                                                        49/62
  Installing : libXmu-1.1.2-2.el7.x86_64                                                       50/62
  Installing : 1:xorg-x11-xauth-1.0.9-1.el7.x86_64                                             51/62
  Installing : 1:quota-nls-4.01-19.el7.noarch                                                  52/62
  Installing : 1:quota-4.01-19.el7.x86_64                                                      53/62
  Installing : 1:nfs-utils-1.3.0-0.68.0.1.el7.1.x86_64                                         54/62
  Installing : libaio-devel-0.3.109-13.el7.x86_64                                              55/62
  Installing : kernel-headers-3.10.0-1160.42.2.el7.x86_64                                      56/62
  Installing : glibc-headers-2.17-324.0.1.el7_9.x86_64                                         57/62
  Installing : glibc-devel-2.17-324.0.1.el7_9.x86_64                                           58/62
  Installing : libstdc++-devel-4.8.5-44.0.3.el7.x86_64                                         59/62
  Installing : oracle-database-preinstall-19c-1.0-3.el7.x86_64                                 60/62
  Cleanup    : glibc-common-2.17-317.0.1.el7.x86_64                                            61/62
  Cleanup    : glibc-2.17-317.0.1.el7.x86_64                                                   62/62
  Verifying  : libtirpc-0.2.4-0.16.el7.x86_64                                                   1/62
  Verifying  : gssproxy-0.7.0-30.el7_9.x86_64                                                   2/62
  Verifying  : libXxf86misc-1.0.3-7.1.el7.x86_64                                                3/62
  Verifying  : libdmx-1.1.3-3.el7.x86_64                                                        4/62
  Verifying  : libverto-libevent-0.2.5-4.el7.x86_64                                             5/62
  Verifying  : glibc-2.17-324.0.1.el7_9.x86_64                                                  6/62
  Verifying  : geoipupdate-2.5.0-1.el7.x86_64                                                   7/62
  Verifying  : libXinerama-1.1.3-2.1.el7.x86_64                                                 8/62
  Verifying  : libX11-1.6.7-4.el7_9.x86_64                                                      9/62
  Verifying  : libXrender-0.9.10-1.el7.x86_64                                                  10/62
  Verifying  : glibc-common-2.17-324.0.1.el7_9.x86_64                                          11/62
  Verifying  : libXv-1.0.11-1.el7.x86_64                                                       12/62
  Verifying  : libXi-1.7.9-1.el7.x86_64                                                        13/62
  Verifying  : libXxf86vm-1.1.4-1.el7.x86_64                                                   14/62
  Verifying  : net-tools-2.0-0.25.20131004git.el7.x86_64                                       15/62
  Verifying  : libbasicobjects-0.1.1-32.el7.x86_64                                             16/62
  Verifying  : 32:bind-utils-9.11.4-26.P2.el7_9.7.x86_64                                       17/62
  Verifying  : rpcbind-0.2.0-49.el7.x86_64                                                     18/62
  Verifying  : 32:bind-license-9.11.4-26.P2.el7_9.7.noarch                                     19/62
  Verifying  : GeoIP-1.5.0-14.el7.x86_64                                                       20/62
  Verifying  : glibc-devel-2.17-324.0.1.el7_9.x86_64                                           21/62
  Verifying  : sysstat-10.1.5-19.el7.x86_64                                                    22/62
  Verifying  : tcp_wrappers-7.6-77.el7.x86_64                                                  23/62
  Verifying  : xorg-x11-utils-7.5-23.el7.x86_64                                                24/62
  Verifying  : libXtst-1.2.3-1.el7.x86_64                                                      25/62
  Verifying  : libXt-1.1.5-3.el7.x86_64                                                        26/62
  Verifying  : 32:bind-libs-9.11.4-26.P2.el7_9.7.x86_64                                        27/62
  Verifying  : libxcb-1.13-1.el7.x86_64                                                        28/62
  Verifying  : libstdc++-devel-4.8.5-44.0.3.el7.x86_64                                         29/62
  Verifying  : 32:bind-libs-lite-9.11.4-26.P2.el7_9.7.x86_64                                   30/62
  Verifying  : 1:nfs-utils-1.3.0-0.68.0.1.el7.1.x86_64                                         31/62
  Verifying  : glibc-headers-2.17-324.0.1.el7_9.x86_64                                         32/62
  Verifying  : 1:smartmontools-7.0-2.el7.x86_64                                                33/62
  Verifying  : libXext-1.3.3-3.el7.x86_64                                                      34/62
  Verifying  : libpath_utils-0.2.1-32.el7.x86_64                                               35/62
  Verifying  : libevent-2.0.21-4.el7.x86_64                                                    36/62
  Verifying  : oracle-database-preinstall-19c-1.0-3.el7.x86_64                                 37/62
  Verifying  : ksh-20120801-142.0.1.el7.x86_64                                                 38/62
  Verifying  : kernel-headers-3.10.0-1160.42.2.el7.x86_64                                      39/62
  Verifying  : compat-libcap1-1.10-7.el7.x86_64                                                40/62
  Verifying  : libXrandr-1.5.1-2.el7.x86_64                                                    41/62
  Verifying  : libaio-devel-0.3.109-13.el7.x86_64                                              42/62
  Verifying  : libref_array-0.1.5-32.el7.x86_64                                                43/62
  Verifying  : 1:xorg-x11-xauth-1.0.9-1.el7.x86_64                                             44/62
  Verifying  : libICE-1.0.9-9.el7.x86_64                                                       45/62
  Verifying  : unzip-6.0-22.el7_9.x86_64                                                       46/62
  Verifying  : 1:quota-4.01-19.el7.x86_64                                                      47/62
  Verifying  : lm_sensors-libs-3.4.0-8.20160601gitf9185e5.el7.x86_64                           48/62
  Verifying  : libnfsidmap-0.25-19.el7.x86_64                                                  49/62
  Verifying  : libSM-1.2.2-2.el7.x86_64                                                        50/62
  Verifying  : libXxf86dga-1.1.4-2.1.el7.x86_64                                                51/62
  Verifying  : libXmu-1.1.2-2.el7.x86_64                                                       52/62
  Verifying  : keyutils-1.5.8-3.el7.x86_64                                                     53/62
  Verifying  : libini_config-1.3.1-32.el7.x86_64                                               54/62
  Verifying  : libcollection-0.7.0-32.el7.x86_64                                               55/62
  Verifying  : libXau-1.0.8-2.1.el7.x86_64                                                     56/62
  Verifying  : 1:quota-nls-4.01-19.el7.noarch                                                  57/62
  Verifying  : mailx-12.5-19.el7.x86_64                                                        58/62
  Verifying  : psmisc-22.20-17.el7.x86_64                                                      59/62
  Verifying  : libX11-common-1.6.7-4.el7_9.noarch                                              60/62
  Verifying  : glibc-common-2.17-317.0.1.el7.x86_64                                            61/62
  Verifying  : glibc-2.17-317.0.1.el7.x86_64                                                   62/62

Installed:
  oracle-database-preinstall-19c.x86_64 0:1.0-3.el7

Dependency Installed:
  GeoIP.x86_64 0:1.5.0-14.el7
  bind-libs.x86_64 32:9.11.4-26.P2.el7_9.7
  bind-libs-lite.x86_64 32:9.11.4-26.P2.el7_9.7
  bind-license.noarch 32:9.11.4-26.P2.el7_9.7
  bind-utils.x86_64 32:9.11.4-26.P2.el7_9.7
  compat-libcap1.x86_64 0:1.10-7.el7
  geoipupdate.x86_64 0:2.5.0-1.el7
  glibc-devel.x86_64 0:2.17-324.0.1.el7_9
  glibc-headers.x86_64 0:2.17-324.0.1.el7_9
  gssproxy.x86_64 0:0.7.0-30.el7_9
  kernel-headers.x86_64 0:3.10.0-1160.42.2.el7
  keyutils.x86_64 0:1.5.8-3.el7
  ksh.x86_64 0:20120801-142.0.1.el7
  libICE.x86_64 0:1.0.9-9.el7
  libSM.x86_64 0:1.2.2-2.el7
  libX11.x86_64 0:1.6.7-4.el7_9
  libX11-common.noarch 0:1.6.7-4.el7_9
  libXau.x86_64 0:1.0.8-2.1.el7
  libXext.x86_64 0:1.3.3-3.el7
  libXi.x86_64 0:1.7.9-1.el7
  libXinerama.x86_64 0:1.1.3-2.1.el7
  libXmu.x86_64 0:1.1.2-2.el7
  libXrandr.x86_64 0:1.5.1-2.el7
  libXrender.x86_64 0:0.9.10-1.el7
  libXt.x86_64 0:1.1.5-3.el7
  libXtst.x86_64 0:1.2.3-1.el7
  libXv.x86_64 0:1.0.11-1.el7
  libXxf86dga.x86_64 0:1.1.4-2.1.el7
  libXxf86misc.x86_64 0:1.0.3-7.1.el7
  libXxf86vm.x86_64 0:1.1.4-1.el7
  libaio-devel.x86_64 0:0.3.109-13.el7
  libbasicobjects.x86_64 0:0.1.1-32.el7
  libcollection.x86_64 0:0.7.0-32.el7
  libdmx.x86_64 0:1.1.3-3.el7
  libevent.x86_64 0:2.0.21-4.el7
  libini_config.x86_64 0:1.3.1-32.el7
  libnfsidmap.x86_64 0:0.25-19.el7
  libpath_utils.x86_64 0:0.2.1-32.el7
  libref_array.x86_64 0:0.1.5-32.el7
  libstdc++-devel.x86_64 0:4.8.5-44.0.3.el7
  libtirpc.x86_64 0:0.2.4-0.16.el7
  libverto-libevent.x86_64 0:0.2.5-4.el7
  libxcb.x86_64 0:1.13-1.el7
  lm_sensors-libs.x86_64 0:3.4.0-8.20160601gitf9185e5.el7
  mailx.x86_64 0:12.5-19.el7
  net-tools.x86_64 0:2.0-0.25.20131004git.el7
  nfs-utils.x86_64 1:1.3.0-0.68.0.1.el7.1
  psmisc.x86_64 0:22.20-17.el7
  quota.x86_64 1:4.01-19.el7
  quota-nls.noarch 1:4.01-19.el7
  rpcbind.x86_64 0:0.2.0-49.el7
  smartmontools.x86_64 1:7.0-2.el7
  sysstat.x86_64 0:10.1.5-19.el7
  tcp_wrappers.x86_64 0:7.6-77.el7
  unzip.x86_64 0:6.0-22.el7_9
  xorg-x11-utils.x86_64 0:7.5-23.el7
  xorg-x11-xauth.x86_64 1:1.0.9-1.el7

Dependency Updated:
  glibc.x86_64 0:2.17-324.0.1.el7_9             glibc-common.x86_64 0:2.17-324.0.1.el7_9

Complete!
[root@localhost repo]#
```
