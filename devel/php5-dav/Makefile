# Created by: Valery Komarov <komarov@valerka.net>
# $FreeBSD$

PORTNAME=	dav
PORTVERSION=	1.2
PORTREVISION=	1
CATEGORIES=	devel
MASTER_SITES=	http://download.pureftpd.org/php-webdav/
PKGNAMEPREFIX=	php5-
DISTNAME=	php-webdav-${PORTVERSION}

MAINTAINER=	komarov@valerka.net
COMMENT=	The PHP WebDAV extension

LICENSE=	ISCL

LIB_DEPENDS=	libneon.so:${PORTSDIR}/www/neon

USE_PHP=	yes
USE_PHPIZE=	yes
USE_PHPEXT=	yes
PHP_MODNAME=	dav

WRKSRC=		${WRKDIR}/${PORTNAME}

.include <bsd.port.mk>
