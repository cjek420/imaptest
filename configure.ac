AC_PREREQ([2.69])
m4_define([imaptest_VERSION],
    m4_esyscmd_s([build-aux/git-version-gen]))



AC_INIT([dovecot-imaptest], [m4_defn([imaptest_VERSION])], [dovecot@dovecot.org])
AC_CONFIG_SRCDIR([src])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_AUX_DIR([build-aux])

AC_CONFIG_HEADERS([imaptest-config.h])
AM_INIT_AUTOMAKE
AM_SILENT_RULES([yes])

AM_MAINTAINER_MODE

AC_PROG_CC
AC_PROG_CPP
LT_INIT

DC_DOVECOT
CFLAGS="$CFLAGS $EXTRA_CFLAGS"
LIBS="$DOVECOT_LIBS"
BINARY_CFLAGS="$PIE_CFLAGS"
BINARY_LDFLAGS="$PIE_LDFLAGS $RELRO_LDFLAGS"
AC_SUBST(BINARY_CFLAGS)
AC_SUBST(BINARY_LDFLAGS)

AM_CONDITIONAL(STATIC_OPENSSL, test "$enable_shared" != "yes")

AS_IF([test "$AR_FLAGS" = "cru"], [AR_FLAGS="cr"], [])
AC_SUBST([AR_FLAGS])

AC_CONFIG_FILES([
Makefile
src/Makefile
build-aux/run-test.sh
stamp.h])

AC_OUTPUT
