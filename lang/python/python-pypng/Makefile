#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pypng
PKG_VERSION:=0.0.18
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/2f/b1/c8dfcf50feb12a30be7d95c5f45d638704682487d8e50419ef41463febcd/
PKG_HASH:=985a1306319e3187e2cb3dabec95a7a0f0f281ae2e1fec04289bed520fecd932

PKG_BUILD_DEPENDS:=python python-setuptools

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Xuefer <xuefer@gmail.com>

include $(INCLUDE_DIR)/package.mk
include ../../../../packages/lang/python/python-package.mk

define Package/python-pypng
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python-pypng
	URL:=https://pypi.python.org/pypi/pypng
	DEPENDS:=+python-light
endef

define Package/python-pypng/description
PyPNG allows PNG image files to be read and written using pure Python.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

$(eval $(call PyPackage,python-pypng))
$(eval $(call BuildPackage,python-pypng))
