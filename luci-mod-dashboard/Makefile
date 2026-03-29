include $(TOPDIR)/rules.mk

PKG_NAME:=luci-mod-dashboard
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_LICENSE:=MIT
PKG_MAINTAINER:=OAT Theme Contributors

LUCI_TITLE:=LuCI Dashboard Module
LUCI_DESCRIPTION:=Modern dashboard for OpenWrt with system stats, VPN status, traffic monitoring, and quick access links. Designed to work with the OAT theme.
LUCI_DEPENDS:=+luci-base
LUCI_PKGARCH:=all
LUCI_TYPE:=mod

include $(TOPDIR)/feeds/luci/luci.mk

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/www/luci-static/resources/view/dashboard
	$(INSTALL_DIR) $(1)/www/luci-static/resources/view/dashboard/include
	$(INSTALL_DIR) $(1)/www/luci-static/resources/view/dashboard/css
	$(INSTALL_DIR) $(1)/www/luci-static/resources/view/dashboard/icons
	$(INSTALL_DIR) $(1)/usr/share/rpcd/acl.d
	$(INSTALL_DIR) $(1)/usr/share/luci/menu.d
	$(INSTALL_DIR) $(1)/usr/libexec

	[ -d ./htdocs/luci-static/resources/view/dashboard ] && \
		$(CP) ./htdocs/luci-static/resources/view/dashboard/*.js $(1)/www/luci-static/resources/view/dashboard/ || true
	
	[ -d ./htdocs/luci-static/resources/view/dashboard/include ] && \
		$(CP) ./htdocs/luci-static/resources/view/dashboard/include/*.js $(1)/www/luci-static/resources/view/dashboard/include/ || true
	
	[ -d ./htdocs/luci-static/resources/view/dashboard/css ] && \
		$(CP) ./htdocs/luci-static/resources/view/dashboard/css/*.css $(1)/www/luci-static/resources/view/dashboard/css/ || true
	
	[ -d ./htdocs/luci-static/resources/view/dashboard/icons ] && \
		$(CP) ./htdocs/luci-static/resources/view/dashboard/icons/*.svg $(1)/www/luci-static/resources/view/dashboard/icons/ || true
	
	[ -d ./root/usr/share/rpcd/acl.d ] && \
		$(CP) ./root/usr/share/rpcd/acl.d/*.json $(1)/usr/share/rpcd/acl.d/ || true
	
	[ -d ./root/usr/share/luci/menu.d ] && \
		$(CP) ./root/usr/share/luci/menu.d/*.json $(1)/usr/share/luci/menu.d/ || true
	
	[ -f ./root/usr/libexec/vpn-status.sh ] && \
		$(INSTALL_BIN) ./root/usr/libexec/vpn-status.sh $(1)/usr/libexec/ || true
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
