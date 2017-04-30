#! /usr/bin/env bash
#########################################################################
#									#
# Script ID: ./source/progs/bash/Makefile.am				#
# Author: Mark Grant							#
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
