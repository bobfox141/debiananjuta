SUBDIRS = images

# Plugin glade file
document_manager_gladedir = $(anjuta_glade_dir)
dist_document_manager_glade_DATA = anjuta-document-manager.ui

# Plugin UI file
document_manager_uidir = $(anjuta_ui_dir)
dist_document_manager_ui_DATA = anjuta-document-manager.xml

# Plugin file
plugin_in_files = anjuta-document-manager.plugin.in
%.plugin: %.plugin.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*po) ; $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache

document_manager_plugindir = $(anjuta_plugin_dir)
dist_document_manager_plugin_DATA = $(plugin_in_files:.plugin.in=.plugin)

plugindir = $(anjuta_plugin_dir)
plugin_LTLIBRARIES = libanjuta-document-manager.la

AM_CPPFLAGS = \
	$(WARN_CFLAGS) \
	$(DEPRECATED_FLAGS) \
	$(GDL_CFLAGS) \
	$(GIO_CFLAGS) \
	$(XML_CFLAGS) \
	$(LIBANJUTA_CFLAGS) \
	-DG_LOG_DOMAIN=\"libanjuta-document-manager\"

libanjuta_document_manager_la_LDFLAGS = $(ANJUTA_PLUGIN_LDFLAGS)

libanjuta_document_manager_la_LIBADD = \
	$(GDL_LIBS) \
	$(GIO_LIBS) \
	$(LIBANJUTA_LIBS)

libanjuta_document_manager_la_SOURCES= \
	plugin.c \
	plugin.h \
	anjuta-docman.c \
	anjuta-docman.h \
	action-callbacks.c\
	action-callbacks.h\
	file_history.c \
	file_history.h \
	search-box.h \
	search-box.c \
	anjuta-bookmarks.h \
	anjuta-bookmarks.c \
	search-files.c \
	search-files.h \
	search-file-command.c \
	search-file-command.h \
	search-filter-file-command.c \
	search-filter-file-command.h

gsettings_in_file = org.gnome.anjuta.document-manager.gschema.xml.in
gsettings_SCHEMAS = $(gsettings_in_file:.xml.in=.xml)
@INTLTOOL_XML_NOMERGE_RULE@
@GSETTINGS_RULES@

EXTRA_DIST = \
	$(plugin_in_files) \
        $(gsettings_in_file)

CLEANFILES = \
        $(gsettings_SCHEMAS)

-include $(top_srcdir)/git.mk
