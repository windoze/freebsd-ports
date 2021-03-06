# Created by: GreenDog <fiziologus@gmail.com>
# $FreeBSD$

PORTNAME=	unknown-horizons
PORTVERSION=	2013.3
PORTREVISION=	1
CATEGORIES=	games
#MASTER_SITES=	SF/unknownhorizons/Unknown%20Horizons/${PORTVERSION}/
MASTER_SITES=	GHL

MAINTAINER=	fiziologus@gmail.com
COMMENT=	Real time simulation game

BUILD_DEPENDS=	${LOCALBASE}/share/xsl/docbook/manpages/docbook.xsl:${PORTSDIR}/textproc/docbook-xsl \
		${LOCALBASE}/bin/xsltproc:${PORTSDIR}/textproc/libxslt
RUN_DEPENDS=	${PYTHON_SITELIBDIR}/fife/__init__.py:${PORTSDIR}/games/py-fife \
		${PYTHON_PKGNAMEPREFIX}sqlite3>0:${PORTSDIR}/databases/py-sqlite3 \
		${PYTHON_SITELIBDIR}/yaml/__init__.py:${PORTSDIR}/devel/py-yaml \
		${PYTHON_PKGNAMEPREFIX}gdbm>0:${PORTSDIR}/databases/py-gdbm

ONLY_FOR_ARCHS=	i386 amd64

USE_GITHUB=	yes
GH_ACCOUNT=	${PORTNAME}
GH_COMMIT=	ac7af43

USE_GNOME=	intltool
USES=		gettext-tools python:2 tar:xz
USE_PYTHON=	distutils
PYDISTUTILS_PKGNAME=	UnknownHorizons

.include <bsd.port.pre.mk>

.if ${ARCH} == i386
ENET_DIR=	x86
PLIST_SUB+=	X86_ONLY=""
.else
PLIST_SUB+=	X86_ONLY="@comment "
.endif

.if ${ARCH} == amd64
ENET_DIR=	x64
PLIST_SUB+=	X64_ONLY=""
.else
PLIST_SUB+=	X64_ONLY="@comment "
.endif

post-patch:
	${REINPLACE_CMD} -e "s|http://docbook.sourceforge.net/release/xsl/current|${LOCALBASE}/share/xsl/docbook|" \
		-e "s|share/man/man6|man/man6|" ${WRKSRC}/setup.py

# Install multiplayer lib (enet+pyenet)
post-install:
	${MKDIR} ${STAGEDIR}${PYTHON_SITELIBDIR}/horizons/network/libs
	${MKDIR} ${STAGEDIR}${PYTHON_SITELIBDIR}/horizons/network/libs/freebsd-${ENET_DIR}
	${INSTALL} ${WRKSRC}/horizons/network/libs/freebsd-${ENET_DIR}/enet.so \
		${STAGEDIR}${PYTHON_SITELIBDIR}/horizons/network/libs/freebsd-${ENET_DIR}/enet.so
# (rene) prune unwanted files to pass 'make check-plist'
	${RM} -r ${STAGEDIR}${PYTHON_SITELIBDIR}/UnknownHorizons-_unknown_-py${PYTHON_VER}.egg-info

.include <bsd.port.post.mk>
