#! /usr/bin/env bash
#########################################################################
#									#
# Script ID: ./source/man/man1/Makefile.am				#
# Author: Mark Grant							#
#									#
# Purpose:								#
#	AutoMake script file to generate kernel-utils manual pages	#
# from source.								#
#									#
#########################################################################

#########################################################################
#									#
# Changelog								#
#									#
# Date		Author	Version	Description				#
#									#
# 07/07/2016	MG	1.0.1	First release.				#
# 30/04/2017	MG	1.0.2	Output from $(edit) was being ignored.	#
#				Rename source file extension .man.in	#
#									#
#########################################################################


kern-bld.sh.1: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	$(edit) $(srcdir)/$(@F).man.in > $@.tmp
	txt2manwrap $(@F) 1 "Kernel Utilities Manual" $@.tmp $@
	rm -f $@.tmp

kern-bld.sh.1: $(srcdir)/kern-bld.sh.1.man.in

man_MANS = kern-bld.sh.1

EXTRA_DIST = $(srcdir)/kern-bld.sh.1.man.in

CLEANFILES = *.tmp kern-bld.sh.1
