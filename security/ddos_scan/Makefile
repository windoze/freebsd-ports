# Created by: David O'Brien (obrien@NUXI.com)
# $FreeBSD$

PORTNAME=	ddos_scan
PORTVERSION=	1.6
PORTREVISION=	1
CATEGORIES=	security
MASTER_SITES=	http://staff.washington.edu/dittrich/misc/
DISTNAME=	${PORTNAME}
EXTRACT_SUFX=	.tar

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Scans for a limited set of distributed denial of service agents

ALL_TARGET=	dds

OPTIONS_DEFINE=	DOCS

do-install:
	@${INSTALL_PROGRAM} ${WRKSRC}/dds ${STAGEDIR}${PREFIX}/sbin
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	@${INSTALL_MAN} ${WRKSRC}/README ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
