
AM_TESTS_ENVIRONMENT = TOP_SRCDIR=$(top_srcdir)

TESTS = \
	run-basic.sh \
	run-exit.sh \
	run-sha256.sh

EXTRA_DIST = \
	run-basic.sh \
	run-exit.sh \
	run-sha256.sh \
	random.data random.data.sum

noinst_PROGRAMS = \
	basic \
	exit0 \
	exit1 \
	sha256-test

basic_SOURCES = basic.c

basic.o:	basic.c
	$(MOX_GCC) -I$(top_srcdir)/runtime -Wall -O2 -c $<
basic$(EXEEXT):	basic.o ../runtime/libsandboxrt.a
	$(MOX_GCC) -Wall -O2 -o $@ basic.o

sha256_test_SOURCES = sha256.h sha256.c sha256-test.c memset.c strstr.c

sha256.o:	sha256.c memset.c
	$(MOX_GCC) -I$(top_srcdir)/tests -I$(top_srcdir)/runtime -Wall -O2 -c $<
sha256-test.o:	sha256-test.c strstr.c
	$(MOX_GCC) -I$(top_srcdir)/tests -I$(top_srcdir)/runtime -Wall -O2 -c $<
sha256-test$(EXEEXT):	sha256.o sha256-test.o ../runtime/libsandboxrt.a
	$(MOX_GCC) -Wall -O2 -o $@ sha256.o sha256-test.o

exit0_SOURCES = exit0.c

exit0.o:	exit0.c
	$(MOX_GCC) -I$(top_srcdir)/runtime -Wall -O2 -c $<
exit0$(EXEEXT):	exit0.o ../runtime/libsandboxrt.a
	$(MOX_GCC) -Wall -O2 -o $@ exit0.o

exit1_SOURCES = exit1.c

exit1.o:	exit1.c
	$(MOX_GCC) -I$(top_srcdir)/runtime -Wall -O2 -c $<
exit1$(EXEEXT):	exit1.o ../runtime/libsandboxrt.a
	$(MOX_GCC) -Wall -O2 -o $@ exit1.o

