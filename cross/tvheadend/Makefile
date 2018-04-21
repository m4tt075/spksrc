PKG_NAME = tvheadend
PKG_VERS = 4.3.1789
PKG_EXT = tar.gz
PKG_DOWNLOAD_METHOD = git
PKG_GIT_HASH = 6bfeca6c03
PKG_DIST_NAME = tvheadend.git
PKG_DIST_SITE = https://github.com/tvheadend
PKG_DIST_FILE = $(PKG_NAME)-git$(PKG_GIT_HASH).$(PKG_EXT)
PKG_DIR = $(PKG_NAME)-git*

DEPENDS = cross/openssl cross/libhdhomerun cross/uriparser cross/libdvbcsa cross/pcre2

HOMEPAGE = https://www.lonelycoder.com/tvheadend/
COMMENT  = Tvheadend is a TV streaming server and recorder for Linux, FreeBSD and Android supporting DVB-S, DVB-S2, DVB-C, DVB-T, ATSC, ISDB-T, IPTV, SAT IP and HDHomeRun as input sources. Tvheadend offers HTTP, HTSP and SAT IP streaming.
LICENSE  = GPL v3

GNU_CONFIGURE = 1

CONFIGURE_ARGS = --enable-imagecache --disable-avahi --enable-dvbcsa --enable-bundle --release
CONFIGURE_ARGS += --disable-hdhomerun_static --enable-hdhomerun_client
CONFIGURE_ARGS += --disable-ffmpeg_static --enable-libav
CONFIGURE_ARGS += --disable-libfdkaac_static --disable-libopus_static --disable-libtheora --disable-libtheora_static
CONFIGURE_ARGS += --disable-libvorbis_static --disable-libvpx_static --disable-libx264_static --disable-libx265_static

POST_PATCH_TARGET = post_patch_target_tvheadend

ifeq ($(wildcard $(FFMPEG_DIR)),)
DEPENDS += cross/ffmpeg
endif

include ../../mk/spksrc.cross-cc.mk

.PHONY: post_patch_target_tvheadend

post_patch_target_tvheadend:
	@if [ "$(ARCH)" = "ppc853x" ] || [ "$(ARCH)" = "qoriq" ]; then \
		cat $(PWD)/patches/ppc/isoc9x.patch | ($(RUN) patch -p0) ;\
		cat $(PWD)/patches/ppc/hts_strtab-undo-inlining-of-functions.patch | ($(RUN) patch -p0) ;\
	fi;
