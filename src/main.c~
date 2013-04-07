/* -*- Mode: C; indent-tabs-mode: t; c-basic-offset: 4; tab-width: 4 -*- */
/*
 * main.c
 * Copyright (C) nehal 2011 <total.sniper@yahoo.com>
 * 
 * round_cross_game is free software: you can redistribute it and/or modify it
 * under the terms of the GNU General Public License as published by the
 * Free Software Foundation, either version 3 of the License, or
 * (at your option) any later version.
 * 
 * round_cross_game is distributed in the hope that it will be useful, but
 * WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
 * See the GNU General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License along
 * with this program.  If not, see <http://www.gnu.org/licenses/>.
 */

#include <config.h>
#include <gtk/gtk.h>
#include <string.h>

#include <glib/gi18n.h>



/* For testing propose use the local (not installed) ui file */
/* #define UI_FILE PACKAGE_DATA_DIR"/round_cross_game/ui/round_cross_game.ui" */
#define UI_FILE "src/round_cross_game.ui"

/* Signal handlers */
/* Note: These may not be declared static because signal autoconnection
 * only works with non-static methods
 */

/* Called when the window is closed */

GtkWidget *btn1,*btn2,*btn3,*btn4,*btn5,*btn6,*btn7,*btn8,*btn9,*dialog;
GtkWidget *window1;
int i;
char *s1,*s2,*s3,*s4,*s5,*s6,*s7,*s8;

int check_hz()
{
	s1=g_strconcat(gtk_button_get_label (btn1),gtk_button_get_label (btn2),gtk_button_get_label (btn3),NULL);
	s2=g_strconcat(gtk_button_get_label (btn4),gtk_button_get_label (btn5),gtk_button_get_label (btn6),NULL);
	s3=g_strconcat(gtk_button_get_label (btn7),gtk_button_get_label (btn8),gtk_button_get_label (btn9),NULL);
	s4=g_strconcat(gtk_button_get_label (btn1),gtk_button_get_label (btn4),gtk_button_get_label (btn7),NULL);
	s5=g_strconcat(gtk_button_get_label (btn2),gtk_button_get_label (btn5),gtk_button_get_label (btn8),NULL);
	s6=g_strconcat(gtk_button_get_label (btn3),gtk_button_get_label (btn6),gtk_button_get_label (btn9),NULL);
	s7=g_strconcat(gtk_button_get_label (btn1),gtk_button_get_label (btn5),gtk_button_get_label (btn9),NULL);
	s8=g_strconcat(gtk_button_get_label (btn3),gtk_button_get_label (btn5),gtk_button_get_label (btn7),NULL);
	if(!g_strcmp0(s1,"XXX")||!g_strcmp0 (s2,"XXX")||!g_strcmp0 (s3,"XXX")||!g_strcmp0 (s4,"XXX")||!g_strcmp0 (s5,"XXX")||!g_strcmp0(s6,"XXX")||!g_strcmp0 (s7,"XXX")||!g_strcmp0 (s8,"XXX"))
		return (1);
	else if(!g_strcmp0(s1,"OOO")||!g_strcmp0 (s2,"OOO")||!g_strcmp0 (s3,"OOO")||!g_strcmp0 (s4,"OOO")||!g_strcmp0 (s5,"OOO")||!g_strcmp0(s6,"OOO")||!g_strcmp0 (s7,"OOO")||!g_strcmp0 (s8,"OOO"))
		return (1);	
	else
		return (0);
}
void
destroy (GtkWidget *widget, gpointer data)
{
	gtk_main_quit ();
}

void
on_click (GtkButton *button, gpointer user_data)
{
	gtk_button_set_label (button,"X");
	i=check_hz();
	if(i==1)
	{
		dialog = gtk_message_dialog_new (window1,
                                 GTK_DIALOG_DESTROY_WITH_PARENT,
                                 GTK_MESSAGE_INFO,
                                 GTK_BUTTONS_CLOSE,
                                 "Congrates u win!");
		g_signal_connect_swapped (dialog,
                             "response",
                             G_CALLBACK (gtk_widget_destroy),
                             dialog);
		gtk_widget_show_all (dialog);
	}
}

gboolean
on_scroll (GtkWidget *widget, GdkEvent *event, gpointer user_data)
{
	gtk_button_set_label (widget,"O");
	
	i=check_hz();
	if(i==1)
	{
		dialog = gtk_message_dialog_new (window1,
                                 GTK_DIALOG_DESTROY_WITH_PARENT,
                                 GTK_MESSAGE_INFO,
                                 GTK_BUTTONS_CLOSE,
                                 "Congrates u win!");
		g_signal_connect_swapped (dialog,
                             "response",
                             G_CALLBACK (gtk_widget_destroy),
                             dialog);
		gtk_widget_show_all (dialog);
	}
}

static GtkWidget*
create_window (void)
{
	GtkWidget *window;
	GtkBuilder *builder;
	GError* error = NULL;

	/* Load UI from file */
	builder = gtk_builder_new ();
	if (!gtk_builder_add_from_file (builder, UI_FILE, &error))
	{
		g_warning ("Couldn't load builder file: %s", error->message);
		g_error_free (error);
	}

	/* Auto-connect signal handlers */
	gtk_builder_connect_signals (builder, NULL);
	btn1 = GTK_WIDGET (gtk_builder_get_object (builder, "button1"));
	btn2 = GTK_WIDGET (gtk_builder_get_object (builder, "button2"));
	btn3 = GTK_WIDGET (gtk_builder_get_object (builder, "button3"));
	btn4 = GTK_WIDGET (gtk_builder_get_object (builder, "button4"));
	btn5 = GTK_WIDGET (gtk_builder_get_object (builder, "button5"));
	btn6 = GTK_WIDGET (gtk_builder_get_object (builder, "button6"));
	btn7 = GTK_WIDGET (gtk_builder_get_object (builder, "button7"));
	btn8 = GTK_WIDGET (gtk_builder_get_object (builder, "button8"));
	btn9 = GTK_WIDGET (gtk_builder_get_object (builder, "button9"));
	
	/* Get the window object from the ui file */
	window1 = GTK_WIDGET (gtk_builder_get_object (builder, "window"));
	window = GTK_WIDGET (gtk_builder_get_object (builder, "window"));
	g_object_unref (builder);
	
	return window;
}


int
main (int argc, char *argv[])
{
 	GtkWidget *window;


#ifdef ENABLE_NLS
	bindtextdomain (GETTEXT_PACKAGE, PACKAGE_LOCALE_DIR);
	bind_textdomain_codeset (GETTEXT_PACKAGE, "UTF-8");
	textdomain (GETTEXT_PACKAGE);
#endif

	
	gtk_init (&argc, &argv);

	window = create_window ();
	gtk_widget_show (window);

	gtk_main ();
	return 0;
}
