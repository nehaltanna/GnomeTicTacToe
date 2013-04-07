## Process this file with automake to produce Makefile.in

## Created by Anjuta


uidir = $(datadir)/round_cross_game/ui
ui_DATA = round_cross_game.ui


AM_CPPFLAGS = \
	-DPACKAGE_LOCALE_DIR=\""$(prefix)/$(DATADIRNAME)/locale"\" \
	-DPACKAGE_SRC_DIR=\""$(srcdir)"\" \
	-DPACKAGE_DATA_DIR=\""$(datadir)"\" \
	$(ROUND_CROSS_GAME_CFLAGS)

AM_CFLAGS =\
	 -Wall\
	 -g

bin_PROGRAMS = round_cross_game

round_cross_game_SOURCES = \
	main.c

round_cross_game_LDFLAGS = \
	-Wl,--export-dynamic

round_cross_game_LDADD = $(ROUND_CROSS_GAME_LIBS)


EXTRA_DIST = $(ui_DATA)

# Remove ui directory on uninstall
uninstall-local:
	-rm -r $(uidir)
	-rm -r $(datadir)/round_cross_game
