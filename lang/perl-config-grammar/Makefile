#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=perl-config-grammar
PKG_VERSION:=1.12
PKG_RELEASE:=1

MODULE_NAME:=Config-Grammar
MODULE_DOWNLOAD_PATH:=D/DS/DSCHWEI
MODULE_FILES:=Config
MODULE_TITLE:=A grammar-based, user-friendly config parser
MODULE_AUTHORS:=David Schweikert, Tobias Oetiker, Niko Tyni
MODULE_HASH:=7a52a3657d96e6f1f529caaa09ec3bf7dd6a245b47875382c323902f6d9590b0
MODULE_DEPENDS:=

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
  DEPENDS:=perl $(addprefix +,$(MODULE_DEPENDS))
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
