# Created by: Steve Wills <swills@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Lexical-Var
PORTVERSION=	0.009
PORTREVISION=	1
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	perl@FreeBSD.org
COMMENT=	Perl module for static variables without namespace pollution

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

USES=		perl5
USE_PERL5=	modbuild

post-patch:
	@${REINPLACE_CMD} -e '/Lexical::SealRequireHints/d' ${WRKSRC}/Build.PL ${WRKSRC}/lib/Lexical/Var.pm

.include <bsd.port.mk>
