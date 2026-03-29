include $(TOPDIR)/rules.mk

LUCI_TITLE:=Oat Theme (OAT UI styled)
LUCI_DEPENDS:=+luci-base
PKG_VERSION:=1.0
PKG_RELEASE:=20260216
PKG_LICENSE:=Apache-2.0

LUCI_TYPE:=theme

define Package/luci-theme-oat/postrm
#!/bin/sh
[ -n "$${IPKG_INSTROOT}" ] || {
    uci -q delete luci.themes.Oat
    uci set luci.main.mediaurlbase='/luci-static/bootstrap'
    uci commit luci
}
exit 0
endef

include $(TOPDIR)/feeds/luci/luci.mk

LUCI_MINIFY_CSS:=0

$(eval $(call BuildPackage,luci-theme-oat))
