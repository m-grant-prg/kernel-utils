#########################################################################
#									#
# Script ID: ./Makefile.am						#
# Author: Copyright (C) 2016-2019, 2021  Mark Grant			#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0-only					#
#									#
# Purpose:								#
#	AutoMake script file to generate kernel-utils project from	#
# source.								#
#									#
#########################################################################

#########################################################################
#									#
# Changelog								#
#									#
# Date		Author	Version	Description				#
#									#
# 07/07/2016	MG	1.0.1	First release.				#
# 08/12/2017	MG	1.0.2	Add SPDX license tags to source files.	#
# 10/02/2018	MG	1.0.3	Shorten directory names to reduce	#
#				overall path length.			#
#				Add macro directory.			#
# 10/04/2018	MG	1.0.4	Add srctarball target to build a source	#
#				tarball in the build directory. Uses	#
#				git archive to archive HEAD.		#
# 10/06/2018	MG	1.0.5	Add info messages to srctarball target.	#
# 31/10/2018	MG	1.0.6	Change srctarball target to build with	#
#				src between package name and version in	#
#				filename.				#
# 10/10/2019	MG	1.0.7	Make source tarball the same as from	#
#				GitHub.					#
#				Add install of standard GNU files like	#
#				AUTHORS, etc.				#
#				Remove unnecessary shebang.		#
#				To enable make distcheck to work, any	#
#				hard-coded paths requiring permissions	#
#				such as /etc or fixed locations such as	#
#				/usr/share/java must be accommodated,	#
#				so set the configure flags to be used	#
#				by make distcheck.			#
# 08/11/2021	MG	1.0.8	Add misc directory to DIST.		#
# 24/11/2021	MG	1.0.9	Tighten SPDX tag.			#
#									#
#########################################################################


ACLOCAL_AMFLAGS = -I m4


AM_DISTCHECK_CONFIGURE_FLAGS =


SUBDIRS = src/man/1
SUBDIRS += src/prg/bash


doc_DATA = AUTHORS ChangeLog COPYING NEWS README


EXTRA_DIST = $(srcdir)/AUTHORS $(srcdir)/ChangeLog $(srcdir)/COPYING \
		$(srcdir)/NEWS $(srcdir)/README $(srcdir)/misc


srctarball:
	@cwd="$${PWD}" && \
	targ="$${cwd}/@PACKAGE_TARNAME@-@PACKAGE_VERSION@.tar.gz" && \
	cd @srcdir@ && \
	echo "making srctarball from @srcdir@" && \
	echo "GA	$${targ}" && \
	git archive --format=tar.gz \
		--prefix=@PACKAGE_TARNAME@-@PACKAGE_VERSION@/ \
		--output=$${targ} \
		HEAD && \
	cd -

