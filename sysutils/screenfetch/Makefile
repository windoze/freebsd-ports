# Created by: Jason Helfman <jgh@FreeBSD.org>
# $FreeBSD$

PORTNAME=	screenFetch
PORTVERSION=	3.6.5
PORTREVISION=	1
CATEGORIES=	sysutils
MASTER_SITES=	LOCAL/jgh/sysutils/${PORTNAME:tl}/ \
		GHL

MAINTAINER=	jgh@FreeBSD.org
COMMENT=	Bash Screenshot Information Tool

LICENSE=	GPLv3

RUN_DEPENDS=	bash:${PORTSDIR}/shells/bash \
		xdpyinfo:${PORTSDIR}/x11/xdpyinfo

OPTIONS_DEFINE=	DOCS

NO_BUILD=	yes
USE_GITHUB=	yes
GH_ACCOUNT=	KittyKatt
GH_TAGNAME=	0fb5733

PLIST_FILES=	bin/screenFetch bin/screenfetch man/man1/screenfetch.1.gz
PORTDOCS=	CHANGELOG README.mkdn TODO

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/${PORTNAME:tl}-dev ${STAGEDIR}${PREFIX}/bin/${PORTNAME}
	${LN} -fs ${PORTNAME} ${STAGEDIR}${PREFIX}/bin/screenfetch
	${INSTALL_MAN} ${WRKSRC}/screenfetch.1 ${STAGEDIR}${MAN1PREFIX}/man/man1
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
.for file in ${PORTDOCS}
	${INSTALL_DATA} ${WRKSRC}/${file} ${STAGEDIR}${DOCSDIR}
.endfor

.include <bsd.port.mk>
