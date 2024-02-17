#########################################################################
#									#
# Author: Copyright (C) 2016-2019, 2021, 2024  Mark Grant		#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0-only					#
#									#
# Purpose:								#
#	AutoMake script file to generate kernel-utils scripts from	#
# source.								#
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
