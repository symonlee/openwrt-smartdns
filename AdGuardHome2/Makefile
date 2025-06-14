#
# Copyright (C) 2019 OpenWrt.org
#
# KFERMercer <KFER.Mercer@gmail.com>
#
# This is free software, licensed under the GNU General Public License v3.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=AdGuardHome
PROJECT_NAME:=AdGuardHome
PKG_VERSION:=0.107.61
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Network-wide ads & trackers blocking DNS server
	URL:=https://github.com/AdguardTeam/AdGuardHome
endef


define Package/$(PKG_NAME)/description
Network-wide ads & trackers blocking DNS server
endef

STRIP:=true

ifeq ($(ARCH),i386)
	PKG_ARCH_ADGUARDHOME:=386
endif

ifeq ($(ARCH),x86_64)
	PKG_ARCH_ADGUARDHOME:=amd64
endif

ifeq ($(ARCH),mipsel)
	PKG_ARCH_ADGUARDHOME:=mipsle
endif

ifeq ($(ARCH),mips)
	PKG_ARCH_ADGUARDHOME:=mips
endif

ifeq ($(ARCH),arm)
	PKG_ARCH_ADGUARDHOME:=arm
endif

ifeq ($(ARCH),arm64)
	PKG_ARCH_ADGUARDHOME:=arm64
endif

ifeq ($(ARCH),aarch64)
	PKG_ARCH_ADGUARDHOME:=arm64
endif

TAR_NAME:=AdGuardHome_linux_$(PKG_ARCH_ADGUARDHOME)

PKG_SOURCE:=$(TAR_NAME).tar.gz

PKG_SOURCE_URL:=https://github.com/AdguardTeam/AdGuardHome/releases/download/v$(PKG_VERSION)/

UNTAR_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)/$(PKG_NAME)-extract/$(PKG_ARCH_ADGUARDHOME)

PKG_HASH:=4ed0fc291f7632fdd9de70b3e31213f8572ec70aa00d3ab70b59462042eb1105

define Build/Prepare
	mkdir -vp $(UNTAR_DIR)
	tar -zxvf $(DL_DIR)/$(PKG_SOURCE) -C $(UNTAR_DIR)
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(UNTAR_DIR)/*/$(PROJECT_NAME) $(1)/usr/bin/$(PKG_NAME)
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/AdGuardHome.init $(1)/etc/init.d/AdGuardHome

	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_CONF) ./files/AdGuardHome.yaml $(1)/etc/AdGuardHome.yaml

	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DATA) ./files/AdGuardHome.config $(1)/etc/config/AdGuardHome
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
