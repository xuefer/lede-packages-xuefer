#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=setproctitle
PKG_VERSION:=1.1.10
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/5a/0d/dc0d2234aacba6cf1a729964383e3452c52096dc695581248b548786f2b3/
PKG_HASH:=6283b7a58477dd8478fbb9e76defb37968ee4ba47b05ec1c053cb39638bd7398

PKG_BUILD_DEPENDS:=python python-setuptools

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Xuefer <xuefer@gmail.com>

include $(INCLUDE_DIR)/package.mk
include ../../../../packages/lang/python/python-package.mk

define Package/python-setproctitle
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python-setproctitle
	URL:=https://pypi.python.org/pypi/setproctitle
	DEPENDS:=+python-light
endef

define Package/python-setproctitle/description
The setproctitle module allows a process to change its title (as displayed by system tools such as ps and top).
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

$(eval $(call PyPackage,python-setproctitle))
$(eval $(call BuildPackage,python-setproctitle))
