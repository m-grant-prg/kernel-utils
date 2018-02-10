#! /usr/bin/env bash
#########################################################################
#									#
# Script ID: src/man/1/Makefile.am					#
# Author: Copyright (C) 2016-2018  Mark Grant				#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0					#
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
# 08/12/2017	MG	1.0.3	Add SPDX license tags to source files.	#
#				Determine the manual section from the	#
#				target suffix. If the suffix is blank	#
#				(foo.) or if there is no suffix (foo)	#
#				then error out.				#
# 10/02/2018	MG	1.0.4	Change file's header for new directory	#
#				names.					#
#									#
#########################################################################


kern-bld.sh.1: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	$(edit) $(srcdir)/$(@F).man.in > $@.tmp
	targfile=$(@F);	\
	if [[ $$targfile == *"."* ]]; then \
		if [[ $${targfile##*.} == "" ]]; then \
			echo "Source file suffix used as section but empty."; \
			exit 1; \
		else \
			section=$${targfile##*.}; \
		fi; \
	else \
		echo "Source file suffix used as section but no dot & empty."; \
		exit 1; \
	fi; \
	txt2manwrap $(@F) $$section "Kernel Utilities Manual" $@.tmp $@
	rm -f $@.tmp

kern-bld.sh.1: $(srcdir)/kern-bld.sh.1.man.in

man_MANS = kern-bld.sh.1

EXTRA_DIST = $(srcdir)/kern-bld.sh.1.man.in

CLEANFILES = *.tmp kern-bld.sh.1
