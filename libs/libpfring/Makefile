#
# Copyright (C) 2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libpf_ring
PKG_VERSION:=git-f79389b
PKG_RELEASE:=1
PKG_MAINTAINER:=Banglang Huang <banglang.huang@foxmail.com>

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/ntop/pf_ring.git
PKG_SOURCE_VERSION:=f79389b6b5f541b17896cb7521cc3c08bf45ba98

PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_LICENSE:=LGPLv2.1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SOURCE_SUBDIR)
PKG_BUILD_PARALLEL:=1

PKG_INSTALL:=1
PKG_FIXUP:=patch-libtool

include $(INCLUDE_DIR)/package.mk

CONFIGURE_PATH:=userland
MAKE_PATH:=userland/lib

define Package/libpf_ring
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Library for PR_RING (package process framework)
  URL:=https://github.com/ntop/pf_ring
  DEPENDS:=+libpcap +libpthread @TARGET_x86_64
endef

define Package/libpf_ring/description
  PF_RING is a high speed packet capture library that turns a commodity PC into an efficient and cheap
  network measurement box suitable for both packet and active traffic analysis and manipulation.
  Moreover, PF_RING opens totally new markets as it enables the creation of efficient application such as
  traffic balancers or packet filters in a matter of lines of codes.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/* \
		$(1)/usr/include/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libpfring.so* \
		$(1)/usr/lib/
endef

define Package/libndpi/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libpf_ring.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libpf_ring))
