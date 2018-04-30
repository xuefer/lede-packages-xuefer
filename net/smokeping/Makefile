#
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=smokeping
PKG_VERSION:=2.7.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://oss.oetiker.ch/smokeping/pub/
PKG_HASH:=5277fb88eed3c79c8ed22ca830e099727b0e612e887b64bbfeaa98d8d75d493b

PKG_BUILD_PARALLEL:=1
PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include ../../../packages/lang/perl/perlmod.mk

define Package/smokeping
  SECTION:=net
  CATEGORY:=Network
  TITLE:=SmokePing keeps track of your network latency
  URL:=http://oss.oetiker.ch/smokeping/
  DEPENDS:= \
		+fping \
		+perl \
		+perlbase-config \
		+perlbase-cpan \
		+perlbase-digest \
		+perlbase-findbin \
		+perlbase-getopt \
		+perlbase-net \
		+perlbase-pod \
		+perlbase-storable \
		+perl-cgi \
		+perl-cgi-fast \
		+perl-config-grammar \
		+perl-data-dumper \
		+perl-digest-hmac \
		+perl-fcgi \
		+perl-io-socket-ssl \
		+perl-libwww \
		+perl-net-dns \
		+perl-rrd \
		+perl-snmp-session \
		+perl-socket6
endef

define Package/smokeping/description
  SmokePing keeps track of your network latency:
  . Best of breed latency visualisation.
  . Interactive graph explorer.
  . Wide range of latency measurment plugins.
  . Master/Slave System for distributed measurement.
  . Highly configurable alerting system.
  . Live Latency Charts with the most 'interesting' graphs.
  . Free and OpenSource Software written in Perl written by Tobi Oetiker, the creator of MRTG and RRDtool
endef

define Package/smokeping/conffiles
/etc/smokeping/basepage.html
/etc/smokeping/config
/etc/smokeping/smokemail
/etc/smokeping/smokeping_secrets
/etc/smokeping/tmail
endef

CONFIGURE_VARS += \
  PERL5LIB=$(PERL_SITELIB) \

CONFIGURE_ARGS += \
  --sysconfdir=/etc/smokeping \
  --with-htdocs-dir=/usr/lib/smokeping

define Build/Patch
	$(call Build/Patch/Default,)
	sed -i -e '/^SUBDIRS = / s, thirdparty\| doc,,g' "$(PKG_BUILD_DIR)"/Makefile.am
	echo $(PKG_VERSION) > $(PKG_BUILD_DIR)/VERSION
endef

define Build/Install
	$(call Build/Install/Default,)

	mv "$(PKG_INSTALL_DIR)/etc/smokeping/basepage.html.dist" "$(PKG_INSTALL_DIR)/etc/smokeping/basepage.html"
	mv "$(PKG_INSTALL_DIR)/etc/smokeping/config.dist" "$(PKG_INSTALL_DIR)/etc/smokeping/config"
	mv "$(PKG_INSTALL_DIR)/etc/smokeping/smokemail.dist" "$(PKG_INSTALL_DIR)/etc/smokeping/smokemail"
	mv "$(PKG_INSTALL_DIR)/etc/smokeping/smokeping_secrets.dist" "$(PKG_INSTALL_DIR)/etc/smokeping/smokeping_secrets"
	mv "$(PKG_INSTALL_DIR)/etc/smokeping/tmail.dist" "$(PKG_INSTALL_DIR)/etc/smokeping/tmail"

	sed -i \
		-e '/^imgcache/{s:\(^imgcache[ \t]*=\).*:\1 /var/lib/smokeping/.simg:}' \
		-e '/^imgurl/{s:\(^imgurl[ \t]*=\).*:\1 ../.simg:}' \
		-e '/^datadir/{s:\(^datadir[ \t]*=\).*:\1 /var/lib/smokeping:}' \
		-e '/^piddir/{s:\(^piddir[ \t]*=\).*:\1 /var/run/smokeping:}' \
		-e '/^cgiurl/{s#\(^cgiurl[ \t]*=\).*#\1 http://some.place.xyz/perl/smokeping.pl#}' \
		-e '/^smokemail/{s:\(^smokemail[ \t]*=\).*:\1 /etc/smokeping/smokemail:}' \
		-e '/^tmail/{s:\(^tmail[ \t]*=\).*:\1 /etc/smokeping/tmail:}' \
		-e '/^secrets/{s:\(^secrets[ \t]*=\).*:\1 /etc/smokeping/smokeping_secrets:}' \
		-e '/^template/{s:\(^template[ \t]*=\).*:\1 /etc/smokeping/basepage.html:}' \
		"$(PKG_INSTALL_DIR)/etc/smokeping/config"

	sed -i \
		-e '/^<script/{s:cropper/:/cropper/:}' \
		"$(PKG_INSTALL_DIR)/etc/smokeping/basepage.html"

	sed -i \
		-e 's/$$$$FindBin::RealBin\/..\/etc\/config/\/etc\/smokeping\/config/g' \
		"$(PKG_INSTALL_DIR)/usr/bin/smokeping" "$(PKG_INSTALL_DIR)/usr/bin/smokeping_cgi"

	sed -i \
		-e 's:etc/config.dist:/etc/smokeping/config:' \
		"$(PKG_INSTALL_DIR)/usr/bin/tSmoke"

	sed -i \
		-e 's:/usr/etc/config:/etc/smokeping/config:' \
		"$(PKG_INSTALL_DIR)/usr/lib/smokeping/smokeping.fcgi.dist"

	mv "$(PKG_INSTALL_DIR)/usr/lib/smokeping/smokeping.fcgi.dist" \
	"$(PKG_INSTALL_DIR)/usr/lib/smokeping/smokeping.fcgi" \

	chmod 700 $(PKG_INSTALL_DIR)/etc/smokeping/smokeping_secrets
endef

define Package/smokeping/install
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
	rm -f $(1)/lib/{BER.pm,SNMP_Session.pm,SNMP_util.pm}
endef

$(eval $(call BuildPackage,smokeping))
