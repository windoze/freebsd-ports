# Created by: J.R. Oldroyd <fbsd@opal.com>
# $FreeBSD$

PORTNAME=	pload
PORTVERSION=	0.9.5
PORTREVISION=	4
CATEGORIES=	net sysutils
MASTER_SITES=	${MASTER_SITE_LOCAL} \
		http://opal.com/jr/freebsd/ports/net/pload/
MASTER_SITE_SUBDIR=	pav

MAINTAINER=	fbsd@opal.com
COMMENT=	X11 program to display network traffic graphs

USES=		imake:env
USE_XORG=	ice sm x11 xaw xext xmu xpm xt
HAS_CONFIGURE=	yes
LATE_INSTALL_ARGS=	install.man

PLIST_FILES=	bin/pload man/man1/pload.1.gz

.include <bsd.port.mk>
