# Created by: znerd@FreeBSD.org
# $FreeBSD$

PORTNAME=	xalan-j
PORTVERSION=	2.7.1
CATEGORIES=	textproc java
MASTER_SITES=	${MASTER_SITE_APACHE_XML}
MASTER_SITE_SUBDIR=	${PORTNAME}/binaries
DISTNAME=	${PORTNAME}_${PORTVERSION:S/./_/g}-bin

MAINTAINER=	ale@FreeBSD.org
COMMENT=	Apache XSLT processor for transforming XML documents

LICENSE=	APACHE20

RUN_DEPENDS=	${JAVALIBDIR}/xml-apis.jar:${PORTSDIR}/textproc/xerces-j

OPTIONS_DEFINE=	DOCS EXAMPLES

USES=		cpe zip
CPE_PRODUCT=	xalan-java
CPE_VENDOR=	apache
USE_JAVA=	yes
JAVA_VERSION=	1.6+
NO_BUILD=	yes

WRKSRC=		${WRKDIR}/${PORTNAME}_${PORTVERSION:S/./_/g}

PORTDOCS=	*
PORTEXAMPLES=	*

JARFILES=	xalan.jar serializer.jar

PLIST_FILES=	${JARFILES:S|^|%%JAVAJARDIR%%/|} bin/xalan-j

SUB_FILES=	xalan-j.sh

.include <bsd.port.options.mk>

do-install:
	@${ECHO_MSG} -n ">> Installing JAR files in ${JAVAJARDIR}..."
.for jarfile in ${JARFILES}
	@${INSTALL_DATA} ${WRKSRC}/${jarfile} ${STAGEDIR}${JAVAJARDIR}/
	@${ECHO_MSG} -n " ${jarfile}"
.endfor
	@${ECHO_MSG} " [ DONE ]"
.if ${PORT_OPTIONS:MDOCS}
	@${ECHO_MSG} -n ">> Installing documentation in ${DOCSDIR}..."
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	@(cd ${WRKSRC}/docs && ${COPYTREE_SHARE} \* ${STAGEDIR}${DOCSDIR})
	@${ECHO_MSG} " [ DONE ]"
.endif
.if ${PORT_OPTIONS:MEXAMPLES}
	@${ECHO_MSG} -n ">> Installing samples in ${EXAMPLESDIR}..."
	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	@(cd ${WRKSRC}/samples && ${COPYTREE_SHARE} \* ${STAGEDIR}${EXAMPLESDIR})
	@${ECHO_MSG} " [ DONE ]"
.endif
	@${ECHO_MSG} -n ">> Installing script in ${PREFIX}/bin/..."
	@${INSTALL_SCRIPT} ${WRKDIR}/xalan-j.sh ${STAGEDIR}${PREFIX}/bin/xalan-j
	@${ECHO_MSG} " [ DONE ]"

.include <bsd.port.mk>
