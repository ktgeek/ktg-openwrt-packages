include $(TOPDIR)/rules.mk

PKG_NAME:=blulb
PKG_VERSION:=0.1
PKG_RELEASE:=2

SOURCE_DIR:=/work/src/blinkstick-userspace-led-daemon

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/ktgeek/blinkstick-userspace-led-daemon.git
PKG_SOURCE_DATE:=2019-10-28
PKG_SOURCE_VERSION:=ed171fbcfc6e89335751813b381ef86ac8b14190

PKG_MAINTAINER:=Keith T. Garner <kgarner@kgarner.com>
PKG_LICENSE:=MIT

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/kernel.mk

EXTRA_CXXFLAGS = -I$(LINUX_DIR)/include
EXTRA_CFLAGS = -I$(LINUX_DIR)/include

include $(INCLUDE_DIR)/cmake.mk

define Package/bluld
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Blinkstick User space LED Daemon
  DEPENDS:=+libstdcpp +hidapi
endef

define Package/bluld/description
  A daemon to expose a Blinkstick to the Linux kernel LED class via /dev/uleds. (Kernel 4.10+ required.)
endef

define Package/bluld/conffiles
/etc/config/bluld
endef

define Package/bluld/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/bluld $(1)/usr/sbin
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/bluld.conf $(1)/etc/config/bluld
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/bluld.init $(1)/etc/init.d/bluld.init
endef

$(eval $(call BuildPackage,bluld))

