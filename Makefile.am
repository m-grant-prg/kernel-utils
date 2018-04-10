#! /usr/bin/env bash
#########################################################################
#									#
# Script ID: ./Makefile.am						#
# Author: Copyright (C) 2016-2018  Mark Grant				#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0					#
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
#									#
#########################################################################


ACLOCAL_AMFLAGS = -I m4


SUBDIRS = src/man/1
SUBDIRS += src/prg/bash


srctarball:
	@cwd="$${PWD}" && \
	cd @srcdir@ && \
	git archive --format=tar.gz \
		--prefix=@PACKAGE_TARNAME@-@PACKAGE_VERSION@/ \
		--output=$${cwd}/@PACKAGE_TARNAME@-@PACKAGE_VERSION@.tar.gz \
		 HEAD && \
	cd -
