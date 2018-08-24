#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=future
PKG_VERSION:=0.16.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/00/2b/8d082ddfed935f3608cc61140df6dcbf0edea1bc3ab52fb6c29ae3e81e85/
PKG_HASH:=e39ced1ab767b5936646cedba8bcce582398233d6a627067d4c6a454c90cfedb

PKG_BUILD_DEPENDS:=python python-setuptools

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Xuefer <xuefer@gmail.com>

include $(INCLUDE_DIR)/package.mk
include ../../../../packages/lang/python/python-package.mk

define Package/python-future
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python-future
	URL:=https://pypi.python.org/pypi/future
	DEPENDS:=+python-light
endef

define Package/python-future/description
future is the missing compatibility layer between Python 2 and Python 3. It allows you to use a single, clean Python 3.x-compatible codebase to support both Python 2 and Python 3 with minimal overhead.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

$(eval $(call PyPackage,python-future))
$(eval $(call BuildPackage,python-future))
