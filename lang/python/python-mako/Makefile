#
# Copyright (C) 2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=Mako
PKG_VERSION:=1.0.7
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/eb/f3/67579bb486517c0d49547f9697e36582cd19dafb5df9e687ed8e22de57fa/
PKG_HASH:=4e02fde57bd4abb5ec400181e4c314f56ac3e49ba4fb8b0d50bba18cb27d25ae

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include ../../../../packages/lang/python/python-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python-mako/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  URL:=https://pypi.org/project/Mako/
endef

define Package/python-mako
$(call Package/python-mako/Default)
  TITLE:=Mako Templates for Python
  DEPENDS:=+python-light
  VARIANT:=python
endef

define Package/python3-mako
$(call Package/python-mako/Default)
  TITLE:=Mako Templates for Python
  DEPENDS:=+python3-light
  VARIANT:=python3
endef

define Package/python-mako/description
Mako is a template library written in Python. It provides a familiar,
non-XML syntax which compiles into Python modules for maximum
performance. Mako's syntax and API borrows from the best ideas of many
others, including Django templates, Cheetah, Myghty, and
Genshi. Conceptually, Mako is an embedded Python (i.e. Python Server
Page) language, which refines the familiar ideas of componentized
layout and inheritance to produce one of the most straightforward and
flexible models available, while also maintaining close ties to Python
calling and scoping semantics.
endef

define Package/python3-mako/description
$(call Package/python-mako/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-mako))
$(eval $(call BuildPackage,python-mako))
$(eval $(call Py3Package,python3-mako))
$(eval $(call BuildPackage,python3-mako))
