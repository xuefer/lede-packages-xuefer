#
# Copyright (C) 2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=Beaker
PKG_VERSION:=1.10.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/c2/21/b052b2fbfee3def06670923d5d34b0d353d4c278013e4a714c3fb663f150/
PKG_HASH:=6072892918225f5a055413082f2ff285f3ebca6a3873a0d6e163253ba83f0450

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-$(PKG_NAME)-$(PKG_VERSION)

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Xuefer <xuefer@gmail.com>

include $(INCLUDE_DIR)/package.mk
include ../../../../packages/lang/python/python-package.mk
include ../../../../packages/lang/python/python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python-beaker/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  URL:=https://pypi.org/project/Beaker/
endef

define Package/python-beaker
$(call Package/python-beaker/Default)
  TITLE:=Beaker
  DEPENDS:=+python-light
  VARIANT:=python
endef

define Package/python3-beaker
$(call Package/python-beaker/Default)
  TITLE:=Beaker
  DEPENDS:=+python3-light
  VARIANT:=python3
endef

define Package/python-beaker/description
Beaker is a web session and general caching library that includes WSGI middleware for use in web applications.
endef

define Package/python3-beaker/description
$(call Package/python-beaker/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-beaker))
$(eval $(call BuildPackage,python-beaker))
$(eval $(call Py3Package,python3-beaker))
$(eval $(call BuildPackage,python3-beaker))
