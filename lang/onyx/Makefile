# Created by: jasone
# $FreeBSD$

PORTNAME=	onyx
PORTVERSION=	5.1.2
PORTREVISION=	4
CATEGORIES=	lang
MASTER_SITES=	http://www.canonware.com/download/onyx/

MAINTAINER=	bofh@FreeBSD.org
COMMENT=	Embeddable stack-based threaded interpreted language

LICENSE=	BSD2CLAUSE

BUILD_DEPENDS=	cook:${PORTSDIR}/devel/cook
LIB_DEPENDS=	libedit.so:${PORTSDIR}/devel/libedit \
		libpcre.so:${PORTSDIR}/devel/pcre

USES=		tar:bzip2 shebangfix
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--with-libedit-prefix=${LOCALBASE} \
		--with-pcre-prefix=${LOCALBASE}
USE_LDCONFIG=	yes
SUB_FILES=	pkg-message

OPTIONS_DEFINE=	DOCS
PLIST_SUB=	ONYX_VERSION=${PORTVERSION}

BROKEN_ia64=	Coredump during build on ia64

.include <bsd.port.options.mk>

do-build:
	@(cd ${WRKSRC}; ${SETENV} ${MAKE_ENV} cook)

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/bin/onyx/bin/onyx ${STAGEDIR}${PREFIX}/bin
	${INSTALL_SCRIPT} ${WRKSRC}/bin/onyx_config/bin/onyx_config ${STAGEDIR}${PREFIX}/bin
	${LN} -sf bin/onyx ${STAGEDIR}${PREFIX}/bin/${PORTNAME}-${PORTVERSION}
	${LN} -sf bin/onyx_config ${STAGEDIR}${PREFIX}/bin/${PORTNAME}_config-${PORTVERSION}
	${MKDIR} ${STAGEDIR}${PREFIX}/include/libonyx
	${INSTALL_DATA} ${WRKSRC}/lib/libonyx/include/libonyx/*.h ${STAGEDIR}${PREFIX}/include/libonyx
	${INSTALL_LIB} ${WRKSRC}/lib/libonyx/lib/libonyx.a ${STAGEDIR}${PREFIX}/lib
	${INSTALL_LIB} ${WRKSRC}/lib/libonyx/lib/libonyx.so ${STAGEDIR}${PREFIX}/lib
	${INSTALL_LIB} ${WRKSRC}/lib/libonyx/lib/libonyx.so.13 ${STAGEDIR}${PREFIX}/lib
	${MKDIR} ${STAGEDIR}${DATADIR}/nx/modclopt
	${INSTALL_DATA} ${WRKSRC}/mod/modclopt/nx/modclopt/*.nx ${STAGEDIR}${DATADIR}/nx/modclopt
	${MKDIR} ${STAGEDIR}${DATADIR}/libonyx
	${INSTALL_DATA} ${WRKSRC}/lib/libonyx/src/libonyx_init.nx ${STAGEDIR}${DATADIR}/libonyx
	${MKDIR} ${STAGEDIR}${DATADIR}/nx/modprompt
	${INSTALL_DATA} ${WRKSRC}/mod/modprompt/nx/modprompt/modprompt.nx ${STAGEDIR}${DATADIR}/nx/modprompt
	${INSTALL_MAN} ${WRKSRC}/bin/onyx/man/man1/onyx.1 ${STAGEDIR}${PREFIX}/man/man1
	${INSTALL_MAN} ${WRKSRC}/bin/onyx_config/man/man1/onyx_config.1 ${STAGEDIR}${PREFIX}/man/man1
.if ${PORT_OPTIONS:MDOCS}
	${MKDIR} ${STAGEDIR}${DOCSDIR}/html
	(cd ${WRKSRC}/doc/html/onyx && ${COPYTREE_SHARE} . ${STAGEDIR}${DOCSDIR}/html)
	${MKDIR} ${STAGEDIR}${DOCSDIR}/pdf
	${INSTALL_DATA} ${WRKSRC}/doc/pdf/onyx/onyx.pdf ${STAGEDIR}${DOCSDIR}/pdf
.endif

.include <bsd.port.mk>
