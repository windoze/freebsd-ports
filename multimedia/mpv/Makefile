# Created by: Grzegorz Blach <gblach@FreeBSD.org>
# $FreeBSD$

PORTNAME=	mpv
PORTVERSION=	0.8.3
PORTEPOCH=	1
CATEGORIES=	multimedia audio
MASTER_SITES=	GHL:0 http://ftp.waf.io/pub/release/:1 \
		http://www.freehackers.org/~tnagy/release/:1
DISTFILES=	${DISTNAME}${EXTRACT_SUFX}:0 waf-${WAF_VERSION}:1
EXTRACT_ONLY=	${DISTNAME}${EXTRACT_SUFX}

MAINTAINER=	chris@bsdjunk.com
COMMENT=	Free and open-source general-purpose video player

LICENSE=	GPLv2

LIB_DEPENDS=	libavcodec.so:${PORTSDIR}/multimedia/ffmpeg \
		libass.so:${PORTSDIR}/multimedia/libass \
		libdvdread.so:${PORTSDIR}/multimedia/libdvdread \
		libdvdnav.so:${PORTSDIR}/multimedia/libdvdnav
BUILD_DEPENDS=	rst2man:${PORTSDIR}/textproc/py-docutils

USE_GITHUB=	yes
GH_ACCOUNT=	mpv-player
GH_TAGNAME=	v${PORTVERSION}
GH_COMMIT=	ff4c1cc

WAF_VERSION=	1.8.7

USES=		compiler:c11 desktop-file-utils iconv pkgconfig python:build waf
USE_XORG=	x11 xv xxf86vm
USE_LDCONFIG=	yes
INSTALLS_ICONS=	yes

CPPFLAGS+=	-I.. -I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

CONFIGURE_ARGS=	--prefix=${PREFIX} \
		--docdir=${EXAMPLESDIR} \
		--mandir=${MANPREFIX}/man \
		--disable-debug-build \
		--disable-optimize \
		--enable-libmpv-shared \
		--disable-mpg123 \
		--disable-alsa \
		--disable-pdf

OPTIONS_DEFINE=		BS2B DOCS ENCA LADSPA LCMS2 LIBGUESS LIRC LUAJIT ZSH
OPTIONS_GROUP=		IN VO AO
OPTIONS_GROUP_IN=	CDIO LIBBLURAY V4L YTDL SMB
OPTIONS_GROUP_VO=	CACA OPENGL VAAPI VDPAU XINERAMA
OPTIONS_GROUP_AO=	JACK PULSEAUDIO
OPTIONS_SUB=		yes

BS2B_DESC=	Enable Bauer Stereophonic-to-Binaural DSP support
ENCA_DESC=	Enable encoding detection support
LIBGUESS_DESC=	Enable high-speed character set detection support
LUAJIT_DESC=	Use LuaJIT instead of Lua
YTDL_DESC=	Install youtube-dl
IN_DESC=	Input
VO_DESC=	Video Output
AO_DESC=	Audio Output

BS2B_LIB_DEPENDS=		libbs2b.so:${PORTSDIR}/audio/libbs2b
BS2B_CONFIGURE_ENABLE=		libbs2b

ENCA_LIB_DEPENDS=		libenca.so:${PORTSDIR}/converters/enca
ENCA_CONFIGURE_ENABLE=		enca

LADSPA_LIB_DEPENDS=		ladspa/amp.so:${PORTSDIR}/audio/ladspa
LADSPA_CONFIGURE_ENABLE=	ladspa

LCMS2_LIB_DEPENDS=		liblcms2.so:${PORTSDIR}/graphics/lcms2
LCMS2_CONFIGURE_ENABLE=		lcms2

LIBGUESS_LIB_DEPENDS=		libguess.so:${PORTSDIR}/textproc/libguess
LIBGUESS_CONFIGURE_ENABLE=	libguess

LIRC_LIB_DEPENDS=		liblirc_client.so:${PORTSDIR}/comms/lirc
LIRC_CONFIGURE_ENABLE=		lirc

LUAJIT_LIB_DEPENDS=		libluajit-5.1.so:${PORTSDIR}/lang/luajit
LUAJIT_USES_OFF=		lua
LUAJIT_CONFIGURE_ON=		--lua=luajit
LUAJIT_CONFIGURE_OFF=		--lua=${LUA_VER_STR}fbsd

ZSH_USES=			perl5
ZSH_USE=			PERL5=build
ZSH_CONFIGURE_ENABLE=		zsh-comp

CDIO_LIB_DEPENDS=		libcdio_paranoia.so:${PORTSDIR}/sysutils/libcdio-paranoia
CDIO_CONFIGURE_ENABLE=		cdda

LIBBLURAY_LIB_DEPENDS=		libbluray.so:${PORTSDIR}/multimedia/libbluray
LIBBLURAY_CONFIGURE_ENABLE=	libbluray

V4L_BUILD_DEPENDS=		${LOCALBASE}/include/linux/videodev2.h:${PORTSDIR}/multimedia/v4l_compat
V4L_LIB_DEPENDS=		libv4l2.so:${PORTSDIR}/multimedia/libv4l
V4L_CONFIGURE_ENABLE=		tv-v4l2

YTDL_RUN_DEPENDS=		youtube-dl:${PORTSDIR}/www/youtube_dl

SMB_LIB_DEPENDS=		libsmbclient.so:${PORTSDIR}/net/samba-libsmbclient
SMB_CONFIGURE_ENABLE=		libsmbclient

CACA_LIB_DEPENDS=		libcaca.so:${PORTSDIR}/graphics/libcaca
CACA_CONFIGURE_ENABLE=		caca

OPENGL_USE=			XORG=glproto
OPENGL_LIB_DEPENDS=		libGL.so:${PORTSDIR}/graphics/libGL
OPENGL_CONFIGURE_ENABLE=	gl

VAAPI_LIB_DEPENDS=		libva.so:${PORTSDIR}/multimedia/libva
VAAPI_CONFIGURE_ENABLE=		vaapi

VDPAU_LIB_DEPENDS=		libvdpau.so:${PORTSDIR}/multimedia/libvdpau
VDPAU_CONFIGURE_ENABLE=		vdpau

XINERAMA_USE=			XORG=xinerama,xineramaproto
XINERAMA_CONFIGURE_ENABLE=	xinerama

JACK_LIB_DEPENDS=		libjack.so:${PORTSDIR}/audio/jack
JACK_CONFIGURE_ENABLE=		jack

PULSEAUDIO_LIB_DEPENDS=		libpulse.so:${PORTSDIR}/audio/pulseaudio
PULSEAUDIO_CONFIGURE_ENABLE=	pulse

post-extract:
	${CP} ${DISTDIR}/waf-${WAF_VERSION} ${WRKSRC}/waf
	@${CHMOD} +x ${WRKSRC}/waf

post-patch:
	@${REINPLACE_CMD} -e 's|/pkgconfig/mpv.pc|data/pkgconfig/mpv.pc|g' \
		${WRKSRC}/wscript_build.py
	@${FIND} ${WRKSRC}/DOCS/man -name '*.rst' | ${XARGS} ${REINPLACE_CMD} \
		-e 's|/usr/local|${PREFIX}|g'

post-stage:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/mpv
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/lib/libmpv.so

.include <bsd.port.mk>
