# Plugin glade file
wizard_gladedir = $(anjuta_glade_dir)
dist_wizard_glade_DATA = project-import.ui

# Plugin pixmaps
wizard_pixmapsdir = $(anjuta_image_dir)
dist_wizard_pixmaps_DATA = \
	anjuta-project-import-plugin.svg \
	anjuta-project-import-plugin-48.png

# Plugin Icon file
plugin_in_files = anjuta-project-import.plugin.in
%.plugin: %.plugin.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*po) ; $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache

wizard_plugindir = $(anjuta_plugin_dir)
dist_wizard_plugin_DATA = $(plugin_in_files:.plugin.in=.plugin)

plugindir = $(anjuta_plugin_dir)
plugin_LTLIBRARIES = libanjuta-project-import.la

AM_CPPFLAGS = \
	$(WARN_CFLAGS) \
	$(DEPRECATED_FLAGS) \
	$(PLUGIN_GNOMEBUILD_CFLAGS) \
	$(LIBANJUTA_CFLAGS)

libanjuta_project_import_la_LDFLAGS = $(ANJUTA_PLUGIN_LDFLAGS)

libanjuta_project_import_la_LIBADD = \
	$(PLUGIN_GNOMEBUILD_LIBS) \
	$(GIO_LIBS) \
	$(LIBANJUTA_LIBS)

libanjuta_project_import_la_SOURCES= \
	plugin.c \
	plugin.h \
	project-import-dialog.h \
	project-import-dialog.c

EXTRA_DIST = \
	$(plugin_in_files)

-include $(top_srcdir)/git.mk
