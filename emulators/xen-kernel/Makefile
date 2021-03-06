# $FreeBSD$

PORTNAME=	xen
PKGNAMESUFFIX=	-kernel
PORTVERSION=	4.5.0
CATEGORIES=	emulators
MASTER_SITES=	http://bits.xensource.com/oss-xen/release/${PORTVERSION}/

MAINTAINER=	bapt@FreeBSD.org
COMMENT=	Hypervisor using a microkernel design

LICENSE=	GPLv2

ONLY_FOR_ARCH=	amd64

USES=		gmake python:build
MAKE_ARGS=	HOSTCC="${CC}" CC="${CC}" PYTHON=${PYTHON_CMD} \
		NM="${NM}" LD="${LD}"
USE_GCC=	yes
NO_MTREE=	yes
PLIST_FILES=	/boot/xen \
		/boot/xen.4th
ALL_TARGET=	build
STRIP=		#
WRKSRC_SUBDIR=	xen
EXTRA_PATCHES=	${FILESDIR}/iommu_share_p2m_table.patch:-p2

.include <bsd.port.options.mk>

.if ${OPSYS} != FreeBSD
IGNORE=		Only supported on FreeBSD
.endif

.if ${OSVERSION} < 1100055
IGNORE=		Only supported on recent FreeBSD 11
.endif

do-install:
	${MKDIR} ${STAGEDIR}/boot
	${INSTALL_PROGRAM} ${WRKSRC}/xen ${STAGEDIR}/boot
	${INSTALL_DATA} ${FILESDIR}/xen.4th ${STAGEDIR}/boot

.include <bsd.port.mk>

#Filter out LDFLAGS
.undef LDFLAGS
RUN_DEPENDS:=	${RUN_DEPENDS:N*gcc*}
