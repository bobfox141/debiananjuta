# Plugin glade file
wizard_gladedir = $(anjuta_glade_dir)
dist_wizard_glade_DATA = anjuta-file-wizard.ui

# Plugin pixmaps
wizard_pixmapsdir = $(anjuta_image_dir)
dist_wizard_pixmaps_DATA = \
	anjuta-file-wizard-plugin.svg \
	anjuta-file-wizard-plugin-48.png

# Plugin Icon file
plugin_in_files = anjuta-file-wizard.plugin.in
%.plugin: %.plugin.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*po) ; $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache

wizard_plugindir = $(anjuta_plugin_dir)
dist_wizard_plugin_DATA = $(plugin_in_files:.plugin.in=.plugin)

plugindir = $(anjuta_plugin_dir)
plugin_LTLIBRARIES = libanjuta-file-wizard.la

AM_CPPFLAGS = \
	$(WARN_CFLAGS) \
	$(DEPRECATED_FLAGS) \
	$(LIBANJUTA_CFLAGS)

libanjuta_file_wizard_la_LDFLAGS = $(ANJUTA_PLUGIN_LDFLAGS)

libanjuta_file_wizard_la_LIBADD = \
	$(GIO_LIBS) \
	$(LIBANJUTA_LIBS)

libanjuta_file_wizard_la_SOURCES= \
	file.c \
	file.h \
	plugin.c \
	plugin.h

EXTRA_DIST = \
	$(plugin_in_files)

-include $(top_srcdir)/git.mk
