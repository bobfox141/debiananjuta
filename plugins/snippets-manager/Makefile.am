# Plugin glade file
# Snippet Browser and Snippet Editor UI files here
snippets_manager_gladedir = $(anjuta_glade_dir)
dist_snippets_manager_glade_DATA = snippets-manager-preferences.ui \
                              snippets-browser.ui \
                              snippets-editor.ui \
                              snippets-export-dialog.ui


# Plugin default data
# The default installed plugins here.
default_snippetsdir = $(anjuta_data_dir)
dist_default_snippets_DATA = \
	snippets.anjuta-snippets \
	snippets-global-variables.xml
                        

snippets_manager_pixmapsdir = $(anjuta_image_dir)
dist_snippets_manager_pixmaps_DATA = \
	anjuta-snippets-manager.png

# Plugin menu UI file
snippets_manager_uidir = $(anjuta_ui_dir)
dist_snippets_manager_ui_DATA = \
	snippets-manager-ui.xml

plugin_in_files = anjuta-snippets-manager.plugin.in
%.plugin: %.plugin.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*po) ; $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache

snippets_manager_plugindir = $(anjuta_plugin_dir)
dist_snippets_manager_plugin_DATA = $(plugin_in_files:.plugin.in=.plugin)

AM_CPPFLAGS= \
	$(WARN_CFLAGS) \
	$(DEPRECATED_FLAGS) \
	$(XML_CFLAGS) \
	$(LIBANJUTA_CFLAGS) \
	$(XML_CFLAGS) \
	-DG_LOG_DOMAIN=\"libanjuta-snippets-manager\"

plugindir = $(anjuta_plugin_dir)
plugin_LTLIBRARIES = libanjuta-snippets-manager.la

libanjuta_snippets_manager_la_LDFLAGS = $(ANJUTA_PLUGIN_LDFLAGS)

libanjuta_snippets_manager_la_LIBADD = \
	$(GIO_LIBS) \
	$(LIBANJUTA_LIBS) \
	$(XML_LIBS)

libanjuta_snippets_manager_la_SOURCES = \
	snippet.c\
	snippet.h\
	snippets-group.c\
	snippets-group.h\
	snippets-db.c\
	snippets-db.h\
	snippets-xml-parser.c\
	snippets-xml-parser.h\
	snippets-browser.c\
	snippets-browser.h\
	snippets-editor.c\
	snippets-editor.h\
	snippets-interaction-interpreter.c\
	snippets-interaction-interpreter.h\
	plugin.c\
	plugin.h\
	snippet-variables-store.c\
	snippet-variables-store.h\
	snippets-provider.c\
	snippets-provider.h\
	snippets-import-export.c\
	snippets-import-export.h

gsettings_in_file = org.gnome.anjuta.snippets.gschema.xml.in
gsettings_SCHEMAS = $(gsettings_in_file:.xml.in=.xml)
@INTLTOOL_XML_NOMERGE_RULE@
@GSETTINGS_RULES@

EXTRA_DIST = \
	$(plugin_in_files) \
        $(gsettings_in_file)

CLEANFILES = \
        $(gsettings_SCHEMAS)

-include $(top_srcdir)/git.mk
