# Created by: sanpei@FreeBSD.org
# $FreeBSD$

PORTNAME=	amfm
PORTVERSION=	1.0
CATEGORIES=	misc
MASTER_SITES=	http://github.com/ikegam/amfm/raw/9679aa06eead7ed3571480e892f426828e17e361/ \
		${MASTER_SITE_LOCAL}
MASTER_SITE_SUBDIR=	sanpei
DISTNAME=	amfm
EXTRACT_SUFX=	.c

MAINTAINER=	sanpei@FreeBSD.org
COMMENT=	THANKO USB AM/FM Radio controller

LIB_DEPENDS=	libhid.so:${PORTSDIR}/devel/libhid

NO_WRKSUBDIR=   yes

EXTRACT_CMD=            ${CP}
EXTRACT_BEFORE_ARGS=    -p
EXTRACT_AFTER_ARGS=     ${WRKDIR}

do-install:
	@${INSTALL} ${WRKSRC}/amfm ${STAGEDIR}${PREFIX}/bin/amfm
	@${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/amfm

.include <bsd.port.mk>
