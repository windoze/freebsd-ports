# Created by: Yuri Victorovich <yuri@rawbw.com>
# $FreeBSD$

PORTNAME=	rapidjson
PORTVERSION=	0.150310
CATEGORIES=	devel textproc

MAINTAINER=	yuri@rawbw.com
COMMENT=	Fast JSON parser/generator for C++ with both SAX/DOM style API

LICENSE=	unknown
LICENSE_NAME=	RapidJSON
LICENSE_FILE=	${WRKSRC}/license.txt
LICENSE_PERMS=	${_LICENSE_PERMS_DEFAULT}

USE_GITHUB=	yes
GH_ACCOUNT=	miloyip
GH_COMMIT=	c745c95
GH_TAGNAME=	${GH_COMMIT}

USES=		cmake compiler:c++11-lang gmake

OPTIONS_DEFINE=	DOCS EXAMPLES
OPTIONS_DEFAULT=${OPTIONS_DEFINE}
OPTIONS_SUB=	yes

post-patch:
	@${REINPLACE_CMD} -e 's|LIB_INSTALL_DIR}/pkgconfig"|CMAKE_INSTALL_PREFIX}/libdata/pkgconfig"|' ${WRKSRC}/CMakeLists.txt
	@${REINPLACE_CMD} -e 's|DOC_INSTALL_DIR}/examples"|CMAKE_INSTALL_PREFIX}/share/examples/${PORTNAME}"|' ${WRKSRC}/CMakeLists.txt

post-stage:
	@${RM} -rf ${STAGEDIR}${EXAMPLESDIR}/CMakeFiles

.include <bsd.port.mk>
