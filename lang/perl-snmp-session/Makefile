#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=perl-snmp-session
PKG_VERSION:=1.13
PKG_RELEASE:=1

MODULE_NAME:=SNMP_Session
MODULE_DOWNLOAD_PATH:=H/HA/HARDAKER
MODULE_FILES:=BER.pm SNMP*.pm
MODULE_TITLE:=SNMP support for Perl 5
MODULE_AUTHORS:=Simon Leinen <simon.leinen@switch.ch>
MODULE_HASH:=a1c6cf5a8893447ab5a6dc38d5bb04b5d492acabb1f282559f9d76b61272ab5f

PKG_SOURCE:=$(MODULE_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://dev.gentoo.org/~dilfridge/distfiles/$(PKG_SOURCE).tar.gz
PKG_HASH:=$(MODULE_HASH)

PKG_LICENSE:=GPL-1.0+ Artistic-1.0-Perl
PKG_MAINTAINER:=$(MODULE_AUTHORS)

PKG_BUILD_DIR:=$(BUILD_DIR)/perl/$(MODULE_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include ../../../packages/lang/perl/perlmod.mk

define Package/$(PKG_NAME)
  SUBMENU:=Perl
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=$(MODULE_TITLE)
  URL:=https://github.com/sleinen/snmp-session
  DEPENDS:=perl
endef

define Build/Configure
        $(call perlmod/Configure,,)
endef

define Build/Compile
        $(call perlmod/Compile,,)
endef

define Package/$(PKG_NAME)/install
        $(call perlmod/Install,$(1),$(MODULE_FILES))
endef


$(eval $(call BuildPackage,$(PKG_NAME)))
