#
# Copyright (C) 2019 OpenWrt.org
#
# KFERMercer <KFER.Mercer@gmail.com>
#
# This is free software, licensed under the GNU General Public License v3.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=dnsproxy
PROJECT_NAME:=dnsproxy
PKG_VERSION:=0.72.1
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=IP Addresses and Names
	TITLE:=Simple DNS proxy with DoH, DoT, DoQ and DNSCrypt support
	URL:=https://github.com/AdguardTeam/dnsproxy
endef


define Package/dnsproxy/description
  A simple DNS proxy server that supports all existing DNS protocols including
  DNS-over-TLS, DNS-over-HTTPS, DNSCrypt, and DNS-over-QUIC.Moreover, it can
  work as a DNS-over-HTTPS, DNS-over-TLS or DNS-over-QUIC server.
endef

STRIP:=true

ifeq ($(ARCH),i386)
	PKG_ARCH_DNSPROXY:=386
endif

ifeq ($(ARCH),x86_64)
	PKG_ARCH_DNSPROXY:=amd64
endif

ifeq ($(ARCH),mipsel)
	PKG_ARCH_DNSPROXY:=mipsle
endif

ifeq ($(ARCH),mips)
	PKG_ARCH_DNSPROXY:=mips
endif

ifeq ($(ARCH),arm)
	PKG_ARCH_DNSPROXY:=arm
endif

ifeq ($(ARCH),arm64)
	PKG_ARCH_DNSPROXY:=arm64
endif

ifeq ($(ARCH),aarch64)
	PKG_ARCH_DNSPROXY:=arm64
endif

TAR_NAME:=dnsproxy-linux-$(PKG_ARCH_DNSPROXY)-v$(PKG_VERSION)

PKG_SOURCE:=$(TAR_NAME).tar.gz

PKG_SOURCE_URL:=https://github.com/AdguardTeam/dnsproxy/releases/download/v$(PKG_VERSION)/

UNTAR_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)/$(PKG_NAME)-extract/$(PKG_ARCH_DNSPROXY)

PKG_HASH:=00ede45576b063f304aeb7f821ed5a58a0982158ff8cd8d81d2b59df920e2328

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
	$(INSTALL_BIN) ./files/dnsproxy.init $(1)/etc/init.d/dnsproxy

	$(INSTALL_DIR) $(1)/etc/capabilities/
	$(INSTALL_DATA) ./files/dnsproxy.json $(1)/etc/capabilities/dnsproxy.json

	$(INSTALL_DIR) $(1)/etc/config/
	$(INSTALL_CONF) ./files/dnsproxy.config $(1)/etc/config/dnsproxy
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
