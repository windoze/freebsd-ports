# Created by: Gleb Smirnoff <glebius@FreeBSD.org>
# $FreeBSD$

PORTNAME=	xf86-input-egalax
PORTVERSION=	0.3
CATEGORIES=	x11-drivers

MAINTAINER=	glebius@FreeBSD.org
COMMENT=	eGalax touch screen input driver for X.Org

USE_GITHUB=	yes
GH_ACCOUNT=	glebius
GH_PROJECT=	${PORTNAME}
GH_COMMIT=	7f1e4ac
GH_TAGNAME=	${GH_COMMIT}
DIST_SUBDIR=	xorg/driver

LICENSE=	BSD2CLAUSE

GNU_CONFIGURE=	yes
USES=		autoreconf libtool pkgconfig
USE_XORG=	xorg-server xproto xi inputproto xf86driproto glproto \
		randrproto renderproto resourceproto scrnsaverproto xorg-macros
CONFIGURE_ENV=	DRIVER_MAN_SUFFIX=4x DRIVER_MAN_DIR='$$(mandir)/man4'
INSTALL_TARGET=	install-strip

.include <bsd.port.mk>
