#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=sqm-scripts
PKG_SOURCE_VERSION:=0325ba47045e82faef9794b9e702dbb673cfe18d
PKG_VERSION:=1.6.0
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/tohojo/sqm-scripts
PKG_MIRROR_HASH:=6237ef0a012fe0b19ce76617101b30e4ffafd6fd0f81141ae2aeab2236c9a8f8

PKG_MAINTAINER:=Toke Høiland-Jørgensen <toke@toke.dk>
PKG_LICENSE:=GPL-2.0-only

include $(INCLUDE_DIR)/package.mk

define Package/sqm-scripts
  SECTION:=net
  CATEGORY:=Base system
  DEPENDS:=+tc +kmod-sched-cake +kmod-ifb +iptables +iptables-mod-ipopt
  TITLE:=SQM Scripts (QoS)
  PKGARCH:=all
endef

define Package/sqm-scripts/description
 A set of scripts that does simple SQM configuration.
endef

define Package/sqm-scripts/conffiles
/etc/config/sqm
/etc/sqm/sqm.conf
endef

define Package/sqm-scripts/install
	make -C $(PKG_BUILD_DIR) DESTDIR=$(1) PLATFORM=openwrt install
endef

$(eval $(call BuildPackage,sqm-scripts))
