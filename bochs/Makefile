# Copyright (C) 2002  MandrakeSoft S.A.
#
#   MandrakeSoft S.A.
#   43, rue d'Aboukir
#   75002 Paris - France
#   http://www.linux-mandrake.com/
#   http://www.mandrakesoft.com/
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301 USA
#
####################################################
# NOTE: To be compatibile with nmake (microsoft vc++) please follow
# the following rules:
#   use $(VAR) not $(VAR)

prefix          = /usr/local
exec_prefix     = $(prefix)
srcdir          = .

bindir          = $(exec_prefix)/bin
libdir          = $(exec_prefix)/lib
plugdir         = $(exec_prefix)/lib/bochs/plugins
datarootdir     = $(prefix)/share
mandir          = $(datarootdir)/man
man1dir         = $(mandir)/man1
man5dir         = $(mandir)/man5
docdir          = $(datarootdir)/doc/bochs
sharedir        = $(datarootdir)/bochs
top_builddir    = .
top_srcdir      = $(srcdir)

DESTDIR =

VERSION=2.4
VER_STRING=2.4
REL_STRING=Build from CVS snapshot on May 3, 2009
MAN_PAGE_1_LIST=bochs bximage bxcommit bochs-dlx
MAN_PAGE_5_LIST=bochsrc
INSTALL_LIST_SHARE=bios/BIOS-bochs-* bios/VGABIOS* 
INSTALL_LIST_DOC=CHANGES COPYING README TODO
INSTALL_LIST_BIN=bochs.exe bximage.exe bxcommit.exe
INSTALL_LIST_BIN_OPTIONAL=bochsdbg.exe
INSTALL_LIST_WIN32=$(INSTALL_LIST_SHARE) $(INSTALL_LIST_DOC) $(INSTALL_LIST_BIN) $(INSTALL_LIST_BIN_OPTIONAL) niclist.exe
INSTALL_LIST_MACOSX=$(INSTALL_LIST_SHARE) $(INSTALL_LIST_DOC) bochs.scpt
# for win32 and macosx, these files get renamed to *.txt in install process
TEXT_FILE_LIST=README CHANGES COPYING TODO VGABIOS-elpin-LICENSE VGABIOS-lgpl-README
CP=cp
CAT=cat
RM=rm
MV=mv
LN_S=ln -sf
DLXLINUX_TAR=dlxlinux4.tar.gz
DLXLINUX_TAR_URL=http://bochs.sourceforge.net/guestos/$(DLXLINUX_TAR)
DLXLINUX_ROMFILE=BIOS-bochs-latest
GUNZIP=gunzip
WGET=not_found
SED=sed
MKDIR=mkdir
RMDIR=rmdir
TAR=tar
CHMOD=chmod
# the GZIP variable is reserved by gzip program
GZIP_BIN=gzip -9
GUNZIP=gunzip
ZIP=zip
UNIX2DOS=unix2dos
LIBTOOL=$(SHELL) $(top_builddir)/libtool
DLLTOOL=dlltool
RC_CMD=rc /fo

.SUFFIXES: .cc

srcdir = .


SHELL = /bin/sh



CC = cl
CXX = cl
CFLAGS = /nologo /MT /W3 /EHs-c- /DNDEBUG /DWIN32 /D_WINDOWS /D_CRT_SECURE_NO_WARNINGS /Ox  $(MCH_CFLAGS) $(FLA_FLAGS)  -DBX_SHARE_PATH='"$(sharedir)"'
CXXFLAGS = /nologo /MT /W3 /EHs-c- /DNDEBUG /DWIN32 /D_WINDOWS /D_CRT_SECURE_NO_WARNINGS /Ox  $(MCH_CFLAGS) $(FLA_FLAGS)  -DBX_SHARE_PATH='"$(sharedir)"'

LDFLAGS = 
LIBS = 
# To compile with readline:
#   linux needs just -lreadline
#   solaris needs -lreadline -lcurses
X_LIBS = 
X_PRE_LIBS = 
XPM_LIB = 
GUI_LINK_OPTS_X = $(X_LIBS) $(X_PRE_LIBS) -lX11 $(XPM_LIB)
GUI_LINK_OPTS_SDL = `sdl-config --cflags --libs`
GUI_LINK_OPTS_SVGA =  -lvga -lvgagl
GUI_LINK_OPTS_BEOS = -lbe
GUI_LINK_OPTS_RFB =  wsock32.lib
GUI_LINK_OPTS_AMIGAOS =
GUI_LINK_OPTS_WIN32 = -luser32 -lgdi32 -lcomdlg32 -lcomctl32 -lwsock32 -lshell32
GUI_LINK_OPTS_WIN32_VCPP = user32.lib gdi32.lib winmm.lib \
  comdlg32.lib comctl32.lib wsock32.lib advapi32.lib shell32.lib
GUI_LINK_OPTS_MACOS =
GUI_LINK_OPTS_CARBON = -framework Carbon
GUI_LINK_OPTS_NOGUI =
GUI_LINK_OPTS_TERM = 
GUI_LINK_OPTS_WX = 
GUI_LINK_OPTS =  $(GUI_LINK_OPTS_RFB) $(GUI_LINK_OPTS_WIN32_VCPP)   wsock32.lib winmm.lib
RANLIB = echo

CFLAGS_CONSOLE = /nologo /MT /W3 /EHs-c- /DNDEBUG /DWIN32 /D_WINDOWS /D_CRT_SECURE_NO_WARNINGS /Ox $(MCH_CFLAGS) $(FLA_FLAGS)
CXXFLAGS_CONSOLE = /nologo /MT /W3 /EHs-c- /DNDEBUG /DWIN32 /D_WINDOWS /D_CRT_SECURE_NO_WARNINGS /Ox $(MCH_CFLAGS) $(FLA_FLAGS)
BXIMAGE_LINK_OPTS = user32.lib

BX_INCDIRS = -I. -I$(srcdir)/. -Iinstrument/stubs -I$(srcdir)/instrument/stubs

#SUBDIRS = iodev bx_debug

#all install uninstall: config.h#
#        for subdir in $(SUBDIRS); do #
#          echo making $@ in $$subdir; #
#          ($(MAKE) -C $$subdir $(MDEFINES) $@) || exit 1; #
#        done#



# gnu flags for clean up
#CFLAGS  = -ansi -O -g -Wunused -Wuninitialized


NONINLINE_OBJS = \
	logio.o \
	main.o \
	config.o \
	load32bitOShack.o \
	pc_system.o \
	osdep.o \
	plugin.o \
	crc.o \
	 win32res.o

EXTERN_ENVIRONMENT_OBJS = \
	main.o \
	config.o \
	load32bitOShack.o \
	pc_system.o

DEBUGGER_LIB   = bx_debug/libdebug.a
DISASM_LIB     = disasm/libdisasm.a
INSTRUMENT_LIB = instrument/stubs/libinstrument.a
FPU_LIB        = fpu/libfpu.a
READLINE_LIB   = 
EXTRA_LINK_OPTS = 

GDBSTUB_OBJS = gdbstub.o

BX_OBJS = $(NONINLINE_OBJS)

BX_INCLUDES = bochs.h config.h osdep.h


.cc.o:
	$(CXX) /c $(BX_INCDIRS) $(CXXFLAGS) /Tp$< /Fo$@
.c.o:
	$(CC) /c $(BX_INCDIRS) $(CFLAGS) $(FPU_FLAGS) $< /Fo$@


all: bochs.exe niclist.exe  bximage.exe bxcommit.exe 



bochs.exe: iodev/libiodev.a  \
           cpu/libcpu.a memory/libmemory.a gui/libgui.a \
           $(DISASM_LIB)  $(BX_OBJS) \
           $(SIMX86_OBJS) $(FPU_LIB)  
	link  /nologo /subsystem:console /incremental:no /out:$@   $(BX_OBJS) $(SIMX86_OBJS) \
		iodev/libiodev.a  cpu/libcpu.a memory/libmemory.a gui/libgui.a \
		$(DISASM_LIB)   \
		 $(FPU_LIB) \
		$(GUI_LINK_OPTS) \
		$(MCH_LINK_FLAGS) \
		$(SIMX86_LINK_FLAGS) \
		$(READLINE_LIB) \
		$(EXTRA_LINK_OPTS) \
		$(LIBS)

# Special make target for cygwin/mingw using dlltool instead of
# libtool.  This creates a .DEF file, and exports file, an import library,
# and then links bochs.exe with the exports file.
.win32_dll_plugin_target: iodev/libiodev.a  \
           cpu/libcpu.a memory/libmemory.a gui/libgui.a \
           $(DISASM_LIB)  $(BX_OBJS) \
           $(SIMX86_OBJS) $(FPU_LIB)  
	$(DLLTOOL) --export-all-symbols --output-def bochs.def \
		$(BX_OBJS) $(SIMX86_OBJS) \
		iodev/libiodev.a cpu/libcpu.a memory/libmemory.a gui/libgui.a \
		 $(DISASM_LIB)   \
		 $(FPU_LIB)
	$(DLLTOOL) --dllname bochs.exe --def bochs.def --output-lib dllexports.a
	$(DLLTOOL) --dllname bochs.exe --output-exp bochs.exp --def bochs.def
	$(CXX) -o bochs.exe $(CXXFLAGS) $(LDFLAGS) -export-dynamic \
	    $(BX_OBJS) bochs.exp $(SIMX86_OBJS) \
		iodev/libiodev.a cpu/libcpu.a memory/libmemory.a gui/libgui.a \
		 $(DISASM_LIB)   \
		 $(FPU_LIB) \
		$(GUI_LINK_OPTS) \
		$(MCH_LINK_FLAGS) \
		$(SIMX86_LINK_FLAGS) \
		$(READLINE_LIB) \
		$(EXTRA_LINK_OPTS) \
		$(LIBS)
	touch .win32_dll_plugin_target

bochs_plugins:
	cd gui 
	$(MAKE) plugins
	cd ..
	cd iodev 
	$(MAKE) plugins
	cd ..

bximage.exe: misc/bximage.o
	link  /nologo /subsystem:console /incremental:no /out:$@  $(BXIMAGE_LINK_OPTS) misc/bximage.o

bxcommit.exe: misc/bxcommit.o
	link  /nologo /subsystem:console /incremental:no /out:$@  misc/bxcommit.o

niclist.exe: misc/niclist.o
	link  /nologo /subsystem:console /incremental:no /out:$@  misc/niclist.o

# compile with console CXXFLAGS, not gui CXXFLAGS
misc/bximage.o: $(srcdir)/misc/bximage.c $(srcdir)/iodev/hdimage.h
	$(CC) /c $(BX_INCDIRS) $(CFLAGS_CONSOLE) $(srcdir)/misc/bximage.c /Fo$@

misc/bxcommit.o: $(srcdir)/misc/bxcommit.c $(srcdir)/iodev/hdimage.h
	$(CC) /c $(BX_INCDIRS) $(CFLAGS_CONSOLE) $(srcdir)/misc/bxcommit.c /Fo$@

misc/niclist.o: $(srcdir)/misc/niclist.c
	$(CC) /c $(BX_INCDIRS) $(CFLAGS_CONSOLE) $(srcdir)/misc/niclist.c /Fo$@

$(BX_OBJS): $(BX_INCLUDES)

# cannot use -C option to be compatible with Microsoft nmake
iodev/libiodev.a::
	cd iodev 
	$(MAKE) $(MDEFINES) libiodev.a
	cd ..

bx_debug/libdebug.a::
	cd bx_debug 
	$(MAKE) $(MDEFINES) libdebug.a
	cd ..

cpu/libcpu.a::
	cd cpu 
	$(MAKE) $(MDEFINES) libcpu.a
	cd ..

memory/libmemory.a::
	cd memory 
	$(MAKE) $(MDEFINES) libmemory.a
	cd ..

gui/libgui.a::
	cd gui 
	$(MAKE) $(MDEFINES) libgui.a
	cd ..

disasm/libdisasm.a::
	cd disasm 
	$(MAKE) $(MDEFINES) libdisasm.a
	cd ..

instrument/stubs/libinstrument.a::
	cd instrument/stubs 
	$(MAKE) $(MDEFINES) libinstrument.a
	cd ..\..

fpu/libfpu.a::
	cd fpu 
	$(MAKE) $(MDEFINES) libfpu.a
	cd ..

libbochs.a:
	-rm -f libbochs.a
	ar rv libbochs.a $(EXTERN_ENVIRONMENT_OBJS)
	$(RANLIB) libbochs.a

libbochs_cpu.a:  $(BX_OBJS)
	-rm -f libbochs_cpu.a
	ar rv libbochs_cpu.a $(BX_OBJS)
	$(RANLIB) libbochs_cpu.a

# for wxWidgets port, on win32 platform
wxbochs_resources.o: wxbochs.rc
	windres $(srcdir)/wxbochs.rc -o $@ --include-dir=`wx-config --prefix`/include

# for win32 gui
win32res.o: win32res.rc bxversion.rc
	$(RC_CMD)$@ $(srcdir)/win32res.rc

#####################################################################
# Install target for all platforms.
#####################################################################

install: all install_win32

#####################################################################
# Install target for win32
#
# This is intended to be run in cygwin, since it has better scripting
# tools.
#####################################################################

install_win32: download_dlx 
	-mkdir -p $(prefix)
	cp obj-release/*.exe .
	for i in $(INSTALL_LIST_WIN32); do if test -f $$i; then cp $$i $(prefix); else cp $(srcdir)/$$i $(prefix); fi; done
	cp $(srcdir)/misc/sb16/sb16ctrl.example $(prefix)/sb16ctrl.txt
	cp $(srcdir)/misc/sb16/sb16ctrl.exe $(prefix)
	#cat $(srcdir)/build/win32/DOC-win32.htm | $(SED) -e 's/2.4/$(VERSION)/g' > $(prefix)/DOC-win32.htm
	cp $(srcdir)/.bochsrc $(prefix)/bochsrc-sample.txt
	-mkdir $(prefix)/keymaps
	cp $(srcdir)/gui/keymaps/*.map $(prefix)/keymaps
	cat $(DLXLINUX_TAR) | (cd $(prefix) && tar xzvf -)
	echo '..\bochs' > $(prefix)/dlxlinux/start.bat
	dlxrc=$(prefix)/dlxlinux/bochsrc.txt; mv $$dlxrc $$dlxrc.orig && sed < $$dlxrc.orig 's/\/usr\/local\/bochs\/latest/../' > $$dlxrc && rm -f $$dlxrc.orig
	mv $(prefix)/README $(prefix)/README.orig
	cat $(srcdir)/build/win32/README.win32-binary $(prefix)/README.orig > $(prefix)/README
	rm -f $(prefix)/README.orig
	for i in $(TEXT_FILE_LIST); do mv $(prefix)/$$i $(prefix)/$$i.txt; done
	cd $(prefix); $(UNIX2DOS) *.txt */*.txt
	cd $(prefix); NAME=`pwd|$(SED) 's/.*\///'`; (cd ..; $(ZIP) $$NAME.zip -r $$NAME); ls -l ../$$NAME.zip

#####################################################################
# install target for unix
#####################################################################

install_unix: install_bin  install_man install_share install_doc 

install_bin::
	for i in $(DESTDIR)$(bindir); do mkdir -p $$i && test -d $$i && test -w $$i; done
	for i in $(INSTALL_LIST_BIN); do if test -f $$i; then install $$i $(DESTDIR)$(bindir); else install $(srcdir)/$$i $(DESTDIR)$(bindir); fi; done
	-for i in $(INSTALL_LIST_BIN_OPTIONAL); do if test -f $$i; then install $$i $(DESTDIR)$(bindir); else install $(srcdir)/$$i $(DESTDIR)$(bindir); fi; done

install_libtool_plugins::
	for i in $(DESTDIR)$(plugdir); do mkdir -p $$i && test -d $$i && test -w $$i; done
	list=`cd gui && echo *.la`; for i in $$list; do $(LIBTOOL) --mode=install install gui/$$i $(DESTDIR)$(plugdir); done
	list=`cd iodev && echo *.la`; for i in $$list; do $(LIBTOOL) --mode=install install iodev/$$i $(DESTDIR)$(plugdir); done
	$(LIBTOOL) --finish $(DESTDIR)$(plugdir)

install_dll_plugins::
	for i in $(DESTDIR)$(plugdir); do mkdir -p $$i && test -d $$i && test -w $$i; done
	list=`cd gui && echo *.dll`; for i in $$list; do cp gui/$$i $(DESTDIR)$(plugdir); done
	list=`cd iodev && echo *.dll`; for i in $$list; do cp iodev/$$i $(DESTDIR)$(plugdir); done

install_share::
	for i in $(DESTDIR)$(sharedir);	do mkdir -p $$i && test -d $$i && test -w $$i; done
	for i in $(INSTALL_LIST_SHARE); do if test -f $$i; then install -m 644 $$i $(DESTDIR)$(sharedir); else install -m 644 $(srcdir)/$$i $(DESTDIR)$(sharedir); fi; done
	-mkdir $(DESTDIR)$(sharedir)/keymaps
	for i in $(srcdir)/gui/keymaps/*.map; do install -m 644 $$i $(DESTDIR)$(sharedir)/keymaps/; done

install_doc::
	for i in $(DESTDIR)$(docdir); do mkdir -p $$i && test -d $$i && test -w $$i; done
	for i in $(INSTALL_LIST_DOC); do if test -f $$i; then install -m 644 $$i $(DESTDIR)$(docdir); else install -m 644 $(srcdir)/$$i $(DESTDIR)$(docdir); fi; done
	$(RM) -f $(DESTDIR)$(docdir)/README
	$(CAT) $(srcdir)/build/linux/README.linux-binary $(srcdir)/README > $(DESTDIR)$(docdir)/README
	install -m 644 $(srcdir)/.bochsrc $(DESTDIR)$(docdir)/bochsrc-sample.txt


build_docbook::
	cd doc/docbook; make

dl_docbook::
	cd doc/docbook; make dl_docs

install_docbook: build_docbook
	cd doc/docbook; make install

install_man::
	-mkdir -p $(DESTDIR)$(man1dir)
	-mkdir -p $(DESTDIR)$(man5dir)
	for i in $(MAN_PAGE_1_LIST); do cat $(srcdir)/doc/man/$$i.1 | $(SED) 's/@version@/$(VERSION)/g' | $(GZIP_BIN) -c >  $(DESTDIR)$(man1dir)/$$i.1.gz; chmod 644 $(DESTDIR)$(man1dir)/$$i.1.gz; done
	for i in $(MAN_PAGE_5_LIST); do cat $(srcdir)/doc/man/$$i.5 | $(GZIP_BIN) -c >  $(DESTDIR)$(man5dir)/$$i.5.gz; chmod 644 $(DESTDIR)$(man5dir)/$$i.5.gz; done

download_dlx: $(DLXLINUX_TAR)

$(DLXLINUX_TAR):
	$(RM) -f $(DLXLINUX_TAR)
	$(WGET) $(DLXLINUX_TAR_URL)
	test -f $(DLXLINUX_TAR)

unpack_dlx: $(DLXLINUX_TAR)
	rm -rf dlxlinux
	$(GUNZIP) -c $(DLXLINUX_TAR) | $(TAR) -xvf -
	test -d dlxlinux
	(cd dlxlinux; $(MV) bochsrc.txt bochsrc.txt.orig; $(SED) -e "s/1\.1\.2/$(VERSION)/g"  -e 's,/usr/local/bochs/latest,$(prefix)/share/bochs,g' < bochsrc.txt.orig > bochsrc.txt; rm -f bochsrc.txt.orig)

install_dlx:
	$(RM) -rf $(DESTDIR)$(sharedir)/dlxlinux
	cp -r dlxlinux $(DESTDIR)$(sharedir)/dlxlinux
	$(CHMOD) 755 $(DESTDIR)$(sharedir)/dlxlinux
	$(GZIP_BIN) $(DESTDIR)$(sharedir)/dlxlinux/hd10meg.img
	$(CHMOD) 644 $(DESTDIR)$(sharedir)/dlxlinux/*
	for i in bochs-dlx; do cp $(srcdir)/build/linux/$$i $(DESTDIR)$(bindir)/$$i; $(CHMOD) 755 $(DESTDIR)$(bindir)/$$i; done

uninstall::
	$(RM) -rf $(DESTDIR)$(sharedir)
	$(RM) -rf $(DESTDIR)$(docdir)
	$(RM) -rf $(DESTDIR)$(libdir)/bochs
	for i in bochs bximage bxcommit bochs-dlx; do rm -f $(DESTDIR)$(bindir)/$$i; done
	for i in $(MAN_PAGE_1_LIST); do $(RM) -f $(man1dir)/$$i.1.gz; done
	for i in $(MAN_PAGE_5_LIST); do $(RM) -f $(man5dir)/$$i.5.gz; done

VS2008_WORKSPACE_ZIP=build/win32/vs2008ex-workspace.zip
VS2008_WORKSPACE_FILES=vs2008/bochs.sln vs2008/*.vcproj

vs2008workspace:
	zip $(VS2008_WORKSPACE_ZIP) $(VS2008_WORKSPACE_FILES)

########
# the win32_snap target is used to create a ZIP of bochs sources configured
# for VC++.  This ZIP is stuck on the website every once in a while to make
# it easier for VC++ users to compile bochs.  First, you should
# run "sh .conf.win32-vcpp" to configure the source code, then do
# "make win32_snap" to unzip the workspace files and create the ZIP.
########
win32_snap:
	unzip $(VS2008_WORKSPACE_ZIP)
	$(MAKE) zip

tar:
	NAME=`pwd|$(SED) 's/.*\///'`; (cd ..; $(RM) -f $$NAME.zip; tar cf - $$NAME | $(GZIP_BIN) > $$NAME.tar.gz); ls -l ../$$NAME.tar.gz

zip:
	NAME=`pwd|$(SED) 's/.*\///'`; (cd ..; $(RM) -f $$NAME-msvc-src.zip; $(ZIP) $$NAME-msvc-src.zip -r $$NAME -x \*CVS\* -x \*.cvsignore ); ls -l ../$$NAME-msvc-src.zip

clean:
	-del *.o
	-del *.a
	-del bochs
	-del bochs.exe
	-del bximage
	-del bximage.exe
	-del bxcommit
	-del bxcommit.exe
	-del niclist
	-del niclist.exe
	-del bochs.out
	-del bochsout.txt
	-del bochs.exp
	-del bochs.def
	-del bochs.scpt
	-del -rf bochs.app
	-del -rf .libs
	-del .win32_dll_plugin_target

local-dist-clean: clean
	-del config.h config.status config.log config.cache
	-del .dummy `find . -name '*.dsp' -o -name '*.dsw' -o -name '*.opt' -o -name '.DS_Store'`
	-del bxversion.h build/linux/bochs-dlx _rpm_top *.rpm
	-del build/win32/nsis/Makefile build/win32/nsis/bochs.nsi
	-del build/macosx/Info.plist build/macosx/script_compiled.rsrc
	-del libtool
	-del ltdlconf.h

all-clean: clean
	cd iodev 
	$(MAKE) clean
	cd ..
	cd bx_debug 
	$(MAKE) clean
	cd ..
	cd cpu 
	$(MAKE) clean
	cd ..
	cd memory 
	$(MAKE) clean
	cd ..
	cd gui 
	$(MAKE) clean
	cd ..
	cd disasm 
	$(MAKE) clean
	cd ..
	cd instrument/stubs 
	$(MAKE) clean
	cd ..\..
	cd misc 
	$(MAKE) clean
	cd ..
	cd fpu 
	$(MAKE) clean
	cd ..
	cd doc/docbook 
	$(MAKE) clean
	cd ..\..
	cd host/linux/pcidev 
	$(MAKE) clean
	cd ..\..\..

dist-clean: local-dist-clean
	cd iodev 
	$(MAKE) dist-clean
	cd ..
	cd bx_debug 
	$(MAKE) dist-clean
	cd ..
	cd bios 
	$(MAKE) dist-clean
	cd ..
	cd cpu 
	$(MAKE) dist-clean
	cd ..
	cd memory 
	$(MAKE) dist-clean
	cd ..
	cd gui 
	$(MAKE) dist-clean
	cd ..
	cd disasm 
	$(MAKE) dist-clean
	cd ..
	cd instrument/stubs 
	$(MAKE) dist-clean
	cd ..\..
	cd misc 
	$(MAKE) dist-clean
	cd ..
	cd fpu 
	$(MAKE) dist-clean
	cd ..
	cd doc/docbook 
	$(MAKE) dist-clean
	cd ..\..
	cd host/linux/pcidev 
	$(MAKE) dist-clean
	cd ..\..\..
	-del Makefile

###########################################
# Build app on MacOS X
###########################################
MACOSX_STUFF=build/macosx
MACOSX_STUFF_SRCDIR=$(srcdir)/$(MACOSX_STUFF)
APP=bochs.app
APP_PLATFORM=MacOS
SCRIPT_EXEC=bochs.scpt
SCRIPT_DATA=$(MACOSX_STUFF_SRCDIR)/script.data
SCRIPT_R=$(MACOSX_STUFF_SRCDIR)/script.r
SCRIPT_APPLESCRIPT=$(MACOSX_STUFF_SRCDIR)/bochs.applescript
SCRIPT_COMPILED_RSRC=$(MACOSX_STUFF)/script_compiled.rsrc
REZ=/Developer/Tools/Rez
CPMAC=/Developer/Tools/CpMac
RINCLUDES=/System/Library/Frameworks/Carbon.framework/Libraries/RIncludes
REZ_ARGS=-append -i $RINCLUDES -d SystemSevenOrLater=1 -useDF
STANDALONE_LIBDIR=`pwd`/$(APP)/Contents/$(APP_PLATFORM)/lib
OSACOMPILE=/usr/bin/osacompile
SETFILE=/Developer/Tools/Setfile

# On a MacOS X machine, you run rez, osacompile, and setfile to
# produce the script executable, which has both a data fork and a
# resource fork.  Ideally, we would just recompile the whole
# executable at build time, but unfortunately this cannot be done on
# the SF compile farm through an ssh connection because osacompile
# needs to be run locally for some reason.  Solution: If the script
# sources are changed, rebuild the executable on a MacOSX machine,
# split it into its data and resource forks and check them into CVS
# as separate files.  Then at release time, all that's left to do is
# put the data and resource forks back together to make a working script.
# (This can be done through ssh.)
#
# Sources:
# 1. script.r: resources for the script
# 2. script.data: binary data for the script
# 3. bochs.applescript: the source of the script
#
# NOTE: All of this will fail if you aren't building on an HFS+
# filesystem!  On the SF compile farm building in your user directory
# will fail, while doing the build in /tmp will work ok.

# check if this filesystem supports resource forks at all
test_hfsplus:
	$(RM) -rf test_hfsplus
	echo data > test_hfsplus
	# if you get "Not a directory", then this filesystem doesn't support resources
	echo resource > test_hfsplus/rsrc
	# test succeeded
	$(RM) -rf test_hfsplus

# Step 1 (must be done locally on MacOSX, only when sources change)
# Compile and pull out just the resource fork.  The resource fork is
# checked into CVS as script_compiled.rsrc.  Note that we don't need
# to check in the data fork of tmpscript because it is identical to the
# script.data input file.
$(SCRIPT_COMPILED_RSRC): $(SCRIPT_R) $(SCRIPT_APPLESCRIPT)
	$(RM) -f tmpscript
	$(CP) -f $(SCRIPT_DATA) tmpscript
	$(REZ) -append $(SCRIPT_R) -o tmpscript
	$(OSACOMPILE) -o tmpscript $(SCRIPT_APPLESCRIPT)
	$(CP) tmpscript/rsrc $(SCRIPT_COMPILED_RSRC)
	$(RM) -f tmpscript

# Step 2 (can be done locally or remotely on MacOSX)
# Combine the data fork and resource fork, and set attributes.
$(SCRIPT_EXEC): $(SCRIPT_DATA) $(SCRIPT_COMPILED_RSRC)
	rm -f $(SCRIPT_EXEC)
	$(CP) $(SCRIPT_DATA) $(SCRIPT_EXEC)
	if test ! -f $(SCRIPT_COMPILED_RSRC); then $(CP) $(srcdir)/$(SCRIPT_COMPILED_RSRC) $(SCRIPT_COMPILED_RSRC); fi
	$(CP) $(SCRIPT_COMPILED_RSRC) $(SCRIPT_EXEC)/rsrc
	$(SETFILE) -t "APPL" -c "aplt" $(SCRIPT_EXEC)

$(APP)/.build: bochs test_hfsplus $(SCRIPT_EXEC)
	rm -f $(APP)/.build
	$(MKDIR) -p $(APP)
	$(MKDIR) -p $(APP)/Contents
	$(CP) -f $(MACOSX_STUFF)/Info.plist $(APP)/Contents
	$(CP) -f $(MACOSX_STUFF_SRCDIR)/pbdevelopment.plist $(APP)/Contents
	echo -n "APPL????"  > $(APP)/Contents/PkgInfo
	$(MKDIR) -p $(APP)/Contents/$(APP_PLATFORM)
	$(CP) bochs $(APP)/Contents/$(APP_PLATFORM)
	$(MKDIR) -p $(APP)/Contents/Resources
	$(REZ) $(REZ_ARGS) $(MACOSX_STUFF_SRCDIR)/bochs.r -o $(APP)/Contents/Resources/bochs.rsrc
	$(CP) -f $(MACOSX_STUFF_SRCDIR)/bochs-icn.icns $(APP)/Contents/Resources
	ls -ld $(APP) $(SCRIPT_EXEC) $(SCRIPT_EXEC)/rsrc
	touch $(APP)/.build

$(APP)/.build_plugins: $(APP)/.build bochs_plugins
	rm -f $(APP)/.build_plugins
	$(MKDIR) -p $(STANDALONE_LIBDIR);
	list=`cd gui && echo *.la`; for i in $$list; do $(LIBTOOL) cp gui/$$i $(STANDALONE_LIBDIR); done;
	list=`cd iodev && echo *.la`; for i in $$list; do $(LIBTOOL) cp iodev/$$i $(STANDALONE_LIBDIR); done;
	$(LIBTOOL) --finish $(STANDALONE_LIBDIR);
	touch $(APP)/.build_plugins

install_macosx: all download_dlx install_man 
	-mkdir -p $(DESTDIR)$(sharedir)
	for i in $(INSTALL_LIST_MACOSX); do if test -e $$i; then $(CPMAC) -r $$i $(DESTDIR)$(sharedir); else $(CPMAC) -r $(srcdir)/$$i $(DESTDIR)$(sharedir); fi; done
	$(CPMAC) $(srcdir)/.bochsrc $(DESTDIR)$(sharedir)/bochsrc-sample.txt
	-mkdir $(DESTDIR)$(sharedir)/keymaps
	$(CPMAC) $(srcdir)/gui/keymaps/*.map $(DESTDIR)$(sharedir)/keymaps
	cat $(DLXLINUX_TAR) | (cd $(DESTDIR)$(sharedir) && tar xzvf -)
	dlxrc=$(DESTDIR)$(sharedir)/dlxlinux/bochsrc.txt; mv "$$dlxrc" "$$dlxrc.orig" && sed < "$$dlxrc.orig" 's/\/usr\/local\/bochs\/latest/../' > "$$dlxrc" && rm -f "$$dlxrc.orig"
	mv $(srcdir)/README $(srcdir)/README.orig
	cat $(srcdir)/build/macosx/README.macosx-binary $(srcdir)/README.orig > $(DESTDIR)$(sharedir)/README
	rm -f $(DESTDIR)$(sharedir)/README.orig
	$(CPMAC) $(SCRIPT_EXEC) $(DESTDIR)$(sharedir)/dlxlinux
#	for i in $(TEXT_FILE_LIST); do mv $(srcdir)/$$i $(DESTDIR)$(sharedir)/$$i.txt; done

###########################################
# BeOS make target.
# Build the binary normally, then copy the resource attributes.
###########################################
.bochs_beos_target: bochs.exe
	unzip $(srcdir)/build/beos/resource.zip
	copyattr -t ICON BeBochs.rsrc bochs
	copyattr -t MICN BeBochs.rsrc bochs

###########################################
# dependencies generated by
#  gcc -MM -I. -Iinstrument/stubs *.cc | sed -e 's/\.cc/.cc/g' -e 's,cpu/,cpu/,g'
###########################################
config.o: config.cc bochs.h config.h osdep.h bx_debug/debug.h config.h \
  osdep.h bxversion.h gui/siminterface.h memory/memory.h pc_system.h \
  plugin.h extplugin.h ltdl.h gui/gui.h instrument/stubs/instrument.h \
  iodev/iodev.h bochs.h iodev/vga.h
crc.o: crc.cc config.h
gdbstub.o: gdbstub.cc bochs.h config.h osdep.h bx_debug/debug.h config.h \
  osdep.h bxversion.h gui/siminterface.h memory/memory.h pc_system.h \
  plugin.h extplugin.h ltdl.h gui/gui.h instrument/stubs/instrument.h \
  cpu/cpu.h cpu/crregs.h cpu/descriptor.h cpu/instr.h cpu/lazy_flags.h \
  cpu/icache.h cpu/apic.h cpu/i387.h fpu/softfloat.h fpu/tag_w.h \
  fpu/status_w.h fpu/control_w.h cpu/xmm.h cpu/stack.h iodev/iodev.h \
  bochs.h iodev/vga.h
load32bitOShack.o: load32bitOShack.cc bochs.h config.h osdep.h \
  bx_debug/debug.h config.h osdep.h bxversion.h gui/siminterface.h \
  memory/memory.h pc_system.h plugin.h extplugin.h ltdl.h gui/gui.h \
  instrument/stubs/instrument.h cpu/cpu.h cpu/crregs.h cpu/descriptor.h \
  cpu/instr.h cpu/lazy_flags.h cpu/icache.h cpu/apic.h cpu/i387.h \
  fpu/softfloat.h fpu/tag_w.h fpu/status_w.h fpu/control_w.h cpu/xmm.h \
  iodev/iodev.h bochs.h iodev/vga.h
logio.o: logio.cc bochs.h config.h osdep.h bx_debug/debug.h config.h \
  osdep.h bxversion.h gui/siminterface.h memory/memory.h pc_system.h \
  plugin.h extplugin.h ltdl.h gui/gui.h instrument/stubs/instrument.h \
  cpu/cpu.h cpu/crregs.h cpu/descriptor.h cpu/instr.h cpu/lazy_flags.h \
  cpu/icache.h cpu/apic.h cpu/i387.h fpu/softfloat.h fpu/tag_w.h \
  fpu/status_w.h fpu/control_w.h cpu/xmm.h iodev/iodev.h bochs.h \
  iodev/vga.h
main.o: main.cc bochs.h config.h osdep.h bx_debug/debug.h config.h \
  osdep.h bxversion.h gui/siminterface.h memory/memory.h pc_system.h \
  plugin.h extplugin.h ltdl.h gui/gui.h instrument/stubs/instrument.h \
  gui/textconfig.h cpu/cpu.h cpu/crregs.h cpu/descriptor.h cpu/instr.h \
  cpu/lazy_flags.h cpu/icache.h cpu/apic.h cpu/i387.h fpu/softfloat.h \
  fpu/tag_w.h fpu/status_w.h fpu/control_w.h cpu/xmm.h iodev/iodev.h \
  bochs.h iodev/vga.h
osdep.o: osdep.cc bochs.h config.h osdep.h bx_debug/debug.h config.h \
  osdep.h bxversion.h gui/siminterface.h memory/memory.h pc_system.h \
  plugin.h extplugin.h ltdl.h gui/gui.h instrument/stubs/instrument.h
pc_system.o: pc_system.cc bochs.h config.h osdep.h bx_debug/debug.h \
  config.h osdep.h bxversion.h gui/siminterface.h memory/memory.h \
  pc_system.h plugin.h extplugin.h ltdl.h gui/gui.h \
  instrument/stubs/instrument.h cpu/cpu.h cpu/crregs.h cpu/descriptor.h \
  cpu/instr.h cpu/lazy_flags.h cpu/icache.h cpu/apic.h cpu/i387.h \
  fpu/softfloat.h fpu/tag_w.h fpu/status_w.h fpu/control_w.h cpu/xmm.h \
  iodev/iodev.h bochs.h iodev/vga.h
plex86-interface.o: plex86-interface.cc bochs.h config.h osdep.h \
  bx_debug/debug.h config.h osdep.h bxversion.h gui/siminterface.h \
  memory/memory.h pc_system.h plugin.h extplugin.h ltdl.h gui/gui.h \
  instrument/stubs/instrument.h plex86-interface.h plex86/plex86.h \
  plex86/descriptor.h
plugin.o: plugin.cc bochs.h config.h osdep.h bx_debug/debug.h config.h \
  osdep.h bxversion.h gui/siminterface.h memory/memory.h pc_system.h \
  plugin.h extplugin.h ltdl.h gui/gui.h instrument/stubs/instrument.h \
  iodev/iodev.h bochs.h iodev/vga.h
