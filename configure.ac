AC_INIT([irssi-icb], [0.17], [marcus@nazgul.ch])
AC_PREREQ([2.61])

AC_CONFIG_HEADERS(config.h)

AM_INIT_AUTOMAKE([-Wall -Werror foreign nostdinc silent-rules])
AM_MAINTAINER_MODE

AM_PROG_AR
AC_PROG_CC
AC_PROG_CPP
AM_PROG_AR
AC_PROG_LIBTOOL
AC_STDC_HEADERS
AC_ARG_PROGRAM
AM_DISABLE_STATIC

AC_ARG_WITH([irssi],
            [AS_HELP_STRING([--with-irssi], [path to irssi directory])],
            [],
            [with_irssi=no])

AS_IF([test "x$with_irssi" = "xno"], [
      AS_IF([test -f ../irssi-config.h],
            [with_irssi=".."],
            AS_IF([test -f ../irssi/irssi-config.h],
                  [with_irssi="../.."],
                  AS_IF([test -f ../../irssi/irssi-config.h],
                        [with_irssi="../../irssi"],
                        AS_ERROR([Could not determine irssi directory])))) ])

# fix relative paths
IRSSI_INCLUDE=`cd $with_irssi; pwd`

AC_SUBST(IRSSI_INCLUDE)

AS_IF([test ! -f "$IRSSI_INCLUDE/irssi-config.h"],
      [AC_ERROR(Not irssi directory: $IRSSI_INCLUDE)]
)

PKG_CHECK_MODULES(GLIB, glib-2.0)

AC_CONFIG_FILES([
	Makefile
	src/Makefile
	src/core/Makefile
	src/fe-common/Makefile
])

AC_OUTPUT
