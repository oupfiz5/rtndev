#
# Copyright (C) 2011-2020 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=25volt
PKG_VERSION:=1.0.5
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/25volt
	SECTION:=utils
	CATEGORY:=Utilities
	DEPENDS:=+libusb-compat
	TITLE:=25volt a tool for monitoring Powercom/APC UPSs
	URL:=http://c61.no-ip.org/forum/viewtopic.php?f=2&t=69
	MAINTAINER:=Entware team, https://entware.net
endef

define Package/25volt/description
 25volt - A lightweight tool for monitoring APC Smart-UPS and Powercom WOW UPSs.
endef

BINARIES:= \
	usb_ups_apc_smart \
	usb_ups_powercom_wow

define Build/Compile
	for bin in $(BINARIES); \
	do \
	    $(TARGET_CC) $(TARGET_CFLAGS) -I$(STAGING_DIR)/opt/include \
	    $(TARGET_LDFLAGS) -L$(STAGING_DIR)/opt/lib -lusb -s \
	    -o $(PKG_BUILD_DIR)/$$$${bin} $(PKG_BUILD_DIR)/$$$${bin}.c; \
	done
endef

define Package/25volt/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(foreach bin,$(BINARIES),$(PKG_BUILD_DIR)/$(bin)) \
	    $(1)/opt/bin
endef

$(eval $(call BuildPackage,25volt))
