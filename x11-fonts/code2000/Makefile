# Created by: Thierry Thomas <thierry@pompo.net>
# $FreeBSD$

PORTNAME=	code2000
PORTVERSION=	1.171
PORTREVISION=	2
CATEGORIES=	x11-fonts
MASTER_SITES=	${MASTER_SITE_LOCAL}
MASTER_SITE_SUBDIR=	thierry/${DIST_SUBDIR}
DISTFILES=	${PORTNAME:tu}${EXTRACT_SUFX:tu}
DIST_SUBDIR=	${PORTNAME}-${PORTVERSION}

MAINTAINER=	thierry@FreeBSD.org
COMMENT=	Shareware demo Unicode TrueType font

USES=		fonts zip

SUB_FILES=	pkg-message

NO_BUILD=	yes

post-extract:
	${MKDIR} ${WRKSRC}
	${MV} ${WRKDIR}/CODE2000.TTF ${WRKSRC}/${FONTNAME}.ttf
	${MV} ${WRKDIR}/CODE2000.HTM ${WRKSRC}/${FONTNAME}.html

do-install:
	${MKDIR} ${STAGEDIR}${FONTSDIR}
	${INSTALL_DATA} ${WRKSRC}/* ${STAGEDIR}${FONTSDIR}

.include <bsd.port.mk>
