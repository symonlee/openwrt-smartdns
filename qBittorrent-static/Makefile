#
# Copyright (C) 2017-2020
#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qBittorrent-static
PKG_VERSION:=5.2.0
DL_VERSION:=5.2.0_v2.0.12
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
  HASH:=cf04a25786b3727276fd703b080ff998fe2a5ae7e4bbc065686f3608ed7aad91
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
