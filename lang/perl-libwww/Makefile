#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=perl-libwww
PKG_VERSION:=6.33
PKG_RELEASE:=1

MODULE_NAME:=libwww-perl
MODULE_DOWNLOAD_PATH:=O/OA/OALDERS
MODULE_FILES:=LWP LWP.pm auto/libwww
MODULE_TITLE:=The World-Wide Web library for Perl
MODULE_AUTHORS:=...
MODULE_HASH:=97417386f11f007ae129fe155b82fd8969473ce396a971a664c8ae6850c69b99
MODULE_DEPENDS:= \
  perl-html-parser \
  perl-html-tagset \
  perl-http-cookies \
  perl-http-daemon \
  perl-http-date \
  perl-http-message \
  perl-http-negotiate \
  perl-net-http \
  perl-try-tiny \

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
