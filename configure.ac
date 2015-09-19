#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([Shairport], [1.1.1], [BUG-REPORT-ADDRESS])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_SRCDIR([src/shairport.c])
AC_CONFIG_HEADERS([config.h])
AM_INIT_AUTOMAKE(foreign)

# Checks for programs.
AC_PROG_CC
AC_PROG_LIBTOOL

# Checks for libraries.
AC_CHECK_LIB([pthread],[pthread_create])

# alsa
AC_ARG_WITH([alsa],
	[AS_HELP_STRING([--without-alsa],[do not use ALSA])],
	[],
	[with_alsa=yes])
AS_IF([test "x$with_alsa" != xno], [
	AC_CHECK_LIB([asound],[snd_pcm_close])
	AM_CONDITIONAL([WITH_ALSA], true)
	], [
	AM_CONDITIONAL([WITH_ALSA], false)
	])
# ao
AC_ARG_WITH([ao],
	[AS_HELP_STRING([--with-ao], [use ao as the audio backend [default=no]])],
	[],
	[with_ao=no])
AS_IF([test "x$with_ao" != xno],
	[
	AC_CHECK_LIB([ao],[ao_initialize])
	AM_CONDITIONAL([WITH_AO], true)
	], [
	AM_CONDITIONAL([WITH_AO], false)
	])
# PulseAudio
AC_ARG_WITH([pulse],
	[AS_HELP_STRING([--with-pulse], [use PulseAudio as the audio backend [default=no]])],
	[],
	[with_pulse=no])
AS_IF([test "x$with_pulse" != xno],
	[
	AC_CHECK_LIB([libpulse-simple],[pa_simple_new])
	AM_CONDITIONAL([WITH_PULSE], true)
	], [
	AM_CONDITIONAL([WITH_PULSE], false)
	])
# SNDIO
AC_ARG_WITH([sndio],
	[AS_HELP_STRING([--with-sndio], [use sndio as the audio backend [default=no]])],
	[],
	[with_sndio=no])
AS_IF([test "x$with_sndio" != xno],
	[
	AC_CHECK_LIB([libsndio],[sio_open])
	AM_CONDITIONAL([WITH_SNDIO], true)
	], [
	AM_CONDITIONAL([WITH_SNDIO], false)
	])

AC_CHECK_LIB([m],[pow])
AC_CHECK_LIB([crypto],[MD5_Init])

# Checks for header files.
AC_HEADER_STDC
AC_CHECK_HEADER([openssl/rsa.h], [], AC_MSG_ERROR([openssl/rsa.h not found.]))

# Checks for typedefs, structures, and compiler characteristics.
AC_C_INLINE
AC_TYPE_INT16_T
AC_TYPE_INT32_T
AC_TYPE_PID_T
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T
AC_CHECK_HEADER_STDBOOL
AC_TYPE_UINT16_T
AC_TYPE_UINT32_T
AC_TYPE_UINT8_T

# Checks for library functions.
AC_FUNC_FORK
AC_FUNC_MALLOC
AC_FUNC_REALLOC
AC_CHECK_FUNCS([dup2 gethostname gettimeofday inet_ntoa memchr memmove memset mkfifo pow select setenv socket stpcpy strcasecmp strchr strcspn strdup strstr strtol])


AC_CONFIG_FILES([Makefile
		 src/Makefile
		 src/lib/Makefile])
AC_OUTPUT
