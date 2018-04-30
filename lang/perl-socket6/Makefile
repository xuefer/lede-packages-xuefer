#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=perl-socket6
PKG_VERSION:=0.28
PKG_RELEASE:=1

MODULE_NAME:=Socket6
MODULE_DOWNLOAD_PATH:=U/UM/UMEMOTO
MODULE_FILES:=Socket6.pm auto/Socket6
MODULE_TITLE:=This module provides glue routines to the various IPv6 functions.
MODULE_AUTHORS:=
MODULE_HASH:=bfd49ab99f3197c99285fed4683c4edc06277c1e4453f593e694d7bff0974586

PKG_SOURCE_URL:=http://www.cpan.org/authors/id/$(MODULE_DOWNLOAD_PATH)
PKG_SOURCE:=$(MODULE_NAME)-$(PKG_VERSION).tar.gz
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
  URL:=http://search.cpan.org/dist/$(MODULE_NAME)/
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
