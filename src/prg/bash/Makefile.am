#########################################################################
#									#
# Script ID: src/prg/bash/Makefile.am					#
# Author: Copyright (C) 2016-2019  Mark Grant				#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0					#
#									#
# Purpose:								#
#	AutoMake script file to generate kernel-utils scripts from	#
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
# 10/02/2018	MG	1.0.3	Change file's header for new directory	#
#				names.					#
# 09/10/2019	MG	1.0.4	Remove unnecessary shebang.		#
#									#
#########################################################################


kern-bld.sh: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	test -f ./$@.in || srcdir=$(srcdir)/; \
	$(edit) $${srcdir}$(@F).in > $@.tmp

	mv $@.tmp $@

	chmod a+x $@

kern-bld.sh: $(srcdir)/kern-bld.sh.in

bin_SCRIPTS = kern-bld.sh

EXTRA_DIST = $(srcdir)/kern-bld.sh.in

CLEANFILES = *.tmp kern-bld.sh
