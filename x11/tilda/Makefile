# $FreeBSD$

PORTNAME=	tilda
PORTVERSION=	1.2.2
CATEGORIES=	x11
MASTER_SITES=	https://github.com/lanoxx/${PORTNAME}/archive/

MAINTAINER=	rodrigo@FreeBSD.org
COMMENT=	Drop down x11 terminal with transparency support

LICENSE=	GPLv2

LIB_DEPENDS=	libconfuse.so:${PORTSDIR}/devel/libconfuse \
		libvte2_90.so:${PORTSDIR}/x11-toolkits/vte290

WRKSRC=		${WRKDIR}/${PORTNAME}-${DISTNAME}
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--disable-rpath
USE_GNOME=	gtk30
USES=		gmake gettext pkgconfig autoreconf pathfix libtool
INSTALL_TARGET=	install-strip

DOCS=		AUTHORS ChangeLog HACKING.md README.md TODO.md

OPTIONS_DEFINE=	DOCS

post-install:
	${MKDIR} ${STAGEDIR}${DOCSDIR}
.for f in ${DOCS}
	${INSTALL_DATA} ${WRKSRC}/${f} ${STAGEDIR}${DOCSDIR}
.endfor
	@${ECHO_MSG} ""
	@${ECHO_MSG} ""
	@${ECHO_MSG} "		ATTENTION:"
	@${ECHO_MSG} "		If you are upgrade from version 0.09.1 or below,"
	@${ECHO_MSG} "		you'll need to delete your old config files and "
	@${ECHO_MSG} "		make them again."
	@${ECHO_MSG} ""
	@${ECHO_MSG} ""

.include <bsd.port.mk>
