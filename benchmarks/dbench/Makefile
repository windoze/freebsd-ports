# Created by: Andrew Shevtsov <nyxo@dnuc.polyn.kiae.su>
# $FreeBSD$

PORTNAME=	dbench
PORTVERSION=	4.0
PORTREVISION=	2
CATEGORIES=	benchmarks
MASTER_SITES=	SAMBA
MASTER_SITE_SUBDIR=	../../ftp/tridge/dbench

MAINTAINER=	jlaffaye@FreeBSD.org
COMMENT=	Simulation of the Ziff-Davis netbench benchmark

BROKEN=		Unfetchable
LIB_DEPENDS=	libpopt.so:${PORTSDIR}/devel/popt

LICENSE=	GPLv3

CFLAGS+=	-I${LOCALBASE}/include
LIBS+=		-L${LOCALBASE}/lib
USE_AUTOTOOLS=	autoconf
GNU_CONFIGURE=	yes
CONFIGURE_ARGS+=--datadir=${DATADIR}

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/*

.include <bsd.port.mk>
