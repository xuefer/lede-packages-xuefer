#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=perl-data-dumper
PKG_VERSION:=2.161
PKG_RELEASE:=1

MODULE_NAME:=Data-Dumper
MODULE_DOWNLOAD_PATH:=S/SM/SMUELLER
MODULE_FILES:=Data auto/Data
MODULE_TITLE:=stringified perl data structures, suitable for both printing and eval
MODULE_AUTHORS:=Gurusamy Sarathy <gsar@activestate.com>
MODULE_HASH:=3aa4ac1b042b3880438165fb2b2139d377564a8e9928ffe689ede5304ee90558

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
