# Created by: Sergey Skvortsov <skv@FreeBSD.org>
# $FreeBSD$

PORTNAME=	podlators
PORTVERSION=	2.5.3
PORTREVISION=	2
CATEGORIES=	textproc perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	Pod
PKGNAMEPREFIX=	p5-

MAINTAINER=	perl@FreeBSD.org
COMMENT=	Modules to convert and parse POD (Plain Old Documentation)

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

USES=		perl5
USE_PERL5=	configure

post-patch:
	@${REINPLACE_CMD} -e "/man1pod (/d; /EXE_FILES/d" ${WRKSRC}/Makefile.PL

.include <bsd.port.mk>
