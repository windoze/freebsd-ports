# Created by: Maxim Sobolev <sobomax@FreeBSD.org>
# $FreeBSD$

PORTNAME=	sdl_image
PORTVERSION=	1.2.12
PORTREVISION=	8
CATEGORIES=	graphics
MASTER_SITES=	http://www.libsdl.org/projects/SDL_image/release/
DISTNAME=	SDL_image-${PORTVERSION}

MAINTAINER=	mva@FreeBSD.org
COMMENT=	Simple library to load images of various formats as SDL surfaces

LICENSE=	LGPL21

USES=		gmake libtool pkgconfig pathfix
USE_SDL=	sdl
GNU_CONFIGURE=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LIBS+=		-L${LOCALBASE}/lib -lm
USE_LDCONFIG=	yes

OPTIONS_DEFINE=	JPEG PNG TIFF WEBP
OPTIONS_DEFAULT=JPEG PNG TIFF WEBP

JPEG_LIB_DEPENDS=	libjpeg.so:${PORTSDIR}/graphics/jpeg
JPEG_CONFIGURE_ENABLE=	jpg
PNG_LIB_DEPENDS=	libpng.so:${PORTSDIR}/graphics/png
PNG_CONFIGURE_ENABLE=	png
TIFF_LIB_DEPENDS=	libtiff.so:${PORTSDIR}/graphics/tiff
TIFF_CONFIGURE_ENABLE=	tif
WEBP_LIB_DEPENDS=	libwebp.so:${PORTSDIR}/graphics/webp
WEBP_CONFIGURE_ENABLE=	webp

post-install:
	${INSTALL_PROGRAM} ${WRKSRC}/.libs/showimage ${STAGEDIR}${PREFIX}/bin

.include <bsd.port.mk>
