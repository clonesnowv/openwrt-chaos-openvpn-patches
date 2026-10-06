#
# Copyright (C) 2006-2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libnl
PKG_VERSION:=3.4.0
PKG_RELEASE:=1
PKG_FIXUP:=autoreconf
PKG_SOURCE_PROTO:=git
PKG_SOURCE:=$(PKG_NMAE)-$(PKG_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=libnl-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/thom311/libnl.git
PKG_SOURCE_VERSION:=3fe3454b0228a6c9729ce9ffebf62bda85fd87ab
PKG_LICENSE:=LGPL-2.1
PKG_MIRROR_HASH:=skip

include $(INCLUDE_DIR)/package.mk

define Package/libnl
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=netlink socket library
  DEPENDS:=+libpthread
  URL:=https://github.com/thom311/libnl
endef

define Package/libnl/description
 This package contains a library for applications dealing with netlink sockets
endef

TARGET_CFLAGS += -ffunction-sections $(FPIC)

define Build/Configure
	$(call Build/Configure/Default )

endef

define Build/Compile
	$(call Build/Compile/Default)
	$(MAKE) -C $(PKG_BUILD_DIR) \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		install
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
	mkdir -p $(1)/usr/include/libnl
	#$(CP) $(PKG_BUILD_DIR)/include/linux $(1)/usr/include/libnl/
endef

define Package/libnl/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libnl-route-3.so.* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libnl-genl-3.so.* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libnl-nf-3.so.* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libnl-3.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libnl))
