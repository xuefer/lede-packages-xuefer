#
# Copyright (C) 2007 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile 9173 2007-10-07 03:20:26Z blogic $

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/uclibc++.mk

PKG_NAME:=rblibtorrent
PKG_VERSION:=1.1.4
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/arvidn/libtorrent.git
PKG_SOURCE_VERSION:=libtorrent-$(subst .,_,$(PKG_VERSION))
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2

PKG_BUILD_PARALLEL:=1
PKG_BUILD_DEPENDS:=libtool python

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Build/Configure
	(cd $(PKG_BUILD_DIR); ACLOCAL_INCLUDE="-I m4 $$$$ACLOCAL_INCLUDE" ./autotool.sh );
	$(call Build/Configure/Default)
endef

define Package/rblibtorrent
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Rasterbar BitTorrent library
  URL:=http://www.rasterbar.com/products/libtorrent/
  DEPENDS:=$(CXX_DEPENDS) +boost-python +boost-filesystem +boost-regex +boost-thread +boost-program_options +boost-system +boost-chrono +boost-random +libopenssl
endef

define Package/rblibtorrent/description
Rasterbar libtorrent is a C++ library that aims to be a good alternative to
all the other bittorrent implementations around. It is a library and not a
full featured client, although it comes with a working example client.
endef

CONFIGURE_VARS+= \
	PYTHON_CFLAGS="-I $(PYTHON_INC_DIR)" \
	PYTHON_LDFLAGS="-L $(PYTHON_LIB_DIR) -l$(PYTHON)" \
	PYTHON_LIBS="-l$(PYTHON)"

CONFIGURE_ARGS+= \
	--enable-shared \
	--disable-debug \
	--enable-python-binding \
	--with-ssl=$(STAGING_DIR)/usr \
	--with-boost=$(STAGING_DIR)/usr/include \
	--with-boost-libdir=$(STAGING_DIR)/usr/lib \
	--with-zlib=detect \
	--with-boost-system=boost_system \
	--with-boost-filesystem=boost_filesystem \
	--with-boost-thread=boost_thread \
	--with-boost-regex=boost_regex \
	--with-boost-python=boost_python \
	--with-boost-program_options=boost_program_options

define Build/Compile
	$(call Build/Compile/Default)
	$(call Build/Install/Default)
endef

define Build/InstallDev
	mkdir -p $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/libtorrent $(1)/usr/include/
	mkdir -p $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	mkdir -p $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libtorrent-rasterbar.pc $(1)/usr/lib/pkgconfig/
endef

define Package/rblibtorrent/install
	$(INSTALL_DIR) $(1)/usr/lib $(1)/$(PYTHON_PKG_DIR)
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/$(PYTHON_PKG_DIR)/*.so* $(1)/$(PYTHON_PKG_DIR)
endef

$(eval $(call BuildPackage,rblibtorrent))
