#
# Copyright (C) 2017-2020
#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qBittorrent-static
PKG_VERSION:=5.1.4
DL_VERSION:=5.1.4_v2.0.12
PKG_RELEASE=1

STRIP:=true

ifeq ($(ARCH),x86_64)
	PKG_ARCH:=x86_64
endif

ifeq ($(ARCH),aarch64)
	PKG_ARCH:=aarch64
endif

ifeq ($(ARCH),arm)
	PKG_ARCH:=armv7
endif

include $(INCLUDE_DIR)/package.mk

define Package/qBittorrent-static
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=@(arm||aarch64||x86_64)
  SUBMENU:=BitTorrent
  TITLE:=bittorrent client programmed in C++ / Qt6
  URL:=https://www.qbittorrent.org/
endef

define Package/qBittorrent-static/description
  qBittorrent is a bittorrent client programmed in C++ / Qt6 that uses
  libtorrent (sometimes called libtorrent-rasterbar) by Arvid Norberg.
  It aims to be a good alternative to all other bittorrent clients out
  there. qBittorrent is fast, stable and provides unicode support as
  well as many features.
endef

define Download/qbittorrent
  URL:=https://github.com/userdocs/qbittorrent-nox-static/releases/download/release-$(DL_VERSION)
  URL_FILE:=$(PKG_ARCH)-qbittorrent-nox
  FILE:=$(PKG_ARCH)-qbittorrent-nox-$(DL_VERSION)
  HASH:=45b29aadab07ab3b035956f1751840fb1838c9532338c8732a83df21c33d727a
endef

define Build/Compile
endef

define Package/qBittorrent-static/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(DL_DIR)/$(PKG_ARCH)-qbittorrent-nox-$(DL_VERSION) $(1)/usr/bin/qbittorrent-nox

	$(INSTALL_DIR) $(1)/etc/config $(1)/etc/init.d $(1)/usr/share/qbittorrent
	$(INSTALL_BIN) ./files/qbittorrent.init $(1)/etc/init.d/qbittorrent
	$(INSTALL_CONF) ./files/qbittorrent.config $(1)/etc/config/qbittorrent
	$(INSTALL_CONF) ./files/qBittorrent.conf.example $(1)/usr/share/qbittorrent/qBittorrent.conf.example
endef

$(eval $(call Download,qbittorrent))
$(eval $(call BuildPackage,qBittorrent-static))
