# Created by: bland@FreeBSD.org
# $FreeBSD$

PORTNAME=	icu
PORTVERSION=	1.8
CATEGORIES=	devel python
MASTER_SITES=	${MASTER_SITE_CHEESESHOP}
MASTER_SITE_SUBDIR=	source/P/PyICU
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTNAME=	PyICU-${PORTVERSION}

MAINTAINER=	bland@FreeBSD.org
COMMENT=	Python extension wrapping IBM's ICU C++ API

USES=		python
USE_PYTHON=	distutils autoplist

MAKE_ENV+= \
	PYICU_INCLUDES="${PREFIX}/include" \
	PYICU_CFLAGS="-w:-DPYICU_VER=\"$(PORTVERSION)\"" \
	PYICU_LFLAGS="-L${PREFIX}/lib"

LIB_DEPENDS+=	libicudata.so:${PORTSDIR}/devel/icu

.include <bsd.port.mk>
