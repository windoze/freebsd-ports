# $FreeBSD$

PORTNAME=	plone.app.folder
PORTVERSION=	1.0.5
PORTREVISION=	1
CATEGORIES=	www python zope
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DIST_SUBDIR=	zope

MAINTAINER=	zope@FreeBSD.org
COMMENT=	Integration package for plone.folder into Plone

LICENSE=	GPLv2

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}plone.folder>=0:${PORTSDIR}/www/py-plone.folder

USES=		python zip
USE_PYTHON=	distutils autoplist

.include <bsd.port.mk>
