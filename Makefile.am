## Process this file with automake to produce Makefile.in
## Created by Anjuta

SUBDIRS = src po

round_cross_gamedocdir = ${prefix}/doc/round_cross_game
round_cross_gamedoc_DATA = \
	README\
	COPYING\
	AUTHORS\
	ChangeLog\
	INSTALL\
	NEWS


INTLTOOL_FILES = intltool-extract.in \
	intltool-merge.in \
	intltool-update.in

EXTRA_DIST = $(round_cross_gamedoc_DATA) \
	$(INTLTOOL_FILES)

DISTCLEANFILES = intltool-extract \
	intltool-merge \
	intltool-update \
	po/.intltool-merge-cache


# Remove doc directory on uninstall
uninstall-local:
	-rm -r $(round_cross_gamedocdir)
