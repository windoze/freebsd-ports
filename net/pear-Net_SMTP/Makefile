# Created by: Thierry Thomas (<thierry@pompo.net>)
# $FreeBSD$

PORTNAME=	Net_SMTP
PORTVERSION=	1.6.2
CATEGORIES=	net mail www pear

MAINTAINER=	ports@FreeBSD.org
COMMENT=	PEAR class that provides an implementation of the SMTP protocol

BUILD_DEPENDS=	${PEARDIR}/Net/Socket.php:${PORTSDIR}/net/pear-Net_Socket
RUN_DEPENDS=	${PEARDIR}/Net/Socket.php:${PORTSDIR}/net/pear-Net_Socket

USES=	pear

OPTIONS_DEFINE=	PEAR_AUTH_SASL
PEAR_AUTH_SASL_DESC=	PEAR::Auth_SASL support

PEAR_AUTH_SASL_BUILD_DEPENDS=	${PEARDIR}/Auth/SASL.php:${PORTSDIR}/security/pear-Auth_SASL

.include <bsd.port.mk>
