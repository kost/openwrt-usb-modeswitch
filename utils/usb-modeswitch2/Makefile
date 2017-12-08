#
# Copyright (C) 2008-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=usb-modeswitch2
PKG_VERSION:=2.5.1
PKG_RELEASE:=1

# # http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-2.5.1.tar.bz2
# PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE:=usb-modeswitch-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://www.draisberghof.de/usb_modeswitch
PKG_MD5SUM:=7e6435a2afe7aed8574fe59cf09a3503
PKG_BUILD_DIR:=usb-modeswitch-$(PKG_VERSION)
PKG_DEPENDS:=+libusb-1.0

include $(INCLUDE_DIR)/package.mk

define Package/usb-modeswitch2
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+libusb-1.0
  TITLE:=USB ModeSwitch
  URL:=http://www.draisberghof.de/usb_modeswitch/
endef

define Package/usb-modeswitch2/description
  A mode switching tool for controlling
  "flip flop" (multiple device) USB gear.
endef

define Build/Compile
	$(TARGET_CC) $(TARGET_CFLAGS) $(TARGET_CPPFLAGS) $(TARGET_LDFLAGS) \
		-lusb-1.0 \
		-o $(PKG_BUILD_DIR)/usb_modeswitch-OpenWrt \
				$(PKG_BUILD_DIR)/usb_modeswitch.c
endef

define Package/usb-modeswitch2/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/usb_modeswitch-OpenWrt $(1)/usr/bin/usb_modeswitch
	$(INSTALL_DIR) $(1)/etc/hotplug.d/usb
	$(INSTALL_DATA) ./files/modeswitch.hotplug $(1)/etc/hotplug.d/usb/20-modeswitch
endef

$(eval $(call BuildPackage,usb-modeswitch2))
