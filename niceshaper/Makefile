# Copyright (C) 2015-2016 Artur Stepniewski

include $(TOPDIR)/rules.mk

PKG_NAME:=niceshaper
PKG_VERSION:=1.2.3
PKG_RELEASE:=1

PKG_SOURCE_URL:=http://niceshaper.jedwabny.net/files
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_MD5SUM:=b0fbd599127a0878a15fb1534d0e6dee

ETC_DIR=$(1)/etc
SBIN_DIR=$(1)/usr/sbin

include $(INCLUDE_DIR)/package.mk

define Package/niceshaper
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:= +libpthread +libstdcpp +tc +kmod-sched
	TITLE:=HTB based traffic shaper
	URL:=http://niceshaper.jedwabny.net/page/en/index
endef

define Package/niceshaper/conffiles
	/etc/niceshaper/class.conf
	/etc/niceshaper/config.conf
endef

define Package/niceshaper/description
	Niceshaper is HTB configurator that gives you dynamic traffic management, which is more effective than traditional, static htb shaping.
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) CXX=$(TARGET_CXX)
endef

define Package/niceshaper/install
	$(INSTALL_DIR) $(SBIN_DIR)
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/niceshaper $(SBIN_DIR)/niceshaper
	$(INSTALL_DIR) $(ETC_DIR)/init.d
	$(INSTALL_BIN) ./files/niceshaper.init $(ETC_DIR)/init.d/niceshaper
	$(INSTALL_DIR) $(ETC_DIR)/niceshaper
	$(CP) $(PKG_BUILD_DIR)/etc/niceshaper/* $(ETC_DIR)/niceshaper
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
