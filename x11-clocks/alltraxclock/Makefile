# Created by: Roman Bogorodskiy <bogorodskiy@inbox.ru>
# $FreeBSD$

PORTNAME=	alltraxclock
PORTVERSION=	2.0.2
PORTREVISION=	11
CATEGORIES=	x11-clocks
MASTER_SITES=	http://perso.wanadoo.fr/alltrax/ \
		${MASTER_SITE_LOCAL}
MASTER_SITE_SUBDIR=	novel
DISTNAME=	${PORTNAME}2_0.2-1

MAINTAINER=	novel@FreeBSD.org
COMMENT=	Analog clock plugin for gkrellm2

BUILD_DEPENDS=	${LOCALBASE}/include/gkrellm2/gkrellm.h:${PORTSDIR}/sysutils/gkrellm2
RUN_DEPENDS=	gkrellm:${PORTSDIR}/sysutils/gkrellm2

USES=		pkgconfig
ALL_TARGET=	alltraxclock.so
PLIST_FILES=	libexec/gkrellm2/plugins/alltraxclock.so
WRKSRC=		${WRKDIR}/${PORTNAME}2_0.2/

post-patch:
	@${REINPLACE_CMD} -e 's|gcc|${CC}|;s|-O2||' ${WRKSRC}/Makefile

do-install:
	@${MKDIR} ${STAGEDIR}${PREFIX}/libexec/gkrellm2/plugins/
	${INSTALL_PROGRAM} ${WRKSRC}/alltraxclock.so ${STAGEDIR}${PREFIX}/libexec/gkrellm2/plugins/

.include <bsd.port.mk>
