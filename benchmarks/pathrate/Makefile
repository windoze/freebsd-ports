# Created by: dikshie <dikshie@lapi.itb.ac.id>
# $FreeBSD$

PORTNAME=	pathrate
PORTVERSION=	2.4.1
CATEGORIES=	benchmarks
MASTER_SITES=	http://www.cc.gatech.edu/fac/Constantinos.Dovrolis/
DISTNAME=	${PORTNAME}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Measurement tool for capacity estimation of network paths

BROKEN=		Unfetchable
GNU_CONFIGURE=	yes
USES=		gmake

WRKSRC=		${WRKDIR}/${PORTNAME}_${PORTVERSION}
MAKEFILE=	makefile

PLIST_FILES=	bin/pathrate_rcv bin/pathrate_snd

do-install:
.for f in pathrate_rcv pathrate_snd
	${INSTALL_PROGRAM} ${WRKSRC}/${f} ${STAGEDIR}${PREFIX}/bin
.endfor

.include <bsd.port.mk>
