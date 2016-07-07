##########################################################################
##									##
## Script ID: ./configure.ac						##
## Author: Mark Grant							##
##									##
## Purpose:								##
##	AutoConf script file to configure kernel-utils project.		##
##									##
## configure cmd line syntax:-						##
##		./configure						##
##									##
##########################################################################

##########################################################################
##									##
## Changelog								##
##									##
## Date		Author	Version	Description				##
##									##
## 07/07/2016	MG	1.0.1	First release.				##
##									##
##########################################################################

AC_REVISION([$Revision: 1.0.1 $])

AC_PREREQ([2.65])


#########################
##
## The following two macros use git to provide versioning information.
## If git is not initialised or no commit has been made, then 'Pre-Release'
## will be used.
## If no Tag has been created then just a commit identifier will be used.
## If a tag has been created then the most recent tag, plus number of commits
## since the tag, plus a commit identifier will be used.
##
#########################

# AC_INIT cannot be split over multiple lines.
AC_INIT([Kernel Utilities], m4_esyscmd([git describe --always 1>/dev/null 2>/dev/null && git describe --always | tr -d '\n' || echo 'Pre-Release' | tr -d '\n']), [m.grant.prg@gmail.com], [kernel-utils])

AC_SUBST([pkgversion], [m4_esyscmd([git describe --always 1>/dev/null \
				2>/dev/null \
				&& git describe --always | tr -d '\n' \
				|| echo 'Pre-Release' | tr -d '\n'])])


#########################
##
## Now set up a sed sequence to substitute bookmarks in script files with either
## standard GNU Directory Variables, or with programmer-defined variables set up
## using an AC_SUBST macro above. This sed sequence will be invoked at
## programmer discretion at sub-directory Makefile.am level.
## ------------------------------------
##
## prefix	/usr/local (typically)
##	exec_prefix	${prefix}
##		bindir	${exec_prefix}/bin	user executables
##		sbindir	${exec_prefix}/sbin	system admin executables
##		libexecdir	${exec_prefix}/libexec	program executables
##		libdir	${exec_prefix}/lib	object code libraries
##	sysconfdir	 ${prefix}/etc	read-only single-machine data
##	sharedstatedir	${prefix}/com	modifiable architecture-independent data
##	localstatedir	${prefix}/var	modifiable single-machine data
##	runstatedir	${localstatedir}/run
##	includedir	${prefix}/include	C header files
##	oldincludedir	$usr/include	C header files
##	datarootdir	${prefix}/share	read-only arch.-independent data root
##		localedir	${datarootdir}/locale	locale-dependent data
##		datadir	${datarootdir}	read-only architecture-independent data
##		mandir	${datarootdir}/man	man documentation
##		infodir	${datarootdir}/info	info documentation
##		docdir	${datarootdir}/doc/${PACKAGE}	documentation root
##			htmldir	${docdir}	html documentation
##			dvidir	${docdir}	dvi documentation
##			pdfdir	${docdir}	pdf documentation
##			psdir	${docdir}	ps documentation
##		lispdir	${datarootdir}/emacs/site-lisp
##	pkgdatadir	${datarootdir}/${PACKAGE}
##	pkgincludedir	${includedir}/${PACKAGE}
##	pkglibdir	${libdir}/${PACKAGE}
##	pkglibexecdir	${libexecdir}/${PACKAGE}
##
#########################

AC_SUBST([edit], ["sed \
		-e 's|@bindir[@]|\$(bindir)|g' \
		-e 's|@pkgdatadir[@]|\$(pkgdatadir)|g' \
		-e 's|@pkglibexecdir[@]|\$(pkglibexecdir)|g' \
		-e 's|@sysconfdir[@]|\$(sysconfdir)|g' \
		-e 's|@datadir[@]|\$(datadir)|g' \
		-e 's|@prefix[@]|\$(prefix)|g' \
		-e 's|@pkgversion[@]|\$(pkgversion)|g' \
		-e 's|@rootconfloc[@]|\$(rootconfloc)|g' \
		-e 's|@desktoploc[@]|\$(desktoploc)|g' \
		-e 's|@localstatedir[@]|\$(localstatedir)|g'"])


# Passes the options to all am files. Puts objects in the subdirectory
# containing the source.
AM_INIT_AUTOMAKE([-Wall -Werror subdir-objects])

#########################
##
## Checks for programs.
## install, mkdir and gawk are checked by AM_INIT_AUTOMAKE.
## grep, egrep and ranlib are also automatically checked.
## Particular and generic program checks follow:
##
#########################

AC_MSG_NOTICE([checking for particular programs required by this application])
AC_PROG_SED

AC_MSG_NOTICE([checking for generic programs required by this application])
AC_CHECK_PROG([TAR], [tar], [yes], [no])
if test "x$TAR" = "xno" ; then
	AC_MSG_ERROR([tar not found])
fi

AC_CHECK_PROG([GETOPT], [getopt], [yes], [no])
if test "x$GETOPT" = "xno" ; then
	AC_MSG_ERROR([getopt not found])
fi

AC_CHECK_PROG([BASH], [bash], [yes], [no])
if test "x$BASH" = "xno" ; then
   	AC_MSG_ERROR([bash not found])
fi

AC_CHECK_PROG([TXT2MAN], [txt2man], [yes], [no])
if test "x$TXT2MAN" = "xno" ; then
   	AC_MSG_ERROR([txt2man not found])
fi

AC_CHECK_PROG([TXT2MANWRAP], [txt2manwrap], [yes], [no])
if test "x$TXT2MANWRAP" = "xno" ; then
   	AC_MSG_ERROR([txt2manwrap not found])
fi


# Project Makefiles to create.
AC_CONFIG_FILES([Makefile
		source/man/man1/Makefile
		source/progs/bash/Makefile])

AC_OUTPUT
