```
[root@localhost repo]# yum repolist
Loaded plugins: ulninfo
local-repo-custom                                                                                                                                                                      | 2.9 kB  00:00:00
local-repo-ol7                                                                                                                                                                         | 2.9 kB  00:00:00
local-repo-uekr6                                                                                                                                                                       | 2.9 kB  00:00:00
(1/3): local-repo-custom/primary_db                                                                                                                                                    |  51 kB  00:00:00
(2/3): local-repo-uekr6/primary_db                                                                                                                                                     | 1.0 MB  00:00:00
(3/3): local-repo-ol7/primary_db                                                                                                                                                       | 4.5 MB  00:00:00
repo id                                                                                                repo name                                                                                        status
local-repo-custom                                                                                      LocalCustom                                                                                         82
local-repo-ol7                                                                                         LocalOL7                                                                                         5,448
local-repo-uekr6                                                                                       LocalUEKR6                                                                                          85
repolist: 5,615
[root@localhost repo]# yum install gparted
Loaded plugins: ulninfo
Resolving Dependencies
--> Running transaction check
---> Package gparted.x86_64 0:0.33.0-1.el7 will be installed
--> Processing Dependency: PolicyKit-authentication-agent for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libsigc-2.0.so.0()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libpangomm-1.4.so.1()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libpangoft2-1.0.so.0()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libpangocairo-1.0.so.0()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libpango-1.0.so.0()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libgtkmm-2.4.so.1()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libgtk-x11-2.0.so.0()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libglibmm-2.4.so.1()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libgiomm-2.4.so.1()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libgdkmm-2.4.so.1()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libgdk_pixbuf-2.0.so.0()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libgdk-x11-2.0.so.0()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libfontconfig.so.1()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libcairomm-1.0.so.1()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libcairo.so.2()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libatkmm-1.6.so.1()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Processing Dependency: libatk-1.0.so.0()(64bit) for package: gparted-0.33.0-1.el7.x86_64
--> Running transaction check
---> Package atk.x86_64 0:2.28.1-2.el7 will be installed
---> Package atkmm.x86_64 0:2.24.2-1.el7 will be installed
---> Package cairo.x86_64 0:1.15.12-4.el7 will be installed
--> Processing Dependency: libxcb.so.1()(64bit) for package: cairo-1.15.12-4.el7.x86_64
--> Processing Dependency: libxcb-shm.so.0()(64bit) for package: cairo-1.15.12-4.el7.x86_64
--> Processing Dependency: libxcb-render.so.0()(64bit) for package: cairo-1.15.12-4.el7.x86_64
--> Processing Dependency: libpixman-1.so.0()(64bit) for package: cairo-1.15.12-4.el7.x86_64
--> Processing Dependency: libXrender.so.1()(64bit) for package: cairo-1.15.12-4.el7.x86_64
--> Processing Dependency: libXext.so.6()(64bit) for package: cairo-1.15.12-4.el7.x86_64
--> Processing Dependency: libX11.so.6()(64bit) for package: cairo-1.15.12-4.el7.x86_64
--> Processing Dependency: libGL.so.1()(64bit) for package: cairo-1.15.12-4.el7.x86_64
--> Processing Dependency: libEGL.so.1()(64bit) for package: cairo-1.15.12-4.el7.x86_64
---> Package cairomm.x86_64 0:1.12.0-1.el7 will be installed
---> Package fontconfig.x86_64 0:2.13.0-4.3.el7 will be installed
--> Processing Dependency: fontpackages-filesystem for package: fontconfig-2.13.0-4.3.el7.x86_64
--> Processing Dependency: dejavu-sans-fonts for package: fontconfig-2.13.0-4.3.el7.x86_64
---> Package gdk-pixbuf2.x86_64 0:2.36.12-3.el7 will be installed
--> Processing Dependency: libtiff.so.5(LIBTIFF_4.0)(64bit) for package: gdk-pixbuf2-2.36.12-3.el7.x86_64
--> Processing Dependency: libjpeg.so.62(LIBJPEG_6.2)(64bit) for package: gdk-pixbuf2-2.36.12-3.el7.x86_64
--> Processing Dependency: libtiff.so.5()(64bit) for package: gdk-pixbuf2-2.36.12-3.el7.x86_64
--> Processing Dependency: libjpeg.so.62()(64bit) for package: gdk-pixbuf2-2.36.12-3.el7.x86_64
--> Processing Dependency: libjasper.so.1()(64bit) for package: gdk-pixbuf2-2.36.12-3.el7.x86_64
---> Package glibmm24.x86_64 0:2.56.0-1.el7 will be installed
---> Package gtk2.x86_64 0:2.24.31-1.el7 will be installed
--> Processing Dependency: libXrandr >= 1.2.99.4-2 for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: hicolor-icon-theme for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: gtk-update-icon-cache for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libcups.so.2()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXrandr.so.2()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXinerama.so.1()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXi.so.6()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXfixes.so.3()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXdamage.so.1()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXcursor.so.1()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXcomposite.so.1()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
---> Package gtkmm24.x86_64 0:2.24.5-1.el7 will be installed
---> Package libsigc++20.x86_64 0:2.10.0-1.el7 will be installed
---> Package mate-polkit.x86_64 0:1.16.0-2.el7 will be installed
--> Processing Dependency: libgtk-3.so.0()(64bit) for package: mate-polkit-1.16.0-2.el7.x86_64
--> Processing Dependency: libgdk-3.so.0()(64bit) for package: mate-polkit-1.16.0-2.el7.x86_64
--> Processing Dependency: libcairo-gobject.so.2()(64bit) for package: mate-polkit-1.16.0-2.el7.x86_64
---> Package pango.x86_64 0:1.42.4-4.el7_7 will be installed
--> Processing Dependency: libthai(x86-64) >= 0.1.9 for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: libXft(x86-64) >= 2.0.0 for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: harfbuzz(x86-64) >= 1.4.2 for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: fribidi(x86-64) >= 1.0 for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: libthai.so.0(LIBTHAI_0.1)(64bit) for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: libthai.so.0()(64bit) for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: libharfbuzz.so.0()(64bit) for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: libfribidi.so.0()(64bit) for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: libXft.so.2()(64bit) for package: pango-1.42.4-4.el7_7.x86_64
---> Package pangomm.x86_64 0:2.40.1-1.el7 will be installed
--> Running transaction check
---> Package cairo-gobject.x86_64 0:1.15.12-4.el7 will be installed
---> Package cups-libs.x86_64 1:1.6.3-51.el7 will be installed
--> Processing Dependency: libavahi-common.so.3()(64bit) for package: 1:cups-libs-1.6.3-51.el7.x86_64
--> Processing Dependency: libavahi-client.so.3()(64bit) for package: 1:cups-libs-1.6.3-51.el7.x86_64
---> Package dejavu-sans-fonts.noarch 0:2.33-6.el7 will be installed
--> Processing Dependency: dejavu-fonts-common = 2.33-6.el7 for package: dejavu-sans-fonts-2.33-6.el7.noarch
---> Package fontpackages-filesystem.noarch 0:1.44-8.el7 will be installed
---> Package fribidi.x86_64 0:1.0.2-1.el7_7.1 will be installed
---> Package gtk-update-icon-cache.x86_64 0:3.22.30-6.el7 will be installed
---> Package gtk3.x86_64 0:3.22.30-6.el7 will be installed
--> Processing Dependency: libwayland-cursor(x86-64) >= 1.9.91 for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: libwayland-client(x86-64) >= 1.9.91 for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: libepoxy(x86-64) >= 1.0 for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: libxkbcommon.so.0(V_0.5.0)(64bit) for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: dconf(x86-64) for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: adwaita-icon-theme for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: libxkbcommon.so.0()(64bit) for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: libwayland-egl.so.1()(64bit) for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: libwayland-cursor.so.0()(64bit) for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: libwayland-client.so.0()(64bit) for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: librest-0.7.so.0()(64bit) for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: libjson-glib-1.0.so.0()(64bit) for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: libepoxy.so.0()(64bit) for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: libcolord.so.2()(64bit) for package: gtk3-3.22.30-6.el7.x86_64
--> Processing Dependency: libatk-bridge-2.0.so.0()(64bit) for package: gtk3-3.22.30-6.el7.x86_64
---> Package harfbuzz.x86_64 0:1.7.5-2.el7 will be installed
--> Processing Dependency: libgraphite2.so.3()(64bit) for package: harfbuzz-1.7.5-2.el7.x86_64
---> Package hicolor-icon-theme.noarch 0:0.12-7.el7 will be installed
---> Package jasper-libs.x86_64 0:1.900.1-33.el7 will be installed
---> Package libX11.x86_64 0:1.6.7-4.el7_9 will be installed
--> Processing Dependency: libX11-common >= 1.6.7-4.el7_9 for package: libX11-1.6.7-4.el7_9.x86_64
---> Package libXcomposite.x86_64 0:0.4.4-4.1.el7 will be installed
---> Package libXcursor.x86_64 0:1.1.15-1.el7 will be installed
---> Package libXdamage.x86_64 0:1.1.4-4.1.el7 will be installed
---> Package libXext.x86_64 0:1.3.3-3.el7 will be installed
---> Package libXfixes.x86_64 0:5.0.3-1.el7 will be installed
---> Package libXft.x86_64 0:2.3.2-2.el7 will be installed
---> Package libXi.x86_64 0:1.7.9-1.el7 will be installed
---> Package libXinerama.x86_64 0:1.1.3-2.1.el7 will be installed
---> Package libXrandr.x86_64 0:1.5.1-2.el7 will be installed
---> Package libXrender.x86_64 0:0.9.10-1.el7 will be installed
---> Package libglvnd-egl.x86_64 1:1.0.1-0.8.git5baa1e5.el7 will be installed
--> Processing Dependency: libglvnd(x86-64) = 1:1.0.1-0.8.git5baa1e5.el7 for package: 1:libglvnd-egl-1.0.1-0.8.git5baa1e5.el7.x86_64
--> Processing Dependency: mesa-libEGL(x86-64) >= 13.0.4-1 for package: 1:libglvnd-egl-1.0.1-0.8.git5baa1e5.el7.x86_64
--> Processing Dependency: libGLdispatch.so.0()(64bit) for package: 1:libglvnd-egl-1.0.1-0.8.git5baa1e5.el7.x86_64
---> Package libglvnd-glx.x86_64 1:1.0.1-0.8.git5baa1e5.el7 will be installed
--> Processing Dependency: mesa-libGL(x86-64) >= 13.0.4-1 for package: 1:libglvnd-glx-1.0.1-0.8.git5baa1e5.el7.x86_64
---> Package libjpeg-turbo.x86_64 0:1.2.90-8.el7 will be installed
---> Package libthai.x86_64 0:0.1.14-9.el7 will be installed
---> Package libtiff.x86_64 0:4.0.3-35.el7 will be installed
--> Processing Dependency: libjbig.so.2.0()(64bit) for package: libtiff-4.0.3-35.el7.x86_64
---> Package libxcb.x86_64 0:1.13-1.el7 will be installed
--> Processing Dependency: libXau.so.6()(64bit) for package: libxcb-1.13-1.el7.x86_64
---> Package pixman.x86_64 0:0.34.0-1.el7 will be installed
--> Running transaction check
---> Package adwaita-icon-theme.noarch 0:3.28.0-1.el7 will be installed
--> Processing Dependency: adwaita-cursor-theme = 3.28.0-1.el7 for package: adwaita-icon-theme-3.28.0-1.el7.noarch
---> Package at-spi2-atk.x86_64 0:2.26.2-1.el7 will be installed
--> Processing Dependency: at-spi2-core(x86-64) >= 2.25.3 for package: at-spi2-atk-2.26.2-1.el7.x86_64
--> Processing Dependency: libatspi.so.0()(64bit) for package: at-spi2-atk-2.26.2-1.el7.x86_64
---> Package avahi-libs.x86_64 0:0.6.31-20.el7 will be installed
---> Package colord-libs.x86_64 0:1.3.4-2.el7 will be installed
--> Processing Dependency: libgusb.so.2(LIBGUSB_0.1.1)(64bit) for package: colord-libs-1.3.4-2.el7.x86_64
--> Processing Dependency: libgusb.so.2(LIBGUSB_0.1.0)(64bit) for package: colord-libs-1.3.4-2.el7.x86_64
--> Processing Dependency: libusb-1.0.so.0()(64bit) for package: colord-libs-1.3.4-2.el7.x86_64
--> Processing Dependency: liblcms2.so.2()(64bit) for package: colord-libs-1.3.4-2.el7.x86_64
--> Processing Dependency: libgusb.so.2()(64bit) for package: colord-libs-1.3.4-2.el7.x86_64
---> Package dconf.x86_64 0:0.28.0-4.el7 will be installed
---> Package dejavu-fonts-common.noarch 0:2.33-6.el7 will be installed
---> Package graphite2.x86_64 0:1.3.10-1.el7_3 will be installed
---> Package jbigkit-libs.x86_64 0:2.0-11.el7 will be installed
---> Package json-glib.x86_64 0:1.4.2-2.el7 will be installed
---> Package libX11-common.noarch 0:1.6.7-4.el7_9 will be installed
---> Package libXau.x86_64 0:1.0.8-2.1.el7 will be installed
---> Package libepoxy.x86_64 0:1.5.2-1.el7 will be installed
---> Package libglvnd.x86_64 1:1.0.1-0.8.git5baa1e5.el7 will be installed
---> Package libwayland-client.x86_64 0:1.15.0-1.el7 will be installed
---> Package libwayland-cursor.x86_64 0:1.15.0-1.el7 will be installed
---> Package libwayland-egl.x86_64 0:1.15.0-1.el7 will be installed
---> Package libxkbcommon.x86_64 0:0.7.1-3.el7 will be installed
--> Processing Dependency: xkeyboard-config for package: libxkbcommon-0.7.1-3.el7.x86_64
---> Package mesa-libEGL.x86_64 0:18.3.4-12.el7_9 will be installed
--> Processing Dependency: mesa-libgbm = 18.3.4-12.el7_9 for package: mesa-libEGL-18.3.4-12.el7_9.x86_64
--> Processing Dependency: libxshmfence.so.1()(64bit) for package: mesa-libEGL-18.3.4-12.el7_9.x86_64
--> Processing Dependency: libwayland-server.so.0()(64bit) for package: mesa-libEGL-18.3.4-12.el7_9.x86_64
--> Processing Dependency: libglapi.so.0()(64bit) for package: mesa-libEGL-18.3.4-12.el7_9.x86_64
--> Processing Dependency: libgbm.so.1()(64bit) for package: mesa-libEGL-18.3.4-12.el7_9.x86_64
---> Package mesa-libGL.x86_64 0:18.3.4-12.el7_9 will be installed
--> Processing Dependency: libXxf86vm.so.1()(64bit) for package: mesa-libGL-18.3.4-12.el7_9.x86_64
---> Package rest.x86_64 0:0.8.1-2.el7 will be installed
--> Processing Dependency: libsoup-gnome-2.4.so.1()(64bit) for package: rest-0.8.1-2.el7.x86_64
--> Processing Dependency: libsoup-2.4.so.1()(64bit) for package: rest-0.8.1-2.el7.x86_64
--> Running transaction check
---> Package adwaita-cursor-theme.noarch 0:3.28.0-1.el7 will be installed
---> Package at-spi2-core.x86_64 0:2.28.0-1.el7 will be installed
--> Processing Dependency: libXtst.so.6()(64bit) for package: at-spi2-core-2.28.0-1.el7.x86_64
---> Package lcms2.x86_64 0:2.6-3.el7 will be installed
---> Package libXxf86vm.x86_64 0:1.1.4-1.el7 will be installed
---> Package libgusb.x86_64 0:0.2.9-1.el7 will be installed
---> Package libsoup.x86_64 0:2.62.2-2.el7 will be installed
--> Processing Dependency: glib-networking(x86-64) >= 2.38.0 for package: libsoup-2.62.2-2.el7.x86_64
---> Package libusbx.x86_64 0:1.0.21-1.el7 will be installed
---> Package libwayland-server.x86_64 0:1.15.0-1.el7 will be installed
---> Package libxshmfence.x86_64 0:1.2-1.el7 will be installed
---> Package mesa-libgbm.x86_64 0:18.3.4-12.el7_9 will be installed
---> Package mesa-libglapi.x86_64 0:18.3.4-12.el7_9 will be installed
---> Package xkeyboard-config.noarch 0:2.24-1.el7 will be installed
--> Running transaction check
---> Package glib-networking.x86_64 0:2.56.1-1.el7 will be installed
--> Processing Dependency: libgnutls.so.28(GNUTLS_3_1_0)(64bit) for package: glib-networking-2.56.1-1.el7.x86_64
--> Processing Dependency: libgnutls.so.28(GNUTLS_3_0_0)(64bit) for package: glib-networking-2.56.1-1.el7.x86_64
--> Processing Dependency: libgnutls.so.28(GNUTLS_2_12)(64bit) for package: glib-networking-2.56.1-1.el7.x86_64
--> Processing Dependency: libgnutls.so.28(GNUTLS_1_4)(64bit) for package: glib-networking-2.56.1-1.el7.x86_64
--> Processing Dependency: gsettings-desktop-schemas for package: glib-networking-2.56.1-1.el7.x86_64
--> Processing Dependency: libproxy.so.1()(64bit) for package: glib-networking-2.56.1-1.el7.x86_64
--> Processing Dependency: libgnutls.so.28()(64bit) for package: glib-networking-2.56.1-1.el7.x86_64
---> Package libXtst.x86_64 0:1.2.3-1.el7 will be installed
--> Running transaction check
---> Package gnutls.x86_64 0:3.3.29-9.el7_6 will be installed
--> Processing Dependency: trousers >= 0.3.11.2 for package: gnutls-3.3.29-9.el7_6.x86_64
--> Processing Dependency: libnettle.so.4()(64bit) for package: gnutls-3.3.29-9.el7_6.x86_64
--> Processing Dependency: libhogweed.so.2()(64bit) for package: gnutls-3.3.29-9.el7_6.x86_64
---> Package gsettings-desktop-schemas.x86_64 0:3.28.0-3.el7 will be installed
---> Package libproxy.x86_64 0:0.4.11-11.el7 will be installed
--> Processing Dependency: libmodman.so.1()(64bit) for package: libproxy-0.4.11-11.el7.x86_64
--> Running transaction check
---> Package libmodman.x86_64 0:2.0.1-8.el7 will be installed
---> Package nettle.x86_64 0:2.7.1-9.el7_9 will be installed
---> Package trousers.x86_64 0:0.3.14-2.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

==============================================================================================================================================================================================================
 Package                                                 Arch                                 Version                                                   Repository                                       Size
==============================================================================================================================================================================================================
Installing:
 gparted                                                 x86_64                               0.33.0-1.el7                                              local-repo-custom                               2.0 M
Installing for dependencies:
 adwaita-cursor-theme                                    noarch                               3.28.0-1.el7                                              local-repo-custom                               641 k
 adwaita-icon-theme                                      noarch                               3.28.0-1.el7                                              local-repo-custom                                11 M
 at-spi2-atk                                             x86_64                               2.26.2-1.el7                                              local-repo-custom                                80 k
 at-spi2-core                                            x86_64                               2.28.0-1.el7                                              local-repo-custom                               157 k
 atk                                                     x86_64                               2.28.1-2.el7                                              local-repo-custom                               262 k
 atkmm                                                   x86_64                               2.24.2-1.el7                                              local-repo-custom                                78 k
 avahi-libs                                              x86_64                               0.6.31-20.el7                                             local-repo-custom                                61 k
 cairo                                                   x86_64                               1.15.12-4.el7                                             local-repo-custom                               740 k
 cairo-gobject                                           x86_64                               1.15.12-4.el7                                             local-repo-custom                                25 k
 cairomm                                                 x86_64                               1.12.0-1.el7                                              local-repo-custom                                58 k
 colord-libs                                             x86_64                               1.3.4-2.el7                                               local-repo-custom                               185 k
 cups-libs                                               x86_64                               1:1.6.3-51.el7                                            local-repo-custom                               359 k
 dconf                                                   x86_64                               0.28.0-4.el7                                              local-repo-custom                               105 k
 dejavu-fonts-common                                     noarch                               2.33-6.el7                                                local-repo-custom                                64 k
 dejavu-sans-fonts                                       noarch                               2.33-6.el7                                                local-repo-custom                               1.4 M
 fontconfig                                              x86_64                               2.13.0-4.3.el7                                            local-repo-custom                               254 k
 fontpackages-filesystem                                 noarch                               1.44-8.el7                                                local-repo-custom                               9.4 k
 fribidi                                                 x86_64                               1.0.2-1.el7_7.1                                           local-repo-custom                                79 k
 gdk-pixbuf2                                             x86_64                               2.36.12-3.el7                                             local-repo-custom                               570 k
 glib-networking                                         x86_64                               2.56.1-1.el7                                              local-repo-custom                               144 k
 glibmm24                                                x86_64                               2.56.0-1.el7                                              local-repo-custom                               533 k
 gnutls                                                  x86_64                               3.3.29-9.el7_6                                            local-repo-custom                               680 k
 graphite2                                               x86_64                               1.3.10-1.el7_3                                            local-repo-custom                               115 k
 gsettings-desktop-schemas                               x86_64                               3.28.0-3.el7                                              local-repo-custom                               605 k
 gtk-update-icon-cache                                   x86_64                               3.22.30-6.el7                                             local-repo-custom                                26 k
 gtk2                                                    x86_64                               2.24.31-1.el7                                             local-repo-custom                               3.4 M
 gtk3                                                    x86_64                               3.22.30-6.el7                                             local-repo-custom                               4.4 M
 gtkmm24                                                 x86_64                               2.24.5-1.el7                                              local-repo-custom                               745 k
 harfbuzz                                                x86_64                               1.7.5-2.el7                                               local-repo-custom                               267 k
 hicolor-icon-theme                                      noarch                               0.12-7.el7                                                local-repo-custom                                42 k
 jasper-libs                                             x86_64                               1.900.1-33.el7                                            local-repo-custom                               150 k
 jbigkit-libs                                            x86_64                               2.0-11.el7                                                local-repo-custom                                46 k
 json-glib                                               x86_64                               1.4.2-2.el7                                               local-repo-custom                               133 k
 lcms2                                                   x86_64                               2.6-3.el7                                                 local-repo-custom                               150 k
 libX11                                                  x86_64                               1.6.7-4.el7_9                                             local-repo-custom                               607 k
 libX11-common                                           noarch                               1.6.7-4.el7_9                                             local-repo-custom                               164 k
 libXau                                                  x86_64                               1.0.8-2.1.el7                                             local-repo-custom                                28 k
 libXcomposite                                           x86_64                               0.4.4-4.1.el7                                             local-repo-custom                                22 k
 libXcursor                                              x86_64                               1.1.15-1.el7                                              local-repo-custom                                30 k
 libXdamage                                              x86_64                               1.1.4-4.1.el7                                             local-repo-custom                                20 k
 libXext                                                 x86_64                               1.3.3-3.el7                                               local-repo-custom                                38 k
 libXfixes                                               x86_64                               5.0.3-1.el7                                               local-repo-custom                                18 k
 libXft                                                  x86_64                               2.3.2-2.el7                                               local-repo-custom                                58 k
 libXi                                                   x86_64                               1.7.9-1.el7                                               local-repo-custom                                40 k
 libXinerama                                             x86_64                               1.1.3-2.1.el7                                             local-repo-custom                                13 k
 libXrandr                                               x86_64                               1.5.1-2.el7                                               local-repo-custom                                27 k
 libXrender                                              x86_64                               0.9.10-1.el7                                              local-repo-custom                                25 k
 libXtst                                                 x86_64                               1.2.3-1.el7                                               local-repo-custom                                20 k
 libXxf86vm                                              x86_64                               1.1.4-1.el7                                               local-repo-custom                                17 k
 libepoxy                                                x86_64                               1.5.2-1.el7                                               local-repo-custom                               210 k
 libglvnd                                                x86_64                               1:1.0.1-0.8.git5baa1e5.el7                                local-repo-custom                                89 k
 libglvnd-egl                                            x86_64                               1:1.0.1-0.8.git5baa1e5.el7                                local-repo-custom                                43 k
 libglvnd-glx                                            x86_64                               1:1.0.1-0.8.git5baa1e5.el7                                local-repo-custom                               124 k
 libgusb                                                 x86_64                               0.2.9-1.el7                                               local-repo-custom                                40 k
 libjpeg-turbo                                           x86_64                               1.2.90-8.el7                                              local-repo-custom                               134 k
 libmodman                                               x86_64                               2.0.1-8.el7                                               local-repo-custom                                28 k
 libproxy                                                x86_64                               0.4.11-11.el7                                             local-repo-custom                                64 k
 libsigc++20                                             x86_64                               2.10.0-1.el7                                              local-repo-custom                                36 k
 libsoup                                                 x86_64                               2.62.2-2.el7                                              local-repo-custom                               410 k
 libthai                                                 x86_64                               0.1.14-9.el7                                              local-repo-custom                               185 k
 libtiff                                                 x86_64                               4.0.3-35.el7                                              local-repo-custom                               172 k
 libusbx                                                 x86_64                               1.0.21-1.el7                                              local-repo-custom                                61 k
 libwayland-client                                       x86_64                               1.15.0-1.el7                                              local-repo-custom                                32 k
 libwayland-cursor                                       x86_64                               1.15.0-1.el7                                              local-repo-custom                                20 k
 libwayland-egl                                          x86_64                               1.15.0-1.el7                                              local-repo-custom                                13 k
 libwayland-server                                       x86_64                               1.15.0-1.el7                                              local-repo-custom                                38 k
 libxcb                                                  x86_64                               1.13-1.el7                                                local-repo-custom                               213 k
 libxkbcommon                                            x86_64                               0.7.1-3.el7                                               local-repo-custom                               108 k
 libxshmfence                                            x86_64                               1.2-1.el7                                                 local-repo-custom                               6.5 k
 mate-polkit                                             x86_64                               1.16.0-2.el7                                              local-repo-custom                               103 k
 mesa-libEGL                                             x86_64                               18.3.4-12.el7_9                                           local-repo-custom                               109 k
 mesa-libGL                                              x86_64                               18.3.4-12.el7_9                                           local-repo-custom                               165 k
 mesa-libgbm                                             x86_64                               18.3.4-12.el7_9                                           local-repo-custom                                39 k
 mesa-libglapi                                           x86_64                               18.3.4-12.el7_9                                           local-repo-custom                                45 k
 nettle                                                  x86_64                               2.7.1-9.el7_9                                             local-repo-custom                               327 k
 pango                                                   x86_64                               1.42.4-4.el7_7                                            local-repo-custom                               280 k
 pangomm                                                 x86_64                               2.40.1-1.el7                                              local-repo-custom                                58 k
 pixman                                                  x86_64                               0.34.0-1.el7                                              local-repo-custom                               247 k
 rest                                                    x86_64                               0.8.1-2.el7                                               local-repo-custom                                63 k
 trousers                                                x86_64                               0.3.14-2.el7                                              local-repo-custom                               289 k
 xkeyboard-config                                        noarch                               2.24-1.el7                                                local-repo-custom                               833 k

Transaction Summary
==============================================================================================================================================================================================================
Install  1 Package (+81 Dependent packages)

Total download size: 35 M
Installed size: 114 M
Is this ok [y/d/N]: y
Downloading packages:
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                                         169 MB/s |  35 MB  00:00:00
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : atk-2.28.1-2.el7.x86_64                                                                                                                                                                   1/82
  Installing : libsigc++20-2.10.0-1.el7.x86_64                                                                                                                                                           2/82
  Installing : glibmm24-2.56.0-1.el7.x86_64                                                                                                                                                              3/82
  Installing : libjpeg-turbo-1.2.90-8.el7.x86_64                                                                                                                                                         4/82
  Installing : libwayland-client-1.15.0-1.el7.x86_64                                                                                                                                                     5/82
  Installing : mesa-libglapi-18.3.4-12.el7_9.x86_64                                                                                                                                                      6/82
  Installing : atkmm-2.24.2-1.el7.x86_64                                                                                                                                                                 7/82
  Installing : libxshmfence-1.2-1.el7.x86_64                                                                                                                                                             8/82
  Installing : pixman-0.34.0-1.el7.x86_64                                                                                                                                                                9/82
  Installing : libwayland-server-1.15.0-1.el7.x86_64                                                                                                                                                    10/82
  Installing : libusbx-1.0.21-1.el7.x86_64                                                                                                                                                              11/82
  Installing : 1:libglvnd-1.0.1-0.8.git5baa1e5.el7.x86_64                                                                                                                                               12/82
  Installing : hicolor-icon-theme-0.12-7.el7.noarch                                                                                                                                                     13/82
  Installing : fontpackages-filesystem-1.44-8.el7.noarch                                                                                                                                                14/82
  Installing : dejavu-fonts-common-2.33-6.el7.noarch                                                                                                                                                    15/82
  Installing : dejavu-sans-fonts-2.33-6.el7.noarch                                                                                                                                                      16/82
  Installing : fontconfig-2.13.0-4.3.el7.x86_64                                                                                                                                                         17/82
  Installing : libgusb-0.2.9-1.el7.x86_64                                                                                                                                                               18/82
  Installing : mesa-libgbm-18.3.4-12.el7_9.x86_64                                                                                                                                                       19/82
  Installing : libwayland-cursor-1.15.0-1.el7.x86_64                                                                                                                                                    20/82
  Installing : jasper-libs-1.900.1-33.el7.x86_64                                                                                                                                                        21/82
  Installing : avahi-libs-0.6.31-20.el7.x86_64                                                                                                                                                          22/82
  Installing : 1:cups-libs-1.6.3-51.el7.x86_64                                                                                                                                                          23/82
  Installing : libX11-common-1.6.7-4.el7_9.noarch                                                                                                                                                       24/82
  Installing : libmodman-2.0.1-8.el7.x86_64                                                                                                                                                             25/82
  Installing : libproxy-0.4.11-11.el7.x86_64                                                                                                                                                            26/82
  Installing : graphite2-1.3.10-1.el7_3.x86_64                                                                                                                                                          27/82
  Installing : harfbuzz-1.7.5-2.el7.x86_64                                                                                                                                                              28/82
  Installing : libXau-1.0.8-2.1.el7.x86_64                                                                                                                                                              29/82
  Installing : libxcb-1.13-1.el7.x86_64                                                                                                                                                                 30/82
  Installing : libX11-1.6.7-4.el7_9.x86_64                                                                                                                                                              31/82
  Installing : libXext-1.3.3-3.el7.x86_64                                                                                                                                                               32/82
  Installing : libXrender-0.9.10-1.el7.x86_64                                                                                                                                                           33/82
  Installing : libXfixes-5.0.3-1.el7.x86_64                                                                                                                                                             34/82
  Installing : libXdamage-1.1.4-4.1.el7.x86_64                                                                                                                                                          35/82
  Installing : libXi-1.7.9-1.el7.x86_64                                                                                                                                                                 36/82
  Installing : libXcursor-1.1.15-1.el7.x86_64                                                                                                                                                           37/82
  Installing : libXrandr-1.5.1-2.el7.x86_64                                                                                                                                                             38/82
  Installing : libXinerama-1.1.3-2.1.el7.x86_64                                                                                                                                                         39/82
  Installing : libXcomposite-0.4.4-4.1.el7.x86_64                                                                                                                                                       40/82
  Installing : libXtst-1.2.3-1.el7.x86_64                                                                                                                                                               41/82
  Installing : at-spi2-core-2.28.0-1.el7.x86_64                                                                                                                                                         42/82
  Installing : at-spi2-atk-2.26.2-1.el7.x86_64                                                                                                                                                          43/82
  Installing : libXft-2.3.2-2.el7.x86_64                                                                                                                                                                44/82
  Installing : libXxf86vm-1.1.4-1.el7.x86_64                                                                                                                                                            45/82
  Installing : 1:libglvnd-glx-1.0.1-0.8.git5baa1e5.el7.x86_64                                                                                                                                           46/82
  Installing : mesa-libGL-18.3.4-12.el7_9.x86_64                                                                                                                                                        47/82
  Installing : 1:libglvnd-egl-1.0.1-0.8.git5baa1e5.el7.x86_64                                                                                                                                           48/82
  Installing : mesa-libEGL-18.3.4-12.el7_9.x86_64                                                                                                                                                       49/82
  Installing : cairo-1.15.12-4.el7.x86_64                                                                                                                                                               50/82
  Installing : cairomm-1.12.0-1.el7.x86_64                                                                                                                                                              51/82
  Installing : cairo-gobject-1.15.12-4.el7.x86_64                                                                                                                                                       52/82
  Installing : lcms2-2.6-3.el7.x86_64                                                                                                                                                                   53/82
  Installing : colord-libs-1.3.4-2.el7.x86_64                                                                                                                                                           54/82
  Installing : nettle-2.7.1-9.el7_9.x86_64                                                                                                                                                              55/82
  Installing : jbigkit-libs-2.0-11.el7.x86_64                                                                                                                                                           56/82
  Installing : libtiff-4.0.3-35.el7.x86_64                                                                                                                                                              57/82
  Installing : gdk-pixbuf2-2.36.12-3.el7.x86_64                                                                                                                                                         58/82
  Installing : gtk-update-icon-cache-3.22.30-6.el7.x86_64                                                                                                                                               59/82
  Installing : dconf-0.28.0-4.el7.x86_64                                                                                                                                                                60/82
  Installing : libepoxy-1.5.2-1.el7.x86_64                                                                                                                                                              61/82
  Installing : json-glib-1.4.2-2.el7.x86_64                                                                                                                                                             62/82
  Installing : gsettings-desktop-schemas-3.28.0-3.el7.x86_64                                                                                                                                            63/82
  Installing : libthai-0.1.14-9.el7.x86_64                                                                                                                                                              64/82
  Installing : fribidi-1.0.2-1.el7_7.1.x86_64                                                                                                                                                           65/82
  Installing : pango-1.42.4-4.el7_7.x86_64                                                                                                                                                              66/82
  Installing : pangomm-2.40.1-1.el7.x86_64                                                                                                                                                              67/82
  Installing : gtk2-2.24.31-1.el7.x86_64                                                                                                                                                                68/82
  Installing : gtkmm24-2.24.5-1.el7.x86_64                                                                                                                                                              69/82
  Installing : adwaita-cursor-theme-3.28.0-1.el7.noarch                                                                                                                                                 70/82
  Installing : adwaita-icon-theme-3.28.0-1.el7.noarch                                                                                                                                                   71/82
  Installing : xkeyboard-config-2.24-1.el7.noarch                                                                                                                                                       72/82
  Installing : libxkbcommon-0.7.1-3.el7.x86_64                                                                                                                                                          73/82
  Installing : trousers-0.3.14-2.el7.x86_64                                                                                                                                                             74/82
  Installing : gnutls-3.3.29-9.el7_6.x86_64                                                                                                                                                             75/82
  Installing : glib-networking-2.56.1-1.el7.x86_64                                                                                                                                                      76/82
  Installing : libsoup-2.62.2-2.el7.x86_64                                                                                                                                                              77/82
  Installing : rest-0.8.1-2.el7.x86_64                                                                                                                                                                  78/82
  Installing : libwayland-egl-1.15.0-1.el7.x86_64                                                                                                                                                       79/82
  Installing : gtk3-3.22.30-6.el7.x86_64                                                                                                                                                                80/82
  Installing : mate-polkit-1.16.0-2.el7.x86_64                                                                                                                                                          81/82
  Installing : gparted-0.33.0-1.el7.x86_64                                                                                                                                                              82/82
  Verifying  : libXext-1.3.3-3.el7.x86_64                                                                                                                                                                1/82
  Verifying  : at-spi2-atk-2.26.2-1.el7.x86_64                                                                                                                                                           2/82
  Verifying  : libXi-1.7.9-1.el7.x86_64                                                                                                                                                                  3/82
  Verifying  : at-spi2-core-2.28.0-1.el7.x86_64                                                                                                                                                          4/82
  Verifying  : fontconfig-2.13.0-4.3.el7.x86_64                                                                                                                                                          5/82
  Verifying  : pangomm-2.40.1-1.el7.x86_64                                                                                                                                                               6/82
  Verifying  : gdk-pixbuf2-2.36.12-3.el7.x86_64                                                                                                                                                          7/82
  Verifying  : libxkbcommon-0.7.1-3.el7.x86_64                                                                                                                                                           8/82
  Verifying  : libXinerama-1.1.3-2.1.el7.x86_64                                                                                                                                                          9/82
  Verifying  : jasper-libs-1.900.1-33.el7.x86_64                                                                                                                                                        10/82
  Verifying  : libXrender-0.9.10-1.el7.x86_64                                                                                                                                                           11/82
  Verifying  : 1:libglvnd-glx-1.0.1-0.8.git5baa1e5.el7.x86_64                                                                                                                                           12/82
  Verifying  : mate-polkit-1.16.0-2.el7.x86_64                                                                                                                                                          13/82
  Verifying  : gtk3-3.22.30-6.el7.x86_64                                                                                                                                                                14/82
  Verifying  : libXcursor-1.1.15-1.el7.x86_64                                                                                                                                                           15/82
  Verifying  : mesa-libglapi-18.3.4-12.el7_9.x86_64                                                                                                                                                     16/82
  Verifying  : adwaita-icon-theme-3.28.0-1.el7.noarch                                                                                                                                                   17/82
  Verifying  : colord-libs-1.3.4-2.el7.x86_64                                                                                                                                                           18/82
  Verifying  : libXtst-1.2.3-1.el7.x86_64                                                                                                                                                               19/82
  Verifying  : cairomm-1.12.0-1.el7.x86_64                                                                                                                                                              20/82
  Verifying  : libwayland-client-1.15.0-1.el7.x86_64                                                                                                                                                    21/82
  Verifying  : 1:cups-libs-1.6.3-51.el7.x86_64                                                                                                                                                          22/82
  Verifying  : fontpackages-filesystem-1.44-8.el7.noarch                                                                                                                                                23/82
  Verifying  : libwayland-egl-1.15.0-1.el7.x86_64                                                                                                                                                       24/82
  Verifying  : hicolor-icon-theme-0.12-7.el7.noarch                                                                                                                                                     25/82
  Verifying  : gparted-0.33.0-1.el7.x86_64                                                                                                                                                              26/82
  Verifying  : libXcomposite-0.4.4-4.1.el7.x86_64                                                                                                                                                       27/82
  Verifying  : trousers-0.3.14-2.el7.x86_64                                                                                                                                                             28/82
  Verifying  : gtk2-2.24.31-1.el7.x86_64                                                                                                                                                                29/82
  Verifying  : libtiff-4.0.3-35.el7.x86_64                                                                                                                                                              30/82
  Verifying  : xkeyboard-config-2.24-1.el7.noarch                                                                                                                                                       31/82
  Verifying  : adwaita-cursor-theme-3.28.0-1.el7.noarch                                                                                                                                                 32/82
  Verifying  : dejavu-fonts-common-2.33-6.el7.noarch                                                                                                                                                    33/82
  Verifying  : pango-1.42.4-4.el7_7.x86_64                                                                                                                                                              34/82
  Verifying  : fribidi-1.0.2-1.el7_7.1.x86_64                                                                                                                                                           35/82
  Verifying  : libthai-0.1.14-9.el7.x86_64                                                                                                                                                              36/82
  Verifying  : atkmm-2.24.2-1.el7.x86_64                                                                                                                                                                37/82
  Verifying  : 1:libglvnd-1.0.1-0.8.git5baa1e5.el7.x86_64                                                                                                                                               38/82
  Verifying  : libxcb-1.13-1.el7.x86_64                                                                                                                                                                 39/82
  Verifying  : libXft-2.3.2-2.el7.x86_64                                                                                                                                                                40/82
  Verifying  : gsettings-desktop-schemas-3.28.0-3.el7.x86_64                                                                                                                                            41/82
  Verifying  : mesa-libGL-18.3.4-12.el7_9.x86_64                                                                                                                                                        42/82
  Verifying  : json-glib-1.4.2-2.el7.x86_64                                                                                                                                                             43/82
  Verifying  : gtk-update-icon-cache-3.22.30-6.el7.x86_64                                                                                                                                               44/82
  Verifying  : gnutls-3.3.29-9.el7_6.x86_64                                                                                                                                                             45/82
  Verifying  : glib-networking-2.56.1-1.el7.x86_64                                                                                                                                                      46/82
  Verifying  : libjpeg-turbo-1.2.90-8.el7.x86_64                                                                                                                                                        47/82
  Verifying  : libepoxy-1.5.2-1.el7.x86_64                                                                                                                                                              48/82
  Verifying  : libusbx-1.0.21-1.el7.x86_64                                                                                                                                                              49/82
  Verifying  : libwayland-server-1.15.0-1.el7.x86_64                                                                                                                                                    50/82
  Verifying  : libXxf86vm-1.1.4-1.el7.x86_64                                                                                                                                                            51/82
  Verifying  : harfbuzz-1.7.5-2.el7.x86_64                                                                                                                                                              52/82
  Verifying  : rest-0.8.1-2.el7.x86_64                                                                                                                                                                  53/82
  Verifying  : dconf-0.28.0-4.el7.x86_64                                                                                                                                                                54/82
  Verifying  : dejavu-sans-fonts-2.33-6.el7.noarch                                                                                                                                                      55/82
  Verifying  : libXrandr-1.5.1-2.el7.x86_64                                                                                                                                                             56/82
  Verifying  : glibmm24-2.56.0-1.el7.x86_64                                                                                                                                                             57/82
  Verifying  : pixman-0.34.0-1.el7.x86_64                                                                                                                                                               58/82
  Verifying  : libsigc++20-2.10.0-1.el7.x86_64                                                                                                                                                          59/82
  Verifying  : libgusb-0.2.9-1.el7.x86_64                                                                                                                                                               60/82
  Verifying  : jbigkit-libs-2.0-11.el7.x86_64                                                                                                                                                           61/82
  Verifying  : cairo-1.15.12-4.el7.x86_64                                                                                                                                                               62/82
  Verifying  : libproxy-0.4.11-11.el7.x86_64                                                                                                                                                            63/82
  Verifying  : mesa-libgbm-18.3.4-12.el7_9.x86_64                                                                                                                                                       64/82
  Verifying  : nettle-2.7.1-9.el7_9.x86_64                                                                                                                                                              65/82
  Verifying  : lcms2-2.6-3.el7.x86_64                                                                                                                                                                   66/82
  Verifying  : libxshmfence-1.2-1.el7.x86_64                                                                                                                                                            67/82
  Verifying  : cairo-gobject-1.15.12-4.el7.x86_64                                                                                                                                                       68/82
  Verifying  : libXau-1.0.8-2.1.el7.x86_64                                                                                                                                                              69/82
  Verifying  : 1:libglvnd-egl-1.0.1-0.8.git5baa1e5.el7.x86_64                                                                                                                                           70/82
  Verifying  : libsoup-2.62.2-2.el7.x86_64                                                                                                                                                              71/82
  Verifying  : libX11-1.6.7-4.el7_9.x86_64                                                                                                                                                              72/82
  Verifying  : graphite2-1.3.10-1.el7_3.x86_64                                                                                                                                                          73/82
  Verifying  : mesa-libEGL-18.3.4-12.el7_9.x86_64                                                                                                                                                       74/82
  Verifying  : gtkmm24-2.24.5-1.el7.x86_64                                                                                                                                                              75/82
  Verifying  : libwayland-cursor-1.15.0-1.el7.x86_64                                                                                                                                                    76/82
  Verifying  : libXdamage-1.1.4-4.1.el7.x86_64                                                                                                                                                          77/82
  Verifying  : libXfixes-5.0.3-1.el7.x86_64                                                                                                                                                             78/82
  Verifying  : atk-2.28.1-2.el7.x86_64                                                                                                                                                                  79/82
  Verifying  : libmodman-2.0.1-8.el7.x86_64                                                                                                                                                             80/82
  Verifying  : libX11-common-1.6.7-4.el7_9.noarch                                                                                                                                                       81/82
  Verifying  : avahi-libs-0.6.31-20.el7.x86_64                                                                                                                                                          82/82

Installed:
  gparted.x86_64 0:0.33.0-1.el7

Dependency Installed:
  adwaita-cursor-theme.noarch 0:3.28.0-1.el7           adwaita-icon-theme.noarch 0:3.28.0-1.el7       at-spi2-atk.x86_64 0:2.26.2-1.el7                at-spi2-core.x86_64 0:2.28.0-1.el7
  atk.x86_64 0:2.28.1-2.el7                            atkmm.x86_64 0:2.24.2-1.el7                    avahi-libs.x86_64 0:0.6.31-20.el7                cairo.x86_64 0:1.15.12-4.el7
  cairo-gobject.x86_64 0:1.15.12-4.el7                 cairomm.x86_64 0:1.12.0-1.el7                  colord-libs.x86_64 0:1.3.4-2.el7                 cups-libs.x86_64 1:1.6.3-51.el7
  dconf.x86_64 0:0.28.0-4.el7                          dejavu-fonts-common.noarch 0:2.33-6.el7        dejavu-sans-fonts.noarch 0:2.33-6.el7            fontconfig.x86_64 0:2.13.0-4.3.el7
  fontpackages-filesystem.noarch 0:1.44-8.el7          fribidi.x86_64 0:1.0.2-1.el7_7.1               gdk-pixbuf2.x86_64 0:2.36.12-3.el7               glib-networking.x86_64 0:2.56.1-1.el7
  glibmm24.x86_64 0:2.56.0-1.el7                       gnutls.x86_64 0:3.3.29-9.el7_6                 graphite2.x86_64 0:1.3.10-1.el7_3                gsettings-desktop-schemas.x86_64 0:3.28.0-3.el7
  gtk-update-icon-cache.x86_64 0:3.22.30-6.el7         gtk2.x86_64 0:2.24.31-1.el7                    gtk3.x86_64 0:3.22.30-6.el7                      gtkmm24.x86_64 0:2.24.5-1.el7
  harfbuzz.x86_64 0:1.7.5-2.el7                        hicolor-icon-theme.noarch 0:0.12-7.el7         jasper-libs.x86_64 0:1.900.1-33.el7              jbigkit-libs.x86_64 0:2.0-11.el7
  json-glib.x86_64 0:1.4.2-2.el7                       lcms2.x86_64 0:2.6-3.el7                       libX11.x86_64 0:1.6.7-4.el7_9                    libX11-common.noarch 0:1.6.7-4.el7_9
  libXau.x86_64 0:1.0.8-2.1.el7                        libXcomposite.x86_64 0:0.4.4-4.1.el7           libXcursor.x86_64 0:1.1.15-1.el7                 libXdamage.x86_64 0:1.1.4-4.1.el7
  libXext.x86_64 0:1.3.3-3.el7                         libXfixes.x86_64 0:5.0.3-1.el7                 libXft.x86_64 0:2.3.2-2.el7                      libXi.x86_64 0:1.7.9-1.el7
  libXinerama.x86_64 0:1.1.3-2.1.el7                   libXrandr.x86_64 0:1.5.1-2.el7                 libXrender.x86_64 0:0.9.10-1.el7                 libXtst.x86_64 0:1.2.3-1.el7
  libXxf86vm.x86_64 0:1.1.4-1.el7                      libepoxy.x86_64 0:1.5.2-1.el7                  libglvnd.x86_64 1:1.0.1-0.8.git5baa1e5.el7       libglvnd-egl.x86_64 1:1.0.1-0.8.git5baa1e5.el7
  libglvnd-glx.x86_64 1:1.0.1-0.8.git5baa1e5.el7       libgusb.x86_64 0:0.2.9-1.el7                   libjpeg-turbo.x86_64 0:1.2.90-8.el7              libmodman.x86_64 0:2.0.1-8.el7
  libproxy.x86_64 0:0.4.11-11.el7                      libsigc++20.x86_64 0:2.10.0-1.el7              libsoup.x86_64 0:2.62.2-2.el7                    libthai.x86_64 0:0.1.14-9.el7
  libtiff.x86_64 0:4.0.3-35.el7                        libusbx.x86_64 0:1.0.21-1.el7                  libwayland-client.x86_64 0:1.15.0-1.el7          libwayland-cursor.x86_64 0:1.15.0-1.el7
  libwayland-egl.x86_64 0:1.15.0-1.el7                 libwayland-server.x86_64 0:1.15.0-1.el7        libxcb.x86_64 0:1.13-1.el7                       libxkbcommon.x86_64 0:0.7.1-3.el7
  libxshmfence.x86_64 0:1.2-1.el7                      mate-polkit.x86_64 0:1.16.0-2.el7              mesa-libEGL.x86_64 0:18.3.4-12.el7_9             mesa-libGL.x86_64 0:18.3.4-12.el7_9
  mesa-libgbm.x86_64 0:18.3.4-12.el7_9                 mesa-libglapi.x86_64 0:18.3.4-12.el7_9         nettle.x86_64 0:2.7.1-9.el7_9                    pango.x86_64 0:1.42.4-4.el7_7
  pangomm.x86_64 0:2.40.1-1.el7                        pixman.x86_64 0:0.34.0-1.el7                   rest.x86_64 0:0.8.1-2.el7                        trousers.x86_64 0:0.3.14-2.el7
  xkeyboard-config.noarch 0:2.24-1.el7

Complete!
[root@localhost repo]#
```
