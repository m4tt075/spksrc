PKG_NAME = File-Rename
PKG_VERS = 1.10
PKG_EXT = tar.gz
PKG_DIST_NAME = $(PKG_NAME)-$(PKG_VERS).$(PKG_EXT)
PKG_DIST_SITE = http://www.cpan.org/modules/by-module/File/RMBARKER
PKG_DIR = $(PKG_NAME)-$(PKG_VERS)

DEPENDS =

HOMEPAGE = https://metacpan.org/release/File-Rename
COMMENT  = Renames the filenames supplied according to the rule specified as the first argument, using Perl expressions.
LICENSE  = GPL

CONFIGURE_TARGET = rename_configure_target

include ../../mk/spksrc.cross-cc.mk

.PHONY: rename_configure_target
rename_configure_target:
	$(RUN) perl Makefile.PL PREFIX=$(STAGING_INSTALL_PREFIX) INSTALLDIRS=vendor
