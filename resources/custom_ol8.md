```
[root@localhost repo]# yum repolist
repo id                                                                                                   repo name
local-repo-custom                                                                                         LocalCustom
[root@localhost repo]# yum install oracle-database-preinstall-19c
LocalCustom                                                                                                                                                                   213 MB/s | 427 kB     00:00
Dependencies resolved.
==============================================================================================================================================================================================================
 Package                                                   Architecture                      Version                                                       Repository                                    Size
==============================================================================================================================================================================================================
Installing:
 oracle-database-preinstall-19c                            x86_64                            1.0-2.el8                                                     local-repo-custom                             31 k
Upgrading:
 libstdc++                                                 x86_64                            8.4.1-1.0.3.el8                                               local-repo-custom                            458 k
Installing dependencies:
 bc                                                        x86_64                            1.07.1-5.el8                                                  local-repo-custom                            129 k
 bind-libs                                                 x86_64                            32:9.11.26-4.el8_4                                            local-repo-custom                            174 k
 bind-libs-lite                                            x86_64                            32:9.11.26-4.el8_4                                            local-repo-custom                            1.2 M
 bind-license                                              noarch                            32:9.11.26-4.el8_4                                            local-repo-custom                            102 k
 bind-utils                                                x86_64                            32:9.11.26-4.el8_4                                            local-repo-custom                            451 k
 binutils                                                  x86_64                            2.30-93.0.3.el8                                               local-repo-custom                            5.9 M
 fstrm                                                     x86_64                            0.6.0-3.el8.1                                                 local-repo-custom                             29 k
 glibc-devel                                               x86_64                            2.28-151.0.1.el8                                              local-repo-custom                            1.0 M
 glibc-headers                                             x86_64                            2.28-151.0.1.el8                                              local-repo-custom                            479 k
 gssproxy                                                  x86_64                            0.8.0-19.el8                                                  local-repo-custom                            119 k
 kernel-headers                                            x86_64                            4.18.0-305.19.1.el8_4                                         local-repo-custom                            7.1 M
 keyutils                                                  x86_64                            1.5.10-6.el8                                                  local-repo-custom                             63 k
 ksh                                                       x86_64                            20120801-254.0.1.el8                                          local-repo-custom                            927 k
 libICE                                                    x86_64                            1.0.9-15.el8                                                  local-repo-custom                             74 k
 libSM                                                     x86_64                            1.2.3-1.el8                                                   local-repo-custom                             47 k
 libX11                                                    x86_64                            1.6.8-4.el8                                                   local-repo-custom                            611 k
 libX11-common                                             noarch                            1.6.8-4.el8                                                   local-repo-custom                            158 k
 libX11-xcb                                                x86_64                            1.6.8-4.el8                                                   local-repo-custom                             14 k
 libXau                                                    x86_64                            1.0.9-3.el8                                                   local-repo-custom                             37 k
 libXcomposite                                             x86_64                            0.4.4-14.el8                                                  local-repo-custom                             28 k
 libXext                                                   x86_64                            1.3.4-1.el8                                                   local-repo-custom                             45 k
 libXi                                                     x86_64                            1.7.10-1.el8                                                  local-repo-custom                             49 k
 libXinerama                                               x86_64                            1.1.4-1.el8                                                   local-repo-custom                             15 k
 libXmu                                                    x86_64                            1.1.3-1.el8                                                   local-repo-custom                             75 k
 libXrandr                                                 x86_64                            1.5.2-1.el8                                                   local-repo-custom                             34 k
 libXrender                                                x86_64                            0.9.10-7.el8                                                  local-repo-custom                             33 k
 libXt                                                     x86_64                            1.1.5-12.el8                                                  local-repo-custom                            185 k
 libXtst                                                   x86_64                            1.2.3-7.el8                                                   local-repo-custom                             22 k
 libXv                                                     x86_64                            1.0.11-7.el8                                                  local-repo-custom                             20 k
 libXxf86dga                                               x86_64                            1.1.5-1.el8                                                   local-repo-custom                             26 k
 libXxf86misc                                              x86_64                            1.0.4-1.el8                                                   local-repo-custom                             23 k
 libXxf86vm                                                x86_64                            1.1.4-9.el8                                                   local-repo-custom                             19 k
 libaio-devel                                              x86_64                            0.3.112-1.el8                                                 local-repo-custom                             19 k
 libdmx                                                    x86_64                            1.1.4-3.el8                                                   local-repo-custom                             22 k
 libmaxminddb                                              x86_64                            1.2.0-10.el8                                                  local-repo-custom                             33 k
 libnsl                                                    x86_64                            2.28-151.0.1.el8                                              local-repo-custom                            102 k
 libpkgconf                                                x86_64                            1.4.2-1.el8                                                   local-repo-custom                             35 k
 libstdc++-devel                                           x86_64                            8.4.1-1.0.3.el8                                               local-repo-custom                            2.1 M
 libverto-libevent                                         x86_64                            0.3.0-5.el8                                                   local-repo-custom                             16 k
 libxcb                                                    x86_64                            1.13.1-1.el8                                                  local-repo-custom                            231 k
 libxcrypt-devel                                           x86_64                            4.1.1-4.el8                                                   local-repo-custom                             25 k
 lm_sensors-libs                                           x86_64                            3.4.0-22.20180522git70f7e08.el8                               local-repo-custom                             59 k
 make                                                      x86_64                            1:4.2.1-10.el8                                                local-repo-custom                            498 k
 net-tools                                                 x86_64                            2.0-0.52.20160912git.el8                                      local-repo-custom                            322 k
 nfs-utils                                                 x86_64                            1:2.3.3-41.el8_4.2                                            local-repo-custom                            498 k
 pkgconf                                                   x86_64                            1.4.2-1.el8                                                   local-repo-custom                             38 k
 pkgconf-m4                                                noarch                            1.4.2-1.el8                                                   local-repo-custom                             17 k
 pkgconf-pkg-config                                        x86_64                            1.4.2-1.el8                                                   local-repo-custom                             15 k
 protobuf-c                                                x86_64                            1.3.0-6.el8                                                   local-repo-custom                             37 k
 psmisc                                                    x86_64                            23.1-5.el8                                                    local-repo-custom                            151 k
 python3-bind                                              noarch                            32:9.11.26-4.el8_4                                            local-repo-custom                            149 k
 python3-pyyaml                                            x86_64                            3.12-12.el8                                                   local-repo-custom                            193 k
 quota                                                     x86_64                            1:4.04-12.el8                                                 local-repo-custom                            213 k
 quota-nls                                                 noarch                            1:4.04-12.el8                                                 local-repo-custom                             95 k
 rpcbind                                                   x86_64                            1.2.5-8.el8                                                   local-repo-custom                             70 k
 smartmontools                                             x86_64                            1:7.1-1.el8                                                   local-repo-custom                            544 k
 sysstat                                                   x86_64                            11.7.3-5.0.1.el8                                              local-repo-custom                            425 k
 unzip                                                     x86_64                            6.0-45.el8_4                                                  local-repo-custom                            195 k
 xorg-x11-utils                                            x86_64                            7.5-28.el8                                                    local-repo-custom                            136 k
 xorg-x11-xauth                                            x86_64                            1:1.0.9-12.el8                                                local-repo-custom                             39 k

Transaction Summary
==============================================================================================================================================================================================================
Install  61 Packages
Upgrade   1 Package

Total size: 26 M
Is this ok [y/N]: y
Downloading Packages:
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                                                                                      1/1
  Upgrading        : libstdc++-8.4.1-1.0.3.el8.x86_64                                                                                                                                                    1/63
  Running scriptlet: libstdc++-8.4.1-1.0.3.el8.x86_64                                                                                                                                                    1/63
/sbin/ldconfig: /etc/ld.so.conf.d/kernel-5.4.17-2102.201.3.el8uek.x86_64.conf:6: hwcap directive ignored

  Installing       : protobuf-c-1.3.0-6.el8.x86_64                                                                                                                                                       2/63
  Installing       : libmaxminddb-1.2.0-10.el8.x86_64                                                                                                                                                    3/63
  Running scriptlet: libmaxminddb-1.2.0-10.el8.x86_64                                                                                                                                                    3/63
/sbin/ldconfig: /etc/ld.so.conf.d/kernel-5.4.17-2102.201.3.el8uek.x86_64.conf:6: hwcap directive ignored

  Installing       : fstrm-0.6.0-3.el8.1.x86_64                                                                                                                                                          4/63
  Installing       : bind-license-32:9.11.26-4.el8_4.noarch                                                                                                                                              5/63
  Installing       : bind-libs-lite-32:9.11.26-4.el8_4.x86_64                                                                                                                                            6/63
  Installing       : libXau-1.0.9-3.el8.x86_64                                                                                                                                                           7/63
  Installing       : libxcb-1.13.1-1.el8.x86_64                                                                                                                                                          8/63
  Installing       : libICE-1.0.9-15.el8.x86_64                                                                                                                                                          9/63
  Installing       : libSM-1.2.3-1.el8.x86_64                                                                                                                                                           10/63
  Installing       : bind-libs-32:9.11.26-4.el8_4.x86_64                                                                                                                                                11/63
  Installing       : python3-bind-32:9.11.26-4.el8_4.noarch                                                                                                                                             12/63
  Installing       : bind-utils-32:9.11.26-4.el8_4.x86_64                                                                                                                                               13/63
  Installing       : binutils-2.30-93.0.3.el8.x86_64                                                                                                                                                    14/63
  Running scriptlet: binutils-2.30-93.0.3.el8.x86_64                                                                                                                                                    14/63
/sbin/ldconfig: /etc/ld.so.conf.d/kernel-5.4.17-2102.201.3.el8uek.x86_64.conf:6: hwcap directive ignored

  Installing       : libstdc++-devel-8.4.1-1.0.3.el8.x86_64                                                                                                                                             15/63
  Running scriptlet: smartmontools-1:7.1-1.el8.x86_64                                                                                                                                                   16/63
  Installing       : smartmontools-1:7.1-1.el8.x86_64                                                                                                                                                   16/63
  Running scriptlet: smartmontools-1:7.1-1.el8.x86_64                                                                                                                                                   16/63
  Installing       : unzip-6.0-45.el8_4.x86_64                                                                                                                                                          17/63
  Running scriptlet: rpcbind-1.2.5-8.el8.x86_64                                                                                                                                                         18/63
  Installing       : rpcbind-1.2.5-8.el8.x86_64                                                                                                                                                         18/63
  Running scriptlet: rpcbind-1.2.5-8.el8.x86_64                                                                                                                                                         18/63
  Installing       : quota-nls-1:4.04-12.el8.noarch                                                                                                                                                     19/63
  Installing       : quota-1:4.04-12.el8.x86_64                                                                                                                                                         20/63
  Installing       : python3-pyyaml-3.12-12.el8.x86_64                                                                                                                                                  21/63
  Installing       : psmisc-23.1-5.el8.x86_64                                                                                                                                                           22/63
  Installing       : pkgconf-m4-1.4.2-1.el8.noarch                                                                                                                                                      23/63
  Installing       : net-tools-2.0-0.52.20160912git.el8.x86_64                                                                                                                                          24/63
  Running scriptlet: net-tools-2.0-0.52.20160912git.el8.x86_64                                                                                                                                          24/63
  Installing       : make-1:4.2.1-10.el8.x86_64                                                                                                                                                         25/63
  Running scriptlet: make-1:4.2.1-10.el8.x86_64                                                                                                                                                         25/63
  Installing       : lm_sensors-libs-3.4.0-22.20180522git70f7e08.el8.x86_64                                                                                                                             26/63
  Running scriptlet: lm_sensors-libs-3.4.0-22.20180522git70f7e08.el8.x86_64                                                                                                                             26/63
/sbin/ldconfig: /etc/ld.so.conf.d/kernel-5.4.17-2102.201.3.el8uek.x86_64.conf:6: hwcap directive ignored

  Installing       : sysstat-11.7.3-5.0.1.el8.x86_64                                                                                                                                                    27/63
  Running scriptlet: sysstat-11.7.3-5.0.1.el8.x86_64                                                                                                                                                    27/63
  Installing       : libverto-libevent-0.3.0-5.el8.x86_64                                                                                                                                               28/63
  Installing       : gssproxy-0.8.0-19.el8.x86_64                                                                                                                                                       29/63
  Running scriptlet: gssproxy-0.8.0-19.el8.x86_64                                                                                                                                                       29/63
  Installing       : libpkgconf-1.4.2-1.el8.x86_64                                                                                                                                                      30/63
  Installing       : pkgconf-1.4.2-1.el8.x86_64                                                                                                                                                         31/63
  Installing       : pkgconf-pkg-config-1.4.2-1.el8.x86_64                                                                                                                                              32/63
  Installing       : libnsl-2.28-151.0.1.el8.x86_64                                                                                                                                                     33/63
  Installing       : libaio-devel-0.3.112-1.el8.x86_64                                                                                                                                                  34/63
  Installing       : libX11-xcb-1.6.8-4.el8.x86_64                                                                                                                                                      35/63
  Installing       : libX11-common-1.6.8-4.el8.noarch                                                                                                                                                   36/63
  Installing       : libX11-1.6.8-4.el8.x86_64                                                                                                                                                          37/63
  Installing       : libXext-1.3.4-1.el8.x86_64                                                                                                                                                         38/63
  Installing       : libXi-1.7.10-1.el8.x86_64                                                                                                                                                          39/63
  Installing       : libXrender-0.9.10-7.el8.x86_64                                                                                                                                                     40/63
  Installing       : libXrandr-1.5.2-1.el8.x86_64                                                                                                                                                       41/63
  Installing       : libXtst-1.2.3-7.el8.x86_64                                                                                                                                                         42/63
  Installing       : libXinerama-1.1.4-1.el8.x86_64                                                                                                                                                     43/63
  Installing       : libXv-1.0.11-7.el8.x86_64                                                                                                                                                          44/63
  Installing       : libXxf86dga-1.1.5-1.el8.x86_64                                                                                                                                                     45/63
  Installing       : libXxf86misc-1.0.4-1.el8.x86_64                                                                                                                                                    46/63
  Installing       : libXxf86vm-1.1.4-9.el8.x86_64                                                                                                                                                      47/63
  Installing       : libdmx-1.1.4-3.el8.x86_64                                                                                                                                                          48/63
  Installing       : libXcomposite-0.4.4-14.el8.x86_64                                                                                                                                                  49/63
  Installing       : xorg-x11-utils-7.5-28.el8.x86_64                                                                                                                                                   50/63
  Installing       : libXt-1.1.5-12.el8.x86_64                                                                                                                                                          51/63
  Installing       : libXmu-1.1.3-1.el8.x86_64                                                                                                                                                          52/63
  Installing       : xorg-x11-xauth-1:1.0.9-12.el8.x86_64                                                                                                                                               53/63
  Installing       : ksh-20120801-254.0.1.el8.x86_64                                                                                                                                                    54/63
  Running scriptlet: ksh-20120801-254.0.1.el8.x86_64                                                                                                                                                    54/63
  Installing       : keyutils-1.5.10-6.el8.x86_64                                                                                                                                                       55/63
  Running scriptlet: nfs-utils-1:2.3.3-41.el8_4.2.x86_64                                                                                                                                                56/63
  Installing       : nfs-utils-1:2.3.3-41.el8_4.2.x86_64                                                                                                                                                56/63
  Running scriptlet: nfs-utils-1:2.3.3-41.el8_4.2.x86_64                                                                                                                                                56/63
  Installing       : kernel-headers-4.18.0-305.19.1.el8_4.x86_64                                                                                                                                        57/63
  Running scriptlet: glibc-headers-2.28-151.0.1.el8.x86_64                                                                                                                                              58/63
  Installing       : glibc-headers-2.28-151.0.1.el8.x86_64                                                                                                                                              58/63
  Installing       : libxcrypt-devel-4.1.1-4.el8.x86_64                                                                                                                                                 59/63
  Installing       : glibc-devel-2.28-151.0.1.el8.x86_64                                                                                                                                                60/63
  Running scriptlet: glibc-devel-2.28-151.0.1.el8.x86_64                                                                                                                                                60/63
  Installing       : bc-1.07.1-5.el8.x86_64                                                                                                                                                             61/63
  Running scriptlet: bc-1.07.1-5.el8.x86_64                                                                                                                                                             61/63
  Running scriptlet: oracle-database-preinstall-19c-1.0-2.el8.x86_64                                                                                                                                    62/63
  Installing       : oracle-database-preinstall-19c-1.0-2.el8.x86_64                                                                                                                                    62/63
  Cleanup          : libstdc++-8.4.1-1.0.1.el8.x86_64                                                                                                                                                   63/63
  Running scriptlet: libstdc++-8.4.1-1.0.1.el8.x86_64                                                                                                                                                   63/63
/sbin/ldconfig: /etc/ld.so.conf.d/kernel-5.4.17-2102.201.3.el8uek.x86_64.conf:6: hwcap directive ignored

  Running scriptlet: oracle-database-preinstall-19c-1.0-2.el8.x86_64                                                                                                                                    63/63
  Running scriptlet: libstdc++-8.4.1-1.0.1.el8.x86_64                                                                                                                                                   63/63
/sbin/ldconfig: /etc/ld.so.conf.d/kernel-5.4.17-2102.201.3.el8uek.x86_64.conf:6: hwcap directive ignored

/sbin/ldconfig: /etc/ld.so.conf.d/kernel-5.4.17-2102.201.3.el8uek.x86_64.conf:6: hwcap directive ignored

  Verifying        : bc-1.07.1-5.el8.x86_64                                                                                                                                                              1/63
  Verifying        : bind-libs-32:9.11.26-4.el8_4.x86_64                                                                                                                                                 2/63
  Verifying        : bind-libs-lite-32:9.11.26-4.el8_4.x86_64                                                                                                                                            3/63
  Verifying        : bind-license-32:9.11.26-4.el8_4.noarch                                                                                                                                              4/63
  Verifying        : bind-utils-32:9.11.26-4.el8_4.x86_64                                                                                                                                                5/63
  Verifying        : binutils-2.30-93.0.3.el8.x86_64                                                                                                                                                     6/63
  Verifying        : fstrm-0.6.0-3.el8.1.x86_64                                                                                                                                                          7/63
  Verifying        : glibc-devel-2.28-151.0.1.el8.x86_64                                                                                                                                                 8/63
  Verifying        : glibc-headers-2.28-151.0.1.el8.x86_64                                                                                                                                               9/63
  Verifying        : gssproxy-0.8.0-19.el8.x86_64                                                                                                                                                       10/63
  Verifying        : kernel-headers-4.18.0-305.19.1.el8_4.x86_64                                                                                                                                        11/63
  Verifying        : keyutils-1.5.10-6.el8.x86_64                                                                                                                                                       12/63
  Verifying        : ksh-20120801-254.0.1.el8.x86_64                                                                                                                                                    13/63
  Verifying        : libICE-1.0.9-15.el8.x86_64                                                                                                                                                         14/63
  Verifying        : libSM-1.2.3-1.el8.x86_64                                                                                                                                                           15/63
  Verifying        : libX11-1.6.8-4.el8.x86_64                                                                                                                                                          16/63
  Verifying        : libX11-common-1.6.8-4.el8.noarch                                                                                                                                                   17/63
  Verifying        : libX11-xcb-1.6.8-4.el8.x86_64                                                                                                                                                      18/63
  Verifying        : libXau-1.0.9-3.el8.x86_64                                                                                                                                                          19/63
  Verifying        : libXcomposite-0.4.4-14.el8.x86_64                                                                                                                                                  20/63
  Verifying        : libXext-1.3.4-1.el8.x86_64                                                                                                                                                         21/63
  Verifying        : libXi-1.7.10-1.el8.x86_64                                                                                                                                                          22/63
  Verifying        : libXinerama-1.1.4-1.el8.x86_64                                                                                                                                                     23/63
  Verifying        : libXmu-1.1.3-1.el8.x86_64                                                                                                                                                          24/63
  Verifying        : libXrandr-1.5.2-1.el8.x86_64                                                                                                                                                       25/63
  Verifying        : libXrender-0.9.10-7.el8.x86_64                                                                                                                                                     26/63
  Verifying        : libXt-1.1.5-12.el8.x86_64                                                                                                                                                          27/63
  Verifying        : libXtst-1.2.3-7.el8.x86_64                                                                                                                                                         28/63
  Verifying        : libXv-1.0.11-7.el8.x86_64                                                                                                                                                          29/63
  Verifying        : libXxf86dga-1.1.5-1.el8.x86_64                                                                                                                                                     30/63
  Verifying        : libXxf86misc-1.0.4-1.el8.x86_64                                                                                                                                                    31/63
  Verifying        : libXxf86vm-1.1.4-9.el8.x86_64                                                                                                                                                      32/63
  Verifying        : libaio-devel-0.3.112-1.el8.x86_64                                                                                                                                                  33/63
  Verifying        : libdmx-1.1.4-3.el8.x86_64                                                                                                                                                          34/63
  Verifying        : libmaxminddb-1.2.0-10.el8.x86_64                                                                                                                                                   35/63
  Verifying        : libnsl-2.28-151.0.1.el8.x86_64                                                                                                                                                     36/63
  Verifying        : libpkgconf-1.4.2-1.el8.x86_64                                                                                                                                                      37/63
  Verifying        : libstdc++-devel-8.4.1-1.0.3.el8.x86_64                                                                                                                                             38/63
  Verifying        : libverto-libevent-0.3.0-5.el8.x86_64                                                                                                                                               39/63
  Verifying        : libxcb-1.13.1-1.el8.x86_64                                                                                                                                                         40/63
  Verifying        : libxcrypt-devel-4.1.1-4.el8.x86_64                                                                                                                                                 41/63
  Verifying        : lm_sensors-libs-3.4.0-22.20180522git70f7e08.el8.x86_64                                                                                                                             42/63
  Verifying        : make-1:4.2.1-10.el8.x86_64                                                                                                                                                         43/63
  Verifying        : net-tools-2.0-0.52.20160912git.el8.x86_64                                                                                                                                          44/63
  Verifying        : nfs-utils-1:2.3.3-41.el8_4.2.x86_64                                                                                                                                                45/63
  Verifying        : oracle-database-preinstall-19c-1.0-2.el8.x86_64                                                                                                                                    46/63
  Verifying        : pkgconf-1.4.2-1.el8.x86_64                                                                                                                                                         47/63
  Verifying        : pkgconf-m4-1.4.2-1.el8.noarch                                                                                                                                                      48/63
  Verifying        : pkgconf-pkg-config-1.4.2-1.el8.x86_64                                                                                                                                              49/63
  Verifying        : protobuf-c-1.3.0-6.el8.x86_64                                                                                                                                                      50/63
  Verifying        : psmisc-23.1-5.el8.x86_64                                                                                                                                                           51/63
  Verifying        : python3-bind-32:9.11.26-4.el8_4.noarch                                                                                                                                             52/63
  Verifying        : python3-pyyaml-3.12-12.el8.x86_64                                                                                                                                                  53/63
  Verifying        : quota-1:4.04-12.el8.x86_64                                                                                                                                                         54/63
  Verifying        : quota-nls-1:4.04-12.el8.noarch                                                                                                                                                     55/63
  Verifying        : rpcbind-1.2.5-8.el8.x86_64                                                                                                                                                         56/63
  Verifying        : smartmontools-1:7.1-1.el8.x86_64                                                                                                                                                   57/63
  Verifying        : sysstat-11.7.3-5.0.1.el8.x86_64                                                                                                                                                    58/63
  Verifying        : unzip-6.0-45.el8_4.x86_64                                                                                                                                                          59/63
  Verifying        : xorg-x11-utils-7.5-28.el8.x86_64                                                                                                                                                   60/63
  Verifying        : xorg-x11-xauth-1:1.0.9-12.el8.x86_64                                                                                                                                               61/63
  Verifying        : libstdc++-8.4.1-1.0.3.el8.x86_64                                                                                                                                                   62/63
  Verifying        : libstdc++-8.4.1-1.0.1.el8.x86_64                                                                                                                                                   63/63

Upgraded:
  libstdc++-8.4.1-1.0.3.el8.x86_64
Installed:
  bc-1.07.1-5.el8.x86_64                      bind-libs-32:9.11.26-4.el8_4.x86_64                          bind-libs-lite-32:9.11.26-4.el8_4.x86_64          bind-license-32:9.11.26-4.el8_4.noarch
  bind-utils-32:9.11.26-4.el8_4.x86_64        binutils-2.30-93.0.3.el8.x86_64                              fstrm-0.6.0-3.el8.1.x86_64                        glibc-devel-2.28-151.0.1.el8.x86_64
  glibc-headers-2.28-151.0.1.el8.x86_64       gssproxy-0.8.0-19.el8.x86_64                                 kernel-headers-4.18.0-305.19.1.el8_4.x86_64       keyutils-1.5.10-6.el8.x86_64
  ksh-20120801-254.0.1.el8.x86_64             libICE-1.0.9-15.el8.x86_64                                   libSM-1.2.3-1.el8.x86_64                          libX11-1.6.8-4.el8.x86_64
  libX11-common-1.6.8-4.el8.noarch            libX11-xcb-1.6.8-4.el8.x86_64                                libXau-1.0.9-3.el8.x86_64                         libXcomposite-0.4.4-14.el8.x86_64
  libXext-1.3.4-1.el8.x86_64                  libXi-1.7.10-1.el8.x86_64                                    libXinerama-1.1.4-1.el8.x86_64                    libXmu-1.1.3-1.el8.x86_64
  libXrandr-1.5.2-1.el8.x86_64                libXrender-0.9.10-7.el8.x86_64                               libXt-1.1.5-12.el8.x86_64                         libXtst-1.2.3-7.el8.x86_64
  libXv-1.0.11-7.el8.x86_64                   libXxf86dga-1.1.5-1.el8.x86_64                               libXxf86misc-1.0.4-1.el8.x86_64                   libXxf86vm-1.1.4-9.el8.x86_64
  libaio-devel-0.3.112-1.el8.x86_64           libdmx-1.1.4-3.el8.x86_64                                    libmaxminddb-1.2.0-10.el8.x86_64                  libnsl-2.28-151.0.1.el8.x86_64
  libpkgconf-1.4.2-1.el8.x86_64               libstdc++-devel-8.4.1-1.0.3.el8.x86_64                       libverto-libevent-0.3.0-5.el8.x86_64              libxcb-1.13.1-1.el8.x86_64
  libxcrypt-devel-4.1.1-4.el8.x86_64          lm_sensors-libs-3.4.0-22.20180522git70f7e08.el8.x86_64       make-1:4.2.1-10.el8.x86_64                        net-tools-2.0-0.52.20160912git.el8.x86_64
  nfs-utils-1:2.3.3-41.el8_4.2.x86_64         oracle-database-preinstall-19c-1.0-2.el8.x86_64              pkgconf-1.4.2-1.el8.x86_64                        pkgconf-m4-1.4.2-1.el8.noarch
  pkgconf-pkg-config-1.4.2-1.el8.x86_64       protobuf-c-1.3.0-6.el8.x86_64                                psmisc-23.1-5.el8.x86_64                          python3-bind-32:9.11.26-4.el8_4.noarch
  python3-pyyaml-3.12-12.el8.x86_64           quota-1:4.04-12.el8.x86_64                                   quota-nls-1:4.04-12.el8.noarch                    rpcbind-1.2.5-8.el8.x86_64
  smartmontools-1:7.1-1.el8.x86_64            sysstat-11.7.3-5.0.1.el8.x86_64                              unzip-6.0-45.el8_4.x86_64                         xorg-x11-utils-7.5-28.el8.x86_64
  xorg-x11-xauth-1:1.0.9-12.el8.x86_64

Complete!
[root@localhost repo]#
```
