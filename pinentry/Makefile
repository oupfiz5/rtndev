#
# Copyright (C) 2006-2015 OpenWrt.org
# Copyright (C) 2020 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pinentry
PKG_VERSION:=1.1.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://gnupg.org/ftp/gcrypt/pinentry
PKG_HASH:=68076686fa724a290ea49cdf0d1c0c1500907d1b759a3bcbfbec0293e8f56570

PKG_LICENSE:=GPL-2.0+
PKG_LICENSE_FILES:=COPYING

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/pinentry
	SECTION:=utils
	CATEGORY:=Utilities
	SUBMENU:=Encryption
	DEPENDS:=+libassuan +libncursesw +libcap
	TITLE:=GNU pinentry
	URL:=http://www.gnupg.org/
endef

define Package/pinentry/description
 pinentry is a small collection of dialog programs
 that allow GnuPG to read passphrases and PIN numbers
 in a secure manner.
 There are versions for the common GTK and Qt toolkits
 as well as for the text terminal (Curses).
endef

CONFIGURE_ARGS += \
	--enable-pinentry-curses \
	--disable-pinentry-qt5

define Package/pinentry/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/pinentry-curses \
		$(1)/opt/bin/pinentry
endef

$(eval $(call BuildPackage,pinentry))
