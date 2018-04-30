#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=perl-io-socket-ssl
PKG_VERSION:=2.056
PKG_RELEASE:=1

MODULE_NAME:=IO-Socket-SSL
MODULE_DOWNLOAD_PATH:=S/SM/SMUELLER
MODULE_FILES:=IO
MODULE_TITLE:=SSL sockets with IO::Socket interface
MODULE_AUTHORS:=Steffen Ullrich <sullr@cpan.org>
MODULE_HASH:=91451ecc28b243a78b438f0a42db24c4b60a86f088879b38e40bdbd697818259

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
